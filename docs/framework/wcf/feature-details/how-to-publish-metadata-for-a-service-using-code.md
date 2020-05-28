---
title: '方法: コードを使用してサービスのメタデータを公開する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
ms.openlocfilehash: db6bca8728789879f9bfea40904bfc80352d1dbe
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144917"
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a><span data-ttu-id="e54a1-102">方法: コードを使用してサービスのメタデータを公開する</span><span class="sxs-lookup"><span data-stu-id="e54a1-102">How to: Publish Metadata for a Service Using Code</span></span>
<span data-ttu-id="e54a1-103">これは、Windows Communication Foundation (WCF) サービスのメタデータの公開について説明する2つの操作方法に関するトピックの1つです。</span><span class="sxs-lookup"><span data-stu-id="e54a1-103">This is one of two how-to topics that discuss publishing metadata for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="e54a1-104">構成ファイルとコードを使用して、サービスがメタデータを公開する手段を指定する方法は 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="e54a1-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="e54a1-105">このトピックでは、コードを使用してサービスのメタデータを公開する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e54a1-105">This topic shows how to publish metadata for a service using a code.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="e54a1-106">このトピックでは、セキュリティで保護されていない方法でメタデータを公開する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e54a1-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="e54a1-107">クライアントは、サービスからメタデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="e54a1-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="e54a1-108">セキュリティで保護された方法でメタデータを公開するサービスが必要な場合は、</span><span class="sxs-lookup"><span data-stu-id="e54a1-108">If you require your service to publish metadata in a secure manner.</span></span> <span data-ttu-id="e54a1-109">「[カスタムセキュアメタデータエンドポイント](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e54a1-109">see [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="e54a1-110">構成ファイルでメタデータを公開する方法の詳細については、「[方法: 構成ファイルを使用してサービスのメタデータを公開](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e54a1-110">For more information about publishing metadata in a configuration file, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span> <span data-ttu-id="e54a1-111">メタデータを公開すると、クライアントが `?wsdl` クエリ文字列を使用した WS-Transfer GET 要求または HTTP/GET 要求によりメタデータを取得できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e54a1-111">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="e54a1-112">コードを機能させるには、基本的な WCF サービスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e54a1-112">To be sure that the code is working you must create a basic WCF service.</span></span> <span data-ttu-id="e54a1-113">次のコードは基本的な自己ホスト型サービスの例です。</span><span class="sxs-lookup"><span data-stu-id="e54a1-113">A basic self-hosted service is provided in the following code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a><span data-ttu-id="e54a1-114">コードでメタデータを公開するには</span><span class="sxs-lookup"><span data-stu-id="e54a1-114">To publish metadata in code</span></span>  
  
1. <span data-ttu-id="e54a1-115">コンソール アプリケーションのメイン メソッド内で、サービス型とベース アドレスを渡して <xref:System.ServiceModel.ServiceHost> オブジェクトをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="e54a1-115">Within the main method of a console application, instantiate a <xref:System.ServiceModel.ServiceHost> object by passing in the service type and the base address.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2. <span data-ttu-id="e54a1-116">手順 1. のコードのすぐ下に try ブロックを作成します。これにより、サービスの実行中にスローされる例外がすべてキャッチされます。</span><span class="sxs-lookup"><span data-stu-id="e54a1-116">Create a try block immediately below the code for step 1, this catches any exceptions that get thrown while the service is running.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3. <span data-ttu-id="e54a1-117">サービス ホストに <xref:System.ServiceModel.Description.ServiceMetadataBehavior> が含まれているかどうかを確認し、含まれていない場合は、新しい <xref:System.ServiceModel.Description.ServiceMetadataBehavior> インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e54a1-117">Check to see whether the service host already contains a <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, if not, create a new <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4. <span data-ttu-id="e54a1-118"><xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> プロパティを `true.` に設定します。</span><span class="sxs-lookup"><span data-stu-id="e54a1-118">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true.`</span></span>  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5. <span data-ttu-id="e54a1-119"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> には <xref:System.ServiceModel.Description.MetadataExporter> プロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e54a1-119">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> contains a <xref:System.ServiceModel.Description.MetadataExporter> property.</span></span> <span data-ttu-id="e54a1-120"><xref:System.ServiceModel.Description.MetadataExporter> には <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> プロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e54a1-120">The <xref:System.ServiceModel.Description.MetadataExporter> contains a <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property.</span></span> <span data-ttu-id="e54a1-121"><xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> プロパティの値を <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> に設定します。</span><span class="sxs-lookup"><span data-stu-id="e54a1-121">Set the value of the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>.</span></span> <span data-ttu-id="e54a1-122"><xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> プロパティを <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> に設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="e54a1-122">The <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property can also be set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>.</span></span> <span data-ttu-id="e54a1-123">に設定すると <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> 、メタデータエクスポーターは、"ws-policy 1.5 に準拠したメタデータを使用してポリシー情報を生成します。</span><span class="sxs-lookup"><span data-stu-id="e54a1-123">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> the metadata exporter generates policy information with the metadata that" conforms to WS-Policy 1.5.</span></span> <span data-ttu-id="e54a1-124"><xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> に設定すると、WS-Policy 1.2 に準拠したポリシー情報がメタデータ エクスポーターによって生成されます。</span><span class="sxs-lookup"><span data-stu-id="e54a1-124">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> the metadata exporter generates policy information that conforms to WS-Policy 1.2.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6. <span data-ttu-id="e54a1-125"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> インスタンスをサービス ホストの動作コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="e54a1-125">Add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance to the service host's behaviors collection.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7. <span data-ttu-id="e54a1-126">メタデータ交換エンドポイントをサービス ホストに追加します。</span><span class="sxs-lookup"><span data-stu-id="e54a1-126">Add the metadata exchange endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8. <span data-ttu-id="e54a1-127">アプリケーション エンドポイントをサービス ホストに追加します。</span><span class="sxs-lookup"><span data-stu-id="e54a1-127">Add an application endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    > <span data-ttu-id="e54a1-128">エンドポイントをサービスに追加しない場合、ランタイムによって既定のエンドポイントが追加されます。</span><span class="sxs-lookup"><span data-stu-id="e54a1-128">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="e54a1-129">この例では、サービスには <xref:System.ServiceModel.Description.ServiceMetadataBehavior> に設定された `true` があるので、サービスで公開メタデータも有効化されています。</span><span class="sxs-lookup"><span data-stu-id="e54a1-129">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, the service has publishing metadata enabled.</span></span> <span data-ttu-id="e54a1-130">既定のエンドポイントの詳細については、「 [WCF サービスの](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)構成と簡略化された構成の[簡略化](../../../../docs/framework/wcf/simplified-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e54a1-130">For more information about default endpoints, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
9. <span data-ttu-id="e54a1-131">サービス ホストを開き、受信呼び出しを待ちます。</span><span class="sxs-lookup"><span data-stu-id="e54a1-131">Open the service host and wait for incoming calls.</span></span> <span data-ttu-id="e54a1-132">ユーザーが Enter キーを押すと、サービス ホストが終了します。</span><span class="sxs-lookup"><span data-stu-id="e54a1-132">When the user presses ENTER, close the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. <span data-ttu-id="e54a1-133">コンソール アプリケーションをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="e54a1-133">Build and run the console application.</span></span>  
  
11. <span data-ttu-id="e54a1-134">Internet Explorer を使用してサービスのベースアドレス ( `http://localhost:8001/MetadataSample` このサンプルでは) を参照し、メタデータの公開が有効になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e54a1-134">Use Internet Explorer to browse to the base address of the service (`http://localhost:8001/MetadataSample` in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="e54a1-135">上部の "サービスを作成しました" のすぐ下に "Simple Service" と表示された Web ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e54a1-135">You should see a Web page displayed that says "Simple Service" at the top and immediately below "You have created a service."</span></span> <span data-ttu-id="e54a1-136">有効になっていない場合は、"このサービスのメタデータ公開は現在は無効になっています。" というメッセージが結果ページの上部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="e54a1-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
## <a name="example"></a><span data-ttu-id="e54a1-137">例</span><span class="sxs-lookup"><span data-stu-id="e54a1-137">Example</span></span>  
 <span data-ttu-id="e54a1-138">次のコード例は、コードでサービスのメタデータを公開する基本的な WCF サービスの実装を示しています。</span><span class="sxs-lookup"><span data-stu-id="e54a1-138">The following code example shows the implementation of a basic WCF service that publishes metadata for the service in code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="e54a1-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="e54a1-139">See also</span></span>

- [<span data-ttu-id="e54a1-140">方法: マネージド アプリケーションで WCF サービスをホストする</span><span class="sxs-lookup"><span data-stu-id="e54a1-140">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="e54a1-141">自己ホスト</span><span class="sxs-lookup"><span data-stu-id="e54a1-141">Self-Host</span></span>](../../../../docs/framework/wcf/samples/self-host.md)
- [<span data-ttu-id="e54a1-142">メタデータ アーキテクチャの概要</span><span class="sxs-lookup"><span data-stu-id="e54a1-142">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [<span data-ttu-id="e54a1-143">メタデータを使用する</span><span class="sxs-lookup"><span data-stu-id="e54a1-143">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [<span data-ttu-id="e54a1-144">方法: 構成ファイルを使用してサービスのメタデータを公開する</span><span class="sxs-lookup"><span data-stu-id="e54a1-144">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
