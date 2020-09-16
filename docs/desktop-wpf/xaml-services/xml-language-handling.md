---
title: XAML における xml:lang の処理
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: 92d1eda62ff394df54d9607bab46d9950681e603
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548209"
---
# <a name="xmllang-handling-in-xaml"></a><span data-ttu-id="b435e-102">XAML における xml:lang の処理</span><span class="sxs-lookup"><span data-stu-id="b435e-102">xml:lang Handling in XAML</span></span>

<span data-ttu-id="b435e-103">`xml:lang`属性は、xml 内の要素の言語およびカルチャ情報を宣言する xml 定義の属性です。</span><span class="sxs-lookup"><span data-stu-id="b435e-103">The `xml:lang` attribute is an XML-defined attribute that declares the language and culture information for an element in XML.</span></span> <span data-ttu-id="b435e-104">属性の意味は XAML でも同じですが、いくつかの追加の考慮事項が適用されます。</span><span class="sxs-lookup"><span data-stu-id="b435e-104">This same meaning of the attribute persists in XAML; however, some additional considerations apply.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="b435e-105">XAML 属性の使用方法</span><span class="sxs-lookup"><span data-stu-id="b435e-105">XAML Attribute Usage</span></span>

```xaml
<object xml:lang="rfc3066lang" />
```

## <a name="xaml-values"></a><span data-ttu-id="b435e-106">XAML 値</span><span class="sxs-lookup"><span data-stu-id="b435e-106">XAML Values</span></span>

|||
|-|-|
|<span data-ttu-id="b435e-107">*rfc3066lang*</span><span class="sxs-lookup"><span data-stu-id="b435e-107">*rfc3066lang*</span></span>|<span data-ttu-id="b435e-108">[RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) 標準で定義されている文字列。1 つの言語、または言語と地域を表します。</span><span class="sxs-lookup"><span data-stu-id="b435e-108">A string that is derived from the [RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) standard and identifies either a language or a language-region.</span></span> <span data-ttu-id="b435e-109">後者の場合は、言語と地域が 1 つのハイフンで区切られます。</span><span class="sxs-lookup"><span data-stu-id="b435e-109">When it is the latter, the language and region are separated by a single hyphen.</span></span> <span data-ttu-id="b435e-110">値と形式の詳細については、「 <xref:System.Windows.Markup.XmlLanguage> 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b435e-110">See <xref:System.Windows.Markup.XmlLanguage> for more information about the values and format.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b435e-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="b435e-111">Remarks</span></span>

<span data-ttu-id="b435e-112">の属性の定義 `xml:lang` は、 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] `xml:lang` XML の World Wide Web コンソーシアム (W3C) によって "特別な属性" として定義されているから派生します。</span><span class="sxs-lookup"><span data-stu-id="b435e-112">The definition for the `xml:lang` attribute in [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] is derived from `xml:lang` as defined as a "special attribute" by the World Wide Web Consortium (W3C) for XML.</span></span> <span data-ttu-id="b435e-113">言語およびカルチャ情報が要素によって処理される方法は、実装に応じて異なる可能性がありますが、 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] における `xml:lang` 属性の既定の処理というものは存在しません。</span><span class="sxs-lookup"><span data-stu-id="b435e-113">Language and culture information is potentially processed in different ways by elements, depending on their implementations; however, there is no default [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processing of the `xml:lang` attribute.</span></span>

<span data-ttu-id="b435e-114">`xml:lang` 属性の既定値は、属性レベルで空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="b435e-114">The default value of the `xml:lang` attribute is an empty string at the attribute level.</span></span>

<span data-ttu-id="b435e-115">`xml:lang` 属性の効果と属性の値が、 `xml:lang` 値を処理するシステムによって解釈される場合、これらの効果と値は、通常、子要素に反映されます。</span><span class="sxs-lookup"><span data-stu-id="b435e-115">The `xml:lang` attribute effects and the value of the attribute are generally perpetuated to child elements, when interpreted by systems that act on `xml:lang` values.</span></span>

<span data-ttu-id="b435e-116">.NET XAML サービスの XAML ライターによって解釈される場合、値は、 `xml:lang` <xref:System.Windows.Markup.XmlLanguage> 基になるオブジェクト表現でまたはオブジェクトを作成できます <xref:System.Globalization.CultureInfo> 。ただし、この動作は、に指定された値 `xml:lang` がこれらのクラスに対して有効な構築であるかどうかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="b435e-116">When interpreted by XAML writers of .NET XAML Services, an `xml:lang` value can create <xref:System.Windows.Markup.XmlLanguage> or <xref:System.Globalization.CultureInfo> objects in the underlying object representation; however, that behavior depends on whether the value specified for `xml:lang` is a valid construction for those classes.</span></span>

<span data-ttu-id="b435e-117">フレームワークは、 `xml:lang` をプロパティに適用することによって、フレームワーク定義プロパティと XML 内の <xref:System.Windows.Markup.XmlLangPropertyAttribute> の意味を関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="b435e-117">Frameworks can create associations between framework-defined properties and the meaning of `xml:lang` in XML by applying <xref:System.Windows.Markup.XmlLangPropertyAttribute> to the property.</span></span>

## <a name="wpf-usage-nodes"></a><span data-ttu-id="b435e-118">WPF の使用上の注意</span><span class="sxs-lookup"><span data-stu-id="b435e-118">WPF Usage Nodes</span></span>

<span data-ttu-id="b435e-119">要素が <xref:System.Windows.FrameworkElement> または <xref:System.Windows.FrameworkContentElement>の派生クラスの場合は、 <xref:System.Windows.FrameworkElement.Language%2A> 属性の代わりに、同等の `xml:lang` 依存関係プロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b435e-119">For elements that are derived classes of <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement>, you can use the equivalent <xref:System.Windows.FrameworkElement.Language%2A> dependency property instead of the `xml:lang` attribute.</span></span> <span data-ttu-id="b435e-120">別途設定されない限り、 <xref:System.Windows.FrameworkElement.Language%2A> プロパティの値は既定で "en-US" となります。このプロパティの値は、このプロパティを通して、または `xml:lang` 属性を処理することによって設定されます。</span><span class="sxs-lookup"><span data-stu-id="b435e-120">By default, the <xref:System.Windows.FrameworkElement.Language%2A> property uses "en-US" if it is not otherwise set, either through the property or through processing the `xml:lang` attribute.</span></span>

## <a name="see-also"></a><span data-ttu-id="b435e-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="b435e-121">See also</span></span>

- [<span data-ttu-id="b435e-122">WPF のグローバリゼーション</span><span class="sxs-lookup"><span data-stu-id="b435e-122">Globalization for WPF</span></span>](/dotnet/desktop/wpf/advanced/globalization-for-wpf)
