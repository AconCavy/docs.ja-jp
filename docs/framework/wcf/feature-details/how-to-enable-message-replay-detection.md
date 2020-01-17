---
title: '方法 : メッセージ リプレイ検出を有効にする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF security
- replay detection [WCF]
- WCF, custom bindings
- WCF, security
ms.assetid: 8b847e91-69a3-49e1-9e5f-0c455e50d804
ms.openlocfilehash: 450a99fc6604ccb3fa796e8a73e1ddc3e3adff9e
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964654"
---
# <a name="how-to-enable-message-replay-detection"></a><span data-ttu-id="5bb99-102">方法 : メッセージ リプレイ検出を有効にする</span><span class="sxs-lookup"><span data-stu-id="5bb99-102">How to: Enable Message Replay Detection</span></span>
<span data-ttu-id="5bb99-103">リプレイ攻撃は、攻撃者がメッセージのストリームを 2 つのパーティ間でコピーし、そのストリームを他の 1 つ以上のパーティにリプレイすることで発生します。</span><span class="sxs-lookup"><span data-stu-id="5bb99-103">A replay attack occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="5bb99-104">攻撃が止むまで、攻撃対象になったコンピューターはストリームを正当なメッセージとして処理しようとし、その結果、命令が重複するなど、望ましくない状況に陥ります。</span><span class="sxs-lookup"><span data-stu-id="5bb99-104">Unless mitigated, the computers subject to the attack will process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
 <span data-ttu-id="5bb99-105">メッセージ再生の検出の詳細については、「[メッセージ再生の検出](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5bb99-105">For more information about message replay detection, see [Message Replay Detection](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span></span>  
  
 <span data-ttu-id="5bb99-106">次の手順では、Windows Communication Foundation (WCF) を使用して再生検出を制御するために使用できるさまざまなプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5bb99-106">The following procedure demonstrates various properties that you can use to control replay detection using Windows Communication Foundation (WCF).</span></span>  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a><span data-ttu-id="5bb99-107">コードを使用してクライアントでのリプレイ検出を制御するには</span><span class="sxs-lookup"><span data-stu-id="5bb99-107">To control replay detection on the client using code</span></span>  
  
1. <span data-ttu-id="5bb99-108"><xref:System.ServiceModel.Channels.SecurityBindingElement> で使用する <xref:System.ServiceModel.Channels.CustomBinding> を作成します。</span><span class="sxs-lookup"><span data-stu-id="5bb99-108">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> <span data-ttu-id="5bb99-109">詳細については、「[方法: カスタムバインディングを使用してカスタムバインディングを作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5bb99-109">For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="5bb99-110">次の例では、<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> クラスの <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> を使用して作成された <xref:System.ServiceModel.Channels.SecurityBindingElement> を使用します。</span><span class="sxs-lookup"><span data-stu-id="5bb99-110">The following example uses a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> created with the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span>  
  
2. <span data-ttu-id="5bb99-111"><xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> プロパティを使用して <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> クラスへの参照を返し、次のプロパティを適切な値に設定します。</span><span class="sxs-lookup"><span data-stu-id="5bb99-111">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class and set any of the following properties, as appropriate:</span></span>  
  
    1. <span data-ttu-id="5bb99-112">`DetectReplay`.</span><span class="sxs-lookup"><span data-stu-id="5bb99-112">`DetectReplay`.</span></span> <span data-ttu-id="5bb99-113">ブール値。</span><span class="sxs-lookup"><span data-stu-id="5bb99-113">A Boolean value.</span></span> <span data-ttu-id="5bb99-114">サーバーからのリプレイをクライアントが検出するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="5bb99-114">This governs whether the client should detect replays from the server.</span></span> <span data-ttu-id="5bb99-115">既定値は、 `true`です。</span><span class="sxs-lookup"><span data-stu-id="5bb99-115">The default is `true`.</span></span>  
  
    2. <span data-ttu-id="5bb99-116">`MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="5bb99-116">`MaxClockSkew`.</span></span> <span data-ttu-id="5bb99-117"><xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="5bb99-117">A <xref:System.TimeSpan> value.</span></span> <span data-ttu-id="5bb99-118">リプレイ機構に許容されるクライアントとサーバー間の時刻のずれを制御します。</span><span class="sxs-lookup"><span data-stu-id="5bb99-118">Governs how much time skew the replay mechanism can tolerate between the client and the server.</span></span> <span data-ttu-id="5bb99-119">セキュリティ機構は送信されたメッセージのタイム スタンプを調べ、メッセージが古すぎるかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="5bb99-119">The security mechanism examines the time stamp sent and determines whether it was sent too far back in the past.</span></span> <span data-ttu-id="5bb99-120">既定値は 5 分です。</span><span class="sxs-lookup"><span data-stu-id="5bb99-120">The default is 5 minutes.</span></span>  
  
    3. <span data-ttu-id="5bb99-121">`ReplayWindow`.</span><span class="sxs-lookup"><span data-stu-id="5bb99-121">`ReplayWindow`.</span></span> <span data-ttu-id="5bb99-122">`TimeSpan` 値。</span><span class="sxs-lookup"><span data-stu-id="5bb99-122">A `TimeSpan` value.</span></span> <span data-ttu-id="5bb99-123">メッセージがサーバーによって送信されてから (中継局を通過して) クライアントに到達するまで、ネットワーク内に存在できる期間を制御します。</span><span class="sxs-lookup"><span data-stu-id="5bb99-123">This governs how long a message can live in the network after the server sends it (through intermediaries) before reaching the client.</span></span> <span data-ttu-id="5bb99-124">クライアントは、リプレイ検出のため、最新の `ReplayWindow` 内で送信されたメッセージの署名を追跡します。</span><span class="sxs-lookup"><span data-stu-id="5bb99-124">The client tracks the signatures of the messages sent within the latest `ReplayWindow` for the purposes of replay detection.</span></span>  
  
    4. <span data-ttu-id="5bb99-125">`ReplayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="5bb99-125">`ReplayCacheSize`.</span></span> <span data-ttu-id="5bb99-126">整数値。</span><span class="sxs-lookup"><span data-stu-id="5bb99-126">An integer value.</span></span> <span data-ttu-id="5bb99-127">クライアントは、メッセージの署名をキャッシュに格納します。</span><span class="sxs-lookup"><span data-stu-id="5bb99-127">The client stores the signatures of the message in a cache.</span></span> <span data-ttu-id="5bb99-128">この設定は、キャッシュに格納できる署名の数を指定します。</span><span class="sxs-lookup"><span data-stu-id="5bb99-128">This setting specifies how many signatures the cache can store.</span></span> <span data-ttu-id="5bb99-129">最新のリプレイ ウィンドウ内の送信されたメッセージの数がキャッシュ制限に達すると、キャッシュされた最も古い署名が制限時間に達するまで、新しいメッセージは拒否されます。</span><span class="sxs-lookup"><span data-stu-id="5bb99-129">If the number of messages sent within the last replay window reaches the cache limit, new messages are rejected until the oldest cached signatures reach the time limit.</span></span> <span data-ttu-id="5bb99-130">既定値は50万です。</span><span class="sxs-lookup"><span data-stu-id="5bb99-130">The default is 500000.</span></span>  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a><span data-ttu-id="5bb99-131">コードを使用してサービスでのリプレイ検出を制御するには</span><span class="sxs-lookup"><span data-stu-id="5bb99-131">To control replay detection on the service using code</span></span>  
  
1. <span data-ttu-id="5bb99-132"><xref:System.ServiceModel.Channels.SecurityBindingElement> で使用する <xref:System.ServiceModel.Channels.CustomBinding> を作成します。</span><span class="sxs-lookup"><span data-stu-id="5bb99-132">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
2. <span data-ttu-id="5bb99-133"><xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> プロパティを使用して <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> クラスへの参照を返し、前述のように各プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="5bb99-133">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class, and set the properties as described previously.</span></span>  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a><span data-ttu-id="5bb99-134">クライアントまたはサービスの構成でリプレイ検出を制御するには</span><span class="sxs-lookup"><span data-stu-id="5bb99-134">To control replay detection in configuration for the client or service</span></span>  
  
1. <span data-ttu-id="5bb99-135">[\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)を作成します。</span><span class="sxs-lookup"><span data-stu-id="5bb99-135">Create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
2. <span data-ttu-id="5bb99-136">`<security>` 要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="5bb99-136">Create a `<security>` element.</span></span>  
  
3. <span data-ttu-id="5bb99-137">[\<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)または[\<localclientsettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)を作成します。</span><span class="sxs-lookup"><span data-stu-id="5bb99-137">Create a [\<localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) or [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).</span></span>  
  
4. <span data-ttu-id="5bb99-138">`detectReplays`、`maxClockSkew`、`replayWindow`、および `replayCacheSize` の各属性値を適切に設定します。</span><span class="sxs-lookup"><span data-stu-id="5bb99-138">Set the following attribute values, as appropriate: `detectReplays`, `maxClockSkew`, `replayWindow`, and `replayCacheSize`.</span></span> <span data-ttu-id="5bb99-139">`<localServiceSettings>`&lt;localClientSettings&gt; 要素と`<localClientSettings>` 要素の両方の属性を設定する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5bb99-139">The following example sets the attributes of both a `<localServiceSettings>` and a `<localClientSettings>` element:</span></span>  
  
    ```xml  
    <customBinding>  
      <binding name="NewBinding0">  
       <textMessageEncoding />  
        <security>  
         <localClientSettings   
          replayCacheSize="800000"   
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
         <localServiceSettings   
          replayCacheSize="800000"   
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
        <secureConversationBootstrap />  
       </security>  
      <httpTransport />  
     </binding>  
    </customBinding>  
    ```  
  
## <a name="example"></a><span data-ttu-id="5bb99-140">使用例</span><span class="sxs-lookup"><span data-stu-id="5bb99-140">Example</span></span>  
 <span data-ttu-id="5bb99-141">次の例は、<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> メソッドを使用して <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> を作成し、作成されたバインディングのリプレイ プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="5bb99-141">The following example creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> using the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> method, and sets the replay properties of the binding.</span></span>  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a><span data-ttu-id="5bb99-142">リプレイのスコープ : メッセージ セキュリティのみ</span><span class="sxs-lookup"><span data-stu-id="5bb99-142">Scope of Replay: Message Security Only</span></span>  
 <span data-ttu-id="5bb99-143">次の手順は、メッセージ セキュリティ モードにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="5bb99-143">Note that the following procedures apply only to Message security mode.</span></span> <span data-ttu-id="5bb99-144">トランスポート モードとメッセージ資格情報付きトランスポート モードでは、トランスポート機構がリプレイを検出します。</span><span class="sxs-lookup"><span data-stu-id="5bb99-144">For Transport and Transport with Message Credential modes, the transport mechanisms detect replays.</span></span>  
  
## <a name="secure-conversation-notes"></a><span data-ttu-id="5bb99-145">セキュリティで保護されたメッセージ交換に関するメモ</span><span class="sxs-lookup"><span data-stu-id="5bb99-145">Secure Conversation Notes</span></span>  
 <span data-ttu-id="5bb99-146">セキュリティで保護されたメッセージ交換を有効にするバインディングでは、アプリケーション チャネルとセキュリティで保護されたメッセージ交換のブートストラップ バインディングの両方で、上記の設定を調整できます。</span><span class="sxs-lookup"><span data-stu-id="5bb99-146">For bindings that enable secure conversations, you can adjust these settings both for the application channel as well as for the secure conversation bootstrap binding.</span></span> <span data-ttu-id="5bb99-147">たとえば、アプリケーション チャネルに対するリプレイを無効にして、セキュリティで保護されたメッセージ交換を確立するブートストラップ チャネルに対するリプレイを有効にできます。</span><span class="sxs-lookup"><span data-stu-id="5bb99-147">For example, you can turn off replays for the application channel but enable them for the bootstrap channel that establishes the secure conversation.</span></span>  
  
 <span data-ttu-id="5bb99-148">セキュリティで保護されたメッセージ交換セッションを使用しない場合、サーバー ファームのシナリオでのリプレイや、プロセスをリサイクルしたときのリプレイについては、リプレイ検出による検出が保証されません。</span><span class="sxs-lookup"><span data-stu-id="5bb99-148">If you do not use secure conversation sessions, replay detection does not guarantee detecting replays in server farm scenarios and when the process is recycled.</span></span> <span data-ttu-id="5bb99-149">これは、次のシステム指定のバインディングに当てはまります。</span><span class="sxs-lookup"><span data-stu-id="5bb99-149">This applies to the following system-provided bindings:</span></span>  
  
- <span data-ttu-id="5bb99-150"><xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="5bb99-150"><xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
- <span data-ttu-id="5bb99-151"><xref:System.ServiceModel.WSHttpBinding> プロパティが <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> に設定された `false`。</span><span class="sxs-lookup"><span data-stu-id="5bb99-151"><xref:System.ServiceModel.WSHttpBinding> with the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property set to `false`.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5bb99-152">コードのコンパイル方法</span><span class="sxs-lookup"><span data-stu-id="5bb99-152">Compiling the Code</span></span>  
  
- <span data-ttu-id="5bb99-153">コードのコンパイルには次の名前空間が必要です。</span><span class="sxs-lookup"><span data-stu-id="5bb99-153">The following namespaces are required to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a><span data-ttu-id="5bb99-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="5bb99-154">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="5bb99-155">セキュリティ保護されたメッセージ交換とセッション</span><span class="sxs-lookup"><span data-stu-id="5bb99-155">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)
- [<span data-ttu-id="5bb99-156">\<localClientSettings></span><span class="sxs-lookup"><span data-stu-id="5bb99-156">\<localClientSettings></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)
- [<span data-ttu-id="5bb99-157">方法 : SecurityBindingElement を使用してカスタム バインディングを作成する</span><span class="sxs-lookup"><span data-stu-id="5bb99-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
