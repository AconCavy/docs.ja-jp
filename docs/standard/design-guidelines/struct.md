---
title: 構造体のデザイン
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
ms.openlocfilehash: b6d06bc8a1e8535f1452af0726138abaebfd4951
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743606"
---
# <a name="struct-design"></a><span data-ttu-id="13cf5-102">構造体のデザイン</span><span class="sxs-lookup"><span data-stu-id="13cf5-102">Struct Design</span></span>
<span data-ttu-id="13cf5-103">一般的な目的の値型は、ほとんどの場合、構造体であるC#キーワードと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="13cf5-103">The general-purpose value type is most often referred to as a struct, its C# keyword.</span></span> <span data-ttu-id="13cf5-104">このセクションでは、一般的な構造体のデザインに関するガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="13cf5-104">This section provides guidelines for general struct design.</span></span>

 <span data-ttu-id="13cf5-105">❌ は、構造体のパラメーターなしのコンストラクターを提供しません。</span><span class="sxs-lookup"><span data-stu-id="13cf5-105">❌ DO NOT provide a parameterless constructor for a struct.</span></span>

 <span data-ttu-id="13cf5-106">このガイドラインに従うことで、配列の各項目に対してコンストラクターを実行しなくても、構造体の配列を作成できます。</span><span class="sxs-lookup"><span data-stu-id="13cf5-106">Following this guideline allows arrays of structs to be created without having to run the constructor on each item of the array.</span></span> <span data-ttu-id="13cf5-107">ではC# 、構造体にパラメーターなしのコンストラクターを含めることはできないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="13cf5-107">Notice that C# does not allow structs to have parameterless constructors.</span></span>

 <span data-ttu-id="13cf5-108">❌ は、変更可能な値の型を定義しません。</span><span class="sxs-lookup"><span data-stu-id="13cf5-108">❌ DO NOT define mutable value types.</span></span>

 <span data-ttu-id="13cf5-109">変更可能な値の型にはいくつかの問題があります。</span><span class="sxs-lookup"><span data-stu-id="13cf5-109">Mutable value types have several problems.</span></span> <span data-ttu-id="13cf5-110">たとえば、プロパティ getter が値型を返す場合、呼び出し元はコピーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="13cf5-110">For example, when a property getter returns a value type, the caller receives a copy.</span></span> <span data-ttu-id="13cf5-111">コピーは暗黙的に作成されるため、開発者は元の値ではなくコピーを変更することを認識していない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="13cf5-111">Because the copy is created implicitly, developers might not be aware that they are mutating the copy, and not the original value.</span></span> <span data-ttu-id="13cf5-112">また、一部の言語 (特に動的言語) では、変更可能な値型を使用した場合に問題が発生します。これは、ローカル変数でも逆参照した場合にコピーが作成されるためです。</span><span class="sxs-lookup"><span data-stu-id="13cf5-112">Also, some languages (dynamic languages, in particular) have problems using mutable value types because even local variables, when dereferenced, cause a copy to be made.</span></span>

 <span data-ttu-id="13cf5-113">✔️、すべてのインスタンスデータが0、false、または null (必要に応じて) に設定されている状態であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="13cf5-113">✔️ DO ensure that a state where all instance data is set to zero, false, or null (as appropriate) is valid.</span></span>

 <span data-ttu-id="13cf5-114">これにより、構造体の配列が作成されたときに無効なインスタンスが誤って作成されるのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="13cf5-114">This prevents accidental creation of invalid instances when an array of the structs is created.</span></span>

 <span data-ttu-id="13cf5-115">✔️値型に <xref:System.IEquatable%601> を実装します。</span><span class="sxs-lookup"><span data-stu-id="13cf5-115">✔️ DO implement <xref:System.IEquatable%601> on value types.</span></span>

 <span data-ttu-id="13cf5-116">値型の <xref:System.Object.Equals%2A?displayProperty=nameWithType> メソッドでは、ボックス化が発生しますが、リフレクションを使用するため、既定の実装はあまり効率的ではありません。</span><span class="sxs-lookup"><span data-stu-id="13cf5-116">The <xref:System.Object.Equals%2A?displayProperty=nameWithType> method on value types causes boxing, and its default implementation is not very efficient, because it uses reflection.</span></span> <span data-ttu-id="13cf5-117"><xref:System.IEquatable%601.Equals%2A> のパフォーマンスは大幅に向上し、ボックス化が行われないように実装できます。</span><span class="sxs-lookup"><span data-stu-id="13cf5-117"><xref:System.IEquatable%601.Equals%2A> can have much better performance and can be implemented so that it will not cause boxing.</span></span>

 <span data-ttu-id="13cf5-118">❌ 明示的に <xref:System.ValueType>を拡張しないでください。</span><span class="sxs-lookup"><span data-stu-id="13cf5-118">❌ DO NOT explicitly extend <xref:System.ValueType>.</span></span> <span data-ttu-id="13cf5-119">実際、ほとんどの言語ではこれを回避できます。</span><span class="sxs-lookup"><span data-stu-id="13cf5-119">In fact, most languages prevent this.</span></span>

 <span data-ttu-id="13cf5-120">一般に、構造体は非常に便利ですが、頻繁にボックス化されない小さな単一の変更できない値に対してのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="13cf5-120">In general, structs can be very useful but should only be used for small, single, immutable values that will not be boxed frequently.</span></span>

 <span data-ttu-id="13cf5-121">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="13cf5-121">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="13cf5-122">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="13cf5-122">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="13cf5-123">参照</span><span class="sxs-lookup"><span data-stu-id="13cf5-123">See also</span></span>

- [<span data-ttu-id="13cf5-124">型デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="13cf5-124">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="13cf5-125">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="13cf5-125">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="13cf5-126">クラスまたは構造体の選択</span><span class="sxs-lookup"><span data-stu-id="13cf5-126">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
