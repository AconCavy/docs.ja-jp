---
title: <add> の <schemaImporterExtensions> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 4f47623aa305ae6e98625acc3d199a76e27d2ea5
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159937"
---
# <a name="add-element-for-schemaimporterextensions"></a><span data-ttu-id="50593-102">\<Schema> Terextensions の要素を追加 \<></span><span class="sxs-lookup"><span data-stu-id="50593-102">\<add> Element for \<schemaImporterExtensions></span></span>
<span data-ttu-id="50593-103">XSD 型を .NET Framework 型に対応付けるために、<xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型を追加します。</span><span class="sxs-lookup"><span data-stu-id="50593-103">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET Framework types.</span></span> <span data-ttu-id="50593-104">構成ファイルの詳細については、「[構成ファイル スキーマ](../../../docs/framework/configure-apps/file-schema/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50593-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="50593-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="50593-105">\<configuration></span></span>  
<span data-ttu-id="50593-106">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="50593-106">\<system.xml.serialization></span></span>  
<span data-ttu-id="50593-107">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="50593-107">\<schemaImporterExtensions></span></span>  
<span data-ttu-id="50593-108">\<add></span><span class="sxs-lookup"><span data-stu-id="50593-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50593-109">構文</span><span class="sxs-lookup"><span data-stu-id="50593-109">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50593-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="50593-110">Attributes and Elements</span></span>  
 <span data-ttu-id="50593-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="50593-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50593-112">属性</span><span class="sxs-lookup"><span data-stu-id="50593-112">Attributes</span></span>  
  
|<span data-ttu-id="50593-113">Attribute</span><span class="sxs-lookup"><span data-stu-id="50593-113">Attribute</span></span>|<span data-ttu-id="50593-114">Description</span><span class="sxs-lookup"><span data-stu-id="50593-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="50593-115">**name**</span><span class="sxs-lookup"><span data-stu-id="50593-115">**name**</span></span>|<span data-ttu-id="50593-116">インスタンスの検索に使用される簡易名。</span><span class="sxs-lookup"><span data-stu-id="50593-116">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="50593-117">**type**</span><span class="sxs-lookup"><span data-stu-id="50593-117">**type**</span></span>|<span data-ttu-id="50593-118">必須。</span><span class="sxs-lookup"><span data-stu-id="50593-118">Required.</span></span> <span data-ttu-id="50593-119">追加するスキーマ拡張クラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="50593-119">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="50593-120">**type** 属性の値は 1 行で指定し、完全修飾型名を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="50593-120">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="50593-121">アセンブリをグローバル アセンブリ キャッシュ (GAC: Global Assembly Cache) に配置する場合は、バージョン、カルチャ、およびアセンブリの署名に使用した公開キーのトークンも含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="50593-121">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="50593-122">子要素</span><span class="sxs-lookup"><span data-stu-id="50593-122">Child Elements</span></span>  
 <span data-ttu-id="50593-123">[なし] :</span><span class="sxs-lookup"><span data-stu-id="50593-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="50593-124">親要素</span><span class="sxs-lookup"><span data-stu-id="50593-124">Parent Elements</span></span>  
  
|<span data-ttu-id="50593-125">要素</span><span class="sxs-lookup"><span data-stu-id="50593-125">Element</span></span>|<span data-ttu-id="50593-126">Description</span><span class="sxs-lookup"><span data-stu-id="50593-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50593-127">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="50593-127">\<schemaImporterExtensions></span></span>|<span data-ttu-id="50593-128"><xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型が含まれます。</span><span class="sxs-lookup"><span data-stu-id="50593-128">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="50593-129">例</span><span class="sxs-lookup"><span data-stu-id="50593-129">Example</span></span>  
 <span data-ttu-id="50593-130">型を対応付けるときに XmlSchemaImporter が使用できる拡張の型を追加するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="50593-130">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <schemaImporterExtensions>  
       <add name="contoso" type="System.Web.Mobile.MobileCapabilities,
       System.Web.Mobile, Version=2.0.0.0, Culture=neutral,
       PublicKeyToken=b03f5f7f11d50a3a" />
    </schemaImporterExtensions>  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="50593-131">参照</span><span class="sxs-lookup"><span data-stu-id="50593-131">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- [<span data-ttu-id="50593-132">\<system.xml.serialization> 要素</span><span class="sxs-lookup"><span data-stu-id="50593-132">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [<span data-ttu-id="50593-133">\<schemaImporterExtensions> 要素</span><span class="sxs-lookup"><span data-stu-id="50593-133">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
