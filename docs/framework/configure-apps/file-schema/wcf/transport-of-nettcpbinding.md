---
title: <transport> の <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 8f752373c51992c51b747f5f4dc4a63910a387c6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162193"
---
# <a name="transport-of-nettcpbinding"></a><span data-ttu-id="7a0e1-102">\<transport> の \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="7a0e1-102">\<transport> of \<netTcpBinding></span></span>

<span data-ttu-id="7a0e1-103">で構成されるエンドポイントのメッセージレベルのセキュリティ要件の種類を定義し [\<netTcpBinding>](nettcpbinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](nettcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="7a0e1-104">構文</span><span class="sxs-lookup"><span data-stu-id="7a0e1-104">Syntax</span></span>  
  
```xml  
<netTcpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential">
      <transport clientCredentialType="None|Windows|Certificate"
                 protectionLevel="None|Sign|EncryptAndSign"
                 sslProtocols="Tls|Tls11|Tls12">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a0e1-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="7a0e1-105">Attributes and Elements</span></span>  

 <span data-ttu-id="7a0e1-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a0e1-107">属性</span><span class="sxs-lookup"><span data-stu-id="7a0e1-107">Attributes</span></span>  
  
|<span data-ttu-id="7a0e1-108">属性</span><span class="sxs-lookup"><span data-stu-id="7a0e1-108">Attribute</span></span>|<span data-ttu-id="7a0e1-109">[説明]</span><span class="sxs-lookup"><span data-stu-id="7a0e1-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7a0e1-110">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="7a0e1-110">clientCredentialType</span></span>|<span data-ttu-id="7a0e1-111">省略可能。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-111">Optional.</span></span> <span data-ttu-id="7a0e1-112">トランスポート セキュリティを使用してクライアント認証を実行するときに使用される資格情報の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-112">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="7a0e1-113">-既定値は `Windows` です。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-113">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="7a0e1-114">-この属性の型は <xref:System.ServiceModel.TcpClientCredentialType> です。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-114">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="7a0e1-115">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="7a0e1-115">protectionLevel</span></span>|<span data-ttu-id="7a0e1-116">省略可能。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-116">Optional.</span></span> <span data-ttu-id="7a0e1-117">TCP トランスポートのレベルでセキュリティを定義します。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-117">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="7a0e1-118">メッセージに署名を付けることで、メッセージの転送中に第三者によって改ざんされるリスクが軽減されます。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="7a0e1-119">暗号化によって、トランスポート中にデータ レベルのプライバシーが提供されます。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-119">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="7a0e1-120">既定値は `EncryptAndSign` です。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-120">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="7a0e1-121">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="7a0e1-121">sslProtocols</span></span>|<span data-ttu-id="7a0e1-122">どの SslProtocols がサポートされているのかを指定する SslProtocols 列挙型フラグの値。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-122">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="7a0e1-123">既定値は Tls&#124;Tls11&#124;Tls12 です。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-123">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="7a0e1-124">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="7a0e1-124">policyEnforcement</span></span>|<span data-ttu-id="7a0e1-125">この列挙体は、<xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> を適用するタイミングを指定します。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-125">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="7a0e1-126">1. never –ポリシーは適用されません (拡張保護は無効になります)。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-126">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="7a0e1-127">2. WhenSupported –ポリシーは、クライアントが拡張保護をサポートしている場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-127">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="7a0e1-128">3. always –ポリシーは常に適用されます。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-128">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="7a0e1-129">拡張保護をサポートしていないクライアントは認証に失敗します。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-129">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="7a0e1-130">clientCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="7a0e1-130">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="7a0e1-131">値</span><span class="sxs-lookup"><span data-stu-id="7a0e1-131">Value</span></span>|<span data-ttu-id="7a0e1-132">説明</span><span class="sxs-lookup"><span data-stu-id="7a0e1-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7a0e1-133">None</span><span class="sxs-lookup"><span data-stu-id="7a0e1-133">None</span></span>|<span data-ttu-id="7a0e1-134">クライアントは匿名です。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-134">The client is anonymous.</span></span> <span data-ttu-id="7a0e1-135">これには、サービスの証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-135">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="7a0e1-136">Windows</span><span class="sxs-lookup"><span data-stu-id="7a0e1-136">Windows</span></span>|<span data-ttu-id="7a0e1-137">SP ネゴシエーション (Kerberos ネゴシエーション) を使用して、クライアントの Windows 認証を指定します。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-137">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="7a0e1-138">Certificate</span><span class="sxs-lookup"><span data-stu-id="7a0e1-138">Certificate</span></span>|<span data-ttu-id="7a0e1-139">クライアントは、証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-139">The client is authenticated using a certificate.</span></span> <span data-ttu-id="7a0e1-140">これは SSL ネゴシエーションを使用し、サービスの証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-140">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="7a0e1-141">protectionLevel 属性</span><span class="sxs-lookup"><span data-stu-id="7a0e1-141">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="7a0e1-142">値</span><span class="sxs-lookup"><span data-stu-id="7a0e1-142">Value</span></span>|<span data-ttu-id="7a0e1-143">説明</span><span class="sxs-lookup"><span data-stu-id="7a0e1-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7a0e1-144">None</span><span class="sxs-lookup"><span data-stu-id="7a0e1-144">None</span></span>|<span data-ttu-id="7a0e1-145">保護されません。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-145">No protection.</span></span>|  
|<span data-ttu-id="7a0e1-146">署名</span><span class="sxs-lookup"><span data-stu-id="7a0e1-146">Sign</span></span>|<span data-ttu-id="7a0e1-147">メッセージは署名されます。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-147">Messages are signed.</span></span>|  
|<span data-ttu-id="7a0e1-148">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="7a0e1-148">EncryptAndSign</span></span>|<span data-ttu-id="7a0e1-149">-メッセージは暗号化され、署名されます。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-149">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7a0e1-150">子要素</span><span class="sxs-lookup"><span data-stu-id="7a0e1-150">Child Elements</span></span>  

 <span data-ttu-id="7a0e1-151">None</span><span class="sxs-lookup"><span data-stu-id="7a0e1-151">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7a0e1-152">親要素</span><span class="sxs-lookup"><span data-stu-id="7a0e1-152">Parent Elements</span></span>  
  
|<span data-ttu-id="7a0e1-153">要素</span><span class="sxs-lookup"><span data-stu-id="7a0e1-153">Element</span></span>|<span data-ttu-id="7a0e1-154">説明</span><span class="sxs-lookup"><span data-stu-id="7a0e1-154">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|<span data-ttu-id="7a0e1-155">のセキュリティ機能を指定し [\<netTcpBinding>](nettcpbinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-155">Specifies the security capabilities of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a0e1-156">解説</span><span class="sxs-lookup"><span data-stu-id="7a0e1-156">Remarks</span></span>  

 <span data-ttu-id="7a0e1-157">トランスポート セキュリティは、SOAP メッセージの整合性と機密性の保護、および相互認証に使用します。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-157">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="7a0e1-158">このセキュリティ モードがバインディング上で選択された場合、チャネル スタックはセキュリティ トランスポートを使用して構成され、SOAP メッセージは Windows (ネゴシエート) や TCP 上の SSL などのトランスポート セキュリティを使用して保護されます。</span><span class="sxs-lookup"><span data-stu-id="7a0e1-158">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a0e1-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a0e1-159">See also</span></span>

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="7a0e1-160">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="7a0e1-160">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="7a0e1-161">バインド</span><span class="sxs-lookup"><span data-stu-id="7a0e1-161">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7a0e1-162">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="7a0e1-162">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7a0e1-163">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="7a0e1-163">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
