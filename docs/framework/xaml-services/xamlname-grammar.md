---
title: XamlName の文法
ms.date: 03/30/2017
helpviewer_keywords:
- DottedXamlName grammar [XAML Services]
- grammar [XAML Services], DottedXamlName
- grammar [XAML Services], XamlName
- names in XAML [XAML Services]
- XamlName grammar [XAML Services]
ms.assetid: 11e4cada-41d2-494d-9531-0d3df4dfcbe3
ms.openlocfilehash: a1e7a5a03db4a24ed4d13d62899754cfe9e76b56
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837156"
---
# <a name="xamlname-grammar"></a><span data-ttu-id="0e284-102">XamlName の文法</span><span class="sxs-lookup"><span data-stu-id="0e284-102">XamlName Grammar</span></span>
<span data-ttu-id="0e284-103">XamlName 文法は、XAML 言語仕様 (MS XAML) で定義されている特定の文法です。これは便宜上、ここで再現します。</span><span class="sxs-lookup"><span data-stu-id="0e284-103">XamlName Grammar is a specific grammar that is defined in the XAML language specification [MS-XAML], which is reproduced here for convenience.</span></span>  
  
## <a name="from-the-xaml-specification"></a><span data-ttu-id="0e284-104">XAML 仕様から</span><span class="sxs-lookup"><span data-stu-id="0e284-104">From the XAML Specification</span></span>  
 <span data-ttu-id="0e284-105">[XamlName 仕様は、型とプロパティに使用される一連の有効なシンボル識別子を識別する文法を定義します。</span><span class="sxs-lookup"><span data-stu-id="0e284-105">The [MS-XAML] specification defines the grammar XamlName to identify the set of legal symbolic identifiers used for types and properties.</span></span>  
  
 <span data-ttu-id="0e284-106">XamlName 型の文字列値は、次の文法に準拠している必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e284-106">String values that are of type XamlName must conform to the following grammar:</span></span>  
  
```xaml  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 <span data-ttu-id="0e284-107">Unicode 文字データベースで定義されている次の一般的なカテゴリ値を前提としています。</span><span class="sxs-lookup"><span data-stu-id="0e284-107">Which assumes the following general category values as defined in the Unicode Character Database</span></span>  

| <span data-ttu-id="0e284-108">Unicode カテゴリ</span><span class="sxs-lookup"><span data-stu-id="0e284-108">Unicode category</span></span>   | <span data-ttu-id="0e284-109">説明</span><span class="sxs-lookup"><span data-stu-id="0e284-109">Description</span></span>                   |
|--------------------|-------------------------------|
| <span data-ttu-id="0e284-110">Lu</span><span class="sxs-lookup"><span data-stu-id="0e284-110">Lu</span></span>                 | <span data-ttu-id="0e284-111">Letter, Uppercase (字、大文字)</span><span class="sxs-lookup"><span data-stu-id="0e284-111">Letter, Uppercase</span></span>             |
| <span data-ttu-id="0e284-112">Ll</span><span class="sxs-lookup"><span data-stu-id="0e284-112">Ll</span></span>                 | <span data-ttu-id="0e284-113">Letter, Lowercase (字、小文字)</span><span class="sxs-lookup"><span data-stu-id="0e284-113">Letter, Lowercase</span></span>             |
| <span data-ttu-id="0e284-114">Lt</span><span class="sxs-lookup"><span data-stu-id="0e284-114">Lt</span></span>                 | <span data-ttu-id="0e284-115">Letter, Titlecase (字、タイトル文字)</span><span class="sxs-lookup"><span data-stu-id="0e284-115">Letter, Titlecase</span></span>             |
| <span data-ttu-id="0e284-116">Lm</span><span class="sxs-lookup"><span data-stu-id="0e284-116">Lm</span></span>                 | <span data-ttu-id="0e284-117">Letter, Modifier (字、修飾)</span><span class="sxs-lookup"><span data-stu-id="0e284-117">Letter, Modifier</span></span>              |
| <span data-ttu-id="0e284-118">Lo</span><span class="sxs-lookup"><span data-stu-id="0e284-118">Lo</span></span>                 | <span data-ttu-id="0e284-119">Letter, Other (字、その他)</span><span class="sxs-lookup"><span data-stu-id="0e284-119">Letter, Other</span></span>                 |
| <span data-ttu-id="0e284-120">Mn</span><span class="sxs-lookup"><span data-stu-id="0e284-120">Mn</span></span>                 | <span data-ttu-id="0e284-121">マーク (スペースなし)</span><span class="sxs-lookup"><span data-stu-id="0e284-121">Mark, Non-Spacing</span></span>             |
| <span data-ttu-id="0e284-122">Mc</span><span class="sxs-lookup"><span data-stu-id="0e284-122">Mc</span></span>                 | <span data-ttu-id="0e284-123">Mark, Spacing Combining (結合文字、幅あり)</span><span class="sxs-lookup"><span data-stu-id="0e284-123">Mark, Spacing Combining</span></span>       |
| <span data-ttu-id="0e284-124">Nd</span><span class="sxs-lookup"><span data-stu-id="0e284-124">Nd</span></span>                 | <span data-ttu-id="0e284-125">Number、Decimal</span><span class="sxs-lookup"><span data-stu-id="0e284-125">Number, Decimal</span></span>               |
| <span data-ttu-id="0e284-126">Nl</span><span class="sxs-lookup"><span data-stu-id="0e284-126">Nl</span></span>                 | <span data-ttu-id="0e284-127">Number, Letter (数、字)</span><span class="sxs-lookup"><span data-stu-id="0e284-127">Number, Letter</span></span>                |
 
 <span data-ttu-id="0e284-128">XAML は、プロパティおよびイベント修飾参照に使用される2番目の文法、DottedXamlName、およびアタッチされたメンバーに対しても定義します。</span><span class="sxs-lookup"><span data-stu-id="0e284-128">XAML defines a second grammar, DottedXamlName, that is used for property and event qualified references, and also for attached members.</span></span> <span data-ttu-id="0e284-129">詳細については、「<xref:System.Windows.DependencyProperty> と[XAML の概要 (WPF)](../../desktop-wpf/fundamentals/xaml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0e284-129">For more information, see <xref:System.Windows.DependencyProperty> and [XAML Overview (WPF)](../../desktop-wpf/fundamentals/xaml.md).</span></span>  
  
 <span data-ttu-id="0e284-130">DottedXamlName 型の文字列値は、次の文法に準拠している必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e284-130">String values that are of type DottedXamlName must conform to the following grammar:</span></span>  
  
```xaml  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a><span data-ttu-id="0e284-131">Remarks</span><span class="sxs-lookup"><span data-stu-id="0e284-131">Remarks</span></span>  
 <span data-ttu-id="0e284-132">完全な仕様については、「 [\[の\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0e284-132">For the complete specification, see [\[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>
