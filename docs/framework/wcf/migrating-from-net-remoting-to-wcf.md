---
title: .NET リモート処理から WCF への移行
description: .NET リモート処理を使用するアプリケーションを WCF を使用するように移行する方法について説明します。 WCF では、いくつかの一般的なリモート処理シナリオを実行できます。
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: 73bdac5d8f4d39694f038bb600828c79e527efb0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "90542851"
---
# <a name="migrating-from-net-remoting-to-wcf"></a><span data-ttu-id="8c5b3-104">.NET リモート処理から WCF への移行</span><span class="sxs-lookup"><span data-stu-id="8c5b3-104">Migrating from .NET Remoting to WCF</span></span>
<span data-ttu-id="8c5b3-105">この記事では、.NET リモート処理を使用するアプリケーションを、Windows Communication Foundation (WCF) を使用するように移行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-105">This article describes how to migrate an application that uses .NET Remoting to use Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="8c5b3-106">これらの製品間で類似する概念を比較した後、WCF で一般的なリモート処理のシナリオを実現する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-106">It compares similar concepts between these products and then describes how to accomplish several common Remoting scenarios in WCF.</span></span>  
  
 <span data-ttu-id="8c5b3-107">.NET リモート処理は、旧バージョンとの互換性のためだけにサポートされているレガシー製品です。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-107">.NET Remoting is a legacy product that is supported only for backward compatibility.</span></span> <span data-ttu-id="8c5b3-108">これは、クライアントとサーバーの間で個々の信頼レベルを維持できないため、信頼レベルが混在する環境において安全ではありません。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-108">It is not secure across mixed-trust environments because it cannot maintain the separate trust levels between client and server.</span></span> <span data-ttu-id="8c5b3-109">たとえば、インターネットまたは信頼できないクライアントには、.NET リモート処理のエンドポイントを非公開にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-109">For example, you should never expose a .NET Remoting endpoint to the Internet or to untrusted clients.</span></span> <span data-ttu-id="8c5b3-110">既存のリモート処理アプリケーションを、より新しく安全なテクノロジに移行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-110">We recommend existing Remoting applications be migrated to newer and more secure technologies.</span></span> <span data-ttu-id="8c5b3-111">そのアプリケーションの設計に HTTP のみが使用されていて、かつ RESTful である場合、ASP.NET Web API をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-111">If the application’s design uses only HTTP and is RESTful, we recommend ASP.NET Web API.</span></span> <span data-ttu-id="8c5b3-112">詳細については、ASP.NET Web API を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-112">For more information, see ASP.NET Web API.</span></span> <span data-ttu-id="8c5b3-113">アプリケーションが SOAP ベースの場合や、TCP などの非 HTTP プロトコルを必要とする場合は、WCF をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-113">If the application is based on SOAP or requires non-Http protocols such as TCP, we recommend WCF.</span></span>  

## <a name="comparing-net-remoting-to-wcf"></a><span data-ttu-id="8c5b3-114">.NET リモート処理と WCF の比較</span><span class="sxs-lookup"><span data-stu-id="8c5b3-114">Comparing .NET Remoting to WCF</span></span>  
 <span data-ttu-id="8c5b3-115">このセクションでは、.NET リモート処理の基本的な構成要素と、それに相当する WCF の構成要素を比較します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-115">This section compares the basic building blocks of .NET Remoting with their WCF equivalents.</span></span> <span data-ttu-id="8c5b3-116">これらの構成要素は、WCF で一般的なクライアントとサーバーのシナリオを作成するために後で使用します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-116">We will use these building blocks later to create some common client-server scenarios in WCF.</span></span> <span data-ttu-id="8c5b3-117">次の表は、.NET リモート処理と WCF の主な類似性と相違点をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-117">The following chart summarizes the main similarities and differences between .NET Remoting and WCF.</span></span>  
  
||<span data-ttu-id="8c5b3-118">.NET リモート処理</span><span class="sxs-lookup"><span data-stu-id="8c5b3-118">.NET Remoting</span></span>|<span data-ttu-id="8c5b3-119">WCF</span><span class="sxs-lookup"><span data-stu-id="8c5b3-119">WCF</span></span>|  
|-|-------------------|---------|  
|<span data-ttu-id="8c5b3-120">サーバーの種類</span><span class="sxs-lookup"><span data-stu-id="8c5b3-120">Server type</span></span>|<span data-ttu-id="8c5b3-121">サブクラス MarshalByRefObject</span><span class="sxs-lookup"><span data-stu-id="8c5b3-121">Subclass MarshalByRefObject</span></span>|<span data-ttu-id="8c5b3-122">[ServiceContract] 属性でマーク</span><span class="sxs-lookup"><span data-stu-id="8c5b3-122">Mark with [ServiceContract] attribute</span></span>|  
|<span data-ttu-id="8c5b3-123">サービス操作</span><span class="sxs-lookup"><span data-stu-id="8c5b3-123">Service operations</span></span>|<span data-ttu-id="8c5b3-124">サーバーの型のパブリック メソッド</span><span class="sxs-lookup"><span data-stu-id="8c5b3-124">Public methods on server type</span></span>|<span data-ttu-id="8c5b3-125">[OperationContract] 属性でマーク</span><span class="sxs-lookup"><span data-stu-id="8c5b3-125">Mark with [OperationContract] attribute</span></span>|  
|<span data-ttu-id="8c5b3-126">シリアル化</span><span class="sxs-lookup"><span data-stu-id="8c5b3-126">Serialization</span></span>|<span data-ttu-id="8c5b3-127">ISerializable または [Serializable]</span><span class="sxs-lookup"><span data-stu-id="8c5b3-127">ISerializable or [Serializable]</span></span>|<span data-ttu-id="8c5b3-128">DataContractSerializer または XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="8c5b3-128">DataContractSerializer or XmlSerializer</span></span>|  
|<span data-ttu-id="8c5b3-129">渡されるオブジェクト</span><span class="sxs-lookup"><span data-stu-id="8c5b3-129">Objects passed</span></span>|<span data-ttu-id="8c5b3-130">値渡しまたは参照渡し</span><span class="sxs-lookup"><span data-stu-id="8c5b3-130">By-value or by-reference</span></span>|<span data-ttu-id="8c5b3-131">値渡しのみ</span><span class="sxs-lookup"><span data-stu-id="8c5b3-131">By-value only</span></span>|  
|<span data-ttu-id="8c5b3-132">エラーと例外</span><span class="sxs-lookup"><span data-stu-id="8c5b3-132">Errors/exceptions</span></span>|<span data-ttu-id="8c5b3-133">すべてのシリアル化可能な例外</span><span class="sxs-lookup"><span data-stu-id="8c5b3-133">Any serializable exception</span></span>|<span data-ttu-id="8c5b3-134">FaultContract\<TDetail></span><span class="sxs-lookup"><span data-stu-id="8c5b3-134">FaultContract\<TDetail></span></span>|  
|<span data-ttu-id="8c5b3-135">クライアント プロキシ オブジェクト</span><span class="sxs-lookup"><span data-stu-id="8c5b3-135">Client proxy objects</span></span>|<span data-ttu-id="8c5b3-136">厳密に型指定された透過的プロキシが MarshalByRefObjects から自動的に作成されます</span><span class="sxs-lookup"><span data-stu-id="8c5b3-136">Strongly typed transparent proxies are created automatically from MarshalByRefObjects</span></span>|<span data-ttu-id="8c5b3-137">厳密に型指定されたプロキシは、ChannelFactory を使用してオンデマンドで生成されます。\<TChannel></span><span class="sxs-lookup"><span data-stu-id="8c5b3-137">Strongly typed proxies are generated on-demand using ChannelFactory\<TChannel></span></span>|  
|<span data-ttu-id="8c5b3-138">必要なプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="8c5b3-138">Platform required</span></span>|<span data-ttu-id="8c5b3-139">クライアントとサーバーの両方で Microsoft OS と .NET を使用する必要があります</span><span class="sxs-lookup"><span data-stu-id="8c5b3-139">Both client and server must use Microsoft OS and .NET</span></span>|<span data-ttu-id="8c5b3-140">クロスプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="8c5b3-140">Cross-platform</span></span>|  
|<span data-ttu-id="8c5b3-141">メッセージの形式</span><span class="sxs-lookup"><span data-stu-id="8c5b3-141">Message format</span></span>|<span data-ttu-id="8c5b3-142">Private</span><span class="sxs-lookup"><span data-stu-id="8c5b3-142">Private</span></span>|<span data-ttu-id="8c5b3-143">業界標準 (SOAP、WS-\* など)</span><span class="sxs-lookup"><span data-stu-id="8c5b3-143">Industry standards (SOAP, WS-\*, etc.)</span></span>|  
  
### <a name="server-implementation-comparison"></a><span data-ttu-id="8c5b3-144">サーバー実装の比較</span><span class="sxs-lookup"><span data-stu-id="8c5b3-144">Server Implementation Comparison</span></span>  
  
#### <a name="creating-a-server-in-net-remoting"></a><span data-ttu-id="8c5b3-145">.NET リモート処理でサーバーを作成する</span><span class="sxs-lookup"><span data-stu-id="8c5b3-145">Creating a Server in .NET Remoting</span></span>  
 <span data-ttu-id="8c5b3-146">.NET リモート処理のサーバーの型は MarshalByRefObject から派生させて、次のようにクライアントから呼び出せるメソッドを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-146">.NET Remoting server types must derive from MarshalByRefObject and define methods the client can call, like the following:</span></span>  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="8c5b3-147">このサーバーの型のパブリック メソッドは、クライアントから使用できるパブリック コントラクトになります。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-147">The public methods of this server type become the public contract available to clients.</span></span>  <span data-ttu-id="8c5b3-148">サーバーのパブリック インターフェイスとその実装の間には境界がありません。1 つの型によって両方を処理します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-148">There is no separation between the server’s public interface and its implementation – one type handles both.</span></span>  
  
 <span data-ttu-id="8c5b3-149">サーバーの型を定義した後は、次の例のように、クライアントから使用可能な状態にできます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-149">Once the server type has been defined, it can be made available to clients, like in the following example:</span></span>  
  
```csharp
TcpChannel channel = new TcpChannel(8080);  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingConfiguration.RegisterWellKnownServiceType(  
    typeof(RemotingServer),
    "RemotingServer",
    WellKnownObjectMode.Singleton);  
Console.WriteLine("RemotingServer is running.  Press ENTER to terminate...");  
Console.ReadLine();  
```  
  
 <span data-ttu-id="8c5b3-150">リモート処理の型をサーバーとして使用できるようにするには、構成ファイルを使用するなど、さまざまな方法があります。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-150">There are many ways to make the Remoting type available as a server, including using configuration files.</span></span> <span data-ttu-id="8c5b3-151">これはほんの一例にすぎません。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-151">This is just one example.</span></span>  
  
#### <a name="creating-a-server-in-wcf"></a><span data-ttu-id="8c5b3-152">WCF でサーバーを作成する</span><span class="sxs-lookup"><span data-stu-id="8c5b3-152">Creating a Server in WCF</span></span>  
 <span data-ttu-id="8c5b3-153">WCF で同等の手順を実行する場合は、パブリック "サービス コントラクト" と具象実装という 2 つの型を作成します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-153">The equivalent step in WCF involves creating two types -- the public "service contract" and the concrete implementation.</span></span> <span data-ttu-id="8c5b3-154">1 つ目の型は、[ServiceContract] でマークされたインターフェイスとして宣言します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-154">The first is declared as an interface marked with [ServiceContract].</span></span> <span data-ttu-id="8c5b3-155">クライアントから使用できるメソッドは、[OperationContract] でマークします。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-155">Methods available to clients are marked with [OperationContract]:</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="8c5b3-156">サーバーの実装は、次の例のように、別の具象クラスで定義します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-156">The server’s implementation is defined in a separate concrete class, like in the following example:</span></span>  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="8c5b3-157">これらの型を定義した後は、次の例のように、WCF サーバーをクライアントから使用可能な状態にできます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-157">Once these types have been defined, the WCF server can be made available to clients, like in the following example:</span></span>  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
Uri baseAddress = new Uri("net.tcp://localhost:8000/wcfserver");  
  
using (ServiceHost serviceHost = new ServiceHost(typeof(WCFServer), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(IWCFServer), binding, baseAddress);  
    serviceHost.Open();  
  
    Console.WriteLine($"The WCF server is ready at {baseAddress}.");
    Console.WriteLine("Press <ENTER> to terminate service...");  
    Console.WriteLine();  
    Console.ReadLine();  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="8c5b3-158">両方の例をできる限り似たものにするため、どちらの例でも TCP を使用します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-158">TCP is used in both examples to keep them as similar as possible.</span></span> <span data-ttu-id="8c5b3-159">HTTP を使用する例については、このトピックで後述するシナリオのチュートリアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-159">Refer to the scenario walk-throughs later in this topic for examples using HTTP.</span></span>  
  
 <span data-ttu-id="8c5b3-160">WCF サービスの構成方法やホスト方法には、さまざまなものがあります。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-160">There are many ways to configure and to host WCF services.</span></span> <span data-ttu-id="8c5b3-161">これは、"自己ホスト型" と呼ばれる一例にすぎません。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-161">This is just one example, known as "self-hosted".</span></span> <span data-ttu-id="8c5b3-162">詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-162">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="8c5b3-163">方法: サービス コントラクトを定義する</span><span class="sxs-lookup"><span data-stu-id="8c5b3-163">How to: Define a Service Contract</span></span>](how-to-define-a-wcf-service-contract.md)  
  
- [<span data-ttu-id="8c5b3-164">構成ファイルを使用してサービスを構成する方法</span><span class="sxs-lookup"><span data-stu-id="8c5b3-164">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)  
  
- [<span data-ttu-id="8c5b3-165">ホスティング サービス</span><span class="sxs-lookup"><span data-stu-id="8c5b3-165">Hosting Services</span></span>](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a><span data-ttu-id="8c5b3-166">クライアント実装の比較</span><span class="sxs-lookup"><span data-stu-id="8c5b3-166">Client Implementation Comparison</span></span>  
  
#### <a name="creating-a-client-in-net-remoting"></a><span data-ttu-id="8c5b3-167">.NET リモート処理でクライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="8c5b3-167">Creating a Client in .NET Remoting</span></span>  
 <span data-ttu-id="8c5b3-168">.NET リモート処理サーバー オブジェクトが使用可能になると、次の例のように、クライアントによって使用することができます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-168">Once a .NET Remoting server object has been made available, it can be consumed by clients, like in the following example:</span></span>  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine($"Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 <span data-ttu-id="8c5b3-169">Activator.GetObject() から返される RemotingServer インスタンスは、"透過的プロキシ" と呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-169">The RemotingServer instance returned from Activator.GetObject() is known as a "transparent proxy."</span></span> <span data-ttu-id="8c5b3-170">これによって RemotingServer 型のパブリック API がクライアントに実装されますが、すべてのメソッドは別のプロセスまたはコンピューターで実行中のサーバー オブジェクトを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-170">It implements the public API for the RemotingServer type on the client, but all the methods call the server object running in a different process or machine.</span></span>  
  
#### <a name="creating-a-client-in-wcf"></a><span data-ttu-id="8c5b3-171">WCF でクライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="8c5b3-171">Creating a Client in WCF</span></span>  
 <span data-ttu-id="8c5b3-172">WCF で同等の手順を実行する場合は、チャネル ファクトリを使用してプロキシを明示的に作成します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-172">The equivalent step in WCF involves using a channel factory to create the proxy explicitly.</span></span> <span data-ttu-id="8c5b3-173">リモート処理と同様、プロキシ オブジェクトは、次の例のように、サーバーでの操作の呼び出しに使用できます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-173">Like Remoting, the proxy object can be used to invoke operations on the server, like in the following example:</span></span>  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
String url = "net.tcp://localhost:8000/wcfserver";  
EndpointAddress address = new EndpointAddress(url);  
ChannelFactory<IWCFServer> channelFactory =
    new ChannelFactory<IWCFServer>(binding, address);  
IWCFServer server = channelFactory.CreateChannel();  
  
Customer customer = server.GetCustomer(42);  
Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 <span data-ttu-id="8c5b3-174">この例では、リモート処理の例に最も近いことから、チャネル レベルでのプログラミングを示しています。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-174">This example shows programming at the channel level because it is most similar to the Remoting example.</span></span> <span data-ttu-id="8c5b3-175">また、Visual Studio の **サービス参照の追加** アプローチを使用して、クライアントプログラミングを簡略化するコードを生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-175">Also available is the **Add Service Reference** approach in Visual Studio that generates code to simplify client programming.</span></span> <span data-ttu-id="8c5b3-176">詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-176">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="8c5b3-177">クライアントのチャネル レベルのプログラミング</span><span class="sxs-lookup"><span data-stu-id="8c5b3-177">Client Channel-Level Programming</span></span>](./extending/client-channel-level-programming.md)  
  
- [<span data-ttu-id="8c5b3-178">方法: サービス参照を追加、更新、または削除する</span><span class="sxs-lookup"><span data-stu-id="8c5b3-178">How to: Add, Update, or Remove a Service Reference</span></span>](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a><span data-ttu-id="8c5b3-179">シリアル化の使用方法</span><span class="sxs-lookup"><span data-stu-id="8c5b3-179">Serialization Usage</span></span>  
 <span data-ttu-id="8c5b3-180">.NET リモート処理と WCF は、どちらもクライアントとサーバーの間のオブジェクト送信にシリアル化を使用しますが、次の重要な点が異なります。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-180">Both .NET Remoting and WCF use serialization to send objects between client and server, but they differ in these important ways:</span></span>  
  
1. <span data-ttu-id="8c5b3-181">シリアル化の対象を示すために異なるシリアライザーと規則を使用します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-181">They use different serializers and conventions to indicate what to serialize.</span></span>  
  
2. <span data-ttu-id="8c5b3-182">.NET リモート処理では、"参照渡し" のシリアル化をサポートしています。これによって、1 つの階層でメソッドまたはプロパティへのアクセスを行い、セキュリティ境界をまたいだ別の階層でコードを実行できます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-182">.NET Remoting supports "by reference" serialization that allows method or property access on one tier to execute code on the other tier, which is across security boundaries.</span></span> <span data-ttu-id="8c5b3-183">この機能によってセキュリティの脆弱性が露呈することが、信頼できないクライアントにはリモート処理のエンドポイントを決して公開できない、主な理由の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-183">This capability exposes security vulnerabilities and is one of the main reasons why Remoting endpoints should never be exposed to untrusted clients.</span></span>  
  
3. <span data-ttu-id="8c5b3-184">リモート処理で使用されるシリアル化はオプトアウト (シリアル化しないものを明示的に除外する) で、WCF でのシリアル化はオプトイン (どのメンバーをシリアル化するのかを明示的にマークする) です。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-184">Serialization used by Remoting is opt-out (explicitly exclude what not to serialize) and WCF serialization is opt-in (explicitly mark which members to serialize).</span></span>  
  
#### <a name="serialization-in-net-remoting"></a><span data-ttu-id="8c5b3-185">.NET リモート処理でのシリアル化</span><span class="sxs-lookup"><span data-stu-id="8c5b3-185">Serialization in .NET Remoting</span></span>  
 <span data-ttu-id="8c5b3-186">.NET リモート処理では、クライアントとサーバーの間でオブジェクトをシリアル化および逆シリアル化するために次の 2 つの方法をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-186">.NET Remoting supports two ways to serialize and deserialize objects between the client and server:</span></span>  
  
- <span data-ttu-id="8c5b3-187">*値渡し* –オブジェクトの値は階層の境界をまたいでシリアル化され、そのオブジェクトの新しいインスタンスがもう一方の層に作成されます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-187">*By value* – the values of the object are serialized across tier boundaries, and a new instance of that object is created on the other tier.</span></span> <span data-ttu-id="8c5b3-188">この新しいインスタンスのメソッドまたはプロパティへの呼び出しはいずれもローカルに実行され、元のオブジェクトまたは階層には影響しません。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-188">Any calls to methods or properties of that new instance execute only locally and do not affect the original object or tier.</span></span>  
  
- <span data-ttu-id="8c5b3-189">*参照渡し* -特別な "オブジェクト参照" は、階層の境界を越えてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-189">*By reference* – a special "object reference" is serialized across tier boundaries.</span></span> <span data-ttu-id="8c5b3-190">1 つの階層がそのオブジェクトのメソッドまたはプロパティとやり取りをする場合、元の階層の元のオブジェクトに対して通信を行います。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-190">When one tier interacts with methods or properties of that object, it communicates back to the original object on the original tier.</span></span> <span data-ttu-id="8c5b3-191">参照渡しのオブジェクトは、いずれかの方向、つまりサーバーからクライアント、またはクライアントからサーバーにフローできます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-191">By-reference objects can flow in either direction – server to client, or client to server.</span></span>  
  
 <span data-ttu-id="8c5b3-192">リモート処理での値渡し型は、次の例のように、[Serializable] 属性でマークされるか、ISerializable を実装します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-192">By-value types in Remoting are marked with the [Serializable] attribute or implement ISerializable, like in the following example:</span></span>  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="8c5b3-193">参照渡し型は、次の例のように、MarshalByRefObject クラスから派生します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-193">By-reference types derive from the MarshalByRefObject class, like in the following example:</span></span>  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="8c5b3-194">リモート処理の参照渡しのオブジェクトによる影響を理解することは、非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-194">It is extremely important to understand the implications of Remoting’s by-reference objects.</span></span> <span data-ttu-id="8c5b3-195">どちらかの階層 (クライアントまたはサーバー) が参照渡しのオブジェクトをもう一方の階層に送信する場合、すべてのメソッド呼び出しは、オブジェクトを持つ元の階層で実行されます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-195">If either tier (client or server) sends a by-reference object to the other tier, all method calls execute back on the tier owning the object.</span></span> <span data-ttu-id="8c5b3-196">たとえば、サーバーから返される参照渡しのオブジェクトでクライアントが呼び出すメソッドは、サーバーでコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-196">For example, a client calling methods on a by-reference object returned by the server will execute code on the server.</span></span> <span data-ttu-id="8c5b3-197">同様に、クライアントから提供される参照渡しのオブジェクトでサーバーが呼び出すメソッドは、クライアントでコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-197">Similarly, a server calling methods on a by-reference object provided by the client will execute code back on the client.</span></span> <span data-ttu-id="8c5b3-198">このため、.NET リモート処理は、完全に信頼できる環境内でのみ使用することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-198">For this reason, the use of .NET Remoting is recommended only within fully-trusted environments.</span></span> <span data-ttu-id="8c5b3-199">パブリック .NET リモート処理のエンドポイントを信頼できないクライアントに公開すると、リモート処理サーバーが攻撃に対して無防備な状態になります。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-199">Exposing a public .NET Remoting endpoint to untrusted clients will make a Remoting server vulnerable to attack.</span></span>  
  
#### <a name="serialization-in-wcf"></a><span data-ttu-id="8c5b3-200">WCF でのシリアル化</span><span class="sxs-lookup"><span data-stu-id="8c5b3-200">Serialization in WCF</span></span>  
 <span data-ttu-id="8c5b3-201">WCF では、値渡しのシリアル化のみをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-201">WCF supports only by-value serialization.</span></span> <span data-ttu-id="8c5b3-202">クライアントとサーバーの間で交換する型を定義するための最も一般的な方法は、次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-202">The most common way to define a type to exchange between client and server is like in the following example:</span></span>  
  
```csharp
[DataContract]  
public class WCFCustomer  
{  
    [DataMember]  
    public string FirstName { get; set; }  
  
    [DataMember]  
    public string LastName { get; set; }  
  
    [DataMember]  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="8c5b3-203">[DataContract] 属性は、この型をクライアントとサーバーの間でシリアル化および逆シリアル化ができる型として識別します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-203">The [DataContract] attribute identifies this type as one that can be serialized and deserialized between client and server.</span></span> <span data-ttu-id="8c5b3-204">[DataMember] 属性は、シリアル化する個々のプロパティまたはフィールドを識別します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-204">The [DataMember] attribute identifies the individual properties or fields to serialize.</span></span>  
  
 <span data-ttu-id="8c5b3-205">WCF が階層をまたいでオブジェクトを送信する場合は、値のみをシリアル化し、もう一方の階層でオブジェクトの新しいインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-205">When WCF sends an object across tiers, it serializes only the values and creates a new instance of the object on the other tier.</span></span> <span data-ttu-id="8c5b3-206">オブジェクトの値とのやり取りはローカルでのみ発生し、.NET リモート処理の参照渡しのオブジェクトのような方法でもう一方の階層と通信することはありません。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-206">Any interactions with the values of the object occur only locally – they do not communicate with the other tier the way .NET Remoting by-reference objects do.</span></span> <span data-ttu-id="8c5b3-207">詳細については、「 [シリアル化と逆シリアル化](./feature-details/serialization-and-deserialization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-207">For more information, see [Serialization and Deserialization](./feature-details/serialization-and-deserialization.md).</span></span>  
  
### <a name="exception-handling-capabilities"></a><span data-ttu-id="8c5b3-208">例外処理の機能</span><span class="sxs-lookup"><span data-stu-id="8c5b3-208">Exception Handling Capabilities</span></span>  
  
#### <a name="exceptions-in-net-remoting"></a><span data-ttu-id="8c5b3-209">.NET リモート処理での例外</span><span class="sxs-lookup"><span data-stu-id="8c5b3-209">Exceptions in .NET Remoting</span></span>  
 <span data-ttu-id="8c5b3-210">リモート処理サーバーによってスローされた例外は、シリアル化され、クライアントに送信されて、その他すべての例外と同様に、クライアントでローカルにスローされます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-210">Exceptions thrown by a Remoting server are serialized, sent to the client, and thrown locally on the client like any other exception.</span></span> <span data-ttu-id="8c5b3-211">カスタムの例外は、Exception 型をサブクラス化して [Serializable] でマークすることによって作成できます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-211">Custom exceptions can be created by sub-classing the Exception type and marking it with [Serializable].</span></span>   <span data-ttu-id="8c5b3-212">フレームワークの例外の大部分は既にこの方法でマークされているため、サーバーによるスロー、シリアル化、およびクライアントでの再スローが可能です。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-212">Most framework exceptions are already marked in this way, allowing most to be thrown by the server, serialized, and re-thrown on the client.</span></span> <span data-ttu-id="8c5b3-213">この設計は開発中には便利ですが、サーバー側の情報が誤ってクライアントに公開されてしまう可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-213">Though this design is convenient during development, server-side information can inadvertently be disclosed to the client.</span></span> <span data-ttu-id="8c5b3-214">リモート処理の使用を完全に信頼できる環境に限定する必要がある理由はさまざまですが、これもその 1 つです。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-214">This is one of many reasons Remoting should be used only in fully-trusted environments.</span></span>  
  
#### <a name="exceptions-and-faults-in-wcf"></a><span data-ttu-id="8c5b3-215">WCF での例外とエラー</span><span class="sxs-lookup"><span data-stu-id="8c5b3-215">Exceptions and Faults in WCF</span></span>  
 <span data-ttu-id="8c5b3-216">WCF では、不注意による情報の漏洩につながる可能性があるため、サーバーからクライアントに任意の例外型を返すことはできません。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-216">WCF does not allow arbitrary exception types to be returned from the server to the client because it could lead to inadvertent information disclosure.</span></span> <span data-ttu-id="8c5b3-217">サービス操作によって予期しない例外がスローされた場合、汎用の FaultException がクライアントでスローされます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-217">If a service operation throws an unexpected exception, it causes a general purpose FaultException to be thrown on the client.</span></span> <span data-ttu-id="8c5b3-218">この例外には、問題の発生原因や発生場所の情報は含まれませんが、これらは一部のアプリケーションにとっては必要ありません。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-218">This exception does not carry any information why or where the problem occurred, and for some applications this is sufficient.</span></span> <span data-ttu-id="8c5b3-219">より豊富なエラー情報をクライアントに伝える必要があるアプリケーションは、エラー コントラクトを定義することによってこれを実行します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-219">Applications that need to communicate richer error information to the client do this by defining a fault contract.</span></span>  
  
 <span data-ttu-id="8c5b3-220">方法としては、まずエラー情報を伝送するための [DataContract] 型を作成します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-220">To do this, first create a [DataContract] type to carry the fault information.</span></span>  
  
```csharp
[DataContract]  
public class CustomerServiceFault  
{  
    [DataMember]  
    public string ErrorMessage { get; set; }  
  
    [DataMember]  
    public int CustomerId {get;set;}  
}  
```  
  
 <span data-ttu-id="8c5b3-221">各サービス操作に使用するエラー コントラクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-221">Specify the fault contract to use for each service operation.</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="8c5b3-222">サーバーは、FaultException のスローによってエラー状態を報告します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-222">The server reports error conditions by throwing a FaultException.</span></span>  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {
        CustomerId = customerId,
        ErrorMessage = "Illegal customer Id"
    });  
```  
  
 <span data-ttu-id="8c5b3-223">また、クライアントがサーバーに要求を行う場合は、常にエラーを通常の例外としてキャッチできます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-223">And whenever the client makes a request to the server, it can catch faults as normal exceptions.</span></span>  
  
```csharp
try  
{  
    Customer customer = server.GetCustomer(-1);  
}  
catch (FaultException<CustomerServiceFault> fault)  
{  
    Console.WriteLine($"Fault received: {fault.Detail.ErrorMessage}");
}  
```  
  
 <span data-ttu-id="8c5b3-224">エラー コントラクトの詳細については、「<xref:System.ServiceModel.FaultException>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-224">For more information about fault contracts, see <xref:System.ServiceModel.FaultException>.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="8c5b3-225">セキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="8c5b3-225">Security Considerations</span></span>  
  
#### <a name="security-in-net-remoting"></a><span data-ttu-id="8c5b3-226">.NET リモート処理でのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="8c5b3-226">Security in .NET Remoting</span></span>  
 <span data-ttu-id="8c5b3-227">一部の .NET リモート処理チャネルでは、チャネル層 (IPC と TCP) での認証および暗号化などのセキュリティ機能をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-227">Some .NET Remoting channels support security features such as authentication and encryption at the channel layer (IPC and TCP).</span></span> <span data-ttu-id="8c5b3-228">HTTP チャネルでは、認証と暗号化の両方にインターネット インフォメーション サービス (IIS) を利用しています。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-228">The HTTP channel relies on Internet Information Services (IIS) for both authentication and encryption.</span></span> <span data-ttu-id="8c5b3-229">こういったサポートがあっても、.NET リモート処理を安全性が低い通信プロトコルと見なし、完全に信頼できる環境内に使用を制限する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-229">Despite this support, you should consider .NET Remoting an unsecure communication protocol and use it only within fully-trusted environments.</span></span> <span data-ttu-id="8c5b3-230">パブリック リモート処理のエンドポイントをインターネットや信頼できないクライアントに公開することは絶対に避けてください。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-230">Never expose a public Remoting endpoint to the Internet or untrusted clients.</span></span>  
  
#### <a name="security-in-wcf"></a><span data-ttu-id="8c5b3-231">WCF でのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="8c5b3-231">Security in WCF</span></span>  
 <span data-ttu-id="8c5b3-232">WCF は、.NET リモート処理で見つかった種類の脆弱性に対処する必要性などがあったため、セキュリティを考慮して設計されています。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-232">WCF was designed with security in mind, in part to address the kinds of vulnerabilities found in .NET Remoting.</span></span> <span data-ttu-id="8c5b3-233">WCF では、トランスポートとメッセージの両方のレベルでセキュリティが提供され、認証、承認、暗号化などのために、数多くのオプションが利用できます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-233">WCF offers security at both the transport and message level, and offers many options for authentication, authorization, encryption, and so on.</span></span> <span data-ttu-id="8c5b3-234">詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-234">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="8c5b3-235">Security</span><span class="sxs-lookup"><span data-stu-id="8c5b3-235">Security</span></span>](./feature-details/security.md)  
  
- [<span data-ttu-id="8c5b3-236">WCF セキュリティガイダンス</span><span class="sxs-lookup"><span data-stu-id="8c5b3-236">WCF Security Guidance</span></span>](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a><span data-ttu-id="8c5b3-237">WCF への移行</span><span class="sxs-lookup"><span data-stu-id="8c5b3-237">Migrating to WCF</span></span>  
  
### <a name="why-migrate-from-remoting-to-wcf"></a><span data-ttu-id="8c5b3-238">リモート処理から WCF に移行する理由</span><span class="sxs-lookup"><span data-stu-id="8c5b3-238">Why Migrate from Remoting to WCF?</span></span>  
  
- <span data-ttu-id="8c5b3-239">**.NET リモート処理はレガシー製品です。**</span><span class="sxs-lookup"><span data-stu-id="8c5b3-239">**.NET Remoting is a legacy product.**</span></span> <span data-ttu-id="8c5b3-240">「 [.Net リモート処理](/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))」で説明されているように、これは従来の製品と見なされ、新規の開発にはお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-240">As described in [.NET Remoting](/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)), it is considered a legacy product and is not recommended for new development.</span></span> <span data-ttu-id="8c5b3-241">新規および既存のアプリケーションには、WCF または ASP.NET Web API をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-241">WCF or ASP.NET Web API are recommended for new and existing applications.</span></span>  
  
- <span data-ttu-id="8c5b3-242">**WCF では、クロスプラットフォーム標準を使用しています。**</span><span class="sxs-lookup"><span data-stu-id="8c5b3-242">**WCF uses cross-platform standards.**</span></span> <span data-ttu-id="8c5b3-243">WCF は、クロスプラットフォームの相互運用性を考慮して設計されており、さまざまな業界標準 (SOAP、WS-Security、WS-Trust など) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-243">WCF was designed with cross-platform interoperability in mind and supports many industry standards (SOAP, WS-Security, WS-Trust, etc.).</span></span> <span data-ttu-id="8c5b3-244">WCF サービスでは、Windows 以外のオペレーション システムで動作中のクライアントとの相互運用ができます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-244">A WCF service can interoperate with clients running on operating systems other than Windows.</span></span> <span data-ttu-id="8c5b3-245">リモート処理は、主に、サーバーアプリケーションとクライアントアプリケーションの両方が Windows オペレーティングシステムで .NET Framework を使用して実行する環境向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-245">Remoting was designed primarily for environments where both the server and client applications run using .NET Framework on a Windows operating system.</span></span>
  
- <span data-ttu-id="8c5b3-246">**WCF にはセキュリティが組み込まれています。**</span><span class="sxs-lookup"><span data-stu-id="8c5b3-246">**WCF has built-in security.**</span></span> <span data-ttu-id="8c5b3-247">WCF はセキュリティを考慮して設計されており、認証、トランスポートレベルのセキュリティ、メッセージレベルのセキュリティなどのさまざまなオプションを提供しています。リモート処理は、アプリケーションの相互運用を容易にするように設計されていますが、信頼されていない環境ではセキュリティで保護するように設計されていません。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-247">WCF was designed with security in mind and offers many options for authentication, transport level security, message level security, etc. Remoting was designed to make it easy for applications to interoperate but was not designed to be secure in non-trusted environments.</span></span> <span data-ttu-id="8c5b3-248">WCF は信頼できる環境と信頼できない環境の両方で動作するよう設計されました。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-248">WCF was designed to work in both trusted and non-trusted environments.</span></span>  
  
### <a name="migration-recommendations"></a><span data-ttu-id="8c5b3-249">移行の推奨事項</span><span class="sxs-lookup"><span data-stu-id="8c5b3-249">Migration Recommendations</span></span>  
 <span data-ttu-id="8c5b3-250">.NET リモート処理から WCF に移行するための推奨手順を次に示します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-250">The following are the recommended steps to migrate from .NET Remoting to WCF:</span></span>  
  
- <span data-ttu-id="8c5b3-251">**サービス コントラクトを作成する。**</span><span class="sxs-lookup"><span data-stu-id="8c5b3-251">**Create the service contract.**</span></span> <span data-ttu-id="8c5b3-252">サービス インターフェイスの型を定義し、[ServiceContract] 属性でマークします。クライアントからの呼び出しを可能にするすべてのメソッドを [OperationContract] でマークします。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-252">Define your service interface types, and mark them with the [ServiceContract] attribute.Mark all the methods the clients will be allowed to call with [OperationContract].</span></span>  
  
- <span data-ttu-id="8c5b3-253">**データコントラクトを作成します。**</span><span class="sxs-lookup"><span data-stu-id="8c5b3-253">**Create the data contract.**</span></span> <span data-ttu-id="8c5b3-254">サーバーとクライアントの間で交換されるデータ型を定義し、[DataContract] 属性でマークします。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-254">Define the data types that will be exchanged between server and client, and mark them with the [DataContract] attribute.</span></span> <span data-ttu-id="8c5b3-255">クライアントから使用できるようにするすべてのフィールドとプロパティを [DataMember] でマークします。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-255">Mark all the fields and properties the client will be allowed to use with [DataMember].</span></span>  
  
- <span data-ttu-id="8c5b3-256">**エラー コントラクトを作成する (省略可能)。**</span><span class="sxs-lookup"><span data-stu-id="8c5b3-256">**Create the fault contract (optional).**</span></span> <span data-ttu-id="8c5b3-257">エラーが検出されたときにサーバーとクライアントの間で交換される型を作成します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-257">Create the types that will be exchanged between server and client when errors are encountered.</span></span> <span data-ttu-id="8c5b3-258">これらの型を [DataContract] と [DataMember] でマークしてシリアル化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-258">Mark these types with [DataContract] and [DataMember] to make them serializable.</span></span> <span data-ttu-id="8c5b3-259">[OperationContract] でマークしたすべてのサービス操作について、どのエラーが返されるのかを示すために [FaultContract] でも同様にマークします。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-259">For all service operations you marked with [OperationContract], also mark them with [FaultContract] to indicate which errors they may return.</span></span>  
  
- <span data-ttu-id="8c5b3-260">**サービスを構成し、ホストする。**</span><span class="sxs-lookup"><span data-stu-id="8c5b3-260">**Configure and host the service.**</span></span> <span data-ttu-id="8c5b3-261">サービス コントラクトの作成後の手順としては、エンドポイントでサービスを公開するためにバインドを構成します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-261">Once the service contract has been created, the next step is to configure a binding to expose the service at an endpoint.</span></span> <span data-ttu-id="8c5b3-262">詳細については、「 [エンドポイント: アドレス、バインディング、およびコントラクト](./feature-details/endpoints-addresses-bindings-and-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-262">For more information, see [Endpoints: Addresses, Bindings, and Contracts](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span></span>  
  
 <span data-ttu-id="8c5b3-263">リモート処理アプリケーションの WCF への移行が完了した後は、.NET リモート処理で依存関係を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-263">Once a Remoting application has been migrated to WCF, it is still important to remove dependencies on .NET Remoting.</span></span> <span data-ttu-id="8c5b3-264">これにより、リモート処理の脆弱性がアプリケーションから確実に取り除かれます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-264">This ensures that any Remoting vulnerabilities are removed from the application.</span></span> <span data-ttu-id="8c5b3-265">実行する必要がある手順は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-265">These steps include the following:</span></span>  
  
- <span data-ttu-id="8c5b3-266">**MarshalByRefObject の使用を中止する。**</span><span class="sxs-lookup"><span data-stu-id="8c5b3-266">**Discontinue use of MarshalByRefObject.**</span></span> <span data-ttu-id="8c5b3-267">MarshalByRefObject 型は、リモート処理のためだけに存在する型で、WCF では使用されません。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-267">The MarshalByRefObject type exists only for Remoting and is not used by WCF.</span></span> <span data-ttu-id="8c5b3-268">MarshalByRefObject をサブクラスに持つアプリケーション型は、削除するか変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-268">Any application types that sub-class MarshalByRefObject should be removed or changed.</span></span>  
  
- <span data-ttu-id="8c5b3-269">**[Serializable] と ISerializable の使用を中止する。**</span><span class="sxs-lookup"><span data-stu-id="8c5b3-269">**Discontinue use of [Serializable] and ISerializable.**</span></span> <span data-ttu-id="8c5b3-270">[Serializable] 属性と ISerializable インターフェイスは、信頼できる環境内の型をシリアル化するように設計されたものであり、これらはリモート処理によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-270">The [Serializable] attribute and ISerializable interface were originally designed to serialize types within trusted environments, and they are used by Remoting.</span></span> <span data-ttu-id="8c5b3-271">WCF のシリアル化では、[DataContract] と [DataMember] でマークされている型を使用します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-271">WCF serialization relies on types being marked with [DataContract] and [DataMember].</span></span> <span data-ttu-id="8c5b3-272">アプリケーションで使用されるデータ型は、ISerializable や [Serializable] を使用せずに [DataContract] を使用するように変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-272">Data types used by an application should be modified to use [DataContract] and not to use ISerializable or [Serializable].</span></span>  
  
### <a name="migration-scenarios"></a><span data-ttu-id="8c5b3-273">移行シナリオ</span><span class="sxs-lookup"><span data-stu-id="8c5b3-273">Migration Scenarios</span></span>  
 <span data-ttu-id="8c5b3-274">WCF で次の一般的なリモート処理のシナリオを実現する方法を見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-274">Now let’s see how to accomplish the following common Remoting scenarios in WCF:</span></span>  
  
1. <span data-ttu-id="8c5b3-275">サーバーからクライアントに値渡しでオブジェクトを返す</span><span class="sxs-lookup"><span data-stu-id="8c5b3-275">Server returns an object by-value to the client</span></span>  
  
2. <span data-ttu-id="8c5b3-276">サーバーからクライアントに参照渡しでオブジェクトを返す</span><span class="sxs-lookup"><span data-stu-id="8c5b3-276">Server returns an object by-reference to the client</span></span>  
  
3. <span data-ttu-id="8c5b3-277">クライアントからサーバーに値渡しでオブジェクトを送信する</span><span class="sxs-lookup"><span data-stu-id="8c5b3-277">Client sends an object by-value to the server</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8c5b3-278">WCF では、クライアントからサーバーに参照渡しでオブジェクを送信することはできません。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-278">Sending an object by-reference from the client to the server is not allowed in WCF.</span></span>  
  
 <span data-ttu-id="8c5b3-279">これらのシナリオを読み進める際は、.NET リモート処理のベースライン インターフェイスが次の例のようになると想定してください。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-279">When reading through these scenarios, assume our baseline interfaces for .NET Remoting look like the following example.</span></span> <span data-ttu-id="8c5b3-280">ここでは、.NET リモート処理の実装は重要ではありません。その理由は、ここで説明するのは WCF を使用して同等の機能を実装する方法のみであるためです。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-280">The .NET Remoting implementation is not important here because we want to illustrate only how to use WCF to implement equivalent functionality.</span></span>  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    // Demonstrates server returning object by-value  
    public Customer GetCustomer(int customerId) {…}  
  
    // Demonstrates server returning object by-reference  
    public CustomerReference GetCustomerReference(int customerId) {…}  
  
    // Demonstrates client passing object to server by-value  
    public bool UpdateCustomer(Customer customer) {…}  
}  
```  
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a><span data-ttu-id="8c5b3-281">シナリオ 1: サービスが値渡しでオブジェクトを返す</span><span class="sxs-lookup"><span data-stu-id="8c5b3-281">Scenario 1: Service Returns an Object by Value</span></span>  
 <span data-ttu-id="8c5b3-282">このシナリオでは、値渡しでクライアントにオブジェクトを返すサーバーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-282">This scenario demonstrates a server returning an object to the client by value.</span></span> <span data-ttu-id="8c5b3-283">WCF は常にサーバーから値渡しでオブジェクトを返すため、次の各手順では、単に通常の WCF サービスを構築する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-283">WCF always returns objects from the server by value, so the following steps simply describe how to build a normal WCF service.</span></span>  
  
1. <span data-ttu-id="8c5b3-284">まずは、WCF サービスのパブリック インターフェイスを定義し、[ServiceContract] 属性でマークします。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-284">Start by defining a public interface for the WCF service and mark it with the [ServiceContract] attribute.</span></span> <span data-ttu-id="8c5b3-285">クライアントが呼び出すサーバー側のメソッドを識別するために [OperationContract] を使用します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-285">We use [OperationContract] to identify the server-side methods our client will call.</span></span>  
  
   ```csharp
   [ServiceContract]  
   public interface ICustomerService  
   {  
       [OperationContract]  
       Customer GetCustomer(int customerId);  
  
       [OperationContract]  
       bool UpdateCustomer(Customer customer);  
   }  
   ```  
  
2. <span data-ttu-id="8c5b3-286">次の手順は、このサービスのデータ コントラクトの作成です。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-286">The next step is to create the data contract for this service.</span></span> <span data-ttu-id="8c5b3-287">これを行うには、[DataContract] 属性でマークされたクラス (インターフェイスではない) を作成します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-287">We do this by creating classes (not interfaces) marked with the [DataContract] attribute.</span></span> <span data-ttu-id="8c5b3-288">クライアントとサーバーの両方に対して表示する個々のプロパティやフィールドは、[DataMember] でマークします。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-288">The individual properties or fields we want visible to both client and server are marked with [DataMember].</span></span> <span data-ttu-id="8c5b3-289">派生型を許可する場合は、それを識別するために [KnownType] 属性を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-289">If we want derived types to be allowed, we must use the [KnownType] attribute to identify them.</span></span> <span data-ttu-id="8c5b3-290">WCF がこのサービス用にシリアル化または逆シリアル化を許可する型は、サービス インターフェイス内の型と、これらの "既知の型" のみです。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-290">The only types WCF will allow to be serialized or deserialized for this service are those in the service interface and these "known types".</span></span> <span data-ttu-id="8c5b3-291">この一覧にないその他の型を交換しようとすると、拒否されます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-291">Attempting to exchange any other type not in this list will be rejected.</span></span>  
  
   ```csharp
   [DataContract]  
   [KnownType(typeof(PremiumCustomer))]  
   public class Customer  
   {  
       [DataMember]  
       public string FirstName { get; set; }  
  
       [DataMember]  
       public string LastName { get; set; }  
  
       [DataMember]  
       public int CustomerId { get; set; }  
   }  
  
   [DataContract]  
   public class PremiumCustomer : Customer
   {  
       [DataMember]  
       public int AccountId { get; set; }  
   }  
   ```  
  
3. <span data-ttu-id="8c5b3-292">次に、サービス インターフェイスの実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-292">Next, we provide the implementation for the service interface.</span></span>  
  
   ```csharp  
   public class CustomerService : ICustomerService  
   {  
       public Customer GetCustomer(int customerId)  
       {  
           // read from database  
       }  
  
       public bool UpdateCustomer(Customer customer)  
       {  
           // write to database  
       }  
   }  
   ```  
  
4. <span data-ttu-id="8c5b3-293">WCF サービスを実行するには、特定の WCF バインドを使用して特定の URL で上記のサービス インターフェイスを公開するエンドポイントを宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-293">To run the WCF service, we need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="8c5b3-294">通常、これを行うには、サーバー プロジェクトの web.config ファイルに次のセクションを追加します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-294">This is typically done by adding the following sections to the server project’s web.config file.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
5. <span data-ttu-id="8c5b3-295">WCF サービスは次のコードで開始できます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-295">The WCF service can then be started with the following code:</span></span>  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     <span data-ttu-id="8c5b3-296">この ServiceHost は、開始されると web.config ファイルを使用して適切なコントラクト、バインド、エンドポイントを確立します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-296">When this ServiceHost is started, it uses the web.config file to establish the proper contract, binding and endpoint.</span></span> <span data-ttu-id="8c5b3-297">構成ファイルの詳細については、「 [構成ファイルを使用したサービスの構成](./configuring-services-using-configuration-files.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-297">For more information about configuration files, see [Configuring Services Using Configuration Files](./configuring-services-using-configuration-files.md).</span></span> <span data-ttu-id="8c5b3-298">このようなサーバーの開始方法は、自己ホストと呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-298">This style of starting the server is known as self-hosting.</span></span> <span data-ttu-id="8c5b3-299">WCF サービスをホストする他の選択肢の詳細については、「 [ホスティングサービス](./hosting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-299">To learn more about other choices for hosting WCF services, see [Hosting Services](./hosting-services.md).</span></span>  
  
6. <span data-ttu-id="8c5b3-300">クライアント プロジェクトの app.config では、サービスのエンドポイントの対応するバインド情報を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-300">The client project’s app.config must declare matching binding information for the service’s endpoint.</span></span> <span data-ttu-id="8c5b3-301">Visual Studio でこれを行う最も簡単な方法は、 **サービス参照の追加**を使用することです。これにより、app.config ファイルが自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-301">The easiest way to do this in Visual Studio is to use **Add Service Reference**, which will automatically update the app.config file.</span></span> <span data-ttu-id="8c5b3-302">また、これと同じ変更を手動で加えることもできます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-302">Alternatively, these same changes can be added manually.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="8c5b3-303">**サービス参照の追加**の使用方法の詳細については、「[方法: サービス参照を追加、更新、または削除](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-303">For more information about using **Add Service Reference**, see [How to: Add, Update, or Remove a Service Reference](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span></span>  
  
7. <span data-ttu-id="8c5b3-304">これで、クライアントから WCF サービスを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-304">Now we can call the WCF service from the client.</span></span> <span data-ttu-id="8c5b3-305">WCF サービスを呼び出すには、そのサービスのチャネル ファクトリを作成し、チャネルを要求して、そのチャネルで必要なメソッドを直接呼び出します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-305">We do this by creating a channel factory for that service, asking it for a channel, and directly calling the method we want on that channel.</span></span> <span data-ttu-id="8c5b3-306">この方法が可能なのは、チャネルがサービスのインターフェイスを実装し、基になる要求/応答のロジックを処理するためです。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-306">We can do this because the channel implements the service’s interface and handles the underlying request/reply logic for us.</span></span> <span data-ttu-id="8c5b3-307">このメソッドの呼び出しからの戻り値は、サーバーの応答の逆シリアル化されたコピーです。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-307">The return value from that method call is the deserialized copy of the server’s response.</span></span>  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
   ```  
  
 <span data-ttu-id="8c5b3-308">WCF によってサーバーからクライアントに返されるオブジェクトは、常に値渡しです。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-308">Objects returned by WCF from the server to the client are always by value.</span></span> <span data-ttu-id="8c5b3-309">オブジェクトは、サーバーから送信されたデータの逆シリアル化されたコピーです。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-309">The objects are deserialized copies of the data sent by the server.</span></span> <span data-ttu-id="8c5b3-310">クライアントは、コールバックによってサーバー コードを呼び出すリスクを冒すことなく、これらのローカル コピーでメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-310">The client can call methods on these local copies without any danger of invoking server code through callbacks.</span></span>  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a><span data-ttu-id="8c5b3-311">シナリオ 2: サーバーから参照渡しでオブジェクトを返す</span><span class="sxs-lookup"><span data-stu-id="8c5b3-311">Scenario 2: Server Returns an Object By Reference</span></span>  
 <span data-ttu-id="8c5b3-312">このシナリオでは、参照渡しでクライアントにオブジェクトを提供するサーバーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-312">This scenario demonstrates the server providing an object to the client by reference.</span></span> <span data-ttu-id="8c5b3-313">.NET リモート処理では、参照渡しでシリアル化された MarshalByRefObject から派生したすべての型に対してこの処理が自動的に行われます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-313">In .NET Remoting, this is handled automatically for any type derived from MarshalByRefObject, which is serialized by-reference.</span></span> <span data-ttu-id="8c5b3-314">このシナリオの例としては、たとえば複数のクライアントが、独立したセッションフルなサーバー側オブジェクトを持てるようにします。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-314">An example of this scenario is allowing multiple clients to have independent sessionful server-side objects.</span></span> <span data-ttu-id="8c5b3-315">前述したように、WCF サービスによって返されるオブジェクトは常に値渡しであるため、参照渡しのオブジェクトに直接相当するものはありませんが、<xref:System.ServiceModel.EndpointAddress10> オブジェクトを使用して参照渡しセマンティクスに類似するものを実現することは可能です。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-315">As previously mentioned, objects returned by a WCF service are always by value, so there is no direct equivalent of a by-reference object, but it is possible to achieve something similar to by-reference semantics using an <xref:System.ServiceModel.EndpointAddress10> object.</span></span> <span data-ttu-id="8c5b3-316">これは、サーバー上のセッションフルな参照渡しのオブジェクトを取得するためにクライアントが使用できる、シリアル化可能な値渡しのオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-316">This is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span> <span data-ttu-id="8c5b3-317">これによって、独立したセッションフルなサーバー側オブジェクトを持つ複数のクライアントを用意するというシナリオが可能になります。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-317">This enables the scenario of having multiple clients with independent sessionful server-side objects.</span></span>  
  
1. <span data-ttu-id="8c5b3-318">まずは、セッションフル オブジェクト自体に対応する WCF サービス コントラクトを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-318">First, we need to define a WCF service contract that corresponds to the sessionful object itself.</span></span>  
  
   ```csharp
   [ServiceContract(SessionMode = SessionMode.Allowed)]  
       public interface ISessionBoundObject  
       {  
           [OperationContract]  
           string GetCurrentValue();  
  
           [OperationContract]  
           void SetCurrentValue(string value);  
       }  
   ```  
  
    > [!TIP]
    > <span data-ttu-id="8c5b3-319">セッションフル オブジェクトは [ServiceContract] でマークされ、通常の WCF サービス インターフェイスになっていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-319">Notice that the sessionful object is marked with [ServiceContract], making it a normal WCF service interface.</span></span> <span data-ttu-id="8c5b3-320">SessionMode プロパティを設定することは、それがセッションフル サービスになることを意味します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-320">Setting the SessionMode property indicates it will be a sessionful service.</span></span> <span data-ttu-id="8c5b3-321">WCF では、セッションは 2 つのエンドポイント間で送信される複数のメッセージを関連付ける方法です。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-321">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span> <span data-ttu-id="8c5b3-322">つまり、クライアントがこのサービスへの接続を確保すると、クライアントとサーバーの間でセッションが確立されます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-322">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span> <span data-ttu-id="8c5b3-323">クライアントは、サーバー側オブジェクトの単一で一意のインスタンスを、この 1 つのセッション内でのすべてのやり取りに使用することになります。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-323">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span>  
  
2. <span data-ttu-id="8c5b3-324">次に、このサービス インターフェイスの実装を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-324">Next, we need to provide the implementation of this service interface.</span></span> <span data-ttu-id="8c5b3-325">[ServiceBehavior] でこれを示し、InstanceContextMode を設定することによって、この型の一意のインスタンスを各セッションに使用することを WCF に伝えます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-325">By denoting it with [ServiceBehavior] and setting the InstanceContextMode, we tell WCF we want to use a unique instance of this type for an each session.</span></span>  
  
   ```csharp
   [ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
       public class MySessionBoundObject : ISessionBoundObject  
       {  
           private string _value;  
  
           public string GetCurrentValue()  
           {  
               return _value;  
           }  
  
           public void SetCurrentValue(string val)  
           {  
               _value = val;  
           }  
  
       }  
   ```  
  
3. <span data-ttu-id="8c5b3-326">ここで、このセッションフル オブジェクトのインスタンスを入手する方法が必要です。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-326">Now we need a way to obtain an instance of this sessionful object.</span></span> <span data-ttu-id="8c5b3-327">これは、EndpointAddress10 オブジェクトを返すもう 1 つの WCF サービス インターフェイスを作成することによって行います。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-327">We do this by creating another WCF service interface that returns an EndpointAddress10 object.</span></span> <span data-ttu-id="8c5b3-328">これはクライアントがセッションフル オブジェクトの作成に使用できる、エンドポイントのシリアル化可能な形式です。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-328">This is a serializable form of an endpoint that the client can use to create the sessionful object.</span></span>  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     <span data-ttu-id="8c5b3-329">さらに、この WCF サービスを実装します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-329">And we implement this WCF service:</span></span>  
  
   ```csharp
   public class SessionBoundFactory : ISessionBoundFactory  
       {  
           public static ChannelFactory<ISessionBoundObject> _factory =
               new ChannelFactory<ISessionBoundObject>("sessionbound");  

           public SessionBoundFactory()  
           {  
           }  
  
           public EndpointAddress10 GetInstanceAddress()  
           {  
               IClientChannel channel = (IClientChannel)_factory.CreateChannel();  
               return EndpointAddress10.FromEndpointAddress(channel.RemoteAddress);  
           }  
       }  
   ```  
  
     <span data-ttu-id="8c5b3-330">この実装では、セッションフル オブジェクトを作成するためにシングルトン チャネル ファクトリを保持しています。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-330">This implementation maintains a singleton channel factory to create sessionful objects.</span></span> <span data-ttu-id="8c5b3-331">チャネル ファクトリは、GetInstanceAddress() が呼び出されるとチャネルを作成し、このチャネルに関連付けられているリモート アドレスを効率的にポイントする EndpointAddress10 オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-331">When GetInstanceAddress() is called, it creates a channel and creates an EndpointAddress10 object that effectively points to the remote address associated with this channel.</span></span> <span data-ttu-id="8c5b3-332">EndpointAddress10 は、単に値渡しでクライアントに返すことのできるデータ型です。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-332">EndpointAddress10 is simply a data type that can be returned to the client by-value.</span></span>  
  
4. <span data-ttu-id="8c5b3-333">以下の例に示すように、次の 2 つの処理を実行して、サーバーの構成ファイルを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-333">We need to modify the server’s configuration file by doing the following two things as shown in the example below:</span></span>  
  
    1. <span data-ttu-id="8c5b3-334">\<client>セッションフルオブジェクトのエンドポイントを記述するセクションを宣言します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-334">Declare a \<client> section that describes the endpoint for the sessionful object.</span></span> <span data-ttu-id="8c5b3-335">この処理が必要な理由は、この状況ではサーバーがクライアントとしても機能するためです。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-335">This is necessary because the server also acts as a client in this situation.</span></span>  
  
    2. <span data-ttu-id="8c5b3-336">ファクトリおよびセッションフル オブジェクトのエンドポイントを宣言します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-336">Declare endpoints for the factory and sessionful object.</span></span> <span data-ttu-id="8c5b3-337">この処理は、クライアントがサービス エンドポイントと通信して EndpointAddress10 の取得とセッションフル チャネルの作成を実行できるようにするために必要です。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-337">This is necessary to allow the client to communicate with the service endpoints to acquire the EndpointAddress10 and to create the sessionful channel.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
         <client>  
          <endpoint name="sessionbound"  
                    address="net.tcp://localhost:8081/SessionBoundObject"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundObject"/>  
        </client>  
        <services>  
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
          <service name="Server.MySessionBoundObject">  
            <endpoint address="net.tcp://localhost:8081/SessionBoundObject"  
                      binding="netTcpBinding"  
                      contract="Shared.ISessionBoundObject" />  
          </service>  
          <service name="Server.SessionBoundFactory">  
            <endpoint address="net.tcp://localhost:8081/SessionBoundFactory"  
                      binding="netTcpBinding"  
                      contract="Shared.ISessionBoundFactory" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="8c5b3-338">これで、次のサービスを開始できます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-338">And then we can start these services:</span></span>  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5. <span data-ttu-id="8c5b3-339">クライアントの構成は、そのプロジェクトの app.config ファイル内でこれらの同じエンドポイントを宣言することによって行います。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-339">We configure the client by declaring these same endpoints in its project’s app.config file.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
          <endpoint name="sessionbound"  
                    address="net.tcp://localhost:8081/SessionBoundObject"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundObject"/>  
          <endpoint name="factory"  
                    address="net.tcp://localhost:8081/SessionBoundFactory"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundFactory"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
6. <span data-ttu-id="8c5b3-340">セッションフル オブジェクトを作成して使用するために、クライアントでは、次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-340">In order to create and use this sessionful object, the client must do the following steps:</span></span>  
  
    1. <span data-ttu-id="8c5b3-341">ISessionBoundFactory サービスへのチャネルを作成する。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-341">Create a channel to the ISessionBoundFactory service.</span></span>  
  
    2. <span data-ttu-id="8c5b3-342">このチャネルを使用してサービスを呼び出し、EndpointAddress10 を取得する。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-342">Use that channel to invoke that service to obtain an EndpointAddress10.</span></span>  
  
    3. <span data-ttu-id="8c5b3-343">EndpointAddress10 を使用してチャネルを作成し、セッションフル オブジェクトを取得する。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-343">Use the EndpointAddress10 to create a channel to obtain a sessionful object.</span></span>  
  
    4. <span data-ttu-id="8c5b3-344">セッションフル オブジェクトと対話し、複数の呼び出し間でインスタンスが同じであることを示す。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-344">Interact with the sessionful object to demonstrate it remains the same instance across multiple calls.</span></span>  
  
   ```csharp
   ChannelFactory<ISessionBoundFactory> channelFactory =
       new ChannelFactory<ISessionBoundFactory>("factory");  
   ISessionBoundFactory sessionFactory = channelFactory.CreateChannel();  
  
   EndpointAddress10 address1 = sessionFactory.GetInstanceAddress();  
   EndpointAddress10 address2 = sessionFactory.GetInstanceAddress();  
  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory1 =
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),
                                               address1.ToEndpointAddress());  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory2 =
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),
                                               address2.ToEndpointAddress());  
  
   ISessionBoundObject sessionInstance1 = sessionObjectFactory1.CreateChannel();  
   ISessionBoundObject sessionInstance2 = sessionObjectFactory2.CreateChannel();  
  
   sessionInstance1.SetCurrentValue("Hello");  
   sessionInstance2.SetCurrentValue("World");  
  
   if (sessionInstance1.GetCurrentValue() == "Hello" &&  
       sessionInstance2.GetCurrentValue() == "World")  
   {  
       Console.WriteLine("sessionful server object works as expected");  
   }  
   ```  
  
 <span data-ttu-id="8c5b3-345">WCF は常に値渡しでオブジェクトを返しますが、EndpointAddress10 を使用することで、参照渡しのセマンティクスに相当するものをサポートすることは可能です。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-345">WCF always returns objects by value, but it is possible to support the equivalent of by-reference semantics through the use of EndpointAddress10.</span></span> <span data-ttu-id="8c5b3-346">これによって、クライアントからセッションフル WCF サービス インスタンスを要求できるようになり、要求後は他のすべての WCF サービスのように対話ができます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-346">This permits the client to request a sessionful WCF service instance, after which it can interact with it like any other WCF service.</span></span>  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a><span data-ttu-id="8c5b3-347">シナリオ 3: クライアントから値渡しのインスタンスをサーバーに送信する</span><span class="sxs-lookup"><span data-stu-id="8c5b3-347">Scenario 3: Client Sends Server a By-Value Instance</span></span>  
 <span data-ttu-id="8c5b3-348">このシナリオでは、サーバーに値渡しで非プリミティブ オブジェクト インスタンスを送信するクライアントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-348">This scenario demonstrates the client sending a non-primitive object instance to the server by value.</span></span> <span data-ttu-id="8c5b3-349">WCF は値渡しでのみオブジェクトを送信するため、このシナリオでは通常の WCF の使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-349">Because WCF only sends objects by value, this scenario demonstrates normal WCF usage.</span></span>  
  
1. <span data-ttu-id="8c5b3-350">シナリオ 1 と同じ WCF サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-350">Use the same WCF Service from Scenario 1.</span></span>  
  
2. <span data-ttu-id="8c5b3-351">クライアントを使用して新しい値渡しのオブジェクト (Customer) を作成し、チャネルを作成して ICustomerService サービスと通信し、それにオブジェクトを送信します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-351">Use the client to create a new by-value object (Customer), create a channel to communicate with the ICustomerService service, and send the object to it.</span></span>  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   PremiumCustomer customer = new PremiumCustomer {
   FirstName = "Bob",
   LastName = "Jones",
   CustomerId = 43,
   AccountId = 99};  
   bool success = service.UpdateCustomer(customer);  
   Console.WriteLine($"  Server returned {success}.");
   ```  
  
     <span data-ttu-id="8c5b3-352">Customer オブジェクトはシリアル化され、サーバーに送信されて、そのオブジェクトの新しいコピーへと逆シリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-352">The customer object will be serialized, and sent to the server, where it is deserialized into a new copy of that object.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8c5b3-353">このコードでは、派生型 (PremiumCustomer) の送信についても示しています。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-353">This code also illustrates sending a derived type (PremiumCustomer).</span></span> <span data-ttu-id="8c5b3-354">サービス インターフェイスは Customer オブジェクトを要求していますが、Customer クラスの [KnownType] 属性は、PremiumCustomer も同様に許可されていることを示していました。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-354">The service interface expects a Customer object, but the [KnownType] attribute on the Customer class indicated PremiumCustomer was also allowed.</span></span> <span data-ttu-id="8c5b3-355">このサービス インターフェイスによって他の型をシリアル化または逆シリアル化しようとしても、WCF は必ず失敗します。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-355">WCF will fail any attempt to serialize or deserialize any other type through this service interface.</span></span>  
  
 <span data-ttu-id="8c5b3-356">WCF での通常のデータ交換は、値渡しで行われます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-356">Normal WCF exchanges of data are by value.</span></span> <span data-ttu-id="8c5b3-357">これにより、こういったデータ オブジェクトの 1 つでのメソッド呼び出しはローカルでのみ実行され、他の階層ではコードが呼び出されないことが保証されています。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-357">This guarantees that invoking methods on one of these data objects executes only locally – it will not invoke code on the other tier.</span></span> <span data-ttu-id="8c5b3-358">サーバー *から* 返される参照渡しのオブジェクトのような処理を実行することは可能ですが、クライアントが参照渡しのオブジェクトをサーバー *に* 渡すことはできません。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-358">While it is possible to achieve something like by-reference objects returned *from* the server, it is not possible for a client to pass a by-reference object *to* the server.</span></span> <span data-ttu-id="8c5b3-359">クライアントとサーバーの間で対話を必要とするシナリオは、WCF で双方向サービスを使用することによって実現できます。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-359">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span> <span data-ttu-id="8c5b3-360">詳細については、「 [双方向サービス](./feature-details/duplex-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-360">For more information, see [Duplex Services](./feature-details/duplex-services.md).</span></span>  
  
## <a name="summary"></a><span data-ttu-id="8c5b3-361">まとめ</span><span class="sxs-lookup"><span data-stu-id="8c5b3-361">Summary</span></span>  
 <span data-ttu-id="8c5b3-362">.NET リモート処理は、完全に信頼できる環境内のみでの使用を意図した通信フレームワークです。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-362">.NET Remoting is a communication framework intended to be used only within fully-trusted environments.</span></span> <span data-ttu-id="8c5b3-363">これはレガシー製品であり、旧バージョンとの互換性のためだけにサポートされています。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-363">It is a legacy product and supported only for backward compatibility.</span></span> <span data-ttu-id="8c5b3-364">新しいアプリケーションの構築には使用できません。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-364">It should not be used to build new applications.</span></span> <span data-ttu-id="8c5b3-365">反対に、WCF はセキュリティを考慮して設計されており、新規および既存のアプリケーション向けに推奨されています。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-365">Conversely, WCF was designed with security in mind and is recommended for new and existing applications.</span></span> <span data-ttu-id="8c5b3-366">既存のリモート処理アプリケーションから、WCF または ASP.NET Web API を使用したアプリケーションに移行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8c5b3-366">Microsoft recommends that existing Remoting applications be migrated to use WCF or ASP.NET Web API instead.</span></span>
