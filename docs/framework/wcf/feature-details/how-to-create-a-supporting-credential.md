---
title: '方法: サポート資格情報を作成する'
ms.date: 03/30/2017
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
ms.openlocfilehash: b181ac72c9f197e9e404f7aa0f04e254abac10da
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557399"
---
# <a name="how-to-create-a-supporting-credential"></a><span data-ttu-id="8ca23-102">方法: サポート資格情報を作成する</span><span class="sxs-lookup"><span data-stu-id="8ca23-102">How to: Create a Supporting Credential</span></span>
<span data-ttu-id="8ca23-103">カスタムのセキュリティ スキームでは、複数の資格情報が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="8ca23-103">It is possible to have a custom security scheme that requires more than one credential.</span></span> <span data-ttu-id="8ca23-104">たとえば、サービスが、ユーザー名とパスワードだけでなく、クライアントが 18 歳以上であることを証明する資格情報もクライアントに要求することがあります。</span><span class="sxs-lookup"><span data-stu-id="8ca23-104">For example, a service may demand from the client not just a user name and password, but also a credential that proves the client is over the age of 18.</span></span> <span data-ttu-id="8ca23-105">2番目の資格情報は、 *サポート資格情報*です。</span><span class="sxs-lookup"><span data-stu-id="8ca23-105">The second credential is a *supporting credential*.</span></span> <span data-ttu-id="8ca23-106">このトピックでは、Windows Communication Foundation (WCF) クライアントでこのような資格情報を実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8ca23-106">This topic explains how to implement such credentials in an Windows Communication Foundation (WCF) client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8ca23-107">サポート資格情報の仕様は、WS-SecurityPolicy 仕様の一部です。</span><span class="sxs-lookup"><span data-stu-id="8ca23-107">The specification for supporting credentials is part of the WS-SecurityPolicy specification.</span></span> <span data-ttu-id="8ca23-108">詳細については、「 [Web Services Security の仕様](/previous-versions/dotnet/articles/ms951273(v=msdn.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ca23-108">For more information, see [Web Services Security Specifications](/previous-versions/dotnet/articles/ms951273(v=msdn.10)).</span></span>  
  
## <a name="supporting-tokens"></a><span data-ttu-id="8ca23-109">トークンのサポート</span><span class="sxs-lookup"><span data-stu-id="8ca23-109">Supporting Tokens</span></span>  
 <span data-ttu-id="8ca23-110">簡単に言えば、メッセージセキュリティを使用する場合は、メッセージをセキュリティで保護するために、 *プライマリ資格情報* (たとえば、x.509 証明書または Kerberos チケット) が常に使用されます。</span><span class="sxs-lookup"><span data-stu-id="8ca23-110">In brief, when you use message security, a *primary credential* is always used to secure the message (for example, an X.509 certificate or a Kerberos ticket).</span></span>  
  
 <span data-ttu-id="8ca23-111">仕様で定義されているように、セキュリティバインディングでは、 *トークン* を使用してメッセージ交換をセキュリティで保護します。</span><span class="sxs-lookup"><span data-stu-id="8ca23-111">As defined by the specification, a security binding uses *tokens* to secure the message exchange.</span></span> <span data-ttu-id="8ca23-112">*トークン*は、セキュリティ資格情報の表現です。</span><span class="sxs-lookup"><span data-stu-id="8ca23-112">A *token* is a representation of a security credential.</span></span>  
  
 <span data-ttu-id="8ca23-113">セキュリティ バインディングは、セキュリティ バインディング ポリシーで特定されたプライマリ トークンを使用して、署名を作成します。</span><span class="sxs-lookup"><span data-stu-id="8ca23-113">The security binding uses a primary token identified in the security binding policy to create a signature.</span></span> <span data-ttu-id="8ca23-114">この署名は、 *メッセージ署名*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="8ca23-114">This signature is referred to as the *message signature*.</span></span>  
  
 <span data-ttu-id="8ca23-115">メッセージ署名に関連付けられたトークンによって提供されるクレームを増やすために、追加のトークンを指定できます。</span><span class="sxs-lookup"><span data-stu-id="8ca23-115">Additional tokens can be specified to augment the claims provided by the token associated with the message signature.</span></span>  
  
## <a name="endorsing-signing-and-encrypting"></a><span data-ttu-id="8ca23-116">保証、署名、および暗号化</span><span class="sxs-lookup"><span data-stu-id="8ca23-116">Endorsing, Signing, and Encrypting</span></span>  
 <span data-ttu-id="8ca23-117">サポート資格情報は、メッセージ内で送信される *サポートトークン* になります。</span><span class="sxs-lookup"><span data-stu-id="8ca23-117">A supporting credential results in a *supporting token* transmitted inside the message.</span></span> <span data-ttu-id="8ca23-118">WS-SecurityPolicy 仕様では、次の表に示すように、サポート トークンをメッセージに追加する方法が 4 つ定義されています。</span><span class="sxs-lookup"><span data-stu-id="8ca23-118">The WS-SecurityPolicy specification defines four ways to attach a supporting token to the message, as described in the following table.</span></span>  
  
|<span data-ttu-id="8ca23-119">目的</span><span class="sxs-lookup"><span data-stu-id="8ca23-119">Purpose</span></span>|<span data-ttu-id="8ca23-120">説明</span><span class="sxs-lookup"><span data-stu-id="8ca23-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8ca23-121">符号付き</span><span class="sxs-lookup"><span data-stu-id="8ca23-121">Signed</span></span>|<span data-ttu-id="8ca23-122">サポート トークンはセキュリティ ヘッダーに追加され、メッセージ署名によって署名されます。</span><span class="sxs-lookup"><span data-stu-id="8ca23-122">The supporting token is included in the security header and is signed by the message signature.</span></span>|  
|<span data-ttu-id="8ca23-123">保証</span><span class="sxs-lookup"><span data-stu-id="8ca23-123">Endorsing</span></span>|<span data-ttu-id="8ca23-124">保証 *トークン* は、メッセージ署名に署名します。</span><span class="sxs-lookup"><span data-stu-id="8ca23-124">An *endorsing token* signs the message signature.</span></span>|  
|<span data-ttu-id="8ca23-125">署名および保証</span><span class="sxs-lookup"><span data-stu-id="8ca23-125">Signed and Endorsing</span></span>|<span data-ttu-id="8ca23-126">署名付き保証トークンは、メッセージ署名から生成された `ds:Signature` 要素全体を署名し、それ自体がこのメッセージ署名によって署名されます。つまり、両方のトークン (メッセージ署名に使用されるトークンと署名付き保証トークン) がお互いに署名します。</span><span class="sxs-lookup"><span data-stu-id="8ca23-126">Signed, endorsing tokens sign the entire `ds:Signature` element produced from the message signature and are themselves signed by that message signature; that is, both tokens (the token used for the message signature and the signed endorsing token) sign each other.</span></span>|  
|<span data-ttu-id="8ca23-127">署名および暗号化</span><span class="sxs-lookup"><span data-stu-id="8ca23-127">Signed and Encrypting</span></span>|<span data-ttu-id="8ca23-128">暗号化された署名付きサポート トークンは、`wsse:SecurityHeader` に表示されたときに暗号化されている署名付きサポート トークンです。</span><span class="sxs-lookup"><span data-stu-id="8ca23-128">Signed, encrypted supporting tokens are signed supporting tokens that are also encrypted when they appear in the `wsse:SecurityHeader`.</span></span>|  
  
## <a name="programming-supporting-credentials"></a><span data-ttu-id="8ca23-129">サポート資格情報のプログラミング</span><span class="sxs-lookup"><span data-stu-id="8ca23-129">Programming Supporting Credentials</span></span>  
 <span data-ttu-id="8ca23-130">サポートトークンを使用するサービスを作成するには、を作成する必要があり [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="8ca23-130">To create a service that uses supporting tokens you must create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span> <span data-ttu-id="8ca23-131">(詳細については、「 [方法: カスタムバインディングを使用してカスタムバインディングを作成](how-to-create-a-custom-binding-using-the-securitybindingelement.md)する」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="8ca23-131">(For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span></span>  
  
 <span data-ttu-id="8ca23-132">カスタム バインドを作成する最初の手順は、次の 3 種類のいずれかのセキュリティ バインド要素を作成することです。</span><span class="sxs-lookup"><span data-stu-id="8ca23-132">The first step when creating a custom binding is to create a security binding element, which can be one of three types:</span></span>  
  
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="8ca23-133">すべてのクラスは、次の 4 つの関連プロパティを備えた <xref:System.ServiceModel.Channels.SecurityBindingElement> から継承します。</span><span class="sxs-lookup"><span data-stu-id="8ca23-133">All classes inherit from the <xref:System.ServiceModel.Channels.SecurityBindingElement>, which includes four relevant properties:</span></span>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a><span data-ttu-id="8ca23-134">スコープ</span><span class="sxs-lookup"><span data-stu-id="8ca23-134">Scopes</span></span>  
 <span data-ttu-id="8ca23-135">サポート資格情報には、次の 2 つのスコープがあります。</span><span class="sxs-lookup"><span data-stu-id="8ca23-135">Two scopes exist for supporting credentials:</span></span>  
  
- <span data-ttu-id="8ca23-136">エンド*ポイントサポートトークン*は、エンドポイントのすべての操作をサポートします。</span><span class="sxs-lookup"><span data-stu-id="8ca23-136">*Endpoint supporting tokens* support all operations of an endpoint.</span></span> <span data-ttu-id="8ca23-137">つまり、サポート トークンによって表される資格情報は、エンドポイントの任意の操作が呼び出されたときにいつでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="8ca23-137">That is, the credential that the supporting token represents can be used whenever any endpoint operations are invoked.</span></span>  
  
- <span data-ttu-id="8ca23-138">*操作* をサポートするトークンは、特定のエンドポイント操作だけをサポートします。</span><span class="sxs-lookup"><span data-stu-id="8ca23-138">*Operation supporting tokens* support only a specific endpoint operation.</span></span>  
  
 <span data-ttu-id="8ca23-139">プロパティ名に示されているように、サポート資格情報は必須またはオプションのどちらかになることができます。</span><span class="sxs-lookup"><span data-stu-id="8ca23-139">As indicated by the property names, supporting credentials can be either required or optional.</span></span> <span data-ttu-id="8ca23-140">つまり、サポート資格情報は必須ではありませんが、存在する場合は使用され、存在しない場合も認証は失敗しません。</span><span class="sxs-lookup"><span data-stu-id="8ca23-140">That is, if the supporting credential is used if it is present, although it is not necessary, but the authentication will not fail if it is not present.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="8ca23-141">手順</span><span class="sxs-lookup"><span data-stu-id="8ca23-141">Procedures</span></span>  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a><span data-ttu-id="8ca23-142">サポート資格情報を備えたカスタム バインドを作成するには</span><span class="sxs-lookup"><span data-stu-id="8ca23-142">To create a custom binding that includes supporting credentials</span></span>  
  
1. <span data-ttu-id="8ca23-143">セキュリティ バインド要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="8ca23-143">Create a security binding element.</span></span> <span data-ttu-id="8ca23-144">次の例では、<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 認証モードで `UserNameForCertificate` を作成します。</span><span class="sxs-lookup"><span data-stu-id="8ca23-144">The example below creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> with the `UserNameForCertificate` authentication mode.</span></span> <span data-ttu-id="8ca23-145"><xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="8ca23-145">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> method.</span></span>  
  
2. <span data-ttu-id="8ca23-146">サポート パラメーターを対応するプロパティ (`Endorsing`、`Signed`、`SignedEncrypted`、または `SignedEndorsed`) によって返される型のコレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="8ca23-146">Add the supporting parameter to the collection of types returned by the appropriate property (`Endorsing`, `Signed`, `SignedEncrypted`, or `SignedEndorsed`).</span></span> <span data-ttu-id="8ca23-147"><xref:System.ServiceModel.Security.Tokens> 名前空間に存在する型には、<xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters> など、一般的に使用される型があります。</span><span class="sxs-lookup"><span data-stu-id="8ca23-147">The types in the <xref:System.ServiceModel.Security.Tokens> namespace include commonly used types, such as the <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ca23-148">例</span><span class="sxs-lookup"><span data-stu-id="8ca23-148">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="8ca23-149">説明</span><span class="sxs-lookup"><span data-stu-id="8ca23-149">Description</span></span>  
 <span data-ttu-id="8ca23-150"><xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> のインスタンスを作成し、<xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> クラスのインスタンスを、Endorsing プロパティによって返されるコレクションに追加する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="8ca23-150">The following example creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and adds an instance of the <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> class to the collection the Endorsing property returned.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8ca23-151">コード</span><span class="sxs-lookup"><span data-stu-id="8ca23-151">Code</span></span>  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8ca23-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ca23-152">See also</span></span>

- [<span data-ttu-id="8ca23-153">方法: SecurityBindingElement を使用してカスタム バインドを作成する</span><span class="sxs-lookup"><span data-stu-id="8ca23-153">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
