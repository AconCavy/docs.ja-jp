---
title: シリアル化プロセスの手順
description: シリアル化プロセスは、フォーマッタでシリアル化メソッドが呼び出されると開始されます。 この記事では、一連のイベントについて説明します。
ms.date: 08/07/2017
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
ms.openlocfilehash: 1f749b9102182e78bc3fda436cf386a9f5759d5a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379101"
---
# <a name="steps-in-the-serialization-process"></a><span data-ttu-id="7e003-104">シリアル化プロセスの手順</span><span class="sxs-lookup"><span data-stu-id="7e003-104">Steps in the serialization process</span></span>
<span data-ttu-id="7e003-105">[フォーマッタ](xref:System.Runtime.Serialization.Formatter)で <xref:System.Runtime.Serialization.Formatter.Serialize%2A> メソッドが呼び出されると、次の一連の規則に従って、オブジェクトのシリアル化プロセスが実行されます。</span><span class="sxs-lookup"><span data-stu-id="7e003-105">When the <xref:System.Runtime.Serialization.Formatter.Serialize%2A> method is called on a [formatter](xref:System.Runtime.Serialization.Formatter), object serialization proceeds according to the following sequence of rules:</span></span>

- <span data-ttu-id="7e003-106">フォーマッタにサロゲート セレクターが存在するかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="7e003-106">A check is made to determine whether the formatter has a surrogate selector.</span></span> <span data-ttu-id="7e003-107">サロゲート セレクターが存在する場合は、そのサロゲート セレクターが指定された型のオブジェクトを処理できるかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="7e003-107">If the formatter does, check whether the surrogate selector handles objects of the given type.</span></span> <span data-ttu-id="7e003-108">そのオブジェクトの型を処理できる場合は、サロゲート セレクターで <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7e003-108">If the selector handles the object type, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> is called on the surrogate selector.</span></span>

- <span data-ttu-id="7e003-109">サロゲート セレクターが存在しないか、またはサロゲート セレクターがそのオブジェクトの型を処理しない場合は、オブジェクトが [Serializable](xref:System.SerializableAttribute) 属性でマークされているかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="7e003-109">If there is no surrogate selector or if it does not handle the object type, a check is made to determine whether the object is marked with the [Serializable](xref:System.SerializableAttribute) attribute.</span></span> <span data-ttu-id="7e003-110">オブジェクトにそのマークがない場合、<xref:System.Runtime.Serialization.SerializationException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="7e003-110">If the object is not, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>

- <span data-ttu-id="7e003-111">オブジェクトが適切にマークされている場合は、オブジェクトが <xref:System.Runtime.Serialization.ISerializable> インターフェイスを実装しているかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="7e003-111">If the object is marked appropriately, check whether the object implements the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span> <span data-ttu-id="7e003-112">実装している場合は、そのオブジェクトで <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7e003-112">If the object does, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> is called on the object.</span></span>
  
- <span data-ttu-id="7e003-113">オブジェクトが <xref:System.Runtime.Serialization.ISerializable> を実装していない場合は、既定のシリアル化ポリシーを適用して、[NonSerialized](xref:System.NonSerializedAttribute) としてマークされていないすべてのフィールドをシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="7e003-113">If the object does not implement <xref:System.Runtime.Serialization.ISerializable>, the default serialization policy is used, serializing all fields not marked as [NonSerialized](xref:System.NonSerializedAttribute).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="7e003-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="7e003-114">See also</span></span>

- [<span data-ttu-id="7e003-115">バイナリ シリアル化</span><span class="sxs-lookup"><span data-stu-id="7e003-115">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="7e003-116">XML シリアル化および SOAP シリアル化</span><span class="sxs-lookup"><span data-stu-id="7e003-116">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
