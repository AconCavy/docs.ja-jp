---
title: データ コントラクト名
description: データコントラクトとメンバーの名前付け規則、および同等のデータコントラクトを使用した通信をサポートする WCF インフラストラクチャの既定の動作について説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], naming
ms.assetid: 31f87e6c-247b-48f5-8e94-b9e1e33d8d09
ms.openlocfilehash: 85c533d683558520d46f259db0bdb34dcb1214c9
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247404"
---
# <a name="data-contract-names"></a><span data-ttu-id="5c033-103">データ コントラクト名</span><span class="sxs-lookup"><span data-stu-id="5c033-103">Data Contract Names</span></span>

<span data-ttu-id="5c033-104">クライアントとサービスが同じ型を共有しないことがあります。</span><span class="sxs-lookup"><span data-stu-id="5c033-104">Sometimes a client and a service do not share the same types.</span></span> <span data-ttu-id="5c033-105">このような場合でも、双方のデータ コントラクトが等価であれば、相互にデータを受け渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="5c033-105">They can still pass data to each other as long as the data contracts are equivalent on both sides.</span></span> <span data-ttu-id="5c033-106">データ[コントラクトの等価性](data-contract-equivalence.md)は、データコントラクトとデータメンバーの名前に基づいています。したがって、型とメンバーをこれらの名前にマップするための機構が用意されています。</span><span class="sxs-lookup"><span data-stu-id="5c033-106">[Data Contract Equivalence](data-contract-equivalence.md) is based on data contract and data member names, and therefore a mechanism is provided to map types and members to those names.</span></span> <span data-ttu-id="5c033-107">このトピックでは、データコントラクトの名前付けの規則と、名前を作成するときの Windows Communication Foundation (WCF) インフラストラクチャの既定の動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="5c033-107">This topic explains the rules for naming data contracts as well as the default behavior of the Windows Communication Foundation (WCF) infrastructure when creating names.</span></span>

## <a name="basic-rules"></a><span data-ttu-id="5c033-108">基本的な規則</span><span class="sxs-lookup"><span data-stu-id="5c033-108">Basic Rules</span></span>
<span data-ttu-id="5c033-109">データ コントラクトの名前付けに関する基本的な規則は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5c033-109">Basic rules regarding naming data contracts include:</span></span>

- <span data-ttu-id="5c033-110">データ コントラクトの完全修飾名は、名前空間と名前から構成されます。</span><span class="sxs-lookup"><span data-stu-id="5c033-110">A fully-qualified data contract name consists of a namespace and a name.</span></span>

- <span data-ttu-id="5c033-111">データ メンバーは名前のみを持ち、名前空間はありません。</span><span class="sxs-lookup"><span data-stu-id="5c033-111">Data members have only names, but no namespaces.</span></span>

- <span data-ttu-id="5c033-112">データコントラクトを処理する場合、WCF インフラストラクチャでは、データコントラクトとデータメンバーの名前空間と名前の両方で大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="5c033-112">When processing data contracts, the WCF infrastructure is case-sensitive to both the namespaces and the names of data contracts and data members.</span></span>

## <a name="data-contract-namespaces"></a><span data-ttu-id="5c033-113">データ コントラクト名前空間</span><span class="sxs-lookup"><span data-stu-id="5c033-113">Data Contract Namespaces</span></span>
<span data-ttu-id="5c033-114">データ コントラクトの名前空間は、URI (Uniform Resource Identifier) の形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="5c033-114">A data contract namespace takes the form of a Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="5c033-115">URI は、絶対 URI でも相対 URI のどちらでもかまいません。</span><span class="sxs-lookup"><span data-stu-id="5c033-115">The URI can be either absolute or relative.</span></span> <span data-ttu-id="5c033-116">既定では、特定の型のデータ コントラクトには、その型の共通言語ランタイム (CLR: Common Language Runtime) 名前空間に基づく名前空間が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="5c033-116">By default, data contracts for a particular type are assigned a namespace that comes from the common language runtime (CLR) namespace of that type.</span></span>

<span data-ttu-id="5c033-117">既定では、指定された CLR 名前空間 ( *clr. namespace*の形式) は、名前空間にマップされ `http://schemas.datacontract.org/2004/07/Clr.Namespace` ます。</span><span class="sxs-lookup"><span data-stu-id="5c033-117">By default, any given CLR namespace (in the format *Clr.Namespace*) is mapped to the namespace `http://schemas.datacontract.org/2004/07/Clr.Namespace`.</span></span> <span data-ttu-id="5c033-118">この既定をオーバーライドするには、<xref:System.Runtime.Serialization.ContractNamespaceAttribute> 属性をモジュールまたはアセンブリ全体に適用します。</span><span class="sxs-lookup"><span data-stu-id="5c033-118">To override this default, apply the <xref:System.Runtime.Serialization.ContractNamespaceAttribute> attribute to the entire module or assembly.</span></span> <span data-ttu-id="5c033-119">また、型ごとにデータ コントラクト名前空間を制御するには、<xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> の <xref:System.Runtime.Serialization.DataContractAttribute> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="5c033-119">Alternatively, to control the data contract namespace for each type, set the <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> property of the <xref:System.Runtime.Serialization.DataContractAttribute>.</span></span>

> [!NOTE]
> <span data-ttu-id="5c033-120">`http://schemas.microsoft.com/2003/10/Serialization`名前空間は予約されており、データコントラクトの名前空間として使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="5c033-120">The `http://schemas.microsoft.com/2003/10/Serialization` namespace is reserved and cannot be used as a data contract namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="5c033-121">`delegate` 宣言を含むデータ コントラクト型では、既定の名前空間をオーバーライドすることはできません。</span><span class="sxs-lookup"><span data-stu-id="5c033-121">You cannot override the default namespace in data contract types that contain `delegate` declarations.</span></span>

## <a name="data-contract-names"></a><span data-ttu-id="5c033-122">データ コントラクト名</span><span class="sxs-lookup"><span data-stu-id="5c033-122">Data Contract Names</span></span>
<span data-ttu-id="5c033-123">ある型のデータ コントラクトの既定の名前は、その型の名前になります。</span><span class="sxs-lookup"><span data-stu-id="5c033-123">The default name of a data contract for a given type is the name of that type.</span></span> <span data-ttu-id="5c033-124">この既定をオーバーライドするには、<xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> の <xref:System.Runtime.Serialization.DataContractAttribute> プロパティを別の名前に設定します。</span><span class="sxs-lookup"><span data-stu-id="5c033-124">To override the default, set the <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> property of the <xref:System.Runtime.Serialization.DataContractAttribute> to an alternative name.</span></span> <span data-ttu-id="5c033-125">ジェネリック型に関する特別な規則については、このトピックで後述される「ジェネリック型のデータ コントラクト名」で説明します。</span><span class="sxs-lookup"><span data-stu-id="5c033-125">Special rules for generic types are described in "Data Contract Names for Generic Types" later in this topic.</span></span>

## <a name="data-member-names"></a><span data-ttu-id="5c033-126">データ メンバー名</span><span class="sxs-lookup"><span data-stu-id="5c033-126">Data Member Names</span></span>
<span data-ttu-id="5c033-127">フィールドまたはプロパティのデータ メンバーの既定の名前は、そのフィールドまたはプロパティの名前になります。</span><span class="sxs-lookup"><span data-stu-id="5c033-127">The default name of a data member for a given field or property is the name of that field or property.</span></span> <span data-ttu-id="5c033-128">この既定をオーバーライドするには、<xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> の <xref:System.Runtime.Serialization.DataMemberAttribute> プロパティを別の値に設定します。</span><span class="sxs-lookup"><span data-stu-id="5c033-128">To override the default, set the <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> to an alternative value.</span></span>

### <a name="examples"></a><span data-ttu-id="5c033-129">使用例</span><span class="sxs-lookup"><span data-stu-id="5c033-129">Examples</span></span>
<span data-ttu-id="5c033-130">次の例では、データ コントラクトおよびデータ メンバーの既定の名前付け動作をオーバーライドする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5c033-130">The following example shows how you can override the default naming behavior of data contracts and data members.</span></span>

[!code-csharp[C_DataContractNames#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#1)]
[!code-vb[C_DataContractNames#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#1)]

## <a name="data-contract-names-for-generic-types"></a><span data-ttu-id="5c033-131">ジェネリック型のデータ コントラクト名</span><span class="sxs-lookup"><span data-stu-id="5c033-131">Data Contract Names for Generic Types</span></span>
<span data-ttu-id="5c033-132">ジェネリック型のデータ コントラクト名を決定する場合は、特別な規則があります。</span><span class="sxs-lookup"><span data-stu-id="5c033-132">Special rules exist for determining data contract names for generic types.</span></span> <span data-ttu-id="5c033-133">これらの規則は、同じジェネリック型の 2 つのクローズ ジェネリックの間でデータ コントラクト名の競合を回避するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="5c033-133">These rules help avoid data contract name collisions between two closed generics of the same generic type.</span></span>

<span data-ttu-id="5c033-134">既定では、ジェネリック型のデータコントラクト名は型の名前になり、その後に文字列 "Of" が続き、その後にジェネリックパラメーターのデータコントラクト名が続き、その後にジェネリックパラメーターのデータコントラクト名前空間を使用して計算された*ハッシュ*が続きます。</span><span class="sxs-lookup"><span data-stu-id="5c033-134">By default, the data contract name for a generic type is the name of the type, followed by the string "Of", followed by the data contract names of the generic parameters, followed by a *hash* computed using the data contract namespaces of the generic parameters.</span></span> <span data-ttu-id="5c033-135">ハッシュとは、1 つのデータを一意に識別するための "フィンガープリント" として機能する、数学関数の結果です。</span><span class="sxs-lookup"><span data-stu-id="5c033-135">A hash is the result of a mathematical function that acts as a "fingerprint" that uniquely identifies a piece of data.</span></span> <span data-ttu-id="5c033-136">ジェネリック パラメーターがすべてプリミティブ型の場合は、ハッシュは省略されます。</span><span class="sxs-lookup"><span data-stu-id="5c033-136">When all of the generic parameters are primitive types, the hash is omitted.</span></span>

<span data-ttu-id="5c033-137">たとえば、次の例の型を見てください。</span><span class="sxs-lookup"><span data-stu-id="5c033-137">For example, see the types in the following example.</span></span>

[!code-csharp[C_DataContractNames#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#2)]
[!code-vb[C_DataContractNames#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#2)]

<span data-ttu-id="5c033-138">この例では、`Drawing<Square,RegularRedBrush>` 型は "DrawingOfSquareRedBrush5HWGAU6h" というデータ コントラクト名を持ちます。ここで "5HWGAU6h" は "urn:shapes" および "urn:default" 名前空間のハッシュになります。</span><span class="sxs-lookup"><span data-stu-id="5c033-138">In this example, the type `Drawing<Square,RegularRedBrush>` has the data contract name "DrawingOfSquareRedBrush5HWGAU6h", where "5HWGAU6h" is a hash of the "urn:shapes" and "urn:default" namespaces.</span></span> <span data-ttu-id="5c033-139">`Drawing<Square,SpecialRedBrush>` 型は "DrawingOfSquareRedBrushjpB5LgQ_S" というデータ コントラクト名を持ちます。ここで "jpB5LgQ_S" は "urn:shapes" および "urn:special" 名前空間のハッシュになります。</span><span class="sxs-lookup"><span data-stu-id="5c033-139">The type `Drawing<Square,SpecialRedBrush>` has the data contract name "DrawingOfSquareRedBrushjpB5LgQ_S", where "jpB5LgQ_S" is a hash of the "urn:shapes" and the "urn:special" namespaces.</span></span> <span data-ttu-id="5c033-140">ハッシュを使用しないと 2 つの名前は同一になり、名前の競合が発生することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5c033-140">Note that if the hash is not used, the two names are identical, and thus a name collision occurs.</span></span>

## <a name="customizing-data-contract-names-for-generic-types"></a><span data-ttu-id="5c033-141">ジェネリック型のデータコントラクト名のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="5c033-141">Customizing data contract names for generic types</span></span>

<span data-ttu-id="5c033-142">前述のようにジェネリック型用に生成されたデータ コントラクト名を容認できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="5c033-142">Sometimes, the data contract names generated for generic types, as described previously, are unacceptable.</span></span> <span data-ttu-id="5c033-143">たとえば、名前の競合が起こらないことが前もってわかっているため、ハッシュを削除するとします。</span><span class="sxs-lookup"><span data-stu-id="5c033-143">For example, you may know in advance that you will not run into name collisions and may want to remove the hash.</span></span> <span data-ttu-id="5c033-144">この場合、プロパティを使用して、 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A?displayProperty=nameWithType> 名前を生成する別の方法を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5c033-144">In this case, you can use the <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A?displayProperty=nameWithType> property to specify a different way to generate names.</span></span> <span data-ttu-id="5c033-145">`Name` プロパティの中かっこ内に数字を指定して、ジェネリック パラメーターのデータ コントラクト名を参照できます </span><span class="sxs-lookup"><span data-stu-id="5c033-145">You can use numbers in curly braces inside of the `Name` property to refer to data contract names of the generic parameters.</span></span> <span data-ttu-id="5c033-146">(0 は最初のパラメーターを示し、1は2番目のパラメーターを表します)。ハッシュを参照するには、中かっこ内にシャープ記号 (#) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="5c033-146">(0 refers to the first parameter, 1 refers to the second, and so on.) You can use a number (#) sign inside curly braces to refer to the hash.</span></span> <span data-ttu-id="5c033-147">これらの各参照は、複数回使用しても、まったく使用しなくてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="5c033-147">You can use each of these references multiple times or not at all.</span></span>

<span data-ttu-id="5c033-148">たとえば、前の `Drawing` ジェネリック型は次の例に示すように宣言できます。</span><span class="sxs-lookup"><span data-stu-id="5c033-148">For example, the preceding generic `Drawing` type could have been declared as shown in the following example.</span></span>

[!code-csharp[c_DataContractNames#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#3)]
[!code-vb[c_DataContractNames#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#3)]

<span data-ttu-id="5c033-149">この場合、`Drawing<Square,RegularRedBrush>` 型は、"Drawing_using_RedBrush_brush_and_Square_shape" というデータ コントラクト名になります。</span><span class="sxs-lookup"><span data-stu-id="5c033-149">In this case, the type `Drawing<Square,RegularRedBrush>` has the data contract name "Drawing_using_RedBrush_brush_and_Square_shape".</span></span> <span data-ttu-id="5c033-150"><xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> プロパティに "{#}" があるため、名前にはハッシュは含まれません。したがって、この型では名前の競合が発生しやすくなります。たとえば、`Drawing<Square,SpecialRedBrush>` 型は、まったく同じデータ コントラクト名を持ちます。</span><span class="sxs-lookup"><span data-stu-id="5c033-150">Note that because there is a "{#}" in the <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> property, the hash is not a part of the name, and thus the type is susceptible to naming collisions; for example, the type `Drawing<Square,SpecialRedBrush>` would have exactly the same data contract name.</span></span>

## <a name="see-also"></a><span data-ttu-id="5c033-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="5c033-151">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.ContractNamespaceAttribute>
- [<span data-ttu-id="5c033-152">データ コントラクトの使用</span><span class="sxs-lookup"><span data-stu-id="5c033-152">Using Data Contracts</span></span>](using-data-contracts.md)
- [<span data-ttu-id="5c033-153">データ コントラクトの等価性</span><span class="sxs-lookup"><span data-stu-id="5c033-153">Data Contract Equivalence</span></span>](data-contract-equivalence.md)
- [<span data-ttu-id="5c033-154">データ コントラクト名</span><span class="sxs-lookup"><span data-stu-id="5c033-154">Data Contract Names</span></span>](data-contract-names.md)
- [<span data-ttu-id="5c033-155">データ コントラクトのバージョン管理</span><span class="sxs-lookup"><span data-stu-id="5c033-155">Data Contract Versioning</span></span>](data-contract-versioning.md)
