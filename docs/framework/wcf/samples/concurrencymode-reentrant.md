---
title: ConcurrencyMode 再入
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: 613a1ed827173b3915892dda54dd20ebabdf6dcf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183895"
---
# <a name="concurrencymode-reentrant"></a><span data-ttu-id="a609e-102">ConcurrencyMode 再入</span><span class="sxs-lookup"><span data-stu-id="a609e-102">ConcurrencyMode Reentrant</span></span>
<span data-ttu-id="a609e-103">このサンプルでは、サービス実装で ConcurrencyMode.Reentrant を使用する必要性と影響を示します。</span><span class="sxs-lookup"><span data-stu-id="a609e-103">This sample demonstrates the necessity and implications of using ConcurrencyMode.Reentrant on a service implementation.</span></span> <span data-ttu-id="a609e-104">ConcurrencyMode.Reentrant は、サービス (またはコールバック) が指定された時間で処理するメッセージが 1 つだけであることを示します (`ConcurencyMode.Single` に似ています)。</span><span class="sxs-lookup"><span data-stu-id="a609e-104">ConcurrencyMode.Reentrant implies that the service (or callback) processes only one message at a given time (analogous to `ConcurencyMode.Single`).</span></span> <span data-ttu-id="a609e-105">スレッドの安全性を確保するために、Windows 通信基盤 (WCF) は、他の`InstanceContext`メッセージを処理できないように、メッセージの処理をロックします。</span><span class="sxs-lookup"><span data-stu-id="a609e-105">To ensure thread safety, Windows Communication Foundation (WCF) locks the `InstanceContext` processing a message so that no other messages can be processed.</span></span> <span data-ttu-id="a609e-106">再入モードの場合、サービスが呼び出しの送信を行う直前に `InstanceContext` のロックが解除されます。これによりその後の呼び出しが可能になり (サンプルに示すように再入可能になり)、次回サービスに呼び出しが届いたときにロックされます。</span><span class="sxs-lookup"><span data-stu-id="a609e-106">In case of Reentrant mode, the `InstanceContext` is unlocked just before the service makes an outgoing call thereby allowing the subsequent call, (which can be reentrant as demonstrated in the sample) to get the lock next time it comes in to the service.</span></span> <span data-ttu-id="a609e-107">この動作を示すために、サンプルでは、クライアントとサービスが双方向コントラクトを使用してメッセージを相互に送信する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a609e-107">To demonstrate the behavior, the sample shows how a client and service can send messages between each other using a duplex contract.</span></span>  
  
 <span data-ttu-id="a609e-108">定義されているコントラクトは双方向コントラクトで、サービスによって実装される `Ping` メソッドと、クライアントによって実装されるコールバック メソッド `Pong` を含みます。</span><span class="sxs-lookup"><span data-stu-id="a609e-108">The contract defined is a duplex contract with the `Ping` method being implemented by the service and the callback method `Pong` being implemented by the client.</span></span> <span data-ttu-id="a609e-109">クライアントは、サーバーの `Ping` メソッドを呼び出します。このメソッドには、呼び出しを初期化するチック カウントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a609e-109">A client invokes the server's `Ping` method with a tick count thereby initiating the call.</span></span> <span data-ttu-id="a609e-110">サービスはチック カウントが 0 でないことを確認し、チック カウントをデクリメントしながらコールバックの `Pong` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a609e-110">The service checks whether the tick count is not equal to 0 and then invokes the callbacks `Pong` method while decrementing the tick count.</span></span> <span data-ttu-id="a609e-111">これは、サンプルの次のコードによって行います。</span><span class="sxs-lookup"><span data-stu-id="a609e-111">This is done by the following code in the sample.</span></span>  
  
```csharp
public void Ping(int ticks)  
{  
     Console.WriteLine("Ping: Ticks = " + ticks);  
     //Keep pinging back and forth till Ticks reaches 0.  
     if (ticks != 0)  
     {  
         OperationContext.Current.GetCallbackChannel<IPingPongCallback>().Pong((ticks - 1));  
     }  
}  
```  
  
 コールバックの `Pong` 実装のロジックは、`Ping` 実装のロジックと同じです。 つまり、このメソッドはチック カウントが 0 でないことを確認し、その後コールバック チャネル (この場合は、元の `Ping` メッセージの送信に使用されたチャネル) の `Ping` メソッドを呼び出し、チック カウントを 1 だけデクリメントします。 チック カウントが 0 になると、このメソッドは返されます。これによってすべての応答のラップが解除され、クライアントが呼び出して初期化した最初の呼び出しに戻されます。 <span data-ttu-id="a609e-115">これを、コールバック実装で示します。</span><span class="sxs-lookup"><span data-stu-id="a609e-115">This is shown in the callback implementation.</span></span>  
  
```csharp
public void Pong(int ticks)  
{  
    Console.WriteLine("Pong: Ticks = " + ticks);  
    if (ticks != 0)  
    {  
        //Retrieve the Callback  Channel (in this case the Channel which was used to send the  
        //original message) and make an outgoing call until ticks reaches 0.  
        IPingPong channel = OperationContext.Current.GetCallbackChannel<IPingPong>();  
        channel.Ping((ticks - 1));  
    }  
}  
```  
  
 `Ping` メソッドと `Pong` メソッドはどちらも要求/応答です。つまり、`Ping` の最初の呼び出しは、`CallbackChannel<T>.Pong()` の呼び出しが返される以前には返されません。 クライアントでは、`Pong` メソッドは、このメソッドを返す次の `Ping` 呼び出しが返される以前には返されません。 <span data-ttu-id="a609e-118">コールバックとサービスはどちらも、保留中の要求に対して応答できるように、あらかじめ要求/応答の呼び出しを送信する必要があるので、どちらの実装も ConcurrencyMode.Reentrant 動作でマークする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a609e-118">Because both the callback and the service must make outgoing request/reply calls before they can reply for the pending request, both the implementations must be marked with the ConcurrencyMode.Reentrant behavior.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a609e-119">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="a609e-119">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a609e-120">[Windows コミュニケーションファウンデーション サンプルのワンタイム セットアップ手順を](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="a609e-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a609e-121">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="a609e-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a609e-122">単一または複数のコンピューターにまたがる構成でサンプルを実行するには[、「Windows コミュニケーション ファウンデーション サンプルの実行」の手順に](../../../../docs/framework/wcf/samples/running-the-samples.md)従います。</span><span class="sxs-lookup"><span data-stu-id="a609e-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="a609e-123">対象</span><span class="sxs-lookup"><span data-stu-id="a609e-123">Demonstrates</span></span>  
 <span data-ttu-id="a609e-124">サンプルを実行するには、クライアント プロジェクトとサーバー プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="a609e-124">To run the sample, build the client and server projects.</span></span> <span data-ttu-id="a609e-125">次に、2 つのコマンド ウィンドウを開\<き、サンプル>\CS\サービス\bin\デバッグ ディレクトリと\<サンプル>\CS\クライアント\bin\デバッグ ディレクトリに変更します。</span><span class="sxs-lookup"><span data-stu-id="a609e-125">Then open two command windows and change the directories to the \<sample>\CS\Service\bin\debug and \<sample>\CS\Client\bin\debug directories.</span></span> <span data-ttu-id="a609e-126">次に、入力`service.exe`してサービスを開始し、入力引数として渡されたティックの初期値を使用して Client.exe を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a609e-126">Then start the service by typing `service.exe` and then invoke the Client.exe with the initial value of ticks passed as an input argument.</span></span> <span data-ttu-id="a609e-127">サンプルでは、チックとして 10 が出力されます。</span><span class="sxs-lookup"><span data-stu-id="a609e-127">A sample output for 10 ticks is shown.</span></span>  
  
```console  
Prompt>Service.exe  
ServiceHost Started. Press Enter to terminate service.  
Ping: Ticks = 10  
Ping: Ticks = 8  
Ping: Ticks = 6  
Ping: Ticks = 4  
Ping: Ticks = 2  
Ping: Ticks = 0  
  
Prompt>Client.exe 10  
Pong: Ticks = 9  
Pong: Ticks = 7  
Pong: Ticks = 5  
Pong: Ticks = 3  
Pong: Ticks = 1  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="a609e-128">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="a609e-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a609e-129">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a609e-129">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a609e-130">このディレクトリが存在しない場合は[、.NET Framework 4 の Windows コミュニケーション ファウンデーション (WCF) および Windows ワークフローファウンデーション (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)に移動して、すべての Windows 通信基盤 (WCF) とサンプルを[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="a609e-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a609e-131">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="a609e-131">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
