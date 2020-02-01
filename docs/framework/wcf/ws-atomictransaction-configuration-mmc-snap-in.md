---
title: WS-AtomicTransaction 構成 MMC スナップイン
ms.date: 03/30/2017
ms.assetid: 23592973-1d51-44cc-b887-bf8b0d801e9e
ms.openlocfilehash: 0bcd08f9a3450c850ead941df6313526d076df2d
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921343"
---
# <a name="ws-atomictransaction-configuration-mmc-snap-in"></a><span data-ttu-id="9c644-102">Ws-atomictransaction 構成 MMC スナップイン</span><span class="sxs-lookup"><span data-stu-id="9c644-102">WS-AtomicTransaction Configuration MMC snap-in</span></span>

<span data-ttu-id="9c644-103">Ws-atomictransaction 構成 MMC スナップインは、ローカルコンピューターとリモートコンピューターの両方で ws-atomictransaction 設定の一部を構成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="9c644-103">The WS-AtomicTransaction Configuration MMC snap-in is used to configure a portion of the WS-AtomicTransaction settings on both local and remote machines.</span></span>

## <a name="remarks"></a><span data-ttu-id="9c644-104">Remarks</span><span class="sxs-lookup"><span data-stu-id="9c644-104">Remarks</span></span>

<span data-ttu-id="9c644-105">Windows XP または Windows Server 2003 を実行している場合は、MMC スナップインが表示されます。そのためには、コントロールパネル、管理ツール、**コンポーネントサービス** の順に移動し、**マイコンピューター**を右クリックして **プロパティ** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9c644-105">If you are running Windows XP or Windows Server 2003, the MMC snap-in can be found by navigating to **Control Panel/Administrative Tools/Component Services/**, right-clicking **My Computer**, and selecting **Properties**.</span></span> <span data-ttu-id="9c644-106">これは MSDTC を構成する場合と同じ場所です。</span><span class="sxs-lookup"><span data-stu-id="9c644-106">This is the same location where you can configure the MSDTC.</span></span> <span data-ttu-id="9c644-107">構成できるオプションは、グループ化されて、 **WS-AT**タブです。</span><span class="sxs-lookup"><span data-stu-id="9c644-107">Options available for configuration are grouped under the **WS-AT** tab.</span></span>

 <span data-ttu-id="9c644-108">Windows Vista または Windows Server 2008 を実行している場合は、MMC スナップインを見つけるには、 **[スタート]** ボタンをクリックし、 **[検索]** ボックスに `dcomcnfg.exe` 入力します。</span><span class="sxs-lookup"><span data-stu-id="9c644-108">If you are running Windows Vista or Windows Server 2008, MMC snap-in can be found by clicking the **Start** button, and typing in `dcomcnfg.exe` in the **Search** box.</span></span> <span data-ttu-id="9c644-109">MMC が開いているときに移動、**マイ Computer\Distributed トランザクション コーディネーター DTC**ノードを右クリックし、**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="9c644-109">When the MMC is opened, navigate to the **My Computer\Distributed Transaction Coordinator\Local DTC** node, right click and select **Properties**.</span></span> <span data-ttu-id="9c644-110">構成できるオプションは、グループ化されて、 **WS-AT**タブです。</span><span class="sxs-lookup"><span data-stu-id="9c644-110">Options available for configuration are grouped under the **WS-AT** tab.</span></span>

 <span data-ttu-id="9c644-111">前の手順は、ローカル マシンを構成するためのスナップインを起動するために使用します。</span><span class="sxs-lookup"><span data-stu-id="9c644-111">The previous steps are used to launch the snap-in for configuring a local machine.</span></span> <span data-ttu-id="9c644-112">リモートコンピューターを構成する場合は、[**コントロールパネル]、[管理ツール]、[コンポーネントサービス**]、の順に移動し、windows XP または windows Server 2003 を実行している場合は同様の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="9c644-112">If you want to configure a remote machine, you should locate the remote machine's name in **Control Panel/Administrative Tools/Component Services/**, and perform similar steps if you are running Windows XP or Windows Server 2003.</span></span> <span data-ttu-id="9c644-113">Windows Vista または windows Server 2008 を実行している場合は、Vista と Windows Server 2008 の前の手順に従いますが、リモートコンピューターのノードの下にある **[分散トランザクション COORDINATOR\LOCAL DTC]** ノードを使用します。</span><span class="sxs-lookup"><span data-stu-id="9c644-113">If you are running Windows Vista or Windows Server 2008, follow the previous steps for Vista and Windows Server 2008, but use the **Distributed Transaction Coordinator\Local DTC** node under the remote computer's node.</span></span>

 <span data-ttu-id="9c644-114">ツールのユーザー インターフェイスを使用するには、WsatUI.dll ファイルを登録する必要があります。このファイルのパスは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9c644-114">To use the user interface provided by the tool, you have to register the WsatUI.dll file, which is located at the following path,</span></span>

 <span data-ttu-id="9c644-115">**%PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin\WsatUI.dll**</span><span class="sxs-lookup"><span data-stu-id="9c644-115">**%PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin\WsatUI.dll**</span></span>

 <span data-ttu-id="9c644-116">登録するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9c644-116">The registration can be done by the following command.</span></span>

```console
regasm.exe /codebase WsatUI.dll
```

 <span data-ttu-id="9c644-117">このツールを使用すると、WS-AtomicTransaction の基本設定を変更できます。</span><span class="sxs-lookup"><span data-stu-id="9c644-117">You can use this tool to modify the basic WS-AtomicTransaction settings.</span></span> <span data-ttu-id="9c644-118">たとえば、WS-AtomicTransaction プロトコル サポートの有効/無効の切り替え、WS-AT で使用する HTTP ポートの構成、SSL 証明書の HTTP ポートへのバインド、証明書のサブジェクト名指定による証明書の構成、トレース モードの選択とタイムアウトの既定および上限の設定を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="9c644-118">For example, you can enable and disable the WS-AtomicTransaction protocol support, configure the HTTP ports for WS-AT, bind an SSL Certificate to the HTTP port, configure certificates by specifying certificate subject names, select the Tracing mode and set default and maximum timeouts.</span></span>

 <span data-ttu-id="9c644-119">ローカルコンピューターでのみ ws-atomictransaction サポートを構成する必要がある場合は、このツールのコマンドラインバージョンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9c644-119">If you must configure WS-AtomicTransaction support on the local machine only, you can use the command-line version of this tool.</span></span> <span data-ttu-id="9c644-120">コマンドラインツールの詳細については、「ws-atomictransaction[構成ユーティリティ (wsatConfig .exe)](ws-atomictransaction-configuration-utility-wsatconfig-exe.md) 」トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c644-120">For more information about the command-line tool, see the [WS-AtomicTransaction Configuration Utility (wsatConfig.exe)](ws-atomictransaction-configuration-utility-wsatconfig-exe.md) topic.</span></span>

 <span data-ttu-id="9c644-121">MMC スナップインとコマンド ライン ツールはいずれも、すべての WS-AT 設定を構成できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="9c644-121">You should be aware that both the MMC Snap-in and the command-line tool do not support configuring all WS-AT settings.</span></span> <span data-ttu-id="9c644-122">これらの設定は、レジストリを直接変更することによってのみ編集できます。</span><span class="sxs-lookup"><span data-stu-id="9c644-122">These settings can be edited only by modifying the registry directly.</span></span> <span data-ttu-id="9c644-123">これらのレジストリ設定の詳細については、「 [ws-atomictransaction のサポートの構成](./feature-details/configuring-ws-atomic-transaction-support.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c644-123">For more information about these registry settings, see [Configuring WS-Atomic Transaction Support](./feature-details/configuring-ws-atomic-transaction-support.md).</span></span>

### <a name="user-interface-description"></a><span data-ttu-id="9c644-124">ユーザー インターフェイスの説明</span><span class="sxs-lookup"><span data-stu-id="9c644-124">User Interface Description</span></span>

<span data-ttu-id="9c644-125">**Ws-atomictransaction のトランザクションネットワークサポートを有効にする**:</span><span class="sxs-lookup"><span data-stu-id="9c644-125">**Enable WS-Atomic Transaction Network Support**:</span></span>

 <span data-ttu-id="9c644-126">このチェック ボックスをオンまたはオフに切り替えると、このスナップインのすべての GUI コンポーネントが有効または無効になります。</span><span class="sxs-lookup"><span data-stu-id="9c644-126">Toggling this checkbox enables or disables all the GUI components of this snap-in.</span></span>

 <span data-ttu-id="9c644-127">このチェック ボックスをオンにする前に、受信か送信の通信、またはその両方で [ネットワーク DTC アクセス] が有効であることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c644-127">Before you check this box, you should make sure that Network DTC Access is enabled with inbound or outbound communication, or both.</span></span> <span data-ttu-id="9c644-128">この値は、MSDTC スナップインの **[セキュリティ]** タブで確認できます。</span><span class="sxs-lookup"><span data-stu-id="9c644-128">This value can be verified in the **Security** Tab of the MSDTC snap-in.</span></span>

#### <a name="network-group-box"></a><span data-ttu-id="9c644-129">Network グループ ボックス</span><span class="sxs-lookup"><span data-stu-id="9c644-129">Network Group Box</span></span>

<span data-ttu-id="9c644-130">Network グループでは、HTTPS ポートや追加のセキュリティ設定 (SSL 暗号化など) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="9c644-130">You can specify the HTTPS port and additional security settings such as SSL encryption in the Network group.</span></span> <span data-ttu-id="9c644-131">DTC ネットワーク トランザクションが有効でない場合、このグループは無効 (灰色表示) です。</span><span class="sxs-lookup"><span data-stu-id="9c644-131">This group is disabled (grayed out) if DTC Network Transactions are not enabled.</span></span>

 <span data-ttu-id="9c644-132">**HTTPS ポート**</span><span class="sxs-lookup"><span data-stu-id="9c644-132">**HTTPS Port**</span></span>

 <span data-ttu-id="9c644-133">これは WS-AT に使用される HTTPS ポートの値です。</span><span class="sxs-lookup"><span data-stu-id="9c644-133">This is the value of the HTTPS port used for WS-AT.</span></span> <span data-ttu-id="9c644-134">有効なポートを表す値は、1 ～ 65535 の範囲内であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="9c644-134">The value must be a number in the range 1-65535 (as to represent a valid port).</span></span> <span data-ttu-id="9c644-135">HTTP ポートを変更すると、HTTP サービス構成が変更されます。つまり、前に使用していた WS-AT サービス アドレスが解放され、新しいポートに基づいて新しい WS-AT サービス アドレスが登録されます。</span><span class="sxs-lookup"><span data-stu-id="9c644-135">Changing the HTTP Port modifies the HTTP Service Configuration, which means that the previously used WS-AT Service Address is released, and a new WS-AT Service Address is registered based on the new port.</span></span> <span data-ttu-id="9c644-136">さらに、新しく選択したポートは、現在選択している SSL 証明書で暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="9c644-136">In addition, the newly selected port is encrypted with the currently selected certificate for SSL Encryption.</span></span>

> [!NOTE]
> <span data-ttu-id="9c644-137">このツールを実行する前にファイアウォールが既に有効な場合、ポートは例外の一覧に自動的に登録されます。</span><span class="sxs-lookup"><span data-stu-id="9c644-137">If you have already enabled the firewall before running this tool, the port is automatically registered in the exception list.</span></span> <span data-ttu-id="9c644-138">このツールを実行する前にファイアウォールが無効な場合、ファイアウォールに関する追加の構成はありません。</span><span class="sxs-lookup"><span data-stu-id="9c644-138">If the firewall is disabled before running this tool, nothing additional is configured regarding the firewall.</span></span>

 <span data-ttu-id="9c644-139">WS-AT の構成後にファイアウォールを有効にする場合は、このツールを再度実行し、このパラメーターを使用してポート番号を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c644-139">If you enable the firewall after configuring WS-AT, you must run this tool again and supply the port number using this parameter.</span></span> <span data-ttu-id="9c644-140">WS-AT の構成後にファイアウォールを無効にする場合は、入力を追加しないで WS-AT の動作を続行します。</span><span class="sxs-lookup"><span data-stu-id="9c644-140">If you disable the firewall after configuring, WS-AT continues to work without additional input.</span></span>

 <span data-ttu-id="9c644-141">**エンドポイント証明書**</span><span class="sxs-lookup"><span data-stu-id="9c644-141">**Endpoint Certificate**</span></span>

 <span data-ttu-id="9c644-142">**[選択**] ボタンをクリックすると、ローカルコンピューターで現在利用可能な証明書が一覧表示され、ユーザーは SSL 暗号化に使用できる証明書を選択できます。</span><span class="sxs-lookup"><span data-stu-id="9c644-142">Clicking the **Select** button displays a list with the currently available certificates on the Local Machine, allowing the user to select the certificate that can be used for SSL encryption.</span></span> <span data-ttu-id="9c644-143">証明書には、秘密キーが必要です。</span><span class="sxs-lookup"><span data-stu-id="9c644-143">The certificates must have a private key.</span></span> <span data-ttu-id="9c644-144">秘密キーがない場合は、エラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c644-144">Otherwise, you receive an error message.</span></span>

> [!NOTE]
> <span data-ttu-id="9c644-145">選択したポートに SSL 証明書を設定すると、そのポートに関連付けられたオリジナルの SSL 証明書が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="9c644-145">When you set an SSL certificate for a selected port, you overwrite the original SSL certificate associated with that port if one exists.</span></span>

 <span data-ttu-id="9c644-146">**承認されたアカウント**</span><span class="sxs-lookup"><span data-stu-id="9c644-146">**Authorized Accounts**</span></span>

 <span data-ttu-id="9c644-147">**[選択**] ボタンをクリックすると、Windows Access Control リストエディターが呼び出されます。このエディターでは、 **[参加]** 許可 グループの **[許可]** または **[拒否]** ボックスをオンにすることで、ws-atomictransaction トランザクションに参加できるユーザーまたはグループを指定できます。</span><span class="sxs-lookup"><span data-stu-id="9c644-147">Clicking the **Select** button invokes the Windows Access Control List editor, where you can specify the user or group that can participate in WS-Atomic transactions by checking the **Allow** or **Deny** box in the **Participate** permission group.</span></span>

 <span data-ttu-id="9c644-148">**承認済み証明書**</span><span class="sxs-lookup"><span data-stu-id="9c644-148">**Authorized Certificates**</span></span>

 <span data-ttu-id="9c644-149">**[選択**] ボタンをクリックすると、LocalMachine で現在利用可能な証明書の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c644-149">Clicking the **Select** button displays a list of currently available certificates on the LocalMachine.</span></span> <span data-ttu-id="9c644-150">WS-AtomicTransaction への参加が許可される証明書 ID を選択できます。</span><span class="sxs-lookup"><span data-stu-id="9c644-150">You can then select which certificate identities are allowed to participate in WS-Atomic transactions.</span></span>

#### <a name="timeout-group-box"></a><span data-ttu-id="9c644-151">Timeout グループ ボックス</span><span class="sxs-lookup"><span data-stu-id="9c644-151">Timeout Group Box</span></span>

<span data-ttu-id="9c644-152">**[タイムアウト]** グループボックスでは、ws-atomictransaction トランザクションの既定のタイムアウトと最大のタイムアウトを指定できます。</span><span class="sxs-lookup"><span data-stu-id="9c644-152">The **Timeout** group box allows you to specify the default and maximum timeout for a WS-Atomic transaction.</span></span> <span data-ttu-id="9c644-153">送信のタイムアウトの有効値は 1 ～ 3600 の範囲です。</span><span class="sxs-lookup"><span data-stu-id="9c644-153">A valid value for outgoing timeout is between 1 and 3600.</span></span> <span data-ttu-id="9c644-154">受信のタイムアウトの有効値は 0 ～ 3600 の範囲です。</span><span class="sxs-lookup"><span data-stu-id="9c644-154">A valid value for incoming timeout is between 0 and 3600.</span></span>

#### <a name="tracing-and-logging-group-box"></a><span data-ttu-id="9c644-155">グループ ボックスのトレースとログ記録</span><span class="sxs-lookup"><span data-stu-id="9c644-155">Tracing and Logging Group Box</span></span>

<span data-ttu-id="9c644-156">**[トレースとログ記録]** グループボックスを使用すると、目的のトレースとログ記録レベルを構成できます。</span><span class="sxs-lookup"><span data-stu-id="9c644-156">The **Tracing and Logging** group box allows you to configure the desired tracing and logging level.</span></span>

 <span data-ttu-id="9c644-157">**[オプション]** ボタンをクリックすると、追加の設定を指定できるページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c644-157">Clicking the **Options** button invokes a page where you can specify additional settings.</span></span>

 <span data-ttu-id="9c644-158">[**トレースレベル**の組み合わせ] ボックスを使用すると、<xref:System.Diagnostics.TraceLevel> 列挙型の任意の有効な値から選択できます。</span><span class="sxs-lookup"><span data-stu-id="9c644-158">The **Trace Level** combination box allows you to choose from any valid value of the <xref:System.Diagnostics.TraceLevel> enumeration.</span></span> <span data-ttu-id="9c644-159">また、チェック ボックスを使用して、アクティビティ トレースやアクティビティ伝達を実行するかどうかを指定したり、個人を特定する情報を収集するかどうかを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="9c644-159">You can also use the checkboxes to specify if you want to perform activity tracing, activity propagation or collect personal identifiable information.</span></span>

 <span data-ttu-id="9c644-160">**[ログセッション]** グループボックスで、ログセッションを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="9c644-160">You can also specify logging sessions in the **Logging Session** group box.</span></span>

> [!NOTE]
> <span data-ttu-id="9c644-161">別のトレース コンシューマーが WS-AT トレース プロバイダーを使用している場合は、トレース イベントの新しいログ セッションを作成できません。</span><span class="sxs-lookup"><span data-stu-id="9c644-161">When another trace consumer is using the WS-AT trace provider, you cannot create a new logging session for trace events.</span></span> <span data-ttu-id="9c644-162">このときにログ記録を構成しようとすると、エラー メッセージ "プロバイダーを有効にできませんでした。</span><span class="sxs-lookup"><span data-stu-id="9c644-162">Any attempt to configure logging during this time results in the error message "Failed to enable provider.</span></span> <span data-ttu-id="9c644-163">エラー コード: 1" が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c644-163">Error code: 1".</span></span>

 <span data-ttu-id="9c644-164">トレースとログ記録の詳細については、「[管理と診断](./diagnostics/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c644-164">For more information about tracing and logging, see [Administration and Diagnostics](./diagnostics/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9c644-165">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c644-165">See also</span></span>

- [<span data-ttu-id="9c644-166">WS-AtomicTransaction サポートの構成</span><span class="sxs-lookup"><span data-stu-id="9c644-166">Configuring WS-Atomic Transaction Support</span></span>](./feature-details/configuring-ws-atomic-transaction-support.md)
- [<span data-ttu-id="9c644-167">WS-AtomicTransaction 構成ユーティリティ (wsatConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="9c644-167">WS-AtomicTransaction Configuration Utility (wsatConfig.exe)</span></span>](ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
- [<span data-ttu-id="9c644-168">管理と診断</span><span class="sxs-lookup"><span data-stu-id="9c644-168">Administration and Diagnostics</span></span>](./diagnostics/index.md)
