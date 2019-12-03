---
title: ローカル チャネル
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 6bc1fac22f6eed3c9acb6b86f7611cbfb4e1d371
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714882"
---
# <a name="local-channel"></a><span data-ttu-id="7b554-102">ローカル チャネル</span><span class="sxs-lookup"><span data-stu-id="7b554-102">Local Channel</span></span>
<span data-ttu-id="7b554-103">ローカルチャネルは、同じアプリケーションドメイン内の通信に使用される Windows Communication Foundation (WCF) トランスポートチャネルです。</span><span class="sxs-lookup"><span data-stu-id="7b554-103">Local Channel is a Windows Communication Foundation (WCF) transport channel that is used for communication within the same application domain.</span></span> <span data-ttu-id="7b554-104">これは、クライアントとサービスが同じアプリケーション ドメイン内で実行されており、通常の WCF チャネル スタックのオーバーヘッド (メッセージのシリアル化と逆シリアル化) を回避する必要がある場合に役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="7b554-104">This is useful for scenarios where the client and the service are running in the same application domain and the overhead of the typical WCF channel stack (serialization and deserialization of messages) must be avoided.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="7b554-105">例</span><span class="sxs-lookup"><span data-stu-id="7b554-105">Demonstrates</span></span>  
 <span data-ttu-id="7b554-106">ローカル チャネル</span><span class="sxs-lookup"><span data-stu-id="7b554-106">Local Channel</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="7b554-107">ディスカッション</span><span class="sxs-lookup"><span data-stu-id="7b554-107">Discussion</span></span>  
 <span data-ttu-id="7b554-108">このサンプルは、2 つのプロジェクト ファイルで構成されます。</span><span class="sxs-lookup"><span data-stu-id="7b554-108">The sample consists of two project files:</span></span>  
  
- <span data-ttu-id="7b554-109">**Localchannel**: 現在のアプリケーションドメイン内のローカルチャネルのプログラムによる表現。</span><span class="sxs-lookup"><span data-stu-id="7b554-109">**LocalChannel**: The programmatic representation of the local channel within the current application domain.</span></span> <span data-ttu-id="7b554-110">このプロジェクトでは、送信側コンポーネントがメッセージをメモリ内キューに入れて、受信側コンポーネントがメッセージをキューから削除して受信します。</span><span class="sxs-lookup"><span data-stu-id="7b554-110">In this project, the sending component places the message in an in-memory queue and the receiving component de-queues the message to receive it.</span></span>  
  
- <span data-ttu-id="7b554-111">**Clientandservice**: このプロジェクトは、コンソールアプリケーションでサービスをホストし、クライアントを実行して、同じアプリケーションドメイン内からサービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7b554-111">**ClientAndService**: This project hosts a service in a console application and then runs a client to call the service from within the same application domain.</span></span>  
  
 <span data-ttu-id="7b554-112">ローカル チャネルのデザインでは、速度を上げるためにチャネル スタックとシリアル化プロセスの両方がスキップされます。</span><span class="sxs-lookup"><span data-stu-id="7b554-112">The local channel design skips both the channel stack and the serialization process to increase speed.</span></span> <span data-ttu-id="7b554-113">ローカル トランスポート チャネルは、キューを使用してサービス呼び出しをクライアントからサービスに転送し、値をクライアントに返すことによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="7b554-113">The local transport channel is implemented using a queue to transport service calls from the client to the service and to return back the value to the client.</span></span> <span data-ttu-id="7b554-114">このサンプルでは、パラメーターと戻り値をシリアル化するのではなく、オブジェクトをコピーします。</span><span class="sxs-lookup"><span data-stu-id="7b554-114">Rather than serializing parameters and return values, the sample copies the objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7b554-115">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="7b554-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7b554-116">LocalChannel ソリューションをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="7b554-116">Build and run the LocalChannel solution.</span></span>  
  
2. <span data-ttu-id="7b554-117">サービス ホストが起動し、クライアントがローカル チャネルを使用してサービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7b554-117">The service host is started and the client calls the service using the local channel.</span></span> <span data-ttu-id="7b554-118">コンソール ウィンドウが表示され、サービス呼び出しの結果が示されます。</span><span class="sxs-lookup"><span data-stu-id="7b554-118">A console window appears to display the results of the service call.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7b554-119">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="7b554-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7b554-120">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="7b554-120">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="7b554-121">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459)にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) と [!INCLUDE[wf1](../../../../includes/wf1-md.md)] サンプルをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="7b554-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7b554-122">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="7b554-122">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
