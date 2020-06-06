---
title: schemeSettings の <add> 要素 (Uri 設定)
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: ed40098e8d4c2d1298771e67a618b8d04f59c912
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087714"
---
# <a name="add-element-for-schemesettings-uri-settings"></a><span data-ttu-id="3c893-102">schemeSettings の \<add> 要素 (Uri 設定)</span><span class="sxs-lookup"><span data-stu-id="3c893-102">\<add> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="3c893-103">スキーム名のスキーム設定を追加します。</span><span class="sxs-lookup"><span data-stu-id="3c893-103">Adds a scheme setting for a scheme name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="3c893-104">構文</span><span class="sxs-lookup"><span data-stu-id="3c893-104">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c893-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="3c893-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3c893-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="3c893-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c893-107">属性</span><span class="sxs-lookup"><span data-stu-id="3c893-107">Attributes</span></span>  
  
|<span data-ttu-id="3c893-108">属性</span><span class="sxs-lookup"><span data-stu-id="3c893-108">Attribute</span></span>|<span data-ttu-id="3c893-109">説明</span><span class="sxs-lookup"><span data-stu-id="3c893-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3c893-110">name</span><span class="sxs-lookup"><span data-stu-id="3c893-110">name</span></span>|<span data-ttu-id="3c893-111">この設定を適用するスキーム名。</span><span class="sxs-lookup"><span data-stu-id="3c893-111">The scheme name for which this setting applies.</span></span> <span data-ttu-id="3c893-112">サポートされている値は、name = "http" と name = "https" だけです。</span><span class="sxs-lookup"><span data-stu-id="3c893-112">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="3c893-113">{属性名}属性</span><span class="sxs-lookup"><span data-stu-id="3c893-113">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="3c893-114">値</span><span class="sxs-lookup"><span data-stu-id="3c893-114">Value</span></span>|<span data-ttu-id="3c893-115">Description</span><span class="sxs-lookup"><span data-stu-id="3c893-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3c893-116">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="3c893-116">genericUriParserOptions</span></span>|<span data-ttu-id="3c893-117">このスキームのパーサーオプション。</span><span class="sxs-lookup"><span data-stu-id="3c893-117">The parser options for this scheme.</span></span> <span data-ttu-id="3c893-118">サポートされている値は、genericUriParserOptions = "DontUnescapePathDotsAndSlashes" だけです。</span><span class="sxs-lookup"><span data-stu-id="3c893-118">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3c893-119">子要素</span><span class="sxs-lookup"><span data-stu-id="3c893-119">Child Elements</span></span>  
 <span data-ttu-id="3c893-120">なし</span><span class="sxs-lookup"><span data-stu-id="3c893-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3c893-121">親要素</span><span class="sxs-lookup"><span data-stu-id="3c893-121">Parent Elements</span></span>  
  
|<span data-ttu-id="3c893-122">要素</span><span class="sxs-lookup"><span data-stu-id="3c893-122">Element</span></span>|<span data-ttu-id="3c893-123">Description</span><span class="sxs-lookup"><span data-stu-id="3c893-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3c893-124">\<schemeSettings>要素 (Uri 設定)</span><span class="sxs-lookup"><span data-stu-id="3c893-124">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="3c893-125"><xref:System.Uri> が特定のスキームに解析される方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="3c893-125">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c893-126">解説</span><span class="sxs-lookup"><span data-stu-id="3c893-126">Remarks</span></span>  
 <span data-ttu-id="3c893-127">既定では、 <xref:System.Uri?displayProperty=nameWithType> クラスは、パスの圧縮を実行する前に、エンコードされたパス区切り記号のエスケープを解除します。</span><span class="sxs-lookup"><span data-stu-id="3c893-127">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="3c893-128">これは、次のような攻撃に対するセキュリティメカニズムとして実装されています。</span><span class="sxs-lookup"><span data-stu-id="3c893-128">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="3c893-129">% Encoded 文字を正しく処理しないモジュールにこの URI が渡された場合、サーバーによって次のコマンドが実行される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3c893-129">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="3c893-130">このため、 <xref:System.Uri?displayProperty=nameWithType> クラスはまずパスの区切り記号をエスケープ解除し、次にパスの圧縮を適用します。</span><span class="sxs-lookup"><span data-stu-id="3c893-130">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="3c893-131">上の悪意のある URL をクラスコンストラクターに渡すと、次の URI が生成され <xref:System.Uri?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="3c893-131">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="3c893-132">この既定の動作は、特定のスキームの schemeSettings 構成オプションを使用して、パーセントエンコードされたパス区切り記号のエスケープを解除しないように変更できます。</span><span class="sxs-lookup"><span data-stu-id="3c893-132">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="3c893-133">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="3c893-133">Configuration Files</span></span>  
 <span data-ttu-id="3c893-134">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="3c893-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c893-135">例</span><span class="sxs-lookup"><span data-stu-id="3c893-135">Example</span></span>  
 <span data-ttu-id="3c893-136">次の例は、 <xref:System.Uri> http スキームに対してパーセントでエンコードされたパス区切り記号をエスケープしないようにするために、クラスによって使用される構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="3c893-136">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3c893-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c893-137">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="3c893-138">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="3c893-138">Network Settings Schema</span></span>](index.md)
