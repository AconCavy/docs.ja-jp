---
title: '方法: Svcutil.exe を使用してメタデータ ドキュメントをダウンロードする'
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: c04b63fa4963a5df0f910da8702643a6484a4edd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596930"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a><span data-ttu-id="9e9fe-102">方法: Svcutil.exe を使用してメタデータ ドキュメントをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="9e9fe-102">How to: Use Svcutil.exe to Download Metadata Documents</span></span>
<span data-ttu-id="9e9fe-103">Svcutil.exe を使用すると、実行中のサービスからメタデータをダウンロードして、ローカル ファイルに保存できます。</span><span class="sxs-lookup"><span data-stu-id="9e9fe-103">You can use Svcutil.exe to download metadata from running services and to save the metadata to local files.</span></span> <span data-ttu-id="9e9fe-104">HTTP および HTTPS の URL スキームの場合、Svcutil.exe は Ws-metadataexchange と[XML Web サービス探索](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100))を使用してメタデータを取得しようとします。</span><span class="sxs-lookup"><span data-stu-id="9e9fe-104">For HTTP and HTTPS URL schemes, Svcutil.exe attempts to retrieve metadata using WS-MetadataExchange and [XML Web Service Discovery](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100)).</span></span> <span data-ttu-id="9e9fe-105">その他の URL スキームの場合、Svcutil.exe は WS-MetadataExchange のみを使用します。</span><span class="sxs-lookup"><span data-stu-id="9e9fe-105">For all other URL schemes, Svcutil.exe uses only WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="9e9fe-106">既定で、Svcutil.exe は <xref:System.ServiceModel.Description.MetadataExchangeBindings> クラスに定義されているバインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="9e9fe-106">By default, Svcutil.exe uses the bindings defined in the <xref:System.ServiceModel.Description.MetadataExchangeBindings> class.</span></span> <span data-ttu-id="9e9fe-107">WS-MetadataExchange で使用するバインディングを構成するには、Svcutil.exe の構成ファイル (svcutil.exe.config) でクライアント エンドポイントを定義する必要があります。このとき、クライアント エンドポイントが `IMetadataExchange` コントラクトを使用し、メタデータ エンドポイントのアドレスの URI (Uniform Resource Identifier) スキームと同じ名前を持つように定義します。</span><span class="sxs-lookup"><span data-stu-id="9e9fe-107">To configure the binding used for WS-MetadataExchange, you must define a client endpoint in the configuration file for Svcutil.exe (svcutil.exe.config) that uses the `IMetadataExchange` contract and that has the same name as the Uniform Resource Identifier (URI) scheme of the metadata endpoint address.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="9e9fe-108">Svcutil.exe を実行して、それぞれに同じ名前の操作が含まれている2つの異なるサービスコントラクトを公開するサービスのメタデータを取得する場合、Svcutil.exe によって "メタデータを取得できません" というエラーが表示されます。たとえば、操作を持つという名前のサービスコントラクトを公開 `ICarService` `Get(Car c)` し、同じサービスが操作を持つという名前のサービスコントラクトを公開するサービスがあるとし `IBookService` `Get(Book b)` ます。</span><span class="sxs-lookup"><span data-stu-id="9e9fe-108">When running Svcutil.exe to get metadata for a service that exposes two different service contracts that each contain an operation of the same name, Svcutil.exe displays an error saying, "Cannot obtain Metadata from ...." For example, if you have a service that exposes a service contract called `ICarService` that has an operation `Get(Car c)` and the same service exposes a service contract called `IBookService` that has an operation `Get(Book b)`.</span></span> <span data-ttu-id="9e9fe-109">この問題を回避するには、次のいずれかのようにします。</span><span class="sxs-lookup"><span data-stu-id="9e9fe-109">To work around this issue, do one of the following:</span></span>
>
> - <span data-ttu-id="9e9fe-110">操作の名前を変更する。</span><span class="sxs-lookup"><span data-stu-id="9e9fe-110">Rename one of the operations.</span></span>
> - <span data-ttu-id="9e9fe-111"><xref:System.ServiceModel.OperationContractAttribute.Name%2A> を別の名前に設定する。</span><span class="sxs-lookup"><span data-stu-id="9e9fe-111">Set the <xref:System.ServiceModel.OperationContractAttribute.Name%2A> to a different name.</span></span>
> - <span data-ttu-id="9e9fe-112"><xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> プロパティを使用して、操作の名前空間のいずれかを別の名前空間に設定する。</span><span class="sxs-lookup"><span data-stu-id="9e9fe-112">Set one of the operations' namespaces to a different namespace using the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>
  
## <a name="to-download-metadata-using-svcutilexe"></a><span data-ttu-id="9e9fe-113">Svcutil.exe を使用してメタデータをダウンロードするには</span><span class="sxs-lookup"><span data-stu-id="9e9fe-113">To download metadata using Svcutil.exe</span></span>  
  
1. <span data-ttu-id="9e9fe-114">次の場所で Svcutil.exe ツールを検索します。</span><span class="sxs-lookup"><span data-stu-id="9e9fe-114">Locate the Svcutil.exe tool at the following location:</span></span>  
  
     <span data-ttu-id="9e9fe-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span><span class="sxs-lookup"><span data-stu-id="9e9fe-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span></span>  
  
2. <span data-ttu-id="9e9fe-116">コマンド プロンプトで、次の形式を使用してツールを起動します。</span><span class="sxs-lookup"><span data-stu-id="9e9fe-116">At the command prompt, launch the tool using the following format.</span></span>  
  
    ```console
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     <span data-ttu-id="9e9fe-117">メタデータをダウンロードするには `/t:metadata` オプションを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e9fe-117">You must specify the `/t:metadata` option to download metadata.</span></span> <span data-ttu-id="9e9fe-118">このオプションを指定しないと、クライアントのコードと構成が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9e9fe-118">Otherwise, client code and configuration are generated.</span></span>  
  
3. <span data-ttu-id="9e9fe-119"><>引数には、 `url` メタデータを提供するサービスエンドポイントの URL、またはオンラインでホストされているメタデータドキュメントを指定します。</span><span class="sxs-lookup"><span data-stu-id="9e9fe-119">The <`url`>argument specifies the URL to a service endpoint that provides metadata or to a metadata document hosted online.</span></span> <span data-ttu-id="9e9fe-120"><`epr`> 引数は、 `EndpointAddress` ws-metadataexchange をサポートするサービスエンドポイントの ws-addressing を含む XML ファイルへのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="9e9fe-120">The <`epr`> argument specifies the path to an XML file that contains a WS-Addressing `EndpointAddress` for a service endpoint that supports WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="9e9fe-121">メタデータのダウンロードにこのツールを使用する方法の詳細については、「 [ServiceModel Metadata Utility tool (svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e9fe-121">For more options about using this tool for metadata download, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e9fe-122">例</span><span class="sxs-lookup"><span data-stu-id="9e9fe-122">Example</span></span>  
 <span data-ttu-id="9e9fe-123">次のコマンドにより、実行中のサービスからメタデータ ドキュメントがダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="9e9fe-123">The following command downloads metadata documents from a running service.</span></span>  
  
```console
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a><span data-ttu-id="9e9fe-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="9e9fe-124">See also</span></span>

- [<span data-ttu-id="9e9fe-125">ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="9e9fe-125">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
