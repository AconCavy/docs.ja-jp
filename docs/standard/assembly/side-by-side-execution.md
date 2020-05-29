---
title: アセンブリと side-by-side 実行
description: アプリケーションやコンポーネントの複数のバージョンを同じコンピューターに格納して実行する機能である、side-by-side 実行について説明します。
ms.date: 08/20/2019
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
ms.openlocfilehash: 74b5710c7e8ad60873fb83a3699ce3992ead6e07
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378626"
---
# <a name="assemblies-and-side-by-side-execution"></a><span data-ttu-id="7f3e7-103">アセンブリと side-by-side 実行</span><span class="sxs-lookup"><span data-stu-id="7f3e7-103">Assemblies and side-by-side execution</span></span>

<span data-ttu-id="7f3e7-104">side-by-side 実行は、アプリケーションやコンポーネントの複数のバージョンを同じコンピューターに格納して実行する機能です。</span><span class="sxs-lookup"><span data-stu-id="7f3e7-104">Side-by-side execution is the ability to store and execute multiple versions of an application or component on the same computer.</span></span> <span data-ttu-id="7f3e7-105">つまり、ランタイムの複数のバージョンと、特定のバージョンのランタイムを使用するアプリケーションおよびコンポーネントの複数のバージョンを、同一コンピューター上に共存させることができます。</span><span class="sxs-lookup"><span data-stu-id="7f3e7-105">This means that you can have multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, on the same computer at the same time.</span></span> <span data-ttu-id="7f3e7-106">side-by-side 実行によって、アプリケーションをバインドするコンポーネントのバージョンや、アプリケーションが使用するランタイムのバージョンを細かく制御できます。</span><span class="sxs-lookup"><span data-stu-id="7f3e7-106">Side-by-side execution gives you more control over what versions of a component an application binds to, and more control over what version of the runtime an application uses.</span></span>  
  
<span data-ttu-id="7f3e7-107">同じアセンブリの異なるバージョンの side-by-side ストレージにおける side-by-side 実行のサポートは、厳密な名前には不可欠の要素であり、ランタイムのインフラストラクチャに組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="7f3e7-107">Support for side-by-side storage and execution of different versions of the same assembly is an integral part of strong naming and is built into the infrastructure of the runtime.</span></span> <span data-ttu-id="7f3e7-108">厳密な名前を持つアセンブリのバージョン番号がその識別子の一部に含まれているため、ランタイムは同じアセンブリの複数のバージョンをグローバル アセンブリ キャッシュに格納し、実行時にこれらのアセンブリを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="7f3e7-108">Because the strong-named assembly's version number is part of its identity, the runtime can store multiple versions of the same assembly in the global assembly cache and load those assemblies at run time.</span></span>  
  
<span data-ttu-id="7f3e7-109">ランタイムは、side-by-side 実行できるアプリケーションの作成機能を提供しますが、side-by-side 実行は自動的にサポートされるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="7f3e7-109">Although the runtime provides you with the ability to create side-by-side applications, side-by-side execution is not automatic.</span></span> <span data-ttu-id="7f3e7-110">side-by-side 実行できるアプリケーションの作成に関する詳細については、「[side-by-side 実行用のコンポーネントを作成するためのガイドライン](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f3e7-110">For more information on creating applications for side-by-side execution, see [Guidelines for creating components for side-by-side execution](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f3e7-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="7f3e7-111">See also</span></span>

- [<span data-ttu-id="7f3e7-112">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="7f3e7-112">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="7f3e7-113">.NET のアセンブリ</span><span class="sxs-lookup"><span data-stu-id="7f3e7-113">Assemblies in .NET</span></span>](index.md)
