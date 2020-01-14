---
title: Windows ストア クライアント アプリを使用した WCF サービスへのアクセス
ms.date: 03/30/2017
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
ms.openlocfilehash: 77dc5d19bc40dc09148a8d2368c56e522bfafc1a
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2020
ms.locfileid: "75938178"
---
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a><span data-ttu-id="d7564-102">Windows ストア クライアント アプリを使用した WCF サービスへのアクセス</span><span class="sxs-lookup"><span data-stu-id="d7564-102">Accessing WCF Services with a Windows Store Client App</span></span>
<span data-ttu-id="d7564-103">Windows 8 では、Windows ストア アプリケーションと呼ばれる新しい種類のアプリケーションが導入されています。</span><span class="sxs-lookup"><span data-stu-id="d7564-103">Windows 8 introduces a new type of application called Windows Store applications.</span></span> <span data-ttu-id="d7564-104">これらのアプリケーションはタッチ スクリーンのインターフェイスを念頭にデザインされています。</span><span class="sxs-lookup"><span data-stu-id="d7564-104">These applications are designed around a touch screen interface.</span></span> <span data-ttu-id="d7564-105">.NET Framework 4.5 により、Windows ストア アプリケーションから WCF サービスを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="d7564-105">.NET Framework 4.5 enables Windows Store applications to call WCF services.</span></span>  
  
## <a name="wcf-support-in-windows-store-applications"></a><span data-ttu-id="d7564-106">Windows ストア アプリケーションでの WCF のサポート</span><span class="sxs-lookup"><span data-stu-id="d7564-106">WCF Support in Windows Store Applications</span></span>  
 <span data-ttu-id="d7564-107">WCF 機能の一部は、Windows ストア アプリケーション内から利用できます。詳細については、以降のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7564-107">A subset of WCF functionality is available from within a Windows Store application, see the following sections for more details.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d7564-108">WCF で公開される API ではなく、WinRT 配信 API を使用してください。</span><span class="sxs-lookup"><span data-stu-id="d7564-108">Use the WinRT syndication APIs instead of those exposed by WCF.</span></span> <span data-ttu-id="d7564-109">詳細については、「 [Windows.Web.Syndication 名前空間](xref:Windows.Web.Syndication)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7564-109">For more information see, [WinRT Syndication API](xref:Windows.Web.Syndication)</span></span>  
  
> [!WARNING]
> <span data-ttu-id="d7564-110">サービス参照の追加を使用して Windows ランタイム コンポーネントへの Web サービス参照を追加することはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d7564-110">Using Add Service Reference to add a web service reference to a Windows Runtime Component isn’t supported.</span></span>  
  
### <a name="supported-bindings"></a><span data-ttu-id="d7564-111">サポート対象のバインド</span><span class="sxs-lookup"><span data-stu-id="d7564-111">Supported Bindings</span></span>  
 <span data-ttu-id="d7564-112">Windows ストア アプリケーションでは、以下の WCF バインドがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d7564-112">The following WCF bindings are supported in Windows Store Applications:</span></span>  
  
1. <xref:System.ServiceModel.BasicHttpBinding>  
  
2. <xref:System.ServiceModel.NetTcpBinding>  
  
3. <xref:System.ServiceModel.NetHttpBinding>  
  
4. <xref:System.ServiceModel.Channels.CustomBinding>
  
 <span data-ttu-id="d7564-113">Windows ストア アプリケーションでは、以下のバインド要素がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d7564-113">The following binding elements are supported in Windows Store Applications</span></span>  
  
1. <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2. <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3. <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4. <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5. <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6. <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7. <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8. <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="d7564-114">テキスト エンコードとバイナリ エンコードの両方がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d7564-114">Both Text and Binary encodings are supported.</span></span> <span data-ttu-id="d7564-115">すべての WCF 転送モードがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d7564-115">All WCF transfer modes are supported.</span></span> <span data-ttu-id="d7564-116">詳細については、「 [Streaming Message Transfer](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7564-116">For more information see, [Streaming Message Transfer](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).</span></span>  
  
### <a name="add-service-reference"></a><span data-ttu-id="d7564-117">サービス参照の追加</span><span class="sxs-lookup"><span data-stu-id="d7564-117">Add Service Reference</span></span>  
 <span data-ttu-id="d7564-118">WCF サービスを Windows ストア アプリケーションから呼び出すには、Visual Studio 2012 の "サービス参照の追加" 機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="d7564-118">To call a WCF service from a Windows Store application, use the Add Service Reference feature of Visual Studio 2012.</span></span> <span data-ttu-id="d7564-119">Windows ストア アプリケーションでは、"サービス参照の追加" 機能にいくつかの変更が行われていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="d7564-119">You will notice a few changes in the functionality of Add Service Reference when done within a Windows Store application.</span></span> <span data-ttu-id="d7564-120">まず、構成ファイルが生成されません。</span><span class="sxs-lookup"><span data-stu-id="d7564-120">First no configuration file is generated.</span></span> <span data-ttu-id="d7564-121">Windows ストア アプリケーションでは構成ファイルが使用されないため、コードで構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7564-121">Windows Store applications do not use configuration files, so they must be configured in code.</span></span> <span data-ttu-id="d7564-122">この構成コードは、"サービス参照の追加" によって生成される References.cs ファイルにあります。</span><span class="sxs-lookup"><span data-stu-id="d7564-122">This configuration code can be found in the References.cs file generated by Add Service Reference.</span></span> <span data-ttu-id="d7564-123">このファイルを表示するには、ソリューションエクスプローラーで [すべてのファイルを表示] を選択してください。</span><span class="sxs-lookup"><span data-stu-id="d7564-123">To see this file, make sure to select "Show All Files" in the solution explorer.</span></span> <span data-ttu-id="d7564-124">このファイルは、[サービス参照] の下のプロジェクト内の Reference.svcmap ノードにあります。</span><span class="sxs-lookup"><span data-stu-id="d7564-124">The file will be located under the Service References and then Reference.svcmap nodes within the project.</span></span> <span data-ttu-id="d7564-125">Windows ストア アプリケーション内で WCF サービスに対して生成されるすべての操作は非同期で、タスク ベースの非同期パターンが使用されます。</span><span class="sxs-lookup"><span data-stu-id="d7564-125">All operations generated for WCF services within a Windows Store application will be asynchronous using the Task-based asynchronous pattern.</span></span> <span data-ttu-id="d7564-126">詳細については、「[非同期タスク-タスクを使用した非同期プログラミングの簡素化](https://docs.microsoft.com/archive/msdn-magazine/2010/september/async-tasks-simplify-asynchronous-programming-with-tasks)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7564-126">For more information, see [Async Tasks - Simplify Asynchronous Programming with Tasks](https://docs.microsoft.com/archive/msdn-magazine/2010/september/async-tasks-simplify-asynchronous-programming-with-tasks).</span></span>  
  
 <span data-ttu-id="d7564-127">構成がコードで生成されるようになったため、サービス参照を更新するたびに、Reference.cs ファイルで行ったすべての変更が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="d7564-127">Because configuration is now generated in code, any changes made in the Reference.cs file would be overwritten every time the service reference is updated.</span></span> <span data-ttu-id="d7564-128">この状況に対処するために、構成コードは部分メソッド内に生成され、これをクライアント プロキシ クラスで実装できます。</span><span class="sxs-lookup"><span data-stu-id="d7564-128">To remedy this situation the configuration code is generated within a partial method, which you can implement in your client proxy class.</span></span> <span data-ttu-id="d7564-129">部分メソッドは次のように宣言されています。</span><span class="sxs-lookup"><span data-stu-id="d7564-129">The partial method is declared as follows:</span></span>  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 <span data-ttu-id="d7564-130">その後、この部分メソッドを実装し、次のように、クライアント プロキシ クラスのバインドまたはエンドポイントを変更できます。</span><span class="sxs-lookup"><span data-stu-id="d7564-130">You can then implement this partial method and change the binding or endpoint in your client proxy class as follows:</span></span>  
  
```csharp  
public partial class Service1Client : System.ServiceModel.ClientBase<MetroWcfClient.ServiceRefMultiEndpt.IService1>, MetroWcfClient.ServiceRefMultiEndpt.IService1  
    {   
        static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,   
            System.ServiceModel.Description.ClientCredentials clientCredentials)  
        {  
            if (serviceEndpoint.Name ==   
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
            }  
            else if (serviceEndpoint.Name ==   
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService11.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
                clientCredentials.UserName.UserName = "username1";  
                clientCredentials.UserName.Password = "password";  
            }  
            else if (serviceEndpoint.Name ==   
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.NetTcpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.Name = "MyTcpBinding";  
                serviceEndpoint.Address = new System.ServiceModel.EndpointAddress("net.tcp://localhost/tcp");  
            }  
        }  
    }  
```  
  
### <a name="serialization"></a><span data-ttu-id="d7564-131">Serialization</span><span class="sxs-lookup"><span data-stu-id="d7564-131">Serialization</span></span>  
 <span data-ttu-id="d7564-132">Windows ストア アプリケーションでは、次のシリアライザーがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d7564-132">The following serializers are supported in Windows Store applications:</span></span>  
  
1. <span data-ttu-id="d7564-133">DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="d7564-133">DataContractSerializer</span></span>  
  
2. <span data-ttu-id="d7564-134">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="d7564-134">DataContractJsonSerializer</span></span>  
  
3. <span data-ttu-id="d7564-135">XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="d7564-135">XmlSerializer</span></span>  
  
> [!WARNING]
> <span data-ttu-id="d7564-136">XmlDictionaryWriter.Write(DateTime) は、DateTime オブジェクトを文字列として出力するようになりました。</span><span class="sxs-lookup"><span data-stu-id="d7564-136">XmlDictionaryWriter.Write(DateTime) now writes the DateTime object as a string.</span></span>  
  
### <a name="security"></a><span data-ttu-id="d7564-137">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="d7564-137">Security</span></span>  

<span data-ttu-id="d7564-138">Windows ストアアプリケーションでは、次のセキュリティモードがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d7564-138">The following security modes are supported in Windows Store applications:</span></span>
  
1. <xref:System.ServiceModel.SecurityMode.None>  
  
2. <xref:System.ServiceModel.SecurityMode.Transport>  
  
3. <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>
  
4. <xref:System.ServiceModel.SecurityMode.Message>
  
<span data-ttu-id="d7564-139">Windows ストアアプリケーションでは、次のクライアント資格情報の種類がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d7564-139">The following client credential types are supported in Windows Store applications:</span></span>
  
1. <span data-ttu-id="d7564-140">[なし]</span><span class="sxs-lookup"><span data-stu-id="d7564-140">None</span></span>  
  
2. <span data-ttu-id="d7564-141">Basic</span><span class="sxs-lookup"><span data-stu-id="d7564-141">Basic</span></span>  
  
3. <span data-ttu-id="d7564-142">Digest</span><span class="sxs-lookup"><span data-stu-id="d7564-142">Digest</span></span>  
  
4. <span data-ttu-id="d7564-143">Negotiate</span><span class="sxs-lookup"><span data-stu-id="d7564-143">Negotiate</span></span>  
  
5. <span data-ttu-id="d7564-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="d7564-144">NTLM</span></span>  
  
6. <span data-ttu-id="d7564-145">Windows</span><span class="sxs-lookup"><span data-stu-id="d7564-145">Windows</span></span>  
  
7. <span data-ttu-id="d7564-146">ユーザー名 (メッセージ セキュリティ)</span><span class="sxs-lookup"><span data-stu-id="d7564-146">Username (Message Security)</span></span>  
  
8. <span data-ttu-id="d7564-147">Windows (トランスポート セキュリティ)</span><span class="sxs-lookup"><span data-stu-id="d7564-147">Windows (Transport Security)</span></span>  
  
 <span data-ttu-id="d7564-148">Windows ストア アプリケーションから既定の Windows 資格情報にアクセスして送信するためには、Package.appmanifest ファイル内でこの機能を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7564-148">In order for Windows Store applications to access and send default Windows credentials, you must enable this functionality within the Package.appmanifest file.</span></span> <span data-ttu-id="d7564-149">このファイルを開き、[機能] タブを選択し、[既定の Windows 資格情報] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d7564-149">Open this file and select the Capabilities tab and select "Default Windows Credentials".</span></span> <span data-ttu-id="d7564-150">これにより、ドメイン資格情報を必要とするイントラネット リソースにアプリケーションが接続できるようになります。</span><span class="sxs-lookup"><span data-stu-id="d7564-150">This allows the application to connect to intranet resources that require domain credentials.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d7564-151">Windows ストアアプリケーションでコンピューター間の呼び出しを行うには、"ホーム/社内ネットワーク" と呼ばれる別の機能を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7564-151">In order for Windows Store applications to make cross machine calls you must enable another capability called "Home/Work Networking".</span></span> <span data-ttu-id="d7564-152">この設定は、appmanifest.xaml ファイルの [機能] タブにもあります。 [ホーム/社内ネットワーク] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="d7564-152">This setting is also in the Package.appmanifest file under the Capabilities tab. Select the Home/Work Networking checkbox.</span></span> <span data-ttu-id="d7564-153">これで、アプリケーションは、自宅や職場など、ユーザーが信頼できる場所のネットワークに着信および発信アクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="d7564-153">This gives your application inbound and outbound access to the networks of the user’s trusted places like home and work.</span></span> <span data-ttu-id="d7564-154">着信方向の重要なポートは常にブロックされます。</span><span class="sxs-lookup"><span data-stu-id="d7564-154">Inbound critical ports are always blocked.</span></span> <span data-ttu-id="d7564-155">また、インターネット上のサービスにアクセスするには、インターネット (クライアント) の機能も有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7564-155">For accessing services on the internet you must also enable Internet (Client) capability.</span></span>  
  
### <a name="misc"></a><span data-ttu-id="d7564-156">[その他]</span><span class="sxs-lookup"><span data-stu-id="d7564-156">Misc</span></span>  
 <span data-ttu-id="d7564-157">Windows ストア アプリケーションでは、次のクラスの使用がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d7564-157">The use of the following classes is supported for Windows Store Applications:</span></span>  
  
1. <xref:System.ServiceModel.ChannelFactory>  
  
2. <xref:System.ServiceModel.DuplexChannelFactory%601>
  
3. <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a><span data-ttu-id="d7564-158">サービス コントラクトの定義</span><span class="sxs-lookup"><span data-stu-id="d7564-158">Defining Service Contracts</span></span>  
 <span data-ttu-id="d7564-159">非同期サービス操作の定義には、タスク ベースの非同期パターンのみを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d7564-159">We recommend only defining asynchronous service operations using the task-based async pattern.</span></span> <span data-ttu-id="d7564-160">これにより、サービス操作の呼び出し中も、Windows ストア アプリケーションの応答が維持されます。</span><span class="sxs-lookup"><span data-stu-id="d7564-160">This ensures Windows Store applications remain responsive while calling a service operation.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="d7564-161">同期操作を定義した場合でも例外はスローされませんが、非同期操作のみを定義することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d7564-161">While no exception will be thrown if you define a synchronous operation, it is strongly recommended to only define asynchronous operations.</span></span>  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a><span data-ttu-id="d7564-162">Windows ストア アプリケーションからの WCF サービスの呼び出し</span><span class="sxs-lookup"><span data-stu-id="d7564-162">Calling WCF Services from Windows Store Applications</span></span>  
 <span data-ttu-id="d7564-163">既に説明したように、すべての構成は、生成されたプロキシ クラスの GetBindingForEndpoint メソッドのコード内で行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7564-163">As mentioned before all configuration must be done in code in the GetBindingForEndpoint method in the generated proxy class.</span></span> <span data-ttu-id="d7564-164">次のコードに示すように、サービス操作の呼び出しは、タスク ベースの非同期メソッドの呼び出しと同じように実行されます。</span><span class="sxs-lookup"><span data-stu-id="d7564-164">Calling a service operation is done the same as calling any task-based asynchronous method as shown in the following code snippet.</span></span>  
  
```csharp  
void async SomeMethod()  
{  
    ServiceClient proxy = new ServiceClient();  
    Task<T> results = await proxy.CallAsync(param1, param2);  
    T result = results.Result;  
    if (result.Success)  
    {  
       // Do something with result  
    }  
}  
```  
  
 <span data-ttu-id="d7564-165">非同期呼び出しを行うメソッドでは async キーワード、非同期メソッドの呼び出し時には await キーワードが使用されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d7564-165">Notice the use of the async keyword on the method making the asynchronous call and the await keyword when calling the asynchronous method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7564-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="d7564-166">See also</span></span>

- [<span data-ttu-id="d7564-167">Windows ストアアプリブログの WCF</span><span class="sxs-lookup"><span data-stu-id="d7564-167">WCF in Windows Store Apps Blog</span></span>](https://docs.microsoft.com/archive/blogs/piyushjo/wcf-in-windows-8-metro-styled-apps-absolutely-supported)
- [<span data-ttu-id="d7564-168">WCF Windows ストアクライアントおよびセキュリティ</span><span class="sxs-lookup"><span data-stu-id="d7564-168">WCF Windows Store Clients and Security</span></span>](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-adding-security)
- [<span data-ttu-id="d7564-169">Windows ストアアプリとコンピューター間の呼び出し</span><span class="sxs-lookup"><span data-stu-id="d7564-169">Windows Store Apps and Cross Machine Calls</span></span>](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario)
- [<span data-ttu-id="d7564-170">Windows ストアアプリから Azure にデプロイされた WCF サービスの呼び出し</span><span class="sxs-lookup"><span data-stu-id="d7564-170">Calling a WCF Service Deployed in Azure from a Windows Store App</span></span>](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario)
- [<span data-ttu-id="d7564-171">WCF セキュリティのプログラミング</span><span class="sxs-lookup"><span data-stu-id="d7564-171">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [<span data-ttu-id="d7564-172">バインディング</span><span class="sxs-lookup"><span data-stu-id="d7564-172">Bindings</span></span>](../../../../docs/framework/wcf/bindings.md)
