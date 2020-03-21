---
title: <providerOption> 要素
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
ms.openlocfilehash: c8ba5b9a0680f5e5102c13eb5bb0c1904a168c07
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155402"
---
# <a name="provideroption-element"></a><span data-ttu-id="cec83-102">\<プロバイダーオプション>要素</span><span class="sxs-lookup"><span data-stu-id="cec83-102">\<providerOption> Element</span></span>
<span data-ttu-id="cec83-103">言語プロバイダーのコンパイラ バージョン属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="cec83-103">Specifies the compiler version attributes for a language provider.</span></span>  

<span data-ttu-id="cec83-104">[**\<構成>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cec83-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cec83-105">&nbsp;&nbsp;[**\<コードダム>**](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="cec83-105">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span></span>\
<span data-ttu-id="cec83-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<コンパイラ>**](compilers-element.md)</span><span class="sxs-lookup"><span data-stu-id="cec83-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)</span></span>\
<span data-ttu-id="cec83-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<コンパイラ>**](compiler-element.md)</span><span class="sxs-lookup"><span data-stu-id="cec83-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)</span></span>\
<span data-ttu-id="cec83-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<プロバイダオプション>**</span><span class="sxs-lookup"><span data-stu-id="cec83-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<providerOption>**</span></span>

## <a name="syntax"></a><span data-ttu-id="cec83-109">構文</span><span class="sxs-lookup"><span data-stu-id="cec83-109">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cec83-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="cec83-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cec83-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="cec83-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cec83-112">属性</span><span class="sxs-lookup"><span data-stu-id="cec83-112">Attributes</span></span>  
  
|<span data-ttu-id="cec83-113">属性</span><span class="sxs-lookup"><span data-stu-id="cec83-113">Attribute</span></span>|<span data-ttu-id="cec83-114">説明</span><span class="sxs-lookup"><span data-stu-id="cec83-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="cec83-115">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="cec83-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="cec83-116">オプションの名前を指定します。たとえば、"コンパイラバージョン" を使用します。</span><span class="sxs-lookup"><span data-stu-id="cec83-116">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="cec83-117">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="cec83-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="cec83-118">オプションの値を指定します。たとえば、"v3.5" です。</span><span class="sxs-lookup"><span data-stu-id="cec83-118">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cec83-119">子要素</span><span class="sxs-lookup"><span data-stu-id="cec83-119">Child Elements</span></span>  
 <span data-ttu-id="cec83-120">[なし] :</span><span class="sxs-lookup"><span data-stu-id="cec83-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cec83-121">親要素</span><span class="sxs-lookup"><span data-stu-id="cec83-121">Parent Elements</span></span>  
  
|<span data-ttu-id="cec83-122">要素</span><span class="sxs-lookup"><span data-stu-id="cec83-122">Element</span></span>|<span data-ttu-id="cec83-123">説明</span><span class="sxs-lookup"><span data-stu-id="cec83-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cec83-124">\<要素>構成</span><span class="sxs-lookup"><span data-stu-id="cec83-124">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="cec83-125">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="cec83-125">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="cec83-126">\<要素>コードダム</span><span class="sxs-lookup"><span data-stu-id="cec83-126">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="cec83-127">使用可能な言語プロバイダーのコンパイラ構成設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="cec83-127">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="cec83-128">\<コンパイラは要素></span><span class="sxs-lookup"><span data-stu-id="cec83-128">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="cec83-129">コンパイラ構成要素のコンテナ。0 個以上`<compiler>`の要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="cec83-129">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="cec83-130">\<コンパイラ>要素</span><span class="sxs-lookup"><span data-stu-id="cec83-130">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="cec83-131">言語プロバイダーのコンパイラ構成属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="cec83-131">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cec83-132">解説</span><span class="sxs-lookup"><span data-stu-id="cec83-132">Remarks</span></span>  
 <span data-ttu-id="cec83-133">NET Framework Version 3.5 では、コード ドキュメント オブジェクト モデル (CodeDOM) コード プロバイダーは、`<providerOption>`要素を使用してプロバイダー固有のオプションをサポートできます。</span><span class="sxs-lookup"><span data-stu-id="cec83-133">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="cec83-134">.NET Framework 3.5 には、更新された .NET Framework 2.0 アセンブリが含まれており、新しい型を含む新しいバージョン 3.5 アセンブリが提供されます。</span><span class="sxs-lookup"><span data-stu-id="cec83-134">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="cec83-135">Microsoft C# および Visual Basic のコード プロバイダーは.NET Framework 2.0 アセンブリに含まれていますが、バージョン 3.5 コンパイラをサポートするように更新されました。</span><span class="sxs-lookup"><span data-stu-id="cec83-135">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="cec83-136">既定では、更新されたコード プロバイダーはバージョン 2.0 コンパイラのコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="cec83-136">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="cec83-137">この要素を`<providerOption>`使用して、ターゲットコンパイラのバージョンを 3.5 に変更できます。</span><span class="sxs-lookup"><span data-stu-id="cec83-137">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="cec83-138">これを行うには、`name`属性に 「CompilerVersion」 を指定し、属性に "v3.5" を指定します。 `value`</span><span class="sxs-lookup"><span data-stu-id="cec83-138">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="cec83-139">バージョン番号の前に小文字の "v" を付けなければなりません。</span><span class="sxs-lookup"><span data-stu-id="cec83-139">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="cec83-140">.NET Framework 2.0 Machine.config ファイルまたはルート Web.config ファイルに`<providerOption>`要素を追加することで、バージョン仕様をグローバルにすることができます。</span><span class="sxs-lookup"><span data-stu-id="cec83-140">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="cec83-141">Machine.config ファイルで既定のコンパイラ バージョンを 3.5 に更新する場合は、アプリケーション構成ファイルの`<providerOption>`要素を使用して、アプリケーションごとに 2.0 に戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="cec83-141">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="cec83-142">CodeDOM コード プロバイダーの実装者は、型`providerOptions`<xref:System.Collections.Generic.IDictionary%602>のパラメーターを受け取るコンストラクターを提供することで、カスタム オプションを処理できます。</span><span class="sxs-lookup"><span data-stu-id="cec83-142">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cec83-143">例</span><span class="sxs-lookup"><span data-stu-id="cec83-143">Example</span></span>  
 <span data-ttu-id="cec83-144">C# コード プロバイダーのバージョン 3.5 を使用する必要があるを指定する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="cec83-144">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler  
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,
          Version=2.0.3600.0, Culture=neutral,
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions="/optimize"  
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cec83-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="cec83-145">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="cec83-146">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="cec83-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="cec83-147">\<コンパイラは要素></span><span class="sxs-lookup"><span data-stu-id="cec83-147">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="cec83-148">完全修飾型名の指定</span><span class="sxs-lookup"><span data-stu-id="cec83-148">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="cec83-149">[compilation の compilers の compiler 要素 (ASP.NET 設定スキーマ)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="cec83-149">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
