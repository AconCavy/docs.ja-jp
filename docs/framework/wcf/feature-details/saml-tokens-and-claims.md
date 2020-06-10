---
title: SAML トークンとクレーム
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
- issued tokens
- SAML token
ms.assetid: 930b6e34-9eab-4e95-826c-4e06659bb977
ms.openlocfilehash: 6220365d5c43299a75d1e0fa8e46a7392b0ccaa2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590372"
---
# <a name="saml-tokens-and-claims"></a><span data-ttu-id="b3251-102">SAML トークンとクレーム</span><span class="sxs-lookup"><span data-stu-id="b3251-102">SAML Tokens and Claims</span></span>
<span data-ttu-id="b3251-103">セキュリティアサーションマークアップ言語 (SAML)*トークン*は、クレームの XML 表現です。</span><span class="sxs-lookup"><span data-stu-id="b3251-103">Security Assertions Markup Language (SAML) *tokens* are XML representations of claims.</span></span> <span data-ttu-id="b3251-104">既定では、フェデレーションセキュリティシナリオで使用される SAML トークン Windows Communication Foundation (WCF) では、*トークンが発行*されます。</span><span class="sxs-lookup"><span data-stu-id="b3251-104">By default, SAML tokens Windows Communication Foundation (WCF) uses in federated security scenarios are *issued tokens*.</span></span>  
  
 <span data-ttu-id="b3251-105">SAML トークンは、ステートメント (特定のエンティティによって他のエンティティに関して作成されるクレームのセット) を伝達します。</span><span class="sxs-lookup"><span data-stu-id="b3251-105">SAML tokens carry statements that are sets of claims made by one entity about another entity.</span></span> <span data-ttu-id="b3251-106">たとえば、フェデレーション セキュリティ シナリオでは、ステートメントがセキュリティ トークン サービスによって、システム内の特定のユーザーに関して作成されます。</span><span class="sxs-lookup"><span data-stu-id="b3251-106">For example, in federated security scenarios, the statements are made by a security token service about a user in the system.</span></span> <span data-ttu-id="b3251-107">セキュリティ トークン サービスは、トークンに含まれるステートメントの信憑性を示すために SAML トークンに署名します。</span><span class="sxs-lookup"><span data-stu-id="b3251-107">The security token service signs the SAML token to indicate the veracity of the statements contained in the token.</span></span> <span data-ttu-id="b3251-108">また、SAML トークンは、SAML トークンのユーザーが証明として提示する暗号化キー マテリアルに関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="b3251-108">In addition, the SAML token is associated with cryptographic key material that the user of the SAML token proves knowledge of.</span></span> <span data-ttu-id="b3251-109">これが証拠となり、証明書利用者は、SAML トークンが実際にそのユーザーに対して発行されたことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="b3251-109">This proof satisfies the relying party that the SAML token was, in fact, issued to that user.</span></span> <span data-ttu-id="b3251-110">一般的なシナリオでの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b3251-110">For example, in a typical scenario:</span></span>  
  
1. <span data-ttu-id="b3251-111">クライアントは、セキュリティ トークン サービスから SAML トークンを要求し、Windows 資格情報を使用して、そのセキュリティ トークン サービスに対して認証を行います。</span><span class="sxs-lookup"><span data-stu-id="b3251-111">A client requests a SAML token from a security token service, authenticating to that security token service by using Windows credentials.</span></span>  
  
2. <span data-ttu-id="b3251-112">セキュリティ トークン サービスは、SAML トークンをクライアントに発行します。</span><span class="sxs-lookup"><span data-stu-id="b3251-112">The security token service issues a SAML token to the client.</span></span> <span data-ttu-id="b3251-113">SAML トークンは、セキュリティ トークン サービスに関連付けられた証明書を使用して署名され、ターゲット サービス用に暗号化された証明キーを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="b3251-113">The SAML token is signed with a certificate associated with the security token service and contains a proof key encrypted for the target service.</span></span>  
  
3. <span data-ttu-id="b3251-114">クライアントは、*証明キー*のコピーも受け取ります。</span><span class="sxs-lookup"><span data-stu-id="b3251-114">The client also receives a copy of the *proof key*.</span></span> <span data-ttu-id="b3251-115">次に、クライアントは SAML トークンをアプリケーションサービス (*証明書利用者*) に提示し、その証明キーを使用してメッセージに署名します。</span><span class="sxs-lookup"><span data-stu-id="b3251-115">The client then presents the SAML token to the application service (the *relying party*) and signs the message with that proof key.</span></span>  
  
4. <span data-ttu-id="b3251-116">SAML トークンの署名は、そのトークンがセキュリティ トークン サービスによって発行されたことを証明書利用者に示します。</span><span class="sxs-lookup"><span data-stu-id="b3251-116">The signature over the SAML token tells the relying party that the security token service issued the token.</span></span> <span data-ttu-id="b3251-117">また、証明キーを使用して作成されたメッセージ署名は、トークンがそのクライアントに対して発行されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="b3251-117">The message signature created with the proof key tells the relying party that the token was issued to the client.</span></span>  
  
## <a name="from-claims-to-samlattributes"></a><span data-ttu-id="b3251-118">クレームから SamlAttributes</span><span class="sxs-lookup"><span data-stu-id="b3251-118">From Claims to SamlAttributes</span></span>  
 <span data-ttu-id="b3251-119">WCF では、SAML トークン内のステートメントはオブジェクトとしてモデル化されます。オブジェクトのプロパティがで、 <xref:System.IdentityModel.Tokens.SamlAttribute> <xref:System.IdentityModel.Claims.Claim> <xref:System.IdentityModel.Claims.Claim> <xref:System.IdentityModel.Claims.Claim.Right%2A> <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> <xref:System.IdentityModel.Claims.Claim.Resource%2A> プロパティが型 <xref:System.String> である場合は、オブジェクトから直接データを設定できます。</span><span class="sxs-lookup"><span data-stu-id="b3251-119">In WCF, statements in SAML tokens are modeled as <xref:System.IdentityModel.Tokens.SamlAttribute> objects, which can be populated directly from <xref:System.IdentityModel.Claims.Claim> objects, provided the <xref:System.IdentityModel.Claims.Claim> object has a <xref:System.IdentityModel.Claims.Claim.Right%2A> property of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> and the <xref:System.IdentityModel.Claims.Claim.Resource%2A> property is of type <xref:System.String>.</span></span> <span data-ttu-id="b3251-120">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="b3251-120">For example:</span></span>  
  
 [!code-csharp[c_CreateSTS#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#8)]
 [!code-vb[c_CreateSTS#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#8)]  
  
> [!NOTE]
> <span data-ttu-id="b3251-121">セキュリティ トークン サービスによって発行されたか、または認証の一部としてクライアントからサービスに提示されたときに、SAML トークンがメッセージ内にシリアル化される場合、メッセージの最大クォータ サイズが、SAML トークンおよびメッセージの他の部分を格納できるだけの大きさである必要があります。</span><span class="sxs-lookup"><span data-stu-id="b3251-121">When SAML tokens are serialized in messages, either when they are issued by a security token service or when they are presented by clients to services as part of authentication, the maximum message size quota must be sufficiently large to accommodate the SAML token and the other message parts.</span></span> <span data-ttu-id="b3251-122">通常は、既定のメッセージ クォータ サイズで十分です。</span><span class="sxs-lookup"><span data-stu-id="b3251-122">In normal cases, the default message size quotas are sufficient.</span></span> <span data-ttu-id="b3251-123">ただし、何百ものクレームを含んでいるために SAML トークンのサイズが大きい場合には、シリアル化されたトークンを格納できるように、クォータを増やす必要が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="b3251-123">However, in cases where a SAML token is large because it contains hundreds of claims, you may need to increase the quotas to accommodate the serialized token.</span></span> <span data-ttu-id="b3251-124">詳細については、「[データのセキュリティに関する考慮事項](security-considerations-for-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3251-124">For more information, see [Security Considerations for Data](security-considerations-for-data.md).</span></span>  
  
## <a name="from-samlattributes-to-claims"></a><span data-ttu-id="b3251-125">SamlAttributes からクレーム</span><span class="sxs-lookup"><span data-stu-id="b3251-125">From SamlAttributes to Claims</span></span>  
 <span data-ttu-id="b3251-126">SAML トークンがメッセージで受信されると、SAML トークン内のさまざまなステートメントは、 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> オブジェクトに変換され、<xref:System.IdentityModel.Policy.AuthorizationContext> に配置されます。</span><span class="sxs-lookup"><span data-stu-id="b3251-126">When SAML tokens are received in messages, the various statements in the SAML token are turned into <xref:System.IdentityModel.Policy.IAuthorizationPolicy> objects that are placed into the <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span> <span data-ttu-id="b3251-127">各 SAML ステートメントのクレームは <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> の <xref:System.IdentityModel.Policy.AuthorizationContext> プロパティによって返され、これを調べることによってユーザーの認証と承認を行うかどうかを決定できます。</span><span class="sxs-lookup"><span data-stu-id="b3251-127">The claims from each SAML statement are returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> and can be examined to determine whether to authenticate and authorize the user.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3251-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="b3251-128">See also</span></span>

- <xref:System.IdentityModel.Policy.AuthorizationContext>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- <xref:System.IdentityModel.Claims.ClaimSet>
- [<span data-ttu-id="b3251-129">フェデレーション</span><span class="sxs-lookup"><span data-stu-id="b3251-129">Federation</span></span>](federation.md)
- [<span data-ttu-id="b3251-130">方法: フェデレーション クライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="b3251-130">How to: Create a Federated Client</span></span>](how-to-create-a-federated-client.md)
- [<span data-ttu-id="b3251-131">方法: フェデレーション サービスで資格情報を設定する</span><span class="sxs-lookup"><span data-stu-id="b3251-131">How to: Configure Credentials on a Federation Service</span></span>](how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="b3251-132">ID モデルを使用したクレームと承認の管理</span><span class="sxs-lookup"><span data-stu-id="b3251-132">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)
- [<span data-ttu-id="b3251-133">クレームとトークン</span><span class="sxs-lookup"><span data-stu-id="b3251-133">Claims and Tokens</span></span>](claims-and-tokens.md)
- [<span data-ttu-id="b3251-134">クレームの作成とリソース値</span><span class="sxs-lookup"><span data-stu-id="b3251-134">Claim Creation and Resource Values</span></span>](claim-creation-and-resource-values.md)
- [<span data-ttu-id="b3251-135">方法: カスタム クレームを作成する</span><span class="sxs-lookup"><span data-stu-id="b3251-135">How to: Create a Custom Claim</span></span>](../extending/how-to-create-a-custom-claim.md)
