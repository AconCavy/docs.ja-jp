---
title: 永続性インスタンス コンテキスト
ms.date: 03/30/2017
ms.assetid: 97bc2994-5a2c-47c7-927a-c4cd273153df
ms.openlocfilehash: d70617fef7ebe0a94e22e858ee403d5d4f1840e3
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728405"
---
# <a name="durable-instance-context"></a><span data-ttu-id="d8a9b-102">永続性インスタンス コンテキスト</span><span class="sxs-lookup"><span data-stu-id="d8a9b-102">Durable Instance Context</span></span>

<span data-ttu-id="d8a9b-103">このサンプルでは、Windows Communication Foundation (WCF) ランタイムをカスタマイズして、永続性インスタンスコンテキストを有効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-103">This sample demonstrates how to customize the Windows Communication Foundation (WCF) runtime to enable durable instance contexts.</span></span> <span data-ttu-id="d8a9b-104">バッキング ストアとして、SQL Server 2005 (この場合は SQL Server 2005 Express) を使用します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-104">It uses SQL Server 2005 as its backing store (SQL Server 2005 Express in this case).</span></span> <span data-ttu-id="d8a9b-105">ただし、カスタム ストレージ機構にアクセスする方法も示します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-105">However, it also provides a way to access custom storage mechanisms.</span></span>

> [!NOTE]
> <span data-ttu-id="d8a9b-106">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="d8a9b-107">このサンプルでは、WCF のチャネル層とサービスモデルレイヤーの両方を拡張します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-107">This sample involves extending both the channel layer and the service model layer of the WCF.</span></span> <span data-ttu-id="d8a9b-108">したがって、実装の詳細に進む前に基になる概念を理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-108">Therefore it is necessary to understand the underlying concepts before going into the implementation details.</span></span>

<span data-ttu-id="d8a9b-109">永続性インスタンス コンテキストは、現実のケースでも頻繁に起こりうるものです。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-109">Durable instance contexts can be found in the real world scenarios quite often.</span></span> <span data-ttu-id="d8a9b-110">たとえば、ショッピングカートアプリケーションでは、ショッピングを途中で一時停止し、別の日に継続することができます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-110">A shopping cart application, for example, has the ability to pause shopping halfway through and continue it on another day.</span></span> <span data-ttu-id="d8a9b-111">そのため、ショッピング カートに翌日アクセスすると、元のコンテキストが復元されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-111">So that when we visit the shopping cart the next day, our original context is restored.</span></span> <span data-ttu-id="d8a9b-112">接続が切断されている間、ショッピング カート アプリケーション (サーバー上) はショッピング カートのインスタンスを保持しないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-112">It is important to note that the shopping cart application (on the server) does not maintain the shopping cart instance while we are disconnected.</span></span> <span data-ttu-id="d8a9b-113">その代わり、状態を永続的なストレージ メディアに保持し、復元されたコンテキストの新しいインスタンスを構築するときにこの状態を使用します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-113">Instead, it persists its state into a durable storage media and uses it when constructing a new instance for the restored context.</span></span> <span data-ttu-id="d8a9b-114">したがって、同じコンテキストに対してサービスを提供できるサービス インスタンスは、以前のインスタンスと同じではありません (つまり、メモリ アドレスが同じではありません)。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-114">Therefore the service instance that may service for the same context is not the same as the previous instance (that is, it does not have the same memory address).</span></span>

<span data-ttu-id="d8a9b-115">永続性インスタンス コンテキストは、コンテキスト ID をクライアントとサービス間で交換するための簡単なプロトコルによって可能になります。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-115">Durable instance context is made possible by a small protocol that exchanges a context ID between the client and service.</span></span> <span data-ttu-id="d8a9b-116">このコンテキスト ID はクライアント上で作成され、サービスに転送されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-116">This context ID is created on the client and transmitted to the service.</span></span> <span data-ttu-id="d8a9b-117">サービス インスタンスが作成されると、サービス上のランタイムは、永続ストレージ (既定では SQL Server 2005 のデータベース) 上で永続化されている、このコンテキスト ID に対応する状態を読み込もうとします。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-117">When the service instance is created, the service runtime tries to load the persisted state that corresponds to this context ID from a persistent storage (by default it is a SQL Server 2005 database).</span></span> <span data-ttu-id="d8a9b-118">使用できる状態がない場合、新しいインスタンスの既定の状態がになります。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-118">If no state is available, the new instance has its default state.</span></span> <span data-ttu-id="d8a9b-119">サービス実装は、カスタム属性を使用してサービス実装の状態を変更する操作の詳細を指定し、ランタイムがその操作を呼び出した後にサービス インスタンスを保存できるようにします。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-119">The service implementation uses a custom attribute to mark operations that change the state of the service implementation so that the runtime can save the service instance after invoking them.</span></span>

<span data-ttu-id="d8a9b-120">前の説明から、目標を達成するための手順は大きく次の 2 つに分けられます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-120">By the previous description, two steps can easily be distinguished to achieve the goal:</span></span>

1. <span data-ttu-id="d8a9b-121">ネットワークに出力されるメッセージを、コンテキスト ID が含まれるように変更します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-121">Change the message that goes on the wire to carry the context ID.</span></span>

2. <span data-ttu-id="d8a9b-122">サービス側のローカル動作を変更して、カスタムのインスタンス化ロジックを実装します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-122">Change the service local behavior to implement custom instancing logic.</span></span>

<span data-ttu-id="d8a9b-123">リスト内の最初のメッセージはネットワーク上のメッセージに影響するため、カスタムチャネルとして実装し、チャネル層にフックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-123">Because the first one in the list affects the messages on the wire, it should be implemented as a custom channel and be hooked up to the channel layer.</span></span> <span data-ttu-id="d8a9b-124">後者の手順が影響を及ぼすのは、サービスのローカル動作だけです。したがって、いくつかのサービス拡張ポイントを拡張することによって実装できます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-124">The latter only affects the service local behavior and therefore can be implemented by extending several service extensibility points.</span></span> <span data-ttu-id="d8a9b-125">以降のセクションでは、こうしたそれぞれの拡張について説明します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-125">In the next few sections, each of these extensions are discussed.</span></span>

## <a name="durable-instancecontext-channel"></a><span data-ttu-id="d8a9b-126">永続的な InstanceContext チャネル</span><span class="sxs-lookup"><span data-stu-id="d8a9b-126">Durable InstanceContext Channel</span></span>

<span data-ttu-id="d8a9b-127">最初に、チャネル レイヤの拡張について考えます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-127">The first thing to look at is a channel layer extension.</span></span> <span data-ttu-id="d8a9b-128">カスタム チャネルを記述する最初の手順として、チャネルの通信構造を決定します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-128">The first step in writing a custom channel is to decide the communication structure of the channel.</span></span> <span data-ttu-id="d8a9b-129">新しいワイヤプロトコルが導入されると、チャネルはチャネルスタック内のほぼすべてのチャネルで動作するようになります。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-129">As a new wire protocol is being introduced, the channel should work with almost any other channel in the channel stack.</span></span> <span data-ttu-id="d8a9b-130">そのため、すべてのメッセージ交換パターンをサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-130">Therefore it should support all the message exchange patterns.</span></span> <span data-ttu-id="d8a9b-131">ただし、チャネルの中心的な機能は通信構造に関係なく同じです。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-131">However, the core functionality of the channel is the same regardless of its communication structure.</span></span> <span data-ttu-id="d8a9b-132">具体的には、コンテキスト ID をクライアント側からメッセージに書き込み、サービス側からこのメッセージのコンテキスト ID を読み取って上位レベルに渡します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-132">More specifically, from the client it should write the context ID to the messages and from the service it should read this context ID from the messages and pass it to the upper levels.</span></span> <span data-ttu-id="d8a9b-133">そのため、すべての永続性インスタンス コンテキスト チャネルの実装に対して抽象基本クラスとして動作する、`DurableInstanceContextChannelBase` クラスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-133">Because of that, a `DurableInstanceContextChannelBase` class is created that acts as the abstract base class for all durable instance context channel implementations.</span></span> <span data-ttu-id="d8a9b-134">このクラスには、共通ステート マシンの管理機能と保護された 2 つのメンバが含まれ、これによってコンテキスト情報をメッセージに適用したり、メッセージからコンテキスト情報を読み取ったりします。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-134">This class contains the common state machine management functions and two protected members to apply and read the context information to and from messages.</span></span>

```csharp
class DurableInstanceContextChannelBase
{
  //…
  protected void ApplyContext(Message message)
  {
    //…
  }
  protected string ReadContextId(Message message)
  {
    //…
  }
}
```

<span data-ttu-id="d8a9b-135">これら 2 つのメソッドは、`IContextManager` 実装を使用して、メッセージへのコンテキスト ID の書き込みと、メッセージからのコンテキスト ID の読み取りを行います </span><span class="sxs-lookup"><span data-stu-id="d8a9b-135">These two methods make use of `IContextManager` implementations to write and read the context ID to or from the message.</span></span> <span data-ttu-id="d8a9b-136">(`IContextManager`は、すべてのコンテキストマネージャーのコントラクトを定義するために使用されるカスタムインターフェイスです)。チャネルは、カスタム SOAP ヘッダーまたは HTTP クッキーヘッダーにコンテキスト ID を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-136">(`IContextManager` is a custom interface used to define the contract for all context managers.) The channel can either include the context ID in a custom SOAP header or in an HTTP cookie header.</span></span> <span data-ttu-id="d8a9b-137">各コンテキスト マネージャの実装は、`ContextManagerBase` クラスを継承します。このクラスには、すべてのコンテキスト マネージャについての共通機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-137">Each context manager implementation inherits from the `ContextManagerBase` class that contains the common functionality for all context managers.</span></span> <span data-ttu-id="d8a9b-138">このクラスの `GetContextId` メソッドは、コンテキスト ID をクライアント側で生成する際に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-138">The `GetContextId` method in this class is used to originate the context ID from the client.</span></span> <span data-ttu-id="d8a9b-139">コンテキスト ID が最初に生成されると、このメソッドはこれをテキスト ファイルに保存します。テキスト ファイルの名前は、リモート エンドポイント アドレスによって作成されます (通常の URI に含まれる、ファイル名として無効な文字は、@ 文字に置き換えられます)。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-139">When a context ID is originated for the first time, this method saves it into a text file whose name is constructed by the remote endpoint address (the invalid file name characters in the typical URIs are replaced with @ characters).</span></span>

<span data-ttu-id="d8a9b-140">コンテキスト ID が後で同じリモート エンドポイントで必要になると、このメソッドは適切なファイルが存在するかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-140">Later when the context ID is required for the same remote endpoint, it checks whether an appropriate file exists.</span></span> <span data-ttu-id="d8a9b-141">ファイルが存在する場合は、コンテキスト ID を読み取って返します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-141">If it does, it reads the context ID and returns.</span></span> <span data-ttu-id="d8a9b-142">存在しない場合は、新しく生成されたコンテキスト ID を返してこれをファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-142">Otherwise it returns a newly generated context ID and saves it to a file.</span></span> <span data-ttu-id="d8a9b-143">既定の構成では、これらのファイルは、現在のユーザーの temp ディレクトリに存在する ContextStore という名前のディレクトリに配置されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-143">With the default configuration, these files are placed in a directory called ContextStore, which resides in the current user's temp directory.</span></span> <span data-ttu-id="d8a9b-144">ただし、この場所はバインド要素を使用して構成できます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-144">However this location is configurable using the binding element.</span></span>

<span data-ttu-id="d8a9b-145">コンテキスト ID の転送に使用される機構は構成可能です。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-145">The mechanism used to transport the context ID is configurable.</span></span> <span data-ttu-id="d8a9b-146">HTTP クッキー ヘッダーか、またはカスタム SOAP ヘッダーのどちらかに記述できます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-146">It could be either written to the HTTP cookie header or to a custom SOAP header.</span></span> <span data-ttu-id="d8a9b-147">カスタム SOAP ヘッダーに記述する場合は、このプロトコルを HTTP 以外のプロトコル (TCP や NamedPipes など) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-147">The custom SOAP header approach makes it possible to use this protocol with non-HTTP protocols (for example, TCP or Named Pipes).</span></span> <span data-ttu-id="d8a9b-148">これらの 2 つのオプションは、`MessageHeaderContextManager` と `HttpCookieContextManager` という名前の 2 つのクラスに実装されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-148">There are two classes, namely `MessageHeaderContextManager` and `HttpCookieContextManager`, which implement these two options.</span></span>

<span data-ttu-id="d8a9b-149">これらのクラスはどちらも、コンテキスト ID をメッセージに適切に書き込みます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-149">Both of them write the context ID to the message appropriately.</span></span> <span data-ttu-id="d8a9b-150">たとえば `MessageHeaderContextManager` クラスでは、`WriteContext` メソッドにより SOAP ヘッダーにコンテキスト ID が書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-150">For example, the `MessageHeaderContextManager` class writes it to a SOAP header in the `WriteContext` method.</span></span>

```csharp
public override void WriteContext(Message message)
{
  string contextId = this.GetContextId();

  MessageHeader contextHeader =
    MessageHeader.CreateHeader(DurableInstanceContextUtility.HeaderName,
      DurableInstanceContextUtility.HeaderNamespace,
      contextId,
      true);

  message.Headers.Add(contextHeader);
}
```

<span data-ttu-id="d8a9b-151">`ApplyContext` クラス内の `ReadContextId` メソッドと `DurableInstanceContextChannelBase` メソッドは、それぞれ `IContextManager.ReadContext` と `IContextManager.WriteContext` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-151">Both the `ApplyContext` and `ReadContextId` methods in the `DurableInstanceContextChannelBase` class invoke the `IContextManager.ReadContext` and `IContextManager.WriteContext`, respectively.</span></span> <span data-ttu-id="d8a9b-152">ただし、これらのコンテキスト マネージャは `DurableInstanceContextChannelBase` クラスによって直接作成されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-152">However, these context managers are not directly created by the `DurableInstanceContextChannelBase` class.</span></span> <span data-ttu-id="d8a9b-153">代わりに `ContextManagerFactory` クラスを使用してこの処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-153">Instead it uses the `ContextManagerFactory` class to do that job.</span></span>

```csharp
IContextManager contextManager =
                ContextManagerFactory.CreateContextManager(contextType,
                this.contextStoreLocation,
                this.endpointAddress);
```

<span data-ttu-id="d8a9b-154">`ApplyContext` メソッドは送信チャネルによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-154">The `ApplyContext` method is invoked by the sending channels.</span></span> <span data-ttu-id="d8a9b-155">このメソッドは、コンテキスト ID を送信メッセージに挿入します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-155">It injects the context ID to the outgoing messages.</span></span> <span data-ttu-id="d8a9b-156">`ReadContextId` メソッドは受信チャネルによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-156">The `ReadContextId` method is invoked by the receiving channels.</span></span> <span data-ttu-id="d8a9b-157">このメソッドは、受信メッセージ内でコンテキスト ID を使用できることを確認し、`Properties` クラスの `Message` コレクションにコンテキスト ID を追加します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-157">This method ensures that the context ID is available in the incoming messages and adds it to the `Properties` collection of the `Message` class.</span></span> <span data-ttu-id="d8a9b-158">さらに、コンテキスト ID の読み取りでエラーが発生した場合は `CommunicationException` をスローし、チャネルを中止します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-158">It also throws a `CommunicationException` in case of a failure to read the context ID and thus causes the channel to be aborted.</span></span>

```csharp
message.Properties.Add(DurableInstanceContextUtility.ContextIdProperty, contextId);
```

<span data-ttu-id="d8a9b-159">次に進む前に、`Properties` クラスの `Message` コレクションの使用方法について理解することが重要です。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-159">Before proceeding, it is important to understand the usage of the `Properties` collection in the `Message` class.</span></span> <span data-ttu-id="d8a9b-160">通常、この `Properties` コレクションは、チャネル レイヤのデータを下位レベルから上位レベルに渡すときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-160">Typically, this `Properties` collection is used when passing data from lower to the upper levels from the channel layer.</span></span> <span data-ttu-id="d8a9b-161">この方法により、必要なデータを、プロトコルの詳細に関係なく一貫した方法で上位レベルに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-161">This way the desired data can be provided to the upper levels in a consistent manner regardless of the protocol details.</span></span> <span data-ttu-id="d8a9b-162">つまり、チャネル層は、SOAP ヘッダーまたは HTTP クッキーヘッダーとしてコンテキスト ID を送受信できます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-162">In other words, the channel layer can send and receive the context ID either as a SOAP header or an HTTP cookie header.</span></span> <span data-ttu-id="d8a9b-163">しかし、上位レベルではこうした詳細を認識する必要はありません。チャネル レイヤにより、この情報が `Properties` コレクションで使用できるためです。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-163">But it is not necessary for the upper levels to know about these details because the channel layer makes this information available in the `Properties` collection.</span></span>

<span data-ttu-id="d8a9b-164">`DurableInstanceContextChannelBase` クラスを配備したら、必要な 10 のインターフェイス (IOutputChannel、IInputChannel、IOutputSessionChannel、IInputSessionChannel、IRequestChannel、IReplyChannel、IRequestSessionChannel、IReplySessionChannel、IDuplexChannel、および IDuplexSessionChannel) のすべてを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-164">Now with the `DurableInstanceContextChannelBase` class in place all ten of the necessary interfaces (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, IDuplexChannel, IDuplexSessionChannel) must be implemented.</span></span> <span data-ttu-id="d8a9b-165">これらは、使用可能なすべてのメッセージ交換パターン (データグラム、単一方向、双方向、およびそれらのセッションフル variant) に似ています。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-165">They resemble every available message exchange pattern (datagram, simplex, duplex, and their sessionful variants).</span></span> <span data-ttu-id="d8a9b-166">これらの各実装は、前に説明した基本`ApplyContext`クラス`ReadContextId`を継承し、適切にを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-166">Each of these implementations inherits the base class previously described and calls `ApplyContext` and `ReadContextId` appropriately.</span></span> <span data-ttu-id="d8a9b-167">たとえば、IOutputChannel インターフェイスを実装する `DurableInstanceContextOutputChannel` は、メッセージを送信する各メソッドから `ApplyContext` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-167">For example, `DurableInstanceContextOutputChannel` - which implements the IOutputChannel interface - calls the `ApplyContext` method from each method that sends the messages.</span></span>

```csharp
public void Send(Message message, TimeSpan timeout)
{
    // Apply the context information before sending the message.
    this.ApplyContext(message);
    //…
}
```

<span data-ttu-id="d8a9b-168">一方、-インターフェイスを`DurableInstanceContextInputChannel` `IInputChannel`実装するは、メッセージを受信する`ReadContextId`各メソッドでメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-168">On the other hand, `DurableInstanceContextInputChannel` - which implements the `IInputChannel` interface - calls the `ReadContextId` method in each method, which receives the messages.</span></span>

```csharp
public Message Receive(TimeSpan timeout)
{
    //…
      ReadContextId(message);
      return message;
}
```

<span data-ttu-id="d8a9b-169">これらのチャネル実装は、これ以外には、チャネル スタック内でチャネル実装の下にあるチャネルへのメソッド呼び出しを代行します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-169">Apart from this, these channel implementations delegate the method invocations to the channel below them in the channel stack.</span></span> <span data-ttu-id="d8a9b-170">ただし、セッションフル バリエーションには、セッション作成の基になる最初のメッセージに対してのみコンテキスト ID の送信と読み取りを許可する、基本的なロジックがあります。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-170">However, sessionful variants have a basic logic to make sure that the context ID is sent and is read only for the first message that causes the session to be created.</span></span>

```csharp
if (isFirstMessage)
{
//…
    this.ApplyContext(message);
    isFirstMessage = false;
}
```

<span data-ttu-id="d8a9b-171">これらのチャネル実装は、 `DurableInstanceContextBindingElement`クラスと`DurableInstanceContextBindingElementSection`クラスによって WCF チャネルランタイムに適切に追加されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-171">These channel implementations are then added to the WCF channel runtime by the `DurableInstanceContextBindingElement` class and `DurableInstanceContextBindingElementSection` class appropriately.</span></span> <span data-ttu-id="d8a9b-172">バインド要素とバインド要素のセクションの詳細については、 [Httpcookiesession](../../../../docs/framework/wcf/samples/httpcookiesession.md) channel サンプルドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-172">See the [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) channel sample documentation for more details about binding elements and binding element sections.</span></span>

## <a name="service-model-layer-extensions"></a><span data-ttu-id="d8a9b-173">サービス モデル レイヤの拡張</span><span class="sxs-lookup"><span data-stu-id="d8a9b-173">Service Model Layer Extensions</span></span>

<span data-ttu-id="d8a9b-174">コンテキスト ID がチャネル レイヤを通過すると、インスタンス化をカスタマイズするようにサービス側の動作を実装できます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-174">Now that the context ID has traveled through the channel layer, the service behavior can be implemented to customize the instantiation.</span></span> <span data-ttu-id="d8a9b-175">このサンプルでは、記憶域マネージャを使用して永続ストアからの状態の読み込みと、永続ストアへの状態の保存が行われます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-175">In this sample, a storage manager is used to load and save state from or to the persistent store.</span></span> <span data-ttu-id="d8a9b-176">前述のように、このサンプルにはバッキング ストアとして SQL Server 2005 を使用する記憶域マネージャが用意されています。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-176">As explained previously, this sample provides a storage manager that uses SQL Server 2005 as its backing store.</span></span> <span data-ttu-id="d8a9b-177">ただし、この拡張に対してカスタム ストレージ機構を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-177">However, it is also possible to add custom storage mechanisms to this extension.</span></span> <span data-ttu-id="d8a9b-178">これを行うには、すべての記憶域マネージャが実装する必要のあるパブリック インターフェイスを宣言します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-178">To do that a public interface is declared, which must be implemented by all storage managers.</span></span>

```csharp
public interface IStorageManager
{
    object GetInstance(string contextId, Type type);
    void SaveInstance(string contextId, object state);
}
```

<span data-ttu-id="d8a9b-179">`SqlServerStorageManager` クラスには、既定の `IStorageManager` 実装が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-179">The `SqlServerStorageManager` class contains the default `IStorageManager` implementation.</span></span> <span data-ttu-id="d8a9b-180">その`SaveInstance`メソッドでは、指定されたオブジェクトは XmlSerializer を使用してシリアル化され、SQL Server データベースに保存されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-180">In its `SaveInstance` method, the given object is serialized using the XmlSerializer and is saved to the SQL Server database.</span></span>

```csharp
XmlSerializer serializer = new XmlSerializer(state.GetType());
string data;

using (StringWriter writer = new StringWriter(CultureInfo.InvariantCulture))
{
    serializer.Serialize(writer, state);
    data = writer.ToString();
}

using (SqlConnection connection = new SqlConnection(GetConnectionString()))
{
    connection.Open();

    string update = @"UPDATE Instances SET Instance = @instance WHERE ContextId = @contextId";

    using (SqlCommand command = new SqlCommand(update, connection))
    {
        command.Parameters.Add("@instance", SqlDbType.VarChar, 2147483647).Value = data;
        command.Parameters.Add("@contextId", SqlDbType.VarChar, 256).Value = contextId;

        int rows = command.ExecuteNonQuery();

        if (rows == 0)
        {
            string insert = @"INSERT INTO Instances(ContextId, Instance) VALUES(@contextId, @instance)";
            command.CommandText = insert;
            command.ExecuteNonQuery();
        }
    }
}
```

<span data-ttu-id="d8a9b-181">`GetInstance`メソッドでは、シリアル化されたデータが特定のコンテキスト ID に対して読み取られ、そこから構築されたオブジェクトが呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-181">In the `GetInstance` method, the serialized data is read for a given context ID and the object constructed from it is returned to the caller.</span></span>

```csharp
object data;
using (SqlConnection connection = new SqlConnection(GetConnectionString()))
{
    connection.Open();

    string select = "SELECT Instance FROM Instances WHERE ContextId = @contextId";
    using (SqlCommand command = new SqlCommand(select, connection))
    {
        command.Parameters.Add("@contextId", SqlDbType.VarChar, 256).Value = contextId;
        data = command.ExecuteScalar();
    }
}

if (data != null)
{
    XmlSerializer serializer = new XmlSerializer(type);
    using (StringReader reader = new StringReader((string)data))
    {
        object instance = serializer.Deserialize(reader);
        return instance;
    }
}
```

<span data-ttu-id="d8a9b-182">この記憶域マネージャを直接インスタンス化することはできません。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-182">Users of these storage managers are not supposed to instantiate them directly.</span></span> <span data-ttu-id="d8a9b-183">その代わりに、`StorageManagerFactory` クラスを使用して、記憶域マネージャの作成に関する詳細から抽出します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-183">They use the `StorageManagerFactory` class, which abstracts from the storage manager creation details.</span></span> <span data-ttu-id="d8a9b-184">このクラスには、指定された型の記憶域マネージャのインスタンスを作成する、1 つの静的メンバ `GetStorageManager` があります。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-184">This class has one static member, `GetStorageManager`, which creates an instance of a given storage manager type.</span></span> <span data-ttu-id="d8a9b-185">型パラメーターが `null` の場合、このメソッドは既定の `SqlServerStorageManager` クラスのインスタンスを作成して返します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-185">If the type parameter is `null`, this method creates an instance of the default `SqlServerStorageManager` class and returns it.</span></span> <span data-ttu-id="d8a9b-186">さらに指定された型を検証して、それが `IStorageManager` インターフェイスを実装していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-186">It also validates the given type to make sure that it implements the `IStorageManager` interface.</span></span>

```csharp
public static IStorageManager GetStorageManager(Type storageManagerType)
{
IStorageManager storageManager = null;

if (storageManagerType == null)
{
    return new SqlServerStorageManager();
}
else
{
    object obj = Activator.CreateInstance(storageManagerType);

    // Throw if the specified storage manager type does not
    // implement IStorageManager.
    if (obj is IStorageManager)
    {
        storageManager = (IStorageManager)obj;
    }
    else
    {
        throw new InvalidOperationException(
                  ResourceHelper.GetString("ExInvalidStorageManager"));
    }

    return storageManager;
}
}
```

<span data-ttu-id="d8a9b-187">永続ストレージのインスタンスの読み取りや書き込みに必要なインフラストラクチャを実装します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-187">The necessary infrastructure to read and write instances from the persistent storage is implemented.</span></span> <span data-ttu-id="d8a9b-188">ここで、サービス側の動作を変更するために必要な手順を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-188">Now the necessary steps to change the service behavior have to be taken.</span></span>

<span data-ttu-id="d8a9b-189">この処理の最初の手順として、チャネル レイヤを通過したコンテキスト ID を現在の InstanceContext に保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-189">As the first step of this process we have to save the context ID, which came through the channel layer to the current InstanceContext.</span></span> <span data-ttu-id="d8a9b-190">InstanceContext は、WCF ディスパッチャーとサービスインスタンス間のリンクとして機能するランタイムコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-190">InstanceContext is a runtime component that acts as the link between the WCF dispatcher and the service instance.</span></span> <span data-ttu-id="d8a9b-191">これを使用すると、追加の状態と動作をサービス インスタンスに提供できます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-191">It can be used to provide additional state and behavior to the service instance.</span></span> <span data-ttu-id="d8a9b-192">セッションの多い通信では、コンテキスト ID は最初のメッセージだけに含まれて送信されるので、これが重要になります。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-192">This is essential because in sessionful communication the context ID is sent only with the first message.</span></span>

<span data-ttu-id="d8a9b-193">WCF では、拡張可能なオブジェクトパターンを使用して新しい状態と動作を追加することで、InstanceContext ランタイムコンポーネントを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-193">WCF allows extending its InstanceContext runtime component by adding a new state and behavior using its extensible object pattern.</span></span> <span data-ttu-id="d8a9b-194">拡張可能オブジェクトパターンは、既存のランタイムクラスを新しい機能で拡張するか、オブジェクトに新しい状態機能を追加するために WCF で使用されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-194">The extensible object pattern is used in WCF to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="d8a9b-195">拡張可能オブジェクトパターンには、IExtensibleObject\<T>、iextension\<T>、および iextensioncollection\<T> の3つのインターフェイスがあります。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-195">There are three interfaces in the extensible object pattern - IExtensibleObject\<T>, IExtension\<T>, and IExtensionCollection\<T>:</span></span>

- <span data-ttu-id="d8a9b-196">IExtensibleObject\<T> インターフェイスは、機能をカスタマイズする拡張を可能にするオブジェクトによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-196">The IExtensibleObject\<T> interface is implemented by objects that allow extensions that customize their functionality.</span></span>

- <span data-ttu-id="d8a9b-197">IExtension\<T> インターフェイスは、t 型のクラスの拡張であるオブジェクトによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-197">The IExtension\<T> interface is implemented by objects that are extensions of classes of type T.</span></span>

- <span data-ttu-id="d8a9b-198">IExtensionCollection\<T> インターフェイスは iextensions のコレクションであり、その型を使用して iextensions を取得できます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-198">The IExtensionCollection\<T> interface is a collection of IExtensions that allows for retrieving IExtensions by their type.</span></span>

<span data-ttu-id="d8a9b-199">このため、IExtension インターフェイスを実装して、コンテキスト ID を保存するために必要な状態を定義する、InstanceContextExtension クラスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-199">Therefore an InstanceContextExtension class should be created that implements the IExtension interface and defines the required state to save the context ID.</span></span> <span data-ttu-id="d8a9b-200">このクラスではさらに、使用される記憶域マネージャを保持する状態も提供されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-200">This class also provides the state to hold the storage manager being used.</span></span> <span data-ttu-id="d8a9b-201">新しい状態が保存された後では、その状態を変更できません。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-201">Once the new state is saved, it should not be possible to modify it.</span></span> <span data-ttu-id="d8a9b-202">したがって、インスタンスが作成される際、読み取り専用のプロパティを使用してのみアクセス可能になった時点で、状態がインスタンスに提供され、保存されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-202">Therefore the state is provided and saved to the instance at the time it is being constructed and then only accessible using read-only properties.</span></span>

```csharp
// Constructor
public DurableInstanceContextExtension(string contextId,
            IStorageManager storageManager)
{
    this.contextId = contextId;
    this.storageManager = storageManager;
}

// Read only properties
public string ContextId
{
    get { return this.contextId; }
}

public IStorageManager StorageManager
{
    get { return this.storageManager; }
}
```

<span data-ttu-id="d8a9b-203">InstanceContextInitializer クラスは IInstanceContextInitializer インターフェイスを実装し、作成された InstanceContext の Extensions コレクションにインスタンス コンテキスト拡張を追加します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-203">The InstanceContextInitializer class implements the IInstanceContextInitializer interface and adds the instance context extension to the Extensions collection of the InstanceContext being constructed.</span></span>

```csharp
public void Initialize(InstanceContext instanceContext, Message message)
{
    string contextId =
  (string)message.Properties[DurableInstanceContextUtility.ContextIdProperty];

    DurableInstanceContextExtension extension =
                new DurableInstanceContextExtension(contextId,
                     storageManager);
    instanceContext.Extensions.Add(extension);
}
```

<span data-ttu-id="d8a9b-204">既に説明したように、コンテキスト ID は `Properties` クラスの `Message` コレクションから読み取られ、拡張クラスのコンストラクタに渡されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-204">As described earlier the context ID is read from the `Properties` collection of the `Message` class and passed to the constructor of the extension class.</span></span> <span data-ttu-id="d8a9b-205">これによって、レイヤ間で情報を交換する場合の一貫性のある方法が示されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-205">This demonstrates how information can be exchanged between the layers in a consistent manner.</span></span>

<span data-ttu-id="d8a9b-206">次の重要な手順は、サービス インスタンスの作成手順をオーバーライドすることです。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-206">The next important step is overriding the service instance creation process.</span></span> <span data-ttu-id="d8a9b-207">WCF を使用すると、カスタムのインスタンス化動作を実装し、IInstanceProvider インターフェイスを使用してランタイムにフックできます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-207">WCF allows implementing custom instantiation behaviors and hooking them up to the runtime using the IInstanceProvider interface.</span></span> <span data-ttu-id="d8a9b-208">新しい `InstanceProvider` クラスがこの処理を行うために実装されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-208">The new `InstanceProvider` class is implemented to do that job.</span></span> <span data-ttu-id="d8a9b-209">インスタンスプロバイダーから要求されるサービスの種類は、コンストラクターで受け入れられます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-209">The service type expected from the instance provider is accepted in the constructor.</span></span> <span data-ttu-id="d8a9b-210">これは、後で新しいインスタンスの作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-210">Later this is used to create new instances.</span></span> <span data-ttu-id="d8a9b-211">`GetInstance`実装では、保存されたインスタンスを検索するために、ストレージマネージャーのインスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-211">In the `GetInstance` implementation, an instance of a storage manager is created looking for a persisted instance.</span></span> <span data-ttu-id="d8a9b-212">がを返す`null`場合は、サービス型の新しいインスタンスがインスタンス化され、呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-212">If it returns `null`, then a new instance of the service type is instantiated and returned to the caller.</span></span>

```csharp
public object GetInstance(InstanceContext instanceContext, Message message)
{
    object instance = null;

    DurableInstanceContextExtension extension =
    instanceContext.Extensions.Find<DurableInstanceContextExtension>();

    string contextId = extension.ContextId;
    IStorageManager storageManager = extension.StorageManager;

    instance = storageManager.GetInstance(contextId, serviceType);

    instance ??= Activator.CreateInstance(serviceType);
    return instance;
}
```

<span data-ttu-id="d8a9b-213">次に重要な手順は、、 `InstanceContextExtension` `InstanceContextInitializer`、および`InstanceProvider`の各クラスをサービスモデルランタイムにインストールすることです。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-213">The next important step is to install the `InstanceContextExtension`, `InstanceContextInitializer`, and `InstanceProvider` classes into the service model runtime.</span></span> <span data-ttu-id="d8a9b-214">カスタム属性を使用すると、サービス実装クラスの詳細を指定して、動作をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-214">A custom attribute could be used to mark the service implementation classes to install the behavior.</span></span> <span data-ttu-id="d8a9b-215">`DurableInstanceContextAttribute` にはこの属性の実装が含まれ、サービス側のランタイム全体を拡張できるようにするために `IServiceBehavior` インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-215">The `DurableInstanceContextAttribute` contains the implementation for this attribute and it implements the `IServiceBehavior` interface to extend the entire service runtime.</span></span>

<span data-ttu-id="d8a9b-216">このクラスには、使用される記憶域マネージャの型を受け入れるプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-216">This class has a property that accepts the type of the storage manager to be used.</span></span> <span data-ttu-id="d8a9b-217">このように実装することで、ユーザーは独自`IStorageManager`の実装をこの属性のパラメーターとして指定できるようになります。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-217">In this way, the implementation enables the users to specify their own `IStorageManager` implementation as parameter of this attribute.</span></span>

<span data-ttu-id="d8a9b-218">`ApplyDispatchBehavior`実装では、現在`InstanceContextMode` `ServiceBehavior`の属性のが検証されています。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-218">In the `ApplyDispatchBehavior` implementation, the `InstanceContextMode` of the current `ServiceBehavior` attribute is being verified.</span></span> <span data-ttu-id="d8a9b-219">このプロパティが Singleton に設定されている場合、永続性インスタンスを有効化できず、`InvalidOperationException` がスローされてホストに通知されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-219">If this property is set to Singleton, enabling durable instancing is not possible and an `InvalidOperationException` is thrown to notify the host.</span></span>

```csharp
ServiceBehaviorAttribute serviceBehavior =
    serviceDescription.Behaviors.Find<ServiceBehaviorAttribute>();

if (serviceBehavior != null &&
     serviceBehavior.InstanceContextMode == InstanceContextMode.Single)
{
    throw new InvalidOperationException(
       ResourceHelper.GetString("ExSingletonInstancingNotSupported"));
}
```

<span data-ttu-id="d8a9b-220">この後、記憶域マネージャのインスタンス、インスタンス コンテキストの初期化子、およびインスタンス プロバイダが作成され、各エンドポイント用に作成された `DispatchRuntime` にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-220">After this the instances of the storage manager, instance context initializer, and the instance provider are created and installed in the `DispatchRuntime` created for every endpoint.</span></span>

```csharp
IStorageManager storageManager =
    StorageManagerFactory.GetStorageManager(storageManagerType);

InstanceContextInitializer contextInitializer =
    new InstanceContextInitializer(storageManager);

InstanceProvider instanceProvider =
    new InstanceProvider(description.ServiceType);

foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)
{
    ChannelDispatcher cd = cdb as ChannelDispatcher;

    if (cd != null)
    {
        foreach (EndpointDispatcher ed in cd.Endpoints)
        {
            ed.DispatchRuntime.InstanceContextInitializers.Add(contextInitializer);
            ed.DispatchRuntime.InstanceProvider = instanceProvider;
        }
    }
}
```

<span data-ttu-id="d8a9b-221">ここまでを要約すると、このサンプルでは、カスタム コンテキスト ID を交換するためにカスタム ワイヤ プロトコルを有効化するチャネルを作成しました。また、永続ストレージのインスタンスを読み込むように、既定のインスタンス化動作を上書きしました。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-221">In summary so far, this sample has produced a channel that enabled the custom wire protocol for custom context ID exchange and it also overwrites the default instancing behavior to load the instances from the persistent storage.</span></span>

<span data-ttu-id="d8a9b-222">残りの手順は、サービス インスタンスを永続ストレージに保存することです。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-222">What is left is a way to save the service instance to the persistent storage.</span></span> <span data-ttu-id="d8a9b-223">既に説明したとおり、`IStorageManager` 実装に状態を保存するには、あらかじめ必要な機能があります。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-223">As discussed previously, there is already the required functionality to save the state in an `IStorageManager` implementation.</span></span> <span data-ttu-id="d8a9b-224">これを WCF ランタイムと統合する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-224">We now must integrate this with the WCF runtime.</span></span> <span data-ttu-id="d8a9b-225">これを行うには、サービス実装クラスのメソッドに適用可能な別の属性が必要です。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-225">Another attribute is required that is applicable to the methods in the service implementation class.</span></span> <span data-ttu-id="d8a9b-226">つまりこの属性は、サービス インスタンスの状態を変更するメソッドに適用できることが必要です。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-226">This attribute is supposed to be applied to the methods that change the state of the service instance.</span></span>

<span data-ttu-id="d8a9b-227">この機能は、`SaveStateAttribute` クラスに実装されています。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-227">The `SaveStateAttribute` class implements this functionality.</span></span> <span data-ttu-id="d8a9b-228">また、各`IOperationBehavior`操作の WCF ランタイムを変更するクラスも実装します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-228">It also implements `IOperationBehavior` class to modify the WCF runtime for each operation.</span></span> <span data-ttu-id="d8a9b-229">メソッドがこの属性でマークされている場合、適切な`ApplyBehavior` `DispatchOperation`が構築されている間、WCF ランタイムはメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-229">When a method is marked with this attribute, the WCF runtime invokes the `ApplyBehavior` method while the appropriate `DispatchOperation` is being constructed.</span></span> <span data-ttu-id="d8a9b-230">このメソッドの実装には、次の1行のコードがあります。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-230">There is a single line of code in this method implementation:</span></span>

```csharp
dispatch.Invoker = new OperationInvoker(dispatch.Invoker);
```

<span data-ttu-id="d8a9b-231">この手順により `OperationInvoker` 型のインスタンスが作成され、作成される `Invoker` の `DispatchOperation` プロパティに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-231">This instruction creates an instance of `OperationInvoker` type and assigns it to the `Invoker` property of the `DispatchOperation` being constructed.</span></span> <span data-ttu-id="d8a9b-232">`OperationInvoker` クラスは、`DispatchOperation` 用に作成された既定の操作呼び出しのラッパーです。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-232">The `OperationInvoker` class is a wrapper for the default operation invoker created for the `DispatchOperation`.</span></span> <span data-ttu-id="d8a9b-233">このクラスによって、`IOperationInvoker` インターフェイスが実装されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-233">This class implements the `IOperationInvoker` interface.</span></span> <span data-ttu-id="d8a9b-234">`Invoke`メソッドの実装では、実際のメソッド呼び出しが内部操作呼び出し元に委任されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-234">In the `Invoke` method implementation, the actual method invocation is delegated to the inner operation invoker.</span></span> <span data-ttu-id="d8a9b-235">ただし、この結果が返される前に `InstanceContext` の記憶域マネージャが使用され、サービス インスタンスが保存されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-235">However, before returning the results the storage manager in the `InstanceContext` is used to save the service instance.</span></span>

```csharp
object result = innerOperationInvoker.Invoke(instance,
    inputs, out outputs);

// Save the instance using the storage manager saved in the
// current InstanceContext.
InstanceContextExtension extension =
    OperationContext.Current.InstanceContext.Extensions.Find<InstanceContextExtension>();

extension.StorageManager.SaveInstance(extension.ContextId, instance);
return result;
```

## <a name="using-the-extension"></a><span data-ttu-id="d8a9b-236">拡張機能の使用</span><span class="sxs-lookup"><span data-stu-id="d8a9b-236">Using the Extension</span></span>

<span data-ttu-id="d8a9b-237">チャネル層とサービスモデルの両方の拡張機能が実行され、WCF アプリケーションで使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-237">Both the channel layer and service model layer extensions are done and they can now be used in WCF applications.</span></span> <span data-ttu-id="d8a9b-238">サービスは、カスタムバインドを使用してチャネルをチャネルスタックに追加し、適切な属性を使用してサービス実装クラスをマークする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-238">Services must add the channel into the channel stack using a custom binding and then mark the service implementation classes with the appropriate attributes.</span></span>

```csharp
[DurableInstanceContext]
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]
public class ShoppingCart : IShoppingCart
{
//…
     [SaveState]
     public int AddItem(string item)
     {
         //…
     }
//…
 }
```

<span data-ttu-id="d8a9b-239">クライアント アプリケーションは、カスタム バインドを使用して DurableInstanceContextChannel をチャネル スタックに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-239">Client applications must add the DurableInstanceContextChannel into the channel stack using a custom binding.</span></span> <span data-ttu-id="d8a9b-240">構成ファイル内でチャネルを宣言して構成するには、バインド要素セクションをバインド要素拡張のコレクションに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-240">To configure the channel declaratively in the configuration file, the binding element section has to be added to the binding element extensions collection.</span></span>

```xml
<system.serviceModel>
 <extensions>
   <bindingElementExtensions>
     <add name="durableInstanceContext"
type="Microsoft.ServiceModel.Samples.DurableInstanceContextBindingElementSection, DurableInstanceContextExtension, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>
   </bindingElementExtensions>
 </extensions>
</system.serviceModel>
```

<span data-ttu-id="d8a9b-241">これで、他の基本的なバインド要素と同様、このバインド要素をカスタム バインドで使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-241">Now the binding element can be used with a custom binding just like other standard binding elements:</span></span>

```xml
<bindings>
 <customBinding>
   <binding name="TextOverHttp">
     <durableInstanceContext contextType="HttpCookie"/>
     <reliableSession />
     <textMessageEncoding />
     <httpTransport />
   </binding>
 </customBinding>
</bindings>
```

## <a name="conclusion"></a><span data-ttu-id="d8a9b-242">まとめ</span><span class="sxs-lookup"><span data-stu-id="d8a9b-242">Conclusion</span></span>

<span data-ttu-id="d8a9b-243">このサンプルでは、カスタム プロトコル チャネルを作成する方法と、これを有効にするためにサービス動作をカスタマイズする方法を示しました。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-243">This sample showed how to create a custom protocol channel and how to customize the service behavior to enable it.</span></span>

<span data-ttu-id="d8a9b-244">構成セクションを使用して `IStorageManager` 実装を指定することで、この拡張機能をさらに強化することができます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-244">The extension can be further improved by letting users specify the `IStorageManager` implementation using a configuration section.</span></span> <span data-ttu-id="d8a9b-245">これにより、サービス コードを再コンパイルせずにバッキング ストアを変更できます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-245">This makes it possible to modify the backing store without recompiling the service code.</span></span>

<span data-ttu-id="d8a9b-246">さらに、インスタンスの状態をカプセル化するクラス (`StateBag` など) を実装できます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-246">Furthermore you could try to implement a class (for example, `StateBag`), which encapsulates the state of the instance.</span></span> <span data-ttu-id="d8a9b-247">このクラスにより、変更されるたびに状態が保持されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-247">That class is responsible for persisting the state whenever it changes.</span></span> <span data-ttu-id="d8a9b-248">この方法により、`SaveState` 属性の使用を回避しながら、永続する処理をより正確に実行できます (たとえば、`SaveState` 属性を含むメソッドを呼び出すたびに状態を保存するのではなく、状態が実際に変更されたときに保持できます)。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-248">This way you can avoid using the `SaveState` attribute and perform the persisting work more accurately (for example, you could persist the state when the state is actually changed rather than saving it each time when a method with the `SaveState` attribute is called).</span></span>

<span data-ttu-id="d8a9b-249">このサンプルを実行すると、次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-249">When you run the sample, the following output is displayed.</span></span> <span data-ttu-id="d8a9b-250">クライアントは、2 つの商品をショッピング カートに追加し、その後ショッピング カートにある商品の一覧をサービスから取得します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-250">The client adds two items to its shopping cart and then gets the list of items in its shopping cart from the service.</span></span> <span data-ttu-id="d8a9b-251">どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-251">Press ENTER in each console window to shut down the service and client.</span></span>

```console
Enter the name of the product: apples
Enter the name of the product: bananas

Shopping cart currently contains the following items.
apples
bananas
Press ENTER to shut down client
```

> [!NOTE]
> <span data-ttu-id="d8a9b-252">サービスを再ビルドすると、データベース ファイルが上書きされます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-252">Rebuilding the service overwrites the database file.</span></span> <span data-ttu-id="d8a9b-253">サンプルを複数回実行する間に状態が保持されていることを確認するには、実行のたびにサンプルを再ビルドしないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-253">To observe state preserved across multiple runs of the sample, be sure not to rebuild the sample between runs.</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d8a9b-254">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="d8a9b-254">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="d8a9b-255">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-255">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="d8a9b-256">ソリューションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-256">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="d8a9b-257">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-257">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

> [!NOTE]
> <span data-ttu-id="d8a9b-258">このサンプルを実行するには、SQL Server 2005 または SQL Express 2005 を実行している必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-258">You must be running SQL Server 2005 or SQL Express 2005 to run this sample.</span></span> <span data-ttu-id="d8a9b-259">SQL Server 2005 を実行している場合は、サービスの接続文字列の構成を変更する必要があります </span><span class="sxs-lookup"><span data-stu-id="d8a9b-259">If you are running SQL Server 2005, you must modify the configuration of the service's connection string.</span></span> <span data-ttu-id="d8a9b-260">複数コンピューターで実行している場合、SQL Server が必要なのはサーバー コンピューターだけです。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-260">When running cross-machine, SQL Server is only required on the server machine.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d8a9b-261">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-261">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d8a9b-262">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-262">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="d8a9b-263">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459)にアクセスして、すべての[!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (wcf) とサンプルをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-263">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d8a9b-264">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="d8a9b-264">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Durable`
