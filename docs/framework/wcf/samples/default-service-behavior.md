---
title: 既定のサービスの動作
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
ms.openlocfilehash: 798231cbfddf17dd63a61f3e2a07a6490289e56f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183752"
---
# <a name="default-service-behavior"></a><span data-ttu-id="5f045-102">既定のサービスの動作</span><span class="sxs-lookup"><span data-stu-id="5f045-102">Default Service Behavior</span></span>
<span data-ttu-id="5f045-103">このサンプルでは、サービスの動作設定を構成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5f045-103">This sample demonstrates how service behavior settings can be configured.</span></span> <span data-ttu-id="5f045-104">このサンプルは、`ICalculator`サービス コントラクトを実装する[[はじめに](../../../../docs/framework/wcf/samples/getting-started-sample.md)] に基づいています。</span><span class="sxs-lookup"><span data-stu-id="5f045-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="5f045-105">このサンプルは、<xref:System.ServiceModel.ServiceBehaviorAttribute> 属性と <xref:System.ServiceModel.OperationBehaviorAttribute> 属性を使用して、サービスの動作と操作の動作を明示的に定義しています。</span><span class="sxs-lookup"><span data-stu-id="5f045-105">This sample explicitly defines service behaviors and operation behaviors using the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes.</span></span> <span data-ttu-id="5f045-106">動作の構成は、このサンプルに示すように、構成ファイルで行うことも、コード内で強制的に行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="5f045-106">You can configure behaviors in configuration files or imperatively in code (as this sample demonstrates).</span></span>  
  
 <span data-ttu-id="5f045-107">この例では、クライアントはコンソール アプリケーション (.exe) であり、サービスはインターネット インフォメーション サービス (IIS) によってホストされます。</span><span class="sxs-lookup"><span data-stu-id="5f045-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5f045-108">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f045-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5f045-109">サービス クラスは、<xref:System.ServiceModel.ServiceBehaviorAttribute> と <xref:System.ServiceModel.OperationBehaviorAttribute> を使用して動作を指定します。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f045-109">The service class specifies behaviors with the <xref:System.ServiceModel.ServiceBehaviorAttribute> and the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following code sample.</span></span> <span data-ttu-id="5f045-110">指定されたすべての値は、既定値です。</span><span class="sxs-lookup"><span data-stu-id="5f045-110">All values specified are the defaults.</span></span>  
  
```csharp
[ServiceBehavior(  
    AutomaticSessionShutdown=true,  
    ConcurrencyMode=ConcurrencyMode.Single,  
    InstanceContextMode=InstanceContextMode.PerSession,  
    IncludeExceptionDetailInFaults=false,  
    UseSynchronizationContext=true,  
    ValidateMustUnderstand=true)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(  
        TransactionAutoComplete=true,  
        TransactionScopeRequired=false,  
        Impersonation=ImpersonationOption.NotAllowed)]  
    public double Add(double n1, double n2)  
    {  
        System.Threading.Thread.Sleep(1600);  
        return n1 + n2;  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="5f045-111">サービスの動作は、<xref:System.ServiceModel.ServiceBehaviorAttribute> 属性で指定されます。</span><span class="sxs-lookup"><span data-stu-id="5f045-111">Service behaviors are specified with the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span> <span data-ttu-id="5f045-112">これらの動作のいくつかを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="5f045-112">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="5f045-113">サービスの動作</span><span class="sxs-lookup"><span data-stu-id="5f045-113">Service behavior</span></span>|<span data-ttu-id="5f045-114">説明</span><span class="sxs-lookup"><span data-stu-id="5f045-114">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|<span data-ttu-id="5f045-115">セッションをクライアントの要求で自動的にシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="5f045-115">Automatically shuts down a session at the client's request.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|<span data-ttu-id="5f045-116">各サービス インスタンスのコンカレンシー モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="5f045-116">Specifies the concurrency mode for each service instance.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|<span data-ttu-id="5f045-117">インスタンス コンテキスト モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="5f045-117">Specifies the instance context mode.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|<span data-ttu-id="5f045-118">同期コンテキストが設定されている場合、その同期コンテキストを使用するかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="5f045-118">Determines whether to use the provided synchronization context, if one is set.</span></span> <span data-ttu-id="5f045-119">Windows フォーム アプリケーションで `WindowsFormsSynchronizationContext` を使用するかどうかを制御する場合に、これを使用します。</span><span class="sxs-lookup"><span data-stu-id="5f045-119">Use this when you want to control whether to use a `WindowsFormsSynchronizationContext` in Windows Forms applications.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|<span data-ttu-id="5f045-120">一般的な未処理の実行例外を `Fault<string>` に変換してエラー メッセージとして送信するかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="5f045-120">Determines whether general unhandled execution exceptions are to be converted into a `Fault<string>` and sent as a fault message.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|<span data-ttu-id="5f045-121">トランザクションの分離レベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="5f045-121">Specifies the isolation level for transactions.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|<span data-ttu-id="5f045-122">予期しないメッセージのヘッダーがエラー状態の原因であるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="5f045-122">Determines whether unexpected message headers cause an error condition.</span></span>|  
  
 <span data-ttu-id="5f045-123">操作の動作は <xref:System.ServiceModel.OperationBehaviorAttribute> 属性を使用して指定されます。</span><span class="sxs-lookup"><span data-stu-id="5f045-123">Operation behaviors are specified by using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="5f045-124">これらの動作のいくつかを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="5f045-124">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="5f045-125">操作の動作</span><span class="sxs-lookup"><span data-stu-id="5f045-125">Operation Behavior</span></span>|<span data-ttu-id="5f045-126">説明</span><span class="sxs-lookup"><span data-stu-id="5f045-126">Description</span></span>|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|<span data-ttu-id="5f045-127">現在のトランザクションがサービス操作の完了によってコミットされるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="5f045-127">Determines whether service operation completion commits the current transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|<span data-ttu-id="5f045-128">サービス操作がクライアントからフローされたトランザクションに参加するかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="5f045-128">Determines whether the service operation enlists in a client-flowed transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|<span data-ttu-id="5f045-129">サービス操作が呼び出し元の ID を偽装するかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="5f045-129">Determines whether the service operation impersonates the caller's identity.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|<span data-ttu-id="5f045-130">サービス操作の呼び出しの開始時または終了時に、サービス インスタンスが再利用されるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="5f045-130">Determines whether service instances are recycled at the start or end of the service operation call.</span></span>|  
  
 <span data-ttu-id="5f045-131">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f045-131">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5f045-132">呼び出し間の遅延は、サービス操作で `System.Threading.Thread.Sleep()` が呼び出されることによるものです。</span><span class="sxs-lookup"><span data-stu-id="5f045-132">The delay between the calls is the result of the calls to `System.Threading.Thread.Sleep()` made in the service operations.</span></span> <span data-ttu-id="5f045-133">以降の動作サンプルでは、これらの動作の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="5f045-133">The rest of the behavior samples explain these behaviors in more detail.</span></span> <span data-ttu-id="5f045-134">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="5f045-134">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5f045-135">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="5f045-135">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5f045-136">[Windows コミュニケーションファウンデーション サンプルのワンタイム セットアップ手順を](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="5f045-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5f045-137">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="5f045-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5f045-138">単一または複数のコンピューターにまたがる構成でサンプルを実行するには[、「Windows コミュニケーション ファウンデーション サンプルの実行」の手順に](../../../../docs/framework/wcf/samples/running-the-samples.md)従います。</span><span class="sxs-lookup"><span data-stu-id="5f045-138">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5f045-139">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="5f045-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5f045-140">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="5f045-140">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5f045-141">このディレクトリが存在しない場合は[、.NET Framework 4 の Windows コミュニケーション ファウンデーション (WCF) および Windows ワークフローファウンデーション (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)に移動して、すべての Windows 通信基盤 (WCF) とサンプルを[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="5f045-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5f045-142">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="5f045-142">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
