---
title: '方法: メタデータをサービス エンドポイントにインポートする'
ms.date: 03/30/2017
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
ms.openlocfilehash: 1de316b8e91739d5e3e24ff960e2cdfb33cc7fab
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597060"
---
# <a name="how-to-import-metadata-into-service-endpoints"></a><span data-ttu-id="23493-102">方法: メタデータをサービス エンドポイントにインポートする</span><span class="sxs-lookup"><span data-stu-id="23493-102">How to: Import Metadata into Service Endpoints</span></span>
<span data-ttu-id="23493-103">このトピックでは、サービスエンドポイントのコレクションにメタデータをインポートし、[はじめに](../samples/getting-started-sample.md)で定義されているサービスを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="23493-103">This topic explains how to import metadata into a collection of service endpoints and use the service defined in the [Getting Started](../samples/getting-started-sample.md).</span></span> <span data-ttu-id="23493-104">また、サービスからメタデータをインポートし、次にそのサービスに対して `Add` メソッドを呼び出すクライアント アプリケーションを作成する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="23493-104">This topic show how to create a client application that imports metadata from the service and then calls the `Add` method on the service.</span></span>  
  
### <a name="to-import-metadata-into-service-endpoints"></a><span data-ttu-id="23493-105">メタデータをサービス エンドポイントにインポートするには</span><span class="sxs-lookup"><span data-stu-id="23493-105">To import metadata into service endpoints</span></span>  
  
1. <span data-ttu-id="23493-106"><xref:System.ServiceModel.EndpointAddress> オブジェクトを定義し、サービスの metadata exchange (MEX) アドレスの URI (Uniform Resource Identifier) を使ってそのオブジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="23493-106">Declare an <xref:System.ServiceModel.EndpointAddress> object and initialize it with the Uniform Resource Identifier (URI) for the metadata exchange (MEX) address of the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2. <span data-ttu-id="23493-107"><xref:System.ServiceModel.Description.MetadataExchangeClient> を作成し、MEX アドレスを渡して <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="23493-107">Create a <xref:System.ServiceModel.Description.MetadataExchangeClient>, passing in the MEX address, and call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>.</span></span> <span data-ttu-id="23493-108">これにより、メタデータをサービスから取得します。</span><span class="sxs-lookup"><span data-stu-id="23493-108">This retrieves the metadata from the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3. <span data-ttu-id="23493-109"><xref:System.ServiceModel.Description.WsdlImporter> を作成し、前に取得したメタデータを渡して <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="23493-109">Create a <xref:System.ServiceModel.Description.WsdlImporter>, passing in the metadata previously retrieved, and call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>.</span></span> <span data-ttu-id="23493-110">これにより、<xref:System.ServiceModel.Description.ContractDescription> オブジェクトのコレクションを生成します。</span><span class="sxs-lookup"><span data-stu-id="23493-110">This generates a collection of <xref:System.ServiceModel.Description.ContractDescription> objects.</span></span> <span data-ttu-id="23493-111">必要に応じて、<xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> または <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A> を呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="23493-111">You could also call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> or <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, depending upon your needs.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    > <span data-ttu-id="23493-112">メタデータのインポートが完了すると、クライアント チャネルの作成もメタデータのエクスポートもできなくなります。</span><span class="sxs-lookup"><span data-stu-id="23493-112">After you have imported the metadata, you will not be able to create a client channel or export the metadata.</span></span> <span data-ttu-id="23493-113">これは、この時点で型情報を使用できないためです。</span><span class="sxs-lookup"><span data-stu-id="23493-113">This is because no type information is available at this point.</span></span> <span data-ttu-id="23493-114">型情報は、サービスと実際に対話する場合またはメタデータをエクスポートする場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="23493-114">Type information is required to actually interact with the service or export metadata.</span></span> <span data-ttu-id="23493-115">型情報を生成するには、コードを生成する必要があります。これについては、手順 4. ～ 5. で説明します。</span><span class="sxs-lookup"><span data-stu-id="23493-115">To generate the type information, you need to generate code, shown in steps 4 and 5.</span></span> <span data-ttu-id="23493-116">別の方法として、<xref:System.ServiceModel.Description.MetadataResolver> ヘルパー クラスを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="23493-116">Alternatively, you could use the <xref:System.ServiceModel.Description.MetadataResolver> helper class.</span></span> <span data-ttu-id="23493-117">詳細については、「[方法: MetadataResolver を使用してバインディングメタデータを動的に取得する](how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23493-117">For more information, see [How to: Use MetadataResolver to Obtain Binding Metadata Dynamically](how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).</span></span>  
  
4. <span data-ttu-id="23493-118">各コントラクトに型情報を生成します。</span><span class="sxs-lookup"><span data-stu-id="23493-118">Generate type information for each contract.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5. <span data-ttu-id="23493-119">これで、この情報を使用できます。</span><span class="sxs-lookup"><span data-stu-id="23493-119">Now you can use this information.</span></span> <span data-ttu-id="23493-120">次の例では、C# ソース コードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="23493-120">The following sample generates C# source code.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="23493-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="23493-121">See also</span></span>

- [<span data-ttu-id="23493-122">Metadata</span><span class="sxs-lookup"><span data-stu-id="23493-122">Metadata</span></span>](metadata.md)
- [<span data-ttu-id="23493-123">はじめに</span><span class="sxs-lookup"><span data-stu-id="23493-123">Getting Started</span></span>](../samples/getting-started-sample.md)
