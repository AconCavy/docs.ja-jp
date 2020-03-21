---
title: '方法 : 構成でクライアント バインディングを指定する'
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: 574f56173c2acfcf41a5e9a9e99abe45281e3636
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184038"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a><span data-ttu-id="a3b84-102">方法 : 構成でクライアント バインディングを指定する</span><span class="sxs-lookup"><span data-stu-id="a3b84-102">How to: Specify a Client Binding in Configuration</span></span>
<span data-ttu-id="a3b84-103">この例では、電卓サービスを使用するためのクライアント コンソール アプリケーションを作成し、そのクライアントのバインディングを構成で宣言によって指定します。</span><span class="sxs-lookup"><span data-stu-id="a3b84-103">In this example, a client console application is created to use a calculator service, and the binding for that client is specified declaratively in configuration.</span></span> <span data-ttu-id="a3b84-104">クライアントは `CalculatorService` にアクセスします。これにより、`ICalculator` インターフェイスが実装され、サービスとクライアントの両方で <xref:System.ServiceModel.BasicHttpBinding> クラスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="a3b84-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="a3b84-105">ここで説明する手順は、電卓サービスが実行されていることを前提とします。</span><span class="sxs-lookup"><span data-stu-id="a3b84-105">The procedure outlined assumes that the calculator service is running.</span></span> <span data-ttu-id="a3b84-106">サービスの構築方法については、「方法 :[構成でサービス バインドを指定する](how-to-specify-a-service-binding-in-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3b84-106">For information about how to build the service, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="a3b84-107">また、クライアント コンポーネントを自動的に生成するために、Windows 通信ファウンデーション (WCF) が提供する[サービス モデル メタデータ ユーティリティ ツール (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)も使用します。</span><span class="sxs-lookup"><span data-stu-id="a3b84-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) that Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="a3b84-108">このツールにより、サービスにアクセスするためのクライアント コードと構成が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a3b84-108">The tool generates the client code and configuration for accessing the service.</span></span>  
  
 <span data-ttu-id="a3b84-109">クライアントは 2 つの部分で構成されます。</span><span class="sxs-lookup"><span data-stu-id="a3b84-109">The client is built in two parts.</span></span> <span data-ttu-id="a3b84-110">Svcutil.exe によって、`ClientCalculator` インターフェイスを実装する `ICalculator` が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a3b84-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="a3b84-111">次に、`ClientCalculator` のインスタンスを作成することで、クライアント アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="a3b84-111">This client application is then constructed by constructing an instance of `ClientCalculator`.</span></span>  
  
 <span data-ttu-id="a3b84-112">通常、ベスト プラクティスは、コードで命令として記述するよりも、構成でバインディングを指定して情報を明示的にアドレス指定することです。</span><span class="sxs-lookup"><span data-stu-id="a3b84-112">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="a3b84-113">設置済みサービスのバインドおよびアドレスは一般的に、サービスの開発中に使用されるものとは異なるので、コード内でエンドポイントを定義することは通常、実用的ではありません。</span><span class="sxs-lookup"><span data-stu-id="a3b84-113">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="a3b84-114">一般的に、バインディング情報とアドレス情報をコードに含めないことで、変更時にアプリケーションの再コンパイルや再展開を行う必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="a3b84-114">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="a3b84-115">[構成エディター ツール (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md)を使用して、次のすべての構成手順を実行できます。</span><span class="sxs-lookup"><span data-stu-id="a3b84-115">You can perform all of the following configuration steps by using the [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="a3b84-116">この例のソース コピーについては[、BasicBinding](./samples/basicbinding.md)サンプルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3b84-116">For the source copy of this example, see the [BasicBinding](./samples/basicbinding.md) sample.</span></span>  
  
### <a name="specifying-a-client-binding-in-configuration"></a><span data-ttu-id="a3b84-117">構成を使用したクライアント バインディングの指定</span><span class="sxs-lookup"><span data-stu-id="a3b84-117">Specifying a client binding in configuration</span></span>  
  
1. <span data-ttu-id="a3b84-118">コマンド ラインから Svcutil.exe を実行して、サービス メタデータからコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="a3b84-118">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="a3b84-119">生成されたクライアントには、クライアントの実装時に満たされなければならないサービス コントラクトを定義する `ICalculator` インターフェイスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a3b84-119">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. <span data-ttu-id="a3b84-120">生成されたクライアントは `ClientCalculator` も実装します。</span><span class="sxs-lookup"><span data-stu-id="a3b84-120">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. <span data-ttu-id="a3b84-121"><xref:System.ServiceModel.BasicHttpBinding> クラスを使用するクライアントの構成も、Svcutil.exe により生成されます。</span><span class="sxs-lookup"><span data-stu-id="a3b84-121">Svcutil.exe also generates the configuration for the client that uses the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span> <span data-ttu-id="a3b84-122">Visual Studio を使用する場合は、このファイルに App.config という名前を付けます。アドレスとバインディング情報は、サービスの実装内のどこにも指定されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a3b84-122">When using Visual Studio, name this file App.config. Note that the address and binding information are not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="a3b84-123">同様に、コードは構成ファイルから情報を取得する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a3b84-123">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]

5. <span data-ttu-id="a3b84-124">アプリケーションで `ClientCalculator` のインスタンスを作成し、サービス操作を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a3b84-124">Create an instance of the `ClientCalculator` in an application, and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. <span data-ttu-id="a3b84-125">クライアントをコンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="a3b84-125">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3b84-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="a3b84-126">See also</span></span>

- [<span data-ttu-id="a3b84-127">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="a3b84-127">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
