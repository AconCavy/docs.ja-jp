---
title: '方法 : 構成を使用して ASP.NET AJAX エンドポイントを追加する'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 3ccfb34614707c17885da3ed37f545bbab808869
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978265"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a><span data-ttu-id="db049-102">方法 : 構成を使用して ASP.NET AJAX エンドポイントを追加する</span><span class="sxs-lookup"><span data-stu-id="db049-102">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>
<span data-ttu-id="db049-103">Windows Communication Foundation (WCF) を使用すると、クライアント Web サイトの JavaScript から呼び出すことができる ASP.NET AJAX 対応エンドポイントを使用できるようにするサービスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="db049-103">Windows Communication Foundation (WCF) allows you to create a service that makes an ASP.NET AJAX-enabled endpoint available that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="db049-104">このようなエンドポイントを作成するには、他のすべての Windows Communication Foundation (WCF) エンドポイントと同様に構成ファイルを使用するか、構成要素を必要としないメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="db049-104">To create such an endpoint, you can either use a configuration file, as with all other Windows Communication Foundation (WCF) endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="db049-105">ここでは、構成を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="db049-105">This topic demonstrates the configuration approach.</span></span>  
  
 <span data-ttu-id="db049-106">サービスエンドポイントが ASP.NET になるようにするための手順の一部は、エンドポイントを構成して <xref:System.ServiceModel.WebHttpBinding> を使用し、 [\<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)エンドポイント動作を追加することで構成されます。</span><span class="sxs-lookup"><span data-stu-id="db049-106">The part of the procedure that enables the service endpoint to become ASP.NET AJAX-enabled consists of configuring the endpoint to use the <xref:System.ServiceModel.WebHttpBinding> and to add the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) endpoint behavior.</span></span> <span data-ttu-id="db049-107">エンドポイントを構成した後、サービスを実装およびホストする手順は、WCF サービスで使用されているものと似ています。</span><span class="sxs-lookup"><span data-stu-id="db049-107">After configuring the endpoint, the steps to implement and host the service are similar to those used by any WCF service.</span></span> <span data-ttu-id="db049-108">実際の例については、「 [HTTP POST を使用した AJAX サービス](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db049-108">For a working example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
 <span data-ttu-id="db049-109">構成を使用せずに ASP.NET AJAX エンドポイントを構成する方法の詳細については、「[方法: 構成を使用せずに ASP.NET Ajax エンドポイントを追加](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db049-109">For more information about how to configure an ASP.NET AJAX endpoint without using configuration, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
## <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="db049-110">基本的な WCF サービスを作成するには</span><span class="sxs-lookup"><span data-stu-id="db049-110">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="db049-111"><xref:System.ServiceModel.ServiceContractAttribute> 属性でマークされたインターフェイスを使用して、基本的な WCF サービスコントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="db049-111">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="db049-112">各操作を <xref:System.ServiceModel.OperationContractAttribute> でマークします。</span><span class="sxs-lookup"><span data-stu-id="db049-112">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="db049-113"><xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> プロパティが設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="db049-113">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
    ```csharp
    [ServiceContract(Namespace = "MyService")]  
    public interface ICalculator  
    {  
        [OperationContract]  
         // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. <span data-ttu-id="db049-114">`ICalculator` を使用して、`CalculatorService` サービス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="db049-114">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }
        // Other operations omitted…
    }
    ```  
  
3. <span data-ttu-id="db049-115">名前空間ブロック内にラップすることにより、`ICalculator` と `CalculatorService` の実装の名前空間を定義します。</span><span class="sxs-lookup"><span data-stu-id="db049-115">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp
    namespace Microsoft.Ajax.Samples
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a><span data-ttu-id="db049-116">サービスに ASP.NET AJAX エンドポイントを作成するには</span><span class="sxs-lookup"><span data-stu-id="db049-116">To create an ASP.NET AJAX endpoint for the service</span></span>  
  
1. <span data-ttu-id="db049-117">動作の構成を作成し、サービスの ASP.NET の AJAX 対応エンドポイントに対して[\<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="db049-117">Create a behavior configuration and specify the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior for ASP.NET AJAX-enabled endpoints of the service.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="AspNetAjaxBehavior">  
                    <enableWebScript />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
    </system.serviceModel>  
    ```  
  
2. <span data-ttu-id="db049-118"><xref:System.ServiceModel.WebHttpBinding> と、前の手順で定義した ASP.NET AJAX 動作を使用するサービスのエンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="db049-118">Create an endpoint for the service that uses the <xref:System.ServiceModel.WebHttpBinding> and the ASP.NET AJAX behavior defined in the previous step.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <services>  
            <service name="Microsoft.Ajax.Samples.CalculatorService">  
                <endpoint address=""  
                    behaviorConfiguration="AspNetAjaxBehavior"   
                    binding="webHttpBinding"  
                    contract="Microsoft.Ajax.Samples.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>   
    ```  
  
## <a name="to-host-the-service-in-iis"></a><span data-ttu-id="db049-119">IIS でサービスをホストするには</span><span class="sxs-lookup"><span data-stu-id="db049-119">To host the service in IIS</span></span>  
  
1. <span data-ttu-id="db049-120">IIS でサービスをホストするには、アプリケーションで .svc 拡張子の新しいサービス ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="db049-120">To host the service in IIS, create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="db049-121">このファイルを編集するには、サービスの適切な[\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)ディレクティブ情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="db049-121">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="db049-122">たとえば、`CalculatorService` サンプルに対応するサービス ファイルのコンテンツには、次の情報が記述されています。</span><span class="sxs-lookup"><span data-stu-id="db049-122">For example, the content in the service file for the `CalculatorService` sample contains the following information.</span></span>  
  
    ```
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. <span data-ttu-id="db049-123">IIS でのホストの詳細については、「 [How to: Host a WCF Service IN iis](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db049-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
## <a name="to-call-the-service"></a><span data-ttu-id="db049-124">サービスを呼び出すには</span><span class="sxs-lookup"><span data-stu-id="db049-124">To call the service</span></span>  
  
1. <span data-ttu-id="db049-125">エンドポイントは、.svc ファイルを基準とした空のアドレスで構成されます。これにより、サービスが使用可能になり、サービスに要求を送信することによって (たとえば、service .svc/\<操作 >、`Add` 操作に対して要求を送信することによって呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="db049-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="db049-126">これは、ASP.NET AJAX Script Manager コントロールのスクリプト コレクションにエンドポイント URL を入力することで使用できます。</span><span class="sxs-lookup"><span data-stu-id="db049-126">You can use it by entering the endpoint URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="db049-127">例については、「 [HTTP POST を使用した AJAX サービス](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db049-127">For an example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db049-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="db049-128">See also</span></span>

- [<span data-ttu-id="db049-129">ASP.NET AJAX 用の WCF サービスの作成</span><span class="sxs-lookup"><span data-stu-id="db049-129">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="db049-130">方法 : AJAX 対応 ASP.NET Web サービスを WCF に移行する</span><span class="sxs-lookup"><span data-stu-id="db049-130">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
