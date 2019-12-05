---
title: フェデレーション サンプル
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: c143ad9315df94a2d836a2c2c742ffa9a7728511
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837884"
---
# <a name="federation-sample"></a><span data-ttu-id="133a7-102">フェデレーション サンプル</span><span class="sxs-lookup"><span data-stu-id="133a7-102">Federation Sample</span></span>
<span data-ttu-id="133a7-103">このサンプルではフェデレーション セキュリティを示します。</span><span class="sxs-lookup"><span data-stu-id="133a7-103">This sample demonstrates federated security.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="133a7-104">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="133a7-104">Sample Details</span></span>  
 <span data-ttu-id="133a7-105">Windows Communication Foundation (WCF) では、`wsFederationHttpBinding`を使用したフェデレーションセキュリティアーキテクチャの展開がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="133a7-105">Windows Communication Foundation (WCF) provides support for deploying federated security architectures through the `wsFederationHttpBinding`.</span></span> <span data-ttu-id="133a7-106">`wsFederationHttpBinding` は、セキュリティで保護された、信頼できる、相互運用が可能なバインディングを提供します。このバインディングでは、要求/応答の通信のための基になるトランスポート機構として HTTP を使用でき、エンコーディングのためのワイヤ形式として Text/XML を使用できます。</span><span class="sxs-lookup"><span data-stu-id="133a7-106">The `wsFederationHttpBinding` provides a secure, reliable, and interoperable binding that involves the use of HTTP as the underlying transport mechanism for request/reply communication, and Text/XML as the wire format for encoding.</span></span> <span data-ttu-id="133a7-107">WCF でのフェデレーションの詳細については、「[フェデレーション](../../../../docs/framework/wcf/feature-details/federation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="133a7-107">For more information about Federation in WCF, see [Federation](../../../../docs/framework/wcf/feature-details/federation.md).</span></span>  
  
 <span data-ttu-id="133a7-108">シナリオは、次の 4 つの部分から構成されます。</span><span class="sxs-lookup"><span data-stu-id="133a7-108">The scenario is made up of 4 pieces:</span></span>  
  
- <span data-ttu-id="133a7-109">BookStore サービス</span><span class="sxs-lookup"><span data-stu-id="133a7-109">BookStore service</span></span>  
  
- <span data-ttu-id="133a7-110">BookStore STS</span><span class="sxs-lookup"><span data-stu-id="133a7-110">BookStore STS</span></span>  
  
- <span data-ttu-id="133a7-111">HomeRealm STS</span><span class="sxs-lookup"><span data-stu-id="133a7-111">HomeRealm STS</span></span>  
  
- <span data-ttu-id="133a7-112">BookStore クライアント</span><span class="sxs-lookup"><span data-stu-id="133a7-112">BookStore Client</span></span>  
  
 <span data-ttu-id="133a7-113">BookStore サービスは、`BrowseBooks` と `BuyBook` の 2 つの操作をサポートします。</span><span class="sxs-lookup"><span data-stu-id="133a7-113">The BookStore service supports two operations, `BrowseBooks` and `BuyBook`.</span></span> <span data-ttu-id="133a7-114">サービスでは、`BrowseBooks` 操作には匿名アクセスできますが、`BuyBooks` 操作にアクセスするには認証済みのアクセス権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="133a7-114">It allows anonymous access to the `BrowseBooks` operation, but requires authenticated access to access the `BuyBooks` operation.</span></span> <span data-ttu-id="133a7-115">認証は、BookStore STS によって発行されたトークンの形式を取ります。</span><span class="sxs-lookup"><span data-stu-id="133a7-115">The authentication takes the form of a token issued by the BookStore STS.</span></span> <span data-ttu-id="133a7-116">BookStore サービス用の構成ファイルは、次のように `wsFederationHttpBinding` を使用して、クライアントを BookStore STS にポイントします。</span><span class="sxs-lookup"><span data-stu-id="133a7-116">The configuration file for the BookStore Service points clients to the BookStore STS using the `wsFederationHttpBinding`.</span></span>  
  
```xml  
<wsFederationHttpBinding>  
<!-- This is the Service binding for the BuyBooks endpoint. It redirects clients to the BookStore STS -->  
    <binding name='BuyBookBinding'>  
        <security mode="Message">  
            <message>  
                <issuerMetadata  
  address='http://localhost/FederationSample/BookStoreSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='BookStoreSTS.com'/>  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 <span data-ttu-id="133a7-117">次に BookStore STS は、HomeRealm STS によって発行されたトークンを使用した、クライアントの認証を要求します。</span><span class="sxs-lookup"><span data-stu-id="133a7-117">The BookStore STS then requires that clients authenticate using a token issued by the HomeRealm STS.</span></span> <span data-ttu-id="133a7-118">ここでも、BookStore STS 用の構成ファイルは、`wsFederationHttpBinding` を使用して、クライアントを HomeRealm STS にポイントします。</span><span class="sxs-lookup"><span data-stu-id="133a7-118">Again, the configuration file for the BookStore STS points clients to the HomeRealm STS using the `wsFederationHttpBinding`.</span></span>  
  
```xml  
<wsFederationHttpBinding>  
 <!-- This is the binding for the clients requesting tokens from this STS. It redirects clients to the HomeRealm STS -->  
    <binding name='BookStoreSTSBinding'>  
        <security mode='Message'>  
            <message>  
                <issuerMetadata  
 address='http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='HomeRealmSTS.com' />  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 <span data-ttu-id="133a7-119">`BuyBook` 操作にアクセスするときに発生するイベントの順序は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="133a7-119">The sequence of events when accessing the `BuyBook` operation is as follows:</span></span>  
  
1. <span data-ttu-id="133a7-120">クライアントは、Windows 資格情報を使用して HomeRealm STS に対する認証を行います。</span><span class="sxs-lookup"><span data-stu-id="133a7-120">The client authenticates to the HomeRealm STS using Windows credentials.</span></span>  
  
2. <span data-ttu-id="133a7-121">HomeRealm STS は、BookStore STS に対する認証に使用できるトークンを発行します。</span><span class="sxs-lookup"><span data-stu-id="133a7-121">The HomeRealm STS issues a token that can be used to authenticate to the BookStore STS.</span></span>  
  
3. <span data-ttu-id="133a7-122">クライアントは、HomeRealm STS によって発行されたトークンを使用して BookStore STS に対する認証を行います。</span><span class="sxs-lookup"><span data-stu-id="133a7-122">The client authenticates to the BookStore STS using the token issued by the HomeRealm STS.</span></span>  
  
4. <span data-ttu-id="133a7-123">BookStore STS は、BookStore サービスに対する認証に使用できるトークンを発行します。</span><span class="sxs-lookup"><span data-stu-id="133a7-123">The BookStore STS issues a token that can be used to authenticate to the BookStore Service.</span></span>  
  
5. <span data-ttu-id="133a7-124">クライアントは、BookStore STS によって発行されたトークンを使用して BookStore サービスに対する認証を行います。</span><span class="sxs-lookup"><span data-stu-id="133a7-124">The client authenticates to the BookStore service using the token issued by the BookStore STS.</span></span>  
  
6. <span data-ttu-id="133a7-125">クライアントは `BuyBook` 操作にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="133a7-125">The client accesses the `BuyBook` operation.</span></span>  
  
 <span data-ttu-id="133a7-126">このサンプルの設定および実行方法については、次の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="133a7-126">See the following instructions about how to set up and run this sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="133a7-127">このサンプルを実行するには、 **wwwroot**ディレクトリに対する書き込みアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="133a7-127">You must have Write permissions to the **wwwroot** directory to run this sample.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="133a7-128">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="133a7-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="133a7-129">SDK コマンド ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="133a7-129">Open the SDK command window.</span></span> <span data-ttu-id="133a7-130">Setup.bat をサンプルのパスで実行します。</span><span class="sxs-lookup"><span data-stu-id="133a7-130">In the sample path, run Setup.bat.</span></span> <span data-ttu-id="133a7-131">これにより、サンプルに必要な仮想ディレクトリが作成され、必要な証明書が適切な権限を付与されてインストールされます。</span><span class="sxs-lookup"><span data-stu-id="133a7-131">This creates the virtual directories required for the sample and installs the required certificates with appropriate permissions.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="133a7-132">Setup.bat バッチ ファイルは、Windows SDK コマンド プロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="133a7-132">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="133a7-133">MSSDK 環境変数が SDK のインストール ディレクトリを指している必要があります。</span><span class="sxs-lookup"><span data-stu-id="133a7-133">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="133a7-134">この環境変数は、Windows SDK コマンド プロンプトで自動設定されます。</span><span class="sxs-lookup"><span data-stu-id="133a7-134">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span> <span data-ttu-id="133a7-135">Windows Vista では、セットアップで IIS 管理者スクリプトが使用されるため、IIS 6.0 管理互換がインストールされていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="133a7-135">On Windows Vista, you must ensure that IIS 6.0 Management Compatibility is installed because the set up uses IIS administrator scripts.</span></span> <span data-ttu-id="133a7-136">Windows Vista でセットアップスクリプトを実行するには、管理者特権が必要です。</span><span class="sxs-lookup"><span data-stu-id="133a7-136">Running the set-up script on Windows Vista requires administrator privileges.</span></span>  
  
2. <span data-ttu-id="133a7-137">Visual Studio で FederationSample を開き、 **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="133a7-137">Open FederationSample.sln in Visual Studio and select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="133a7-138">これによって共通のプロジェクト ファイル、Bookstore サービス、Bookstore STS、および HomeRealm STS が作成され、IIS に展開されます。</span><span class="sxs-lookup"><span data-stu-id="133a7-138">This builds the common project files, Bookstore service, Bookstore STS, HomeRealm STS, and deploys them in IIS.</span></span> <span data-ttu-id="133a7-139">さらに Bookstore クライアント アプリケーションがビルドされ、FederationSample\BookStoreClient\bin\Debug フォルダーに実行可能ファイル BookStoreClient.exe が配置されます。</span><span class="sxs-lookup"><span data-stu-id="133a7-139">This also builds the Bookstore client application and places the executable BookStoreClient.exe in the FederationSample\BookStoreClient\bin\Debug folder.</span></span>  
  
3. <span data-ttu-id="133a7-140">BookStoreClient.exe をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="133a7-140">Double-click BookStoreClient.exe.</span></span> <span data-ttu-id="133a7-141">BookStoreClient ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="133a7-141">The BookStoreClient window is displayed.</span></span>  
  
4. <span data-ttu-id="133a7-142">書店で利用可能な書籍を参照するには、 **[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="133a7-142">You can browse the books available in the bookstore by clicking **Browse Books**.</span></span>  
  
5. <span data-ttu-id="133a7-143">特定の本を購入するには、一覧で本を選択し、 **[Book book]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="133a7-143">To purchase a particular book, select the book in the list and click **Buy Book**.</span></span> <span data-ttu-id="133a7-144">アプリケーションが起動し、HomeRealm セキュリティ トークン サービスを使用した Windows 認証によって認証を行います。</span><span class="sxs-lookup"><span data-stu-id="133a7-144">The application starts up and authenticates using Windows authentication with the HomeRealm Security Token Service.</span></span>  
  
     <span data-ttu-id="133a7-145">サンプルは、ユーザーが 15 ドル以下の本を購入できるように構成されています。</span><span class="sxs-lookup"><span data-stu-id="133a7-145">The sample is configured to allow users to purchase books that cost $15 or less.</span></span> <span data-ttu-id="133a7-146">15 ドルを超える本を購入しようとすると、クライアントは、BookStore サービスからアクセス拒否のメッセージを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="133a7-146">Attempting to buy books that cost more than $15 results in the client getting an Access Denied message from the Book Store Service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="133a7-147">サンプルでは、購入後にユーザーの与信限度額を更新しません。</span><span class="sxs-lookup"><span data-stu-id="133a7-147">The sample does not update the user’s credit limit after a purchase.</span></span> <span data-ttu-id="133a7-148">ユーザーは、(固定の) 与信限度額以内なら何度でも本を購入できます。</span><span class="sxs-lookup"><span data-stu-id="133a7-148">You can repeatedly purchase books within the user’s (fixed) credit limit.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="133a7-149">クリーンアップするには</span><span class="sxs-lookup"><span data-stu-id="133a7-149">To clean up</span></span>  
  
1. <span data-ttu-id="133a7-150">Cleanup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="133a7-150">Run Cleanup.bat.</span></span> <span data-ttu-id="133a7-151">これによって、設定中に作成された仮想ディレクトリが削除されます。同時に、設定中にインストールされた証明書も削除されます。</span><span class="sxs-lookup"><span data-stu-id="133a7-151">This deletes the virtual directories that were created during set up and also removes the certificates installed during setup.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="133a7-152">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="133a7-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="133a7-153">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="133a7-153">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="133a7-154">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459)にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) と [!INCLUDE[wf1](../../../../includes/wf1-md.md)] サンプルをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="133a7-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="133a7-155">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="133a7-155">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
