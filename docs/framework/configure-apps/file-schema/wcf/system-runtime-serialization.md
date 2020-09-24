---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: 84ced06691ce3b3c9c9573fc9d114335096a849d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157110"
---
# \<system.runtime.serialization>

<span data-ttu-id="e5779-102"><xref:System.Runtime.Serialization> 名前空間セクションのルート要素を表し、<xref:System.Runtime.Serialization.DataContractSerializer> のオプションを設定するための要素を含みます。</span><span class="sxs-lookup"><span data-stu-id="e5779-102">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.runtime.serialization>**  
  
## <a name="syntax"></a><span data-ttu-id="e5779-103">構文</span><span class="sxs-lookup"><span data-stu-id="e5779-103">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer ignoreExtensionDataObject="Boolean"
                            maxItemsInObjectGraph="Integer">
      <declaredTypes>
        <add type="String">
          <knownType type="String">
            <parameter index="Integer" />
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5779-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e5779-104">Attributes and Elements</span></span>  

 <span data-ttu-id="e5779-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e5779-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5779-106">属性</span><span class="sxs-lookup"><span data-stu-id="e5779-106">Attributes</span></span>  

 <span data-ttu-id="e5779-107">なし。</span><span class="sxs-lookup"><span data-stu-id="e5779-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e5779-108">子要素</span><span class="sxs-lookup"><span data-stu-id="e5779-108">Child Elements</span></span>  
  
|<span data-ttu-id="e5779-109">要素</span><span class="sxs-lookup"><span data-stu-id="e5779-109">Element</span></span>|<span data-ttu-id="e5779-110">説明</span><span class="sxs-lookup"><span data-stu-id="e5779-110">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="e5779-111">逆シリアル化時に使用される既知の型の追加を可能にします。</span><span class="sxs-lookup"><span data-stu-id="e5779-111">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e5779-112">親要素</span><span class="sxs-lookup"><span data-stu-id="e5779-112">Parent Elements</span></span>  
  
|<span data-ttu-id="e5779-113">要素</span><span class="sxs-lookup"><span data-stu-id="e5779-113">Element</span></span>|<span data-ttu-id="e5779-114">説明</span><span class="sxs-lookup"><span data-stu-id="e5779-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5779-115">\<configuration> 要素</span><span class="sxs-lookup"><span data-stu-id="e5779-115">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="e5779-116">構成の最上位の要素。</span><span class="sxs-lookup"><span data-stu-id="e5779-116">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e5779-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="e5779-117">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="e5779-118">データ コントラクトの使用</span><span class="sxs-lookup"><span data-stu-id="e5779-118">Using Data Contracts</span></span>](../../../wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="e5779-119">既知のデータ コントラクト型</span><span class="sxs-lookup"><span data-stu-id="e5779-119">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
