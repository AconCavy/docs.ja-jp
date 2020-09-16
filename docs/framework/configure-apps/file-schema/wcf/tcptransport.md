---
title: <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 8fcd18c1-9958-42e7-b442-7903f7bdb563
ms.openlocfilehash: 987dcad5e239b35f5ff367ab668d40526593f970
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556461"
---
# \<tcpTransport>
<span data-ttu-id="a89e3-101">カスタム バインドのメッセージを転送するためにチャネルで使用できる TCP トランスポートを定義します。</span><span class="sxs-lookup"><span data-stu-id="a89e3-101">Defines a TCP transport that can be used by a channel to transfers messages for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tcpTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="a89e3-102">構文</span><span class="sxs-lookup"><span data-stu-id="a89e3-102">Syntax</span></span>  
  
```xml  
<tcpTransport channelInitializationTimeout="TimeSpan"
              connectionBufferSize="Integer"
              hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
              listenBacklog="Integer"
              manualAddressing="Boolean"
              maxBufferPoolSize="Integer"
              maxBufferSize="Integer"
              maxOutputDelay="TimeSpan"
              maxPendingAccepts="Integer"
              maxPendingConnections="Integer"
              maxReceivedMessageSize="Integer"
              portSharingEnabled="Boolean"
              teredoEnabled="Boolean"
              transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse" >
  <connectionPoolSettings groupName="String"
                          idleTimeout="TimeSpan"
                          leaseTimeout="TimeSpan"
                          maxOutboundConnectionsPerEndpoint="Integer" />
</tcpTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a89e3-103">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a89e3-103">Attributes and Elements</span></span>  
 <span data-ttu-id="a89e3-104">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a89e3-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a89e3-105">属性</span><span class="sxs-lookup"><span data-stu-id="a89e3-105">Attributes</span></span>  
  
|<span data-ttu-id="a89e3-106">属性</span><span class="sxs-lookup"><span data-stu-id="a89e3-106">Attribute</span></span>|<span data-ttu-id="a89e3-107">説明</span><span class="sxs-lookup"><span data-stu-id="a89e3-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a89e3-108">channelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="a89e3-108">channelInitializationTimeout</span></span>|<span data-ttu-id="a89e3-109">チャネルの初期化に対して許容される時間制限を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="a89e3-109">Gets or sets the time limit for initializing a channel to be accepted.</span></span>  <span data-ttu-id="a89e3-110">接続が切断されるまでのチャネルの初期化ステータスの最大時間 (秒単位)。</span><span class="sxs-lookup"><span data-stu-id="a89e3-110">The maximum time a channel can be in the initialization state before being disconnected in seconds.</span></span> <span data-ttu-id="a89e3-111">このクォータには、TCP 接続が .NET メッセージフレーミングプロトコルを使用して自身を認証するのにかかる時間が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a89e3-111">This quota includes the time a TCP connection can take to authenticate itself using the .NET Message Framing protocol.</span></span> <span data-ttu-id="a89e3-112">クライアントは、サーバーが認証を実行するための十分な情報を得る前に初期データを送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a89e3-112">A client needs to send some initial data before the server has enough information to perform authentication.</span></span> <span data-ttu-id="a89e3-113">既定値は 30 秒です。</span><span class="sxs-lookup"><span data-stu-id="a89e3-113">The default is 30 seconds.</span></span>|  
|<span data-ttu-id="a89e3-114">connectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="a89e3-114">connectionBufferSize</span></span>|<span data-ttu-id="a89e3-115">クライアントまたサービスからネットワークでシリアル化されたメッセージのチャンクを転送するために使用されるバッファーのサイズを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="a89e3-115">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="a89e3-116">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="a89e3-116">hostNameComparisonMode</span></span>|<span data-ttu-id="a89e3-117">URI で一致する場合にサービスに到達するためにホスト名を使用するかどうかを示す値を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="a89e3-117">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="a89e3-118">listenBacklog</span><span class="sxs-lookup"><span data-stu-id="a89e3-118">listenBacklog</span></span>|<span data-ttu-id="a89e3-119">Web サービスの保留可能なキュー内の接続要求の最大数。</span><span class="sxs-lookup"><span data-stu-id="a89e3-119">The maximum number of queued connection requests that can be pending for a Web service.</span></span> <span data-ttu-id="a89e3-120">`connectionLeaseTimeout` 属性は、クライアントが接続されるのを待つ時間を制限します。この時間が経過すると接続の例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="a89e3-120">The `connectionLeaseTimeout` attribute limits the duration the client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="a89e3-121">これは、Web サービスに対して保留可能なキュー内の接続要求の最大数を制御するソケット レベルのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="a89e3-121">This is a socket level property which controls the maximum number of queued connection requests that can be pending for a Web service.</span></span> <span data-ttu-id="a89e3-122">ListenBacklog が低すぎると、WCF は要求の受け入れを停止し、既存のキューに置かれた接続の一部がサーバーによって確認されるまで、新しい接続を破棄します。</span><span class="sxs-lookup"><span data-stu-id="a89e3-122">When ListenBacklog is too low, WCF will stop accepting requests and therefore drop new connections until the server acknowledges some of the existing queued connections.</span></span> <span data-ttu-id="a89e3-123">既定値は 16 \* プロセッサの数です。</span><span class="sxs-lookup"><span data-stu-id="a89e3-123">The default is 16 \* number of processors.</span></span>|  
|<span data-ttu-id="a89e3-124">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="a89e3-124">manualAddressing</span></span>|<span data-ttu-id="a89e3-125">メッセージの手動アドレス指定が必要かどうかを示す値を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="a89e3-125">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="a89e3-126">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="a89e3-126">maxBufferPoolSize</span></span>|<span data-ttu-id="a89e3-127">トランスポートが使用するバッファー プールの最大サイズを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="a89e3-127">Gets or sets the maximum size of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="a89e3-128">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="a89e3-128">maxBufferSize</span></span>|<span data-ttu-id="a89e3-129">使用するバッファーの最大サイズを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="a89e3-129">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="a89e3-130">ストリーム メッセージの場合、この値は少なくともメッセージ ヘッダーで使用できる最大サイズにする必要があります。これは、バッファー モードで読み取られます。</span><span class="sxs-lookup"><span data-stu-id="a89e3-130">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="a89e3-131">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="a89e3-131">maxOutputDelay</span></span>|<span data-ttu-id="a89e3-132">メッセージのチャンクまたは完全なメッセージを、送信前にメモリ内のバッファーに残したままにできる最長期間を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="a89e3-132">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="a89e3-133">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="a89e3-133">maxPendingAccepts</span></span>|<span data-ttu-id="a89e3-134">サービスに対する着信接続処理に使用できる保留中の非同期受け入れ操作の最大数を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="a89e3-134">Gets or sets the maximum number of pending asynchronous accept operations that are available for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="a89e3-135">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="a89e3-135">maxPendingConnections</span></span>|<span data-ttu-id="a89e3-136">サービスでディスパッチを待機している最大接続数を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="a89e3-136">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="a89e3-137">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="a89e3-137">maxReceivedMessageSize</span></span>|<span data-ttu-id="a89e3-138">受信できる最大メッセージ サイズを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="a89e3-138">Gets and sets the maximum allowable message size that can be received.</span></span>|  
|<span data-ttu-id="a89e3-139">portSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="a89e3-139">portSharingEnabled</span></span>|<span data-ttu-id="a89e3-140">TCP ポート共有をこの接続で有効にする場合に指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="a89e3-140">A Boolean value that specifies if TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="a89e3-141">これが `false` の場合、各バインディングは独自の排他ポートを使用します。</span><span class="sxs-lookup"><span data-stu-id="a89e3-141">If this is `false`, each binding will use its own exclusive port.</span></span> <span data-ttu-id="a89e3-142">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="a89e3-142">The default is `false`.</span></span><br /><br /> <span data-ttu-id="a89e3-143">この設定は、サービスのみに関連します。</span><span class="sxs-lookup"><span data-stu-id="a89e3-143">This setting is relevant only to services.</span></span> <span data-ttu-id="a89e3-144">クライアントには影響はありません。</span><span class="sxs-lookup"><span data-stu-id="a89e3-144">Clients are not affected.</span></span><br /><br /> <span data-ttu-id="a89e3-145">この設定を使用するには、[スタートアップの種類] を [手動] または [自動] に変更して、Windows Communication Foundation (WCF) の TCP ポート共有サービスを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a89e3-145">Using this setting requires enabling the Windows Communication Foundation (WCF) TCP Port Sharing Service by changing its Startup Type to Manual or Automatic</span></span>|  
|<span data-ttu-id="a89e3-146">teredoEnabled</span><span class="sxs-lookup"><span data-stu-id="a89e3-146">teredoEnabled</span></span>|<span data-ttu-id="a89e3-147">Teredo (ファイアウォールの内側にあるクライアントをアドレス指定するためのテクノロジ) が有効であるかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="a89e3-147">A Boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span> <span data-ttu-id="a89e3-148">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="a89e3-148">The default is `false`.</span></span><br /><br /> <span data-ttu-id="a89e3-149">このプロパティは、基になる TCP ソケットで Tredo を有効にします。</span><span class="sxs-lookup"><span data-stu-id="a89e3-149">This property enables Teredo for the underlying TCP socket.</span></span> <span data-ttu-id="a89e3-150">詳細については、「 [Teredo の概要](/previous-versions/windows/it-pro/windows-xp/bb457011(v=technet.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a89e3-150">For more information, see [Teredo Overview](/previous-versions/windows/it-pro/windows-xp/bb457011(v=technet.10)).</span></span><br /><br /> <span data-ttu-id="a89e3-151">このプロパティは、Windows XP SP2 および Windows Server 2003 でのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="a89e3-151">This property is applicable only on Windows XP SP2 and Windows Server 2003.</span></span> <span data-ttu-id="a89e3-152">Windows Vista には、Teredo 用のコンピューター全体の構成オプションがあるため、Vista を実行する場合、このプロパティは無視されます。</span><span class="sxs-lookup"><span data-stu-id="a89e3-152">Windows Vista has a machine-wide configuration option for Teredo, so when running Vista, this property is ignored.</span></span> <span data-ttu-id="a89e3-153">Teredo の場合、クライアント コンピューターおよびサービス コンピューターの両方に Microsoft IPv6 スタックをインストールし、Teredo 用に正しく設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a89e3-153">Teredo requires that the client and service machines both have the Microsoft IPv6 stack installed and correctly configured for Teredo usage.</span></span>|  
|<span data-ttu-id="a89e3-154">transferMode</span><span class="sxs-lookup"><span data-stu-id="a89e3-154">transferMode</span></span>|<span data-ttu-id="a89e3-155">接続指向のトランスポートでメッセージをバッファーするか、ストリーム配信するかを示す値を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="a89e3-155">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|<span data-ttu-id="a89e3-156">connectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="a89e3-156">connectionPoolSettings</span></span>|<span data-ttu-id="a89e3-157">名前付きパイプ バインディングの追加の接続プール設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="a89e3-157">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a89e3-158">子要素</span><span class="sxs-lookup"><span data-stu-id="a89e3-158">Child Elements</span></span>  
 <span data-ttu-id="a89e3-159">なし</span><span class="sxs-lookup"><span data-stu-id="a89e3-159">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a89e3-160">親要素</span><span class="sxs-lookup"><span data-stu-id="a89e3-160">Parent Elements</span></span>  
  
|<span data-ttu-id="a89e3-161">要素</span><span class="sxs-lookup"><span data-stu-id="a89e3-161">Element</span></span>|<span data-ttu-id="a89e3-162">説明</span><span class="sxs-lookup"><span data-stu-id="a89e3-162">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="a89e3-163">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="a89e3-163">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a89e3-164">Remarks</span><span class="sxs-lookup"><span data-stu-id="a89e3-164">Remarks</span></span>  
 <span data-ttu-id="a89e3-165">このトランスポートは、"net.tcp://hostname:port/path" の形式の URI を使用します。</span><span class="sxs-lookup"><span data-stu-id="a89e3-165">This transport uses URIs of the form "net.tcp://hostname:port/path".</span></span> <span data-ttu-id="a89e3-166">他の URI コンポーネントは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="a89e3-166">Other URI components are optional.</span></span>  
  
 <span data-ttu-id="a89e3-167">`tcpTransport` 要素は、TCP トランスポート プロトコルを実装するカスタム バインディングを作成する場合の開始点となります。</span><span class="sxs-lookup"><span data-stu-id="a89e3-167">The `tcpTransport` element is the starting point for creating a custom binding that implements the TCP transport protocol.</span></span> <span data-ttu-id="a89e3-168">このトランスポートは、WCF 間の通信用に最適化されています。</span><span class="sxs-lookup"><span data-stu-id="a89e3-168">This transport is optimized for WCF-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a89e3-169">関連項目</span><span class="sxs-lookup"><span data-stu-id="a89e3-169">See also</span></span>

- <xref:System.ServiceModel.Configuration.TcpTransportElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="a89e3-170">トランスポート</span><span class="sxs-lookup"><span data-stu-id="a89e3-170">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="a89e3-171">トランスポートの選択</span><span class="sxs-lookup"><span data-stu-id="a89e3-171">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="a89e3-172">バインド</span><span class="sxs-lookup"><span data-stu-id="a89e3-172">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a89e3-173">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="a89e3-173">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a89e3-174">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="a89e3-174">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
