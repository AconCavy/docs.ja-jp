---
title: セキュリティ プロトコル
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], protocols
ms.assetid: 57ffcbea-807c-4e43-a41c-44b3db8ed2af
ms.openlocfilehash: 86e0c77b899ad590b9958fea3a050ad0e660bb43
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463787"
---
# <a name="security-protocols"></a><span data-ttu-id="3cbcc-102">セキュリティ プロトコル</span><span class="sxs-lookup"><span data-stu-id="3cbcc-102">Security Protocols</span></span>
<span data-ttu-id="3cbcc-103">Web サービス セキュリティ プロトコルには、既存のエンタープライズ メッセージング セキュリティのあらゆる要件に対応する Web サービス セキュリティ機構が用意されています。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-103">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="3cbcc-104">ここでは、次の Web サービス セキュリティ プロトコルの Windows 通信<xref:System.ServiceModel.Channels.SecurityBindingElement>基盤 (WCF) の詳細 ( で実装) について説明します。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-104">This section describes the Windows Communication Foundation (WCF) details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="3cbcc-105">仕様/ドキュメント</span><span class="sxs-lookup"><span data-stu-id="3cbcc-105">Specification/Document</span></span>|<span data-ttu-id="3cbcc-106">Link</span><span class="sxs-lookup"><span data-stu-id="3cbcc-106">Link</span></span>|  
|-|-|  
|<span data-ttu-id="3cbcc-107">WSS SOAP Message Security 1.0</span><span class="sxs-lookup"><span data-stu-id="3cbcc-107">WSS: SOAP Message Security 1.0</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf|  
|<span data-ttu-id="3cbcc-108">WSS: Username Token Profile 1.0</span><span class="sxs-lookup"><span data-stu-id="3cbcc-108">WSS: Username Token Profile 1.0</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf|  
|<span data-ttu-id="3cbcc-109">WSS: X509 Token Profile 1.0</span><span class="sxs-lookup"><span data-stu-id="3cbcc-109">WSS: X509 Token Profile 1.0</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf|  
|<span data-ttu-id="3cbcc-110">WSS: SAML 1.1 Token Profile 1.0</span><span class="sxs-lookup"><span data-stu-id="3cbcc-110">WSS: SAML 1.1 Token Profile 1.0</span></span>|http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf|  
|<span data-ttu-id="3cbcc-111">WSS SOAP Message Security 1.1</span><span class="sxs-lookup"><span data-stu-id="3cbcc-111">WSS: SOAP Message Security 1.1</span></span>|http://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf|  
|<span data-ttu-id="3cbcc-112">WSS Username Token Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="3cbcc-112">WSS Username Token Profile 1.1</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf|  
|<span data-ttu-id="3cbcc-113">WSS: X.509 Token Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="3cbcc-113">WSS: X.509 Token Profile 1.1</span></span>|http://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf|  
|<span data-ttu-id="3cbcc-114">WSS: Kerberos Token Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="3cbcc-114">WSS: Kerberos Token Profile 1.1</span></span>|http://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf|  
|<span data-ttu-id="3cbcc-115">WSS: SAML 1.1 Token Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="3cbcc-115">WSS: SAML 1.1 Token Profile 1.1</span></span>|http://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf|  
|<span data-ttu-id="3cbcc-116">WS-Secure Conversation 1.3</span><span class="sxs-lookup"><span data-stu-id="3cbcc-116">WS-Secure Conversation 1.3</span></span>|http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512/ws-secureconversation-1.3-os.pdf|  
|<span data-ttu-id="3cbcc-117">WS-Trust 1.3</span><span class="sxs-lookup"><span data-stu-id="3cbcc-117">WS-Trust 1.3</span></span>|http://docs.oasis-open.org/ws-sx/ws-trust/200512/ws-trust-1.3-os.pdf|  
|<span data-ttu-id="3cbcc-118">Application Note:</span><span class="sxs-lookup"><span data-stu-id="3cbcc-118">Application Note:</span></span><br /><br /> <span data-ttu-id="3cbcc-119">Using WS-Trust for TLS Handshake</span><span class="sxs-lookup"><span data-stu-id="3cbcc-119">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="3cbcc-120">公開予定</span><span class="sxs-lookup"><span data-stu-id="3cbcc-120">To be published</span></span>|  
|<span data-ttu-id="3cbcc-121">Application Note:</span><span class="sxs-lookup"><span data-stu-id="3cbcc-121">Application Note:</span></span><br /><br /> <span data-ttu-id="3cbcc-122">Using WS-Trust for SPNEGO</span><span class="sxs-lookup"><span data-stu-id="3cbcc-122">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="3cbcc-123">公開予定</span><span class="sxs-lookup"><span data-stu-id="3cbcc-123">To be published</span></span>|  
|<span data-ttu-id="3cbcc-124">Application Note:</span><span class="sxs-lookup"><span data-stu-id="3cbcc-124">Application Note:</span></span><br /><br /> <span data-ttu-id="3cbcc-125">Web Services Addressing Endpoint References And Identity</span><span class="sxs-lookup"><span data-stu-id="3cbcc-125">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="3cbcc-126">公開予定</span><span class="sxs-lookup"><span data-stu-id="3cbcc-126">To be published</span></span>|  
|<span data-ttu-id="3cbcc-127">WS-SecurityPolicy 1.2 (2007/04)</span><span class="sxs-lookup"><span data-stu-id="3cbcc-127">WS-SecurityPolicy 1.2 (2007/04)</span></span>|http://www.oasis-open.org/committees/download.php/23821/ws-securitypolicy-1.2-spec-cs.pdf|  
  
 <span data-ttu-id="3cbcc-128">WCF バージョン 1 では、Web サービス セキュリティ構成の基礎として使用できる 17 の認証モードを提供します。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-128">WCF, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="3cbcc-129">各モードは、次のような一般的な展開要件について最適化されています。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-129">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
- <span data-ttu-id="3cbcc-130">クライアントとサービスの認証に使用する資格情報</span><span class="sxs-lookup"><span data-stu-id="3cbcc-130">Credentials used to authenticate client and service.</span></span>  
  
- <span data-ttu-id="3cbcc-131">メッセージまたはトランスポートのセキュリティ保護機構</span><span class="sxs-lookup"><span data-stu-id="3cbcc-131">Message or transport security protection mechanisms.</span></span>  
  
- <span data-ttu-id="3cbcc-132">メッセージ交換パターン</span><span class="sxs-lookup"><span data-stu-id="3cbcc-132">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="3cbcc-133">認証モード</span><span class="sxs-lookup"><span data-stu-id="3cbcc-133">Authentication Mode</span></span>|<span data-ttu-id="3cbcc-134">クライアント認証</span><span class="sxs-lookup"><span data-stu-id="3cbcc-134">Client Authentication</span></span>|<span data-ttu-id="3cbcc-135">[サーバー認証]</span><span class="sxs-lookup"><span data-stu-id="3cbcc-135">Server Authentication</span></span>|<span data-ttu-id="3cbcc-136">モード</span><span class="sxs-lookup"><span data-stu-id="3cbcc-136">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="3cbcc-137">UserNameOverTransport</span><span class="sxs-lookup"><span data-stu-id="3cbcc-137">UserNameOverTransport</span></span>|<span data-ttu-id="3cbcc-138">ユーザー名/パスワード</span><span class="sxs-lookup"><span data-stu-id="3cbcc-138">User name/password</span></span>|<span data-ttu-id="3cbcc-139">X509</span><span class="sxs-lookup"><span data-stu-id="3cbcc-139">X509</span></span>|<span data-ttu-id="3cbcc-140">トランスポート</span><span class="sxs-lookup"><span data-stu-id="3cbcc-140">Transport</span></span>|  
|<span data-ttu-id="3cbcc-141">CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="3cbcc-141">CertificateOverTransport</span></span>|<span data-ttu-id="3cbcc-142">X509</span><span class="sxs-lookup"><span data-stu-id="3cbcc-142">X509</span></span>|<span data-ttu-id="3cbcc-143">X509</span><span class="sxs-lookup"><span data-stu-id="3cbcc-143">X509</span></span>|<span data-ttu-id="3cbcc-144">トランスポート</span><span class="sxs-lookup"><span data-stu-id="3cbcc-144">Transport</span></span>|  
|<span data-ttu-id="3cbcc-145">KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="3cbcc-145">KerberosOverTransport</span></span>|<span data-ttu-id="3cbcc-146">Windows</span><span class="sxs-lookup"><span data-stu-id="3cbcc-146">Windows</span></span>|<span data-ttu-id="3cbcc-147">X509</span><span class="sxs-lookup"><span data-stu-id="3cbcc-147">X509</span></span>|<span data-ttu-id="3cbcc-148">トランスポート</span><span class="sxs-lookup"><span data-stu-id="3cbcc-148">Transport</span></span>|  
|<span data-ttu-id="3cbcc-149">IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="3cbcc-149">IssuedTokenOverTransport</span></span>|<span data-ttu-id="3cbcc-150">フェデレーション</span><span class="sxs-lookup"><span data-stu-id="3cbcc-150">Federated</span></span>|<span data-ttu-id="3cbcc-151">X509</span><span class="sxs-lookup"><span data-stu-id="3cbcc-151">X509</span></span>|<span data-ttu-id="3cbcc-152">トランスポート</span><span class="sxs-lookup"><span data-stu-id="3cbcc-152">Transport</span></span>|  
|<span data-ttu-id="3cbcc-153">SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="3cbcc-153">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="3cbcc-154">Windows SSPI ネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="3cbcc-154">Windows Sspi Negotiated</span></span>|<span data-ttu-id="3cbcc-155">Windows SSPI ネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="3cbcc-155">Windows Sspi Negotiated</span></span>|<span data-ttu-id="3cbcc-156">トランスポート</span><span class="sxs-lookup"><span data-stu-id="3cbcc-156">Transport</span></span>|  
|<span data-ttu-id="3cbcc-157">AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="3cbcc-157">AnonymousForCertificate</span></span>|<span data-ttu-id="3cbcc-158">なし</span><span class="sxs-lookup"><span data-stu-id="3cbcc-158">None</span></span>|<span data-ttu-id="3cbcc-159">X509</span><span class="sxs-lookup"><span data-stu-id="3cbcc-159">X509</span></span>|<span data-ttu-id="3cbcc-160">Message</span><span class="sxs-lookup"><span data-stu-id="3cbcc-160">Message</span></span>|  
|<span data-ttu-id="3cbcc-161">UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="3cbcc-161">UserNameForCertificate</span></span>|<span data-ttu-id="3cbcc-162">ユーザー名/パスワード</span><span class="sxs-lookup"><span data-stu-id="3cbcc-162">User name/password</span></span>|<span data-ttu-id="3cbcc-163">X509</span><span class="sxs-lookup"><span data-stu-id="3cbcc-163">X509</span></span>|<span data-ttu-id="3cbcc-164">Message</span><span class="sxs-lookup"><span data-stu-id="3cbcc-164">Message</span></span>|  
|<span data-ttu-id="3cbcc-165">MutualCertificate</span><span class="sxs-lookup"><span data-stu-id="3cbcc-165">MutualCertificate</span></span>|<span data-ttu-id="3cbcc-166">X509</span><span class="sxs-lookup"><span data-stu-id="3cbcc-166">X509</span></span>|<span data-ttu-id="3cbcc-167">X509</span><span class="sxs-lookup"><span data-stu-id="3cbcc-167">X509</span></span>|<span data-ttu-id="3cbcc-168">Message</span><span class="sxs-lookup"><span data-stu-id="3cbcc-168">Message</span></span>|  
|<span data-ttu-id="3cbcc-169">MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="3cbcc-169">MutualCertificateDuplex</span></span>|<span data-ttu-id="3cbcc-170">X509</span><span class="sxs-lookup"><span data-stu-id="3cbcc-170">X509</span></span>|<span data-ttu-id="3cbcc-171">X509</span><span class="sxs-lookup"><span data-stu-id="3cbcc-171">X509</span></span>|<span data-ttu-id="3cbcc-172">Message</span><span class="sxs-lookup"><span data-stu-id="3cbcc-172">Message</span></span>|  
|<span data-ttu-id="3cbcc-173">IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="3cbcc-173">IssuedTokenForCertificate</span></span>|<span data-ttu-id="3cbcc-174">フェデレーション</span><span class="sxs-lookup"><span data-stu-id="3cbcc-174">Federated</span></span>|<span data-ttu-id="3cbcc-175">X509</span><span class="sxs-lookup"><span data-stu-id="3cbcc-175">X509</span></span>|<span data-ttu-id="3cbcc-176">Message</span><span class="sxs-lookup"><span data-stu-id="3cbcc-176">Message</span></span>|  
|<span data-ttu-id="3cbcc-177">Kerberos</span><span class="sxs-lookup"><span data-stu-id="3cbcc-177">Kerberos</span></span>|<span data-ttu-id="3cbcc-178">Windows</span><span class="sxs-lookup"><span data-stu-id="3cbcc-178">Windows</span></span>|<span data-ttu-id="3cbcc-179">Windows</span><span class="sxs-lookup"><span data-stu-id="3cbcc-179">Windows</span></span>|<span data-ttu-id="3cbcc-180">Message</span><span class="sxs-lookup"><span data-stu-id="3cbcc-180">Message</span></span>|  
|<span data-ttu-id="3cbcc-181">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="3cbcc-181">IssuedToken</span></span>|<span data-ttu-id="3cbcc-182">フェデレーション</span><span class="sxs-lookup"><span data-stu-id="3cbcc-182">Federated</span></span>|<span data-ttu-id="3cbcc-183">フェデレーション</span><span class="sxs-lookup"><span data-stu-id="3cbcc-183">Federated</span></span>|<span data-ttu-id="3cbcc-184">Message</span><span class="sxs-lookup"><span data-stu-id="3cbcc-184">Message</span></span>|  
|<span data-ttu-id="3cbcc-185">SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="3cbcc-185">SspiNegotiated</span></span>|<span data-ttu-id="3cbcc-186">Windows SSPI ネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="3cbcc-186">Windows Sspi Negotiated</span></span>|<span data-ttu-id="3cbcc-187">Windows SSPI ネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="3cbcc-187">Windows Sspi Negotiated</span></span>|<span data-ttu-id="3cbcc-188">Message</span><span class="sxs-lookup"><span data-stu-id="3cbcc-188">Message</span></span>|  
|<span data-ttu-id="3cbcc-189">AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="3cbcc-189">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="3cbcc-190">なし</span><span class="sxs-lookup"><span data-stu-id="3cbcc-190">None</span></span>|<span data-ttu-id="3cbcc-191">X509、TLS ネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="3cbcc-191">X509, TLS-Nego</span></span>|<span data-ttu-id="3cbcc-192">Message</span><span class="sxs-lookup"><span data-stu-id="3cbcc-192">Message</span></span>|  
|<span data-ttu-id="3cbcc-193">UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="3cbcc-193">UserNameForSslNegotiated</span></span>|<span data-ttu-id="3cbcc-194">ユーザー名/パスワード</span><span class="sxs-lookup"><span data-stu-id="3cbcc-194">User name/password</span></span>|<span data-ttu-id="3cbcc-195">X509、TLS ネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="3cbcc-195">X509, TLS-Nego</span></span>|<span data-ttu-id="3cbcc-196">Message</span><span class="sxs-lookup"><span data-stu-id="3cbcc-196">Message</span></span>|  
|<span data-ttu-id="3cbcc-197">MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="3cbcc-197">MutualSslNegotiated</span></span>|<span data-ttu-id="3cbcc-198">X509</span><span class="sxs-lookup"><span data-stu-id="3cbcc-198">X509</span></span>|<span data-ttu-id="3cbcc-199">X509、TLS ネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="3cbcc-199">X509, TLS-Nego</span></span>|<span data-ttu-id="3cbcc-200">Message</span><span class="sxs-lookup"><span data-stu-id="3cbcc-200">Message</span></span>|  
|<span data-ttu-id="3cbcc-201">IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="3cbcc-201">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="3cbcc-202">フェデレーション</span><span class="sxs-lookup"><span data-stu-id="3cbcc-202">Federated</span></span>|<span data-ttu-id="3cbcc-203">X509、TLS ネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="3cbcc-203">X509, TLS-Nego</span></span>|<span data-ttu-id="3cbcc-204">Message</span><span class="sxs-lookup"><span data-stu-id="3cbcc-204">Message</span></span>|  
  
 <span data-ttu-id="3cbcc-205">このような認証モードを使用するエンドポイントは、WS-SecurityPolicy (WS-SP) を使用してセキュリティ要件を表現できます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-205">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="3cbcc-206">ここでは、各認証モードのセキュリティ ヘッダーとインフラストラクチャ メッセージの構造について説明します。また、ポリシーとメッセージの例も示します。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-206">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 <span data-ttu-id="3cbcc-207">WCF では WS-SecureConversation を利用して、セキュリティで保護されたセッションのサポートを提供し、アプリケーション間の複数メッセージ交換を保護します。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-207">WCF leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="3cbcc-208">実装の詳細については、後述の「セキュリティで保護されたセッション」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-208">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="3cbcc-209">WCF では、認証モードに加えて、ほとんどのメッセージ セキュリティ ベースの認証モードに適用される共通の保護メカニズムを制御するための設定が用意されています。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-209">In addition to authentication modes, WCF provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="3cbcc-210">このドキュメントでは、以下のプレフィックスと名前空間を使用します。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-210">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="3cbcc-211">Prefix</span><span class="sxs-lookup"><span data-stu-id="3cbcc-211">Prefix</span></span>|<span data-ttu-id="3cbcc-212">名前空間</span><span class="sxs-lookup"><span data-stu-id="3cbcc-212">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="3cbcc-213">s</span><span class="sxs-lookup"><span data-stu-id="3cbcc-213">s</span></span>|http://www.w3.org/2003/05/soap-envelope|  
|<span data-ttu-id="3cbcc-214">sp</span><span class="sxs-lookup"><span data-stu-id="3cbcc-214">sp</span></span>|http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702|  
|<span data-ttu-id="3cbcc-215">a</span><span class="sxs-lookup"><span data-stu-id="3cbcc-215">a</span></span>|http://www.w3.org/2005/08/addressing|  
|<span data-ttu-id="3cbcc-216">wsse</span><span class="sxs-lookup"><span data-stu-id="3cbcc-216">wsse</span></span>|<span data-ttu-id="3cbcc-217">未定 - OASIS WSS 1.0 の URI</span><span class="sxs-lookup"><span data-stu-id="3cbcc-217">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="3cbcc-218">wsse11</span><span class="sxs-lookup"><span data-stu-id="3cbcc-218">wsse11</span></span>|<span data-ttu-id="3cbcc-219">未定 - OASIS WSS 1.1 の URI</span><span class="sxs-lookup"><span data-stu-id="3cbcc-219">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="3cbcc-220">wsu</span><span class="sxs-lookup"><span data-stu-id="3cbcc-220">wsu</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd|  
|<span data-ttu-id="3cbcc-221">ds</span><span class="sxs-lookup"><span data-stu-id="3cbcc-221">ds</span></span>|<span data-ttu-id="3cbcc-222">未定 - W3C XMLDSig の URI</span><span class="sxs-lookup"><span data-stu-id="3cbcc-222">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="3cbcc-223">wst</span><span class="sxs-lookup"><span data-stu-id="3cbcc-223">wst</span></span>|<span data-ttu-id="3cbcc-224">未定 - WS-Trust 2005/02 の URI</span><span class="sxs-lookup"><span data-stu-id="3cbcc-224">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="3cbcc-225">wssc</span><span class="sxs-lookup"><span data-stu-id="3cbcc-225">wssc</span></span>|<span data-ttu-id="3cbcc-226">未定 - WS-SecureConversation 2005/02 の URI</span><span class="sxs-lookup"><span data-stu-id="3cbcc-226">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="3cbcc-227">wsaw</span><span class="sxs-lookup"><span data-stu-id="3cbcc-227">wsaw</span></span>|http://www.w3.org/2006/05/addressing/wsdl|  
|<span data-ttu-id="3cbcc-228">wsp</span><span class="sxs-lookup"><span data-stu-id="3cbcc-228">wsp</span></span>|http://schemas.xmlsoap.org/ws/2004/09/policy|  
|<span data-ttu-id="3cbcc-229">mssp</span><span class="sxs-lookup"><span data-stu-id="3cbcc-229">mssp</span></span>|http://schemas.microsoft.com/ws/2005/07/securitypolicy|  
  
## <a name="1-token-profiles"></a><span data-ttu-id="3cbcc-230">1. トークンプロファイル</span><span class="sxs-lookup"><span data-stu-id="3cbcc-230">1. Token Profiles</span></span>  
 <span data-ttu-id="3cbcc-231">Web サービス セキュリティ仕様では、資格情報をセキュリティ トークンとして表します。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-231">Web Services Security specifications represent credential as security tokens.</span></span> <span data-ttu-id="3cbcc-232">WCF では、次の種類のトークンをサポートします。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-232">WCF supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="3cbcc-233">1.1 UsernameToken</span><span class="sxs-lookup"><span data-stu-id="3cbcc-233">1.1 UsernameToken</span></span>  
 <span data-ttu-id="3cbcc-234">WCF は、次の制約を持つユーザー名トークン10 およびユーザー名トークン11 プロファイルに従います。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-234">WCF follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="3cbcc-235">R1101 : UsernameToken\Password 要素の PasswordType 属性では、#PasswordText (既定値) を省略するか、指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-235">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="3cbcc-236">機能拡張を使用すると、#PasswordDigest を実装できます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-236">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="3cbcc-237">#PasswordDigest は、十分に安全性の高いパスワード保護機構であると誤解されがちであることが報告されています。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-237">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="3cbcc-238">しかし、#PasswordDigest は、UsernameToken の暗号化の代替として使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-238">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="3cbcc-239">#PasswordDigest の第一の目的は、リプレイ攻撃から保護することです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-239">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="3cbcc-240">WCF 認証モードでは、リプレイ攻撃の脅威は、メッセージ署名を使用して軽減されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-240">In WCF authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="3cbcc-241">B1102 WCF は、ユーザー名トークンの Nonce および作成済みサブ要素を生成しません。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-241">B1102 WCF never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="3cbcc-242">これらのサブ要素は、リプレイ検出を支援するためのものです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-242">These sub-elements are intended to help replay detection.</span></span> <span data-ttu-id="3cbcc-243">WCF では、代わりにメッセージ署名が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-243">WCF uses message signatures instead.</span></span>  
  
 <span data-ttu-id="3cbcc-244">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) では、パスワードからのキー派生機能が導入されています。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-244">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="3cbcc-245">B1103 : UsernameToken のパスワードをキー派生に使用することはできません。したがって、暗号化操作では使用できません。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-245">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="3cbcc-246">理由 : パスワードは、一般に暗号化操作に使用するには脆弱すぎると見なされています。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-246">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="3cbcc-247">1.2 X509 トークン</span><span class="sxs-lookup"><span data-stu-id="3cbcc-247">1.2 X509 Token</span></span>  
 <span data-ttu-id="3cbcc-248">WCF は、資格情報の種類として X509v3 証明書をサポートし、次の制約を持つ X509TokenProfile1.0 および X509TokenProfile1.1 に従います。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-248">WCF supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="3cbcc-249">R1201 : BinarySecurityToken 要素に X509v3 証明書が含まれている場合、この要素の ValueType 属性の値は #X509v3 であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-249">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="3cbcc-250">WSS X509 Token Profile 1.0 および 1.1 では、値の種類として #X509PKIPathv1 と #PKCS7 も定義されています。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-250">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> <span data-ttu-id="3cbcc-251">WCF では、これらの型をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-251">WCF does not support these types.</span></span>  
  
 <span data-ttu-id="3cbcc-252">R1202 : X509 証明書に SubjectKeyIdentifier (SKI) 拡張が含まれている場合、トークンへの外部参照に wsse:KeyIdentifier を使用する必要があります。この場合、ValueType 属性に #X509SubjectKeyIdentifier を指定し、証明書の SKI 拡張の Base64 でエンコードされた値を含めます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-252">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="3cbcc-253">SKI 参照は幅広く実装されており、相互運用性の高い外部参照型であることが証明されています。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-253">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="3cbcc-254">R1203 : X509 セキュリティ トークンへの外部参照では、ds:X509IssuerSerial を使用できません。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-254">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="3cbcc-255">R1204 : X509TokenProfile1.1 を使用している場合、X509 セキュリティ トークンへの外部参照では、WS-Security 1.1 で導入された拇印を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-255">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 <span data-ttu-id="3cbcc-256">WCF は、X509 発行者シリアルをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-256">WCF supports X509IssuerSerial.</span></span> <span data-ttu-id="3cbcc-257">ただし、X509IssuerSerial で相互運用性の問題があります: WCF は、文字列を使用して X509IssuerSerial の 2 つの値を比較します。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-257">However there are interoperability issues with X509IssuerSerial: WCF uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="3cbcc-258">したがって、サブジェクト名のコンポーネントを並べ替え、WCF サービスに証明書への参照を送信した場合、そのコンポーネントが見つからない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-258">Therefore if one reorders components of the Subject Name and sends to an WCF service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="3cbcc-259">1.3 Kerberos トークン</span><span class="sxs-lookup"><span data-stu-id="3cbcc-259">1.3 Kerberos Token</span></span>  
 <span data-ttu-id="3cbcc-260">WCF は、次の制約を持つ Windows 認証の目的で KerberosTokenProfile1.1 をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-260">WCF supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="3cbcc-261">R1301 : GSS_API と Kerberos 仕様で定義されているように、Kerberos トークンは GSS によってラップされた Kerberos v4 AP_REQ の値を伝達する必要があります。また、値 #GSS_Kerberosv5_AP_REQ が指定された ValueType 属性を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-261">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 <span data-ttu-id="3cbcc-262">WCF は、ベア AP-REQ ではなく、GSS でラップされた Kerberos AP-REQ を使用します。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-262">WCF uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="3cbcc-263">これは、セキュリティのベスト プラクティスです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-263">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="3cbcc-264">1.4 SAML v1.1 トークン</span><span class="sxs-lookup"><span data-stu-id="3cbcc-264">1.4 SAML v1.1 Token</span></span>  
 <span data-ttu-id="3cbcc-265">WCF は、SAML v1.1 トークンの WSS SAML トークン プロファイル 1.0 および 1.1 をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-265">WCF supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="3cbcc-266">SAML トークンの形式のその他のバージョンも実装できます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-266">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="3cbcc-267">1.5 セキュリティ コンテキスト トークン</span><span class="sxs-lookup"><span data-stu-id="3cbcc-267">1.5 Security Context Token</span></span>  
 <span data-ttu-id="3cbcc-268">WCF は、WS-Secure 会話で導入されたセキュリティ コンテキスト トークン (SCT) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-268">WCF supports the Security Context Token (SCT) introduced in WS-SecureConversation.</span></span> <span data-ttu-id="3cbcc-269">SCT は、SecureConversation と、後述する TLS および SSPI の各バイナリ ネゴシエーション プロトコルで確立されたセキュリティ コンテキストを表すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-269">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="3cbcc-270">2. 共通メッセージセキュリティパラメータ</span><span class="sxs-lookup"><span data-stu-id="3cbcc-270">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="3cbcc-271">2.1 タイムスタンプ</span><span class="sxs-lookup"><span data-stu-id="3cbcc-271">2.1 TimeStamp</span></span>  
 <span data-ttu-id="3cbcc-272">タイムスタンプの有無は、<xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> クラスの <xref:System.ServiceModel.Channels.SecurityBindingElement> プロパティを使用して制御します。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-272">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> <span data-ttu-id="3cbcc-273">WCF は常に wsse:タイムスタンプを wsse:作成し、wsse:Expires フィールドをシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-273">WCF always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="3cbcc-274">署名を使用する場合、wsse:TimeStamp は必ず署名されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-274">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="3cbcc-275">2.2 保護の順序</span><span class="sxs-lookup"><span data-stu-id="3cbcc-275">2.2 Protection Order</span></span>  
 <span data-ttu-id="3cbcc-276">WCF では、メッセージ保護命令 "暗号化前に署名" と "署名前に暗号化" (セキュリティ ポリシー 1.2) がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-276">WCF supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.2).</span></span> <span data-ttu-id="3cbcc-277">WS-Security 1.1 の SignatureConfirmation 機構を使用していない場合、"署名前に暗号化" を使用して保護されたメッセージを開くと、置き換え攻撃への署名が行われます。また、暗号化された内容に署名すると監査が困難になります。これらの理由から、"暗号化前に署名" を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-277">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="3cbcc-278">2.3 署名の保護</span><span class="sxs-lookup"><span data-stu-id="3cbcc-278">2.3 Signature Protection</span></span>  
 <span data-ttu-id="3cbcc-279">"署名前に暗号化" を使用する場合、暗号化された内容や署名キー (特に、脆弱なキー マテリアルでカスタム トークンを使用する場合) を推測するブルート フォース攻撃を防ぐために、署名を保護することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-279">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="3cbcc-280">2.4 アルゴリズム スイート</span><span class="sxs-lookup"><span data-stu-id="3cbcc-280">2.4 Algorithm Suite</span></span>  
 <span data-ttu-id="3cbcc-281">WCF では、セキュリティ ポリシー 1.2 に記載されているすべてのアルゴリズム スイートをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-281">WCF supports all algorithm suites listed in Security Policy 1.2.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="3cbcc-282">2.5 キー派生</span><span class="sxs-lookup"><span data-stu-id="3cbcc-282">2.5 Key Derivation</span></span>  
 <span data-ttu-id="3cbcc-283">WCF では、WS-Secure 会話で説明されているように、対称キーのキー派生を使用します。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-283">WCF uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="3cbcc-284">2.6 署名確認</span><span class="sxs-lookup"><span data-stu-id="3cbcc-284">2.6 Signature Confirmation</span></span>  
 <span data-ttu-id="3cbcc-285">"man-in-the-middle" 攻撃への対策として署名確認を使用することによって、署名セットを保護できます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-285">Signature confirmation can be used as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="3cbcc-286">2.7 セキュリティ ヘッダーのレイアウト</span><span class="sxs-lookup"><span data-stu-id="3cbcc-286">2.7 Security Header Layout</span></span>  
 <span data-ttu-id="3cbcc-287">各認証モードでは、セキュリティ ヘッダーの特定のレイアウトが使用されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-287">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="3cbcc-288">セキュリティ ヘッダー内の要素は、部分的に順序付けられています。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-288">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="3cbcc-289">セキュリティ ヘッダーの子要素の順序を定義するために、WS-Security Policy では、以下のセキュリティ ヘッダー レイアウト モードが定義されています。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-289">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3cbcc-290">高</span><span class="sxs-lookup"><span data-stu-id="3cbcc-290">Strict</span></span>|<span data-ttu-id="3cbcc-291">"使用前に宣言する" という一般的原則に基づき、Security Policy のセクション 7.7.1 に記載された番号付きレイアウト ルールに従って、項目がセキュリティ ヘッダーに追加されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-291">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="3cbcc-292">Lax</span><span class="sxs-lookup"><span data-stu-id="3cbcc-292">Lax</span></span>|<span data-ttu-id="3cbcc-293">WSS: SOAP Message Security に準拠した任意の順序で、項目がセキュリティ ヘッダーに追加されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-293">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="3cbcc-294">LaxTimestampFirst</span><span class="sxs-lookup"><span data-stu-id="3cbcc-294">LaxTimestampFirst</span></span>|<span data-ttu-id="3cbcc-295">セキュリティ ヘッダー内の最初の項目が wsse:Timestamp でなければならないという点を除き、Lax と同じです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-295">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="3cbcc-296">LaxTimestampLast</span><span class="sxs-lookup"><span data-stu-id="3cbcc-296">LaxTimestampLast</span></span>|<span data-ttu-id="3cbcc-297">セキュリティ ヘッダー内の最後の項目が wsse:Timestamp でなければならないという点を除き、Lax と同じです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-297">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 <span data-ttu-id="3cbcc-298">WCF では、セキュリティ ヘッダー レイアウトの 4 つのモードをすべてサポートしています。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-298">WCF supports all four modes for security header layout.</span></span> <span data-ttu-id="3cbcc-299">後ほど示す各認証モードのセキュリティ ヘッダーの構造とメッセージの例では、"Strict" モードに従っています。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-299">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="3-common-message-security-parameters"></a><span data-ttu-id="3cbcc-300">3. 共通メッセージセキュリティパラメータ</span><span class="sxs-lookup"><span data-stu-id="3cbcc-300">3. Common Message Security Parameters</span></span>  
 <span data-ttu-id="3cbcc-301">このセクションでは、各認証モードのポリシーの例、およびクライアントとサービスによって交換されるメッセージのセキュリティ ヘッダーの構造を示す例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-301">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="31-transport-protection"></a><span data-ttu-id="3cbcc-302">3.1 輸送保護</span><span class="sxs-lookup"><span data-stu-id="3cbcc-302">3.1 Transport Protection</span></span>  
 <span data-ttu-id="3cbcc-303">WCF には、メッセージを保護するためにセキュリティで保護されたトランスポートを使用する 5 つの認証モードが用意されています。ユーザー名オーバートランスポート、証明書オーバートランスポート、KerberosOverトランスポート、発行されたトークンオーバートランスポートとスピーネゴシエートオーバートランスポート。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-303">WCF provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="3cbcc-304">これらの認証モードは、SecurityPolicy に記載されたトランスポート バインディングを使用して構築されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-304">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="3cbcc-305">UserNameOverTransport 認証モードの場合、UsernameToken は署名付きサポート トークンです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-305">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="3cbcc-306">その他の認証モードでは、トークンは署名付き保証トークンとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-306">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="3cbcc-307">SecurityPolicy の Appendix C.1.2 および C.1.3 には、セキュリティ ヘッダーのレイアウトの詳細が記載されています。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-307">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="3cbcc-308">以降のセキュリティ ヘッダーの例は、指定の認証モードの Strict レイアウトを示しています。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-308">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="3cbcc-309">すべてのケースで、トークンの "派生キー" プロパティの値は "false" です。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-309">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="3cbcc-310">トランスポート バインディングの各プロパティの値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-310">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="3cbcc-311">タイムスタンプ : true</span><span class="sxs-lookup"><span data-stu-id="3cbcc-311">Timestamp: true</span></span>  
  
 <span data-ttu-id="3cbcc-312">セキュリティ ヘッダーのレイアウト : Strict</span><span class="sxs-lookup"><span data-stu-id="3cbcc-312">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="3cbcc-313">アルゴリズム スイート : Basic256</span><span class="sxs-lookup"><span data-stu-id="3cbcc-313">Algorithm Suite: Basic256</span></span>  
  
#### <a name="311-usernameovertransport"></a><span data-ttu-id="3cbcc-314">3.1.1 UsernameOverTransport</span><span class="sxs-lookup"><span data-stu-id="3cbcc-314">3.1.1 UsernameOverTransport</span></span>  
 <span data-ttu-id="3cbcc-315">この認証モードでは、クライアントはユーザー名トークンを使用して認証を行います。ユーザー名トークンは、イニシエーターから受信者に必ず送信される署名付きサポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-315">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="3cbcc-316">サービスはトランスポート層で X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-316">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="3cbcc-317">使用するバインディングは、トランスポート バインディングです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-317">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="3cbcc-318">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-318">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="UserNameOverTransport_policy"><wsp:ExactlyOne><wsp:All><sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:TransportToken><wsp:Policy><sp:HttpsToken/></wsp:Policy></sp:TransportToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/></wsp:Policy></sp:TransportBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
 <span data-ttu-id="3cbcc-319">セキュリティ ヘッダーのレイアウト</span><span class="sxs-lookup"><span data-stu-id="3cbcc-319">Security Header Layout</span></span>  
  
 <span data-ttu-id="3cbcc-320">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-320">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp><o:UsernameToken u:Id="uuid-b96fbb3a-e646-4403-9473-2e5ffc733ff8-1"> ... </o:UsernameToken></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-321">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-321">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp></o:Security>  
```  
  
#### <a name="312-certificateovertransport"></a><span data-ttu-id="3cbcc-322">3.1.2 CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="3cbcc-322">3.1.2 CertificateOverTransport</span></span>  
 <span data-ttu-id="3cbcc-323">この認証モードでは、クライアントは X.509 証明書を使用して認証を行います。X.509 証明書は、イニシエーターから受信者に必ず送信される保証サポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-323">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="3cbcc-324">サービスはトランスポート層で X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-324">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="3cbcc-325">使用するバインディングは、トランスポート バインディングです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-325">The binding used is a transport binding.</span></span> <span data-ttu-id="3cbcc-326">CertificateOverTransport が署名するのは SOAP ヘッダーのみで、SOAP 本文には署名しません。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-326">CertificateOverTransport only signs the SOAP headers, not the SOAP body.</span></span> <span data-ttu-id="3cbcc-327">これは、TransportWithMessageCredentials セキュリティ モードで使用される認証モードです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-327">This is the authentication mode used by the TransportWithMessageCredentials security mode.</span></span> <span data-ttu-id="3cbcc-328">認証はメッセージ資格情報を使用して行われるので、SOAP ヘッダーのみが署名されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-328">Only the SOAP headers are signed because authentication is done by using message credentials.</span></span>  
  
 <span data-ttu-id="3cbcc-329">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-329">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="CertificateOverTransport_policy"><wsp:ExactlyOne><wsp:All><sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:TransportToken><wsp:Policy><sp:HttpsToken/></wsp:Policy></sp:TransportToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/></wsp:Policy></sp:TransportBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token><sp:SignedParts><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
 <span data-ttu-id="3cbcc-330">セキュリティ ヘッダーのレイアウト</span><span class="sxs-lookup"><span data-stu-id="3cbcc-330">Security Header Layout</span></span>  
  
 <span data-ttu-id="3cbcc-331">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-331">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-332">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-332">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp></o:Security>  
```  
  
#### <a name="313-issuedtokenovertransport"></a><span data-ttu-id="3cbcc-333">3.1.3 IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="3cbcc-333">3.1.3 IssuedTokenOverTransport</span></span>  
 <span data-ttu-id="3cbcc-334">この認証モードでは、クライアントはサービスに対する認証を行わず、セキュリティ トークン サービス (STS) により発行されたトークンを示すことで、共有キーの有無を示します。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-334">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="3cbcc-335">発行されたトークンは、イニシエーターから受信者に必ず送信される保証サポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-335">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="3cbcc-336">サービスはトランスポート層で X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-336">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="3cbcc-337">バインディングはトランスポート バインディングです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-337">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="3cbcc-338">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-338">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenOverTransport_policy">
 <wsp:ExactlyOne>
  <wsp:All>
   <sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702">
    <wsp:Policy>
     <sp:TransportToken>
      <wsp:Policy>
       <sp:HttpsToken />
      </wsp:Policy>
     </sp:TransportToken>
     <sp:AlgorithmSuite>
      <wsp:Policy>
       <sp:Basic256 />
      </wsp:Policy>
     </sp:AlgorithmSuite>
     <sp:Layout>
      <wsp:Policy>
       <sp:Strict/>
      </wsp:Policy>
     </sp:Layout>
     <sp:IncludeTimestamp/>
    </wsp:Policy>
   </sp:TransportBinding>
   <sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702">
    <wsp:Policy>
     <sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient">
      <Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702">
       <Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address>
       <Metadata xmlns="http://www.w3.org/2005/08/addressing">
        <Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
         <wsx:MetadataSection xmlns="">
          <wsx:MetadataReference>
           <Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address>
           <Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity">
            <Dns> ...  </Dns>
           </Identity>
          </wsx:MetadataReference>
         </wsx:MetadataSection>
        </Metadata>
       </Metadata>
      </Issuer>
      <sp:RequestSecurityTokenTemplate>
       <trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType>
      </sp:RequestSecurityTokenTemplate>
      <wsp:Policy>
       <sp:RequireInternalReference/>
      </wsp:Policy>
     </sp:IssuedToken>
     <sp:SignedParts>
      <sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/>
     </sp:SignedParts>
    </wsp:Policy>
   </sp:EndorsingSupportingTokens>
   <sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702">
    <wsp:Policy>
     <sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/>
     <sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/>
    </wsp:Policy>
   </sp:Wss11>
   <sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702">
    <wsp:Policy>
     <sp:MustSupportIssuedTokens/>
     <sp:RequireClientEntropy/>
     <sp:RequireServerEntropy/>
    </wsp:Policy>
   </sp:Trust13>
   <wsaw:UsingAddressing/>
  </wsp:All>
 </wsp:ExactlyOne>
</wsp:Policy>
```  
  
 <span data-ttu-id="3cbcc-339">セキュリティ ヘッダーのレイアウト</span><span class="sxs-lookup"><span data-stu-id="3cbcc-339">Security Header Layout</span></span>  
  
 <span data-ttu-id="3cbcc-340">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-340">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-67692bb6-85b7-4299-8587-3ce60086b0d2-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-fab7e1b2-8dc4-412b-bda9-b95a4f836815-16" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-341">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-341">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-fab7e1b2-8dc4-412b-bda9-b95a4f836815-21"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
#### <a name="314-kerberosovertransport"></a><span data-ttu-id="3cbcc-342">3.1.4 KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="3cbcc-342">3.1.4 KerberosOverTransport</span></span>  
 <span data-ttu-id="3cbcc-343">この認証モードを使用すると、クライアントは Kerberos チケットを使用してサービスに対する認証を行います。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-343">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="3cbcc-344">Kerberos トークンは、保証サポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-344">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="3cbcc-345">サービスはトランスポート層で X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-345">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="3cbcc-346">バインディングはトランスポート バインディングです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-346">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="3cbcc-347">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-347">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="KerberosOverTransport_policy"><wsp:ExactlyOne><wsp:All><sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:TransportToken><wsp:Policy><sp:HttpsToken/></wsp:Policy></sp:TransportToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic128/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/></wsp:Policy></sp:TransportBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:KerberosToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Once"><wsp:Policy><sp:WssGssKerberosV5ApReqToken11/></wsp:Policy></sp:KerberosToken><sp:SignedParts><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
 <span data-ttu-id="3cbcc-348">セキュリティ ヘッダーのレイアウト</span><span class="sxs-lookup"><span data-stu-id="3cbcc-348">Security Header Layout</span></span>  
  
 <span data-ttu-id="3cbcc-349">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-349">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-350">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-350">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp></o:Security>  
```  
  
#### <a name="315-sspinegotiatedovertransport"></a><span data-ttu-id="3cbcc-351">3.1.5 SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="3cbcc-351">3.1.5 SspiNegotiatedOverTransport</span></span>  
 <span data-ttu-id="3cbcc-352">このモードでは、ネゴシエーション プロトコルを使用して、クライアントとサーバーの認証を行います。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-352">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="3cbcc-353">Kerberos を使用できる場合は Kerberos が使用され、それ以外の場合は NTLM が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-353">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="3cbcc-354">発行された SCT は、イニシエーターから受信者に必ず送信される保証サポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-354">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="3cbcc-355">サービスは、トランスポート層で X.509 証明書により追加的に認証されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-355">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="3cbcc-356">使用するバインディングは、トランスポート バインディングです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-356">The binding used is a transport binding.</span></span> <span data-ttu-id="3cbcc-357">"SPNEGO" (ネゴシエーション) では、WCF が WS-Trust で SSPI バイナリ ネゴシエーション プロトコルを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-357">"SPNEGO" (negotiation) describes how WCF uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="3cbcc-358">このセクションで示すセキュリティ ヘッダーの例は、SPNEGO ハンドシェイクによって SCT が確立された後の状態を示しています。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-358">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="3cbcc-359">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-359">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="SspiNegotiatedOverTransport_policy"><wsp:ExactlyOne><wsp:All><sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:TransportToken><wsp:Policy><sp:HttpsToken/></wsp:Policy></sp:TransportToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/></wsp:Policy></sp:TransportBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></sp:SpnegoContextToken><sp:SignedParts><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples"></a><span data-ttu-id="3cbcc-360">セキュリティ ヘッダーの例</span><span class="sxs-lookup"><span data-stu-id="3cbcc-360">Security Header Examples</span></span>  
 <span data-ttu-id="3cbcc-361">WS-Trust バイナリ ネゴシエーションを使用して、SPNEGO ハンドシェイクによってセキュリティ コンテキスト トークンが確立されると、アプリケーション メッセージのセキュリティ ヘッダーは、次のような構造になります。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-361">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="3cbcc-362">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-362">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-9a29d087-5dae-4d40-bf86-5746d9d30eca-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-363">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-363">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp></o:Security>  
```  
  
### <a name="32-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="3cbcc-364">3.2 サービス認証に X.509 証明書を使用する</span><span class="sxs-lookup"><span data-stu-id="3cbcc-364">3.2 Using X.509 Certificates for Service Authentication</span></span>  
 <span data-ttu-id="3cbcc-365">このセクションでは、MutualCertificate WSS1.0、Mutual CertificateDuplex、MutualCertificate WSS1.1、AnonymousForCertificate、UserNameForCertificate、および IssuedTokenForCertificate の各認証モードについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-365">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="321-mutualcertificate-wss10"></a><span data-ttu-id="3cbcc-366">3.2.1 MutualCertificate WSS1.0</span><span class="sxs-lookup"><span data-stu-id="3cbcc-366">3.2.1 MutualCertificate WSS1.0</span></span>  
 <span data-ttu-id="3cbcc-367">この認証モードでは、クライアントは X.509 証明書を使用して認証を行います。X.509 証明書は、イニシエーター トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-367">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="3cbcc-368">また、サービスは X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-368">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="3cbcc-369">SOAP ヘッダーと SOAP 本文の両方が署名されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-369">Both the SOAP headers and the SOAP body are signed.</span></span> <span data-ttu-id="3cbcc-370">対称キーが作成され、受信者のトランスポート証明書を使用して暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-370">A symmetric key is created and is encrypted with the transport certificate for the recipient.</span></span>  
  
 <span data-ttu-id="3cbcc-371">使用するバインディングは、次のプロパティ値が設定された非対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-371">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="3cbcc-372">イニシエーター トークン : インクルード モードが .../IncludeToken/AlwaysToRecipient に設定されたクライアントの X.509 証明書</span><span class="sxs-lookup"><span data-stu-id="3cbcc-372">Initiator Token: the client’s X.509 certificate, with inclusion mode set to .../IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="3cbcc-373">受信者トークン : インクルード モードが .../IncludeToken/Never に設定されたサーバーの X.509 証明書</span><span class="sxs-lookup"><span data-stu-id="3cbcc-373">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set .../IncludeToken/Never</span></span>  
  
 <span data-ttu-id="3cbcc-374">トークンの保護 : False</span><span class="sxs-lookup"><span data-stu-id="3cbcc-374">Token Protection: False</span></span>  
  
 <span data-ttu-id="3cbcc-375">ヘッダーと本文全体の署名 : True</span><span class="sxs-lookup"><span data-stu-id="3cbcc-375">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="3cbcc-376">保護の順序 : SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="3cbcc-376">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="3cbcc-377">署名の暗号化 : True</span><span class="sxs-lookup"><span data-stu-id="3cbcc-377">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="3cbcc-378">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-378">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:AsymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:InitiatorToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:InitiatorToken><sp:RecipientToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:RecipientToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:AsymmetricBinding><sp:Wss10 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/></wsp:Policy></sp:Wss10><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="3cbcc-379">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="3cbcc-379">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="3cbcc-380">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-380">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-39cb393e-9da8-4d5d-b273-540ef614569b-1"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><e:EncryptedData Id="_7" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-381">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-381">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"> <u:Timestamp u:Id="uuid-3d742930-70d3-4d7e-aa0a-8721128dc115-8"> ... </u:Timestamp><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><e:EncryptedData Id="_5" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-382">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-382">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:AsymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:InitiatorToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:InitiatorToken><sp:RecipientToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:RecipientToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:AsymmetricBinding><sp:Wss10 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/></wsp:Policy></sp:Wss10><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="3cbcc-383">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="3cbcc-383">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="3cbcc-384">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-384">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-73da3e21-abff-4294-a910-e75303d280cc-1"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-385">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-385">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-02f276b6-804f-480d-99e9-2e90fc76ab27-3"> ... </u:Timestamp><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="322-mutualcertificateduplex"></a><span data-ttu-id="3cbcc-386">3.2.2 MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="3cbcc-386">3.2.2 MutualCertificateDuplex</span></span>  
 <span data-ttu-id="3cbcc-387">この認証モードでは、クライアントは X.509 証明書を使用して認証を行います。X.509 証明書は、イニシエーター トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-387">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="3cbcc-388">また、サービスは X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-388">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="3cbcc-389">使用するバインディングは、次のプロパティ値が設定された非対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-389">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="3cbcc-390">イニシエーター トークン : インクルード モードが .../IncludeToken/AlwaysToRecipient に設定されたクライアントの X.509 証明書</span><span class="sxs-lookup"><span data-stu-id="3cbcc-390">Initiator Token: Client’s X509 Certificate, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="3cbcc-391">受信者トークン : インクルード モードが .../IncludeToken/AlwaysToInitiator に設定されたサーバーの X509 証明書</span><span class="sxs-lookup"><span data-stu-id="3cbcc-391">Recipient Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="3cbcc-392">トークンの保護 : False</span><span class="sxs-lookup"><span data-stu-id="3cbcc-392">Token Protection: False</span></span>  
  
 <span data-ttu-id="3cbcc-393">ヘッダーと本文全体の署名 : True</span><span class="sxs-lookup"><span data-stu-id="3cbcc-393">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="3cbcc-394">保護の順序 : SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="3cbcc-394">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="3cbcc-395">署名の暗号化 : True</span><span class="sxs-lookup"><span data-stu-id="3cbcc-395">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="3cbcc-396">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-396">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificateDuplex_policy"><wsp:ExactlyOne><wsp:All><sp:AsymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:InitiatorToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:InitiatorToken><sp:RecipientToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToInitiator"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:RecipientToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:AsymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><cdp:CompositeDuplex xmlns:cdp="http://schemas.microsoft.com/net/2006/06/duplex"/><ow:OneWay xmlns:ow="http://schemas.microsoft.com/ws/2005/05/routing/policy"/><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="3cbcc-397">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="3cbcc-397">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="3cbcc-398">要求と応答</span><span class="sxs-lookup"><span data-stu-id="3cbcc-398">Request and Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-4dec3da4-b572-4654-ba4d-4a2f84a87510-1"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><e:EncryptedData Id="_7" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-399">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-399">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificateDuplex_policy"><wsp:ExactlyOne><wsp:All><sp:AsymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:InitiatorToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:InitiatorToken><sp:RecipientToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToInitiator"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:RecipientToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:AsymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><cdp:CompositeDuplex xmlns:cdp="http://schemas.microsoft.com/net/2006/06/duplex"/><ow:OneWay xmlns:ow="http://schemas.microsoft.com/ws/2005/05/routing/policy"/><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="3cbcc-400">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="3cbcc-400">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="3cbcc-401">要求と応答</span><span class="sxs-lookup"><span data-stu-id="3cbcc-401">Request and Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-b0e23feb-cd2d-4dc1-bad9-284bc45f3be3-1"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="323-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="3cbcc-402">3.2.3 X.509 サービス認証での SymmetricBinding の使用</span><span class="sxs-lookup"><span data-stu-id="3cbcc-402">3.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  
 <span data-ttu-id="3cbcc-403">"WSS10" では、X509 トークンを使用するシナリオのサポートが制限されていました。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-403">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="3cbcc-404">たとえば、サービスの X509 トークンだけを使用して、メッセージの署名と暗号化を保護することはできませんでした。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-404">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="3cbcc-405">"WSS11" では、EncryptedKey を共通鍵トークンとして使用する方法が導入されています。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-405">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="3cbcc-406">これにより、サービスの X.509 証明書の暗号化された一時キーを使用して、要求メッセージと応答メッセージの両方を保護できるようになります。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-406">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="3cbcc-407">このパターンは、以下のセクション 3.4 で説明する認証モードです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-407">The authentication modes described in the section 3.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="3cbcc-408">WS-SecurityPolicy には、サービスの X509 トークンを保護トークンとして使用して SymmetricBinding を使用するこのパターンが記載されています。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-408">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="3cbcc-409">AnonymousForCertificate、UsernameForCertificate、MutualCertificate WSS11、および IssuedTokenForCertificate の各認証モードはすべて、以下のプロパティ値が設定された sp:SymmetricBinding の同様のインスタンスを使用します。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-409">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="3cbcc-410">保護トークン: インクルード モードが .../IncludeToken/Never に設定されたサーバーの X509 証明書</span><span class="sxs-lookup"><span data-stu-id="3cbcc-410">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="3cbcc-411">トークンの保護 : False</span><span class="sxs-lookup"><span data-stu-id="3cbcc-411">Token Protection: False</span></span>  
  
 <span data-ttu-id="3cbcc-412">ヘッダーと本文全体の署名 : True</span><span class="sxs-lookup"><span data-stu-id="3cbcc-412">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="3cbcc-413">保護の順序 : SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="3cbcc-413">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="3cbcc-414">署名の暗号化 : True</span><span class="sxs-lookup"><span data-stu-id="3cbcc-414">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="3cbcc-415">前述の各認証モードは、使用するサポート トークンだけが異なります。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-415">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="3cbcc-416">AnonymousForCertificate はサポート トークンをまったく使用せず、MutualCertificate WSS 1.1 は保証サポート トークンとしてクライアントの X509 証明書を使用します。また、UserNameForCertificate は署名付きサポート トークンとしてユーザー名トークンを使用し、IssuedTokenForCertificate は保証サポート トークンとして発行済みトークンを使用します。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-416">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
#### <a name="324-anonymousforcertificate"></a><span data-ttu-id="3cbcc-417">3.2.4 AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="3cbcc-417">3.2.4 AnonymousForCertificate</span></span>  
 <span data-ttu-id="3cbcc-418">この認証モードでは、クライアントは匿名になり、X.509 証明書を使用してサービスが認証されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-418">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="3cbcc-419">使用するバインディングは、3.4.2 で説明する対称バインディングのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-419">The binding used is an instance of symmetric binding as described in 3.4.2.</span></span>  
  
 <span data-ttu-id="3cbcc-420">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-420">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="AnonymousforCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="3cbcc-421">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="3cbcc-421">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="3cbcc-422">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-422">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-4de2d2a1-6266-4a02-93e6-242a1ac2aeb3-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-4de2d2a1-6266-4a02-93e6-242a1ac2aeb3-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-423">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-423">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-b06cb481-3176-4c56-af35-c38252bb6c78-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_2" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_7" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-424">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-424">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="AnonymousforCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="3cbcc-425">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="3cbcc-425">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="3cbcc-426">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-426">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-562aac68-8cdd-45d5-bc03-df662e6ed048-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-562aac68-8cdd-45d5-bc03-df662e6ed048-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-427">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-427">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-15b48260-23da-424d-8dc4-8f4e150fb8cf-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><k:SignatureConfirmation u:Id="_2" Value="ALF+QNGmWn2k3LpWEDIzSBgTkvo=" xmlns:k="http://docs.oasis-open.org/wss/oasis-wss-wssecurity-secext-1.1.xsd"></k:SignatureConfirmation><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="325-usernameforcertificate"></a><span data-ttu-id="3cbcc-428">3.2.5 UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="3cbcc-428">3.2.5 UserNameForCertificate</span></span>  
 <span data-ttu-id="3cbcc-429">この認証モードでは、クライアントはユーザー名トークンを使用してサーバーに対する認証を行います。ユーザー名トークンは、署名付きサポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-429">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="3cbcc-430">X.509 証明書を使用したクライアントに対するサービス認証。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-430">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="3cbcc-431">使用するバインディングは、クライアントによって生成され、サービスの公開キーで暗号化されたキーを保護トークンとして使用する対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-431">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="3cbcc-432">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-432">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="UserNameForCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><http:BasicAuthentication xmlns:http="http://schemas.microsoft.com/ws/06/2004/policy/http"/><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="3cbcc-433">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="3cbcc-433">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="3cbcc-434">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-434">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-27196139-acb9-410f-a2c6-51d20d24278b-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-27196139-acb9-410f-a2c6-51d20d24278b-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_9" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-435">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-435">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-681226f7-126a-4806-b732-fcca097cd7a8-5"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-436">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-436">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="UserNameForCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><http:BasicAuthentication xmlns:http="http://schemas.microsoft.com/ws/06/2004/policy/http"/><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="3cbcc-437">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="3cbcc-437">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="3cbcc-438">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-438">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-8276d8b7-74a0-4257-b8a5-e25350e7c2d4-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-8276d8b7-74a0-4257-b8a5-e25350e7c2d4-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-439">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-439">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-8a7ad353-f071-49dc-90dd-5ad2e9abd40a-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="326-mutualcertificate-wss-11"></a><span data-ttu-id="3cbcc-440">3.2.6 MutualCertificate (WSS 1.1)</span><span class="sxs-lookup"><span data-stu-id="3cbcc-440">3.2.6 MutualCertificate (WSS 1.1)</span></span>  
 <span data-ttu-id="3cbcc-441">この認証モードでは、クライアントは X.509 証明書を使用して認証を行います。X.509 証明書は、保証サポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-441">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="3cbcc-442">また、サービスは X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-442">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="3cbcc-443">使用するバインディングは、クライアントによって生成され、サービスの公開キーで暗号化されたキーを保護トークンとして使用する対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-443">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="3cbcc-444">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-444">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="3cbcc-445">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="3cbcc-445">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="3cbcc-446">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-446">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-75305d4e-f54f-4e36-9de9-45b6d2053c80-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-75305d4e-f54f-4e36-9de9-45b6d2053c80-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_2" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><o:BinarySecurityToken> ...</o:BinarySecurityToken><e:EncryptedData Id="_9" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_10" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-447">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-447">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-8c73fa91-f95b-40ff-b088-48118e6fadcf-5"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_3" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_9" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_10" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-448">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-448">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="3cbcc-449">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="3cbcc-449">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="3cbcc-450">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-450">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-0b940a9e-606f-43b9-b05d-a162043529bc-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-0b940a9e-606f-43b9-b05d-a162043529bc-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><o:BinarySecurityToken> ... </o:BinarySecurityToken><Signature Id="_2" xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-451">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-451">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-67dacc31-4a50-4866-b673-ccc03e156337-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><k:SignatureConfirmation u:Id="_2" Value="mYyksUQKkK27Fd6hmgOiqFwvudk=" xmlns:k="http://docs.oasis-open.org/wss/oasis-wss-wssecurity-secext-1.1.xsd"></k:SignatureConfirmation><k:SignatureConfirmation u:Id="_3" Value="SreOZ4Rr2BcXjFQFvgN55ERypI/1/86hdWThE5lav0eYIxF1OCzQgZF+y7cQ82t+g3CRnLbE3c52DqMpY/HXlrdMct3m3rnpDH+fqdhNY4fE+M2v4zUMFR7uxDKWcEm9zZpmUvJCDfJRfKRaKjy5cTbccRKqSxw7HAqOYnqibA4=" xmlns:k="http://docs.oasis-open.org/wss/oasis-wss-wssecurity-secext-1.1.xsd"></k:SignatureConfirmation><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="327-issuedtokenforcertificate"></a><span data-ttu-id="3cbcc-452">3.2.7 IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="3cbcc-452">3.2.7 IssuedTokenForCertificate</span></span>  
 <span data-ttu-id="3cbcc-453">この認証モードでは、クライアントはサービスに対する認証を行わず、STS により発行されたトークンを示すことで、共有キーの有無を示します。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-453">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="3cbcc-454">発行済みトークンは、保証サポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-454">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="3cbcc-455">X.509 証明書を使用したクライアントに対するサービス認証。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-455">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="3cbcc-456">使用するバインディングは、クライアントによって生成され、サービスの公開キーで暗号化されたキーを保護トークンとして使用する対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-456">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="3cbcc-457">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-457">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenForCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ...  </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="3cbcc-458">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="3cbcc-458">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="3cbcc-459">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-459">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-1d2c03e6-0b69-4483-903a-6ef9b9d286ed-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-3f0f57fa-046d-40c0-919f-d0d7aa640b9f-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-460">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-460">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-3f0f57fa-046d-40c0-919f-d0d7aa640b9f-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="3cbcc-461">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="3cbcc-461">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="3cbcc-462">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-462">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenForCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ...  </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
 <span data-ttu-id="3cbcc-463">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-463">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-de1c51aa-2ecc-4e70-b6bd-9dca58331fa7-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-96c5e80a-9b87-4c6f-af77-752ca65cf607-16" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-464">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-464">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-96c5e80a-9b87-4c6f-af77-752ca65cf607-21"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
## <a name="33-kerberos"></a><span data-ttu-id="3cbcc-465">3.3 Kerberos</span><span class="sxs-lookup"><span data-stu-id="3cbcc-465">3.3 Kerberos</span></span>  
 <span data-ttu-id="3cbcc-466">この認証モードを使用すると、クライアントは Kerberos チケットを使用してサービスに対する認証を行います。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-466">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="3cbcc-467">また、その同じチケットによってサーバーが認証されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-467">That same ticket also provides server authentication.</span></span> <span data-ttu-id="3cbcc-468">使用するバインディングは、以下のプロパティが設定された対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-468">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="3cbcc-469">保護トークン: インクルード モードが .../IncludeToken/Once に設定された Kerberos チケット</span><span class="sxs-lookup"><span data-stu-id="3cbcc-469">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="3cbcc-470">トークンの保護 : False</span><span class="sxs-lookup"><span data-stu-id="3cbcc-470">Token Protection: False</span></span>  
  
 <span data-ttu-id="3cbcc-471">ヘッダーと本文全体の署名 : True</span><span class="sxs-lookup"><span data-stu-id="3cbcc-471">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="3cbcc-472">保護の順序 : SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="3cbcc-472">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="3cbcc-473">署名の暗号化 : True</span><span class="sxs-lookup"><span data-stu-id="3cbcc-473">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="3cbcc-474">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-474">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="Kerberos_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:KerberosToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Once"><wsp:Policy><sp:RequireDerivedKeys/><sp:WssGssKerberosV5ApReqToken11/></wsp:Policy></sp:KerberosToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic128/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="3cbcc-475">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="3cbcc-475">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="3cbcc-476">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-476">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-e8f6dc3b-407d-4387-bd33-97aedfd8bf13-2"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-477">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-477">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-7b03568e-66ae-49da-82ee-5d12d372876e-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-478">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-478">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="Kerberos_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:KerberosToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Once"><wsp:Policy><sp:RequireDerivedKeys/><sp:WssGssKerberosV5ApReqToken11/></wsp:Policy></sp:KerberosToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic128/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="3cbcc-479">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="3cbcc-479">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="3cbcc-480">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-480">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d29247f0-f220-4e81-9a8d-a15f5ac31072-2"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-481">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-481">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-9025b930-4f15-42fe-8e78-35d3a3480177-2"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="34-issuedtoken"></a><span data-ttu-id="3cbcc-482">3.4 発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="3cbcc-482">3.4 IssuedToken</span></span>  
 <span data-ttu-id="3cbcc-483">この認証モードでは、クライアントはサービスに対する認証を行わず、STS により発行されたトークンを示すことで、共有キーの有無を示します。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-483">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="3cbcc-484">サービスはクライアントに対する認証を行いませんが、そのサービスだけがキーを復号化できるように、STS は発行されたトークンの一部として共有キーを暗号化します。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-484">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="3cbcc-485">使用するバインディングは、以下のプロパティが設定された対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-485">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="3cbcc-486">保護トークン: インクルード モードが .../IncludeToken/AlwaysToRecipient に設定された発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="3cbcc-486">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="3cbcc-487">トークンの保護 : False</span><span class="sxs-lookup"><span data-stu-id="3cbcc-487">Token Protection: False</span></span>  
  
 <span data-ttu-id="3cbcc-488">ヘッダーと本文全体の署名 : True</span><span class="sxs-lookup"><span data-stu-id="3cbcc-488">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="3cbcc-489">保護の順序 : SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="3cbcc-489">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="3cbcc-490">署名の暗号化 : True</span><span class="sxs-lookup"><span data-stu-id="3cbcc-490">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="3cbcc-491">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-491">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="IssuedToken_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ...  </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="3cbcc-492">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="3cbcc-492">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="3cbcc-493">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-493">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-61ce3989-bc38-4d67-8262-6232c9d49a26-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-7e2d2617-1c28-465a-be30-de4a78cfc0e2-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-494">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-494">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-7e2d2617-1c28-465a-be30-de4a78cfc0e2-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>
```  
  
 <span data-ttu-id="3cbcc-495">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-495">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="IssuedToken_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ...  </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="3cbcc-496">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="3cbcc-496">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="3cbcc-497">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-497">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-1dc8bdef-4202-4e08-8a5e-ab94da579dec-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-7e004f51-63a3-4069-9b03-6a1a311a3181-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-498">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-498">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-7e004f51-63a3-4069-9b03-6a1a311a3181-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> </c:DerivedKeyToken> ... <c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
### <a name="35-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="3cbcc-499">3.5 サービス認証に Ssl ネゴシエーションを使用する</span><span class="sxs-lookup"><span data-stu-id="3cbcc-499">3.5 Using SslNegotiated for Service Authentication</span></span>  
 <span data-ttu-id="3cbcc-500">このセクションでは、WS-SecureConversation (WS-SC) ごとのセキュリティ コンテキスト トークンである保護トークンと共に、対称バインディングを使用する認証モードのグループについて説明します。WS-SecureConversation (WS-SC) のキー値は、WS-Trust (WS-T) RST/RSTR メッセージで TLS プロトコルを実行することによりネゴシエートされます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-500">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="3cbcc-501">WS-Trust を使用した TLS ハンドシェイク実装の詳細は、TLSNEGO に記述されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-501">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="3cbcc-502">ここで示すメッセージの例は、セキュリティ コンテキストに関連付けられた SCT が、ハンドシェイクによって既に確立されていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-502">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="3cbcc-503">使用するバインディングは、以下のプロパティが設定された対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-503">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="3cbcc-504">保護トークン: インクルード モードが .../IncludeToken/Never に設定された SslContextToken</span><span class="sxs-lookup"><span data-stu-id="3cbcc-504">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="3cbcc-505">トークンの保護 : False</span><span class="sxs-lookup"><span data-stu-id="3cbcc-505">Token Protection: False</span></span>  
  
 <span data-ttu-id="3cbcc-506">ヘッダーと本文全体の署名 : True</span><span class="sxs-lookup"><span data-stu-id="3cbcc-506">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="3cbcc-507">保護の順序 : SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="3cbcc-507">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="3cbcc-508">署名の暗号化 : True</span><span class="sxs-lookup"><span data-stu-id="3cbcc-508">Encrypt Signature: True</span></span>  
  
#### <a name="351-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="3cbcc-509">3.5.1 SslNegotiated サービス認証のポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-509">3.5.1 Policy for SslNegotiated service authentication</span></span>  
 <span data-ttu-id="3cbcc-510">このセクションで説明するすべての認証モードのポリシーは、使用する署名付きサポート トークンまたは保証トークンだけが異なります。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-510">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
#### <a name="352-anonymousforsslnegotiated"></a><span data-ttu-id="3cbcc-511">3.5.2 AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="3cbcc-511">3.5.2 AnonymousForSslNegotiated</span></span>  
 <span data-ttu-id="3cbcc-512">この認証モードでは、クライアントは匿名になり、X.509 証明書を使用してサービスが認証されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-512">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="3cbcc-513">使用するバインディングは、前述の 3.5.1 に示した対称バインディングのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-513">The binding used is an instance of symmetric binding as described in 3.5.1 above.</span></span>  
  
 <span data-ttu-id="3cbcc-514">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-514">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="AnonymousForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="3cbcc-515">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="3cbcc-515">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="3cbcc-516">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-516">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-f4b86ce2-4ba6-4c55-bac1-2e920fc6d5db-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-d21ec2b8-99f5-443c-a4c6-a4d40619187e-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-517">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-517">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d21ec2b8-99f5-443c-a4c6-a4d40619187e-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-518">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-518">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="AnonymousForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="3cbcc-519">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="3cbcc-519">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="3cbcc-520">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-520">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-c84b24b9-39e0-4cc3-99e2-cec088f1b9eb-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-df206ad9-1ee2-46d7-9fb4-6e4631c9762f-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-521">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-521">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-df206ad9-1ee2-46d7-9fb4-6e4631c9762f-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="353-usernameforsslnegotiated"></a><span data-ttu-id="3cbcc-522">3.5.3 UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="3cbcc-522">3.5.3 UserNameForSslNegotiated</span></span>  
 <span data-ttu-id="3cbcc-523">この認証モードでは、クライアントはユーザー名トークンを使用して認証を行います。ユーザー名トークンは、署名付きサポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-523">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="3cbcc-524">サービスは X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-524">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="3cbcc-525">使用するバインディングは、3.5.1 で説明した対称バインディングのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-525">The binding used is an instance of symmetric binding as described in 3.5.1.</span></span>  
  
 <span data-ttu-id="3cbcc-526">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-526">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="UserNameForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="3cbcc-527">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="3cbcc-527">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="3cbcc-528">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-528">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-3d1a12c3-e690-474a-a223-a346fc0329a9-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-137ea768-7d49-404b-87eb-f11d9c7154aa-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_9" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-529">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-529">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-137ea768-7d49-404b-87eb-f11d9c7154aa-5"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-530">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-530">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="UserNameForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="3cbcc-531">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="3cbcc-531">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="3cbcc-532">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-532">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-56e931e8-20c2-457f-a83e-8fcd6b92c258-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-83d053cb-03a0-4461-9616-86475cf083c4-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-533">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-533">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-83d053cb-03a0-4461-9616-86475cf083c4-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="354-issuedtokenforsslnegotiated"></a><span data-ttu-id="3cbcc-534">3.5.4 IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="3cbcc-534">3.5.4 IssuedTokenForSslNegotiated</span></span>  
 <span data-ttu-id="3cbcc-535">この認証モードでは、クライアントはサービスに対する認証を行わず、STS により発行されたトークンを示すことで、共有キーの有無を示します。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-535">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="3cbcc-536">発行済みトークンは、保証サポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-536">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="3cbcc-537">サービスは X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-537">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="3cbcc-538">使用するバインディングは、前述の 3.5.1 に示した対称バインディングのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-538">The binding used is an instance of symmetric binding as described in 3.5.1 above.</span></span>  
  
 <span data-ttu-id="3cbcc-539">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-539">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ... </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="3cbcc-540">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="3cbcc-540">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="3cbcc-541">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-541">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-b19fb2e7-8f0c-45c1-b62c-45d6ff6d57e7-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-199509f9-7963-42b7-b340-7598ee261d5a-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-542">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-542">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-199509f9-7963-42b7-b340-7598ee261d5a-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-543">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-543">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ... </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="3cbcc-544">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="3cbcc-544">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="3cbcc-545">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-545">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d75104d5-313e-440f-b112-db8aff57a5fe-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-e668caab-b7e4-4056-ac42-4015ae2a67a6-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-546">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-546">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-e668caab-b7e4-4056-ac42-4015ae2a67a6-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
#### <a name="355-mutualsslnegotiated"></a><span data-ttu-id="3cbcc-547">3.5.5 MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="3cbcc-547">3.5.5 MutualSslNegotiated</span></span>  
 <span data-ttu-id="3cbcc-548">この認証モードでは、クライアントとサービスは X.509 証明書を使用して認証を行います。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-548">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="3cbcc-549">使用するバインディングは、前述の 3.5.1 に示した対称バインディングのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-549">The binding used is an instance of symmetric binding as described in 3.5.1 above.</span></span>  
  
 <span data-ttu-id="3cbcc-550">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-550">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><mssp:RequireClientCertificate/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="3cbcc-551">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="3cbcc-551">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="3cbcc-552">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-552">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d1e6037e-8a64-494f-9447-07d3125b81b5-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-e4b73625-3011-4f6d-a6f9-4d682e860801-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-553">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-553">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-e4b73625-3011-4f6d-a6f9-4d682e860801-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-554">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-554">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><mssp:RequireClientCertificate/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="3cbcc-555">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="3cbcc-555">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="3cbcc-556">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-556">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-c2a6ab10-889a-4ee1-871d-05410c90fc10-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-ede0bd89-1f7e-4453-96ed-13e58c7ba8fe-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-557">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-557">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-ede0bd89-1f7e-4453-96ed-13e58c7ba8fe-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
### <a name="36-sspinegotiated"></a><span data-ttu-id="3cbcc-558">3.6 スパイネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="3cbcc-558">3.6 SspiNegotiated</span></span>  
 <span data-ttu-id="3cbcc-559">この認証モードを使用すると、クライアントとサーバーの認証を実行するために、ネゴシエーション プロトコルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-559">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="3cbcc-560">Kerberos を使用できる場合は Kerberos が使用され、それ以外の場合は NTLM が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-560">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="3cbcc-561">使用するバインディングは、以下のプロパティが設定された対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-561">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="3cbcc-562">保護トークン: インクルード モードが .../IncludeToken/AlwaysToRecipient に設定された SpnegoContextToken</span><span class="sxs-lookup"><span data-stu-id="3cbcc-562">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="3cbcc-563">トークンの保護 : False</span><span class="sxs-lookup"><span data-stu-id="3cbcc-563">Token Protection: False</span></span>  
  
 <span data-ttu-id="3cbcc-564">ヘッダーと本文全体の署名 : True</span><span class="sxs-lookup"><span data-stu-id="3cbcc-564">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="3cbcc-565">保護の順序 : SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="3cbcc-565">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="3cbcc-566">署名の暗号化 : True</span><span class="sxs-lookup"><span data-stu-id="3cbcc-566">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="3cbcc-567">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-567">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="SspiNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></sp:SpnegoContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="3cbcc-568">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="3cbcc-568">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="3cbcc-569">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-569">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-9a954fcb-4df2-4610-9800-f542f2b5130a-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-554d8cfc-e956-43db-9abb-afcafd024347-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-570">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-570">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-554d8cfc-e956-43db-9abb-afcafd024347-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>
```  
  
 <span data-ttu-id="3cbcc-571">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-571">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="SspiNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></sp:SpnegoContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="3cbcc-572">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="3cbcc-572">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="3cbcc-573">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-573">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-f1673773-f9a7-4b43-b13b-405e7dd4a6e3-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-e0aabc81-6942-4fe6-81bc-9def184565ea-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-574">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-574">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-e0aabc81-6942-4fe6-81bc-9def184565ea-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
### <a name="37-secureconversation"></a><span data-ttu-id="3cbcc-575">3.7 セキュア会話</span><span class="sxs-lookup"><span data-stu-id="3cbcc-575">3.7 SecureConversation</span></span>  
 <span data-ttu-id="3cbcc-576">使用するバインディングは、WS-SecureConversation (WS-SC) ごとの SCT を保護トークンとして使用する対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-576">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="3cbcc-577">入れ子になったバインディング (このバインディング自体も、ネゴシエーション プロトコルを使用する対称バインディングです) に従い、SCT は WS-Trust (WS-Trust) または WS-SecureConversation (WS-SC) を使用してネゴシエートされます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-577">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="3cbcc-578">ネゴシエーション プロトコルは、可能であれば Kerberos を使用してクライアントとサーバーの認証を行います。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-578">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="3cbcc-579">Kerberos を使用できない場合は、NTLM が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3cbcc-579">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="3cbcc-580">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-580">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="SecureConversation_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SecureConversationToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/><sp:BootstrapPolicy><wsp:Policy><sp:SignedParts xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><sp:Body/><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="From" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="FaultTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="ReplyTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="MessageID" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="RelatesTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="Action" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts><sp:EncryptedParts xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><sp:Body/></sp:EncryptedParts><sp:SymmetricBinding xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/></wsp:Policy></sp:SpnegoContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust10 xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust10></wsp:Policy></sp:BootstrapPolicy><sp:MustNotSendAmend/></wsp:Policy></sp:SecureConversationToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="3cbcc-581">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="3cbcc-581">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="3cbcc-582">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-582">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-f01c6159-f159-454d-bd97-bbcc9b8e25d3-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-582920d7-14a7-4adc-8091-e1f92d7d8055-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-583">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-583">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-582920d7-14a7-4adc-8091-e1f92d7d8055-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-584">ポリシー</span><span class="sxs-lookup"><span data-stu-id="3cbcc-584">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="SecureConversation_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SecureConversationToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/><sp:BootstrapPolicy><wsp:Policy><sp:SignedParts xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><sp:Body/><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="From" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="FaultTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="ReplyTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="MessageID" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="RelatesTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="Action" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts><sp:EncryptedParts xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><sp:Body/></sp:EncryptedParts><sp:SymmetricBinding xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/></wsp:Policy></sp:SpnegoContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust10 xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust10></wsp:Policy></sp:BootstrapPolicy><sp:MustNotSendAmend/></wsp:Policy></sp:SecureConversationToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="3cbcc-585">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="3cbcc-585">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="3cbcc-586">Request</span><span class="sxs-lookup"><span data-stu-id="3cbcc-586">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d57e6342-1c68-4095-a0c1-41979088a944-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-9b22407d-b914-4c41-9105-1cf8cf7c3fe5-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="3cbcc-587">Response</span><span class="sxs-lookup"><span data-stu-id="3cbcc-587">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-9b22407d-b914-4c41-9105-1cf8cf7c3fe5-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```
