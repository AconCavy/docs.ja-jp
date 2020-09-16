---
title: WAS アクティベーション アーキテクチャ
ms.date: 03/30/2017
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
ms.openlocfilehash: 77cebede5827016c5c9660663c0491614ba0ef19
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545983"
---
# <a name="was-activation-architecture"></a><span data-ttu-id="7a60e-102">WAS アクティベーション アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="7a60e-102">WAS Activation Architecture</span></span>
<span data-ttu-id="7a60e-103">ここでは、Windows プロセス アクティブ化サービス (WAS とも呼ばれます) の各コンポーネントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7a60e-103">This topic itemizes and discusses the components of the Windows Process Activation Service (also known as WAS).</span></span>  
  
## <a name="activation-components"></a><span data-ttu-id="7a60e-104">アクティベーション コンポーネント</span><span class="sxs-lookup"><span data-stu-id="7a60e-104">Activation Components</span></span>  
 <span data-ttu-id="7a60e-105">WAS は、複数のアーキテクチャ コンポーネントで構成されます。</span><span class="sxs-lookup"><span data-stu-id="7a60e-105">WAS consists of several architectural components:</span></span>  
  
- <span data-ttu-id="7a60e-106">リスナー アダプター : </span><span class="sxs-lookup"><span data-stu-id="7a60e-106">Listener adapters.</span></span> <span data-ttu-id="7a60e-107">特定のネットワーク プロトコルでメッセージを受信し、WAS と通信して、受信メッセージを適切なワーカー プロセスにルーティングする Windows サービス。</span><span class="sxs-lookup"><span data-stu-id="7a60e-107">Windows services that receive messages on specific network protocols and communicate with WAS to route incoming messages to the correct worker process.</span></span>  
  
- <span data-ttu-id="7a60e-108">WAS : </span><span class="sxs-lookup"><span data-stu-id="7a60e-108">WAS.</span></span> <span data-ttu-id="7a60e-109">ワーカー プロセスの作成と有効期間を管理する Windows サービス。</span><span class="sxs-lookup"><span data-stu-id="7a60e-109">The Windows service that manages the creation and lifetime of worker processes.</span></span>  
  
- <span data-ttu-id="7a60e-110">汎用ワーカー プロセス実行可能ファイル (w3wp.exe)。</span><span class="sxs-lookup"><span data-stu-id="7a60e-110">The generic worker process executable (w3wp.exe).</span></span>  
  
- <span data-ttu-id="7a60e-111">アプリケーション マネージャー : </span><span class="sxs-lookup"><span data-stu-id="7a60e-111">Application manager.</span></span> <span data-ttu-id="7a60e-112">ワーカー プロセス内のアプリケーションをホストするアプリケーション ドメインの作成と有効期間を管理します。</span><span class="sxs-lookup"><span data-stu-id="7a60e-112">Manages the creation and lifetime of application domains that host applications within the worker process.</span></span>  
  
- <span data-ttu-id="7a60e-113">プロトコル ハンドラー : </span><span class="sxs-lookup"><span data-stu-id="7a60e-113">Protocol handlers.</span></span> <span data-ttu-id="7a60e-114">ワーカー プロセスで実行され、ワーカー プロセスと個々のリスナー アダプター間の通信を管理するプロトコル固有のコンポーネント。</span><span class="sxs-lookup"><span data-stu-id="7a60e-114">Protocol-specific components that run in the worker process and manage communication between the worker process and the individual listener adapters.</span></span> <span data-ttu-id="7a60e-115">プロトコル ハンドラーには、プロセス プロトコル ハンドラーと AppDomain プロトコル ハンドラーの 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="7a60e-115">Two types of protocol handlers exist: process protocol handlers and AppDomain protocol handlers.</span></span>  
  
 <span data-ttu-id="7a60e-116">ワーカー プロセス インスタンスをアクティブ化する場合、WAS は必要なプロセス プロトコル ハンドラーをワーカー プロセスに読み込み、アプリケーション マネージャーを使用して、アプリケーションをホストするアプリケーション ドメインを作成します。</span><span class="sxs-lookup"><span data-stu-id="7a60e-116">When WAS activates a worker process instance, it loads the process protocol handlers required into the worker process and uses the application manager to create an application domain to host the application.</span></span> <span data-ttu-id="7a60e-117">アプリケーション ドメインは、アプリケーションのコードと、アプリケーションが使用するネットワーク プロトコルに必要な AppDomain プロトコル ハンドラーを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="7a60e-117">The application domain loads the application’s code as well as the AppDomain protocol handlers that the network protocols used by the application require.</span></span>  
  
 ![WAS アーキテクチャを示すスクリーンショット。](./media/was-activation-architecture/windows-process-application-service-architecture.gif)  
  
### <a name="listener-adapters"></a><span data-ttu-id="7a60e-119">リスナー アダプター</span><span class="sxs-lookup"><span data-stu-id="7a60e-119">Listener Adapters</span></span>  
 <span data-ttu-id="7a60e-120">リスナー アダプターは個別の Windows サービスであり、リッスンするネットワーク プロトコルを使用して、メッセージ受信に使用されるネットワーク通信ロジックを実装します。</span><span class="sxs-lookup"><span data-stu-id="7a60e-120">Listener adapters are individual Windows services that implement the network communication logic used to receive messages using the network protocol on which they listen.</span></span> <span data-ttu-id="7a60e-121">次の表は、Windows Communication Foundation (WCF) プロトコルのリスナーアダプターの一覧です。</span><span class="sxs-lookup"><span data-stu-id="7a60e-121">The following table lists the listener adapters for Windows Communication Foundation (WCF) protocols.</span></span>  
  
|<span data-ttu-id="7a60e-122">リスナー アダプターのサービス名</span><span class="sxs-lookup"><span data-stu-id="7a60e-122">Listener adapter service name</span></span>|<span data-ttu-id="7a60e-123">Protocol</span><span class="sxs-lookup"><span data-stu-id="7a60e-123">Protocol</span></span>|<span data-ttu-id="7a60e-124">メモ</span><span class="sxs-lookup"><span data-stu-id="7a60e-124">Notes</span></span>|  
|-----------------------------------|--------------|-----------|  
|<span data-ttu-id="7a60e-125">W3SVC</span><span class="sxs-lookup"><span data-stu-id="7a60e-125">W3SVC</span></span>|<span data-ttu-id="7a60e-126">http</span><span class="sxs-lookup"><span data-stu-id="7a60e-126">http</span></span>|<span data-ttu-id="7a60e-127">IIS 7.0 と WCF の両方に対して HTTP アクティベーションを提供する共通コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="7a60e-127">Common component that provides HTTP activation for both IIS 7.0 and WCF.</span></span>|  
|<span data-ttu-id="7a60e-128">NetTcpActivator</span><span class="sxs-lookup"><span data-stu-id="7a60e-128">NetTcpActivator</span></span>|<span data-ttu-id="7a60e-129">net.tcp</span><span class="sxs-lookup"><span data-stu-id="7a60e-129">net.tcp</span></span>|<span data-ttu-id="7a60e-130">NetTcpPortSharing サービスに依存します。</span><span class="sxs-lookup"><span data-stu-id="7a60e-130">Depends on the NetTcpPortSharing service.</span></span>|  
|<span data-ttu-id="7a60e-131">NetPipeActivator</span><span class="sxs-lookup"><span data-stu-id="7a60e-131">NetPipeActivator</span></span>|<span data-ttu-id="7a60e-132">net.pipe</span><span class="sxs-lookup"><span data-stu-id="7a60e-132">net.pipe</span></span>||  
|<span data-ttu-id="7a60e-133">NetMsmqActivator</span><span class="sxs-lookup"><span data-stu-id="7a60e-133">NetMsmqActivator</span></span>|<span data-ttu-id="7a60e-134">net.msmq</span><span class="sxs-lookup"><span data-stu-id="7a60e-134">net.msmq</span></span>|<span data-ttu-id="7a60e-135">WCF ベースのメッセージキューアプリケーションで使用します。</span><span class="sxs-lookup"><span data-stu-id="7a60e-135">For use with WCF-based Message Queuing applications.</span></span>|  
|<span data-ttu-id="7a60e-136">NetMsmqActivator</span><span class="sxs-lookup"><span data-stu-id="7a60e-136">NetMsmqActivator</span></span>|<span data-ttu-id="7a60e-137">msmq.formatname</span><span class="sxs-lookup"><span data-stu-id="7a60e-137">msmq.formatname</span></span>|<span data-ttu-id="7a60e-138">既存のメッセージ キュー アプリケーションとの下位互換性を提供します。</span><span class="sxs-lookup"><span data-stu-id="7a60e-138">Provides backwards compatibility with existing Message Queuing applications.</span></span>|  
  
 <span data-ttu-id="7a60e-139">次の XML サンプルに示すように、特定プロトコルのリスナー アダプターは、インストール時に applicationHost.config ファイルに登録されます。</span><span class="sxs-lookup"><span data-stu-id="7a60e-139">Listener adapters for specific protocols are registered during installation in the applicationHost.config file, as shown in the following XML example.</span></span>  
  
```xml  
<system.applicationHost>  
    <listenerAdapters>  
        <add name="http" />  
        <add name="net.tcp"
          identity="S-1-5-80-3579033775-2824656752-1522793541-1960352512-462907086" />  
         <add name="net.pipe"
           identity="S-1-5-80-2943419899-937267781-4189664001-1229628381-3982115073" />  
          <add name="net.msmq"
            identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
           <add name="msmq.formatname"
             identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
    </listenerAdapters>  
</system.applicationHost>  
```  
  
### <a name="protocol-handlers"></a><span data-ttu-id="7a60e-140">プロトコル ハンドラー</span><span class="sxs-lookup"><span data-stu-id="7a60e-140">Protocol Handlers</span></span>  
 <span data-ttu-id="7a60e-141">特定のプロトコルのプロセス プロトコル ハンドラーと AppDomain プロトコル ハンドラーは、コンピューター レベルの Web.config ファイルに登録されます。</span><span class="sxs-lookup"><span data-stu-id="7a60e-141">Process and AppDomain protocol handlers for specific protocols are registered in the machine-level Web.config file.</span></span>  
  
```xml  
<system.web>  
   <protocols>  
      <add name="net.tcp"
        processHandlerType=  
         "System.ServiceModel.WasHosting.TcpProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.TcpAppDomainProtocolHandler"  
        validate="false" />  
      <add name="net.pipe"
        processHandlerType=  
         "System.ServiceModel.WasHosting.NamedPipeProcessProtocolHandler"  
          appDomainHandlerType=  
           "System.ServiceModel.WasHosting.NamedPipeAppDomainProtocolHandler"/>  
      <add name="net.msmq"  
        processHandlerType=  
         "System.ServiceModel.WasHosting.MsmqProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.MsmqAppDomainProtocolHandler"  
        validate="false" />  
   </protocols>  
</system.web>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a60e-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a60e-142">See also</span></span>

- [<span data-ttu-id="7a60e-143">WCF で使用するための WAS を設定する</span><span class="sxs-lookup"><span data-stu-id="7a60e-143">Configuring WAS for Use with WCF</span></span>](configuring-the-wpa--service-for-use-with-wcf.md)
- <span data-ttu-id="7a60e-144">[AppFabric のホスティング機能](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="7a60e-144">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
