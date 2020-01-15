---
title: '方法 : WCF アクティブ化コンポーネントをインストールして設定する'
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: e71664b4361ba28a50b29499585b20a8adbaefd2
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964466"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a><span data-ttu-id="0a34b-102">方法 : WCF アクティブ化コンポーネントをインストールして設定する</span><span class="sxs-lookup"><span data-stu-id="0a34b-102">How to: Install and Configure WCF Activation Components</span></span>

<span data-ttu-id="0a34b-103">このトピックでは、windows Vista で Windows プロセスアクティブ化サービス (WAS) をセットアップして、HTTP ネットワークプロトコルでは通信しない Windows Communication Foundation (WCF) サービスをホストするために必要な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="0a34b-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) on Windows Vista to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="0a34b-104">以降の各セクションで、この構成に関する手順について概説します。</span><span class="sxs-lookup"><span data-stu-id="0a34b-104">The following sections outline the steps for this configuration:</span></span>

- <span data-ttu-id="0a34b-105">WCF アクティブ化コンポーネントをインストール (または、のインストールを確認) します。</span><span class="sxs-lookup"><span data-stu-id="0a34b-105">Install (or confirm the installation of) the WCF activation components.</span></span>

- <span data-ttu-id="0a34b-106">非 HTTP プロトコルをサポートようにする WAS を構成します。</span><span class="sxs-lookup"><span data-stu-id="0a34b-106">Configure WAS to support a non-HTTP protocol.</span></span> <span data-ttu-id="0a34b-107">次の手順では、TCP ライセンス認証用に Windows Vista を構成します。</span><span class="sxs-lookup"><span data-stu-id="0a34b-107">The following procedure configures Windows Vista for TCP activation.</span></span>

<span data-ttu-id="0a34b-108">WAS をインストールして構成した後、「 [How to: Host a Wcf service IN was](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) 」を参照して、was を使用する非 HTTP エンドポイントを公開する wcf サービスを作成する手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a34b-108">After installing and configuring WAS, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) for the procedures to create a WCF service that exposes an non-HTTP endpoint that employs WAS.</span></span>

## <a name="to-install-the-wcf-non-http-activation-components"></a><span data-ttu-id="0a34b-109">WCF 非 HTTP アクティブ化コンポーネントをインストールするには</span><span class="sxs-lookup"><span data-stu-id="0a34b-109">To install the WCF non-HTTP activation components</span></span>

1. <span data-ttu-id="0a34b-110">をクリックして、**開始**ボタンをクリックし、をクリックし、 **コントロール パネルの** します。</span><span class="sxs-lookup"><span data-stu-id="0a34b-110">Click the **Start** button, and then click **Control Panel**.</span></span>

2. <span data-ttu-id="0a34b-111">**[プログラム]** をクリックし、 **[プログラムと機能]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a34b-111">Click **Programs**, and then click **Programs and Features**.</span></span>

3. <span data-ttu-id="0a34b-112">**[タスク]** メニューの **[Windows の機能の有効化または無効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a34b-112">On the **Tasks** menu, click **Turn Windows features on or off**.</span></span>

4. <span data-ttu-id="0a34b-113">WinFX ノードを見つけて、それを選択して展開します。</span><span class="sxs-lookup"><span data-stu-id="0a34b-113">Find the WinFX node, select and then expand it.</span></span>

5. <span data-ttu-id="0a34b-114">**[WCF 非 Http アクティブ化コンポーネント]** チェックボックスをオンにして、設定を保存します。</span><span class="sxs-lookup"><span data-stu-id="0a34b-114">Select the **WCF Non-Http Activation Components** box and save the setting.</span></span>

## <a name="to-configure-the-was-to-support-tcp-activation"></a><span data-ttu-id="0a34b-115">TCP アクティベーションをサポートするように WAS を構成するには</span><span class="sxs-lookup"><span data-stu-id="0a34b-115">To configure the WAS to support TCP activation</span></span>

1. <span data-ttu-id="0a34b-116">net.tcp アクティベーションをサポートするには、既定の Web サイトをあらかじめ net.tcp ポートにバインドしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a34b-116">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="0a34b-117">これを行うには、IIS 7.0 管理ツールセットと共にインストールされる Appcmd.exe を使用します。</span><span class="sxs-lookup"><span data-stu-id="0a34b-117">You can do this by using Appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="0a34b-118">管理者レベルのコマンド プロンプト ウィンドウで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="0a34b-118">In an administrator-level Command Prompt window, run the following command.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > <span data-ttu-id="0a34b-119">このコマンドはテキスト 1 行です。</span><span class="sxs-lookup"><span data-stu-id="0a34b-119">This command is a single line of text.</span></span> <span data-ttu-id="0a34b-120">このコマンドは、net.tcp サイト バインディングを、TCP ポート 808 で任意のホスト名をリッスンする既定の Web サイトに追加します。</span><span class="sxs-lookup"><span data-stu-id="0a34b-120">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any host name.</span></span>

2. <span data-ttu-id="0a34b-121">サイト内のすべてのアプリケーションが同じ net.tcp バインディングを共有しますが、net.tcp サポートの有効化はアプリケーションごとに指定できます。</span><span class="sxs-lookup"><span data-stu-id="0a34b-121">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="0a34b-122">アプリケーションで net.tcp を有効にするには、管理者レベルのコマンド プロンプトから、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="0a34b-122">To enable net.tcp for the application, run the following command from an administrator-level command prompt.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp
    ```

    > [!NOTE]
    > <span data-ttu-id="0a34b-123">このコマンドはテキスト 1 行です。</span><span class="sxs-lookup"><span data-stu-id="0a34b-123">This command is a single line of text.</span></span> <span data-ttu-id="0a34b-124">このコマンドは、`http://localhost/<WCF Application>` と `net.tcp://localhost/<WCF Application>`の両方を使用して、/\<*WCF アプリケーション*> アプリケーションにアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="0a34b-124">This command enables the /\<*WCF Application*> application to be accessed using both `http://localhost/<WCF Application>` and `net.tcp://localhost/<WCF Application>`.</span></span>

     <span data-ttu-id="0a34b-125">このサンプル用に追加した net.tcp サイト バインディングを削除します。</span><span class="sxs-lookup"><span data-stu-id="0a34b-125">Remove the net.tcp site binding you added for this sample.</span></span>

     <span data-ttu-id="0a34b-126">便宜上次の 2 つの手順が、サンプル ディレクトリにある RemoveNetTcpSiteBinding.cmd というバッチ ファイルに実装されています。</span><span class="sxs-lookup"><span data-stu-id="0a34b-126">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="0a34b-127">管理者レベルのコマンド プロンプト ウィンドウで次のコマンドを実行して、有効なプロトコルの一覧から net.tcp を削除します。</span><span class="sxs-lookup"><span data-stu-id="0a34b-127">Remove net.tcp from the list of enabled protocols by running the following command in an administrator-level Command Prompt window.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="0a34b-128">このコマンドはテキスト 1 行です。</span><span class="sxs-lookup"><span data-stu-id="0a34b-128">This command is a single line of text.</span></span>

    2. <span data-ttu-id="0a34b-129">権限のレベルが高いコマンド プロンプト ウィンドウで次のコマンドを実行して、net.tcp サイト バインディングを削除します。</span><span class="sxs-lookup"><span data-stu-id="0a34b-129">Remove the net.tcp site binding by running the following command in an elevated Command Prompt window:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > <span data-ttu-id="0a34b-130">このコマンドはテキスト 1 行です。</span><span class="sxs-lookup"><span data-stu-id="0a34b-130">This command is a single line of text.</span></span>

## <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a><span data-ttu-id="0a34b-131">有効なプロトコルの一覧から net.tcp を削除するには</span><span class="sxs-lookup"><span data-stu-id="0a34b-131">To remove net.tcp from the list of enabled protocols</span></span>

1. <span data-ttu-id="0a34b-132">有効なプロトコルの一覧から net.tcp を削除するには、管理者レベルのコマンド プロンプト ウィンドウで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="0a34b-132">To remove net.tcp from the list of enabled protocols, run the following command in an administrator-level Command Prompt window.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
    ```

    > [!NOTE]
    > <span data-ttu-id="0a34b-133">このコマンドはテキスト 1 行です。</span><span class="sxs-lookup"><span data-stu-id="0a34b-133">This command is a single line of text.</span></span>

## <a name="to-remove-the-nettcp-site-binding"></a><span data-ttu-id="0a34b-134">net.tcp サイト バインディングを削除するには</span><span class="sxs-lookup"><span data-stu-id="0a34b-134">To remove the net.tcp site binding</span></span>

1. <span data-ttu-id="0a34b-135">net.tcp サイト バインディングを削除するには、管理者レベルのコマンド プロンプト ウィンドウで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="0a34b-135">To remove the net.tcp site binding run the following command in an administrator-level Command Prompt window.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
    -bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > <span data-ttu-id="0a34b-136">このコマンドはテキスト 1 行です。</span><span class="sxs-lookup"><span data-stu-id="0a34b-136">This command is a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a34b-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="0a34b-137">See also</span></span>

- [<span data-ttu-id="0a34b-138">TCP アクティベーション</span><span class="sxs-lookup"><span data-stu-id="0a34b-138">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)
- [<span data-ttu-id="0a34b-139">MSMQ アクティベーション</span><span class="sxs-lookup"><span data-stu-id="0a34b-139">MSMQ Activation</span></span>](../../../../docs/framework/wcf/samples/msmq-activation.md)
- [<span data-ttu-id="0a34b-140">NamedPipe アクティベーション</span><span class="sxs-lookup"><span data-stu-id="0a34b-140">NamedPipe Activation</span></span>](../../../../docs/framework/wcf/samples/namedpipe-activation.md)
- <span data-ttu-id="0a34b-141">[AppFabric のホスティング機能](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="0a34b-141">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
