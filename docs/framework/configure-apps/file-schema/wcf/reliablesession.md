---
title: <reliableSession>
ms.date: 03/30/2017
ms.assetid: 129b4a59-37f0-4030-b664-03795d257d29
ms.openlocfilehash: 95f6646041dc2dd7bae7691a0a9f748c844f50b6
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738754"
---
# <a name="reliablesession"></a><span data-ttu-id="884f3-101">\<reliableSession ></span><span class="sxs-lookup"><span data-stu-id="884f3-101">\<reliableSession></span></span>
<span data-ttu-id="884f3-102">WS-ReliableMessaging の設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="884f3-102">Defines setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="884f3-103">この要素がカスタム バインディングに追加される場合、その結果となるチャネルにより、正確に 1 回の配信保証をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="884f3-103">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span>  
  
<span data-ttu-id="884f3-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="884f3-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="884f3-105">&nbsp; &nbsp;[ **\<system >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="884f3-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="884f3-106">&nbsp;&nbsp;&nbsp;&nbsp;\<[**バインド**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="884f3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="884f3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="884f3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="884f3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**バインド >** </span><span class="sxs-lookup"><span data-stu-id="884f3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="884f3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**reliableSession >**</span><span class="sxs-lookup"><span data-stu-id="884f3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<reliableSession>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="884f3-110">構文</span><span class="sxs-lookup"><span data-stu-id="884f3-110">Syntax</span></span>  
  
```xml  
<reliableSession acknowledgementInterval="TimeSpan"
                 flowControlEnabled="Boolean"
                 inactivityTimeout="TimeSpan"
                 maxPendingChannels="Integer"
                 maxRetryCount="Integer"
                 maxTransferWindowSize="Integer"
                 reliableMessagingVersion="Default/WSReliableMessagingFebruary2005/WSReliableMessaging11"
                 ordered="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="884f3-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="884f3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="884f3-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="884f3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="884f3-113">属性</span><span class="sxs-lookup"><span data-stu-id="884f3-113">Attributes</span></span>  
  
|<span data-ttu-id="884f3-114">属性</span><span class="sxs-lookup"><span data-stu-id="884f3-114">Attribute</span></span>|<span data-ttu-id="884f3-115">説明</span><span class="sxs-lookup"><span data-stu-id="884f3-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="884f3-116">acknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="884f3-116">acknowledgementInterval</span></span>|<span data-ttu-id="884f3-117">そのポイントまで受信したメッセージの受信確認の送信をチャネルが待機する最大時間間隔を含む <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="884f3-117">A <xref:System.TimeSpan> that contains the maximum time interval the channel is going to wait to send an acknowledgment for messages received up to that point.</span></span> <span data-ttu-id="884f3-118">既定値は 00:00:0.2 です。</span><span class="sxs-lookup"><span data-stu-id="884f3-118">The default is 00:00:0.2.</span></span>|  
|<span data-ttu-id="884f3-119">flowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="884f3-119">flowControlEnabled</span></span>|<span data-ttu-id="884f3-120">高度なフロー制御を有効にするかどうかを示すブール値。WS-ReliableMessaging のフロー制御の Microsoft 固有の実装です。</span><span class="sxs-lookup"><span data-stu-id="884f3-120">A Boolean value that indicates whether advanced flow control, a Microsoft-specific implementation of flow control for WS-Reliable messaging, is activated.</span></span> <span data-ttu-id="884f3-121">既定値は、 `true`です。</span><span class="sxs-lookup"><span data-stu-id="884f3-121">The default is `true`.</span></span>|  
|<span data-ttu-id="884f3-122">inactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="884f3-122">inactivityTimeout</span></span>|<span data-ttu-id="884f3-123">他の通信相手がチャネルにメッセージを送信せずにいられる最長期間を指定する <xref:System.TimeSpan>。他の通信相手がメッセージを送信しない期間がこの値を超えると、チャネルでエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="884f3-123">A <xref:System.TimeSpan> that specifies the maximum duration that the channel is going to allow the other communication party not to send any messages, before faulting the channel.</span></span> <span data-ttu-id="884f3-124">既定値は 00:10:00 です。</span><span class="sxs-lookup"><span data-stu-id="884f3-124">The default is 00:10:00.</span></span><br /><br /> <span data-ttu-id="884f3-125">チャネルでのアクティビティは、アプリケーションまたはインフラストラクチャのメッセージを受信するように定義されています。</span><span class="sxs-lookup"><span data-stu-id="884f3-125">Activity on a channel is defined as receiving an application or infrastructure messages.</span></span> <span data-ttu-id="884f3-126">このプロパティは、アクティブでないセッションを維持する最長期間を制御します。</span><span class="sxs-lookup"><span data-stu-id="884f3-126">This property controls the maximum amount of time to keep an inactive session alive.</span></span> <span data-ttu-id="884f3-127">反応のない時間がこれより長く経過すると、インフラストラクチャによってセッションは中止され、チャネルはエラーとなります。</span><span class="sxs-lookup"><span data-stu-id="884f3-127">If longer time passes with no activity, the session is aborted by the infrastructure and the channel faults.</span></span> <span data-ttu-id="884f3-128">**注:** アプリケーションが定期的にメッセージを送信して接続を維持する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="884f3-128">**Note:**  It is not necessary for the application to periodically send messages to keep the connection alive.</span></span>|  
|<span data-ttu-id="884f3-129">maxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="884f3-129">maxPendingChannels</span></span>|<span data-ttu-id="884f3-130">受け入れるリスナーを待機できるチャネルの最大数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="884f3-130">An integer that specifies the maximum number of channels that can wait on the listener to be accepted.</span></span> <span data-ttu-id="884f3-131">この値は、1 ～ 16384 (1 と 16384を含む) のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="884f3-131">This value should be between 1 to 16384 inclusive.</span></span> <span data-ttu-id="884f3-132">既定値は 4 です。</span><span class="sxs-lookup"><span data-stu-id="884f3-132">The default is 4.</span></span><br /><br /> <span data-ttu-id="884f3-133">チャネルは、受け入れを待っている間は保留状態になります。</span><span class="sxs-lookup"><span data-stu-id="884f3-133">Channels are pending when they are waiting to be accepted.</span></span> <span data-ttu-id="884f3-134">制限に達すると、チャネルは作成されなくなります。</span><span class="sxs-lookup"><span data-stu-id="884f3-134">Once that limit is reached, no channels are created.</span></span> <span data-ttu-id="884f3-135">正確には、この数が (保留状態のチャネルの受け入れによって) 減少するまで、保留モードにされます。</span><span class="sxs-lookup"><span data-stu-id="884f3-135">Rather, they are put in pending mode until this number goes down (by accepting pending channels).</span></span> <span data-ttu-id="884f3-136">これはファクトリごとの制限です。</span><span class="sxs-lookup"><span data-stu-id="884f3-136">This is a per-factory limit.</span></span><br /><br /> <span data-ttu-id="884f3-137">しきい値に達した後に、リモート アプリケーションが新しい信頼できるセッションを確立しようとした場合、要求は拒否され、この原因となる open 操作でエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="884f3-137">When the threshold is reached and a remote application tries to establish a new reliable session, the request is denied and the open operation that prompted this faults.</span></span> <span data-ttu-id="884f3-138">この制限は、保留状態の送信チャネルの数には適用されません。</span><span class="sxs-lookup"><span data-stu-id="884f3-138">This limit does not apply to the number of pending outgoing channels.</span></span>|  
|<span data-ttu-id="884f3-139">maxRetryCount</span><span class="sxs-lookup"><span data-stu-id="884f3-139">maxRetryCount</span></span>|<span data-ttu-id="884f3-140">基になるチャネルで Send を呼び出すことで、信頼できるチャネルが受信確認を受信していないメッセージの再転送を試みる最大回数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="884f3-140">An integer that specifies the maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgment for, by calling Send on its underlying channel.</span></span><br /><br /> <span data-ttu-id="884f3-141">この値は、ゼロより大きい値である必要があります。</span><span class="sxs-lookup"><span data-stu-id="884f3-141">This value should be greater than zero.</span></span> <span data-ttu-id="884f3-142">既定値は 8 です。</span><span class="sxs-lookup"><span data-stu-id="884f3-142">The default is 8.</span></span><br /><br /> <span data-ttu-id="884f3-143">この値は、0 を超えた整数にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="884f3-143">This value should be an integer greater than zero.</span></span> <span data-ttu-id="884f3-144">最後の再転送後に受信確認が受信されない場合、チャネルでエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="884f3-144">If an acknowledgment is not received after the last retransmission, the channel faults.</span></span><br /><br /> <span data-ttu-id="884f3-145">メッセージは、受信側でその配信が確認されている場合、転送されたと見なされます。</span><span class="sxs-lookup"><span data-stu-id="884f3-145">A message is considered to be transferred if its delivery at the recipient has been acknowledged by the recipient.</span></span><br /><br /> <span data-ttu-id="884f3-146">転送済みのメッセージの受信確認が一定時間内に受信されない場合、インフラストラクチャは、自動的にそのメッセージを再転送します。</span><span class="sxs-lookup"><span data-stu-id="884f3-146">If an acknowledgment has not been received within a certain amount of time for a message that has been transmitted, the infrastructure automatically retransmits the message.</span></span> <span data-ttu-id="884f3-147">インフラストラクチャは、このプロパティで指定された回数まで、メッセージを再送信しようとします。</span><span class="sxs-lookup"><span data-stu-id="884f3-147">The infrastructure tries to resend the message for at most the number of times specified by this property.</span></span> <span data-ttu-id="884f3-148">最後の再転送後に受信確認が受信されない場合、チャネルでエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="884f3-148">If an acknowledgment is not received after the last retransmission, the channel faults.</span></span><br /><br /> <span data-ttu-id="884f3-149">インフラストラクチャは、指数バックオフ アルゴリズムを使用し、計算された平均ラウンドトリップ時間に基づいて、いつ再転送するかを判断します。</span><span class="sxs-lookup"><span data-stu-id="884f3-149">The infrastructure uses an exponential back-off algorithm to determine when to retransmit, based on a computed average round-trip time.</span></span> <span data-ttu-id="884f3-150">時間は、まず再転送の 1 秒前に開始され、試行ごとに遅延が 2 倍にされます。この結果、最初の転送試行から最後の再転送試行までに約 8.5 分かかります。</span><span class="sxs-lookup"><span data-stu-id="884f3-150">The time initially starts at 1 second before retransmission and doubling the delay with every attempt, which results in approximately 8.5 minutes passing between the first transmission attempt and the last retransmission attempt.</span></span> <span data-ttu-id="884f3-151">最初の再転送試行のタイミングは、計算されたラウンドトリップ時間に従って調整されるので、試行にかかる時間延長はさまざまです。</span><span class="sxs-lookup"><span data-stu-id="884f3-151">The time for the first retransmission attempt is adjusted according to the calculated round-trip time and the resulting stretch of time that those attempts take varies accordingly.</span></span> <span data-ttu-id="884f3-152">これにより、再転送のタイミングをさまざまなネットワーク条件に動的に適用できます。</span><span class="sxs-lookup"><span data-stu-id="884f3-152">This allows the retransmission time to dynamically adapt to varying network conditions.</span></span>|  
|<span data-ttu-id="884f3-153">maxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="884f3-153">maxTransferWindowSize</span></span>|<span data-ttu-id="884f3-154">バッファーの最大サイズを指定する整数。</span><span class="sxs-lookup"><span data-stu-id="884f3-154">An integer that specifies the maximum size of the buffer.</span></span> <span data-ttu-id="884f3-155">有効値は 1 ～ 4096 の範囲です。</span><span class="sxs-lookup"><span data-stu-id="884f3-155">Valid values are from 1 to 4096 inclusive.</span></span><br /><br /> <span data-ttu-id="884f3-156">クライアントでは、この属性は、まだ受信側で受信が確認されていないメッセージを保持するために信頼できるチャネルが使用するバッファーの最大サイズを定義します。</span><span class="sxs-lookup"><span data-stu-id="884f3-156">On the client, this attribute defines the maximum size of the buffer used by a reliable channel to hold messages not yet acknowledged by the receiver.</span></span> <span data-ttu-id="884f3-157">クォータの単位はメッセージです。</span><span class="sxs-lookup"><span data-stu-id="884f3-157">The unit of the quota is a message.</span></span> <span data-ttu-id="884f3-158">バッファーがいっぱいになると、それ以降の SEND 操作がブロックされます。</span><span class="sxs-lookup"><span data-stu-id="884f3-158">If the buffer is full, further SEND operations are blocked.</span></span><br /><br /> <span data-ttu-id="884f3-159">受信側では、この属性は、まだアプリケーションにディスパッチされていない受信メッセージを格納するためにチャネルが使用するバッファーの最大サイズを定義します。</span><span class="sxs-lookup"><span data-stu-id="884f3-159">On the receiver, this attribute defines the maximum size of the buffer used by the channel to store incoming messages not yet dispatched to the application.</span></span> <span data-ttu-id="884f3-160">バッファーがいっぱいになると、それ以降のメッセージは、受信側によって通知なしに自動的に削除されるので、クライアントによる再転送が必要になります。</span><span class="sxs-lookup"><span data-stu-id="884f3-160">If the buffer is full, further messages are silently dropped by the receiver and require retransmission by the client.</span></span>|  
|<span data-ttu-id="884f3-161">ordered</span><span class="sxs-lookup"><span data-stu-id="884f3-161">ordered</span></span>|<span data-ttu-id="884f3-162">メッセージが送信された順序で到着されることを保証するかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="884f3-162">A Boolean that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span> <span data-ttu-id="884f3-163">この設定が `false` の場合、メッセージは送信された順序で到着しません。</span><span class="sxs-lookup"><span data-stu-id="884f3-163">If this setting is `false`, messages can arrive out of order.</span></span> <span data-ttu-id="884f3-164">既定値は、 `true`です。</span><span class="sxs-lookup"><span data-stu-id="884f3-164">The default is `true`.</span></span>|  
|<span data-ttu-id="884f3-165">reliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="884f3-165">reliableMessagingVersion</span></span>|<span data-ttu-id="884f3-166">使用する WS-ReliableMessaging バージョンを指定する <xref:System.ServiceModel.ReliableMessagingVersion> の有効な値。</span><span class="sxs-lookup"><span data-stu-id="884f3-166">A valid value from <xref:System.ServiceModel.ReliableMessagingVersion> that specifies the WS-ReliableMessaging version to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="884f3-167">子要素</span><span class="sxs-lookup"><span data-stu-id="884f3-167">Child Elements</span></span>  
 <span data-ttu-id="884f3-168">None</span><span class="sxs-lookup"><span data-stu-id="884f3-168">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="884f3-169">親要素</span><span class="sxs-lookup"><span data-stu-id="884f3-169">Parent Elements</span></span>  
  
|<span data-ttu-id="884f3-170">要素</span><span class="sxs-lookup"><span data-stu-id="884f3-170">Element</span></span>|<span data-ttu-id="884f3-171">説明</span><span class="sxs-lookup"><span data-stu-id="884f3-171">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="884f3-172">\<binding ></span><span class="sxs-lookup"><span data-stu-id="884f3-172">\<binding></span></span>](bindings.md)|<span data-ttu-id="884f3-173">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="884f3-173">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="884f3-174">Remarks</span><span class="sxs-lookup"><span data-stu-id="884f3-174">Remarks</span></span>  
 <span data-ttu-id="884f3-175">信頼できるセッションは、信頼できるメッセージとセッションに関する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="884f3-175">Reliable sessions provide features for reliable messaging and sessions.</span></span> <span data-ttu-id="884f3-176">信頼できるメッセージは、エラー時に通信を再試行するほか、メッセージの順次到着などの配信の保証を指定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="884f3-176">Reliable messaging retries communication on failure and allows delivery assurances such as in-order arrival of messages to be specified.</span></span> <span data-ttu-id="884f3-177">セッションでは、呼び出し間でクライアントの状態が保持されます。</span><span class="sxs-lookup"><span data-stu-id="884f3-177">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="884f3-178">この要素には、オプションとして、順序付けされたメッセージ配信を行う機能も用意されています。</span><span class="sxs-lookup"><span data-stu-id="884f3-178">This element also optionally provides ordered message delivery.</span></span> <span data-ttu-id="884f3-179">この実装されたセッションは、SOAP およびトランスポート中継局を通過できます。</span><span class="sxs-lookup"><span data-stu-id="884f3-179">This implemented session can cross SOAP and transport intermediaries.</span></span>  
  
 <span data-ttu-id="884f3-180">各バインド要素は、メッセージの送信または受信時の処理手順を表します。</span><span class="sxs-lookup"><span data-stu-id="884f3-180">Each binding element represents a processing step when sending or receiving messages.</span></span> <span data-ttu-id="884f3-181">実行時に、バインド要素は、メッセージの送受信に求められる送信および受信チャネル スタックを作成するために必要なチャネル ファクトリとリスナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="884f3-181">At runtime, binding elements create the channel factories and listeners that are necessary to build outgoing and incoming channel stacks required to send and receive messages.</span></span> <span data-ttu-id="884f3-182">`reliableSession` が提供するスタック内のオプションの層は、エンドポイント間に信頼できるセッションを確立し、このセッションの動作を構成することができます。</span><span class="sxs-lookup"><span data-stu-id="884f3-182">The `reliableSession` provides an optional layer in the stack that can establish a reliable session between endpoints and configure the behavior of this session.</span></span>  
  
 <span data-ttu-id="884f3-183">詳細については、「[信頼できるセッション](../../../wcf/feature-details/reliable-sessions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="884f3-183">For more information, see [Reliable Sessions](../../../wcf/feature-details/reliable-sessions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="884f3-184">例</span><span class="sxs-lookup"><span data-stu-id="884f3-184">Example</span></span>  
 <span data-ttu-id="884f3-185">次の例では、さまざまなトランスポートとメッセージ エンコーディング要素を使用し、特に、クライアントの状態を保持し、配信順序を保証することを指定する、信頼できるセッションを有効化することによって、カスタム バインドを構成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="884f3-185">The following example demonstrates how to configure a custom binding with various transport and message encoding elements, especially enabling reliable sessions, which maintains client state and specifies in-order delivery assurances.</span></span> <span data-ttu-id="884f3-186">この機能は、クライアントとサービスのアプリケーション構成ファイルで構成されます。</span><span class="sxs-lookup"><span data-stu-id="884f3-186">This feature is configured in the application configuration files for the client and service.</span></span> <span data-ttu-id="884f3-187">サービスの構成の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="884f3-187">The example show the service configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc -->
        <!-- specify customBinding binding and a binding configuration to use -->
        <endpoint address=""
                  binding="customBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <!-- custom binding configuration - configures HTTP transport, reliable sessions -->
    <bindings>
      <customBinding>
        <binding name="Binding1">
          <reliableSession />
          <security authenticationMode="SecureConversation"
                    requireSecurityContextCancellation="true">
          </security>
          <compositeDuplex />
          <oneWay />
          <textMessageEncoding messageVersion="Soap12WSAddressing10"
                               writeEncoding="utf-8" />
          <httpTransport authenticationScheme="Anonymous"
                         bypassProxyOnLocal="false"
                         hostNameComparisonMode="StrongWildcard"
                         proxyAuthenticationScheme="Anonymous"
                         realm=""
                         useDefaultWebProxy="true" />
        </binding>
      </customBinding>
    </bindings>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="884f3-188">関連項目</span><span class="sxs-lookup"><span data-stu-id="884f3-188">See also</span></span>

- <xref:System.ServiceModel.Configuration.ReliableSessionElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
- [<span data-ttu-id="884f3-189">信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="884f3-189">Reliable Sessions</span></span>](../../../wcf/feature-details/reliable-sessions.md)
- [<span data-ttu-id="884f3-190">バインディング</span><span class="sxs-lookup"><span data-stu-id="884f3-190">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="884f3-191">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="884f3-191">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="884f3-192">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="884f3-192">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="884f3-193">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="884f3-193">\<customBinding></span></span>](custombinding.md)
