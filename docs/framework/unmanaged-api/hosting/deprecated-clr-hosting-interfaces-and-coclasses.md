---
title: 非推奨の CLR のホスト インターフェイスおよびコクラス
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 1
- .NET Framework 1.1, hosting interfaces
- hosting interfaces [.NET Framework], version 1
- .NET Framework 1.0, hosting interfaces
ms.assetid: 7b3d2755-cbab-4160-bc69-eb85791e38c7
ms.openlocfilehash: 814f148b39045ad5454a23dfce8e7f9441f69041
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616412"
---
# <a name="deprecated-clr-hosting-interfaces-and-coclasses"></a><span data-ttu-id="af63d-102">非推奨の CLR のホスト インターフェイスおよびコクラス</span><span class="sxs-lookup"><span data-stu-id="af63d-102">Deprecated CLR Hosting Interfaces and Coclasses</span></span>
<span data-ttu-id="af63d-103">ここでは、アンマネージホストが .NET Framework バージョン1.0 および1.1 の共通言語ランタイム (CLR) をアプリケーションに統合するために使用できるインターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="af63d-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework versions 1.0 and 1.1 into their applications.</span></span> <span data-ttu-id="af63d-104">これらのインターフェイスは、ホストがランタイムを構成してプロセスに読み込むためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="af63d-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="af63d-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="af63d-105">In This Section</span></span>  
 <span data-ttu-id="af63d-106">IAppDomainSetup</span><span class="sxs-lookup"><span data-stu-id="af63d-106">IAppDomainSetup</span></span>  
 <span data-ttu-id="af63d-107">を構成するためのホストのメソッドを提供 <xref:System.AppDomain> します。</span><span class="sxs-lookup"><span data-stu-id="af63d-107">Provides methods for the host to configure an <xref:System.AppDomain>.</span></span>  
  
 [<span data-ttu-id="af63d-108">ICeeFileGen クラス</span><span class="sxs-lookup"><span data-stu-id="af63d-108">ICeeFileGen Class</span></span>](iceefilegen-class.md)  
 <span data-ttu-id="af63d-109">れネイティブのポータブル実行可能 (PE) ファイルを作成するための機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="af63d-109">(Deprecated) Provides functionality for creating a native portable executable (PE) file.</span></span>  
  
 [<span data-ttu-id="af63d-110">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="af63d-110">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)  
 <span data-ttu-id="af63d-111">ホストが CLR 設定を構成するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="af63d-111">Provides methods for the host to configure CLR settings.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="af63d-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="af63d-112">Related Sections</span></span>  
 [<span data-ttu-id="af63d-113">CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="af63d-113">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)  
 <span data-ttu-id="af63d-114">.NET Framework バージョン2.0 以降のバージョンで提供されるホストインターフェイスについて説明するトピックが含まれています。</span><span class="sxs-lookup"><span data-stu-id="af63d-114">Contains topics that describe the hosting interfaces provided with the .NET Framework version 2.0 and later versions.</span></span>
