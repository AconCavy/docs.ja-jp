---
title: Windows Communication Foundation のプライバシー情報
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
ms.openlocfilehash: 7bd56d44eeb6af70b94cdde77d48e917ef8afb9a
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347780"
---
# <a name="windows-communication-foundation-privacy-information"></a><span data-ttu-id="af569-102">Windows Communication Foundation のプライバシー情報</span><span class="sxs-lookup"><span data-stu-id="af569-102">Windows Communication Foundation Privacy Information</span></span>
<span data-ttu-id="af569-103">マイクロソフトは、エンド ユーザーのプライバシー保護に力を入れています。</span><span class="sxs-lookup"><span data-stu-id="af569-103">Microsoft is committed to protecting end-users' privacy.</span></span> <span data-ttu-id="af569-104">Windows Communication Foundation (WCF) バージョン3.0 を使用してアプリケーションをビルドすると、アプリケーションがエンドユーザーのプライバシーに影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="af569-104">When you build an application using Windows Communication Foundation (WCF), version 3.0, your application may impact your end-users' privacy.</span></span> <span data-ttu-id="af569-105">たとえば、アプリケーションが明示的にユーザーの連絡先情報を収集することがあります。つまり、アプリケーションがインターネットを経由して Web サイトに情報を要求したり、情報を送信したりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="af569-105">For example, your application may explicitly collect user contact information, or it may request or send information over the Internet to your Web site.</span></span> <span data-ttu-id="af569-106">マイクロソフトの技術をアプリケーションに組み込んでいる場合、その技術にプライバシーに影響を与える可能性がある独自の動作が存在することがあります。</span><span class="sxs-lookup"><span data-stu-id="af569-106">If you embed Microsoft technology in your application, that technology may have its own behavior that might affect privacy.</span></span> <span data-ttu-id="af569-107">WCF は、お客様またはエンドユーザーが Microsoft に送信することを選択しない限り、アプリケーションからマイクロソフトに情報を送信しません。</span><span class="sxs-lookup"><span data-stu-id="af569-107">WCF does not send any information to Microsoft from your application unless you or the end-user choose to send it to us.</span></span>  
  
## <a name="wcf-in-brief"></a><span data-ttu-id="af569-108">WCF の概要</span><span class="sxs-lookup"><span data-stu-id="af569-108">WCF in Brief</span></span>  
 <span data-ttu-id="af569-109">WCF は、開発者が分散アプリケーションを構築できるようにする Microsoft .NET Framework を使用する分散メッセージングフレームワークです。</span><span class="sxs-lookup"><span data-stu-id="af569-109">WCF is a distributed messaging framework using the Microsoft .NET Framework that allows developers to build distributed applications.</span></span> <span data-ttu-id="af569-110">2 つのアプリケーション間で交換されるメッセージには、ヘッダーと本文情報が入ります。</span><span class="sxs-lookup"><span data-stu-id="af569-110">Messages communicated between two applications contain header and body information.</span></span>  
  
 <span data-ttu-id="af569-111">ヘッダーには、アプリケーションが使用するサービスに応じて、メッセージ ルーティング、セキュリティ情報、トランザクションなどの情報が追加されます。</span><span class="sxs-lookup"><span data-stu-id="af569-111">Headers may contain message routing, security information, transactions, and more depending on the services used by the application.</span></span> <span data-ttu-id="af569-112">メッセージは、通常、既定で暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="af569-112">Messages are typically encrypted by default.</span></span> <span data-ttu-id="af569-113">ただし、`BasicHttpBinding` を使用する場合は例外です。このバインディングは、セキュリティで保護されていない従来の Web サービスで使用するために設計されています。</span><span class="sxs-lookup"><span data-stu-id="af569-113">The one exception is when using the `BasicHttpBinding`, which was designed for use with non-secured, legacy Web services.</span></span> <span data-ttu-id="af569-114">アプリケーションの設計者であるユーザーには最終設計に対する責任があります。</span><span class="sxs-lookup"><span data-stu-id="af569-114">As the application designer, you are responsible for the final design.</span></span> <span data-ttu-id="af569-115">SOAP 本文内のメッセージには、アプリケーション固有のデータが含まれます。ただし、アプリケーションによって定義された個人情報など、このデータは、WCF 暗号化機能または機密性機能を使用してセキュリティで保護することができます。</span><span class="sxs-lookup"><span data-stu-id="af569-115">Messages in the SOAP body contain application-specific data; however, this data, such as application-defined personal information, can be secured by using WCF encryption or confidentiality features.</span></span> <span data-ttu-id="af569-116">次のセクションでは、プライバシーに影響を与える可能性がある機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="af569-116">The following sections describe the features that potentially impact privacy.</span></span>  
  
## <a name="messaging"></a><span data-ttu-id="af569-117">メッセージング</span><span class="sxs-lookup"><span data-stu-id="af569-117">Messaging</span></span>  
 <span data-ttu-id="af569-118">各 WCF メッセージには、メッセージの送信先と応答の送信先を指定するアドレスヘッダーがあります。</span><span class="sxs-lookup"><span data-stu-id="af569-118">Each WCF message has an address header that specifies the message destination and where the reply should go.</span></span>  
  
 <span data-ttu-id="af569-119">エンドポイント アドレスのアドレス構成要素は、エンドポイントを識別する URI (Uniform Resource Identifier) です。</span><span class="sxs-lookup"><span data-stu-id="af569-119">The address component of an endpoint address is a Uniform Resource Identifier (URI) that identifies the endpoint.</span></span> <span data-ttu-id="af569-120">このアドレスは、ネットワーク アドレスまたは論理アドレスのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="af569-120">The address can be a network address or a logical address.</span></span> <span data-ttu-id="af569-121">アドレスには、コンピューター名 (ホスト名、完全修飾ドメイン名) と IP アドレスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="af569-121">The address may include machine name (hostname, fully qualified domain name) and an IP address.</span></span> <span data-ttu-id="af569-122">また、エンドポイント アドレスには、グローバル一意識別子 (GUID)、または各アドレスを識別するために使用される一時アドレス指定用に GUID のコレクションを入れることもできます。</span><span class="sxs-lookup"><span data-stu-id="af569-122">The endpoint address may also contain a globally unique identifier (GUID), or a collection of GUIDs for temporary addressing used to discern each address.</span></span> <span data-ttu-id="af569-123">各メッセージには、GUID 形式のメッセージ ID があります。</span><span class="sxs-lookup"><span data-stu-id="af569-123">Each message contains a message ID that is a GUID.</span></span> <span data-ttu-id="af569-124">この機能は、WS-Addressing 参照仕様に準拠します。</span><span class="sxs-lookup"><span data-stu-id="af569-124">This feature follows the WS-Addressing reference standard.</span></span>  
  
 <span data-ttu-id="af569-125">WCF メッセージングレイヤーは、個人情報をローカルコンピューターに書き込みません。</span><span class="sxs-lookup"><span data-stu-id="af569-125">The WCF messaging layer does not write any personal information to the local machine.</span></span> <span data-ttu-id="af569-126">ただし、サービスの開発者が個人情報を公開するサービスを作成した場合は、ネットワーク レベルで個人情報を公開することがあります。このような例として、エンドポイント名に個人名を使用している場合や、エンドポイントの Web サービス記述言語に個人情報を追加しても、https を使用して WSDL にアクセスすることをクライアントに要求しない場合などがあります。</span><span class="sxs-lookup"><span data-stu-id="af569-126">However, it might propagate personal information at the network level if a service developer has created a service that exposes such information (for example, by using a person's name in an endpoint name, or including personal information in the endpoint's Web Services Description Language but not requiring clients to use https to access the WSDL).</span></span> <span data-ttu-id="af569-127">また、開発者が個人情報を公開するエンドポイントに対して[ServiceModel メタデータユーティリティツール (svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)ツールを実行した場合、ツールの出力にその情報が含まれている可能性があり、出力ファイルはローカルハードディスクに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="af569-127">Also, if a developer runs the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) tool against an endpoint that exposes personal information, the tool's output could contain that information, and the output file is written to the local hard disk.</span></span>  
  
## <a name="hosting"></a><span data-ttu-id="af569-128">ホスト</span><span class="sxs-lookup"><span data-stu-id="af569-128">Hosting</span></span>  
 <span data-ttu-id="af569-129">WCF のホスティング機能を使用すると、アプリケーションをオンデマンドで開始したり、複数のアプリケーション間でポートの共有を有効にしたりできます。</span><span class="sxs-lookup"><span data-stu-id="af569-129">The hosting feature in WCF allows applications to start on demand or to enable port sharing between multiple applications.</span></span> <span data-ttu-id="af569-130">WCF アプリケーションは、ASP.NET と同様にインターネットインフォメーションサービス (IIS) でホストできます。</span><span class="sxs-lookup"><span data-stu-id="af569-130">An WCF application can be hosted in Internet Information Services (IIS), similar to ASP.NET.</span></span>  
  
 <span data-ttu-id="af569-131">ホストでは、特定の情報をネットワークに公開せず、コンピューター上にデータを格納しません。</span><span class="sxs-lookup"><span data-stu-id="af569-131">Hosting does not expose any specific information on the network and it does not keep data on the machine.</span></span>  
  
## <a name="message-security"></a><span data-ttu-id="af569-132">メッセージのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="af569-132">Message Security</span></span>  
 <span data-ttu-id="af569-133">WCF セキュリティは、メッセージングアプリケーションのセキュリティ機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="af569-133">WCF security provides the security capabilities for messaging applications.</span></span> <span data-ttu-id="af569-134">提供するセキュリティ機能には、認証と承認があります。</span><span class="sxs-lookup"><span data-stu-id="af569-134">The security functions provided include authentication and authorization.</span></span>  
  
 <span data-ttu-id="af569-135">認証は、クライアントとサービスとの間で資格情報を交換することによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="af569-135">Authentication is performed by passing credentials between the clients and services.</span></span> <span data-ttu-id="af569-136">認証は、次のように、トランスポート レベルのセキュリティまたは SOAP メッセージ レベルのセキュリティで実行できます。</span><span class="sxs-lookup"><span data-stu-id="af569-136">Authentication can be either through transport-level security or through SOAP message-level security, as follows:</span></span>  
  
- <span data-ttu-id="af569-137">SOAP メッセージ セキュリティでは、発行者に応じて、ユーザー名とパスワード、X.509 証明書、Kerberos チケット、SAML トークンのような資格情報を使用して認証が実行されます。このすべての資格情報は、個人情報を含んでいる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="af569-137">In SOAP message security, authentication is performed through credentials like username/passwords, X.509 certificates, Kerberos tickets, and SAML tokens, all of which might contain personal information, depending on the issuer.</span></span>  
  
- <span data-ttu-id="af569-138">トランスポート セキュリティでは、HTTP 認証方式 (Basic、Digest、Negotiate、Integrated Windows Authorization、NTLM、None、および Anonymous) のような従来のトランスポート認証機構によって認証が実行されます。</span><span class="sxs-lookup"><span data-stu-id="af569-138">Using transport security, authentication is done through traditional transport authentication mechanisms like HTTP authentication schemes (Basic, Digest, Negotiate, Integrated Windows Authorization, NTLM, None, and Anonymous), and form authentication.</span></span>  
  
 <span data-ttu-id="af569-139">認証によって、通信するエンドポイント間にセキュリティで保護されたセッションを確立できます。</span><span class="sxs-lookup"><span data-stu-id="af569-139">Authentication can result in a secure session established between the communicating endpoints.</span></span> <span data-ttu-id="af569-140">このセッションは、セキュリティ セッションの有効期間が切れるまで有効な GUID によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="af569-140">The session is identified by a GUID that lasts the lifetime of the security session.</span></span> <span data-ttu-id="af569-141">格納されるデータと格納場所を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="af569-141">The following table shows what is kept and where.</span></span>  
  
|<span data-ttu-id="af569-142">data</span><span class="sxs-lookup"><span data-stu-id="af569-142">Data</span></span>|<span data-ttu-id="af569-143">ストレージ</span><span class="sxs-lookup"><span data-stu-id="af569-143">Storage</span></span>|  
|----------|-------------|  
|<span data-ttu-id="af569-144">ユーザー名、X.509 証明書、Kerberos トークンなどのプレゼンテーション資格情報、および資格情報への参照</span><span class="sxs-lookup"><span data-stu-id="af569-144">Presentation credentials, such as username, X.509 certificates, Kerberos tokens, and references to credentials.</span></span>|<span data-ttu-id="af569-145">Windows 証明書ストアなど、標準の Windows 資格情報管理機構</span><span class="sxs-lookup"><span data-stu-id="af569-145">Standard Windows credential management mechanisms such as the Windows certificate store.</span></span>|  
|<span data-ttu-id="af569-146">ユーザー名とパスワードなど、ユーザーのメンバーシップ情報</span><span class="sxs-lookup"><span data-stu-id="af569-146">User membership information, such as usernames and passwords.</span></span>|<span data-ttu-id="af569-147">ASP.NET メンバーシッププロバイダー。</span><span class="sxs-lookup"><span data-stu-id="af569-147">ASP.NET membership providers.</span></span>|  
|<span data-ttu-id="af569-148">クライアントに対するサービスの認証に使用されるサービスの ID 情報</span><span class="sxs-lookup"><span data-stu-id="af569-148">Identity information about the service used to authenticate the service to clients.</span></span>|<span data-ttu-id="af569-149">サービスのエンドポイント アドレス</span><span class="sxs-lookup"><span data-stu-id="af569-149">Endpoint address of the service.</span></span>|  
|<span data-ttu-id="af569-150">呼び出し元情報</span><span class="sxs-lookup"><span data-stu-id="af569-150">Caller information.</span></span>|<span data-ttu-id="af569-151">監査ログ</span><span class="sxs-lookup"><span data-stu-id="af569-151">Auditing logs.</span></span>|  
  
## <a name="auditing"></a><span data-ttu-id="af569-152">監査</span><span class="sxs-lookup"><span data-stu-id="af569-152">Auditing</span></span>  
 <span data-ttu-id="af569-153">監査では、認証イベントと承認イベントの成功と失敗を記録します。</span><span class="sxs-lookup"><span data-stu-id="af569-153">Auditing records the success and failure of authentication and authorization events.</span></span> <span data-ttu-id="af569-154">監査レコードには、サービス URI、アクション URI、および呼び出し元の ID が入ります。</span><span class="sxs-lookup"><span data-stu-id="af569-154">Auditing records contain the following data: service URI, action URI, and the caller's identification.</span></span>  
  
 <span data-ttu-id="af569-155">また、監査では、管理者がメッセージ ログの設定 (オンまたはオフ) を変更した時刻を記録します。その理由は、メッセージ ログが、ヘッダーと本文のアプリケーション固有のデータをログに記録する可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="af569-155">Auditing also records when the administrator modifies the configuration of message logging (turning it on or off), because message logging may log application-specific data in headers and bodies.</span></span> <span data-ttu-id="af569-156">[!INCLUDE[wxp](../../../includes/wxp-md.md)] の場合、レコードはアプリケーション イベント ログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="af569-156">For [!INCLUDE[wxp](../../../includes/wxp-md.md)], a record is logged in the application event log.</span></span> <span data-ttu-id="af569-157">Windows Vista および Windows Server 2003 では、レコードがセキュリティイベントログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="af569-157">For Windows Vista and Windows Server 2003, a record is logged in the security event log.</span></span>  
  
## <a name="transactions"></a><span data-ttu-id="af569-158">トランザクション</span><span class="sxs-lookup"><span data-stu-id="af569-158">Transactions</span></span>  
 <span data-ttu-id="af569-159">トランザクション機能は、WCF アプリケーションにトランザクションサービスを提供します。</span><span class="sxs-lookup"><span data-stu-id="af569-159">The transactions feature provides transactional services to a WCF application.</span></span>  
  
 <span data-ttu-id="af569-160">トランザクションの伝達で使用されるトランザクション ヘッダーには、GUID 形式のトランザクション ID または登録リスト ID を追加できます。</span><span class="sxs-lookup"><span data-stu-id="af569-160">Transaction headers used in transaction propagation may contain Transaction IDs or Enlistment IDs, which are GUIDs.</span></span>  
  
 <span data-ttu-id="af569-161">トランザクション機能では、Microsoft 分散トランザクション コーディネーター (MSDTC) トランザクション マネージャー (Windows コンポーネントの 1 つ) を使用して、トランザクション状態を管理します。</span><span class="sxs-lookup"><span data-stu-id="af569-161">The Transactions feature uses the Microsoft Distributed Transaction Coordinator (MSDTC) Transaction Manager (a Windows component) to manage transaction state.</span></span> <span data-ttu-id="af569-162">既定では、トランザクション マネージャー間の通信は暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="af569-162">By default, communications between Transactions Managers are encrypted.</span></span> <span data-ttu-id="af569-163">トランザクション マネージャーは、エンドポイント参照、トランザクション ID、および登録リスト ID を永続状態の一部としてログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="af569-163">Transaction Managers may log endpoint references, Transaction IDs, and Enlistment IDs as part of their durable state.</span></span> <span data-ttu-id="af569-164">この状態の有効期間は、トランザクション マネージャーのログ ファイルの有効期間によって決まります。</span><span class="sxs-lookup"><span data-stu-id="af569-164">The lifetime of this state is determined by the lifetime of the Transaction Manager’s log file.</span></span> <span data-ttu-id="af569-165">MSDTC サービスがこのログを所有し、管理します。</span><span class="sxs-lookup"><span data-stu-id="af569-165">The MSDTC service owns and maintains this log.</span></span>  
  
 <span data-ttu-id="af569-166">トランザクション機能は、WS-Coordination 仕様と WS-AtomicTransaction 仕様を実装します。</span><span class="sxs-lookup"><span data-stu-id="af569-166">The Transactions feature implements the WS-Coordination and WS-Atomic Transaction standards.</span></span>  
  
## <a name="reliable-sessions"></a><span data-ttu-id="af569-167">信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="af569-167">Reliable Sessions</span></span>  
 <span data-ttu-id="af569-168">WCF の信頼できるセッションでは、トランスポートまたは中継エラーが発生したときにメッセージが転送されます。</span><span class="sxs-lookup"><span data-stu-id="af569-168">Reliable sessions in WCF provide the transfer of messages when transport or intermediary failures occur.</span></span> <span data-ttu-id="af569-169">信頼できるセッションは、基になるトランスポート (たとえば、ワイヤレス ネットワーク上の TCP 接続) が切断している場合やメッセージを紛失した場合 (HTTP プロキシでの送受信メッセージの破棄) でも、正確に 1 回のメッセージ転送を実行します。</span><span class="sxs-lookup"><span data-stu-id="af569-169">They provide an exactly-once transfer of messages even when the underlying transport disconnects (for example, a TCP connection on a wireless network) or loses a message (an HTTP proxy dropping an outgoing or incoming message).</span></span> <span data-ttu-id="af569-170">また、メッセージが送信された順序を維持するので、メッセージの並べ替え (マルチパス ルーティングの場合に発生する可能性がある) を回復できます。</span><span class="sxs-lookup"><span data-stu-id="af569-170">Reliable sessions also recover message reordering (as may happen in the case of multipath routing), preserving the order in which the messages were sent.</span></span>  
  
 <span data-ttu-id="af569-171">信頼できるセッションは、WS-ReliableMessaging (WS-RM) プロトコルを使用して実装されています。</span><span class="sxs-lookup"><span data-stu-id="af569-171">Reliable sessions are implemented using the WS-ReliableMessaging (WS-RM) protocol.</span></span> <span data-ttu-id="af569-172">これによって追加される WS-RM ヘッダーには、特定の信頼できるセッションに関連付けられたすべてのメッセージの識別に使用されるセッション情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="af569-172">They add WS-RM headers that contain session information, which is used to identify all messages associated with a particular reliable session.</span></span> <span data-ttu-id="af569-173">各 WS-RM セッションには、GUID 形式の識別子があります。</span><span class="sxs-lookup"><span data-stu-id="af569-173">Each WS-RM session has an identifier, which is a GUID.</span></span>  
  
 <span data-ttu-id="af569-174">エンド ユーザーのコンピューターに保持される個人情報はありません。</span><span class="sxs-lookup"><span data-stu-id="af569-174">No personal information is retained on the end-user's machine.</span></span>  
  
## <a name="queued-channels"></a><span data-ttu-id="af569-175">キューに置かれたチャネル</span><span class="sxs-lookup"><span data-stu-id="af569-175">Queued Channels</span></span>  
 <span data-ttu-id="af569-176">キューは、送信元アプリケーションが送ったメッセージを受信側アプリケーションに代わって保存しておき、後で受信側アプリケーションに転送します。</span><span class="sxs-lookup"><span data-stu-id="af569-176">Queues store messages from a sending application on behalf of a receiving application and later forward these messages to the receiving application.</span></span> <span data-ttu-id="af569-177">受信側アプリケーションが一時的な場合なども、キューによって、送信元アプリケーションから受信側アプリケーションへのメッセージの転送を確実に実行できます。</span><span class="sxs-lookup"><span data-stu-id="af569-177">They help ensure the transfer of messages from sending applications to receiving applications when, for example, the receiving application is transient.</span></span> <span data-ttu-id="af569-178">WCF では、トランスポートとして Microsoft Message Queuing (MSMQ) を使用したキューのサポートを提供しています。</span><span class="sxs-lookup"><span data-stu-id="af569-178">WCF provides support for queuing by using Microsoft Message Queuing (MSMQ) as a transport.</span></span>  
  
 <span data-ttu-id="af569-179">キューに置かれたチャネル機能では、ヘッダーをメッセージに追加しません。</span><span class="sxs-lookup"><span data-stu-id="af569-179">The queued channels feature does not add headers to a message.</span></span> <span data-ttu-id="af569-180">代わりに、適切なメッセージ キューのメッセージ プロパティ セットを備えたメッセージ キューのメッセージを作成し、メッセージ キューのメソッドを呼び出して、メッセージ キューのキューにメッセージを追加します。</span><span class="sxs-lookup"><span data-stu-id="af569-180">Instead it creates a Message Queuing message with appropriate Message Queuing message properties set, and invokes Message Queuing methods to put the message in the Message Queuing queue.</span></span> <span data-ttu-id="af569-181">メッセージ キューは、Windows に付属しているオプション コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="af569-181">Message Queuing is an optional component that ships with Windows.</span></span>  
  
 <span data-ttu-id="af569-182">キューに置かれたチャネル機能では、キュー インフラストラクチャとしてメッセージ キューを使用するので、この機能によってエンド ユーザーのコンピューターに保持される情報はありません。</span><span class="sxs-lookup"><span data-stu-id="af569-182">No information is retained on the end-user's machine by the queued channels feature, because it uses Message Queuing as the queuing infrastructure.</span></span>  
  
## <a name="com-integration"></a><span data-ttu-id="af569-183">COM+ 統合</span><span class="sxs-lookup"><span data-stu-id="af569-183">COM+ Integration</span></span>  
 <span data-ttu-id="af569-184">この機能は、既存の COM および COM + 機能をラップして、WCF サービスと互換性のあるサービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="af569-184">This feature wraps existing COM and COM+ functionality to create services that are compatible with WCF services.</span></span> <span data-ttu-id="af569-185">この機能は、特定のヘッダーを使用せず、エンド ユーザーのコンピューターにデータを保持しません。</span><span class="sxs-lookup"><span data-stu-id="af569-185">This feature does not use specific headers and it does not retain data on the end-user's machine.</span></span>  
  
## <a name="com-service-moniker"></a><span data-ttu-id="af569-186">COM サービス モニカー</span><span class="sxs-lookup"><span data-stu-id="af569-186">COM Service Moniker</span></span>  
 <span data-ttu-id="af569-187">これにより、標準の WCF クライアントにアンマネージラッパーが提供されます。</span><span class="sxs-lookup"><span data-stu-id="af569-187">This provides an unmanaged wrapper to a standard WCF client.</span></span> <span data-ttu-id="af569-188">この機能は、ネットワーク上で特定のヘッダーを使用せず、コンピューターにデータを保持しません。</span><span class="sxs-lookup"><span data-stu-id="af569-188">This feature does not have specific headers on the wire nor does it persist data on the machine.</span></span>  
  
## <a name="peer-channel"></a><span data-ttu-id="af569-189">ピア チャネル</span><span class="sxs-lookup"><span data-stu-id="af569-189">Peer Channel</span></span>  
 <span data-ttu-id="af569-190">ピアチャネルを使用すると、WCF を使用してマルチパーティアプリケーションを開発できます。</span><span class="sxs-lookup"><span data-stu-id="af569-190">A peer channel enables development of multiparty applications using WCF.</span></span> <span data-ttu-id="af569-191">マルチパーティ メッセージングはメッシュのコンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="af569-191">Multiparty messaging occurs in the context of a mesh.</span></span> <span data-ttu-id="af569-192">メッシュは、ノードが参加できる名前によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="af569-192">Meshes are identified by a name that nodes can join.</span></span> <span data-ttu-id="af569-193">ピア チャネル内の各ノードは、ユーザー指定のポートで TCP リスナーを作成し、メッシュ内の他のノードとの接続を確立することによって、回復力を確保します。</span><span class="sxs-lookup"><span data-stu-id="af569-193">Each node in the peer channel creates a TCP listener at a user-specified port and establishes connections with other nodes in the mesh to ensure resiliency.</span></span> <span data-ttu-id="af569-194">メッシュ内の他のノードに接続するため、ノードは、リスナー アドレスやコンピューターの IP アドレスなど一部のデータをメッシュ内の他のノードと交換します。</span><span class="sxs-lookup"><span data-stu-id="af569-194">To connect to other nodes in the mesh, nodes also exchange some data, including the listener address and the machine's IP addresses, with other nodes in the mesh.</span></span> <span data-ttu-id="af569-195">メッシュ内で送信されるメッセージに送信者に関するセキュリティ情報を入れ、メッセージのなりすましと改ざんを防止することができます。</span><span class="sxs-lookup"><span data-stu-id="af569-195">Messages sent around in the mesh can contain security information that pertains to the sender to prevent message spoofing and tampering.</span></span>  
  
 <span data-ttu-id="af569-196">エンド ユーザーのコンピューターに個人情報は格納されません。</span><span class="sxs-lookup"><span data-stu-id="af569-196">No personal information is stored on the end-user's machine.</span></span>  
  
## <a name="it-professional-experience"></a><span data-ttu-id="af569-197">IT 専門家向けの機能</span><span class="sxs-lookup"><span data-stu-id="af569-197">IT Professional Experience</span></span>  
  
### <a name="tracing"></a><span data-ttu-id="af569-198">トレース</span><span class="sxs-lookup"><span data-stu-id="af569-198">Tracing</span></span>  
 <span data-ttu-id="af569-199">WCF インフラストラクチャの診断機能では、トランスポート層とサービスモデルレイヤーを通過するメッセージと、これらのメッセージに関連付けられているアクティビティとイベントがログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="af569-199">The diagnostics feature of the WCF infrastructure logs messages that pass through the transport and service model layers, and the activities and events associated with these messages.</span></span> <span data-ttu-id="af569-200">この機能は既定で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="af569-200">This feature is turned off by default.</span></span> <span data-ttu-id="af569-201">アプリケーションの構成ファイルを使用して有効にし、実行時に WCF WMI プロバイダーを使用してトレース動作を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="af569-201">It is enabled using the application’s configuration file and the tracing behavior may be modified using the WCF WMI provider at run time.</span></span> <span data-ttu-id="af569-202">有効にすると、トレース インフラストラクチャは、メッセージ、アクティビティ、および処理イベントを含んだ診断トレースを構成済みリスナーに出力します。</span><span class="sxs-lookup"><span data-stu-id="af569-202">When enabled, the tracing infrastructure emits a diagnostic trace that contains messages, activities, and processing events to configured listeners.</span></span> <span data-ttu-id="af569-203">出力の形式と場所は、管理者が選択するリスナー構成によって決まりますが、通常は XML 形式のファイルです。</span><span class="sxs-lookup"><span data-stu-id="af569-203">The format and location of the output are determined by the administrator’s listener configuration choices, but is typically an XML formatted file.</span></span> <span data-ttu-id="af569-204">管理者は、トレース ファイルでアクセス制御リスト (ACL) を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="af569-204">The administrator is responsible for setting the access control list (ACL) on the trace files.</span></span> <span data-ttu-id="af569-205">特に、Windows アクティベーション システム (WAS) でホストするとき、管理者は、ファイルがパブリック仮想ルート ディレクトリから提供されていないことを確認する必要があります (提供されることを望まない場合)。</span><span class="sxs-lookup"><span data-stu-id="af569-205">In particular, when hosted by Windows Activation System (WAS), the administrator should make sure the files are not served from the public virtual root directory if that is not desired.</span></span>  
  
 <span data-ttu-id="af569-206">トレースには、次の2種類があります。次のセクションで説明するメッセージログとサービスモデル診断トレース。</span><span class="sxs-lookup"><span data-stu-id="af569-206">There are two types of tracing: Message logging and Service Model diagnostic tracing, described in the following section.</span></span> <span data-ttu-id="af569-207">この 2 つのトレースは、それぞれ <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> と <xref:System.ServiceModel> というトレース ソースから構成されます。</span><span class="sxs-lookup"><span data-stu-id="af569-207">Each type is configured through its own trace source: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> and <xref:System.ServiceModel>.</span></span> <span data-ttu-id="af569-208">このログ トレース ソースは両方とも、アプリケーションにローカルなデータを取り込みます。</span><span class="sxs-lookup"><span data-stu-id="af569-208">Both of these logging trace sources capture data that is local to the application.</span></span>  
  
### <a name="message-logging"></a><span data-ttu-id="af569-209">メッセージ ログ</span><span class="sxs-lookup"><span data-stu-id="af569-209">Message Logging</span></span>  
 <span data-ttu-id="af569-210">メッセージ ログのトレース ソース (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) によって管理者は、システムを通過するメッセージをログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="af569-210">The message logging trace source (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) allows an administrator to log the messages that flow through the system.</span></span> <span data-ttu-id="af569-211">ユーザーは構成によって、メッセージ全体またはメッセージ ヘッダーだけをログに記録するかどうか、トランスポート レイヤーまたはサービス モデル レイヤーでログに記録するかどうか、および形式が正しくないメッセージをログに記録するかどうかを設定できます。</span><span class="sxs-lookup"><span data-stu-id="af569-211">Through configuration, the user may decide to log entire messages or message headers only, whether to log at the transport and/or service model layers, and whether to include malformed messages.</span></span> <span data-ttu-id="af569-212">また、ユーザーは、フィルター処理を設定して、ログに記録するメッセージを制限できます。</span><span class="sxs-lookup"><span data-stu-id="af569-212">Also, the user may configure filtering to restrict which messages are logged.</span></span>  
  
 <span data-ttu-id="af569-213">既定では、メッセージ ログは無効になっています。</span><span class="sxs-lookup"><span data-stu-id="af569-213">By default, message logging is disabled.</span></span> <span data-ttu-id="af569-214">ローカル コンピューターの管理者は、アプリケーション レベルの管理者がメッセージ ログを有効にするのを防止できます。</span><span class="sxs-lookup"><span data-stu-id="af569-214">The local machine administrator can prevent the application-level administrator from turning message logging on.</span></span>  
  
#### <a name="encrypted-and-decrypted-message-logging"></a><span data-ttu-id="af569-215">暗号化および復号化されるメッセージ ログ</span><span class="sxs-lookup"><span data-stu-id="af569-215">Encrypted and Decrypted Message Logging</span></span>  
 <span data-ttu-id="af569-216">メッセージは、以下に説明するようにログに記録され、暗号化および復号化されます。</span><span class="sxs-lookup"><span data-stu-id="af569-216">Messages are logged, encrypted, or decrypted, as described in the following terms.</span></span>  
  
 <span data-ttu-id="af569-217">トランスポート ログ</span><span class="sxs-lookup"><span data-stu-id="af569-217">Transport Logging</span></span>  
 <span data-ttu-id="af569-218">トランスポート レベルで送受信されるメッセージをログに記録します。</span><span class="sxs-lookup"><span data-stu-id="af569-218">Logs messages received and sent at the transport level.</span></span> <span data-ttu-id="af569-219">このメッセージは、すべてのヘッダーを含んでいて、ネットワーク上に送信される前と受信されるときに暗号化できます。</span><span class="sxs-lookup"><span data-stu-id="af569-219">These messages contain all headers, and may be encrypted before being sent on the wire and when being received.</span></span>  
  
 <span data-ttu-id="af569-220">メッセージがネットワーク上に送信される前と受信されるときに暗号化される場合、そのメッセージは暗号化されたままログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="af569-220">If messages are encrypted before being sent on the wire and when they are received, they are logged encrypted as well.</span></span> <span data-ttu-id="af569-221">例外は、セキュリティ プロトコル (https) を使用する場合です。メッセージは、ネットワーク上で暗号化されている場合でも、送信前と受信後は復号化された状態でログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="af569-221">An exception is when a security protocol is used (https): they are then logged decrypted before being sent and after being received even if they are encrypted on the wire.</span></span>  
  
 <span data-ttu-id="af569-222">サービス ログ</span><span class="sxs-lookup"><span data-stu-id="af569-222">Service Logging</span></span>  
 <span data-ttu-id="af569-223">チャネル ヘッダー処理が実行された後、ユーザー コードを入力する直前と直後に、サービス モデル レベルで送受信されるメッセージをログに記録します。</span><span class="sxs-lookup"><span data-stu-id="af569-223">Logs messages received or sent at the service model level, after channel header processing has occurred, just before and after entering user code.</span></span>  
  
 <span data-ttu-id="af569-224">このレベルでログに記録されるメッセージは、ネットワーク上でセキュリティ保護され、暗号化されている場合でも復号化されます。</span><span class="sxs-lookup"><span data-stu-id="af569-224">Messages logged at this level are decrypted even if they were secured and encrypted on the wire.</span></span>  
  
 <span data-ttu-id="af569-225">形式が正しくないメッセージのログ</span><span class="sxs-lookup"><span data-stu-id="af569-225">Malformed Message Logging</span></span>  
 <span data-ttu-id="af569-226">WCF インフラストラクチャが理解または処理できないメッセージをログに記録します。</span><span class="sxs-lookup"><span data-stu-id="af569-226">Logs messages that the WCF infrastructure cannot understand or process.</span></span>  
  
 <span data-ttu-id="af569-227">メッセージは、暗号化の有無を問わず、そのままの状態でログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="af569-227">Messages are logged as-is, that is, encrypted or not</span></span>  
  
 <span data-ttu-id="af569-228">暗号化されていない形式または暗号化されていない形式でメッセージをログに記録する場合、既定では、WCF は、メッセージをログに記録する前に、セキュリティキーや個人情報を削除します</span><span class="sxs-lookup"><span data-stu-id="af569-228">When messages are logged in decrypted or unencrypted form, by default WCF removes security keys and potentially personal information from the messages before logging them.</span></span> <span data-ttu-id="af569-229">次のセクションでは、削除される情報と削除が実行される状況について説明します。</span><span class="sxs-lookup"><span data-stu-id="af569-229">The next sections describe what information is removed, and when.</span></span> <span data-ttu-id="af569-230">キーと個人情報の可能性がある情報をログに記録するには、コンピューターの管理者とアプリケーションを配置するユーザーの両方が、所定の構成操作を実行して既定の動作を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="af569-230">The machine administrator and application deployer must both take certain configuration actions to change the default behavior to log keys and potentially personal information.</span></span>  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="af569-231">復号化されたまたは暗号化されていないメッセージをログに記録するときにメッセージ ヘッダーから削除される情報</span><span class="sxs-lookup"><span data-stu-id="af569-231">Information Removed from Message Headers When Logging Decrypted/Unencrypted Messages</span></span>  
 <span data-ttu-id="af569-232">メッセージが復号化された状態または暗号化されていない状態でログに記録される場合、既定ではメッセージがログに記録される前に、セキュリティ キーと個人情報の可能性がある情報がメッセージ ヘッダーとメッセージ本文から削除されます。</span><span class="sxs-lookup"><span data-stu-id="af569-232">When messages are logged in decrypted/unencrypted form, security keys and potentially personal information are removed by default from message headers and message bodies before they are logged.</span></span> <span data-ttu-id="af569-233">次の一覧は、WCF がキーおよび可能性のある個人情報を考慮することを示しています。</span><span class="sxs-lookup"><span data-stu-id="af569-233">The following list shows what WCF considers keys and potentially personal information.</span></span>  
  
 <span data-ttu-id="af569-234">削除されるキー :</span><span class="sxs-lookup"><span data-stu-id="af569-234">Keys that are removed:</span></span>  
  
 <span data-ttu-id="af569-235">xmlns: wst = "http://schemas.xmlsoap.org/ws/2004/04/trust" と xmlns: wst = "http://schemas.xmlsoap.org/ws/2005/02/trust" の \-</span><span class="sxs-lookup"><span data-stu-id="af569-235">\- For xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"</span></span>  
  
 <span data-ttu-id="af569-236">wst:BinarySecret</span><span class="sxs-lookup"><span data-stu-id="af569-236">wst:BinarySecret</span></span>  
  
 <span data-ttu-id="af569-237">wst:Entropy</span><span class="sxs-lookup"><span data-stu-id="af569-237">wst:Entropy</span></span>  
  
 <span data-ttu-id="af569-238">xmlns: wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" と xmlns: wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd" の \-</span><span class="sxs-lookup"><span data-stu-id="af569-238">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="af569-239">wsse:Password</span><span class="sxs-lookup"><span data-stu-id="af569-239">wsse:Password</span></span>  
  
 <span data-ttu-id="af569-240">wsse:Nonce</span><span class="sxs-lookup"><span data-stu-id="af569-240">wsse:Nonce</span></span>  
  
 <span data-ttu-id="af569-241">削除される個人情報の可能性がある情報 :</span><span class="sxs-lookup"><span data-stu-id="af569-241">Potentially personal information that is removed:</span></span>  
  
 <span data-ttu-id="af569-242">xmlns: wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" と xmlns: wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd" の \-</span><span class="sxs-lookup"><span data-stu-id="af569-242">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="af569-243">wsse:Username</span><span class="sxs-lookup"><span data-stu-id="af569-243">wsse:Username</span></span>  
  
 <span data-ttu-id="af569-244">wsse:BinarySecurityToken</span><span class="sxs-lookup"><span data-stu-id="af569-244">wsse:BinarySecurityToken</span></span>  
  
 <span data-ttu-id="af569-245">xmlns: saml = "urn: oasis: names: tc: SAML: 1.0: assertion" の \- は、太字 (下) の項目が削除されます。</span><span class="sxs-lookup"><span data-stu-id="af569-245">\- For xmlns:saml="urn:oasis:names:tc:SAML:1.0:assertion" the items in bold (below) are removed:</span></span>  
  
 <span data-ttu-id="af569-246">\<アサーション</span><span class="sxs-lookup"><span data-stu-id="af569-246">\<Assertion</span></span>  
  
 <span data-ttu-id="af569-247">MajorVersion="1"</span><span class="sxs-lookup"><span data-stu-id="af569-247">MajorVersion="1"</span></span>  
  
 <span data-ttu-id="af569-248">MinorVersion="1"</span><span class="sxs-lookup"><span data-stu-id="af569-248">MinorVersion="1"</span></span>  
  
 <span data-ttu-id="af569-249">AssertionId="[ID]"</span><span class="sxs-lookup"><span data-stu-id="af569-249">AssertionId="[ID]"</span></span>  
  
 <span data-ttu-id="af569-250">Issuer="[string]"</span><span class="sxs-lookup"><span data-stu-id="af569-250">Issuer="[string]"</span></span>  
  
 <span data-ttu-id="af569-251">IssueInstant="[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="af569-251">IssueInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="af569-252">\<条件 NotBefore = "[dateTime]" NotOnOrAfter = "[dateTime]" ></span><span class="sxs-lookup"><span data-stu-id="af569-252">\<Conditions NotBefore="[dateTime]" NotOnOrAfter="[dateTime]"></span></span>  
  
 <span data-ttu-id="af569-253">\<AudienceRestrictionCondition></span><span class="sxs-lookup"><span data-stu-id="af569-253">\<AudienceRestrictionCondition></span></span>  
  
 <span data-ttu-id="af569-254">\<オーディエンス > [uri]\</対象ユーザー > +</span><span class="sxs-lookup"><span data-stu-id="af569-254">\<Audience>[uri]\</Audience>+</span></span>  
  
 <span data-ttu-id="af569-255">\</AudienceRestrictionCondition>\*</span><span class="sxs-lookup"><span data-stu-id="af569-255">\</AudienceRestrictionCondition>\*</span></span>  
  
 <span data-ttu-id="af569-256">\<DoNotCacheCondition />\*</span><span class="sxs-lookup"><span data-stu-id="af569-256">\<DoNotCacheCondition />\*</span></span>  
  
 <span data-ttu-id="af569-257"><\!--抽象基本データ型</span><span class="sxs-lookup"><span data-stu-id="af569-257"><\!-- abstract base type</span></span>  
  
 <span data-ttu-id="af569-258">\<条件/> \*</span><span class="sxs-lookup"><span data-stu-id="af569-258">\<Condition />\*</span></span>  
  
 -->  
  
 <span data-ttu-id="af569-259">\</条件 >?</span><span class="sxs-lookup"><span data-stu-id="af569-259">\</Conditions>?</span></span>  
  
 <span data-ttu-id="af569-260">\<通知 ></span><span class="sxs-lookup"><span data-stu-id="af569-260">\<Advice></span></span>  
  
 <span data-ttu-id="af569-261">\<AssertionIDReference > [ID]\</AssertionIDReference > \*</span><span class="sxs-lookup"><span data-stu-id="af569-261">\<AssertionIDReference>[ID]\</AssertionIDReference>\*</span></span>  
  
 <span data-ttu-id="af569-262">\<Assertion > [assertion]\</assertion > \*</span><span class="sxs-lookup"><span data-stu-id="af569-262">\<Assertion>[assertion]\</Assertion>\*</span></span>  
  
 <span data-ttu-id="af569-263">[any]\*</span><span class="sxs-lookup"><span data-stu-id="af569-263">[any]\*</span></span>  
  
 <span data-ttu-id="af569-264">\</アドバイス > ですか?</span><span class="sxs-lookup"><span data-stu-id="af569-264">\</Advice>?</span></span>  
  
 <span data-ttu-id="af569-265"><\!--抽象基本型</span><span class="sxs-lookup"><span data-stu-id="af569-265"><\!-- Abstract base types</span></span>  
  
 <span data-ttu-id="af569-266">\<ステートメント/> \*</span><span class="sxs-lookup"><span data-stu-id="af569-266">\<Statement />\*</span></span>  
  
 <span data-ttu-id="af569-267">\<SubjectStatement></span><span class="sxs-lookup"><span data-stu-id="af569-267">\<SubjectStatement></span></span>  
  
 <span data-ttu-id="af569-268">\<サブジェクト ></span><span class="sxs-lookup"><span data-stu-id="af569-268">\<Subject></span></span>  
  
 `<NameIdentifier`  
  
 `NameQualifier="[string]"?`  
  
 `Format="[uri]"?`  
  
 `>`  
  
 `[string]`  
  
 `</NameIdentifier>?`  
  
 <span data-ttu-id="af569-269">\<SubjectConfirmation ></span><span class="sxs-lookup"><span data-stu-id="af569-269">\<SubjectConfirmation></span></span>  
  
 <span data-ttu-id="af569-270">\<ConfirmationMethod > [anyUri]\</ConfirmationMethod > +</span><span class="sxs-lookup"><span data-stu-id="af569-270">\<ConfirmationMethod>[anyUri]\</ConfirmationMethod>+</span></span>  
  
 <span data-ttu-id="af569-271">\<SubjectConfirmationData > [any]\</SubjectConfirmationData >?</span><span class="sxs-lookup"><span data-stu-id="af569-271">\<SubjectConfirmationData>[any]\</SubjectConfirmationData>?</span></span>  
  
 <span data-ttu-id="af569-272">\<ds:KeyInfo>...\</ds:KeyInfo>?</span><span class="sxs-lookup"><span data-stu-id="af569-272">\<ds:KeyInfo>...\</ds:KeyInfo>?</span></span>  
  
 <span data-ttu-id="af569-273">\</> 確認しますか?</span><span class="sxs-lookup"><span data-stu-id="af569-273">\</SubjectConfirmation>?</span></span>  
  
 <span data-ttu-id="af569-274">\</Subject></span><span class="sxs-lookup"><span data-stu-id="af569-274">\</Subject></span></span>  
  
 <span data-ttu-id="af569-275">\</SubjectStatement>\*</span><span class="sxs-lookup"><span data-stu-id="af569-275">\</SubjectStatement>\*</span></span>  
  
 -->  
  
 <span data-ttu-id="af569-276">\<AuthenticationStatement</span><span class="sxs-lookup"><span data-stu-id="af569-276">\<AuthenticationStatement</span></span>  
  
 <span data-ttu-id="af569-277">AuthenticationMethod="[uri]"</span><span class="sxs-lookup"><span data-stu-id="af569-277">AuthenticationMethod="[uri]"</span></span>  
  
 <span data-ttu-id="af569-278">AuthenticationInstant="[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="af569-278">AuthenticationInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="af569-279">[Subject]</span><span class="sxs-lookup"><span data-stu-id="af569-279">[Subject]</span></span>  
  
 `<SubjectLocality`  
  
 `IPAddress="[string]"?`  
  
 `DNSAddress="[string]"?`  
  
 `/>?`  
  
 <span data-ttu-id="af569-280">< AuthorityBinding</span><span class="sxs-lookup"><span data-stu-id="af569-280"><AuthorityBinding</span></span>  
  
 <span data-ttu-id="af569-281">AuthorityKind="[QName]"</span><span class="sxs-lookup"><span data-stu-id="af569-281">AuthorityKind="[QName]"</span></span>  
  
 <span data-ttu-id="af569-282">Location="[uri]"</span><span class="sxs-lookup"><span data-stu-id="af569-282">Location="[uri]"</span></span>  
  
 <span data-ttu-id="af569-283">Binding="[uri]"</span><span class="sxs-lookup"><span data-stu-id="af569-283">Binding="[uri]"</span></span>  
  
 />*  
  
 <span data-ttu-id="af569-284">\</AuthenticationStatement>\*</span><span class="sxs-lookup"><span data-stu-id="af569-284">\</AuthenticationStatement>\*</span></span>  
  
 <span data-ttu-id="af569-285">\<AttributeStatement></span><span class="sxs-lookup"><span data-stu-id="af569-285">\<AttributeStatement></span></span>  
  
 <span data-ttu-id="af569-286">[Subject]</span><span class="sxs-lookup"><span data-stu-id="af569-286">[Subject]</span></span>  
  
 <span data-ttu-id="af569-287">\<属性</span><span class="sxs-lookup"><span data-stu-id="af569-287">\<Attribute</span></span>  
  
 <span data-ttu-id="af569-288">AttributeName="[string]"</span><span class="sxs-lookup"><span data-stu-id="af569-288">AttributeName="[string]"</span></span>  
  
 <span data-ttu-id="af569-289">AttributeNamespace="[uri]"</span><span class="sxs-lookup"><span data-stu-id="af569-289">AttributeNamespace="[uri]"</span></span>  
  
 >  
  
 `<AttributeValue>[any]</AttributeValue>+`  
  
 <span data-ttu-id="af569-290">\</属性 > +</span><span class="sxs-lookup"><span data-stu-id="af569-290">\</Attribute>+</span></span>  
  
 <span data-ttu-id="af569-291">\</AttributeStatement>\*</span><span class="sxs-lookup"><span data-stu-id="af569-291">\</AttributeStatement>\*</span></span>  
  
 <span data-ttu-id="af569-292">\<AuthorizationDecisionStatement</span><span class="sxs-lookup"><span data-stu-id="af569-292">\<AuthorizationDecisionStatement</span></span>  
  
 <span data-ttu-id="af569-293">Resource="[uri]"</span><span class="sxs-lookup"><span data-stu-id="af569-293">Resource="[uri]"</span></span>  
  
 <span data-ttu-id="af569-294">Decision="[Permit&#124;Deny&#124;Indeterminate]"</span><span class="sxs-lookup"><span data-stu-id="af569-294">Decision="[Permit&#124;Deny&#124;Indeterminate]"</span></span>  
  
 >  
  
 <span data-ttu-id="af569-295">[Subject]</span><span class="sxs-lookup"><span data-stu-id="af569-295">[Subject]</span></span>  
  
 <span data-ttu-id="af569-296">\<Action Namespace = "[uri]" > [string]\</Action > +</span><span class="sxs-lookup"><span data-stu-id="af569-296">\<Action Namespace="[uri]">[string]\</Action>+</span></span>  
  
 <span data-ttu-id="af569-297">証拠 > の \<</span><span class="sxs-lookup"><span data-stu-id="af569-297">\<Evidence></span></span>  
  
 <span data-ttu-id="af569-298">\<AssertionIDReference > [ID]\</AssertionIDReference > +</span><span class="sxs-lookup"><span data-stu-id="af569-298">\<AssertionIDReference>[ID]\</AssertionIDReference>+</span></span>  
  
 <span data-ttu-id="af569-299">\<Assertion > [assertion]\</assertion > +</span><span class="sxs-lookup"><span data-stu-id="af569-299">\<Assertion>[assertion]\</Assertion>+</span></span>  
  
 <span data-ttu-id="af569-300">\</Evidence>?</span><span class="sxs-lookup"><span data-stu-id="af569-300">\</Evidence>?</span></span>  
  
 <span data-ttu-id="af569-301">\</AuthorizationDecisionStatement>\*</span><span class="sxs-lookup"><span data-stu-id="af569-301">\</AuthorizationDecisionStatement>\*</span></span>  
  
 <span data-ttu-id="af569-302">\</Assertion></span><span class="sxs-lookup"><span data-stu-id="af569-302">\</Assertion></span></span>  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="af569-303">復号化されたまたは暗号化されていないメッセージをログに記録するときにメッセージ本文から削除される情報</span><span class="sxs-lookup"><span data-stu-id="af569-303">Information Removed from Message Bodies When Logging Decrypted/Unencrypted Messages</span></span>  
 <span data-ttu-id="af569-304">前に説明したように、WCF では、暗号化された暗号化されていないメッセージや暗号化されていないメッセージのメッセージヘッダーから、キーと既知の可能性がある</span><span class="sxs-lookup"><span data-stu-id="af569-304">As previously described, WCF removes keys and known potentially personal information from message headers for logged decrypted/unencrypted messages.</span></span> <span data-ttu-id="af569-305">さらに、WCF は、キー交換に関連するセキュリティメッセージについて説明する次の一覧の本文要素とアクションの本文から、キーと既知の可能性がある個人情報を削除します。</span><span class="sxs-lookup"><span data-stu-id="af569-305">In addition, WCF removes keys and known potentially personal information from message bodies for the body elements and actions in the following list, which describe security messages involved in key exchange.</span></span>  
  
 <span data-ttu-id="af569-306">次の名前空間の場合 :</span><span class="sxs-lookup"><span data-stu-id="af569-306">For the following namespaces:</span></span>  
  
 <span data-ttu-id="af569-307">xmlns: wst = "http://schemas.xmlsoap.org/ws/2004/04/trust" と xmlns: wst = "http://schemas.xmlsoap.org/ws/2005/02/trust" (たとえば、使用可能なアクションがない場合)</span><span class="sxs-lookup"><span data-stu-id="af569-307">xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust" (for example, if no action available)</span></span>  
  
 <span data-ttu-id="af569-308">キー交換を伴うこの本文要素について情報が削除されます。</span><span class="sxs-lookup"><span data-stu-id="af569-308">Information is removed for these body elements, which involve key exchange:</span></span>  
  
 <span data-ttu-id="af569-309">wst:RequestSecurityToken</span><span class="sxs-lookup"><span data-stu-id="af569-309">wst:RequestSecurityToken</span></span>  
  
 <span data-ttu-id="af569-310">wst:RequestSecurityTokenResponse</span><span class="sxs-lookup"><span data-stu-id="af569-310">wst:RequestSecurityTokenResponse</span></span>  
  
 <span data-ttu-id="af569-311">wst:RequestSecurityTokenResponseCollection</span><span class="sxs-lookup"><span data-stu-id="af569-311">wst:RequestSecurityTokenResponseCollection</span></span>  
  
 <span data-ttu-id="af569-312">次の各アクションについても情報が削除されます。</span><span class="sxs-lookup"><span data-stu-id="af569-312">Information is also removed for each of the following Actions:</span></span>  
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Validate`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Validate`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Amend`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Amend`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT-Amend`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT-Amend`
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a><span data-ttu-id="af569-313">情報が削除されないアプリケーション固有のヘッダーと本文データ</span><span class="sxs-lookup"><span data-stu-id="af569-313">No Information Is Removed from Application-specific Headers and Body Data</span></span>  
 <span data-ttu-id="af569-314">WCF では、アプリケーション固有のヘッダー (クエリ文字列など) や本文データ (クレジットカード番号など) の個人情報は追跡されません。</span><span class="sxs-lookup"><span data-stu-id="af569-314">WCF does not track personal information in application-specific headers (for example, query strings) or body data (for example, credit card number).</span></span>  
  
 <span data-ttu-id="af569-315">メッセージ ログが有効な場合、アプリケーション固有のヘッダーと本文情報にある個人情報はログに表示される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="af569-315">When message logging is on, personal information in application-specific headers and body information may be visible in the logs.</span></span> <span data-ttu-id="af569-316">そのため、この場合もアプリケーションを配置するユーザーが、構成ファイルとログ ファイルに対する ACL を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="af569-316">Again, the application deployer is responsible for setting the ACLs on the configuration and log files.</span></span> <span data-ttu-id="af569-317">また、この情報を表示しない場合にログを無効にすることや、情報がログに記録された後で、この情報をログ ファイルからフィルターで除外することもできます。</span><span class="sxs-lookup"><span data-stu-id="af569-317">He also can turn off logging if he does not want this information to be visible, or he may filter out this information from the log files after it is logged.</span></span>  
  
### <a name="service-model-tracing"></a><span data-ttu-id="af569-318">サービス モデル トレース</span><span class="sxs-lookup"><span data-stu-id="af569-318">Service Model Tracing</span></span>  
 <span data-ttu-id="af569-319">サービス モデルのトレース ソース (<xref:System.ServiceModel>) によって、メッセージ処理に関するアクティビティとイベントのトレースを実行できます。</span><span class="sxs-lookup"><span data-stu-id="af569-319">The Service Model trace source (<xref:System.ServiceModel>) enables tracing of activities and events related to message processing.</span></span> <span data-ttu-id="af569-320">この機能では、<xref:System.Diagnostics> から .NET Framework 診断機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="af569-320">This feature uses the .NET Framework diagnostic functionality from <xref:System.Diagnostics>.</span></span> <span data-ttu-id="af569-321"><xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> プロパティと同様、場所とその ACL は、.NET Framework アプリケーションの構成ファイルを使用してユーザーが設定できます。</span><span class="sxs-lookup"><span data-stu-id="af569-321">As with the <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> property, the location and its ACL are user-configurable using .NET Framework application configuration files.</span></span> <span data-ttu-id="af569-322">メッセージ ログと同様、管理者がトレースを有効にするときに必ずファイルの場所が設定されるので、管理者は ACL を制御できます。</span><span class="sxs-lookup"><span data-stu-id="af569-322">As with message logging, the file location is always configured when the administrator enables tracing; thus, the administrator controls the ACL.</span></span>  
  
 <span data-ttu-id="af569-323">スコープ内のメッセージに含まれるメッセージ ヘッダーをトレースします。</span><span class="sxs-lookup"><span data-stu-id="af569-323">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="af569-324">前のセクションで説明した、メッセージ ヘッダーに含まれる個人情報の可能性がある情報を非表示にする場合と同じ規則が適用されます。既定では、先に示した個人情報はトレース時にヘッダーから削除されます。</span><span class="sxs-lookup"><span data-stu-id="af569-324">The same rules for hiding potentially personal information in message headers in the previous section apply: the personal information previously identified is removed by default from the headers in traces.</span></span> <span data-ttu-id="af569-325">個人情報の可能性がある情報をログに記録するには、コンピューターの管理者とアプリケーションを配置するユーザーの両方が構成を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="af569-325">Both the machine administrator and the application deployer must modify the configuration in order to log potentially personal information.</span></span> <span data-ttu-id="af569-326">ただし、アプリケーション固有のヘッダーにある個人情報はトレース時にログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="af569-326">However, personal information contained in application-specific headers is logged in traces.</span></span> <span data-ttu-id="af569-327">アプリケーションを配置するユーザーは、構成ファイルとトレース ファイルに対する ACL を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="af569-327">The application deployer is responsible for setting the ACLs on the configuration and trace files.</span></span> <span data-ttu-id="af569-328">また、この情報を表示しない場合にトレースを無効にすることや、情報がログに記録された後で、この情報をトレース ファイルからフィルターで除外することもできます。</span><span class="sxs-lookup"><span data-stu-id="af569-328">He also can turn off tracing if he does not want this information to be visible, or he can filter out this information from the trace files after it is logged.</span></span>  
  
 <span data-ttu-id="af569-329">ServiceModel トレースの一部として、一意な ID (呼び出されたアクティビティ ID、通常は GUID) は、インフラストラクチャのさまざまな部分を通過するメッセージとして、異なる複数のアクティビティを結合します。</span><span class="sxs-lookup"><span data-stu-id="af569-329">As part of ServiceModel Tracing, Unique IDs (called Activity IDs, and typically a GUID) link different activities together as a message flows through different parts of the infrastructure.</span></span>  
  
#### <a name="custom-trace-listeners"></a><span data-ttu-id="af569-330">カスタム トレース リスナー</span><span class="sxs-lookup"><span data-stu-id="af569-330">Custom Trace Listeners</span></span>  
 <span data-ttu-id="af569-331">メッセージ ログとトレースの両方で、カスタム トレース リスナーを構成できます。このリスナーは、ネットワーク上で、リモート データベースなどにトレースとメッセージを送信できます。</span><span class="sxs-lookup"><span data-stu-id="af569-331">For both message logging and tracing, a custom trace listener can be configured, which can send traces and messages on the wire (for example, to a remote database).</span></span> <span data-ttu-id="af569-332">アプリケーションを配置するユーザーは、カスタム リスナーを構成するか、ユーザーがリスナーを構成できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="af569-332">The application deployer is responsible for configuring custom listeners or enabling users to do so.</span></span> <span data-ttu-id="af569-333">また、遠隔地で公開される個人情報に対しても責任があり、この遠隔地に ACL を適切に適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="af569-333">He is also responsible for any personal information exposed at the remote location, and for properly applying ACLs to this location.</span></span>  
  
### <a name="other-features-for-it-professionals"></a><span data-ttu-id="af569-334">IT 専門家向けのその他の機能</span><span class="sxs-lookup"><span data-stu-id="af569-334">Other features for IT Professionals</span></span>  
 <span data-ttu-id="af569-335">WCF には、WMI (Windows に付属) を介して WCF インフラストラクチャの構成情報を公開する WMI プロバイダーがあります。</span><span class="sxs-lookup"><span data-stu-id="af569-335">WCF has a WMI provider that exposes the WCF infrastructure configuration information through WMI (shipped with Windows).</span></span> <span data-ttu-id="af569-336">既定では、WMI インターフェイスは管理者が利用できます。</span><span class="sxs-lookup"><span data-stu-id="af569-336">By default, the WMI interface is available to administrators.</span></span>  
  
 <span data-ttu-id="af569-337">WCF 構成では、.NET Framework 構成メカニズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="af569-337">WCF configuration uses the .NET Framework configuration mechanism.</span></span> <span data-ttu-id="af569-338">構成ファイルはコンピューターに保存されます。</span><span class="sxs-lookup"><span data-stu-id="af569-338">The configuration files are stored on the machine.</span></span> <span data-ttu-id="af569-339">アプリケーション開発者と管理者が、アプリケーションの要件に応じて構成ファイルと ACL を作成します。</span><span class="sxs-lookup"><span data-stu-id="af569-339">The application developer and the administrator create the configuration files and ACL for each of the application's requirements.</span></span> <span data-ttu-id="af569-340">構成ファイルには、エンドポイント アドレスと証明書ストア内の証明書へのリンクを入れることができます。</span><span class="sxs-lookup"><span data-stu-id="af569-340">A configuration file can contain endpoint addresses and links to certificates in the certificate store.</span></span> <span data-ttu-id="af569-341">証明書を使用してアプリケーション データを提供し、アプリケーションによって使用される機能の各プロパティを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="af569-341">The certificates can be used to provide application data to configure various properties of the features used by the application.</span></span>  
  
 <span data-ttu-id="af569-342">また、WCF では、<xref:System.Environment.FailFast%2A> メソッドを呼び出すことによって .NET Framework プロセスダンプ機能も使用します。</span><span class="sxs-lookup"><span data-stu-id="af569-342">WCF also uses the .NET Framework process dump functionality by calling the <xref:System.Environment.FailFast%2A> method.</span></span>  
  
### <a name="it-pro-tools"></a><span data-ttu-id="af569-343">IT 専門家のツール</span><span class="sxs-lookup"><span data-stu-id="af569-343">IT Pro Tools</span></span>  
 <span data-ttu-id="af569-344">また、WCF には、Windows SDK に付属する次の IT プロフェッショナル向けツールも用意されています。</span><span class="sxs-lookup"><span data-stu-id="af569-344">WCF also provides the following IT professional tools, which ship in the Windows SDK.</span></span>  
  
#### <a name="svctraceviewerexe"></a><span data-ttu-id="af569-345">SvcTraceViewer.exe</span><span class="sxs-lookup"><span data-stu-id="af569-345">SvcTraceViewer.exe</span></span>  
 <span data-ttu-id="af569-346">ビューアーには、WCF トレースファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="af569-346">The viewer displays WCF trace files.</span></span> <span data-ttu-id="af569-347">このビューアーは、トレースに含まれているすべての情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="af569-347">The viewer shows whatever information is contained in the traces.</span></span>  
  
#### <a name="svcconfigeditorexe"></a><span data-ttu-id="af569-348">SvcConfigEditor.exe</span><span class="sxs-lookup"><span data-stu-id="af569-348">SvcConfigEditor.exe</span></span>  
 <span data-ttu-id="af569-349">ユーザーは、エディターを使用して、WCF 構成ファイルを作成および編集できます。</span><span class="sxs-lookup"><span data-stu-id="af569-349">The editor allows the user to create and edit WCF configuration files.</span></span> <span data-ttu-id="af569-350">このエディターは、構成ファイルに含まれているすべての情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="af569-350">The editor shows whatever information is contained in the configuration files.</span></span> <span data-ttu-id="af569-351">テキスト エディターでも同じタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="af569-351">The same task can be accomplished with a text editor.</span></span>  
  
#### <a name="servicemodel_reg"></a><span data-ttu-id="af569-352">ServiceModel_Reg</span><span class="sxs-lookup"><span data-stu-id="af569-352">ServiceModel_Reg</span></span>  
 <span data-ttu-id="af569-353">このツールでは、コンピューター上の ServiceModel のインストールを管理できます。</span><span class="sxs-lookup"><span data-stu-id="af569-353">This tool allows the user to manage ServiceModel installs on a machine.</span></span> <span data-ttu-id="af569-354">このツールでは、実行時にステータスメッセージがコンソールウィンドウに表示され、プロセス内で WCF インストールの構成に関する情報が表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="af569-354">The tool displays status messages in a console window when it runs and, in the process, may display information about the configuration of the WCF installation.</span></span>  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a><span data-ttu-id="af569-355">WSATConfig.exe と WSATUI.dll</span><span class="sxs-lookup"><span data-stu-id="af569-355">WSATConfig.exe and WSATUI.dll</span></span>  
 <span data-ttu-id="af569-356">これらのツールを使用すると、IT 担当者は WCF で相互運用可能な ws-atomictransaction ネットワークサポートを構成できます。</span><span class="sxs-lookup"><span data-stu-id="af569-356">These tools allow IT Professionals to configure interoperable WS-AtomicTransaction network support in WCF.</span></span> <span data-ttu-id="af569-357">このツールは、レジストリに格納された最も一般的に使用される WS-AtomicTransaction 設定の値を表示し、ユーザーはこのツールを使用してその値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="af569-357">The tools display and allow the user to change the values of the most commonly used WS-AtomicTransaction settings stored in the registry.</span></span>  
  
## <a name="cross-cutting-features"></a><span data-ttu-id="af569-358">広範囲に使用できる機能</span><span class="sxs-lookup"><span data-stu-id="af569-358">Cross-cutting Features</span></span>  
 <span data-ttu-id="af569-359">次の機能は広範囲に使用できます。</span><span class="sxs-lookup"><span data-stu-id="af569-359">The following features are cross-cutting.</span></span> <span data-ttu-id="af569-360">つまり、前述の任意の機能と共に構成できます。</span><span class="sxs-lookup"><span data-stu-id="af569-360">That is, they can be composed with any of the preceding features.</span></span>  
  
### <a name="service-framework"></a><span data-ttu-id="af569-361">サービス フレームワーク</span><span class="sxs-lookup"><span data-stu-id="af569-361">Service Framework</span></span>  
 <span data-ttu-id="af569-362">ヘッダーには、インスタンス ID を入れることができます。このインスタンス ID は、メッセージを CLR クラスのインスタンスに関連付ける GUID です。</span><span class="sxs-lookup"><span data-stu-id="af569-362">Headers can contain an instance ID, which is a GUID that associates a message with an instance of a CLR class.</span></span>  
  
 <span data-ttu-id="af569-363">Web サービス記述言語 (WSDL) には、ポートの定義が入ります。</span><span class="sxs-lookup"><span data-stu-id="af569-363">The Web Services Description Language (WSDL) contains a definition of the port.</span></span> <span data-ttu-id="af569-364">各ポートには、エンドポイント アドレス、およびアプリケーションが使用するサービスを表すバインディングがあります。</span><span class="sxs-lookup"><span data-stu-id="af569-364">Each port has an endpoint address and a binding that represents the services used by the application.</span></span> <span data-ttu-id="af569-365">WSDL の公開は、構成を使用して無効にできます。</span><span class="sxs-lookup"><span data-stu-id="af569-365">Exposing WSDL can be turned off using configuration.</span></span> <span data-ttu-id="af569-366">コンピューターに保持される情報はありません。</span><span class="sxs-lookup"><span data-stu-id="af569-366">No information is retained on the machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af569-367">関連項目</span><span class="sxs-lookup"><span data-stu-id="af569-367">See also</span></span>

- [<span data-ttu-id="af569-368">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="af569-368">Windows Communication Foundation</span></span>](index.md)
- [<span data-ttu-id="af569-369">Security</span><span class="sxs-lookup"><span data-stu-id="af569-369">Security</span></span>](./feature-details/security.md)
