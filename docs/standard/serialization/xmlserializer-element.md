---
title: <xmlSerializer> 要素
description: <xmlSerializer> 要素は、XmlSerializer の進行状況の追加チェックを行うかどうかを指定します。
ms.date: 03/30/2017
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
ms.openlocfilehash: 667d59f7eb0d1c7682afcdda584cc5b0ca2da802
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2020
ms.locfileid: "84288928"
---
# <a name="xmlserializer-element"></a><span data-ttu-id="2eb1b-103">\<xmlSerializer> 要素</span><span class="sxs-lookup"><span data-stu-id="2eb1b-103">\<xmlSerializer> Element</span></span>
<span data-ttu-id="2eb1b-104"><xref:System.Xml.Serialization.XmlSerializer> の進行状況の追加チェックを行うかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="2eb1b-104">Specifies whether an additional check of progress of the <xref:System.Xml.Serialization.XmlSerializer> is done.</span></span>  
  
 \<configuration>  
\<system.xml.serialization>  
  
## <a name="syntax"></a><span data-ttu-id="2eb1b-105">構文</span><span class="sxs-lookup"><span data-stu-id="2eb1b-105">Syntax</span></span>  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2eb1b-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="2eb1b-106">Attributes and Elements</span></span>  
 <span data-ttu-id="2eb1b-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="2eb1b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2eb1b-108">属性</span><span class="sxs-lookup"><span data-stu-id="2eb1b-108">Attributes</span></span>  
  
|<span data-ttu-id="2eb1b-109">属性</span><span class="sxs-lookup"><span data-stu-id="2eb1b-109">Attribute</span></span>|<span data-ttu-id="2eb1b-110">説明</span><span class="sxs-lookup"><span data-stu-id="2eb1b-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2eb1b-111">**checkDeserializeAdvances**</span><span class="sxs-lookup"><span data-stu-id="2eb1b-111">**checkDeserializeAdvances**</span></span>|<span data-ttu-id="2eb1b-112"><xref:System.Xml.Serialization.XmlSerializer> の進行状況をチェックするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="2eb1b-112">Specifies whether the progress of the <xref:System.Xml.Serialization.XmlSerializer> is checked.</span></span> <span data-ttu-id="2eb1b-113">属性は "true" または "false" に設定します。</span><span class="sxs-lookup"><span data-stu-id="2eb1b-113">Set the attribute to "true" or "false".</span></span> <span data-ttu-id="2eb1b-114">既定値は "true" です。</span><span class="sxs-lookup"><span data-stu-id="2eb1b-114">The default is "true".</span></span>|  
|<span data-ttu-id="2eb1b-115">**useLegacySerializationGeneration**</span><span class="sxs-lookup"><span data-stu-id="2eb1b-115">**useLegacySerializationGeneration**</span></span>|<span data-ttu-id="2eb1b-116">C# コードをファイルに記述し、それをアセンブリにコンパイルすることによってアセンブリを生成する従来のシリアル化の生成を、<xref:System.Xml.Serialization.XmlSerializer> で使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="2eb1b-116">Specifies whether the <xref:System.Xml.Serialization.XmlSerializer> uses legacy serialization generation which generates assemblies by writing C# code to a file and then compiling it to an assembly.</span></span> <span data-ttu-id="2eb1b-117">既定値は **false** です。</span><span class="sxs-lookup"><span data-stu-id="2eb1b-117">The default is **false**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2eb1b-118">子要素</span><span class="sxs-lookup"><span data-stu-id="2eb1b-118">Child Elements</span></span>  
 <span data-ttu-id="2eb1b-119">なし。</span><span class="sxs-lookup"><span data-stu-id="2eb1b-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2eb1b-120">親要素</span><span class="sxs-lookup"><span data-stu-id="2eb1b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2eb1b-121">要素</span><span class="sxs-lookup"><span data-stu-id="2eb1b-121">Element</span></span>|<span data-ttu-id="2eb1b-122">説明</span><span class="sxs-lookup"><span data-stu-id="2eb1b-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2eb1b-123">\<system.xml.serialization> 要素</span><span class="sxs-lookup"><span data-stu-id="2eb1b-123">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)|<span data-ttu-id="2eb1b-124"><xref:System.Xml.Serialization.XmlSerializer> クラスおよび <xref:System.Xml.Serialization.XmlSchemaImporter> クラスの構成設定を含みます。</span><span class="sxs-lookup"><span data-stu-id="2eb1b-124">Contains configuration settings for the <xref:System.Xml.Serialization.XmlSerializer> and <xref:System.Xml.Serialization.XmlSchemaImporter> classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2eb1b-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="2eb1b-125">Remarks</span></span>  
 <span data-ttu-id="2eb1b-126">既定では、<xref:System.Xml.Serialization.XmlSerializer> は、信頼できないデータを逆シリアル化する際に、サービス拒否攻撃の可能性に対するセキュリティをさらに高めることができます。</span><span class="sxs-lookup"><span data-stu-id="2eb1b-126">By default, the <xref:System.Xml.Serialization.XmlSerializer> provides an additional layer of security against potential denial of service attacks when deserializing untrusted data.</span></span> <span data-ttu-id="2eb1b-127">これは、逆シリアル化中に無限ループを検出することにより行われます。</span><span class="sxs-lookup"><span data-stu-id="2eb1b-127">It does so by attempting to detect infinite loops during deserialization.</span></span> <span data-ttu-id="2eb1b-128">このような状態が検出されると、例外がスローされ、次のメッセージが表示されます。"内部エラー: 基になるストリームで逆シリアル化を継続できませんでした。"</span><span class="sxs-lookup"><span data-stu-id="2eb1b-128">If such a condition is detected, an exception is thrown with the following message: "Internal error: deserialization failed to advance over underlying stream."</span></span>  
  
 <span data-ttu-id="2eb1b-129">このメッセージは、必ずしもサービス拒否攻撃を受けていることを示すわけではありません。</span><span class="sxs-lookup"><span data-stu-id="2eb1b-129">Receiving this message does not necessarily indicate that a denial of service attack is in progress.</span></span> <span data-ttu-id="2eb1b-130">まれに、無限ループ検出機構で誤検出が発生し、適正な受信メッセージに対して例外がスローされる場合があります。</span><span class="sxs-lookup"><span data-stu-id="2eb1b-130">In some rare circumstances, the infinite loop detection mechanism produces a false positive and the exception is thrown for a legitimate incoming message.</span></span> <span data-ttu-id="2eb1b-131">特定のアプリケーションにおいて、セキュリティの強化によって適正なメッセージが拒否される場合は、**checkDeserializeAdvances** 属性を "false" に設定します。</span><span class="sxs-lookup"><span data-stu-id="2eb1b-131">If you find that in your particular application legitimate messages are being rejected by this extra layer of protection, set **checkDeserializeAdvances** attribute to "false".</span></span>  
  
## <a name="example"></a><span data-ttu-id="2eb1b-132">例</span><span class="sxs-lookup"><span data-stu-id="2eb1b-132">Example</span></span>  
 <span data-ttu-id="2eb1b-133">**checkDeserializeAdvances** 属性を "false" に設定するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="2eb1b-133">The following code example sets the **checkDeserializeAdvances** attribute to "false".</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2eb1b-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="2eb1b-134">See also</span></span>

- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="2eb1b-135">\<system.xml.serialization> 要素</span><span class="sxs-lookup"><span data-stu-id="2eb1b-135">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
- [<span data-ttu-id="2eb1b-136">XML シリアル化および SOAP シリアル化</span><span class="sxs-lookup"><span data-stu-id="2eb1b-136">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
