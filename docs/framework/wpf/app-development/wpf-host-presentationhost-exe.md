---
title: WPF ホスト (PresentationHost.exe)
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: bda7efbb1b7a4760199215bdb58c12b3063e290c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743400"
---
# <a name="wpf-host-presentationhostexe"></a><span data-ttu-id="65e9f-102">WPF ホスト (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="65e9f-102">WPF Host (PresentationHost.exe)</span></span>
<span data-ttu-id="65e9f-103">Windows Presentation Foundation (WPF) ホスト (PresentationHost.exe) は、互換性のあるブラウザー (Microsoft Internet Explorer 6 以降を含む) で WPF アプリケーションをホストできるようにするアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="65e9f-103">Windows Presentation Foundation (WPF) Host (PresentationHost.exe) is the application that enables WPF applications to be hosted in compatible browsers (including Microsoft Internet Explorer 6 and later).</span></span> <span data-ttu-id="65e9f-104">既定では、Windows Presentation Foundation (WPF) ホストは、ブラウザーでホストされる WPF コンテンツのシェルおよび MIME ハンドラーとして登録されます。これには次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="65e9f-104">By default, Windows Presentation Foundation (WPF) Host is registered as the shell and MIME handler for browser-hosted WPF content, which includes:</span></span>  
  
- <span data-ttu-id="65e9f-105">Loose (コンパイルされていない) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイル (.xaml)。</span><span class="sxs-lookup"><span data-stu-id="65e9f-105">Loose (uncompiled) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files (.xaml).</span></span>  
  
- <span data-ttu-id="65e9f-106">XAML ブラウザー アプリケーション (XBAP) (.xbap)。</span><span class="sxs-lookup"><span data-stu-id="65e9f-106">XAML browser application (XBAP) (.xbap).</span></span>  
  
 <span data-ttu-id="65e9f-107">これらの種類のファイルについて、Windows Presentation Foundation (WPF) ホストでは次のことが行われます。</span><span class="sxs-lookup"><span data-stu-id="65e9f-107">For files of these types, Windows Presentation Foundation (WPF) Host:</span></span>  
  
- <span data-ttu-id="65e9f-108">登録されている HTML ハンドラーを起動して、Windows Presentation Foundation (WPF) コンテンツをホストします。</span><span class="sxs-lookup"><span data-stu-id="65e9f-108">Launches the registered HTML handler to host the Windows Presentation Foundation (WPF) content.</span></span>  
  
- <span data-ttu-id="65e9f-109">適切なバージョンの必要な共通言語ランタイム (CLR) アセンブリと Windows Presentation Foundation (WPF) アセンブリを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="65e9f-109">Loads the right versions of the required common language runtime (CLR) and Windows Presentation Foundation (WPF) assemblies.</span></span>  
  
- <span data-ttu-id="65e9f-110">展開のゾーンに適切なアクセス許可レベルが設定されるようにします。</span><span class="sxs-lookup"><span data-stu-id="65e9f-110">Ensures the appropriate permission levels for the zone of deployment are in place.</span></span>  
  
 <span data-ttu-id="65e9f-111">このトピックでは、PresentationHost.exe で使用できるコマンド ライン パラメーターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="65e9f-111">This topic describes the command line parameters that can be used with PresentationHost.exe.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="65e9f-112">使用方法</span><span class="sxs-lookup"><span data-stu-id="65e9f-112">Usage</span></span>  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a><span data-ttu-id="65e9f-113">パラメーター</span><span class="sxs-lookup"><span data-stu-id="65e9f-113">Parameters</span></span>  
  
|<span data-ttu-id="65e9f-114">パラメーター</span><span class="sxs-lookup"><span data-stu-id="65e9f-114">Parameter</span></span>|<span data-ttu-id="65e9f-115">説明</span><span class="sxs-lookup"><span data-stu-id="65e9f-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="65e9f-116">ファイル名</span><span class="sxs-lookup"><span data-stu-id="65e9f-116">filename</span></span>|<span data-ttu-id="65e9f-117">アクティブにするファイルのパス。</span><span class="sxs-lookup"><span data-stu-id="65e9f-117">The path of the file to be activated.</span></span> <span data-ttu-id="65e9f-118">URI でもかまいません。</span><span class="sxs-lookup"><span data-stu-id="65e9f-118">Can also be a URI.</span></span>|  
|<span data-ttu-id="65e9f-119">-debug</span><span class="sxs-lookup"><span data-stu-id="65e9f-119">-debug</span></span>|<span data-ttu-id="65e9f-120">アプリケーションをアクティブにする場合に、このアプリケーションをストアにコミットしたり、ストアから実行しません。</span><span class="sxs-lookup"><span data-stu-id="65e9f-120">When activating an application, does not commit it to or run it from the store.</span></span> <span data-ttu-id="65e9f-121">これは、ローカル ファイルをアクティブにする場合に限って使用できます。</span><span class="sxs-lookup"><span data-stu-id="65e9f-121">This only works when a local file is activated.</span></span>|  
|<span data-ttu-id="65e9f-122">-debugSecurityZoneURL \<url></span><span class="sxs-lookup"><span data-stu-id="65e9f-122">-debugSecurityZoneURL \<url></span></span>|<span data-ttu-id="65e9f-123">アプリケーションを、指定した URL から展開されたものとしてデバッグする必要があることを PresentationHost.exe に指示するために、URL 値と共に使用します。</span><span class="sxs-lookup"><span data-stu-id="65e9f-123">Used with a URL value to indicate to PresentationHost.exe that an application should be debugged as if it were deployed from the specified URL.</span></span> <span data-ttu-id="65e9f-124">これは、展開ゾーンと起点サイトの両方を決定します。</span><span class="sxs-lookup"><span data-stu-id="65e9f-124">This determines both the deployment zone and the site of origin.</span></span>|  
|<span data-ttu-id="65e9f-125">-embedding</span><span class="sxs-lookup"><span data-stu-id="65e9f-125">-embedding</span></span>|<span data-ttu-id="65e9f-126">OLE で必要になります。</span><span class="sxs-lookup"><span data-stu-id="65e9f-126">Required by OLE.</span></span> <span data-ttu-id="65e9f-127">`-event` パラメーターまたは `-debug` パラメーターを指定した場合、`-embedding` パラメーターは内部で設定されるため、指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="65e9f-127">If the `-event` or `-debug` parameter are specified, it is not necessary to specify the `-embedding` parameter, since that parameter is set internally.</span></span>|  
|<span data-ttu-id="65e9f-128">-event \<eventname></span><span class="sxs-lookup"><span data-stu-id="65e9f-128">-event \<eventname></span></span>|<span data-ttu-id="65e9f-129">PresentationHost.exe が初期化され、WPF コンテンツをホストする準備ができた時点で、この名前のイベントを開き、シグナルを送信します。</span><span class="sxs-lookup"><span data-stu-id="65e9f-129">Open the event with this name and signal it when PresentationHost.exe is initialized and ready to host WPF content.</span></span> <span data-ttu-id="65e9f-130">PresentationHost.exe は、イベントを開く際にエラーが発生すると (そのイベントがまだ作成されていない場合など) 終了します。</span><span class="sxs-lookup"><span data-stu-id="65e9f-130">PresentationHost.exe will terminate if there was an error opening the event, such as if it has not already been created.</span></span>|  
|<span data-ttu-id="65e9f-131">-launchApplication \<url></span><span class="sxs-lookup"><span data-stu-id="65e9f-131">-launchApplication \<url></span></span>|<span data-ttu-id="65e9f-132">指定した URL から、スタンドアロンの ClickOnce アプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="65e9f-132">Launches a standalone ClickOnce application from the specified URL.</span></span> <span data-ttu-id="65e9f-133">.NET アプリケーションに関する Internet Explorer と WinINet のセキュリティ ポリシーが適用されます。</span><span class="sxs-lookup"><span data-stu-id="65e9f-133">Internet Explorer and WinINet security policy concerning .NET applications are applied.</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="65e9f-134">シナリオ</span><span class="sxs-lookup"><span data-stu-id="65e9f-134">Scenarios</span></span>  
  
### <a name="shell-handler"></a><span data-ttu-id="65e9f-135">シェル ハンドラー</span><span class="sxs-lookup"><span data-stu-id="65e9f-135">Shell Handler</span></span>  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a><span data-ttu-id="65e9f-136">MIME ハンドラー</span><span class="sxs-lookup"><span data-stu-id="65e9f-136">MIME Handler</span></span>  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a><span data-ttu-id="65e9f-137">Visual Studio によるデバッグ</span><span class="sxs-lookup"><span data-stu-id="65e9f-137">Visual Studio Debugging</span></span>  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a><span data-ttu-id="65e9f-138">Visual Studio によるゾーンでのデバッグ</span><span class="sxs-lookup"><span data-stu-id="65e9f-138">Visual Studio Debugging In Zone</span></span>  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a><span data-ttu-id="65e9f-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="65e9f-139">See also</span></span>

- [<span data-ttu-id="65e9f-140">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="65e9f-140">Security</span></span>](../security-wpf.md)
