---
title: .NET Framework 配置ガイド (管理者向け)
description: 管理者向けの .NET 配置ガイドをお読みください。 この情報を使用して、.NET バージョン 4.5 とそのシステム依存関係をネットワーク経由で配置します。
ms.date: 04/10/2018
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
ms.openlocfilehash: d58eac4f21e4f1069ac392aacb4e9818831e914c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622654"
---
# <a name="net-framework-deployment-guide-for-administrators"></a><span data-ttu-id="910b1-104">.NET Framework 配置ガイド (管理者向け)</span><span class="sxs-lookup"><span data-stu-id="910b1-104">.NET Framework Deployment Guide for Administrators</span></span>

<span data-ttu-id="910b1-105">この記事では、システム管理者が Microsoft Endpoint Configuration Manager を使用して .NET Framework 4.5 とそのシステムの依存関係をネットワーク経由で配置する方法を手順に沿って説明します。</span><span class="sxs-lookup"><span data-stu-id="910b1-105">This step-by-step article describes how a system administrator can deploy the .NET Framework 4.5 and its system dependencies across a network by using Microsoft Endpoint Configuration Manager.</span></span> <span data-ttu-id="910b1-106">ここでは、すべての対象のクライアント コンピューターが .NET Framework の最小要件を満たしていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="910b1-106">This article assumes that all target client computers meet the minimum requirements for the .NET Framework.</span></span> <span data-ttu-id="910b1-107">.NET Framework 4.5 のインストールに必要なソフトウェアとハードウェアの要件の一覧については、[システム要件](../get-started/system-requirements.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="910b1-107">For a list of the software and hardware requirements for installing the .NET Framework 4.5, see [System Requirements](../get-started/system-requirements.md).</span></span>

> [!NOTE]
> <span data-ttu-id="910b1-108">.NET Framework 4.5、Configuration Manager、Active Directory など、このドキュメントで言及されるソフトウェアなどにはそれぞれ、ライセンス条項が適用されます。</span><span class="sxs-lookup"><span data-stu-id="910b1-108">The software referenced in this document, including, without limitation, the .NET Framework 4.5, Configuration Manager, and Active Directory, are each subject to license terms and conditions.</span></span> <span data-ttu-id="910b1-109">このドキュメントの内容は、ライセンス条項がソフトウェアの適切なライセンス取得者によって確認され、同意されていることを前提にしています</span><span class="sxs-lookup"><span data-stu-id="910b1-109">These instructions assume that such license terms and conditions have been reviewed and accepted by the appropriate licensees of the software.</span></span> <span data-ttu-id="910b1-110">記載の内容についても、ライセンス条項は効力があるものとします。</span><span class="sxs-lookup"><span data-stu-id="910b1-110">These instructions do not waive any of the terms and conditions of such license agreements.</span></span>
>
> <span data-ttu-id="910b1-111">.NET Framework のサポートの詳細については、Microsoft サポート オンラインの [.NET Framework の公式サポート ライフサイクル ポリシー](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="910b1-111">For information about support for the .NET Framework, see [.NET Framework official support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework) on the Microsoft Support website.</span></span>

<span data-ttu-id="910b1-112">このトピックは、次のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="910b1-112">This topic contains the following sections:</span></span>

- [<span data-ttu-id="910b1-113">配置プロセス</span><span class="sxs-lookup"><span data-stu-id="910b1-113">The deployment process</span></span>](#the_deployment_process)
- [<span data-ttu-id="910b1-114">.NET Framework の配置</span><span class="sxs-lookup"><span data-stu-id="910b1-114">Deploying the .NET Framework</span></span>](#deploying_in_a_test_environment)
- [<span data-ttu-id="910b1-115">コレクションの作成</span><span class="sxs-lookup"><span data-stu-id="910b1-115">Create a collection</span></span>](#creating_a_collection)
- [<span data-ttu-id="910b1-116">パッケージとプログラムの作成</span><span class="sxs-lookup"><span data-stu-id="910b1-116">Create a package and program</span></span>](#creating_a_package)
- [<span data-ttu-id="910b1-117">配布ポイントの選択</span><span class="sxs-lookup"><span data-stu-id="910b1-117">Select a distribution point</span></span>](#select_dist_point)
- [<span data-ttu-id="910b1-118">パッケージの配置</span><span class="sxs-lookup"><span data-stu-id="910b1-118">Deploy the package</span></span>](#deploying_package)
- [<span data-ttu-id="910b1-119">リソース</span><span class="sxs-lookup"><span data-stu-id="910b1-119">Resources</span></span>](#resources)
- [<span data-ttu-id="910b1-120">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="910b1-120">Troubleshooting</span></span>](#troubleshooting)

<a name="the_deployment_process"></a>

## <a name="the-deployment-process"></a><span data-ttu-id="910b1-121">配置プロセス</span><span class="sxs-lookup"><span data-stu-id="910b1-121">The deployment process</span></span>

<span data-ttu-id="910b1-122">サポートするインフラストラクチャが整っている場合は、Configuration Manager を使用して、.NET Framework 再頒布可能パッケージをネットワーク上のコンピューターに配置します。</span><span class="sxs-lookup"><span data-stu-id="910b1-122">When you have the supporting infrastructure in place, you use Configuration Manager to deploy the .NET Framework redistributable package to computers on the network.</span></span> <span data-ttu-id="910b1-123">インフラストラクチャを構築するには、コレクション、ソフトウェアのパッケージとプログラム、配布ポイント、配置という 5 つの主要な項目を作成し定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="910b1-123">Building the infrastructure involves creating and defining five primary areas: collections, a package and program for the software, distribution points, and deployments.</span></span>

- <span data-ttu-id="910b1-124">**コレクション**は、ユーザー、ユーザー グループ、コンピューターなど、.NET Framework の配置先となる Configuration Manager リソースのグループです。</span><span class="sxs-lookup"><span data-stu-id="910b1-124">**Collections** are groups of Configuration Manager resources, such as users, user groups, or computers, to which the .NET Framework is deployed.</span></span> <span data-ttu-id="910b1-125">詳細については、Configuration Manager ドキュメント ライブラリの「[Configuration Manager のコレクションの概要](https://docs.microsoft.com/configmgr/core/clients/manage/collections/introduction-to-collections)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="910b1-125">For more information, see [Introduction to collections in Configuration Manager](https://docs.microsoft.com/configmgr/core/clients/manage/collections/introduction-to-collections) in the Configuration Manager documentation library.</span></span>

- <span data-ttu-id="910b1-126">**パッケージとプログラム**は、通常、クライアント コンピューターにインストールされるソフトウェア アプリケーションを表しますが、個々のファイル、更新プログラム、さらには個々のコマンドが含まれることがあります。</span><span class="sxs-lookup"><span data-stu-id="910b1-126">**Packages and programs** typically represent software applications to be installed on a client computer, but they might also contain individual files, updates, or even individual commands.</span></span> <span data-ttu-id="910b1-127">詳細については、Configuration Manager ドキュメント ライブラリの「[Configuration Manager のパッケージとプログラム](https://docs.microsoft.com/configmgr/apps/deploy-use/packages-and-programs)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="910b1-127">For more information, see [Packages and programs in Configuration Manager](https://docs.microsoft.com/configmgr/apps/deploy-use/packages-and-programs) in the Configuration Manager documentation library.</span></span>

- <span data-ttu-id="910b1-128">**配布ポイント**は、ソフトウェアをクライアント コンピューター上で実行するために必要なファイルを格納する Configuration Manager のサイト システムの役割です。</span><span class="sxs-lookup"><span data-stu-id="910b1-128">**Distribution points** are Configuration Manager site system roles that store files required for software to run on client computers.</span></span> <span data-ttu-id="910b1-129">Configuration Manager クライアントは、ソフトウェア配置を受け取って処理するときに、配布ポイントに接続してソフトウェアに関連するコンテンツをダウンロードし、インストール処理を開始します。</span><span class="sxs-lookup"><span data-stu-id="910b1-129">When the Configuration Manager client receives and processes a software deployment, it contacts a distribution point to download the content associated with the software and to start the installation process.</span></span> <span data-ttu-id="910b1-130">詳細については、Configuration Manager ドキュメント ライブラリの「[Configuration Manager でのコンテンツ管理の基本的な概念](https://docs.microsoft.com/configmgr/core/plan-design/hierarchy/fundamental-concepts-for-content-management)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="910b1-130">For more information, see [Fundamental concepts for content management in Configuration Manager](https://docs.microsoft.com/configmgr/core/plan-design/hierarchy/fundamental-concepts-for-content-management) in the Configuration Manager documentation library.</span></span>

- <span data-ttu-id="910b1-131">**配置**は、指定されたターゲット コレクションの該当するメンバーにソフトウェア パッケージをインストールするよう指示します。</span><span class="sxs-lookup"><span data-stu-id="910b1-131">**Deployments** instruct applicable members of the specified target collection to install the software package.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="910b1-132">このトピックの手順では、パッケージとプログラムを作成するための一般的な設定を使用していて、すべての可能な設定について説明していない場合があります。</span><span class="sxs-lookup"><span data-stu-id="910b1-132">The procedures in this topic contain typical settings for creating and deploying a package and program, and might not cover all possible settings.</span></span> <span data-ttu-id="910b1-133">その他の Configuration Manager の配置オプションについては、[Configuration Manager のドキュメント ライブラリ](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg682041%28v=technet.10%29)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="910b1-133">For other Configuration Manager deployment options, see the [Configuration Manager Documentation Library](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg682041%28v=technet.10%29).</span></span>

<a name="deploying_in_a_test_environment"></a>

## <a name="deploying-the-net-framework"></a><span data-ttu-id="910b1-134">.NET Framework の配置</span><span class="sxs-lookup"><span data-stu-id="910b1-134">Deploying the .NET Framework</span></span>

<span data-ttu-id="910b1-135">Configuration Manager を使用して、インストール処理時にユーザーが操作しない NET Framework 4.5 のサイレント インストールを配置できます。</span><span class="sxs-lookup"><span data-stu-id="910b1-135">You can use Configuration Manager to deploy a silent installation of the .NET Framework 4.5, where the users do not interact with the installation process.</span></span> <span data-ttu-id="910b1-136">この場合は、以下の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="910b1-136">Follow these steps:</span></span>

1. <span data-ttu-id="910b1-137">[コレクションを作成します](#creating_a_collection)。</span><span class="sxs-lookup"><span data-stu-id="910b1-137">[Create a collection](#creating_a_collection).</span></span>

2. <span data-ttu-id="910b1-138">[.NET Framework 再頒布可能パッケージとプログラムを作成します](#creating_a_package)。</span><span class="sxs-lookup"><span data-stu-id="910b1-138">[Create a package and program for the .NET Framework redistributable](#creating_a_package).</span></span>

3. <span data-ttu-id="910b1-139">[配布ポイントを選択します](#select_dist_point)。</span><span class="sxs-lookup"><span data-stu-id="910b1-139">[Select a distribution point](#select_dist_point).</span></span>

4. <span data-ttu-id="910b1-140">[パッケージを配置します](#deploying_package)。</span><span class="sxs-lookup"><span data-stu-id="910b1-140">[Deploy the package](#deploying_package).</span></span>

<a name="creating_a_collection"></a>

### <a name="create-a-collection"></a><span data-ttu-id="910b1-141">コレクションの作成</span><span class="sxs-lookup"><span data-stu-id="910b1-141">Create a collection</span></span>

<span data-ttu-id="910b1-142">この手順では、パッケージとプログラムを配置するコンピューターを選択し、それをデバイス コレクションにグループ化します。</span><span class="sxs-lookup"><span data-stu-id="910b1-142">In this step, you select the computers to which you will deploy the package and program, and group them into a device collection.</span></span> <span data-ttu-id="910b1-143">Configuration Manager でコレクションを作成するときは、ダイレクト メンバーシップ規則 (コレクション メンバーを手動で指定) またはクエリ規則 (指定した条件に基づいて Configuration Manager がコレクション メンバーを決定) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="910b1-143">To create a collection in Configuration Manager, you can use direct membership rules (where you manually specify the collection members) or query rules (where Configuration Manager determines the collection members based on criteria you specify).</span></span> <span data-ttu-id="910b1-144">メンバーシップ規則の詳細については、クエリ規則とダイレクト規則も含めて、Configuration Manager ドキュメント ライブラリの「[Configuration Manager のコレクションの概要](https://docs.microsoft.com/configmgr/core/clients/manage/collections/introduction-to-collections)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="910b1-144">For more information about membership rules, including queries and direct rules, see [Introduction to collections in Configuration Manager](https://docs.microsoft.com/configmgr/core/clients/manage/collections/introduction-to-collections) in the Configuration Manager Documentation Library.</span></span>

<span data-ttu-id="910b1-145">コレクションを作成するには</span><span class="sxs-lookup"><span data-stu-id="910b1-145">To create a collection:</span></span>

1. <span data-ttu-id="910b1-146">Configuration Manager コンソールで、 **[資産とコンプライアンス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="910b1-146">In the Configuration Manager console, choose **Assets and Compliance**.</span></span>

2. <span data-ttu-id="910b1-147">**[資産とコンプライアンス]** ワークスペースで、 **[デバイス コレクション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="910b1-147">In the **Assets and Compliance** workspace, choose **Device Collections**.</span></span>

3. <span data-ttu-id="910b1-148">**[ホーム]** タブの **[作成]** グループで、 **[デバイス コレクションの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="910b1-148">On the **Home** tab in the **Create** group, choose **Create Device Collection**.</span></span>

4. <span data-ttu-id="910b1-149">**デバイス コレクションの作成ウィザード**の **[全般]** ページで、コレクションの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="910b1-149">On the **General** page of the **Create Device Collection Wizard**, enter a name for the collection.</span></span>

5. <span data-ttu-id="910b1-150">**[参照]** をクリックして、限定するコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="910b1-150">Choose **Browse** to specify a limiting collection.</span></span>

6. <span data-ttu-id="910b1-151">**[メンバーシップの規則]** ページで、 **[規則の追加]** をクリックし、 **[ダイレクト規則]** をクリックして**ダイレクト メンバーシップの規則の作成ウィザード**を開きます。</span><span class="sxs-lookup"><span data-stu-id="910b1-151">On the **Membership Rules** page, choose **Add Rule**, and then choose **Direct Rule** to open the **Create Direct Membership Rule Wizard**.</span></span> <span data-ttu-id="910b1-152">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="910b1-152">Choose **Next**.</span></span>

7. <span data-ttu-id="910b1-153">**[リソースの検索]** ページで、 **[リソース クラス]** ボックスの一覧の **[システム リソース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="910b1-153">On the **Search for Resources** page, in the **Resource class** list, choose **System Resource**.</span></span> <span data-ttu-id="910b1-154">**[属性名]** ボックスの一覧の **[名前]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="910b1-154">In the **Attribute name** list, choose **Name**.</span></span> <span data-ttu-id="910b1-155">**[値]** フィールドに「`%`」と入力し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="910b1-155">In the **Value** field, enter `%`, and then choose **Next**.</span></span>

8. <span data-ttu-id="910b1-156">**[リソースの選択]** ページで、.NET Framework を配置する各コンピューターのチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="910b1-156">On the **Select Resources** page, select the check box for each computer that you want to deploy the .NET Framework to.</span></span> <span data-ttu-id="910b1-157">**[次へ]** をクリックして、ウィザードの操作を完了します。</span><span class="sxs-lookup"><span data-stu-id="910b1-157">Choose **Next**, and then complete the wizard.</span></span>

9. <span data-ttu-id="910b1-158">**デバイス コレクションの作成ウィザード**の **[メンバーシップの規則]** ページで、 **[次へ]** をクリックし、ウィザードの処理を完了します。</span><span class="sxs-lookup"><span data-stu-id="910b1-158">On the **Membership Rules** page of the **Create Device Collection Wizard**, choose **Next**, and then complete the wizard.</span></span>

<a name="creating_a_package"></a>

### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a><span data-ttu-id="910b1-159">.NET Framework 再頒布可能パッケージとプログラムの作成</span><span class="sxs-lookup"><span data-stu-id="910b1-159">Create a package and program for the .NET Framework redistributable package</span></span>

<span data-ttu-id="910b1-160">次の手順では、.NET Framework 再頒布可能パッケージを手動で作成します。</span><span class="sxs-lookup"><span data-stu-id="910b1-160">The following steps create a package for the .NET Framework redistributable manually.</span></span> <span data-ttu-id="910b1-161">パッケージには、.NET Framework をインストールするためのパラメーター、およびターゲット コンピューターへのパッケージの配布元となる場所が含まれます。</span><span class="sxs-lookup"><span data-stu-id="910b1-161">The package contains the specified parameters for installing the .NET Framework and the location from where the package will be distributed to the target computers.</span></span>

<span data-ttu-id="910b1-162">パッケージを作成するには</span><span class="sxs-lookup"><span data-stu-id="910b1-162">To create a package:</span></span>

1. <span data-ttu-id="910b1-163">Configuration Manager コンソールで、 **[ソフトウェア ライブラリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="910b1-163">In the Configuration Manager console, choose **Software Library**.</span></span>

2. <span data-ttu-id="910b1-164">**[ソフトウェア ライブラリ]** ワークスペースで、 **[アプリケーション管理]** を展開し、 **[パッケージ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="910b1-164">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>

3. <span data-ttu-id="910b1-165">**[ホーム]** タブの **[作成]** グループで、 **[パッケージの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="910b1-165">On the **Home** tab, in the **Create** group, choose **Create Package**.</span></span>

4. <span data-ttu-id="910b1-166">**パッケージとプログラムの作成ウィザード**の **[パッケージ]** ページで、次の情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="910b1-166">On the **Package** page of the **Create Package and Program Wizard**, enter the following information:</span></span>

    - <span data-ttu-id="910b1-167">名前: `.NET Framework 4.5`</span><span class="sxs-lookup"><span data-stu-id="910b1-167">Name: `.NET Framework 4.5`</span></span>

    - <span data-ttu-id="910b1-168">製造元: `Microsoft`</span><span class="sxs-lookup"><span data-stu-id="910b1-168">Manufacturer: `Microsoft`</span></span>

    - <span data-ttu-id="910b1-169">言語:</span><span class="sxs-lookup"><span data-stu-id="910b1-169">Language.</span></span> `English (US)`

5. <span data-ttu-id="910b1-170">**[このパッケージにソース ファイルを含める]** チェック ボックスをオンにし、 **[参照]** をクリックして .NET Framework のインストール ファイルを含むローカルまたはネットワーク フォルダーを選択します。</span><span class="sxs-lookup"><span data-stu-id="910b1-170">Choose **This package contains source files**, and then choose **Browse** to select the local or network folder that contains the .NET Framework installation files.</span></span> <span data-ttu-id="910b1-171">フォルダーを選択したら、 **[OK]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="910b1-171">When you have selected the folder, choose **OK**, and then choose **Next**.</span></span>

6. <span data-ttu-id="910b1-172">ウィザードの **[プログラミングの種類]** ページで、 **[標準プログラム]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="910b1-172">On the **Program Type** page of the wizard, choose **Standard Program**, and then choose **Next**.</span></span>

7. <span data-ttu-id="910b1-173">**パッケージとプログラムの作成ウィザード**の **[プログラム]** ページで、次の情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="910b1-173">On the **Program** page of the **Create Package and Program Wizard**, enter the following information:</span></span>

    1. <span data-ttu-id="910b1-174">**Name:** `.NET Framework 4.5`</span><span class="sxs-lookup"><span data-stu-id="910b1-174">**Name:** `.NET Framework 4.5`</span></span>

    2. <span data-ttu-id="910b1-175">**コマンド ライン:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (コマンド ライン オプションの説明はこの手順の後の表にあります)</span><span class="sxs-lookup"><span data-stu-id="910b1-175">**Command line:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (command-line options are described in the table after these steps)</span></span>

    3. <span data-ttu-id="910b1-176">**実行:** **[非表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="910b1-176">**Run:** Choose **Hidden**.</span></span>

    4. <span data-ttu-id="910b1-177">**プログラムの実行条件:** ユーザーがログオンしているかどうかに関係なく、プログラムを実行できることを指定するオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="910b1-177">**Program can run:** Choose the option that specifies that the program can run regardless of whether a user is logged on.</span></span>

8. <span data-ttu-id="910b1-178">**[要件]** ページで、 **[次へ]** をクリックして既定値を受け入れ、ウィザードの処理を完了します。</span><span class="sxs-lookup"><span data-stu-id="910b1-178">On the **Requirements** page, choose **Next** to accept the default values, and then complete the wizard.</span></span>

<span data-ttu-id="910b1-179">次の表は、手順 7. で指定したコマンド ライン オプションについて説明しています。</span><span class="sxs-lookup"><span data-stu-id="910b1-179">The following table describes the command-line options specified in step 7.</span></span>

|<span data-ttu-id="910b1-180">オプション</span><span class="sxs-lookup"><span data-stu-id="910b1-180">Option</span></span>|<span data-ttu-id="910b1-181">説明</span><span class="sxs-lookup"><span data-stu-id="910b1-181">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="910b1-182">**/q**</span><span class="sxs-lookup"><span data-stu-id="910b1-182">**/q**</span></span>|<span data-ttu-id="910b1-183">クワイエット モードを設定します。</span><span class="sxs-lookup"><span data-stu-id="910b1-183">Sets quiet mode.</span></span> <span data-ttu-id="910b1-184">ユーザー入力は必要なく、出力は表示されません。</span><span class="sxs-lookup"><span data-stu-id="910b1-184">No user input is required, and no output is shown.</span></span>|
|<span data-ttu-id="910b1-185">**/norestart**</span><span class="sxs-lookup"><span data-stu-id="910b1-185">**/norestart**</span></span>|<span data-ttu-id="910b1-186">セットアップ プログラムが自動的に再起動しないようにします。</span><span class="sxs-lookup"><span data-stu-id="910b1-186">Prevents the Setup program from rebooting automatically.</span></span> <span data-ttu-id="910b1-187">このオプションを使用する場合、Configuration Manager でコンピューターの再起動を処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="910b1-187">If you use this option, Configuration Manager must handle the computer restart.</span></span>|
|<span data-ttu-id="910b1-188">**/chainingpackage** *PackageName*</span><span class="sxs-lookup"><span data-stu-id="910b1-188">**/chainingpackage** *PackageName*</span></span>|<span data-ttu-id="910b1-189">チェーンを行っているパッケージの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="910b1-189">Specifies the name of the package that is doing the chaining.</span></span> <span data-ttu-id="910b1-190">この情報は、Microsoft カスタマー エクスペリエンス向上プログラム (CEIP) に申し込んだ場合のその他のインストール セッション情報と共に報告されます。</span><span class="sxs-lookup"><span data-stu-id="910b1-190">This information is reported with other installation session information for those who have signed up for the Microsoft Customer Experience Improvement Program (CEIP).</span></span> <span data-ttu-id="910b1-191">パッケージ名にスペースが含まれている場合は、区切り記号として二重引用符を使用します (例: **/chainingpackage "Chaining Product"** )。</span><span class="sxs-lookup"><span data-stu-id="910b1-191">If the package name includes spaces, use double quotation marks as delimiters; for example: **/chainingpackage "Chaining Product"**.</span></span>|

<span data-ttu-id="910b1-192">これらの手順によって、.NET Framework 4.5 という名前のパッケージが作成されます。</span><span class="sxs-lookup"><span data-stu-id="910b1-192">These steps create a package named .NET Framework 4.5.</span></span> <span data-ttu-id="910b1-193">プログラムは、.NET Framework 4.5 のサイレント インストールを配置します。</span><span class="sxs-lookup"><span data-stu-id="910b1-193">The program deploys a silent installation of the .NET Framework 4.5.</span></span> <span data-ttu-id="910b1-194">サイレント インストールでは、ユーザーはインストール プロセスと対話しないので、チェーン アプリケーションがリターン コードをキャプチャし、再起動を処理する必要があります。「[Getting Progress Information from an Installation Package](https://docs.microsoft.com/previous-versions/cc825975(v=vs.100))」 (インストール パッケージからの進行状況に関する情報の取得) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="910b1-194">In a silent installation, users do not interact with the installation process, and the chaining application has to capture the return code and handle rebooting; see [Getting Progress Information from an Installation Package](https://docs.microsoft.com/previous-versions/cc825975(v=vs.100)).</span></span>

<a name="select_dist_point"></a>

### <a name="select-a-distribution-point"></a><span data-ttu-id="910b1-195">配布ポイントの選択</span><span class="sxs-lookup"><span data-stu-id="910b1-195">Select a distribution point</span></span>

<span data-ttu-id="910b1-196">サーバーからクライアント コンピューターにパッケージとプログラムを配布するには、まずサイト システムを配布ポイントとして指定し、次にパッケージを配布ポイントに配布する必要があります。</span><span class="sxs-lookup"><span data-stu-id="910b1-196">To distribute the package and program to client computers from a server, you must first designate a site system as a distribution point and then distribute the package to the distribution point.</span></span>

<span data-ttu-id="910b1-197">以下の手順を使用して、前のセクションで作成した .NET Framework 4.5 パッケージの配布ポイントを選択します。</span><span class="sxs-lookup"><span data-stu-id="910b1-197">Use the following steps to select a distribution point for the .NET Framework 4.5 package you created in the previous section:</span></span>

1. <span data-ttu-id="910b1-198">Configuration Manager コンソールで、 **[ソフトウェア ライブラリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="910b1-198">In the Configuration Manager console, choose **Software Library**.</span></span>

2. <span data-ttu-id="910b1-199">**[ソフトウェア ライブラリ]** ワークスペースで、 **[アプリケーション管理]** を展開し、 **[パッケージ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="910b1-199">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>

3. <span data-ttu-id="910b1-200">パッケージの一覧で、前のセクションで作成したパッケージ **[.NET Framework 4.5]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="910b1-200">From the list of packages, select the package **.NET Framework 4.5** that you created in the previous section.</span></span>

4. <span data-ttu-id="910b1-201">**[ホーム]** タブの **[展開]** グループで、 **[コンテンツの配布]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="910b1-201">On the **Home** tab, in the **Deployment** group, choose **Distribute Content**.</span></span>

5. <span data-ttu-id="910b1-202">**コンテンツの配布ウィザード**の **[全般]** タブで、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="910b1-202">On the **General** tab of the **Distribute Content Wizard**, choose **Next**.</span></span>

6. <span data-ttu-id="910b1-203">ウィザードの **[コンテンツの配布先]** ページで、 **[追加]** をクリックし、 **[配布ポイント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="910b1-203">On the **Content Destination** page of the wizard, choose **Add**, and then choose **Distribution Point**.</span></span>

7. <span data-ttu-id="910b1-204">**[配布ポイントの追加]** ダイアログ ボックスで、パッケージとプログラムをホストする配布ポイントを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="910b1-204">In the **Add Distribution Points** dialog box, select the distribution point(s) that will host the package and program, and then choose **OK**.</span></span>

8. <span data-ttu-id="910b1-205">ウィザードを完了します。</span><span class="sxs-lookup"><span data-stu-id="910b1-205">Complete the wizard.</span></span>

<span data-ttu-id="910b1-206">これでパッケージには、.NET Framework 4.5 をサイレントで配置するために必要なすべての情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="910b1-206">The package now contains all the information you need to silently deploy the .NET Framework 4.5.</span></span> <span data-ttu-id="910b1-207">パッケージとプログラムを配置する前に、そのパッケージが配布ポイントにインストールされていることを確認します。Configuration Manager ドキュメント ライブラリの「[Configuration Manager で配布するコンテンツを監視する](https://docs.microsoft.com/configmgr/core/servers/deploy/configure/monitor-content-you-have-distributed)」の「コンテンツのステータスの監視」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="910b1-207">Before you deploy the package and program, verify that it was installed on the distribution point; see the "Content status monitoring" section of [Monitor content you distribute with Configuration Manager](https://docs.microsoft.com/configmgr/core/servers/deploy/configure/monitor-content-you-have-distributed) in the Configuration Manager Documentation Library.</span></span>

<a name="deploying_package"></a>

### <a name="deploy-the-package"></a><span data-ttu-id="910b1-208">パッケージの配置</span><span class="sxs-lookup"><span data-stu-id="910b1-208">Deploy the package</span></span>

<span data-ttu-id="910b1-209">.NET Framework 4.5 パッケージとプログラムを配置するには</span><span class="sxs-lookup"><span data-stu-id="910b1-209">To deploy the .NET Framework 4.5 package and program:</span></span>

1. <span data-ttu-id="910b1-210">Configuration Manager コンソールで、 **[ソフトウェア ライブラリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="910b1-210">In the Configuration Manager console, choose **Software Library**.</span></span>

2. <span data-ttu-id="910b1-211">**[ソフトウェア ライブラリ]** ワークスペースで、 **[アプリケーション管理]** を展開し、 **[パッケージ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="910b1-211">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>

3. <span data-ttu-id="910b1-212">パッケージの一覧で、作成したパッケージ **[.NET Framework 4.5]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="910b1-212">From the list of packages, select the package you created named **.NET Framework 4.5**.</span></span>

4. <span data-ttu-id="910b1-213">**[ホーム]** タブの **[展開]** グループで、 **[展開]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="910b1-213">On the **Home** tab, in the **Deployment** group, choose **Deploy**.</span></span>

5. <span data-ttu-id="910b1-214">**ソフトウェアの展開ウィザード**の **[全般]** ページで、 **[参照]** をクリックし、前に作成したコレクションを選択します。</span><span class="sxs-lookup"><span data-stu-id="910b1-214">On the **General** page of the **Deploy Software Wizard**, choose **Browse**, and then select the collection that you created earlier.</span></span> <span data-ttu-id="910b1-215">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="910b1-215">Choose **Next**.</span></span>

6. <span data-ttu-id="910b1-216">ウィザードの **[コンテンツ]** ページで、ソフトウェアを配布するポイントが表示されていることを確認し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="910b1-216">On the **Content** page of the wizard, verify that the point from which you want to distribute the software is displayed, and then choose **Next**.</span></span>

7. <span data-ttu-id="910b1-217">ウィザードの **[展開設定]** ページで、 **[操作]** が **[インストール]** に設定され、 **[目的]** が **[必須]** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="910b1-217">On the **Deployment Settings** page of the wizard, confirm that **Action** is set to **Install**, and **Purpose** is set to **Required**.</span></span> <span data-ttu-id="910b1-218">これにより、ソフトウェア パッケージがターゲット コンピューターに対する必須インストールになることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="910b1-218">This ensures that the software package will be a mandatory installation on the targeted computers.</span></span> <span data-ttu-id="910b1-219">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="910b1-219">Choose **Next**.</span></span>

8. <span data-ttu-id="910b1-220">ウィザードの **[スケジュール]** ページで、.NET Framework をインストールする時期を指定します。</span><span class="sxs-lookup"><span data-stu-id="910b1-220">On the **Scheduling** page of the wizard, specify when you want the .NET Framework to be installed.</span></span> <span data-ttu-id="910b1-221">**[新規]** をクリックしてインストール時期を指定することも、ユーザーがログオンまたはログオフしたとき、またはできるだけ早い時期にインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="910b1-221">You can choose **New** to assign an installation time, or instruct the software to install when the user logs on or off, or as soon as possible.</span></span> <span data-ttu-id="910b1-222">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="910b1-222">Choose **Next**.</span></span>

9. <span data-ttu-id="910b1-223">ウィザードの **[ユーザー側の表示と操作]** ページで、既定値を使用し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="910b1-223">On the **User Experience** page of the wizard, use the default values and choose **Next**.</span></span>

    > [!WARNING]
    > <span data-ttu-id="910b1-224">稼動環境では、配置スケジュールで異なる選択が必要になるポリシーが適用されている場合があります。</span><span class="sxs-lookup"><span data-stu-id="910b1-224">Your production environment might have policies that require different selections for the deployment schedule.</span></span> <span data-ttu-id="910b1-225">これらのオプションについて詳しくは、「[[提供情報の名前のプロパティ] の[スケジュール] タブ](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb694016%28v=technet.10%29)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="910b1-225">For information about these options, see [Advertisement Name Properties: Schedule Tab](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb694016%28v=technet.10%29).</span></span>

10. <span data-ttu-id="910b1-226">ウィザードの **[配布ポイント]** ページで、既定値を使用し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="910b1-226">On the **Distribution Points** page of the wizard, use the default values and choose **Next**.</span></span>

11. <span data-ttu-id="910b1-227">ウィザードを完了します。</span><span class="sxs-lookup"><span data-stu-id="910b1-227">Complete the wizard.</span></span> <span data-ttu-id="910b1-228">**[監視]** ワークスペースの **[展開]** ノードで配置の進行状況を監視できます。</span><span class="sxs-lookup"><span data-stu-id="910b1-228">You can monitor the progress of the deployment in the **Deployments** node of the **Monitoring** workspace.</span></span>

<span data-ttu-id="910b1-229">これで、対象のコレクションにパッケージが配置され、.NET Framework 4.5 のサイレント インストールが開始されます。</span><span class="sxs-lookup"><span data-stu-id="910b1-229">The package will now be deployed to the targeted collection and the silent installation of .NET Framework 4.5 will begin.</span></span> <span data-ttu-id="910b1-230">.NET Framework 4.5 のインストールのエラー コードについては、このトピックの「[リターン コード](#return_codes)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="910b1-230">For information about .NET Framework 4.5 installation error codes, see the [Return Codes](#return_codes) section later in this topic.</span></span>

<a name="resources"></a>

## <a name="resources"></a><span data-ttu-id="910b1-231">リソース</span><span class="sxs-lookup"><span data-stu-id="910b1-231">Resources</span></span>

<span data-ttu-id="910b1-232">.NET Framework 4.5 再頒布可能パッケージの配置をテストするためのインフラストラクチャの詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="910b1-232">For more information about the infrastructure for testing the deployment of the .NET Framework 4.5 redistributable package, see the following resources.</span></span>

<span data-ttu-id="910b1-233">**Active Directory、DNS、DHCP:**</span><span class="sxs-lookup"><span data-stu-id="910b1-233">**Active Directory, DNS, DHCP:**</span></span>

- [<span data-ttu-id="910b1-234">Active Directory Domain Services</span><span class="sxs-lookup"><span data-stu-id="910b1-234">Active Directory Domain Services</span></span>](/windows/desktop/ad/active-directory-domain-services)

- [<span data-ttu-id="910b1-235">ドメイン ネーム システム (DNS)</span><span class="sxs-lookup"><span data-stu-id="910b1-235">Domain Name System (DNS)</span></span>](/windows-server/networking/dns/dns-top)

- [<span data-ttu-id="910b1-236">動的ホスト構成プロトコル (DHCP)</span><span class="sxs-lookup"><span data-stu-id="910b1-236">Dynamic Host Configuration Protocol (DHCP)</span></span>](/windows-server/networking/technologies/dhcp/dhcp-top)

<span data-ttu-id="910b1-237">**SQL Server 2008:**</span><span class="sxs-lookup"><span data-stu-id="910b1-237">**SQL Server 2008:**</span></span>

- <span data-ttu-id="910b1-238">[SQL Server 2008 のインストール (SQL Server ビデオ)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/dd299415(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="910b1-238">[Installing SQL Server 2008 (SQL Server Video)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/dd299415(v=sql.100))</span></span>

- [<span data-ttu-id="910b1-239">SQL Server 2008 のデータベース管理者向けセキュリティ概要</span><span class="sxs-lookup"><span data-stu-id="910b1-239">SQL Server 2008 Security Overview for Database Administrators</span></span>](https://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)

<span data-ttu-id="910b1-240">**System Center 2012 Configuration Manager (管理ポイント、配布ポイント):**</span><span class="sxs-lookup"><span data-stu-id="910b1-240">**System Center 2012 Configuration Manager (Management Point, Distribution Point):**</span></span>

- [<span data-ttu-id="910b1-241">System Center 2012 Configuration Manager のサイト管理</span><span class="sxs-lookup"><span data-stu-id="910b1-241">Site Administration for System Center 2012 Configuration Manager</span></span>](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg681983%28v=technet.10%29)

- [<span data-ttu-id="910b1-242">Configuration Manager の単一サイトの計画と展開</span><span class="sxs-lookup"><span data-stu-id="910b1-242">Configuration Manager Single Site Planning and Deployment</span></span>](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb680961%28v=technet.10%29)

<span data-ttu-id="910b1-243">**Windows コンピューター用の System Center 2012 Configuration Manager クライアント:**</span><span class="sxs-lookup"><span data-stu-id="910b1-243">**System Center 2012 Configuration Manager client for Windows computers:**</span></span>

- [<span data-ttu-id="910b1-244">System Center 2012 Configuration Manager のクライアントの展開</span><span class="sxs-lookup"><span data-stu-id="910b1-244">Deploying Clients for System Center 2012 Configuration Manager</span></span>](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg699391%28v=technet.10%29)

<a name="troubleshooting"></a>

## <a name="troubleshooting"></a><span data-ttu-id="910b1-245">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="910b1-245">Troubleshooting</span></span>

### <a name="log-file-locations"></a><span data-ttu-id="910b1-246">ログ ファイルの場所</span><span class="sxs-lookup"><span data-stu-id="910b1-246">Log file locations</span></span>

<span data-ttu-id="910b1-247">.NET Framework のセットアップ中に次のログ ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="910b1-247">The following log files are generated during .NET Framework setup:</span></span>

- <span data-ttu-id="910b1-248">%temp%\Microsoft .NET Framework <*バージョン*>\*.txt</span><span class="sxs-lookup"><span data-stu-id="910b1-248">%temp%\Microsoft .NET Framework *version*\*.txt</span></span>
- <span data-ttu-id="910b1-249">%temp%\Microsoft .NET Framework <*バージョン*>\*.html</span><span class="sxs-lookup"><span data-stu-id="910b1-249">%temp%\Microsoft .NET Framework *version*\*.html</span></span>

<span data-ttu-id="910b1-250"><*バージョン*> は、インストールしている .NET Framework のバージョンです (4.5 や 4.7.2 など)。</span><span class="sxs-lookup"><span data-stu-id="910b1-250">where *version* is the version of the .NET Framework that you're installing, such as 4.5 or 4.7.2.</span></span>

<span data-ttu-id="910b1-251">.NET Framework インストール コマンドの `/log` コマンド ライン オプションを使用して、ログ ファイルが書き込まれるディレクトリを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="910b1-251">You can also specify the directory to which log files are written by using the `/log` command-line option in the .NET Framework installation command.</span></span> <span data-ttu-id="910b1-252">詳しくは、「[.NET Framework 配置ガイド (開発者向け)](deployment-guide-for-developers.md#command-line-options)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="910b1-252">For more information, see [.NET Framework deployment guide for developers](deployment-guide-for-developers.md#command-line-options).</span></span>

<span data-ttu-id="910b1-253">[ログ収集ツール](https://www.microsoft.com/download/details.aspx?id=12493)を使用して .NET Framework のログ ファイルを収集し、それらのファイルのサイズを縮小した圧縮キャビネット (.cab) ファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="910b1-253">You can use the [log collection tool](https://www.microsoft.com/download/details.aspx?id=12493) to collect the .NET Framework log files and to create a compressed cabinet (.cab) file that reduces the size of the files.</span></span>

<a name="return_codes"></a>

### <a name="return-codes"></a><span data-ttu-id="910b1-254">リターン コード</span><span class="sxs-lookup"><span data-stu-id="910b1-254">Return codes</span></span>

<span data-ttu-id="910b1-255">次の表は、.NET Framework 4.5 の再頒布可能インストール プログラムから返される最も一般的なリターン コードを示しています。</span><span class="sxs-lookup"><span data-stu-id="910b1-255">The following table lists the most common return codes from the .NET Framework 4.5 redistributable installation program.</span></span> <span data-ttu-id="910b1-256">これらのリターン コードは、すべてのバージョンのインストーラーで共通です。</span><span class="sxs-lookup"><span data-stu-id="910b1-256">The return codes are the same for all versions of the installer.</span></span>

<span data-ttu-id="910b1-257">詳細情報へのリンクについては、次の「[ダウンロードのエラー コード](#additional_error_codes)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="910b1-257">For links to detailed information, see the next section, [Download error codes](#additional_error_codes).</span></span>

|<span data-ttu-id="910b1-258">リターン コード</span><span class="sxs-lookup"><span data-stu-id="910b1-258">Return code</span></span>|<span data-ttu-id="910b1-259">説明</span><span class="sxs-lookup"><span data-stu-id="910b1-259">Description</span></span>|
|-----------------|-----------------|
|<span data-ttu-id="910b1-260">0</span><span class="sxs-lookup"><span data-stu-id="910b1-260">0</span></span>|<span data-ttu-id="910b1-261">インストールは正常に終了しました。</span><span class="sxs-lookup"><span data-stu-id="910b1-261">Installation completed successfully.</span></span>|
|<span data-ttu-id="910b1-262">1602</span><span class="sxs-lookup"><span data-stu-id="910b1-262">1602</span></span>|<span data-ttu-id="910b1-263">ユーザーがインストールをキャンセルしました。</span><span class="sxs-lookup"><span data-stu-id="910b1-263">The user canceled installation.</span></span>|
|<span data-ttu-id="910b1-264">1603</span><span class="sxs-lookup"><span data-stu-id="910b1-264">1603</span></span>|<span data-ttu-id="910b1-265">インストール中に致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="910b1-265">A fatal error occurred during installation.</span></span>|
|<span data-ttu-id="910b1-266">1641</span><span class="sxs-lookup"><span data-stu-id="910b1-266">1641</span></span>|<span data-ttu-id="910b1-267">インストールを完了するには再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="910b1-267">A restart is required to complete the installation.</span></span> <span data-ttu-id="910b1-268">このメッセージが表示された場合、操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="910b1-268">This message indicates success.</span></span>|
|<span data-ttu-id="910b1-269">3010</span><span class="sxs-lookup"><span data-stu-id="910b1-269">3010</span></span>|<span data-ttu-id="910b1-270">インストールを完了するには再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="910b1-270">A restart is required to complete the installation.</span></span> <span data-ttu-id="910b1-271">このメッセージが表示された場合、操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="910b1-271">This message indicates success.</span></span>|
|<span data-ttu-id="910b1-272">5100</span><span class="sxs-lookup"><span data-stu-id="910b1-272">5100</span></span>|<span data-ttu-id="910b1-273">ユーザーのコンピューターは、システム要件を満たしていません。</span><span class="sxs-lookup"><span data-stu-id="910b1-273">The user's computer does not meet system requirements.</span></span>|

<a name="additional_error_codes"></a>

### <a name="download-error-codes"></a><span data-ttu-id="910b1-274">ダウンロードのエラー コード</span><span class="sxs-lookup"><span data-stu-id="910b1-274">Download error codes</span></span>

- [<span data-ttu-id="910b1-275">Background Intelligent Transfer Service (BITS) のエラー コード</span><span class="sxs-lookup"><span data-stu-id="910b1-275">Background Intelligent Transfer Service (BITS) error codes</span></span>](/windows/desktop/Bits/bits-return-values)

- [<span data-ttu-id="910b1-276">URL モニカーのエラー コード</span><span class="sxs-lookup"><span data-stu-id="910b1-276">URL moniker error codes</span></span>](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775145%28v=vs.85%29)

- [<span data-ttu-id="910b1-277">WinHttp エラー コード</span><span class="sxs-lookup"><span data-stu-id="910b1-277">WinHttp error codes</span></span>](/windows/desktop/WinHttp/error-messages)

<span data-ttu-id="910b1-278">その他のエラー コード:</span><span class="sxs-lookup"><span data-stu-id="910b1-278">Other error codes:</span></span>

- [<span data-ttu-id="910b1-279">Windows インストーラーのエラー コード</span><span class="sxs-lookup"><span data-stu-id="910b1-279">Windows Installer error codes</span></span>](/windows/desktop/msi/error-codes)

- <span data-ttu-id="910b1-280">[Windows Update エージェントの結果コード](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc720442(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="910b1-280">[Windows Update Agent result codes](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc720442(v=ws.10))</span></span>

## <a name="see-also"></a><span data-ttu-id="910b1-281">関連項目</span><span class="sxs-lookup"><span data-stu-id="910b1-281">See also</span></span>

- [<span data-ttu-id="910b1-282">配置ガイド (開発者向け)</span><span class="sxs-lookup"><span data-stu-id="910b1-282">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)
- [<span data-ttu-id="910b1-283">システム要件</span><span class="sxs-lookup"><span data-stu-id="910b1-283">System Requirements</span></span>](../get-started/system-requirements.md)
