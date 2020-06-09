---
title: '方法: 双方向コントラクトを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 500a75b6-998a-47d5-8e3b-24e3aba2a434
ms.openlocfilehash: e5b6c7eecce08a23490b6ab1991e4561d9462469
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598984"
---
# <a name="how-to-create-a-duplex-contract"></a><span data-ttu-id="ed6da-102">方法: 双方向コントラクトを作成する</span><span class="sxs-lookup"><span data-stu-id="ed6da-102">How to: Create a Duplex Contract</span></span>
<span data-ttu-id="ed6da-103">ここでは、双方向コントラクトを使用するメソッドを作成するための基本手順を示します。</span><span class="sxs-lookup"><span data-stu-id="ed6da-103">This topic shows the basic steps to create methods that use a duplex (two-way) contract.</span></span> <span data-ttu-id="ed6da-104">双方向コントラクトでは、クライアントとサーバーが互いに独立して通信できるため、どちらからでも相手の呼び出しを開始できます。</span><span class="sxs-lookup"><span data-stu-id="ed6da-104">A duplex contract allows clients and servers to communicate with each other independently so that either can initiate calls to the other.</span></span> <span data-ttu-id="ed6da-105">双方向コントラクトは、Windows Communication Foundation (WCF) サービスで使用可能な3つのメッセージパターンのうちの1つです。</span><span class="sxs-lookup"><span data-stu-id="ed6da-105">The duplex contract is one of three message patterns available to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="ed6da-106">他の 2 つのメッセージ パターンは、一方向および要求/応答です。</span><span class="sxs-lookup"><span data-stu-id="ed6da-106">The other two message patterns are one-way and request-reply.</span></span> <span data-ttu-id="ed6da-107">双方向コントラクトは、クライアントとサーバー間の 2 つの一方向コントラクトで構成され、メソッドの呼び出しが相互に関連付けられている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ed6da-107">A duplex contract consists of two one-way contracts between the client and the server and does not require that the method calls be correlated.</span></span> <span data-ttu-id="ed6da-108">サービスでクライアントに詳細を照会したり、クライアントで明示的にイベントを発生させたりする必要がある場合は、この種のコントラクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="ed6da-108">Use this kind of contract when your service must query the client for more information or explicitly raise events on the client.</span></span> <span data-ttu-id="ed6da-109">双方向コントラクト用のクライアントアプリケーションを作成する方法の詳細については、「[方法: 双方向コントラクトを使用してサービスにアクセスする](how-to-access-services-with-a-duplex-contract.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed6da-109">For more information about creating a client application for a duplex contract, see [How to: Access Services with a Duplex Contract](how-to-access-services-with-a-duplex-contract.md).</span></span> <span data-ttu-id="ed6da-110">実際のサンプルについては、[二重](../samples/duplex.md)サンプルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed6da-110">For a working sample, see the [Duplex](../samples/duplex.md) sample.</span></span>  
  
### <a name="to-create-a-duplex-contract"></a><span data-ttu-id="ed6da-111">双方向コントラクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="ed6da-111">To create a duplex contract</span></span>  
  
1. <span data-ttu-id="ed6da-112">双方向コントラクトのサーバー側を構成するインターフェイスを作成します。</span><span class="sxs-lookup"><span data-stu-id="ed6da-112">Create the interface that makes up the server side of the duplex contract.</span></span>  
  
2. <span data-ttu-id="ed6da-113">インターフェイスに <xref:System.ServiceModel.ServiceContractAttribute> クラスを適用します。</span><span class="sxs-lookup"><span data-stu-id="ed6da-113">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#3)]
     [!code-vb[S_WS_DualHttp#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#3)]  
  
3. <span data-ttu-id="ed6da-114">インターフェイスでメソッド署名を宣言します。</span><span class="sxs-lookup"><span data-stu-id="ed6da-114">Declare the method signatures in the interface.</span></span>  
  
4. <span data-ttu-id="ed6da-115">パブリック コントラクトの一部であることが必要な各メソッド シグネチャに、<xref:System.ServiceModel.OperationContractAttribute> クラスを適用します。</span><span class="sxs-lookup"><span data-stu-id="ed6da-115">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method signature that must be part of the public contract.</span></span>  
  
5. <span data-ttu-id="ed6da-116">クライアントでサービスが呼び出すことができる一連の操作を定義するコールバック インターフェイスを作成します。</span><span class="sxs-lookup"><span data-stu-id="ed6da-116">Create the callback interface that defines the set of operations that the service can invoke on the client.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#4)]
     [!code-vb[S_WS_DualHttp#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#4)]  
  
6. <span data-ttu-id="ed6da-117">コールバック インターフェイスでメソッド署名を宣言します。</span><span class="sxs-lookup"><span data-stu-id="ed6da-117">Declare the method signatures in the callback interface.</span></span>  
  
7. <span data-ttu-id="ed6da-118">パブリック コントラクトの一部であることが必要な各メソッド シグネチャに、<xref:System.ServiceModel.OperationContractAttribute> クラスを適用します。</span><span class="sxs-lookup"><span data-stu-id="ed6da-118">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method signature that must be part of the public contract.</span></span>  
  
8. <span data-ttu-id="ed6da-119">プライマリ インターフェイスの <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> プロパティをコールバック インターフェイスの型に設定することにより、2 つのインターフェイスを双方向コントラクトにリンクします。</span><span class="sxs-lookup"><span data-stu-id="ed6da-119">Link the two interfaces into a duplex contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> property in the primary interface to the type of the callback interface.</span></span>  
  
### <a name="to-call-methods-on-the-client"></a><span data-ttu-id="ed6da-120">クライアントでメソッドを呼び出すには</span><span class="sxs-lookup"><span data-stu-id="ed6da-120">To call methods on the client</span></span>  
  
1. <span data-ttu-id="ed6da-121">サービスのプライマリ コントラクトの実装で、コールバック インターフェイスの変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="ed6da-121">In the service's implementation of the primary contract, declare a variable for the callback interface.</span></span>  
  
2. <span data-ttu-id="ed6da-122"><xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> クラスの <xref:System.ServiceModel.OperationContext> メソッドから返されるオブジェクト参照に変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="ed6da-122">Set the variable to the object reference returned by the <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> method of the <xref:System.ServiceModel.OperationContext> class.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#1)]
     [!code-vb[S_WS_DualHttp#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#1)]  
  
     [!code-csharp[S_WS_DualHttp#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#2)]
     [!code-vb[S_WS_DualHttp#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#2)]  
  
3. <span data-ttu-id="ed6da-123">コールバック インターフェイスで定義されたメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ed6da-123">Call the methods defined by the callback interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed6da-124">例</span><span class="sxs-lookup"><span data-stu-id="ed6da-124">Example</span></span>  
 <span data-ttu-id="ed6da-125">次のコード例は、双方向通信を示しています。</span><span class="sxs-lookup"><span data-stu-id="ed6da-125">The following code example demonstrates duplex communication.</span></span> <span data-ttu-id="ed6da-126">サービスのコントラクトには、順方向および逆方向に移動するためのサービス操作が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ed6da-126">The service’s contract contains service operations for moving forward and backward.</span></span> <span data-ttu-id="ed6da-127">クライアントのコントラクトには、位置を報告するためのサービス操作が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ed6da-127">The client’s contract contains a service operation for reporting its position.</span></span>  
  
 [!code-csharp[S_WS_DualHttp#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#5)]
 [!code-vb[S_WS_DualHttp#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#5)]  
  
- <span data-ttu-id="ed6da-128"><xref:System.ServiceModel.ServiceContractAttribute> 属性と <xref:System.ServiceModel.OperationContractAttribute> 属性を適用すると、サービス コントラクトの定義を Web サービス記述言語 (WSDL) で自動的に生成できます。</span><span class="sxs-lookup"><span data-stu-id="ed6da-128">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes allows the automatic generation of service contract definitions in the Web Services Description Language (WSDL).</span></span>  
  
- <span data-ttu-id="ed6da-129">[ServiceModel メタデータユーティリティツール (svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)を使用して、クライアントの WSDL ドキュメントおよび (省略可能な) コードと構成を取得します。</span><span class="sxs-lookup"><span data-stu-id="ed6da-129">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to retrieve the WSDL document and (optional) code and configuration for a client.</span></span>  
  
- <span data-ttu-id="ed6da-130">双方向サービスを公開しているエンドポイントは、セキュリティで保護されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ed6da-130">Endpoints exposing duplex services must be secured.</span></span> <span data-ttu-id="ed6da-131">サービスが双方向メッセージを受信すると、その受信メッセージの ReplyTo を参照して応答の送信先を決定します。</span><span class="sxs-lookup"><span data-stu-id="ed6da-131">When a service receives a duplex message, it looks at the ReplyTo in that incoming message to determine where to send the reply.</span></span> <span data-ttu-id="ed6da-132">チャネルがセキュリティで保護されていない場合、信頼関係のないクライアントが対象コンピューターの ReplyTo を使用して悪意のあるメッセージを送信し、その対象コンピューターのサービス拒否 (DOS: Denial Of Service) を引き起こす可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ed6da-132">If the channel is not secured, then an untrusted client could send a malicious message with a target machine's ReplyTo, leading to a denial of service of the target machine.</span></span> <span data-ttu-id="ed6da-133">通常の要求/応答メッセージでは、ReplyTo は無視され、元のメッセージを受信したチャネルで応答が送信されます。したがって、この問題は発生しません。</span><span class="sxs-lookup"><span data-stu-id="ed6da-133">With regular request-reply messages, this is not an issue, because the ReplyTo is ignored and the response is sent on the channel the original message came in on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed6da-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="ed6da-134">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="ed6da-135">方法: 双方向コントラクトを使用してサービスにアクセスする</span><span class="sxs-lookup"><span data-stu-id="ed6da-135">How to: Access Services with a Duplex Contract</span></span>](how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="ed6da-136">二重</span><span class="sxs-lookup"><span data-stu-id="ed6da-136">Duplex</span></span>](../samples/duplex.md)
- [<span data-ttu-id="ed6da-137">サービスの設計と実装</span><span class="sxs-lookup"><span data-stu-id="ed6da-137">Designing and Implementing Services</span></span>](../designing-and-implementing-services.md)
- [<span data-ttu-id="ed6da-138">方法: サービス コントラクトを定義する</span><span class="sxs-lookup"><span data-stu-id="ed6da-138">How to: Define a Service Contract</span></span>](../how-to-define-a-wcf-service-contract.md)
- [<span data-ttu-id="ed6da-139">セッション</span><span class="sxs-lookup"><span data-stu-id="ed6da-139">Session</span></span>](../samples/session.md)
