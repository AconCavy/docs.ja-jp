---
title: カスタム メッセージ インターセプター
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: b9a517d0f8ada3680d49cd5ab0b13fa9e4d85402
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600063"
---
# <a name="custom-message-interceptor"></a><span data-ttu-id="3fc78-102">カスタム メッセージ インターセプター</span><span class="sxs-lookup"><span data-stu-id="3fc78-102">Custom Message Interceptor</span></span>
<span data-ttu-id="3fc78-103">このサンプルでは、チャネル拡張モデルの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3fc78-103">This sample demonstrates the use of the channel extensibility model.</span></span> <span data-ttu-id="3fc78-104">特に、チャネル ファクトリとチャネル リスナーを作成するカスタム バインド要素を実装して、ランタイム スタックの特定のポイントですべての送受信メッセージを中断する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3fc78-104">In particular, it shows how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span> <span data-ttu-id="3fc78-105">また、このサンプルには、こうしたカスタム ファクトリの使用方法を示すクライアントとサーバーも含まれます。</span><span class="sxs-lookup"><span data-stu-id="3fc78-105">The sample also includes a client and server that demonstrate the use of these custom factories.</span></span>  
  
 <span data-ttu-id="3fc78-106">このサンプルでは、クライアントとサービスは両方ともコンソール プログラム (.exe) です。</span><span class="sxs-lookup"><span data-stu-id="3fc78-106">In this sample, both the client and the service are console programs (.exe).</span></span> <span data-ttu-id="3fc78-107">そして、これらのクライアントとサービスの両方で、カスタム バインド要素およびこれに関連付けられたランタイム オブジェクトを含む共通ライブラリ (.dll) を使用します。</span><span class="sxs-lookup"><span data-stu-id="3fc78-107">The client and service both make use of a common library (.dll) that contains the custom binding element and its associated run-time objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3fc78-108">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3fc78-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3fc78-109">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="3fc78-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3fc78-110">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="3fc78-110">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3fc78-111">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459)にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="3fc78-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3fc78-112">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="3fc78-112">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 <span data-ttu-id="3fc78-113">このサンプルでは、チャネルフレームワークと次の WCF のベストプラクティスに従って、Windows Communication Foundation (WCF) でカスタム層チャネルを作成するための推奨手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="3fc78-113">The sample describes the recommended procedure for creating a custom layered channel in Windows Communication Foundation (WCF), by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="3fc78-114">カスタム階層チャネルを作成する手順は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3fc78-114">The steps to create a custom layered channel are as follows:</span></span>  
  
1. <span data-ttu-id="3fc78-115">どのチャネル形状をチャネル ファクトリおよびチャネル リスナがサポートするかを決定します。</span><span class="sxs-lookup"><span data-stu-id="3fc78-115">Decide which of the channel shapes your channel factory and channel listener will support.</span></span>  
  
2. <span data-ttu-id="3fc78-116">チャネル形状をサポートするチャネル ファクトリおよびチャネル リスナを作成します。</span><span class="sxs-lookup"><span data-stu-id="3fc78-116">Create a channel factory and a channel listener that support your channel shapes.</span></span>  
  
3. <span data-ttu-id="3fc78-117">チャネル スタックにカスタム階層チャネルを追加するバインド要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="3fc78-117">Add a binding element that adds the custom layered channel to a channel stack.</span></span>  
  
4. <span data-ttu-id="3fc78-118">バインド要素拡張セクションを追加して、新しいバインド要素を構成システムに公開します。</span><span class="sxs-lookup"><span data-stu-id="3fc78-118">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
## <a name="channel-shapes"></a><span data-ttu-id="3fc78-119">チャネル形状</span><span class="sxs-lookup"><span data-stu-id="3fc78-119">Channel Shapes</span></span>  
 <span data-ttu-id="3fc78-120">カスタム階層チャネルを記述する最初の手順として、どの形状がチャネルに必要かを判断します。</span><span class="sxs-lookup"><span data-stu-id="3fc78-120">The first step in writing a custom layered channel is to decide which shapes are required for the channel.</span></span> <span data-ttu-id="3fc78-121">メッセージ インスペクタの場合、下のレイヤでサポートされる任意の形状をサポートします (たとえば、下のレイヤで <xref:System.ServiceModel.Channels.IOutputChannel> と <xref:System.ServiceModel.Channels.IDuplexSessionChannel> が作成できる場合は、<xref:System.ServiceModel.Channels.IOutputChannel> と <xref:System.ServiceModel.Channels.IDuplexSessionChannel> を公開します)。</span><span class="sxs-lookup"><span data-stu-id="3fc78-121">For our message inspector, we support any shape that the layer below us supports (for example, if the layer below us can build <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, then we also expose <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span></span>  
  
## <a name="channel-factory-and-listener-factory"></a><span data-ttu-id="3fc78-122">チャネル ファクトリとリスナ ファクトリ</span><span class="sxs-lookup"><span data-stu-id="3fc78-122">Channel Factory and Listener Factory</span></span>  
 <span data-ttu-id="3fc78-123">カスタム階層チャネルを記述する次の手順では、クライアント チャネルでの <xref:System.ServiceModel.Channels.IChannelFactory> の実装とサービス チャネルでの <xref:System.ServiceModel.Channels.IChannelListener> の実装を作成します。</span><span class="sxs-lookup"><span data-stu-id="3fc78-123">The next step in writing a custom layered channel is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span>  
  
 <span data-ttu-id="3fc78-124">これらのクラスでは、内部ファクトリとリスナが取得され、この内部ファクトリとリスナが `OnCreateChannel` と `OnAcceptChannel` 以外のすべての呼び出しを代行します。</span><span class="sxs-lookup"><span data-stu-id="3fc78-124">These classes take an inner factory and listener, and delegate all but the `OnCreateChannel` and `OnAcceptChannel` calls to the inner factory and listener.</span></span>  
  
```csharp
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{
    //...
}

class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{
    //...
}  
```  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="3fc78-125">バインド要素の追加</span><span class="sxs-lookup"><span data-stu-id="3fc78-125">Adding a Binding Element</span></span>  
 <span data-ttu-id="3fc78-126">このサンプルでは、`InterceptingBindingElement` というカスタム バインド要素を定義します。</span><span class="sxs-lookup"><span data-stu-id="3fc78-126">The sample defines a custom binding element: `InterceptingBindingElement`.</span></span> <span data-ttu-id="3fc78-127">`InterceptingBindingElement`はを `ChannelMessageInterceptor` 入力として受け取り、これを使用して、それを通過 `ChannelMessageInterceptor` するメッセージを操作します。</span><span class="sxs-lookup"><span data-stu-id="3fc78-127">`InterceptingBindingElement` takes a `ChannelMessageInterceptor` as an input, and uses this `ChannelMessageInterceptor` to manipulate messages that pass through it.</span></span> <span data-ttu-id="3fc78-128">公開する必要があるクラスはこれだけです。</span><span class="sxs-lookup"><span data-stu-id="3fc78-128">This is the only class that must be public.</span></span> <span data-ttu-id="3fc78-129">ファクトリ、リスナ、およびチャネルはすべて、ランタイム パブリック インターフェイスの内部実装として設定できます。</span><span class="sxs-lookup"><span data-stu-id="3fc78-129">The factory, listener, and channels can all be internal implementations of the public run-time interfaces.</span></span>  
  
```csharp
public class InterceptingBindingElement : BindingElement
{
}
```  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="3fc78-130">構成サポートの追加</span><span class="sxs-lookup"><span data-stu-id="3fc78-130">Adding Configuration Support</span></span>  
 <span data-ttu-id="3fc78-131">バインディング構成と統合するには、ライブラリで、構成セクション ハンドラをバインディング要素拡張セクションとして定義します。</span><span class="sxs-lookup"><span data-stu-id="3fc78-131">To integrate with binding configuration, the library defines a configuration section handler as a binding element extension section.</span></span> <span data-ttu-id="3fc78-132">クライアントとサーバーの構成ファイルでは、バインド要素拡張を構成システムに登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3fc78-132">The client and server configuration files must register the binding element extension with the configuration system.</span></span> <span data-ttu-id="3fc78-133">バインディング要素を構成システムに公開する実装は、このクラスから派生できます。</span><span class="sxs-lookup"><span data-stu-id="3fc78-133">Implementers that want to expose their binding element to the configuration system can derive from this class.</span></span>  
  
```csharp
public abstract class InterceptingElement : BindingElementExtensionElement
{
    //...
}
```  
  
## <a name="adding-policy"></a><span data-ttu-id="3fc78-134">ポリシーの追加</span><span class="sxs-lookup"><span data-stu-id="3fc78-134">Adding Policy</span></span>  
 <span data-ttu-id="3fc78-135">ポリシー システムと統合するには、`InterceptingBindingElement` に IPolicyExportExtension を実装し、ポリシーの生成に参加する必要があることを通知します。</span><span class="sxs-lookup"><span data-stu-id="3fc78-135">To integrate with our policy system, `InterceptingBindingElement` implements IPolicyExportExtension to signal that we should participate in generating policy.</span></span> <span data-ttu-id="3fc78-136">生成されたクライアント上でポリシーのインポートをサポートするには、`InterceptingBindingElementImporter` の派生クラスを登録し、`CreateMessageInterceptor`() をオーバーライドして、ポリシーが有効なそれらの `ChannelMessageInterceptor` クラスを生成します。</span><span class="sxs-lookup"><span data-stu-id="3fc78-136">To support importing policy on a generated client, the user can register a derived class of `InterceptingBindingElementImporter` and override `CreateMessageInterceptor`() to generate their policy-enabled `ChannelMessageInterceptor` class.</span></span>  
  
## <a name="example-droppable-message-inspector"></a><span data-ttu-id="3fc78-137">例: 破棄可能なメッセージ インスペクタ</span><span class="sxs-lookup"><span data-stu-id="3fc78-137">Example: Droppable Message Inspector</span></span>  
 <span data-ttu-id="3fc78-138">このサンプルには、メッセージを破棄する `ChannelMessageInspector` の実装例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3fc78-138">Included in the sample is an example implementation of `ChannelMessageInspector` which drops messages.</span></span>  
  
```csharp
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 <span data-ttu-id="3fc78-139">この例には、次のように構成からアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="3fc78-139">You can access it from configuration as follows:</span></span>  
  
```xml  
<configuration>  
    ...  
    <system.serviceModel>  
        ...  
        <extensions>  
            <bindingElementExtensions>  
                <add name="droppingInterceptor"
                   type=  
          "Microsoft.ServiceModel.Samples.DroppingServerElement, library"/>  
            </bindingElementExtensions>  
        </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="3fc78-140">クライアントとサーバーでは、両方ともこの新しく作成された構成セクションを使用して、カスタム ファクトリをランタイム チャネル スタックの最低レベル (トランスポート レベルの上) に挿入します。</span><span class="sxs-lookup"><span data-stu-id="3fc78-140">The client and server both use this newly created configuration section to insert the custom factories into the lowest-level of their run-time channel stacks (above the transport level).</span></span>  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="3fc78-141">クライアントでは `MessageInterceptor` ライブラリを使用して、カスタム ヘッダーを偶数番号付きメッセージに追加します。</span><span class="sxs-lookup"><span data-stu-id="3fc78-141">The client uses the `MessageInterceptor` library to add a custom header to even numbered messages.</span></span> <span data-ttu-id="3fc78-142">一方、サービスでは `MessageInterceptor` ライブラリを使用して、この特殊なヘッダーを持たないメッセージを削除します。</span><span class="sxs-lookup"><span data-stu-id="3fc78-142">The service on the other hand uses `MessageInterceptor` library to drop any messages that do not have this special header.</span></span>  
  
 <span data-ttu-id="3fc78-143">サービスを実行し、次にクライアントを実行すると、次のクライアント出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3fc78-143">You should see the following client output after running the service and then the client.</span></span>  
  
```console  
Reporting the next 10 wind speed  
100 kph  
Server dropped a message.  
90 kph  
80 kph  
Server dropped a message.  
70 kph  
60 kph  
Server dropped a message.  
50 kph  
40 kph  
Server dropped a message.  
30 kph  
20 kph  
Server dropped a message.  
10 kph  
Press ENTER to shut down client  
```  
  
 <span data-ttu-id="3fc78-144">クライアントからは 10 種類の異なる風速がサービスに報告されますが、特殊なヘッダーがあるのはそれらのタグの半分だけです。</span><span class="sxs-lookup"><span data-stu-id="3fc78-144">The client reports 10 different wind speeds to the service, but only tags half of them with the special header.</span></span>  
  
 <span data-ttu-id="3fc78-145">サービスには、次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3fc78-145">On the service, you should see the following output:</span></span>  
  
```console  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3fc78-146">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="3fc78-146">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3fc78-147">次のコマンドを使用して、ASP.NET 4.0 をインストールします。</span><span class="sxs-lookup"><span data-stu-id="3fc78-147">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="3fc78-148">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="3fc78-148">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="3fc78-149">ソリューションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="3fc78-149">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="3fc78-150">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="3fc78-150">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="3fc78-151">最初に Service.exe を実行して次に Client.exe を実行し、両方のコンソール ウィンドウで出力を表示します。</span><span class="sxs-lookup"><span data-stu-id="3fc78-151">Run Service.exe first then run Client.exe and watch both console windows for output.</span></span>  
