---
title: アプリケーション ドメインとアセンブリを使用したプログラミング
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
ms.openlocfilehash: 3f66eacaf30f8001cdbf3a486e5ce1c878712e2f
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644273"
---
# <a name="programming-with-application-domains-and-assemblies"></a><span data-ttu-id="aec56-102">アプリケーション ドメインとアセンブリを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="aec56-102">Programming with Application Domains and Assemblies</span></span>

<span data-ttu-id="aec56-103">Microsoft Internet Explorer、ASP.NET、Windows シェルなどのホストは、共通言語ランタイムをプロセスに読み込み、そのプロセス内で[アプリケーション ドメイン](application-domains.md)を作成します。その後 .NET Framework アプリケーションを実行するときに、そのアプリケーション ドメインにユーザー コードを読み込んでコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="aec56-103">Hosts such as Microsoft Internet Explorer, ASP.NET, and the Windows shell load the common language runtime into a process, create an [application domain](application-domains.md) in that process, and then load and execute user code in that application domain when running a .NET Framework application.</span></span> <span data-ttu-id="aec56-104">通常、アプリケーション ドメインの作成およびそれらのドメインへのアセンブリの読み込みはランタイム ホストが実行するため、考慮する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="aec56-104">In most cases, you do not have to worry about creating application domains and loading assemblies into them because the runtime host performs those tasks.</span></span>  
  
<span data-ttu-id="aec56-105">しかし、共通言語ランタイムをホストするアプリケーションを作成する場合、プログラムによってアンロードされるツールまたはコードを作成する場合、または実行時にアンロードおよび再読み込みできるプラグ可能なコンポーネントを作成する場合は、独自のアプリケーション ドメインを作成します。</span><span class="sxs-lookup"><span data-stu-id="aec56-105">However, if you are creating an application that will host the common language runtime, creating tools or code you want to unload programmatically, or creating pluggable components that can be unloaded and reloaded on the fly, you will be creating your own application domains.</span></span> <span data-ttu-id="aec56-106">ランタイム ホストを作成しない場合でも、このセクションにある、アプリケーション ドメインとアプリケーション ドメインに読み込まれたアセンブリをどのように使用するかという説明は重要です。</span><span class="sxs-lookup"><span data-stu-id="aec56-106">Even if you are not creating a runtime host, this section provides important information on how to work with application domains and assemblies loaded in these application domains.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aec56-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="aec56-107">In This Section</span></span>  

[<span data-ttu-id="aec56-108">アプリケーション ドメインとアセンブリに関する方法のトピック</span><span class="sxs-lookup"><span data-stu-id="aec56-108">Application Domains and Assemblies How-to Topics</span></span>](application-domains-and-assemblies-how-to-topics.md)  
<span data-ttu-id="aec56-109">アプリケーション ドメインとアセンブリを使用したプログラミングの概念に関するドキュメントに用意されているすべての方法トピックへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="aec56-109">Provides links to all How-to topics found in the conceptual documentation for programming with application domains and assemblies.</span></span>  
  
[<span data-ttu-id="aec56-110">アプリケーション ドメインの使用</span><span class="sxs-lookup"><span data-stu-id="aec56-110">Using Application Domains</span></span>](use.md)  
<span data-ttu-id="aec56-111">アプリケーション ドメインを作成、構成、および使用する例を示します。</span><span class="sxs-lookup"><span data-stu-id="aec56-111">Provides examples of creating, configuring, and using application domains.</span></span>  
  
[<span data-ttu-id="aec56-112">アセンブリを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="aec56-112">Programming with Assemblies</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="aec56-113">アセンブリを作成し、署名し、その属性を設定する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="aec56-113">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="aec56-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="aec56-114">Related Sections</span></span>  

[<span data-ttu-id="aec56-115">動的メソッドおよびアセンブリの出力</span><span class="sxs-lookup"><span data-stu-id="aec56-115">Emitting Dynamic Methods and Assemblies</span></span>](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
<span data-ttu-id="aec56-116">動的アセンブリの作成方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="aec56-116">Describes how to create dynamic assemblies.</span></span>  
  
[<span data-ttu-id="aec56-117">.NET のアセンブリ</span><span class="sxs-lookup"><span data-stu-id="aec56-117">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="aec56-118">アセンブリの概念的な概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="aec56-118">Provides a conceptual overview of assemblies.</span></span>  
  
[<span data-ttu-id="aec56-119">アプリケーション ドメイン</span><span class="sxs-lookup"><span data-stu-id="aec56-119">Application Domains</span></span>](application-domains.md)  
<span data-ttu-id="aec56-120">アプリケーション ドメインの概念的な概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="aec56-120">Provides a conceptual overview of application domains.</span></span>  
  
[<span data-ttu-id="aec56-121">リフレクションの概要</span><span class="sxs-lookup"><span data-stu-id="aec56-121">Reflection Overview</span></span>](../reflection-and-codedom/reflection.md)  
<span data-ttu-id="aec56-122">**Reflection** クラスを使用して、アセンブリに関する情報を取得する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="aec56-122">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
