---
title: アプリケーション ドメインの使用
ms.date: 03/30/2017
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
ms.openlocfilehash: 6ee02a3f27a645f19fd6a327052939586fac4aa9
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645438"
---
# <a name="using-application-domains"></a><span data-ttu-id="a789a-102">アプリケーション ドメインの使用</span><span class="sxs-lookup"><span data-stu-id="a789a-102">Using Application Domains</span></span>

<span data-ttu-id="a789a-103">アプリケーション ドメインには、共通言語ランタイムに使用できる分離の単位が用意されています。</span><span class="sxs-lookup"><span data-stu-id="a789a-103">Application domains provide a unit of isolation for the common language runtime.</span></span> <span data-ttu-id="a789a-104">アプリケーション ドメインはプロセス内で作成され、実行されます。</span><span class="sxs-lookup"><span data-stu-id="a789a-104">They are created and run inside a process.</span></span> <span data-ttu-id="a789a-105">通常、アプリケーション ドメインはランタイム ホストによって作成されます。ランタイム ホストは、ランタイムをプロセスに読み込み、アプリケーション ドメイン内でユーザー コードを実行する処理を担当します。</span><span class="sxs-lookup"><span data-stu-id="a789a-105">Application domains are usually created by a runtime host, which is an application responsible for loading the runtime into a process and executing user code within an application domain.</span></span> <span data-ttu-id="a789a-106">ランタイム ホストはプロセスと既定のアプリケーション ドメインを作成し、その中でマネージド コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="a789a-106">The runtime host creates a process and a default application domain, and runs managed code inside it.</span></span> <span data-ttu-id="a789a-107">ランタイム ホストには、ASP.NET、Microsoft Internet Explorer、Windows シェルなどがあります。</span><span class="sxs-lookup"><span data-stu-id="a789a-107">Runtime hosts include ASP.NET, Microsoft Internet Explorer, and the Windows shell.</span></span>  
  
<span data-ttu-id="a789a-108">ほとんどのアプリケーションでは、独自のアプリケーション ドメインを作成する必要はありません。必要なアプリケーション ドメインがあれば、ランタイム ホストで自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="a789a-108">For most applications, you do not need to create your own application domain; the runtime host creates any necessary application domains for you.</span></span> <span data-ttu-id="a789a-109">ただし、アプリケーションでコードを分離する必要がある場合や、DLL を使用してアンロードする必要がある場合は、追加のアプリケーション ドメインを作成して構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a789a-109">However, you can create and configure additional application domains if your application needs to isolate code or to use and unload DLLs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a789a-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a789a-110">In This Section</span></span>  

[<span data-ttu-id="a789a-111">方法: アプリケーション ドメインを作成する</span><span class="sxs-lookup"><span data-stu-id="a789a-111">How to: Create an Application Domain</span></span>](how-to-create-an-application-domain.md)  
<span data-ttu-id="a789a-112">プログラムでアプリケーション ドメインを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a789a-112">Describes how to programmatically create an application domain.</span></span>  
  
[<span data-ttu-id="a789a-113">方法: アプリケーション ドメインをアンロードする</span><span class="sxs-lookup"><span data-stu-id="a789a-113">How to: Unload an Application Domain</span></span>](how-to-unload-an-application-domain.md)  
<span data-ttu-id="a789a-114">プログラムでアプリケーション ドメインをアンロードする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a789a-114">Describes how to programmatically unload an application domain.</span></span>  
  
[<span data-ttu-id="a789a-115">方法: アプリケーション ドメインを構成する</span><span class="sxs-lookup"><span data-stu-id="a789a-115">How to: Configure an Application Domain</span></span>](how-to-configure-an-application-domain.md)  
<span data-ttu-id="a789a-116">アプリケーション ドメインの構成方法の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="a789a-116">Provides an introduction to configuring an application domain.</span></span>  
  
[<span data-ttu-id="a789a-117">アプリケーション ドメインからのセットアップ情報の取得</span><span class="sxs-lookup"><span data-stu-id="a789a-117">Retrieving Setup Information from an Application Domain</span></span>](retrieve-setup-information.md)  
<span data-ttu-id="a789a-118">アプリケーション ドメインからセットアップ情報を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a789a-118">Describes how to retrieve setup information from an application domain.</span></span>  
  
[<span data-ttu-id="a789a-119">方法: アプリケーション ドメインにアセンブリを読み込む</span><span class="sxs-lookup"><span data-stu-id="a789a-119">How to: Load Assemblies into an Application Domain</span></span>](how-to-load-assemblies-into-an-application-domain.md)  
<span data-ttu-id="a789a-120">アセンブリをアプリケーション ドメインに読み込む方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a789a-120">Describes how to load an assembly into an application domain.</span></span>  
  
[<span data-ttu-id="a789a-121">方法: アセンブリから型およびメンバーの情報を取得する</span><span class="sxs-lookup"><span data-stu-id="a789a-121">How to: Obtain Type and Member Information from an Assembly</span></span>](../reflection-and-codedom/get-type-member-information.md)  
<span data-ttu-id="a789a-122">アセンブリに関する情報を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a789a-122">Describes how to retrieve information about an assembly.</span></span>  
  
[<span data-ttu-id="a789a-123">アセンブリのシャドウ コピー</span><span class="sxs-lookup"><span data-stu-id="a789a-123">Shadow Copying Assemblies</span></span>](shadow-copy-assemblies.md)  
<span data-ttu-id="a789a-124">シャドウ コピーによってアセンブリの使用中に更新する方法と、シャドウ コピーを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a789a-124">Describes how shadow copying allows updates to assemblies while they are in use, and how to configure shadow copying.</span></span>  
  
[<span data-ttu-id="a789a-125">方法: 初回例外通知を受け取る</span><span class="sxs-lookup"><span data-stu-id="a789a-125">How to: Receive First-Chance Exception Notifications</span></span>](how-to-receive-first-chance-exception-notifications.md)  
<span data-ttu-id="a789a-126">共通言語ランタイムが例外ハンドラーの検索を開始する前に、例外がスローされたことを知らせる通知を受け取る方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a789a-126">Explains how you can receive a notification that an exception has been thrown, before the common language runtime has begun searching for exception handlers.</span></span>  
  
[<span data-ttu-id="a789a-127">アセンブリ読み込みの解決</span><span class="sxs-lookup"><span data-stu-id="a789a-127">Resolving Assembly Loads</span></span>](../../standard/assembly/resolve-loads.md)  
<span data-ttu-id="a789a-128"><xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> イベントを使用してアセンブリの読み込みエラーを解決する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a789a-128">Provides guidance on using the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event to resolve assembly load failures.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a789a-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="a789a-129">Reference</span></span>  

<xref:System.AppDomain>  
<span data-ttu-id="a789a-130">アプリケーション ドメインを表現します。</span><span class="sxs-lookup"><span data-stu-id="a789a-130">Represents an application domain.</span></span> <span data-ttu-id="a789a-131">アプリケーション ドメインの作成と制御に使用するメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a789a-131">Provides methods for creating and controlling application domains.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a789a-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="a789a-132">Related Sections</span></span>  
[<span data-ttu-id="a789a-133">.NET のアセンブリ</span><span class="sxs-lookup"><span data-stu-id="a789a-133">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="a789a-134">アセンブリで実行される関数の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="a789a-134">Provides an overview of the functions performed by assemblies.</span></span>  
  
[<span data-ttu-id="a789a-135">アセンブリを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="a789a-135">Programming with Assemblies</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="a789a-136">アセンブリを作成し、署名し、その属性を設定する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a789a-136">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
[<span data-ttu-id="a789a-137">動的メソッドおよびアセンブリの出力</span><span class="sxs-lookup"><span data-stu-id="a789a-137">Emitting Dynamic Methods and Assemblies</span></span>](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
<span data-ttu-id="a789a-138">動的アセンブリの作成方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a789a-138">Describes how to create dynamic assemblies.</span></span>  
  
[<span data-ttu-id="a789a-139">アプリケーション ドメイン</span><span class="sxs-lookup"><span data-stu-id="a789a-139">Application Domains</span></span>](application-domains.md)  
<span data-ttu-id="a789a-140">アプリケーション ドメインの概念的な概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="a789a-140">Provides a conceptual overview of application domains.</span></span>  
  
[<span data-ttu-id="a789a-141">リフレクションの概要</span><span class="sxs-lookup"><span data-stu-id="a789a-141">Reflection Overview</span></span>](../reflection-and-codedom/reflection.md)  
<span data-ttu-id="a789a-142">**Reflection** クラスを使用して、アセンブリに関する情報を取得する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a789a-142">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
