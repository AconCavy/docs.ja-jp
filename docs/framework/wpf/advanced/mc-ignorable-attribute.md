---
title: mc:Ignorable 属性
ms.date: 03/30/2017
helpviewer_keywords:
- mc XML namespace prefix [WPF]
- mc:Ignorable attribute
- XML [WPF], mc namespace prefix
- XAML [WPF], mc:Ignorable attribute
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: acd9a6ef-b7ca-4146-abb6-60f3b366e9ec
ms.openlocfilehash: d8fdeec8784c9a44c9b272a0a5a8b9c56ace5230
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458819"
---
# <a name="mcignorable-attribute"></a><span data-ttu-id="60ad7-102">mc:Ignorable 属性</span><span class="sxs-lookup"><span data-stu-id="60ad7-102">mc:Ignorable Attribute</span></span>
<span data-ttu-id="60ad7-103">マークアップファイルで検出された [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 名前空間プレフィックスが [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサによって無視される可能性があるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="60ad7-103">Specifies which [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefixes encountered in a markup file may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="60ad7-104">`mc:Ignorable` 属性は、カスタム名前空間マッピングと [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] バージョン管理の両方で、マークアップ互換性をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="60ad7-104">The `mc:Ignorable` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage-single-prefix"></a><span data-ttu-id="60ad7-105">XAML 属性の使用法 (単一のプレフィックス)</span><span class="sxs-lookup"><span data-stu-id="60ad7-105">XAML Attribute Usage (Single Prefix)</span></span>  
  
```xaml  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a><span data-ttu-id="60ad7-106">XAML 属性の使用法 (2 つのプレフィックス)</span><span class="sxs-lookup"><span data-stu-id="60ad7-106">XAML Attribute Usage (Two Prefixes)</span></span>  
  
```xaml  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="60ad7-107">XAML 値</span><span class="sxs-lookup"><span data-stu-id="60ad7-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="60ad7-108">*ignorablePrefix、ignorablePrefix1、その他*</span><span class="sxs-lookup"><span data-stu-id="60ad7-108">*ignorablePrefix, ignorablePrefix1, etc.*</span></span>|<span data-ttu-id="60ad7-109">XML 1.0 仕様に従って、任意の有効なプレフィックス文字列。</span><span class="sxs-lookup"><span data-stu-id="60ad7-109">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="60ad7-110">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="60ad7-110">*ignorableUri*</span></span>|<span data-ttu-id="60ad7-111">XML 1.0 仕様に従って、名前空間を指定するための任意の有効な URI。</span><span class="sxs-lookup"><span data-stu-id="60ad7-111">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="60ad7-112">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="60ad7-112">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="60ad7-113">基になる型を解決できない場合に [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] のプロセッサ実装によって無視される要素。</span><span class="sxs-lookup"><span data-stu-id="60ad7-113">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60ad7-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="60ad7-114">Remarks</span></span>  
 <span data-ttu-id="60ad7-115">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 互換性名前空間 `http://schemas.openxmlformats.org/markup-compatibility/2006`をマップするときに使用するプレフィックスとして、`mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 名前空間プレフィックスを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="60ad7-115">The `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefix is the recommended prefix convention to use when mapping the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] compatibility namespace `http://schemas.openxmlformats.org/markup-compatibility/2006`.</span></span>  
  
 <span data-ttu-id="60ad7-116">要素名のプレフィックス部分が `mc:Ignorable` として識別される要素または属性は、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサによって処理されるときにエラーを発生させません。</span><span class="sxs-lookup"><span data-stu-id="60ad7-116">Elements or attributes where the prefix portion of the element name are identified as `mc:Ignorable` will not raise errors when processed by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="60ad7-117">その属性を基になる型またはプログラミング構成体に解決できなかった場合、その要素は無視されます。</span><span class="sxs-lookup"><span data-stu-id="60ad7-117">If that attribute could not be resolved to an underlying type or programming construct, then that element is ignored.</span></span> <span data-ttu-id="60ad7-118">ただし、無視された要素では、その要素が処理されないという副作用を伴う追加の要素の要件に対して、追加の解析エラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="60ad7-118">Note however that ignored elements might still generate additional parsing errors for additional element requirements that are side effects of that element not being processed.</span></span> <span data-ttu-id="60ad7-119">たとえば、特定の要素のコンテンツモデルでは、1つの子要素だけが必要になる場合がありますが、指定された子要素が `mc:Ignorable` プレフィックスに含まれていて、指定された子要素が型に解決できなかった場合、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] のプロセッサによってエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="60ad7-119">For instance, a particular element content model might require exactly one child element, but if the specified child element was in an `mc:Ignorable` prefix, and the specified child element could not be resolved to a type, then the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor might raise an error.</span></span>  
  
 <span data-ttu-id="60ad7-120">`mc:Ignorable` は、識別子文字列への名前空間のマッピングにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="60ad7-120">`mc:Ignorable` only applies to namespace mappings to identifier strings.</span></span> <span data-ttu-id="60ad7-121">`mc:Ignorable` は、CLR 名前空間とアセンブリを指定するアセンブリ (または、現在の実行可能ファイルをアセンブリとして既定値として使用するアセンブリ) への名前空間マッピングには適用されません。</span><span class="sxs-lookup"><span data-stu-id="60ad7-121">`mc:Ignorable` does not apply to namespace mappings into assemblies, which specify a CLR namespace and an assembly (or default to the current executable as the assembly).</span></span>  
  
 <span data-ttu-id="60ad7-122">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサを実装する場合、`mc:Ignorable`として識別されたプレフィックスによって修飾された要素または属性の型解決では、プロセッサ実装で解析または処理エラーが発生しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="60ad7-122">If you are implementing a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor, your processor implementation must not raise parsing or processing errors on type resolution for any element or attribute that is qualified by a prefix that is identified as `mc:Ignorable`.</span></span> <span data-ttu-id="60ad7-123">しかし、プロセッサの実装では、前に示した1つの子要素の例のように、要素の読み込みまたは処理に失敗した場合の二次的な結果である例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="60ad7-123">But your processor implementation can still raise exceptions that are a secondary result of an element failing to load or be processed, such as the one-child element example given earlier.</span></span>  
  
 <span data-ttu-id="60ad7-124">既定では、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] のプロセッサは無視された要素内のコンテンツを無視します。</span><span class="sxs-lookup"><span data-stu-id="60ad7-124">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="60ad7-125">ただし、追加の属性である[mc: ProcessContent 属性](mc-processcontent-attribute.md)を指定して、次に使用可能な親要素によって無視された要素内のコンテンツを継続して処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="60ad7-125">However, you can specify an additional attribute, [mc:ProcessContent Attribute](mc-processcontent-attribute.md), to require continued processing of content within an ignored element by the next available parent element.</span></span>  
  
 <span data-ttu-id="60ad7-126">属性では、複数のプレフィックスを指定できます。たとえば、`mc:Ignorable="ignore1 ignore2"`のように、区切り記号として1つ以上の空白文字を使用します。</span><span class="sxs-lookup"><span data-stu-id="60ad7-126">Multiple prefixes can be specified in the attribute, using one or more white-space characters as the separator, for example: `mc:Ignorable="ignore1 ignore2"`.</span></span>  

 <span data-ttu-id="60ad7-127">`http://schemas.openxmlformats.org/markup-compatibility/2006` 名前空間は、SDK のこの領域内には記載されていない他の要素と属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="60ad7-127">The `http://schemas.openxmlformats.org/markup-compatibility/2006` namespace defines other elements and attributes that are not documented within this area of the SDK.</span></span> <span data-ttu-id="60ad7-128">詳細については、「 [XML マークアップ互換性の仕様](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60ad7-128">For more information, see [XML Markup Compatibility Specification](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60ad7-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="60ad7-129">See also</span></span>

- <xref:System.Windows.Markup.XamlReader>
- [<span data-ttu-id="60ad7-130">PresentationOptions:Freeze 属性</span><span class="sxs-lookup"><span data-stu-id="60ad7-130">PresentationOptions:Freeze Attribute</span></span>](presentationoptions-freeze-attribute.md)
- [<span data-ttu-id="60ad7-131">XAML の概要 (WPF)</span><span class="sxs-lookup"><span data-stu-id="60ad7-131">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="60ad7-132">WPF のドキュメント</span><span class="sxs-lookup"><span data-stu-id="60ad7-132">Documents in WPF</span></span>](documents-in-wpf.md)
