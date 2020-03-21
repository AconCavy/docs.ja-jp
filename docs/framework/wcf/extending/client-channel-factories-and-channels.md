---
title: 'クライアント : チャネル ファクトリとチャネル'
ms.date: 03/30/2017
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
ms.openlocfilehash: 25e2c034d1fefc7728667231040a97c3aeecabbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185691"
---
# <a name="client-channel-factories-and-channels"></a><span data-ttu-id="690ce-102">クライアント : チャネル ファクトリとチャネル</span><span class="sxs-lookup"><span data-stu-id="690ce-102">Client: Channel Factories and Channels</span></span>
<span data-ttu-id="690ce-103">ここでは、チャネル ファクトリとチャネルの作成について説明します。</span><span class="sxs-lookup"><span data-stu-id="690ce-103">This topic discusses the creation of channel factories and channels.</span></span>  
  
## <a name="channel-factories-and-channels"></a><span data-ttu-id="690ce-104">チャネル ファクトリとチャネル</span><span class="sxs-lookup"><span data-stu-id="690ce-104">Channel Factories and Channels</span></span>  
 <span data-ttu-id="690ce-105">チャネル ファクトリには、チャネルを作成する役割があります。</span><span class="sxs-lookup"><span data-stu-id="690ce-105">Channel factories are responsible for creating channels.</span></span> <span data-ttu-id="690ce-106">チャネル ファクトリによって作成されるチャネルは、メッセージの送信に使用されます。</span><span class="sxs-lookup"><span data-stu-id="690ce-106">Channels created by channel factories are used for sending messages.</span></span> <span data-ttu-id="690ce-107">このチャネルは、上の層からメッセージを取得し、必要な処理を実行し、そのメッセージを下の層に送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="690ce-107">These channels are responsible for getting the message from the layer above, performing whatever processing is necessary, then sending the message to the layer below.</span></span> <span data-ttu-id="690ce-108">このプロセスを説明する図を次に示します。</span><span class="sxs-lookup"><span data-stu-id="690ce-108">The following graphic illustrates this process.</span></span>  
  
 <span data-ttu-id="690ce-109">![クライアント ファクトリおよびチャネル](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span><span class="sxs-lookup"><span data-stu-id="690ce-109">![Client Factories and Channels](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span></span>  
<span data-ttu-id="690ce-110">チャネル ファクトリがチャネルを作成します。</span><span class="sxs-lookup"><span data-stu-id="690ce-110">A channel factory creates channels.</span></span>  
  
 <span data-ttu-id="690ce-111">終了時に、チャネル ファクトリは、作成したチャネルのうちまだ閉じていないチャネルを閉じる必要があります。</span><span class="sxs-lookup"><span data-stu-id="690ce-111">When closed, channel factories are responsible for closing any channels they created that are not yet closed.</span></span> <span data-ttu-id="690ce-112">チャネル リスナーを閉じたとき、新しいチャネルの受け入れだけが停止され、既存のチャネルは開いたままで、メッセージの受信を続行できるので、ここに示すモデルは非対称です。</span><span class="sxs-lookup"><span data-stu-id="690ce-112">Note that the model is asymmetric here because when a channel listener is closed, it only stops accepting new channels but leaves existing channels open so that they can continue receiving messages.</span></span>  
  
 <span data-ttu-id="690ce-113">WCF では、このプロセスの基本クラス ヘルパーを提供します。</span><span class="sxs-lookup"><span data-stu-id="690ce-113">WCF provides base class helpers for this process.</span></span> <span data-ttu-id="690ce-114">(このトピックで説明するチャネル ヘルパー クラスの図については、「[チャネル モデルの概要](channel-model-overview.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="690ce-114">(For a diagram of the channel helper classes discussed in this topic, see [Channel Model Overview](channel-model-overview.md).)</span></span>  
  
- <span data-ttu-id="690ce-115">この<xref:System.ServiceModel.Channels.CommunicationObject>クラスは、「<xref:System.ServiceModel.ICommunicationObject>チャネルの開発」のステップ 2 で説明したステート マシン[を実装し](developing-channels.md)、適用します。</span><span class="sxs-lookup"><span data-stu-id="690ce-115">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine described in step 2 of [Developing Channels](developing-channels.md).</span></span>  
  
- <span data-ttu-id="690ce-116"><xref:System.ServiceModel.Channels.ChannelManagerBase> クラスには <xref:System.ServiceModel.Channels.CommunicationObject> が実装され、<xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> と <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType> の統合基本クラスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="690ce-116">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> and <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="690ce-117"><xref:System.ServiceModel.Channels.ChannelManagerBase> クラスは、<xref:System.ServiceModel.Channels.ChannelBase> を実装する基本クラスである <xref:System.ServiceModel.Channels.IChannel> との組み合わせによって動作します。</span><span class="sxs-lookup"><span data-stu-id="690ce-117">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>
  
- <span data-ttu-id="690ce-118">この<xref:System.ServiceModel.Channels.ChannelFactoryBase>クラスは`CreateChannel`、<xref:System.ServiceModel.Channels.ChannelManagerBase>オーバーロード<xref:System.ServiceModel.Channels.IChannelFactory>を実装し、1 つの`OnCreateChannel`抽象メソッドに統合します。</span><span class="sxs-lookup"><span data-stu-id="690ce-118">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>
  
- <span data-ttu-id="690ce-119"><xref:System.ServiceModel.Channels.ChannelListenerBase> クラスは、<xref:System.ServiceModel.Channels.IChannelListener> を実装しています。</span><span class="sxs-lookup"><span data-stu-id="690ce-119">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="690ce-120">基本状態管理を行います。</span><span class="sxs-lookup"><span data-stu-id="690ce-120">It takes care of basic state management.</span></span>
  
 <span data-ttu-id="690ce-121">次の説明は[、トランスポート: UDP](../samples/transport-udp.md)サンプルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="690ce-121">The following discussion is based upon the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
### <a name="creating-a-channel-factory"></a><span data-ttu-id="690ce-122">チャネル ファクトリの作成</span><span class="sxs-lookup"><span data-stu-id="690ce-122">Creating a Channel Factory</span></span>  
 <span data-ttu-id="690ce-123">`UdpChannelFactory` は <xref:System.ServiceModel.Channels.ChannelFactoryBase> から派生します。</span><span class="sxs-lookup"><span data-stu-id="690ce-123">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="690ce-124">サンプルでは、<xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> をオーバーライドして、メッセージ エンコーダーのメッセージ バージョンにアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="690ce-124">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="690ce-125">さらに、<xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> をオーバーライドして、ステート マシンの移行時に <xref:System.ServiceModel.Channels.BufferManager> のインスタンスを破棄します。</span><span class="sxs-lookup"><span data-stu-id="690ce-125">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> to tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="690ce-126">UDP 出力チャネル</span><span class="sxs-lookup"><span data-stu-id="690ce-126">The UDP Output Channel</span></span>  
 <span data-ttu-id="690ce-127">`UdpOutputChannel` では、<xref:System.ServiceModel.Channels.IOutputChannel> が実装されます。</span><span class="sxs-lookup"><span data-stu-id="690ce-127">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="690ce-128">このコンストラクターは、引数を検証し、渡される <xref:System.Net.EndPoint> に基づいて出力先の <xref:System.ServiceModel.EndpointAddress> オブジェクトを構築します。</span><span class="sxs-lookup"><span data-stu-id="690ce-128">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
 <span data-ttu-id="690ce-129"><xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> のオーバーライドによって、この <xref:System.Net.EndPoint> にメッセージを送信するために使用されるソケットが作成されます。</span><span class="sxs-lookup"><span data-stu-id="690ce-129">The override of <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> creates a socket that is used to send messages to this <xref:System.Net.EndPoint>.</span></span>  
  
 ```csharp
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 <span data-ttu-id="690ce-130">チャネルが閉じる際には、正常終了することも異常終了することもあります。</span><span class="sxs-lookup"><span data-stu-id="690ce-130">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="690ce-131">チャネルが正常に閉じた場合はソケットも終了し、基本クラスの `OnClose` メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="690ce-131">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="690ce-132">このときに例外がスローされると、インフラストラクチャによって `Abort` が呼び出され、チャネルがクリーンアップされます。</span><span class="sxs-lookup"><span data-stu-id="690ce-132">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 <span data-ttu-id="690ce-133">と`Send()``BeginSend()`/`EndSend()`を実装します。</span><span class="sxs-lookup"><span data-stu-id="690ce-133">Implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="690ce-134">この実装は、2 つの主要セクションに分かれます。</span><span class="sxs-lookup"><span data-stu-id="690ce-134">This breaks down into two main sections.</span></span> <span data-ttu-id="690ce-135">最初に、メッセージを次のようにシリアル化してバイト配列で表します。</span><span class="sxs-lookup"><span data-stu-id="690ce-135">First serialize the message into a byte array:</span></span>  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="690ce-136">次に、結果として生成されたデータを次のようにネットワークに送信します。</span><span class="sxs-lookup"><span data-stu-id="690ce-136">Then send the resulting data on the wire:</span></span>  
  
```csharp  
this.socket.SendTo(  
  messageBuffer.Array,
  messageBuffer.Offset,
  messageBuffer.Count,
  SocketFlags.None,
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a><span data-ttu-id="690ce-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="690ce-137">See also</span></span>

- [<span data-ttu-id="690ce-138">チャネルの開発</span><span class="sxs-lookup"><span data-stu-id="690ce-138">Developing Channels</span></span>](developing-channels.md)
