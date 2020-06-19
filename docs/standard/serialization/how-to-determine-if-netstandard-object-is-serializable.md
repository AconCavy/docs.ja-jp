---
title: .NET Standard オブジェクトがシリアル化可能かどうかを判断する方法
description: .NET Standard 型をシリアル化できるかどうかを実行時に判断する方法について説明します。
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.openlocfilehash: 4037dee36aeb619eb2757016904fd877158e57cf
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159898"
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a><span data-ttu-id="868e9-103">.NET Standard オブジェクトがシリアル化可能かどうかを判断する方法</span><span class="sxs-lookup"><span data-stu-id="868e9-103">How to determine if a .NET Standard object is serializable</span></span>

<span data-ttu-id="868e9-104">.NET Standard とは、そのバージョンの標準に準拠する特定の .NET 実装に存在する必要がある型とメンバーを定義する仕様です。</span><span class="sxs-lookup"><span data-stu-id="868e9-104">The .NET Standard is a specification that defines the types and members that must be present on specific .NET implementations that conform to that version of the standard.</span></span> <span data-ttu-id="868e9-105">ただし、.NET Standard では、型がシリアル化可能かどうかは定義されていません。</span><span class="sxs-lookup"><span data-stu-id="868e9-105">However, the .NET Standard does not define whether a type is serializable.</span></span> <span data-ttu-id="868e9-106">.NET Standard ライブラリに定義されている型は、<xref:System.SerializableAttribute> 属性でマークされていません。</span><span class="sxs-lookup"><span data-stu-id="868e9-106">The types defined in the .NET Standard Library are not marked with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="868e9-107">代わりに、特定の型がシリアル化可能かどうかは、.NET Framework や .NET Core などの特定の .NET 実装で自由に決定できます。</span><span class="sxs-lookup"><span data-stu-id="868e9-107">Instead, specific .NET implementations, such as the .NET Framework and .NET Core, are free to determine whether a particular type is serializable.</span></span>

<span data-ttu-id="868e9-108">.NET Standard をターゲットとするライブラリを開発した場合、そのライブラリは、.NET Standard をサポートするすべての .NET 実装で使用できます。</span><span class="sxs-lookup"><span data-stu-id="868e9-108">If you've developed a library that targets the .NET Standard, your library can be consumed by any .NET implementation that supports the .NET Standard.</span></span> <span data-ttu-id="868e9-109">つまり、特定の型がシリアル化可能かどうかを事前に知ることはできません。シリアル化可能かどうかは、実行時にのみ判断できます。</span><span class="sxs-lookup"><span data-stu-id="868e9-109">This means that you cannot know in advance whether a particular type is serializable; you can only determine whether it is serializable at run time.</span></span>

<span data-ttu-id="868e9-110">オブジェクトがシリアル化可能かどうかを実行時に判断するには、オブジェクトの型を表す <xref:System.Type> オブジェクトの <xref:System.Type.IsSerializable> プロパティの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="868e9-110">You can determine whether an object is serializable at runtime by retrieving the value of the <xref:System.Type.IsSerializable> property of a <xref:System.Type> object that represents that object's type.</span></span> <span data-ttu-id="868e9-111">次の例で 1 つの実装を示します。</span><span class="sxs-lookup"><span data-stu-id="868e9-111">The following example provides one implementation.</span></span> <span data-ttu-id="868e9-112">これは、<xref:System.Object> インスタンスをシリアル化できるかどうかを示す `IsSerializable(Object)` 拡張メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="868e9-112">It defines an `IsSerializable(Object)` extension method that indicates whether any <xref:System.Object> instance can be serialized.</span></span>

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

<span data-ttu-id="868e9-113">次の例に示すように、任意のオブジェクトをメソッドに渡して、それを現在の .NET 実装でシリアル化および逆シリアル化できるかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="868e9-113">You can then pass any object to the method to determine whether it can be serialized and deserialized on the current .NET implementation, as the following example shows:</span></span>

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

## <a name="see-also"></a><span data-ttu-id="868e9-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="868e9-114">See also</span></span>

- [<span data-ttu-id="868e9-115">バイナリ シリアル化</span><span class="sxs-lookup"><span data-stu-id="868e9-115">Binary serialization</span></span>](binary-serialization.md)
- <xref:System.SerializableAttribute?displayProperty=nameWithType>
- <xref:System.Type.IsSerializable?displayProperty=nameWithType>
