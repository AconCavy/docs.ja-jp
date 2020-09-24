---
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 1698ce421b4dcefc6ab94206443d2d7bca47aca8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162284"
---
# \<rsa>

<span data-ttu-id="c5504-101">この ID のエンドポイントに接続するセキュリティで保護された WCF クライアントは、サーバーから提示されたクレームに、この ID を構築するために使用された RSA 公開キーを含むクレームが含まれていることを検証します。</span><span class="sxs-lookup"><span data-stu-id="c5504-101">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<rsa>**  
  
## <a name="syntax"></a><span data-ttu-id="c5504-102">構文</span><span class="sxs-lookup"><span data-stu-id="c5504-102">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5504-103">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c5504-103">Attributes and Elements</span></span>  

 <span data-ttu-id="c5504-104">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c5504-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5504-105">属性</span><span class="sxs-lookup"><span data-stu-id="c5504-105">Attributes</span></span>  
  
|<span data-ttu-id="c5504-106">属性</span><span class="sxs-lookup"><span data-stu-id="c5504-106">Attribute</span></span>|<span data-ttu-id="c5504-107">説明</span><span class="sxs-lookup"><span data-stu-id="c5504-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c5504-108">value</span><span class="sxs-lookup"><span data-stu-id="c5504-108">value</span></span>|<span data-ttu-id="c5504-109">省略可能な文字列。</span><span class="sxs-lookup"><span data-stu-id="c5504-109">Optional String.</span></span> <span data-ttu-id="c5504-110">クライアントで比較される RSA 公開キー値。</span><span class="sxs-lookup"><span data-stu-id="c5504-110">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5504-111">子要素</span><span class="sxs-lookup"><span data-stu-id="c5504-111">Child Elements</span></span>  

 <span data-ttu-id="c5504-112">None</span><span class="sxs-lookup"><span data-stu-id="c5504-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5504-113">親要素</span><span class="sxs-lookup"><span data-stu-id="c5504-113">Parent Elements</span></span>  
  
|<span data-ttu-id="c5504-114">要素</span><span class="sxs-lookup"><span data-stu-id="c5504-114">Element</span></span>|<span data-ttu-id="c5504-115">説明</span><span class="sxs-lookup"><span data-stu-id="c5504-115">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="c5504-116">クライアントで認証するサービスの ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="c5504-116">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5504-117">解説</span><span class="sxs-lookup"><span data-stu-id="c5504-117">Remarks</span></span>  

 <span data-ttu-id="c5504-118">RSA チェックを行うと、その RSA キーまたは生成された独自の RSA キー値に基づいて、単一の証明書の認証を明確に制限できます。</span><span class="sxs-lookup"><span data-stu-id="c5504-118">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="c5504-119">これにより、RSA キーが変更された場合に既存のクライアントで使用できなくなるサービスを犠牲にして、特定の RSA キーをより厳しく認証できます。</span><span class="sxs-lookup"><span data-stu-id="c5504-119">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="c5504-120">Id を使用してクライアントに対するサービスを検証する方法の詳細については、「 [サービス id と認証](../../../wcf/feature-details/service-identity-and-authentication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5504-120">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5504-121">例</span><span class="sxs-lookup"><span data-stu-id="c5504-121">Example</span></span>  

 <span data-ttu-id="c5504-122">次の構成コードは、サーバーの認証に使用される X.509 証明書の公開キー値を指定します。</span><span class="sxs-lookup"><span data-stu-id="c5504-122">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="c5504-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5504-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="c5504-124">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="c5504-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
