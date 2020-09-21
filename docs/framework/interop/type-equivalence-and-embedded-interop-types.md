---
title: 型の等価性と埋め込まれた相互運用機能型
description: マネージド アセンブリを含む .NET の型とメンバーと、そのアセンブリに埋め込まれた COM 型の間の型の等価性を理解します。 .NET 4 以上の場合。
ms.date: 03/30/2017
helpviewer_keywords:
- type equivalence
- embedded interop types
- primary interop assemblies,not necessary in CLR version 4
- NoPIA
ms.assetid: 78892eba-2a58-4165-b4b1-0250ee2f41dc
ms.openlocfilehash: a096c6bd0703c19c6049ad5ab2532b4b05f6ede0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558824"
---
# <a name="type-equivalence-and-embedded-interop-types"></a><span data-ttu-id="52395-104">型の等価性と埋め込まれた相互運用機能型</span><span class="sxs-lookup"><span data-stu-id="52395-104">Type equivalence and embedded interop types</span></span>

<span data-ttu-id="52395-105">.NET Framework 4 以降、共通言語ランタイムでは、マネージド アセンブリに COM 型の型情報を直接埋め込めるようになりました。マネージド アセンブリで相互運用アセンブリから COM 型の型情報を取得する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="52395-105">Beginning with the .NET Framework 4, the common language runtime supports embedding type information for COM types directly into managed assemblies, instead of requiring the managed assemblies to obtain type information for COM types from interop assemblies.</span></span> <span data-ttu-id="52395-106">埋め込まれる型情報にはマネージド アセンブリに実際に使用される型とメンバーのみが含まれるため、2 つのマネージド アセンブリで同じ COM 型の表示が非常に異なることが考えられます。</span><span class="sxs-lookup"><span data-stu-id="52395-106">Because the embedded type information includes only the types and members that are actually used by a managed assembly, two managed assemblies might have very different views of the same COM type.</span></span> <span data-ttu-id="52395-107">マネージド アセンブリごとに、COM 型の表示を表す異なる <xref:System.Type> オブジェクトが与えられます。</span><span class="sxs-lookup"><span data-stu-id="52395-107">Each managed assembly has a different <xref:System.Type> object to represent its view of the COM type.</span></span> <span data-ttu-id="52395-108">共通言語ランタイムでは、インターフェイス、構造、列挙、委任といった異なる表示間で型の等価性が与えられます。</span><span class="sxs-lookup"><span data-stu-id="52395-108">The common language runtime supports type equivalence between these different views for interfaces, structures, enumerations, and delegates.</span></span>

<span data-ttu-id="52395-109">型の等価性とは、マネージド アセンブリ間で渡される COM オブジェクトを受け取り側のアセンブリで適切なマネージド型に変換できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="52395-109">Type equivalence means that a COM object that is passed from one managed assembly to another can be cast to the appropriate managed type in the receiving assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="52395-110">型の等価性と埋め込まれた相互運用機能型により、COM コンポーネントを利用するアプリケーションとアドインの展開が簡単になります。アプリケーションで相互運用アセンブリを展開する必要がないためです。</span><span class="sxs-lookup"><span data-stu-id="52395-110">Type equivalence and embedded interop types simplify the deployment of applications and add-ins that use COM components, because it is not necessary to deploy interop assemblies with the applications.</span></span> <span data-ttu-id="52395-111">ただし、以前のバージョンの .NET Framework でコンポーネントを利用する場合、共有 COM コンポーネントの開発者はプライマリ相互運用アセンブリ (PIA) を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52395-111">Developers of shared COM components still have to create primary interop assemblies (PIAs) if they want their components to be used by earlier versions of the .NET Framework.</span></span>

## <a name="type-equivalence"></a><span data-ttu-id="52395-112">型の等価性</span><span class="sxs-lookup"><span data-stu-id="52395-112">Type equivalence</span></span>

 <span data-ttu-id="52395-113">COM 型の等価性は、インターフェイス、構造、列挙、委任でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="52395-113">Equivalence of COM types is supported for interfaces, structures, enumerations, and delegates.</span></span> <span data-ttu-id="52395-114">COM 型は、次のすべてに該当する場合に等価となります。</span><span class="sxs-lookup"><span data-stu-id="52395-114">COM types qualify as equivalent if all of the following are true:</span></span>

- <span data-ttu-id="52395-115">型がいずれもインターフェイスであるか、いずれも構造であるか、いずれも列挙であるか、いずれも委任である。</span><span class="sxs-lookup"><span data-stu-id="52395-115">The types are both interfaces, or both structures, or both enumerations, or both delegates.</span></span>

- <span data-ttu-id="52395-116">型の ID が同じである (次のセクションに詳細あり)。</span><span class="sxs-lookup"><span data-stu-id="52395-116">The types have the same identity, as described in the next section.</span></span>

- <span data-ttu-id="52395-117">いずれの型も、型の等価性に適合する (「[型の等価性の資格ありとして COM 型を設定する](#marking-com-types-for-type-equivalence)」セクションに詳細あり)。</span><span class="sxs-lookup"><span data-stu-id="52395-117">Both types are eligible for type equivalence, as described in the [Marking COM types for type equivalence](#marking-com-types-for-type-equivalence) section.</span></span>

### <a name="type-identity"></a><span data-ttu-id="52395-118">型の ID</span><span class="sxs-lookup"><span data-stu-id="52395-118">Type identity</span></span>

<span data-ttu-id="52395-119">範囲と ID が一致するとき、言い換えると、それぞれに <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> 属性が含まれ、2 つの属性の <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> プロパティと <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> プロパティが一致する場合、2 つの型の ID が同じであると判断されます。</span><span class="sxs-lookup"><span data-stu-id="52395-119">Two types are determined to have the same identity when their scopes and identities match, in other words, if they each have the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> attribute, and the two attributes have matching <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> and <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> properties.</span></span> <span data-ttu-id="52395-120"><xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> の比較では、大文字と小文字が区別されません。</span><span class="sxs-lookup"><span data-stu-id="52395-120">The comparison for <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> is case-insensitive.</span></span>

<span data-ttu-id="52395-121">型に <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> 属性が含まれない場合、あるいは範囲や識別子を指定しない <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> 属性が型に含まれる場合も、型は次のように等価性適用として考慮されます。</span><span class="sxs-lookup"><span data-stu-id="52395-121">If a type does not have the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> attribute, or if it has a <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> attribute that does not specify scope and identifier, the type can still be considered for equivalence as follows:</span></span>

- <span data-ttu-id="52395-122">インターフェイスの場合、<xref:System.Runtime.InteropServices.GuidAttribute> の値が <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A?displayProperty=nameWithType> プロパティの代わりに使用されます。<xref:System.Type.FullName%2A?displayProperty=nameWithType> プロパティ (つまり、名前空間を含む、型の名前) が <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A?displayProperty=nameWithType> プロパティの代わりに使用されます。</span><span class="sxs-lookup"><span data-stu-id="52395-122">For interfaces, the value of the <xref:System.Runtime.InteropServices.GuidAttribute> is used instead of the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A?displayProperty=nameWithType> property, and the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property (that is, the type name, including the namespace) is used instead of the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A?displayProperty=nameWithType> property.</span></span>

- <span data-ttu-id="52395-123">構造、列挙、委任の場合、含んでいるアセンブリの <xref:System.Runtime.InteropServices.GuidAttribute> が <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> プロパティの代わりに使用されます。<xref:System.Type.FullName%2A?displayProperty=nameWithType> プロパティが <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> プロパティの代わりに使用されます。</span><span class="sxs-lookup"><span data-stu-id="52395-123">For structures, enumerations, and delegates, the <xref:System.Runtime.InteropServices.GuidAttribute> of the containing assembly is used instead of the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> property, and the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property is used instead of the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> property.</span></span>

### <a name="marking-com-types-for-type-equivalence"></a><span data-ttu-id="52395-124">型の等価性に適合するものとして COM 型を設定する</span><span class="sxs-lookup"><span data-stu-id="52395-124">Marking COM types for type equivalence</span></span>

 <span data-ttu-id="52395-125">型の等価性に適合するものとして 2 つの方法で型を設定できます。</span><span class="sxs-lookup"><span data-stu-id="52395-125">You can mark a type as eligible for type equivalence in two ways:</span></span>

- <span data-ttu-id="52395-126">型に <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> 属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="52395-126">Apply the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> attribute to the type.</span></span>

- <span data-ttu-id="52395-127">型を COM インポート型にします。</span><span class="sxs-lookup"><span data-stu-id="52395-127">Make the type a COM import type.</span></span> <span data-ttu-id="52395-128"><xref:System.Runtime.InteropServices.ComImportAttribute> 属性が与えられていると、インターフェイスは COM インポート型となります。</span><span class="sxs-lookup"><span data-stu-id="52395-128">An interface is a COM import type if it has the <xref:System.Runtime.InteropServices.ComImportAttribute> attribute.</span></span> <span data-ttu-id="52395-129">それが定義されているアセンブリに <xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute> 属性が含まれる場合、インターフェイス、構造、列挙、委任は COM インポート型となります。</span><span class="sxs-lookup"><span data-stu-id="52395-129">An interface, structure, enumeration, or delegate is a COM import type if the assembly in which it is defined has the <xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute> attribute.</span></span>

## <a name="see-also"></a><span data-ttu-id="52395-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="52395-130">See also</span></span>

- <xref:System.Type.IsEquivalentTo%2A>
- <span data-ttu-id="52395-131">[マネージド コードでの COM 型の使用](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="52395-131">[Using COM Types in Managed Code](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span></span>
- [<span data-ttu-id="52395-132">タイプ ライブラリのアセンブリとしてのインポート</span><span class="sxs-lookup"><span data-stu-id="52395-132">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
