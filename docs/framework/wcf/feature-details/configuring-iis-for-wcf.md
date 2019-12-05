---
title: Windows Communication Foundation での Internet Information Services 7.0 の構成
ms.date: 03/30/2017
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
ms.openlocfilehash: 369fd641adc91c58a676a7c2708e267366d73b41
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74838053"
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a><span data-ttu-id="7b123-102">Windows Communication Foundation での Internet Information Services 7.0 の構成</span><span class="sxs-lookup"><span data-stu-id="7b123-102">Configuring Internet Information Services 7.0 for Windows Communication Foundation</span></span>

<span data-ttu-id="7b123-103">Internet Information Services (IIS) 7.0 はモジュール設計になっており、必要なコンポーネントを選択してインストールできます。</span><span class="sxs-lookup"><span data-stu-id="7b123-103">Internet Information Services (IIS) 7.0 has a modular design that allows you to selectively install components that are required.</span></span> <span data-ttu-id="7b123-104">この設計は、Windows Vista で導入された新しいマニフェスト駆動型コンポーネント化テクノロジをベースにしています。</span><span class="sxs-lookup"><span data-stu-id="7b123-104">This design is based on the new manifest-driven componentization technology introduced in Windows Vista.</span></span> <span data-ttu-id="7b123-105">IIS 7.0 には40以上のスタンドアロン機能コンポーネントがあり、個別にインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="7b123-105">There are more than 40 standalone feature components of IIS 7.0 that can be installed independently.</span></span> <span data-ttu-id="7b123-106">これにより、IT プロフェッショナルは必要に応じてインストールをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="7b123-106">This allows IT professionals to easily customize the installation as required.</span></span> <span data-ttu-id="7b123-107">このトピックでは、Windows Communication Foundation (WCF) で使用する IIS 7.0 を構成し、どのコンポーネントが必要かを判断する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b123-107">This topic discusses how to configure IIS 7.0 for use with Windows Communication Foundation (WCF) and determine which components are required.</span></span>

## <a name="minimal-installation-installing-was"></a><span data-ttu-id="7b123-108">最小インストール : WAS のインストール</span><span class="sxs-lookup"><span data-stu-id="7b123-108">Minimal Installation: Installing WAS</span></span>
 <span data-ttu-id="7b123-109">IIS 7.0 パッケージ全体の最小インストールでは、Windows プロセスアクティブ化サービス (WAS) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="7b123-109">The minimal installation of the whole IIS 7.0 package is to install the Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="7b123-110">WAS はスタンドアロン機能であり、すべての Windows Vista オペレーティングシステム (Home Basic、Home Premium、Business、Ultimate および Enterprise) で利用できる IIS 7.0 の唯一の機能です。</span><span class="sxs-lookup"><span data-stu-id="7b123-110">WAS is a standalone feature and it is the only feature from the IIS 7.0 that is available for all Windows Vista operating systems (Home Basic, Home Premium, Business, and Ultimate and Enterprise).</span></span>

 <span data-ttu-id="7b123-111">コントロールパネルで、**プログラム** をクリックし、**プログラムと機能** の下に表示される **Windows の機能の有効化または無効化** をクリックすると、次の図のように WAS コンポーネントが一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="7b123-111">From the Control Panel, click **Programs** and then click **Turn Windows features on or off** which is listed under **Programs and Features**, the WAS component is shown in the list as in the following illustration.</span></span>

 <span data-ttu-id="7b123-112">![[機能の有効化または無効化] ダイアログ](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span><span class="sxs-lookup"><span data-stu-id="7b123-112">![Turn Features On or Off Dialog](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span></span>

 <span data-ttu-id="7b123-113">この機能には、次のサブコンポーネントがあります。</span><span class="sxs-lookup"><span data-stu-id="7b123-113">This feature has the following sub-components:</span></span>

- <span data-ttu-id="7b123-114">.NET 環境</span><span class="sxs-lookup"><span data-stu-id="7b123-114">.NET Environment</span></span>

- <span data-ttu-id="7b123-115">構成 API</span><span class="sxs-lookup"><span data-stu-id="7b123-115">Configuration APIs</span></span>

- <span data-ttu-id="7b123-116">プロセス モデル</span><span class="sxs-lookup"><span data-stu-id="7b123-116">Process Model</span></span>

 <span data-ttu-id="7b123-117">WAS のルートノードを選択した場合は、 **[プロセスモデル]** サブノードのみが既定でオンになっています。</span><span class="sxs-lookup"><span data-stu-id="7b123-117">If you select the root node of WAS, only the **Process Model** sub-node is checked by default.</span></span> <span data-ttu-id="7b123-118">このインストールでは Web サーバーをサポートしないため、WAS のみをインストールすることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7b123-118">Please note that with this installation you are only installing WAS, because there is no support for a Web server.</span></span>

 <span data-ttu-id="7b123-119">WCF または ASP.NET アプリケーションを機能させるには、 **[.Net 環境]** チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="7b123-119">To make WCF or any ASP.NET application work, check the **.NET Environment** checkbox.</span></span> <span data-ttu-id="7b123-120">これは、WCF と ASP.NET を適切に機能させるために、すべての WAS コンポーネントが必要であることを意味します。</span><span class="sxs-lookup"><span data-stu-id="7b123-120">This means that all of WAS components are required to make WCF and ASP.NET to work well.</span></span> <span data-ttu-id="7b123-121">これらのコンポーネントのいずれかを一度インストールすると、チェック ボックスは自動的にオンになります。</span><span class="sxs-lookup"><span data-stu-id="7b123-121">These are automatically checked once you install any of those components.</span></span>

## <a name="iis-70-default-installation"></a><span data-ttu-id="7b123-122">IIS 7.0 : 既定のインストール</span><span class="sxs-lookup"><span data-stu-id="7b123-122">IIS 7.0: Default Installation</span></span>
 <span data-ttu-id="7b123-123">**インターネットインフォメーションサービス**機能を確認することによって、次の図に示すように、一部のサブノードが自動的にチェックされます。</span><span class="sxs-lookup"><span data-stu-id="7b123-123">By checking the **Internet Information Services** feature, some of the sub-nodes are automatically checked as shown in the following illustration.</span></span>

 <span data-ttu-id="7b123-124">![IIS 7.0 機能の既定の設定](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span><span class="sxs-lookup"><span data-stu-id="7b123-124">![Default settings for IIS 7.0 features](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span></span>

 <span data-ttu-id="7b123-125">IIS 7.0 は既定でインストールされています。</span><span class="sxs-lookup"><span data-stu-id="7b123-125">This is the default installation of IIS 7.0.</span></span> <span data-ttu-id="7b123-126">このインストールでは、IIS 7.0 を使用して、静的コンテンツ (HTML ページやその他のコンテンツなど) を処理できます。</span><span class="sxs-lookup"><span data-stu-id="7b123-126">With this installation, you can use IIS 7.0 to service static content (such as HTML pages and other content).</span></span> <span data-ttu-id="7b123-127">ただし、ASP.NET または CGI アプリケーションを実行したり、WCF サービスをホストしたりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="7b123-127">However, you cannot run ASP.NET or CGI applications or host WCF services.</span></span>

## <a name="iis-70-installation-with-aspnet-support"></a><span data-ttu-id="7b123-128">IIS 7.0 : ASP.NET サポートを行うインストール</span><span class="sxs-lookup"><span data-stu-id="7b123-128">IIS 7.0: Installation with ASP.NET Support</span></span>
 <span data-ttu-id="7b123-129">ASP.NET を IIS 7.0 で動作させるには、ASP.NET をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b123-129">You must install ASP.NET to make ASP.NET work on IIS 7.0.</span></span> <span data-ttu-id="7b123-130">**ASP.NET**を確認すると、画面は次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="7b123-130">After checking **ASP.NET**, your screen should look like the following illustration.</span></span>

 <span data-ttu-id="7b123-131">![Asp.NET の必須設定](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span><span class="sxs-lookup"><span data-stu-id="7b123-131">![Asp.NET required settings](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span></span>

 <span data-ttu-id="7b123-132">これは、WCF と ASP.NET の両方のアプリケーションが IIS 7.0 で動作するための最小限の環境です。</span><span class="sxs-lookup"><span data-stu-id="7b123-132">This is the minimal environment for both WCF and ASP.NET applications to work in IIS 7.0.</span></span>

## <a name="iis-70-installation-with-iis-60-compatibility-components"></a><span data-ttu-id="7b123-133">IIS 7.0 : IIS 6.0 互換コンポーネントを備えたインストール</span><span class="sxs-lookup"><span data-stu-id="7b123-133">IIS 7.0: Installation with IIS 6.0 Compatibility Components</span></span>
 <span data-ttu-id="7b123-134">Visual Studio 2005 を使用しているシステム、または IIS 6.0 メタベース API を使用する仮想アプリケーションを構成するその他の自動化スクリプトまたはツール (Adsutil.vbs など) に IIS 7.0 をインストールする場合は、必ず IIS の 6.0**スクリプトツール**を確認してください。</span><span class="sxs-lookup"><span data-stu-id="7b123-134">When installing IIS 7.0 on a system with Visual Studio 2005 or some other automation scripts or tools (such as Adsutil.vbs) that configure virtual applications that use IIS 6.0 Metabase API, ensure that you check the IIS 6.0 **Scripting Tools**.</span></span> <span data-ttu-id="7b123-135">これにより、IIS 6.0**管理互換性**の他のサブノードが自動的にチェックされます。</span><span class="sxs-lookup"><span data-stu-id="7b123-135">This automatically checks the other sub-nodes of IIS 6.0 **Management Compatibility**.</span></span> <span data-ttu-id="7b123-136">次の図は、この処理が完了した後の画面を示しています。</span><span class="sxs-lookup"><span data-stu-id="7b123-136">The following illustration shows the screen after this is done:</span></span>

 <span data-ttu-id="7b123-137">![IIS 6.0 の管理互換設定](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span><span class="sxs-lookup"><span data-stu-id="7b123-137">![IIS 6.0 Management Compatibility Settings](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span></span>

 <span data-ttu-id="7b123-138">このインストールでは、IIS 7.0、ASP.NET、および WCF の機能と Web で使用可能なサンプルを使用するために必要なすべてのものが揃っています。</span><span class="sxs-lookup"><span data-stu-id="7b123-138">With this installation, you have everything required to use IIS 7.0, ASP.NET and WCF features and samples available on the Web.</span></span>

## <a name="request-limits"></a><span data-ttu-id="7b123-139">要求制限</span><span class="sxs-lookup"><span data-stu-id="7b123-139">Request Limits</span></span>
 <span data-ttu-id="7b123-140">Windows Vista と IIS 7 では、`maxUri` と `maxQueryStringSize` の設定の既定値が変更されています。</span><span class="sxs-lookup"><span data-stu-id="7b123-140">On Windows Vista with IIS 7 the default value of the `maxUri` and `maxQueryStringSize` settings have been changed.</span></span> <span data-ttu-id="7b123-141">既定では、IIS 7.0 における要求のフィルター処理で使用できる文字数は、URL が 4096 文字、クエリ文字列が 2048 文字です。</span><span class="sxs-lookup"><span data-stu-id="7b123-141">By default, request filtering in IIS 7.0 allows a URL length of 4096 characters and a query string length of 2048 characters.</span></span> <span data-ttu-id="7b123-142">これらの既定値を変更するには、App.config ファイルに次の XML を追加します。</span><span class="sxs-lookup"><span data-stu-id="7b123-142">To change these defaults add the following XML to your App.config file.</span></span>

```xml
 <system.webServer>
    <security>
        <requestFiltering>
            <requestLimits maxUrl="8192" maxQueryString="8192" />
        </requestFiltering>
    </security>
 </system.webServer>
 ```

## <a name="see-also"></a><span data-ttu-id="7b123-143">参照</span><span class="sxs-lookup"><span data-stu-id="7b123-143">See also</span></span>

- [<span data-ttu-id="7b123-144">WAS アクティベーション アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="7b123-144">WAS Activation Architecture</span></span>](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)
- [<span data-ttu-id="7b123-145">WCF で使用するための WAS を設定する</span><span class="sxs-lookup"><span data-stu-id="7b123-145">Configuring WAS for Use with WCF</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [<span data-ttu-id="7b123-146">方法 : WCF アクティブ化コンポーネントをインストールして設定する</span><span class="sxs-lookup"><span data-stu-id="7b123-146">How to: Install and Configure WCF Activation Components</span></span>](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)
- [<span data-ttu-id="7b123-147">AppFabric のホスティング機能</span><span class="sxs-lookup"><span data-stu-id="7b123-147">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
