---
title: カスタム検索基準
ms.date: 03/30/2017
ms.assetid: b2723929-8829-424d-8015-a37ba2ab4f68
ms.openlocfilehash: a7f1b5996f3aefe1ccd77d3ddc117bc7c53ed2aa
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715459"
---
# <a name="custom-find-criteria"></a><span data-ttu-id="592db-102">カスタム検索基準</span><span class="sxs-lookup"><span data-stu-id="592db-102">Custom Find Criteria</span></span>
<span data-ttu-id="592db-103">このサンプルでは、ロジックを使用するカスタム スコープ一致の作成方法とカスタム探索サービスの実装方法を示します。</span><span class="sxs-lookup"><span data-stu-id="592db-103">This sample demonstrates how to create a custom scope match using logic and how to implement a custom discovery service.</span></span> <span data-ttu-id="592db-104">クライアントは、カスタム スコープ一致機能を使用して、システムによって提供される WCF Discovery の検索機能を改良および拡張します。</span><span class="sxs-lookup"><span data-stu-id="592db-104">Clients use custom scope matching functionality to refine and further build on top of the system-provided find functionality of WCF Discovery.</span></span> <span data-ttu-id="592db-105">このサンプルでは次のシナリオを扱います。</span><span class="sxs-lookup"><span data-stu-id="592db-105">The scenario this sample covers is as follows:</span></span>  
  
1. <span data-ttu-id="592db-106">クライアントは電卓サービスを検索します。</span><span class="sxs-lookup"><span data-stu-id="592db-106">A client is looking for a calculator service.</span></span>  
  
2. <span data-ttu-id="592db-107">検索を絞り込むために、クライアントはカスタム スコープ一致ルールを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="592db-107">To refine its search, the client must use a custom scope matching rule.</span></span>  
  
3. <span data-ttu-id="592db-108">このルールに従って、サービスは、エンドポイントがクライアントによって指定されたスコープのいずれかと一致した場合、クライアントに応答を送り返します。</span><span class="sxs-lookup"><span data-stu-id="592db-108">According to this rule, a service responds back to the client if its endpoint matches any of the scopes specified by the client.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="592db-109">例</span><span class="sxs-lookup"><span data-stu-id="592db-109">Demonstrates</span></span>  
  
- <span data-ttu-id="592db-110">カスタム探索サービスの作成。</span><span class="sxs-lookup"><span data-stu-id="592db-110">Creating a custom discovery service.</span></span>  
  
- <span data-ttu-id="592db-111">アルゴリズムに基づくカスタム スコープ一致の実装</span><span class="sxs-lookup"><span data-stu-id="592db-111">Implementing a custom scope match by algorithm.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="592db-112">ディスカッション</span><span class="sxs-lookup"><span data-stu-id="592db-112">Discussion</span></span>  
 <span data-ttu-id="592db-113">クライアントは、"OR" 型の一致条件を探しています。</span><span class="sxs-lookup"><span data-stu-id="592db-113">The client is looking for "OR" type matching criteria.</span></span> <span data-ttu-id="592db-114">サービスは、エンドポイントのスコープがクライアントによって指定されたスコープのいずれかと一致した場合、応答を送り返します。</span><span class="sxs-lookup"><span data-stu-id="592db-114">A service responds back if the scopes on its endpoints match any of the scopes provided by the client.</span></span> <span data-ttu-id="592db-115">この場合、クライアントは、次のいずれかのスコープを含む電卓サービスを検索します。</span><span class="sxs-lookup"><span data-stu-id="592db-115">In this case, the client is looking for a calculator service that has any of the scopes in the following list:</span></span>  
  
1. `net.tcp://Microsoft.Samples.Discovery/RedmondLocation`  
  
2. `net.tcp://Microsoft.Samples.Discovery/SeattleLocation`  
  
3. `net.tcp://Microsoft.Samples.Discovery/PortlandLocation`  
  
 <span data-ttu-id="592db-116">これを行うために、クライアントはカスタム スコープ一致を URI で渡すことで、カスタム スコープ一致を使用するようにサービスに指示します。</span><span class="sxs-lookup"><span data-stu-id="592db-116">To accomplish this, the client directs services to use a custom scope matching rule by passing in a custom scope match by URI.</span></span> <span data-ttu-id="592db-117">サービスは、カスタム スコープ一致を容易にするために、カスタム スコープ一致ルールを理解し、関連する一致ロジックを実装するカスタム探索サービスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="592db-117">To facilitate the custom scope matching, the service must use a custom discovery service that understands the custom scope match rule and implements the associated matching logic.</span></span>  
  
 <span data-ttu-id="592db-118">クライアント プロジェクトで Program.cs ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="592db-118">In the client project, open the Program.cs file.</span></span> <span data-ttu-id="592db-119">`ScopeMatchBy` オブジェクトの `FindCriteria` フィールドが特定の URI に設定されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="592db-119">Note that the `ScopeMatchBy` field of the `FindCriteria` object is set to a specific URI.</span></span> <span data-ttu-id="592db-120">この識別子はサービスに送信されます。</span><span class="sxs-lookup"><span data-stu-id="592db-120">This identifier is sent to the service.</span></span> <span data-ttu-id="592db-121">サービスがこのルールを理解できない場合、クライアントの検索要求は無視されます。</span><span class="sxs-lookup"><span data-stu-id="592db-121">If the service does not understand this rule, it ignores the client’s find request.</span></span>  
  
 <span data-ttu-id="592db-122">サービス プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="592db-122">Open the service project.</span></span> <span data-ttu-id="592db-123">カスタム探索サービスの実装には、次の 3 つのファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="592db-123">Three files are used to implement the Custom Discovery Service:</span></span>  
  
1. <span data-ttu-id="592db-124">**AsyncResult.cs**: これは、探索方法で必要な `AsyncResult` の実装です。</span><span class="sxs-lookup"><span data-stu-id="592db-124">**AsyncResult.cs**: This is the implementation of the `AsyncResult` that is required by Discovery methods.</span></span>  
  
2. <span data-ttu-id="592db-125">**CustomDiscoveryService.cs**: このファイルは、カスタム探索サービスを実装します。</span><span class="sxs-lookup"><span data-stu-id="592db-125">**CustomDiscoveryService.cs**: This file implements the custom discovery service.</span></span> <span data-ttu-id="592db-126">この実装では、<xref:System.ServiceModel.Discovery.DiscoveryService> クラスを拡張し、必要なメソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="592db-126">The implementation extends the <xref:System.ServiceModel.Discovery.DiscoveryService> class and overrides the necessary methods.</span></span> <span data-ttu-id="592db-127"><xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> メソッドの実装に注意してください。</span><span class="sxs-lookup"><span data-stu-id="592db-127">Note the implementation of the <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> method.</span></span> <span data-ttu-id="592db-128">このメソッドは、ルールに基づくカスタム スコープ一致がクライアントによって指定されているかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="592db-128">The method checks to see whether the custom scope match by rule was specified by the client.</span></span> <span data-ttu-id="592db-129">これはクライアントが前に指定したカスタム URI です。</span><span class="sxs-lookup"><span data-stu-id="592db-129">This is the same custom URI that the client specified previously.</span></span> <span data-ttu-id="592db-130">カスタムルールが指定されている場合は、"OR" 一致ロジックを実装するコードパスに従います。</span><span class="sxs-lookup"><span data-stu-id="592db-130">If the custom rule is specified, the code path that implements the "OR" match logic is followed.</span></span>  
  
     <span data-ttu-id="592db-131">このカスタム ロジックでは、サービスに含まれている各エンドポイントのスコープがすべてチェックされます。</span><span class="sxs-lookup"><span data-stu-id="592db-131">This custom logic goes through all of the scopes on each of the endpoints that the service has.</span></span> <span data-ttu-id="592db-132">エンドポイントのスコープのいずれかがクライアントによって指定されたスコープのいずれかに一致した場合、探索サービスはクライアントに送り返す応答にそのエンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="592db-132">If any of the endpoint's scopes match any of the scopes provided by the client, the discovery service adds that endpoint to the response that is sent back to the client.</span></span>  
  
3. <span data-ttu-id="592db-133">**CustomDiscoveryExtension.cs**: 探索サービスを実装する最後の手順は、カスタム探索サービスのこの実装をサービスホストに接続することです。</span><span class="sxs-lookup"><span data-stu-id="592db-133">**CustomDiscoveryExtension.cs**: The last step in implementing the discovery service is to connect this implementation of the custom discover service to the service host.</span></span> <span data-ttu-id="592db-134">ここで使用するヘルパー クラスは `CustomDiscoveryExtension` クラスです。</span><span class="sxs-lookup"><span data-stu-id="592db-134">The helper class used here is the `CustomDiscoveryExtension` class.</span></span> <span data-ttu-id="592db-135">このクラスは <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> クラスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="592db-135">This class extends the <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> class.</span></span> <span data-ttu-id="592db-136">ユーザーは <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> メソッドをオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="592db-136">The user must override the <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> method.</span></span> <span data-ttu-id="592db-137">この場合、このメソッドは、前に作成されたカスタム探索サービスのインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="592db-137">In this case, the method returns an instance of the custom discovery service that was created before.</span></span> <span data-ttu-id="592db-138">`PublishedEndpoints` は、<xref:System.Collections.ObjectModel.ReadOnlyCollection%601> に追加されるすべてのアプリケーション エンドポイントを含む <xref:System.ServiceModel.ServiceHost> です。</span><span class="sxs-lookup"><span data-stu-id="592db-138">`PublishedEndpoints` is a <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> that contains all of the application endpoints that are added to the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="592db-139">カスタム探索サービスは、これを使用して内部リストを設定します。</span><span class="sxs-lookup"><span data-stu-id="592db-139">The custom discovery service uses this to populate its internal list.</span></span> <span data-ttu-id="592db-140">ユーザーは、その他のエンドポイント メタデータも追加できます。</span><span class="sxs-lookup"><span data-stu-id="592db-140">A user can to add other endpoint metadata as well.</span></span>  
  
 <span data-ttu-id="592db-141">最後に、Program.cs を開きます。</span><span class="sxs-lookup"><span data-stu-id="592db-141">Lastly, open Program.cs.</span></span> <span data-ttu-id="592db-142"><xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> と `CustomDiscoveryExtension` の両方がホストに追加されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="592db-142">Note that both the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and `CustomDiscoveryExtension` are added to the host.</span></span> <span data-ttu-id="592db-143">これが完了し、探索メッセージの受信に使用されるエンドポイントがホストに追加されると、アプリケーションがカスタム探索サービスを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="592db-143">Once this is done and the host has an endpoint over which to receive discovery messages, the application can use the custom discovery service.</span></span>  
  
 <span data-ttu-id="592db-144">クライアントがサービスのアドレスを知ることなくサービスを検索できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="592db-144">Observe that the client is able to find the service without knowing its address.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="592db-145">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="592db-145">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="592db-146">プロジェクトを含むソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="592db-146">Open the solution that contains the project.</span></span>  
  
2. <span data-ttu-id="592db-147">プロジェクトをビルドする。</span><span class="sxs-lookup"><span data-stu-id="592db-147">Build the project.</span></span>  
  
3. <span data-ttu-id="592db-148">サービス アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="592db-148">Run the service application.</span></span>  
  
4. <span data-ttu-id="592db-149">クライアント アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="592db-149">Run the client application.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="592db-150">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="592db-150">The samples may already be installed on your machine.</span></span> <span data-ttu-id="592db-151">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="592db-151">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="592db-152">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459)にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) と [!INCLUDE[wf1](../../../../includes/wf1-md.md)] サンプルをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="592db-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="592db-153">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="592db-153">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\CustomFindCriteria`
