---
title: <localClientSettings> 要素
ms.date: 03/30/2017
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
ms.openlocfilehash: 19eaea71fdaad1b945524cca5cf15634e0b0fa14
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158735"
---
# <a name="localclientsettings-element"></a><span data-ttu-id="1d8c2-102">\<localClientSettings> 要素</span><span class="sxs-lookup"><span data-stu-id="1d8c2-102">\<localClientSettings> element</span></span>

<span data-ttu-id="1d8c2-103">このバインディングのローカル クライアントのセキュリティ設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-103">Specifies the security settings of a local client for this binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localClientSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="1d8c2-104">構文</span><span class="sxs-lookup"><span data-stu-id="1d8c2-104">Syntax</span></span>  
  
```xml  
<security>
   <localClientSettings cacheCookies="Boolean"
                        cookieRenewalThresholdPercentage="Integer"
                        detectReplays="Boolean"
                        maxClockSkew="TimeSpan"
                        maxCookieCachingTime="TimeSpan"
                        reconnectTransportOnFailure="Boolean"
                        replayCacheSize="Integer"
                        replayWindow="TimeSpan"
                        sessionKeyRenewalInterval="TimeSpan"
                        sessionKeyRolloverInterval="TimeSpan"
                        timestampValidityDuration="TimeSpan" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d8c2-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="1d8c2-105">Attributes and Elements</span></span>  

 <span data-ttu-id="1d8c2-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d8c2-107">属性</span><span class="sxs-lookup"><span data-stu-id="1d8c2-107">Attributes</span></span>  
  
|<span data-ttu-id="1d8c2-108">属性</span><span class="sxs-lookup"><span data-stu-id="1d8c2-108">Attribute</span></span>|<span data-ttu-id="1d8c2-109">[説明]</span><span class="sxs-lookup"><span data-stu-id="1d8c2-109">Description</span></span>|  
|---------------|-----------------|  
|`cacheCookies`|<span data-ttu-id="1d8c2-110">クッキーのキャッシュが有効かどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-110">A Boolean value that specifies whether cookie caching is enabled.</span></span> <span data-ttu-id="1d8c2-111">既定では、 `false`です。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-111">The default is `false`.</span></span>|  
|`cookieRenewalThresholdPercentage`|<span data-ttu-id="1d8c2-112">更新できるクッキーの最大パーセンテージを指定する整数。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-112">An integer that specifies the maximum percentage of cookies that can be renewed.</span></span> <span data-ttu-id="1d8c2-113">この値は、0 ～ 100 (0 と 100を含む) のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-113">This value should be between 0 and 100 inclusively.</span></span> <span data-ttu-id="1d8c2-114">既定値は 90 です。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-114">The default is 90.</span></span>|  
|`detectReplays`|<span data-ttu-id="1d8c2-115">チャネルに対するリプレイ攻撃を検出し、自動的に処理するかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-115">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span> <span data-ttu-id="1d8c2-116">既定では、 `false`です。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-116">The default is `false`.</span></span>|  
|`maxClockSkew`|<span data-ttu-id="1d8c2-117">通信している双方の 2 つのシステム クロックのずれの最長時間を指定する <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-117">A <xref:System.TimeSpan> that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span> <span data-ttu-id="1d8c2-118">既定値は、"00:05:00" です。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-118">The default value is "00:05:00".</span></span><br /><br /> <span data-ttu-id="1d8c2-119">この値が既定値に設定されている場合、受信側はメッセージが受信された時間より前後最大 5 分間の送信時間タイム スタンプを持つメッセージを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-119">When this value is set to the default, the receiver accepts messages with send-time time stamps up to 5 minutes later or earlier than the time the message was received.</span></span> <span data-ttu-id="1d8c2-120">送信時間テストにパスしないメッセージは拒否されます。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-120">Messages that do not pass the send-time test are rejected.</span></span> <span data-ttu-id="1d8c2-121">この設定は、`replayWindow` 属性と組み合わせて使用します。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-121">This setting is used in conjunction with the `replayWindow` attribute.</span></span>|  
|`maxCookieCachingTime`|<span data-ttu-id="1d8c2-122">クッキーの最長有効期間を指定する <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-122">A <xref:System.TimeSpan> that specifies the maximum lifetime of cookies.</span></span> <span data-ttu-id="1d8c2-123">デフォルト値は "10675199.02:48:05.4775807" です。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-123">The default value is "10675199.02:48:05.4775807".</span></span>|  
|`reconnectTransportOnFailure`|<span data-ttu-id="1d8c2-124">WS-ReliableMessaging を使用した接続が、トランスポート エラーの後再接続を試みるかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-124">A Boolean value that specifies whether connections using WS-Reliable messaging will attempt to reconnect after transport failures.</span></span> <span data-ttu-id="1d8c2-125">既定値は `true` です。これは、再接続の試行が無限に行われることを意味します。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-125">The default is `true`, which means that infinite attempts to reconnect are attempted.</span></span> <span data-ttu-id="1d8c2-126">循環は非アクティブ タイムアウトにより破棄され、再接続できない場合はチャネルが例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-126">The cycle is broken by the inactivity time-out, which causes the channel to throw an exception when it cannot be reconnected.</span></span>|  
|`replayCacheSize`|<span data-ttu-id="1d8c2-127">リプレイ検証で使用される、キャッシュ済みの nonce 数を指定する正の整数。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-127">A positive integer that specifies the number of cached nonces used for replay detection.</span></span> <span data-ttu-id="1d8c2-128">この制限を越えると、最も古い nonce が削除され、新しいメッセージ用に新しい nonce が作成されます。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-128">If this limit is exceeded, the oldest nonce is removed and a new nonce is created for the new message.</span></span> <span data-ttu-id="1d8c2-129">既定値は 500000 です。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-129">The default value is 500000.</span></span>|  
|`replayWindow`|<span data-ttu-id="1d8c2-130">個別のメッセージ nonce の有効期間を指定する <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-130">A <xref:System.TimeSpan> that specifies the duration in which individual message nonces are valid.</span></span><br /><br /> <span data-ttu-id="1d8c2-131">この期間が過ぎると、以前に送信されたメッセージと同じ nonce を持つメッセージは受け入れられません。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-131">After this duration, a message sent with the same nonce as the one sent before will not be accepted.</span></span> <span data-ttu-id="1d8c2-132">この属性は、リプレイ攻撃を防ぐために `maxClockSkew` 属性と組み合わせて使用します。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-132">This attribute is used in conjunction with the `maxClockSkew` attribute to prevent replay attacks.</span></span> <span data-ttu-id="1d8c2-133">攻撃者は、メッセージのリプレイ ウィンドウの期限が切れた後にメッセージをリプレイする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-133">An attacker could replay a message after its replay window has expired.</span></span> <span data-ttu-id="1d8c2-134">ただし、このメッセージは `maxClockSkew` テストに失敗します。このテストは、メッセージが受信された時間の前後指定時間以内の送信時間タイムスタンプを持つメッセージを拒否します。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-134">This message, however, would fail the `maxClockSkew` test which rejects messages with send-time timestamps up to a specified time later or earlier than the time the message was received.</span></span>|  
|`sessionKeyRenewalInterval`|<span data-ttu-id="1d8c2-135">イニシエーターがセキュリティ セッションのキーを更新するまでの期間を指定する <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-135">A <xref:System.TimeSpan> that specifies the duration after which the initiator will renew the key for the security session.</span></span> <span data-ttu-id="1d8c2-136">既定値は "10:00:00" です。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-136">The default is "10:00:00".</span></span>|  
|`sessionKeyRolloverInterval`|<span data-ttu-id="1d8c2-137">キーの更新中に、前のセッション キーが受信メッセージで有効な時間間隔を指定する <xref:System.TimeSpan> です。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-137">A <xref:System.TimeSpan> that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span> <span data-ttu-id="1d8c2-138">既定値は "00:05:00" です。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-138">The default is "00:05:00".</span></span><br /><br /> <span data-ttu-id="1d8c2-139">キーの更新中、クライアントおよびサーバーは、常に、利用可能な最新のキーを使用してメッセージを送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-139">During key renewal, the client and server must always send messages using the most current available key.</span></span> <span data-ttu-id="1d8c2-140">どちらのパーティも、ロールオーバー時間に達するまで、前のセッション キーで保護された受信メッセージを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-140">Both parties will accept incoming messages secured with the previous session key until the rollover time expires.</span></span>|  
|`timestampValidityDuration`|<span data-ttu-id="1d8c2-141">タイムスタンプの有効期間を指定する正の <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-141">A positive <xref:System.TimeSpan> that specifies the duration in which a time stamp is valid.</span></span> <span data-ttu-id="1d8c2-142">既定値は "00:15:00" です。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-142">The default is "00:15:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d8c2-143">子要素</span><span class="sxs-lookup"><span data-stu-id="1d8c2-143">Child Elements</span></span>  

 <span data-ttu-id="1d8c2-144">None</span><span class="sxs-lookup"><span data-stu-id="1d8c2-144">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d8c2-145">親要素</span><span class="sxs-lookup"><span data-stu-id="1d8c2-145">Parent Elements</span></span>  
  
|<span data-ttu-id="1d8c2-146">要素</span><span class="sxs-lookup"><span data-stu-id="1d8c2-146">Element</span></span>|<span data-ttu-id="1d8c2-147">説明</span><span class="sxs-lookup"><span data-stu-id="1d8c2-147">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="1d8c2-148">カスタム バインドのセキュリティ オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-148">Specifies the security options for a custom binding.</span></span>|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|<span data-ttu-id="1d8c2-149">セキュリティで保護されたメッセージ交換サービスの開始に使用される既定値を指定します。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-149">Specifies the default values used for initiating a secure conversation service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d8c2-150">解説</span><span class="sxs-lookup"><span data-stu-id="1d8c2-150">Remarks</span></span>  

 <span data-ttu-id="1d8c2-151">この設定は、サービスのセキュリティ ポリシーから派生する設定ではないという点でローカルです。</span><span class="sxs-lookup"><span data-stu-id="1d8c2-151">The settings are local in the sense that they are not settings derived from the security policy of the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d8c2-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d8c2-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="1d8c2-153">バインド</span><span class="sxs-lookup"><span data-stu-id="1d8c2-153">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1d8c2-154">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="1d8c2-154">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1d8c2-155">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="1d8c2-155">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="1d8c2-156">方法: SecurityBindingElement を使用してカスタム バインドを作成する</span><span class="sxs-lookup"><span data-stu-id="1d8c2-156">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="1d8c2-157">カスタム バインディング セキュリティ</span><span class="sxs-lookup"><span data-stu-id="1d8c2-157">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
