---
title: ローカリゼーション属性とコメント
ms.date: 03/30/2017
helpviewer_keywords:
- localization [WPF], attributes
- localization [WPF], comments
ms.assetid: ead2d9ac-b709-4ec1-a924-39927a29d02f
ms.openlocfilehash: 4f9c2700d8163988b7ea1e75bec1427778cf571c
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004894"
---
# <a name="localization-attributes-and-comments"></a><span data-ttu-id="5f641-102">ローカリゼーション属性とコメント</span><span class="sxs-lookup"><span data-stu-id="5f641-102">Localization Attributes and Comments</span></span>
<span data-ttu-id="5f641-103">ローカリゼーションコメント [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、開発者がローカライズに関する規則やヒントを提供するために、XAML ソースコード内のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="5f641-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] localization comments are properties, inside XAML source code, supplied by developers to provide rules and hints for localization.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="5f641-104">ローカリゼーション コメントには、ローカライズ可否属性と自由形式のローカリゼーション コメントの 2 つの情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="5f641-104">localization comments contain two sets of information: localizability attributes and free-form localization comments.</span></span> <span data-ttu-id="5f641-105">ローカライズ可否属性は、ローカライズするリソースを示すために [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ローカリゼーション API によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="5f641-105">Localizability attributes are used by the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Localization API to indicate which resources are to be localized.</span></span> <span data-ttu-id="5f641-106">自由形式のコメントは、アプリケーションの作成者が含めたい任意の情報です。</span><span class="sxs-lookup"><span data-stu-id="5f641-106">Free-form comments are any information that the application author wants to include.</span></span>  

<a name="Localizer_Comments_"></a>   
## <a name="localization-comments"></a><span data-ttu-id="5f641-107">ローカリゼーション コメント</span><span class="sxs-lookup"><span data-stu-id="5f641-107">Localization Comments</span></span>  
 <span data-ttu-id="5f641-108">マークアップアプリケーションの作成者が、テキストの長さ、フォントファミリ、またはフォントサイズの制約など、XAML の特定の要素に関する要件を持つ場合は、XAML コード内のコメントを使用して、この情報をローカライザーに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="5f641-108">If markup application authors have requirements for specific elements in XAML, such as constraints on text length, font family, or font size, they can convey this information to localizers with comments in the XAML code.</span></span> <span data-ttu-id="5f641-109">ソース コードにコメントを追加する手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5f641-109">The process for adding comments to source code is as follows:</span></span>  
  
1. <span data-ttu-id="5f641-110">アプリケーション開発者は、XAML ソースコードにローカリゼーションコメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="5f641-110">Application developer adds localization comments to XAML source code.</span></span>  
  
2. <span data-ttu-id="5f641-111">ビルド プロセス中に、.proj ファイル内でアセンブリ内に自由形式のローカリゼーション コメントを残すかどうか、コメントの一部を取り除くか、またはすべてのコメントを取り除くかのいずれかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="5f641-111">During the build process, you can specify in the .proj file whether to leave the free-form localization comments in the assembly, strip out part of the comments, or strip out all the comments.</span></span> <span data-ttu-id="5f641-112">取り除かれたコメントは、別のファイルに配置されます。</span><span class="sxs-lookup"><span data-stu-id="5f641-112">The stripped-out comments are placed in a separate file.</span></span> <span data-ttu-id="5f641-113">次のような `LocalizationDirectivesToLocFile` タグを使用して、オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="5f641-113">You specify your option using a `LocalizationDirectivesToLocFile` tag, eg:</span></span>  
  
     <span data-ttu-id="5f641-114">`<LocalizationDirectivesToLocFile>` *value* `</LocalizationDirectivesToLocFile>`</span><span class="sxs-lookup"><span data-stu-id="5f641-114">`<LocalizationDirectivesToLocFile>` *value* `</LocalizationDirectivesToLocFile>`</span></span>  
  
3. <span data-ttu-id="5f641-115">割り当てることのできる値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5f641-115">The values that can be assigned are:</span></span>  
  
    - <span data-ttu-id="5f641-116">**None** - コメントと属性の両方がアセンブリ内に残り、別のファイルは生成されません。</span><span class="sxs-lookup"><span data-stu-id="5f641-116">**None** - Both comments and attributes stay inside the assembly and no separate file is generated.</span></span>  
  
    - <span data-ttu-id="5f641-117">**CommentsOnly** - アセンブリからコメントだけを取り除き、別の LocFile に配置します。</span><span class="sxs-lookup"><span data-stu-id="5f641-117">**CommentsOnly** - Strips only the comments from the assembly and places them in the separate LocFile.</span></span>  
  
    - <span data-ttu-id="5f641-118">**All** - コメントと属性の両方をアセンブリから取り除き、両方とも別の 1 つの LocFile に配置します。</span><span class="sxs-lookup"><span data-stu-id="5f641-118">**All** - Strips both the comments and the attributes from the assembly and places them both in a separate LocFile.</span></span>  
  
4. <span data-ttu-id="5f641-119">ローカライズ可能なリソースが BAML から抽出された場合、ローカライズ可能な属性は BAML ローカライズ API によって尊重されます。</span><span class="sxs-lookup"><span data-stu-id="5f641-119">When localizable resources are extracted from BAML, the localizability attributes are respected by the BAML Localization API.</span></span>  
  
5. <span data-ttu-id="5f641-120">自由形式のコメントのみを含むローカリゼーション コメント ファイルは、後でローカライズ プロセスに組み込まれます。</span><span class="sxs-lookup"><span data-stu-id="5f641-120">Localization comment files, containing only free-form comments, are incorporated into the localization process at a later time.</span></span>  
  
 <span data-ttu-id="5f641-121">次の例は、XAML ファイルにローカリゼーションコメントを追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="5f641-121">The following example shows how to add localization comments to a XAML file.</span></span>  
  
 `<TextBlock x:Id = "text01"`  
  
 `FontFamily = "Microsoft Sans Serif"`  
  
 `FontSize = "12"`  
  
 `Localization.Attributes = "$Content (Unmodifiable Readable Text)`  
  
 `FontFamily (Unmodifiable Readable)"`  
  
 `Localization.Comments = "$Content (Trademark)`  
  
 `FontSize (Trademark font size)" >`  
  
 `Microsoft`  
  
 `</TextBlock>`  
  
 <span data-ttu-id="5f641-122">前のサンプル、Localization.Attributes セクションには、ローカリゼーション属性と Localization.Comments セクションの自由形式のコメントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="5f641-122">In the previous sample the Localization.Attributes section contains the localization attributes and the Localization.Comments section the free-form comments.</span></span> <span data-ttu-id="5f641-123">次の表に、属性とコメントおよびローカライザーにとってのそれらの意味を示します。</span><span class="sxs-lookup"><span data-stu-id="5f641-123">The following tables show the attributes and comments and their meaning to the localizer.</span></span>  
  
|<span data-ttu-id="5f641-124">ローカリゼーション属性</span><span class="sxs-lookup"><span data-stu-id="5f641-124">Localization attributes</span></span>|<span data-ttu-id="5f641-125">意味</span><span class="sxs-lookup"><span data-stu-id="5f641-125">Meaning</span></span>|  
|-----------------------------|-------------|  
|<span data-ttu-id="5f641-126">$Content (Unmodifiable Readable Text)</span><span class="sxs-lookup"><span data-stu-id="5f641-126">$Content (Unmodifiable Readable Text)</span></span>|<span data-ttu-id="5f641-127">TextBlock 要素のコンテンツは変更できません。</span><span class="sxs-lookup"><span data-stu-id="5f641-127">Contents of the TextBlock element cannot be modified.</span></span> <span data-ttu-id="5f641-128">ローカライザーは、"Microsoft" という単語を変更できません。</span><span class="sxs-lookup"><span data-stu-id="5f641-128">Localizers cannot change the word "Microsoft".</span></span> <span data-ttu-id="5f641-129">コンテンツは、ローカライザーに表示可能 (読み取り可能) です。</span><span class="sxs-lookup"><span data-stu-id="5f641-129">The content is visible (Readable) to the localizer.</span></span> <span data-ttu-id="5f641-130">コンテンツのカテゴリはテキストです。</span><span class="sxs-lookup"><span data-stu-id="5f641-130">The category of the content is text.</span></span>|  
|<span data-ttu-id="5f641-131">FontFamily (Unmodifiable Readable)</span><span class="sxs-lookup"><span data-stu-id="5f641-131">FontFamily (Unmodifiable Readable)</span></span>|<span data-ttu-id="5f641-132">TextBlock 要素のフォント ファミリ プロパティを変更することはできませんが、ローカライザーに表示することはできます。</span><span class="sxs-lookup"><span data-stu-id="5f641-132">The font family property of the TextBlock element cannot be changed but it is visible to the localizer.</span></span>|  
  
|<span data-ttu-id="5f641-133">自由形式コメントのローカライズ</span><span class="sxs-lookup"><span data-stu-id="5f641-133">Localization free-form comments</span></span>|<span data-ttu-id="5f641-134">意味</span><span class="sxs-lookup"><span data-stu-id="5f641-134">Meaning</span></span>|  
|--------------------------------------|-------------|  
|<span data-ttu-id="5f641-135">$Content (Trademark)</span><span class="sxs-lookup"><span data-stu-id="5f641-135">$Content (Trademark)</span></span>|<span data-ttu-id="5f641-136">アプリケーションの作成者が、TextBlock 要素内のコンテンツが商標であることをローカライザーに伝えます。</span><span class="sxs-lookup"><span data-stu-id="5f641-136">The application author tells the localizer that the content in the TextBlock element is a trademark.</span></span>|  
|<span data-ttu-id="5f641-137">FontSize (Trademark font size)</span><span class="sxs-lookup"><span data-stu-id="5f641-137">FontSize (Trademark font size)</span></span>|<span data-ttu-id="5f641-138">アプリケーションの作成者が、フォント サイズ プロパティが標準の商標のサイズに適切に従う必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="5f641-138">The application author indicates that the font size property should follow the standard trademark size.</span></span>|  
  
### <a name="localizability-attributes"></a><span data-ttu-id="5f641-139">ローカライズ可否属性</span><span class="sxs-lookup"><span data-stu-id="5f641-139">Localizability Attributes</span></span>  
 <span data-ttu-id="5f641-140">Localization.Attributes 内の情報には、ターゲット値の名前と関連付けられているローカライズ可否の値のペアのリストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="5f641-140">The information in Localization.Attributes contains a list of pairs: the targeted value name and the associated localizability values.</span></span> <span data-ttu-id="5f641-141">ターゲット名には、プロパティ名または特殊な $Content 名を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5f641-141">The target name can be a property name or the special $Content name.</span></span> <span data-ttu-id="5f641-142">プロパティ名を指定した場合は、ターゲット値はプロパティの値となります。</span><span class="sxs-lookup"><span data-stu-id="5f641-142">If it is a property name, the targeted value is the value of the property.</span></span> <span data-ttu-id="5f641-143">$Content を指定した場合は、ターゲット値は要素のコンテンツとなります。</span><span class="sxs-lookup"><span data-stu-id="5f641-143">If it is $Content, the target value is the content of the element.</span></span>  
  
 <span data-ttu-id="5f641-144">次の 3 種類の属性があります。</span><span class="sxs-lookup"><span data-stu-id="5f641-144">There are three types of attributes:</span></span>  
  
- <span data-ttu-id="5f641-145">**カテゴリ**。</span><span class="sxs-lookup"><span data-stu-id="5f641-145">**Category**.</span></span> <span data-ttu-id="5f641-146">これは、ローカライザー ツールで値を変更可能にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5f641-146">This specifies whether a value should be modifiable from a localizer tool.</span></span> <span data-ttu-id="5f641-147">「<xref:System.Windows.LocalizabilityAttribute.Category%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f641-147">See <xref:System.Windows.LocalizabilityAttribute.Category%2A>.</span></span>  
  
- <span data-ttu-id="5f641-148">**読みやすさ**。</span><span class="sxs-lookup"><span data-stu-id="5f641-148">**Readability**.</span></span> <span data-ttu-id="5f641-149">これは、ローカライザー ツールで値を読み取る (および表示する) かどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5f641-149">This specifies whether a localizer tool should read (and display) a value.</span></span> <span data-ttu-id="5f641-150">「<xref:System.Windows.LocalizabilityAttribute.Readability%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f641-150">See <xref:System.Windows.LocalizabilityAttribute.Readability%2A>.</span></span>  
  
- <span data-ttu-id="5f641-151">**変更可能性**。</span><span class="sxs-lookup"><span data-stu-id="5f641-151">**Modifiability**.</span></span> <span data-ttu-id="5f641-152">これは、ローカライザー ツールで値の変更を許可するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5f641-152">This specifies whether a localizer tool allows a value to be modified.</span></span> <span data-ttu-id="5f641-153">「<xref:System.Windows.LocalizabilityAttribute.Modifiability%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f641-153">See <xref:System.Windows.LocalizabilityAttribute.Modifiability%2A>.</span></span>  
  
 <span data-ttu-id="5f641-154">これらの属性は、スペースで区切られた任意の順序で指定できます。</span><span class="sxs-lookup"><span data-stu-id="5f641-154">These attributes can be specified in any order delimited by a space.</span></span> <span data-ttu-id="5f641-155">重複する属性が指定された場合、最後の属性にオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="5f641-155">In case duplicate attributes are specified, the last attribute will override former ones.</span></span> <span data-ttu-id="5f641-156">たとえば、Localization.Attributes = "Unmodifiable Modifiable" は、これが最後の値であるため、変更可能性を Modifiable に設定します。</span><span class="sxs-lookup"><span data-stu-id="5f641-156">For example, Localization.Attributes = "Unmodifiable Modifiable" sets Modifiability to Modifiable because it is the last value.</span></span>  
  
 <span data-ttu-id="5f641-157">変更可能性と読みやすさはその名のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5f641-157">Modifiability and Readability are self-explanatory.</span></span> <span data-ttu-id="5f641-158">カテゴリ属性は、テキストを変換するときに、ローカライザーを支援する定義済みのカテゴリを提供します。</span><span class="sxs-lookup"><span data-stu-id="5f641-158">The Category attribute provides predefined categories that help the localizer when translating text.</span></span> <span data-ttu-id="5f641-159">Text、Label、Title などのカテゴリは、テキストの変換方法についてローカライザーに情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5f641-159">Categories, such as, Text, Label, and Title give the localizer information about how to translate the text.</span></span> <span data-ttu-id="5f641-160">None、Inherit、Ignore、NeverLocalize の特殊なカテゴリもあります。</span><span class="sxs-lookup"><span data-stu-id="5f641-160">There are also special categories: None, Inherit, Ignore, and NeverLocalize.</span></span>  
  
 <span data-ttu-id="5f641-161">次の表に、特殊なカテゴリの意味を示します。</span><span class="sxs-lookup"><span data-stu-id="5f641-161">The following table shows the meaning of the special categories.</span></span>  
  
|<span data-ttu-id="5f641-162">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="5f641-162">Category</span></span>|<span data-ttu-id="5f641-163">意味</span><span class="sxs-lookup"><span data-stu-id="5f641-163">Meaning</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="5f641-164">なし</span><span class="sxs-lookup"><span data-stu-id="5f641-164">None</span></span>|<span data-ttu-id="5f641-165">ターゲット値に定義済みのカテゴリがありません。</span><span class="sxs-lookup"><span data-stu-id="5f641-165">Targeted value has no defined category.</span></span>|  
|<span data-ttu-id="5f641-166">[継承する]</span><span class="sxs-lookup"><span data-stu-id="5f641-166">Inherit</span></span>|<span data-ttu-id="5f641-167">ターゲット値は、その親からそのカテゴリを継承します。</span><span class="sxs-lookup"><span data-stu-id="5f641-167">Targeted value inherits its category from its parent.</span></span>|  
|<span data-ttu-id="5f641-168">無視</span><span class="sxs-lookup"><span data-stu-id="5f641-168">Ignore</span></span>|<span data-ttu-id="5f641-169">ローカライズ プロセスでは、ターゲット値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="5f641-169">Targeted value is ignored in the localization process.</span></span> <span data-ttu-id="5f641-170">Ignore は現在の値にのみ影響します。</span><span class="sxs-lookup"><span data-stu-id="5f641-170">Ignore affects only the current value.</span></span> <span data-ttu-id="5f641-171">子ノードには影響しません。</span><span class="sxs-lookup"><span data-stu-id="5f641-171">It will not affect child nodes.</span></span>|  
|<span data-ttu-id="5f641-172">NeverLocalize</span><span class="sxs-lookup"><span data-stu-id="5f641-172">NeverLocalize</span></span>|<span data-ttu-id="5f641-173">現在の値をローカライズすることはできません。</span><span class="sxs-lookup"><span data-stu-id="5f641-173">Current value cannot be localized.</span></span> <span data-ttu-id="5f641-174">このカテゴリは、要素の子に継承されます。</span><span class="sxs-lookup"><span data-stu-id="5f641-174">This category is inherited by the children of an element.</span></span>|  
  
<a name="Localization_Comments"></a>   
## <a name="localization-comments"></a><span data-ttu-id="5f641-175">ローカリゼーション コメント</span><span class="sxs-lookup"><span data-stu-id="5f641-175">Localization Comments</span></span>  
 <span data-ttu-id="5f641-176">Localization.Comments には、ターゲットの値に関する自由形式の文字列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="5f641-176">Localization.Comments contains free-form strings concerning the targeted value.</span></span> <span data-ttu-id="5f641-177">アプリケーション開発者は、アプリケーションのテキストを変換する方法についてのヒントをローカライザーに提供するための情報を追加できます。</span><span class="sxs-lookup"><span data-stu-id="5f641-177">Application developers can add information to give localizers hints about how the applications text should be translated.</span></span> <span data-ttu-id="5f641-178">コメントの形式は、"()" で囲まれた任意の文字列で指定できます。</span><span class="sxs-lookup"><span data-stu-id="5f641-178">The format of the comments can be any string surrounded by "()".</span></span> <span data-ttu-id="5f641-179">文字をエスケープするには、'\\' を使用します。</span><span class="sxs-lookup"><span data-stu-id="5f641-179">Use '\\' to escape characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f641-180">参照</span><span class="sxs-lookup"><span data-stu-id="5f641-180">See also</span></span>

- [<span data-ttu-id="5f641-181">WPF のグローバリゼーション</span><span class="sxs-lookup"><span data-stu-id="5f641-181">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="5f641-182">自動レイアウトを使用してボタンを作成する</span><span class="sxs-lookup"><span data-stu-id="5f641-182">Use Automatic Layout to Create a Button</span></span>](how-to-use-automatic-layout-to-create-a-button.md)
- [<span data-ttu-id="5f641-183">自動レイアウト用のグリッドを使用する</span><span class="sxs-lookup"><span data-stu-id="5f641-183">Use a Grid for Automatic Layout</span></span>](how-to-use-a-grid-for-automatic-layout.md)
- [<span data-ttu-id="5f641-184">アプリケーションをローカライズする</span><span class="sxs-lookup"><span data-stu-id="5f641-184">Localize an Application</span></span>](how-to-localize-an-application.md)
