---
title: <cryptographySettings> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptographySettings
helpviewer_keywords:
- cryptographySettings element
- <cryptographySettings> element
ms.assetid: 6201b7da-bcb7-49f7-b9f5-ba1fe05573b9
ms.openlocfilehash: ca0a9a4b37f28eb03f58de4fd9b120cb7e654e0c
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088642"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="24b1f-102">\<cryptographySettings > 要素</span><span class="sxs-lookup"><span data-stu-id="24b1f-102">\<cryptographySettings> Element</span></span>
<span data-ttu-id="24b1f-103">暗号設定を含みます。</span><span class="sxs-lookup"><span data-stu-id="24b1f-103">Contains cryptography settings.</span></span>  

<span data-ttu-id="24b1f-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="24b1f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="24b1f-105">&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="24b1f-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="24b1f-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<cryptographySettings >**</span><span class="sxs-lookup"><span data-stu-id="24b1f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptographySettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="24b1f-107">構文</span><span class="sxs-lookup"><span data-stu-id="24b1f-107">Syntax</span></span>  
  
```xml  
      <cryptographySettings>   
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24b1f-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="24b1f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="24b1f-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="24b1f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24b1f-110">属性</span><span class="sxs-lookup"><span data-stu-id="24b1f-110">Attributes</span></span>  
 <span data-ttu-id="24b1f-111">なし。</span><span class="sxs-lookup"><span data-stu-id="24b1f-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="24b1f-112">子要素</span><span class="sxs-lookup"><span data-stu-id="24b1f-112">Child Elements</span></span>  
  
|<span data-ttu-id="24b1f-113">要素</span><span class="sxs-lookup"><span data-stu-id="24b1f-113">Element</span></span>|<span data-ttu-id="24b1f-114">説明</span><span class="sxs-lookup"><span data-stu-id="24b1f-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24b1f-115">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="24b1f-115">\<cryptoNameMapping></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="24b1f-116">表示名へのクラスのマッピングを含みます。</span><span class="sxs-lookup"><span data-stu-id="24b1f-116">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="24b1f-117">\<oidMap ></span><span class="sxs-lookup"><span data-stu-id="24b1f-117">\<oidMap></span></span>](oidmap-element.md)|<span data-ttu-id="24b1f-118">クラスに対する asn.1 オブジェクト識別子 (OID) マッピングが含まれています。</span><span class="sxs-lookup"><span data-stu-id="24b1f-118">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="24b1f-119">親要素</span><span class="sxs-lookup"><span data-stu-id="24b1f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="24b1f-120">要素</span><span class="sxs-lookup"><span data-stu-id="24b1f-120">Element</span></span>|<span data-ttu-id="24b1f-121">説明</span><span class="sxs-lookup"><span data-stu-id="24b1f-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="24b1f-122">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="24b1f-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="24b1f-123">`cryptographySettings` 要素を格納します。</span><span class="sxs-lookup"><span data-stu-id="24b1f-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="24b1f-124">例</span><span class="sxs-lookup"><span data-stu-id="24b1f-124">Example</span></span>  
 <span data-ttu-id="24b1f-125">次の例では、 **\<cryptographySettings >** 要素を使用して、暗号化名マッピングと OID マッピングを含める方法を示します。</span><span class="sxs-lookup"><span data-stu-id="24b1f-125">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="24b1f-126">この例では、<xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> が `MyHashClass` オブジェクトを返し、`MyCryptoClass` クラスがオブジェクト識別子1.3.36.2.1 にマップされるようにランタイムを構成します。</span><span class="sxs-lookup"><span data-stu-id="24b1f-126">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyHash="MyHashClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MyHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="24b1f-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="24b1f-127">See also</span></span>

- [<span data-ttu-id="24b1f-128">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="24b1f-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="24b1f-129">暗号化設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="24b1f-129">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="24b1f-130">暗号サービス</span><span class="sxs-lookup"><span data-stu-id="24b1f-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
