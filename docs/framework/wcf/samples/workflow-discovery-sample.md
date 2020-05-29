---
title: ワークフローの探索のサンプル
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: 1c6210472b594aec02bdf47f472a1a8b1823230c
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202071"
---
# <a name="workflow-discovery-sample"></a><span data-ttu-id="5d40b-102">ワークフローの探索のサンプル</span><span class="sxs-lookup"><span data-stu-id="5d40b-102">Workflow Discovery Sample</span></span>
<span data-ttu-id="5d40b-103">このサンプルでは、ワークフロー サービスを探索可能にする方法と、特定のサービスを検索するカスタム コード アクティビティを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5d40b-103">This sample demonstrates how to make a workflow service discoverable and how to author a custom code activity that searches for a particular service.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="5d40b-104">対象</span><span class="sxs-lookup"><span data-stu-id="5d40b-104">Demonstrates</span></span>  
 <span data-ttu-id="5d40b-105">探索検索アクティビティとワークフローの使用方法</span><span class="sxs-lookup"><span data-stu-id="5d40b-105">Discovery Find Activity and Workflow Usage</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="5d40b-106">ディスカッション</span><span class="sxs-lookup"><span data-stu-id="5d40b-106">Discussion</span></span>  
 <span data-ttu-id="5d40b-107">サンプルの最初の部分では、構成を使用してワークフロー サービスを探索可能にしています。</span><span class="sxs-lookup"><span data-stu-id="5d40b-107">In the first part of the sample, a workflow service is made discoverable using configuration.</span></span> <span data-ttu-id="5d40b-108">また、カスタム メタデータ (スコープなど) と共に構成を使用すると、サービスを適切に適用することができます。</span><span class="sxs-lookup"><span data-stu-id="5d40b-108">Configuration can also be used to apply the service appropriately with custom metadata (such as scopes).</span></span> <span data-ttu-id="5d40b-109">このサンプルは、クライアントでカスタム コード アクティビティを使用します。カスタム コード アクティビティは、探索を使用して、特定のコントラクトに一致するサービスを検索します。</span><span class="sxs-lookup"><span data-stu-id="5d40b-109">On the client, the sample uses a custom code activity, which uses Discovery to search for a service matching a particular contract.</span></span> <span data-ttu-id="5d40b-110">コード アクティビティは URI を出力します。この URI は、後で送信アクティビティで使用されます。</span><span class="sxs-lookup"><span data-stu-id="5d40b-110">The code activity outputs a URI, which is later used by a send activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5d40b-111">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="5d40b-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5d40b-112">このサンプルでは、適切な URL Acl を実行する必要がある HTTP エンドポイントを使用します (詳細については、「 [http および HTTPS の構成](../feature-details/configuring-http-and-https.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="5d40b-112">This sample uses HTTP endpoints, which must have proper URL ACLs to run (see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md) for details).</span></span> <span data-ttu-id="5d40b-113">権限のレベルが高いコマンド プロンプトで次のコマンドを実行すると、適切な ACL が追加されます。</span><span class="sxs-lookup"><span data-stu-id="5d40b-113">Executing the following command at an elevated command prompt should add the appropriate ACLs.</span></span> <span data-ttu-id="5d40b-114">シェルが変数形式を理解していない場合は、次の引数について、ドメインとユーザー名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="5d40b-114">If your shell does not understand the variable format, substitute your Domain and Username for the following arguments.</span></span>  
  
    `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`
  
> [!IMPORTANT]
> <span data-ttu-id="5d40b-115">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="5d40b-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5d40b-116">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="5d40b-116">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5d40b-117">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459)にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="5d40b-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5d40b-118">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="5d40b-118">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
