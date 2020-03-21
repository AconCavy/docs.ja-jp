---
title: '方法 : 構成ファイルを使用してサービスのメタデータを公開する'
ms.date: 03/30/2017
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
ms.openlocfilehash: 7ea0a2aa386f747b89f56f21d75a97e4409140a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184868"
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a><span data-ttu-id="4751b-102">方法 : 構成ファイルを使用してサービスのメタデータを公開する</span><span class="sxs-lookup"><span data-stu-id="4751b-102">How to: Publish Metadata for a Service Using a Configuration File</span></span>
<span data-ttu-id="4751b-103">これは、Windows コミュニケーション ファウンデーション (WCF) サービスのメタデータの公開方法を示す 2 つの方法のトピックの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="4751b-103">This is one of two how-to topics that demonstrate publishing metadata for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="4751b-104">構成ファイルとコードを使用して、サービスがメタデータを公開する手段を指定する方法は 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="4751b-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="4751b-105">このトピックでは、構成ファイルを使用してサービスのメタデータを公開する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4751b-105">This topic shows how to publish metadata for a service using a configuration file.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="4751b-106">このトピックでは、セキュリティで保護されていない方法でメタデータを公開する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4751b-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="4751b-107">クライアントは、サービスからメタデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="4751b-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="4751b-108">サービスでメタデータを安全な方法で公開する必要がある場合は、「[カスタムセキュア メタデータ エンドポイント](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4751b-108">If you require your service to publish metadata in a secure manner, see [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="4751b-109">コードでのメタデータの公開の詳細については、「[方法 : コードを使用してサービスのメタデータを公開する](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4751b-109">For more information about publishing metadata in code, see [How to: Publish Metadata for a Service Using Code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).</span></span> <span data-ttu-id="4751b-110">メタデータを公開すると、クライアントが `?wsdl` クエリ文字列を使用した WS-Transfer GET 要求または HTTP/GET 要求によりメタデータを取得できるようになります。</span><span class="sxs-lookup"><span data-stu-id="4751b-110">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="4751b-111">コードが動作していることを確認するには、基本的な WCF サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="4751b-111">To be sure that the code is working, create a basic WCF service.</span></span> <span data-ttu-id="4751b-112">簡略化のため、次のコードに基本的な自己ホスト型サービスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="4751b-112">For simplicity, a basic self-hosted service is provided in the following code.</span></span>  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
 <span data-ttu-id="4751b-113">これは、構成ファイルを使用して構成された自己ホスト型サービスです。</span><span class="sxs-lookup"><span data-stu-id="4751b-113">This service is a self-hosted service, which is configured using a configuration file.</span></span> <span data-ttu-id="4751b-114">以下の構成ファイルをベースとして使用します。</span><span class="sxs-lookup"><span data-stu-id="4751b-114">The following configuration file serves as a starting point.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Metadata.Example.SimpleService">  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
      </service>  
    </services>  
    <behaviors>  
  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a><span data-ttu-id="4751b-115">アプリケーション構成ファイルを使用して WCF サービスのメタデータを公開するには</span><span class="sxs-lookup"><span data-stu-id="4751b-115">To publish metadata for a WCF service using an application configuration file</span></span>  
  
1. <span data-ttu-id="4751b-116">`</services>` 要素を閉じた後、App.config ファイル内に `<behaviors>` 要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="4751b-116">Within the App.config file, after the closing `</services>` element, create a `<behaviors>` element.</span></span>  

2. <span data-ttu-id="4751b-117">`<behaviors>` 要素内に、`<serviceBehaviors>` 要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="4751b-117">Within the `<behaviors>` element, add a `<serviceBehaviors>` element.</span></span>  

3. <span data-ttu-id="4751b-118">`<behavior>`要素に `<serviceBehaviors>` 要素を追加し、`name` 要素の `<behavior>` 属性に値を指定します。</span><span class="sxs-lookup"><span data-stu-id="4751b-118">Add a `<behavior>` element to the `<serviceBehaviors>` element and specify a value for the `name` attribute of the `<behavior>` element.</span></span>  

4. <span data-ttu-id="4751b-119">`<serviceMetadata>` 要素を `<behavior>` 要素に追加します。</span><span class="sxs-lookup"><span data-stu-id="4751b-119">Add a `<serviceMetadata>` element to the `<behavior>` element.</span></span> <span data-ttu-id="4751b-120">`httpGetEnabled` 属性を `true` に設定し、`policyVersion` 属性を Policy15 に設定します。</span><span class="sxs-lookup"><span data-stu-id="4751b-120">Set the `httpGetEnabled` attribute to `true` and the `policyVersion` attribute to Policy15.</span></span> <span data-ttu-id="4751b-121">`httpGetEnabled` により、サービスは HTTP GET 要求からのメタデータ要求に応答できるようになります。</span><span class="sxs-lookup"><span data-stu-id="4751b-121">`httpGetEnabled` allows the service to respond to metadata requests made by an HTTP GET request.</span></span> <span data-ttu-id="4751b-122">`policyVersion` は、サービスに対して、WS-Policy 1.5 準拠でメタデータを生成するように指示します。</span><span class="sxs-lookup"><span data-stu-id="4751b-122">`policyVersion` tells the service to conform to WS-Policy 1.5 when generating metadata.</span></span>  

5. <span data-ttu-id="4751b-123">次のコード例に示すように、`behaviorConfiguration` 要素に `<service>` 属性を追加し、手順 1. で追加した `name` 要素の `<behavior>` 属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="4751b-123">Add a `behaviorConfiguration` attribute to the `<service>` element and specify the `name` attribute of the `<behavior>` element added in step 1, as shown in the following code example.</span></span>  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
        ...  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy15" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
6. <span data-ttu-id="4751b-124">1 つ以上の `<endpoint>` 要素を追加して、コントラクトを `IMetadataExchange` に設定します。コード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4751b-124">Add one or more `<endpoint>` elements with the contract set to `IMetadataExchange`, as shown in the following code example.</span></span>  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    ```  
  
7. <span data-ttu-id="4751b-125">前の手順で追加したメタデータ エンドポイントについて、`binding` 属性に次のいずれかの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="4751b-125">For the metadata endpoints added in the previous step, set the `binding` attribute to one of the following:</span></span>  
  
    - <span data-ttu-id="4751b-126">HTTP 公開の場合、`mexHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="4751b-126">`mexHttpBinding` for HTTP publication.</span></span>  
  
    - <span data-ttu-id="4751b-127">HTTPS 公開の場合、`mexHttpsBinding`</span><span class="sxs-lookup"><span data-stu-id="4751b-127">`mexHttpsBinding` for HTTPS publication.</span></span>  
  
    - <span data-ttu-id="4751b-128">名前付きパイプ公開の場合、`mexNamedPipeBinding`</span><span class="sxs-lookup"><span data-stu-id="4751b-128">`mexNamedPipeBinding` for named pipe publication.</span></span>  
  
    - <span data-ttu-id="4751b-129">TCP 公開の場合、`mexTcpBinding`</span><span class="sxs-lookup"><span data-stu-id="4751b-129">`mexTcpBinding` for TCP publication.</span></span>  
  
8. <span data-ttu-id="4751b-130">前の手順で追加したメタデータ エンドポイントについて、次のいずれかに等しいアドレスを設定します。</span><span class="sxs-lookup"><span data-stu-id="4751b-130">For the metadata endpoints added in a previous step, set the address equal to:</span></span>  
  
    - <span data-ttu-id="4751b-131">ベース アドレスがメタデータ バインディングと同じ場合に、公開ポイントとしてホスト アプリケーションのベース アドレスを使用するための空の文字列</span><span class="sxs-lookup"><span data-stu-id="4751b-131">An empty string to use the host application's base address as the publication point if the base address is the same as the metadata binding.</span></span>  
  
    - <span data-ttu-id="4751b-132">ホスト アプリケーションにベース アドレスがある場合、相対アドレス</span><span class="sxs-lookup"><span data-stu-id="4751b-132">A relative address if the host application has a base address.</span></span>  
  
    - <span data-ttu-id="4751b-133">絶対アドレス</span><span class="sxs-lookup"><span data-stu-id="4751b-133">An absolute address.</span></span>  
  
9. <span data-ttu-id="4751b-134">コンソール アプリケーションをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="4751b-134">Build and run the console application.</span></span>  
  
10. <span data-ttu-id="4751b-135">Internet Explorer を使用してサービスのベース アドレスをhttp://localhost:8001/MetadataSample参照し (このサンプルでは)、メタデータの公開が有効になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4751b-135">Use Internet Explorer to browse to the base address of the service (http://localhost:8001/MetadataSample in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="4751b-136">有効になっていない場合は、"このサービスのメタデータ公開は現在は無効になっています。" というメッセージが結果ページの上部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="4751b-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
### <a name="to-use-default-endpoints"></a><span data-ttu-id="4751b-137">既定のエンドポイントを使用するには</span><span class="sxs-lookup"><span data-stu-id="4751b-137">To use default endpoints</span></span>  
  
1. <span data-ttu-id="4751b-138">既定のエンドポイントを使用するサービスでメタデータを構成するには、前の例のように、構成ファイルで <xref:System.ServiceModel.Description.ServiceMetadataBehavior> を指定します。ただし、エンドポイントは指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="4751b-138">To configure metadata on a service that uses default endpoints, specify the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> in the configuration file as in the previous example, but do not specify any endpoints.</span></span> <span data-ttu-id="4751b-139">構成ファイルは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="4751b-139">The configuration file would then look like this.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="SimpleServiceBehavior">  
              <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="4751b-140">サービスの <xref:System.ServiceModel.Description.ServiceMetadataBehavior> では `httpGetEnabled` が `true` に設定されているため、サービスではメタデータの公開が有効になっています。また、エンドポイントが明示的に追加されていないため、ランタイムは既定のエンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="4751b-140">Because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> with the `httpGetEnabled` set to `true`, the service has publishing metadata enabled, and because no endpoints were explicitly added, the runtime adds the default endpoints.</span></span> <span data-ttu-id="4751b-141">既定のエンドポイントについては、「[Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)」 (簡易構成) と「[Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)」 (WCF サービスの簡易構成) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4751b-141">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4751b-142">例</span><span class="sxs-lookup"><span data-stu-id="4751b-142">Example</span></span>  
 <span data-ttu-id="4751b-143">基本 WCF サービスの実装と、サービスのメタデータを公開する構成ファイルの実装を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="4751b-143">The following code example shows the implementation of a basic WCF service and the configuration file that publishes metadata for the service.</span></span>  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4751b-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="4751b-144">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [<span data-ttu-id="4751b-145">How to: Host a WCF Service in a Managed Application</span><span class="sxs-lookup"><span data-stu-id="4751b-145">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="4751b-146">自己ホスト</span><span class="sxs-lookup"><span data-stu-id="4751b-146">Self-Host</span></span>](../../../../docs/framework/wcf/samples/self-host.md)
- [<span data-ttu-id="4751b-147">メタデータ アーキテクチャの概要</span><span class="sxs-lookup"><span data-stu-id="4751b-147">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [<span data-ttu-id="4751b-148">メタデータを使用する</span><span class="sxs-lookup"><span data-stu-id="4751b-148">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [<span data-ttu-id="4751b-149">方法: コードを使用してサービスのメタデータを公開する</span><span class="sxs-lookup"><span data-stu-id="4751b-149">How to: Publish Metadata for a Service Using Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
