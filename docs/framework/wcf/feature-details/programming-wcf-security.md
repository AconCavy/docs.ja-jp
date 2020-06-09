---
title: WCF セキュリティのプログラミング
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
ms.openlocfilehash: 2b3c96e91c0d6f01fa30b3b617449e7d4a148933
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596774"
---
# <a name="programming-wcf-security"></a><span data-ttu-id="f8351-102">WCF セキュリティのプログラミング</span><span class="sxs-lookup"><span data-stu-id="f8351-102">Programming WCF Security</span></span>
<span data-ttu-id="f8351-103">このトピックでは、セキュリティで保護された Windows Communication Foundation (WCF) アプリケーションの作成に使用される基本的なプログラミングタスクについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f8351-103">This topic describes the fundamental programming tasks used to create a secure Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="f8351-104">このトピックでは、*転送セキュリティ*と総称される認証、機密性、および整合性についてのみ説明します。</span><span class="sxs-lookup"><span data-stu-id="f8351-104">This topic covers only authentication, confidentiality, and integrity, collectively known as *transfer security*.</span></span> <span data-ttu-id="f8351-105">このトピックでは、承認 (リソースまたはサービスへのアクセスの制御) については説明しません。承認の詳細については、「[承認](authorization-in-wcf.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8351-105">This topic does not cover authorization (the control of access to resources or services); for information on authorization, see [Authorization](authorization-in-wcf.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8351-106">特に WCF に関するセキュリティの概念の概要については、MSDN の「 [Web サービス拡張機能 (WSE) 3.0 のシナリオ、パターン、実装ガイダンス](https://docs.microsoft.com/previous-versions/msp-n-p/ff648183(v=pandp.10))」で、一連のパターンとプラクティスに関するチュートリアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8351-106">For a valuable introduction to security concepts, especially in regard to WCF, see the set of patterns and practices tutorials on MSDN at [Scenarios, Patterns, and Implementation Guidance for Web Services Enhancements (WSE) 3.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff648183(v=pandp.10)).</span></span>  
  
 <span data-ttu-id="f8351-107">WCF セキュリティのプログラミングは、セキュリティモード、クライアント資格情報の種類、および資格情報の値を設定する3つの手順に基づいています。</span><span class="sxs-lookup"><span data-stu-id="f8351-107">Programming WCF security is based on three steps setting the following: the security mode, a client credential type, and the credential values.</span></span> <span data-ttu-id="f8351-108">これらの手順は、コードまたは構成を使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="f8351-108">You can perform these steps either through code or configuration.</span></span>  
  
## <a name="setting-the-security-mode"></a><span data-ttu-id="f8351-109">セキュリティ モードの設定</span><span class="sxs-lookup"><span data-stu-id="f8351-109">Setting the Security Mode</span></span>  
 <span data-ttu-id="f8351-110">ここでは、WCF のセキュリティモードを使用したプログラミングの一般的な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="f8351-110">The following explains the general steps for programming with the security mode in WCF:</span></span>  
  
1. <span data-ttu-id="f8351-111">アプリケーション要件を満たす適切な定義済みバインディングを選択します。</span><span class="sxs-lookup"><span data-stu-id="f8351-111">Select one of the predefined bindings appropriate to your application requirements.</span></span> <span data-ttu-id="f8351-112">バインディングの選択肢の一覧については、「[システム指定のバインディング](../system-provided-bindings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8351-112">For a list of the binding choices, see [System-Provided Bindings](../system-provided-bindings.md).</span></span> <span data-ttu-id="f8351-113">既定では、ほとんどのバインディングでセキュリティが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="f8351-113">By default, nearly every binding has security enabled.</span></span> <span data-ttu-id="f8351-114">1つの例外は <xref:System.ServiceModel.BasicHttpBinding> クラスです (構成を使用し [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) ます)。</span><span class="sxs-lookup"><span data-stu-id="f8351-114">The one exception is the <xref:System.ServiceModel.BasicHttpBinding> class (using configuration, the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md)).</span></span>  
  
     <span data-ttu-id="f8351-115">選択するバインディングによってトランスポートが決まります。</span><span class="sxs-lookup"><span data-stu-id="f8351-115">The binding you select determines the transport.</span></span> <span data-ttu-id="f8351-116">たとえば、<xref:System.ServiceModel.WSHttpBinding> はトランスポートとして HTTP を使用し、<xref:System.ServiceModel.NetTcpBinding> は TCP を使用します。</span><span class="sxs-lookup"><span data-stu-id="f8351-116">For example, <xref:System.ServiceModel.WSHttpBinding> uses HTTP as the transport; <xref:System.ServiceModel.NetTcpBinding> uses TCP.</span></span>  
  
2. <span data-ttu-id="f8351-117">バインディングのセキュリティ モードを選択します。</span><span class="sxs-lookup"><span data-stu-id="f8351-117">Select one of the security modes for the binding.</span></span> <span data-ttu-id="f8351-118">選択したバインディングによって、選択できるモードが決まります。</span><span class="sxs-lookup"><span data-stu-id="f8351-118">Note that the binding you select determines the available mode choices.</span></span> <span data-ttu-id="f8351-119">たとえば、<xref:System.ServiceModel.WSDualHttpBinding> を選択すると、トランスポート セキュリティを使用できません (このオプションはありません)。</span><span class="sxs-lookup"><span data-stu-id="f8351-119">For example, the <xref:System.ServiceModel.WSDualHttpBinding> does not allow transport security (it is not an option).</span></span> <span data-ttu-id="f8351-120">同様に、<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> や <xref:System.ServiceModel.NetNamedPipeBinding> を選択すると、メッセージ セキュリティを使用できません。</span><span class="sxs-lookup"><span data-stu-id="f8351-120">Similarly, neither the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> nor the <xref:System.ServiceModel.NetNamedPipeBinding> allows message security.</span></span>  
  
     <span data-ttu-id="f8351-121">次の 3 つの選択肢があります。</span><span class="sxs-lookup"><span data-stu-id="f8351-121">You have three choices:</span></span>  
  
    1. `Transport`  
  
         <span data-ttu-id="f8351-122">トランスポート セキュリティは、選択したバインディングが使用する機構に依存します。</span><span class="sxs-lookup"><span data-stu-id="f8351-122">Transport security depends on the mechanism that the binding you have selected uses.</span></span> <span data-ttu-id="f8351-123">たとえば、`WSHttpBinding` を使用している場合、セキュリティ機構は SSL (Secure Sockets Layer) です (これは、HTTPS プロトコルの機構でもあります)。</span><span class="sxs-lookup"><span data-stu-id="f8351-123">For example, if you are using `WSHttpBinding` then the security mechanism is Secure Sockets Layer (SSL) (also the mechanism for the HTTPS protocol).</span></span> <span data-ttu-id="f8351-124">一般に、トランスポート セキュリティの主な利点は、使用するトランスポートに関係なく、優れたスループットが得られることです。</span><span class="sxs-lookup"><span data-stu-id="f8351-124">Generally speaking, the main advantage of transport security is that it delivers good throughput no matter which transport you are using.</span></span> <span data-ttu-id="f8351-125">ただし、制限が 2 つあります。1 つは、ユーザーの認証に使用する資格情報の種類がトランスポート機構によって決まることです。</span><span class="sxs-lookup"><span data-stu-id="f8351-125">However, it does have two limitations: The first is that the transport mechanism dictates the credential type used to authenticate a user.</span></span> <span data-ttu-id="f8351-126">これは、異なる種類の資格情報を要求する他のサービスと相互運用する必要がある場合には不都合です。</span><span class="sxs-lookup"><span data-stu-id="f8351-126">This is a drawback only if a service needs to interoperate with other services that demand different types of credentials.</span></span> <span data-ttu-id="f8351-127">もう 1 つの制限は、メッセージ レベルでセキュリティが適用されないため、エンド ツー エンドではなく、ホップ単位でセキュリティが実装されることです。</span><span class="sxs-lookup"><span data-stu-id="f8351-127">The second is that, because the security is not applied at the message level, security is implemented in a hop-by-hop manner rather than end-to-end.</span></span> <span data-ttu-id="f8351-128">この 2 つ目の制限は、クライアントとサービス間のメッセージ パスに中継局が含まれている場合にのみ問題になります。</span><span class="sxs-lookup"><span data-stu-id="f8351-128">This latter limitation is an issue only if the message path between client and service includes intermediaries.</span></span> <span data-ttu-id="f8351-129">使用するトランスポートの詳細については、「[トランスポートの選択](choosing-a-transport.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8351-129">For more information about which transport to use, see [Choosing a Transport](choosing-a-transport.md).</span></span> <span data-ttu-id="f8351-130">トランスポートセキュリティの使用方法の詳細については、「[トランスポートセキュリティの概要](transport-security-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8351-130">For more information about using transport security, see [Transport Security Overview](transport-security-overview.md).</span></span>  
  
    2. `Message`  
  
         <span data-ttu-id="f8351-131">メッセージ セキュリティでは、メッセージの安全性を維持するために必要なヘッダーとデータがすべてのメッセージに含まれます。</span><span class="sxs-lookup"><span data-stu-id="f8351-131">Message security means that every message includes the necessary headers and data to keep the message secure.</span></span> <span data-ttu-id="f8351-132">ヘッダーの構成は変更可能であるため、任意の数の資格情報を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="f8351-132">Because the composition of the headers varies, you can include any number of credentials.</span></span> <span data-ttu-id="f8351-133">トランスポート機構で提供できない特殊な資格情報の種類を要求する他のサービスと相互運用している場合や、メッセージを複数のサービスで使用する必要があり、各サービスが異なる資格情報の種類を要求する場合には、これは重要な要素になります。</span><span class="sxs-lookup"><span data-stu-id="f8351-133">This becomes a factor if you are interoperating with other services that demand a specific credential type that a transport mechanism can't supply, or if the message must be used with more than one service, where each service demands a different credential type.</span></span>  
  
         <span data-ttu-id="f8351-134">詳細については、「[メッセージセキュリティ](message-security-in-wcf.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8351-134">For more information, see [Message Security](message-security-in-wcf.md).</span></span>  
  
    3. `TransportWithMessageCredential`  
  
         <span data-ttu-id="f8351-135">このモードを選択すると、トランスポート層を使用してメッセージの転送がセキュリティで保護されると同時に、他のサービスが必要とするさまざまな資格情報がすべてのメッセージに含まれます。</span><span class="sxs-lookup"><span data-stu-id="f8351-135">This choice uses the transport layer to secure the message transfer, while every message includes the rich credentials other services need.</span></span> <span data-ttu-id="f8351-136">これにより、トランスポート セキュリティのパフォーマンス上の利点とメッセージ セキュリティの豊富な資格情報の利点の両方が提供されます。</span><span class="sxs-lookup"><span data-stu-id="f8351-136">This combines the performance advantage of transport security with the rich credentials advantage of message security.</span></span> <span data-ttu-id="f8351-137">このモードは、<xref:System.ServiceModel.BasicHttpBinding>、<xref:System.ServiceModel.WSFederationHttpBinding>、<xref:System.ServiceModel.NetPeerTcpBinding>、および <xref:System.ServiceModel.WSHttpBinding> の各バインディングで使用できます。</span><span class="sxs-lookup"><span data-stu-id="f8351-137">This is available with the following bindings: <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding>, and <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
3. <span data-ttu-id="f8351-138">HTTP でトランスポート セキュリティを使用する (つまり、HTTPS を使用する) 場合は、SSL 証明書を使用してホストを構成し、ポートで SSL を有効にします。</span><span class="sxs-lookup"><span data-stu-id="f8351-138">If you decide to use transport security for HTTP (in other words, HTTPS), you must also configure the host with an SSL certificate and enable SSL on a port.</span></span> <span data-ttu-id="f8351-139">詳細については、「 [HTTP トランスポートセキュリティ](http-transport-security.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8351-139">For more information, see [HTTP Transport Security](http-transport-security.md).</span></span>  
  
4. <span data-ttu-id="f8351-140"><xref:System.ServiceModel.WSHttpBinding> を使用している場合、セキュリティで保護されたセッションを確立する必要がないときは、<xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> プロパティを `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="f8351-140">If you are using the <xref:System.ServiceModel.WSHttpBinding> and do not need to establish a secure session, set the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="f8351-141">セキュリティで保護されたセッションは、クライアントとサーバーが対称キーを使用してチャネルを作成するときに発生します (メッセージ交換中、やりとりが終了するまで、クライアントとサーバーの両方が同じキーを使用します)。</span><span class="sxs-lookup"><span data-stu-id="f8351-141">A secure session occurs when a client and service create a channel using a symmetric key (both client and server use the same key for the length of a conversation, until the dialog is closed).</span></span>  
  
## <a name="setting-the-client-credential-type"></a><span data-ttu-id="f8351-142">クライアント資格情報の種類の設定</span><span class="sxs-lookup"><span data-stu-id="f8351-142">Setting the Client Credential Type</span></span>  
 <span data-ttu-id="f8351-143">適切なクライアント資格情報の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="f8351-143">Select a client credential type as appropriate.</span></span> <span data-ttu-id="f8351-144">詳細については、「[資格情報の種類の選択](selecting-a-credential-type.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8351-144">For more information, see [Selecting a Credential Type](selecting-a-credential-type.md).</span></span> <span data-ttu-id="f8351-145">使用できるクライアント資格情報の種類は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f8351-145">The following client credential types are available:</span></span>  
  
- `Windows`  
  
- `Certificate`  
  
- `Digest`  
  
- `Basic`  
  
- `UserName`  
  
- `NTLM`  
  
- `IssuedToken`  
  
 <span data-ttu-id="f8351-146">モードの設定に応じて、資格情報の種類を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8351-146">Depending on how you set the mode, you must set the credential type.</span></span> <span data-ttu-id="f8351-147">たとえば、次の構成例に示すように、`wsHttpBinding` を選択しており、モードを "Message" に設定した場合は、Message 要素の `clientCredentialType` 属性の値を `None`、`Windows`、`UserName`、`Certificate`、および `IssuedToken` のいずれかに設定できます。</span><span class="sxs-lookup"><span data-stu-id="f8351-147">For example, if you have selected the `wsHttpBinding`, and have set the mode to "Message," then you can also set the `clientCredentialType` attribute of the Message element to one of the following values: `None`, `Windows`, `UserName`, `Certificate`, and `IssuedToken`, as shown in the following configuration example.</span></span>  
  
```xml  
<system.serviceModel>  
<bindings>  
  <wsHttpBinding>  
    <binding name="myBinding">  
      <security mode="Message"/>  
      <message clientCredentialType="Windows"/>  
    </binding>
  </wsHttpBinding>
</bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="f8351-148">または</span><span class="sxs-lookup"><span data-stu-id="f8351-148">Or in code:</span></span>  
  
 [!code-csharp[c_WsHttpService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#1)]
 [!code-vb[c_WsHttpService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#1)]  
  
## <a name="setting-service-credential-values"></a><span data-ttu-id="f8351-149">サービス資格情報の値の設定</span><span class="sxs-lookup"><span data-stu-id="f8351-149">Setting Service Credential Values</span></span>  
 <span data-ttu-id="f8351-150">クライアント資格情報の種類を選択したら、サービスとクライアントが使用する実際の資格情報を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8351-150">Once you select a client credential type, you must set the actual credentials for the service and client to use.</span></span> <span data-ttu-id="f8351-151">サービスでは、資格情報は <xref:System.ServiceModel.Description.ServiceCredentials> クラスを使用して設定します。また、資格情報は <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> クラスの <xref:System.ServiceModel.ServiceHostBase> プロパティによって返されます。</span><span class="sxs-lookup"><span data-stu-id="f8351-151">On the service, credentials are set using the <xref:System.ServiceModel.Description.ServiceCredentials> class and returned by the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property of the <xref:System.ServiceModel.ServiceHostBase> class.</span></span> <span data-ttu-id="f8351-152">使用しているバインディングによって、サービス資格情報の種類、選択されるセキュリティ モード、およびクライアント資格情報の種類が暗黙的に決まります。</span><span class="sxs-lookup"><span data-stu-id="f8351-152">The binding in use implies the service credential type, the security mode chosen, and the type of the client credential.</span></span> <span data-ttu-id="f8351-153">サービス資格情報の証明書を設定するコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="f8351-153">The following code sets a certificate for a service credential.</span></span>  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a><span data-ttu-id="f8351-154">クライアント資格情報の値の設定</span><span class="sxs-lookup"><span data-stu-id="f8351-154">Setting Client Credential Values</span></span>  
 <span data-ttu-id="f8351-155">クライアントでは、クライアント資格情報の値は <xref:System.ServiceModel.Description.ClientCredentials> クラスを使用して設定します。また、クライアント資格情報の値は <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> クラスの <xref:System.ServiceModel.ClientBase%601> プロパティから返されます。</span><span class="sxs-lookup"><span data-stu-id="f8351-155">On the client, set client credential values using the <xref:System.ServiceModel.Description.ClientCredentials> class and returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class.</span></span> <span data-ttu-id="f8351-156">TCP プロトコルを使用するクライアントで、資格情報として証明書を設定するコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="f8351-156">The following code sets a certificate as a credential on a client using the TCP protocol.</span></span>  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f8351-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8351-157">See also</span></span>

- [<span data-ttu-id="f8351-158">基本的な WCF プログラミング</span><span class="sxs-lookup"><span data-stu-id="f8351-158">Basic WCF Programming</span></span>](../basic-wcf-programming.md)
- [<span data-ttu-id="f8351-159">一般的なセキュリティ シナリオ</span><span class="sxs-lookup"><span data-stu-id="f8351-159">Common Security Scenarios</span></span>](common-security-scenarios.md)
