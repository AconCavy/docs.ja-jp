---
title: <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
ms.openlocfilehash: 118159617a7f4c27ecc5e8fe077c28cfefac8537
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397615"
---
# \<peerAuthentication>
<span data-ttu-id="3a6b1-101">ピア ノードで使用されるピア証明書の認証設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-101">Specifies authentication settings for a peer certificate used by a peer node.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="3a6b1-102">構文</span><span class="sxs-lookup"><span data-stu-id="3a6b1-102">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a6b1-103">属性および要素</span><span class="sxs-lookup"><span data-stu-id="3a6b1-103">Attributes and Elements</span></span>  
 <span data-ttu-id="3a6b1-104">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a6b1-105">属性</span><span class="sxs-lookup"><span data-stu-id="3a6b1-105">Attributes</span></span>  
  
|<span data-ttu-id="3a6b1-106">属性</span><span class="sxs-lookup"><span data-stu-id="3a6b1-106">Attribute</span></span>|<span data-ttu-id="3a6b1-107">説明</span><span class="sxs-lookup"><span data-stu-id="3a6b1-107">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="3a6b1-108">省略可能な列挙体です。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-108">Optional enumeration.</span></span> <span data-ttu-id="3a6b1-109">資格情報の検証に使用される 3 つのモードのいずれかを指定します。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-109">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="3a6b1-110">この属性は <xref:System.ServiceModel.Security.X509CertificateValidationMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-110">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="3a6b1-111">`Custom` に設定されている場合、`customCertificateValidator` も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-111">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="3a6b1-112">省略可能な文字列。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-112">Optional string.</span></span> <span data-ttu-id="3a6b1-113">ユーザー設定タイプの検証に使用されるタイプおよびアセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-113">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="3a6b1-114">`certificateValidationMode` が `Custom` に設定されている場合は、この属性を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-114">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="3a6b1-115">この属性は <xref:System.IdentityModel.Selectors.X509CertificateValidator> 型です。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-115">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="3a6b1-116">Windows Communication Foundation (WCF) は、信頼された people ストアに対してピア証明書を検証する既定のピア証明書検証コントロールを提供します。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-116">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="3a6b1-117">証明書が有効なルートまでつながっていることを検証します。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-117">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="3a6b1-118">カスタム検証を実装して別の動作を指定したり、この属性を使用してカスタム検証を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-118">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="3a6b1-119">省略可能な列挙体です。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-119">Optional enumeration.</span></span> <span data-ttu-id="3a6b1-120">証明書失効モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-120">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="3a6b1-121">この属性は <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-121">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="3a6b1-122">システムは、ピア証明書を失効証明書リストで検索して、それが失効していないことを検証します。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-122">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="3a6b1-123">このチェックは、オンラインで、またはキャッシュされた失効リストをチェックする方法で実行されます。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-123">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="3a6b1-124">失効チェックは、この属性を NoCheck に設定することにより無効にできます。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-124">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="3a6b1-125">省略可能な列挙体です。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-125">Optional enumeration.</span></span> <span data-ttu-id="3a6b1-126">WCF セキュリティシステムによってピア証明書が検証される、信頼されたストアの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-126">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="3a6b1-127">この属性は <xref:System.Security.Cryptography.X509Certificates.StoreLocation> 型です。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-127">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a6b1-128">子要素</span><span class="sxs-lookup"><span data-stu-id="3a6b1-128">Child Elements</span></span>  
 <span data-ttu-id="3a6b1-129">なし。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3a6b1-130">親要素</span><span class="sxs-lookup"><span data-stu-id="3a6b1-130">Parent Elements</span></span>  
  
|<span data-ttu-id="3a6b1-131">要素</span><span class="sxs-lookup"><span data-stu-id="3a6b1-131">Element</span></span>|<span data-ttu-id="3a6b1-132">Description</span><span class="sxs-lookup"><span data-stu-id="3a6b1-132">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="3a6b1-133">ピア ノードの現在の資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-133">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a6b1-134">解説</span><span class="sxs-lookup"><span data-stu-id="3a6b1-134">Remarks</span></span>  
 <span data-ttu-id="3a6b1-135">`<authentication>` 要素は、<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> クラスに対応します。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-135">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="3a6b1-136">この要素は、メッシュ内の近隣ノード間の認証時に呼び出される検証コントロールを指定します。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-136">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="3a6b1-137">新しいピアが近隣ノードとの接続を確立しようとするとき、自身の資格情報を応答側のピアに渡します。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-137">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="3a6b1-138">リモート パーティの資格情報を検証するために、応答側の検証が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-138">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="3a6b1-139">メッシュ内でピア接続が確立されるたびに、両方のピアが相互に認証されます。つまり、双方の検証が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3a6b1-139">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a6b1-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="3a6b1-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="3a6b1-141">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="3a6b1-141">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="3a6b1-142">ピアツーピア ネットワーク</span><span class="sxs-lookup"><span data-stu-id="3a6b1-142">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="3a6b1-143">[ピア チャネル メッセージの認証](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3a6b1-143">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="3a6b1-144">[ピア チャネル カスタム認証](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3a6b1-144">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="3a6b1-145">セキュリティによるピア チャネル アプリケーションの保護</span><span class="sxs-lookup"><span data-stu-id="3a6b1-145">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
