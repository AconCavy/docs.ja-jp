---
title: 暗号設定の <mscorlib> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib
helpviewer_keywords:
- mscorlib element
- <mscorlib> element
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
ms.openlocfilehash: d1d805f7154c18dba2dcd4eb7228cc200d8da811
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155182"
---
# <a name="mscorlib-element-for-cryptography-settings"></a><span data-ttu-id="6059c-102">\<暗号化設定の mscorlib>要素</span><span class="sxs-lookup"><span data-stu-id="6059c-102">\<mscorlib> Element for Cryptography Settings</span></span>
<span data-ttu-id="6059c-103">要素の[\<設定>暗号化](cryptographysettings-element.md)が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6059c-103">Contains the [\<cryptographySettings> element](cryptographysettings-element.md).</span></span>  
  
[<span data-ttu-id="6059c-104">**\<構成>**</span><span class="sxs-lookup"><span data-stu-id="6059c-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="6059c-105">&nbsp;&nbsp;**\<>**</span><span class="sxs-lookup"><span data-stu-id="6059c-105">&nbsp;&nbsp;**\<mscorlib>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6059c-106">構文</span><span class="sxs-lookup"><span data-stu-id="6059c-106">Syntax</span></span>  
  
```xml  
      <mscorlib>
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6059c-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="6059c-107">Attributes and Elements</span></span>  
 <span data-ttu-id="6059c-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6059c-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6059c-109">属性</span><span class="sxs-lookup"><span data-stu-id="6059c-109">Attributes</span></span>  
 <span data-ttu-id="6059c-110">[なし] :</span><span class="sxs-lookup"><span data-stu-id="6059c-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6059c-111">子要素</span><span class="sxs-lookup"><span data-stu-id="6059c-111">Child Elements</span></span>  
  
|<span data-ttu-id="6059c-112">要素</span><span class="sxs-lookup"><span data-stu-id="6059c-112">Element</span></span>|<span data-ttu-id="6059c-113">説明</span><span class="sxs-lookup"><span data-stu-id="6059c-113">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="6059c-114">暗号設定を含みます。</span><span class="sxs-lookup"><span data-stu-id="6059c-114">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6059c-115">親要素</span><span class="sxs-lookup"><span data-stu-id="6059c-115">Parent Elements</span></span>  
  
|<span data-ttu-id="6059c-116">要素</span><span class="sxs-lookup"><span data-stu-id="6059c-116">Element</span></span>|<span data-ttu-id="6059c-117">説明</span><span class="sxs-lookup"><span data-stu-id="6059c-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6059c-118">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="6059c-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6059c-119">例</span><span class="sxs-lookup"><span data-stu-id="6059c-119">Example</span></span>  
 <span data-ttu-id="6059c-120">次の例では**\<、mscorlib>** 要素を使用して暗号化クラスを参照し、ランタイムを構成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6059c-120">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="6059c-121">その後、<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>メソッドに文字列 "RSA" を渡し、<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>メソッドを使用して`MyCryptoRSAClass`オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="6059c-121">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6059c-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="6059c-122">See also</span></span>

- <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>
- <xref:System.Security.Cryptography>
- [<span data-ttu-id="6059c-123">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="6059c-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6059c-124">暗号化設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="6059c-124">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6059c-125">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="6059c-125">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="6059c-126">暗号化クラスの設定</span><span class="sxs-lookup"><span data-stu-id="6059c-126">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
