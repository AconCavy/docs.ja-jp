---
title: リプレイ攻撃
ms.date: 03/30/2017
ms.assetid: 7a17e040-93cd-4432-81b9-9f62fec78c8f
ms.openlocfilehash: 47a4726859605415b4e3e1b4d523f2f8059a3989
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586300"
---
# <a name="replay-attacks"></a><span data-ttu-id="d424c-102">リプレイ攻撃</span><span class="sxs-lookup"><span data-stu-id="d424c-102">Replay Attacks</span></span>
<span data-ttu-id="d424c-103">*リプレイ攻撃*は、攻撃者がメッセージのストリームを2つのパーティ間でコピーし、そのストリームを1つ以上のパーティにリプレイする場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="d424c-103">A *replay attack* occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="d424c-104">攻撃が和らげられていない場合、攻撃対象になったコンピューターはストリームを正当なメッセージとして処理するため、項目の順序が重複するなど、望ましくない状況に陥ります。</span><span class="sxs-lookup"><span data-stu-id="d424c-104">Unless mitigated, the computers subject to the attack process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
## <a name="bindings-may-be-subject-to-reflection-attacks"></a><span data-ttu-id="d424c-105">バインディングはリフレクション攻撃にさらされる可能性がある</span><span class="sxs-lookup"><span data-stu-id="d424c-105">Bindings May Be Subject to Reflection Attacks</span></span>  
 <span data-ttu-id="d424c-106">*リフレクション攻撃*は、応答として受信者から送信されたメッセージと同じように、送信側からのメッセージを再生します。</span><span class="sxs-lookup"><span data-stu-id="d424c-106">*Reflection attacks* are replays of messages back to a sender as if they came from the receiver as the reply.</span></span> <span data-ttu-id="d424c-107">Windows Communication Foundation (WCF) メカニズムでの標準の*再生検出*では、これは自動的には処理されません。</span><span class="sxs-lookup"><span data-stu-id="d424c-107">The standard *replay detection* in the Windows Communication Foundation (WCF) mechanism does not automatically handle this.</span></span>  
  
 <span data-ttu-id="d424c-108">既定では、リフレクション攻撃が軽減されます。これは、WCF サービスモデルが署名付きメッセージ ID を要求メッセージに追加し、応答メッセージに署名済みヘッダーを要求するため `relates-to` です。</span><span class="sxs-lookup"><span data-stu-id="d424c-108">Reflection attacks are mitigated by default because the WCF service model adds a signed message ID to request messages and expects a signed `relates-to` header on response messages.</span></span> <span data-ttu-id="d424c-109">その結果、要求メッセージを応答としてリプレイできません。</span><span class="sxs-lookup"><span data-stu-id="d424c-109">Consequently, the request message cannot be replayed as a response.</span></span> <span data-ttu-id="d424c-110">セキュリティで保護された信頼できるメッセージ (RM) シナリオでは、リフレクション攻撃は次の理由で軽減されます。</span><span class="sxs-lookup"><span data-stu-id="d424c-110">In secure reliable message (RM) scenarios, reflection attacks are mitigated because:</span></span>  
  
- <span data-ttu-id="d424c-111">シーケンス メッセージの作成スキーマとシーケンス応答メッセージの作成スキーマが異なります。</span><span class="sxs-lookup"><span data-stu-id="d424c-111">The create sequence and create sequence response message schemas are different.</span></span>  
  
- <span data-ttu-id="d424c-112">一方向シーケンスの場合、クライアントから送信されたシーケンス メッセージをクライアントに対してリプレイすることはできません。これは、クライアントがこのようなメッセージを認識できないためです。</span><span class="sxs-lookup"><span data-stu-id="d424c-112">For simplex sequences, sequence messages the client sends cannot be replayed back to it because the client cannot understand such messages.</span></span>  
  
- <span data-ttu-id="d424c-113">双方向シーケンスの場合、2 つのシーケンス ID が一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d424c-113">For duplex sequences, the two sequence IDs must be unique.</span></span> <span data-ttu-id="d424c-114">このため、送信シーケンス メッセージを受信シーケンス メッセージとしてリプレイできません (すべてのシーケンス ヘッダーと本文も署名されています)。</span><span class="sxs-lookup"><span data-stu-id="d424c-114">Thus, an outgoing sequence message cannot be replayed back as an incoming sequence message (all sequence headers and bodies are signed, too).</span></span>  
  
 <span data-ttu-id="d424c-115">リフレクション攻撃の影響を受けやすい唯一のバインディングは WS-Addressing を使用しないバインディング (WS-Addressing を無効にして、対称キー ベースのセキュリティを使用するカスタム バインド) です。</span><span class="sxs-lookup"><span data-stu-id="d424c-115">The only bindings that are susceptible to reflection attacks are those without WS-Addressing: custom bindings that have WS-Addressing disabled and use the symmetric key-based security.</span></span> <span data-ttu-id="d424c-116"><xref:System.ServiceModel.BasicHttpBinding> は、既定では WS-Addressing を使用しませんが、この攻撃を受けやすい方法で対称キー ベースのセキュリティを使用することはありません。</span><span class="sxs-lookup"><span data-stu-id="d424c-116">The <xref:System.ServiceModel.BasicHttpBinding> does not use WS-Addressing by default, but it does not use symmetric key-based security in a way that allows it to be vulnerable to this attack.</span></span>  
  
 <span data-ttu-id="d424c-117">カスタム バインドに対する攻撃を軽減するには、セキュリティ コンテキストを確立しないか、WS-Addressing ヘッダーを要求します。</span><span class="sxs-lookup"><span data-stu-id="d424c-117">The mitigation for custom bindings is to not establish security context or to require WS-Addressing headers.</span></span>  
  
## <a name="web-farm-attacker-replays-request-to-multiple-nodes"></a><span data-ttu-id="d424c-118">Web ファーム : 攻撃者が複数のノードに対して要求をリプレイする</span><span class="sxs-lookup"><span data-stu-id="d424c-118">Web Farm: Attacker Replays Request to Multiple Nodes</span></span>  
 <span data-ttu-id="d424c-119">クライアントは、Web ファームに実装されているサービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="d424c-119">A client uses a service that is implemented on a Web farm.</span></span> <span data-ttu-id="d424c-120">攻撃者は、ファーム内の特定のノードに送信された要求を同じファーム内の別のノードに対してリプレイします。</span><span class="sxs-lookup"><span data-stu-id="d424c-120">An attacker replays a request that was sent to one node in the farm to another node in the farm.</span></span> <span data-ttu-id="d424c-121">また、サービスが再開されると、リプレイ キャッシュがフラッシュされ、攻撃者が要求をリプレイできるようになります </span><span class="sxs-lookup"><span data-stu-id="d424c-121">In addition, if a service is restarted, the replay cache is flushed, allowing an attacker to replay the request.</span></span> <span data-ttu-id="d424c-122">(このキャッシュには、以前使用されたメッセージ署名の値が格納されています。これにより、メッセージ署名は一度しか使用できないため、リプレイを防止できます。</span><span class="sxs-lookup"><span data-stu-id="d424c-122">(The cache contains used, previously seen message signature values and prevents replays so those signatures can be used only once.</span></span> <span data-ttu-id="d424c-123">リプレイ キャッシュは Web ファーム内で共有されません)。</span><span class="sxs-lookup"><span data-stu-id="d424c-123">Replay caches are not shared across a Web farm.)</span></span>  
  
 <span data-ttu-id="d424c-124">回避事項を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d424c-124">Mitigations include:</span></span>  
  
- <span data-ttu-id="d424c-125">ステートフルなセキュリティ コンテキスト トークンと共にメッセージ モード セキュリティを使用します (セキュリティで保護されたメッセージ交換を有効にするかどうかは任意)。</span><span class="sxs-lookup"><span data-stu-id="d424c-125">Use message mode security with stateful security context tokens (with or without secure conversation enabled).</span></span> <span data-ttu-id="d424c-126">詳細については、「[方法: セキュリティで保護されたセッションのセキュリティコンテキストトークンを作成](how-to-create-a-security-context-token-for-a-secure-session.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d424c-126">For more information, see [How to: Create a Security Context Token for a Secure Session](how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
- <span data-ttu-id="d424c-127">トランスポート レベルのセキュリティを使用するようにサービスを構成します。</span><span class="sxs-lookup"><span data-stu-id="d424c-127">Configure the service to use transport-level security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d424c-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="d424c-128">See also</span></span>

- [<span data-ttu-id="d424c-129">セキュリティの考慮事項</span><span class="sxs-lookup"><span data-stu-id="d424c-129">Security Considerations</span></span>](security-considerations-in-wcf.md)
- [<span data-ttu-id="d424c-130">情報の公開</span><span class="sxs-lookup"><span data-stu-id="d424c-130">Information Disclosure</span></span>](information-disclosure.md)
- [<span data-ttu-id="d424c-131">特権の昇格</span><span class="sxs-lookup"><span data-stu-id="d424c-131">Elevation of Privilege</span></span>](elevation-of-privilege.md)
- [<span data-ttu-id="d424c-132">サービス拒否</span><span class="sxs-lookup"><span data-stu-id="d424c-132">Denial of Service</span></span>](denial-of-service.md)
- [<span data-ttu-id="d424c-133">改ざん</span><span class="sxs-lookup"><span data-stu-id="d424c-133">Tampering</span></span>](tampering.md)
- [<span data-ttu-id="d424c-134">サポートされていないシナリオ</span><span class="sxs-lookup"><span data-stu-id="d424c-134">Unsupported Scenarios</span></span>](unsupported-scenarios.md)
