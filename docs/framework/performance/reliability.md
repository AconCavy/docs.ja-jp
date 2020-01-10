---
title: 信頼性
ms.date: 03/30/2017
helpviewer_keywords:
- SQL Server [.NET Framework]
- managed code, reliability
- reliability [.NET Framework]
- writing reliable code
- code, reliability
ms.assetid: 294aa306-0afe-4cbe-b397-86ba9f1860f8
ms.openlocfilehash: 2d6601c4cbad32f768ff16301307083f35d986a0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715963"
---
# <a name="reliability"></a><span data-ttu-id="997ab-102">信頼性</span><span class="sxs-lookup"><span data-stu-id="997ab-102">Reliability</span></span>
<span data-ttu-id="997ab-103">SQL Server などのサーバー環境で実行するコードは、非同期例外から保護することが重要です。</span><span class="sxs-lookup"><span data-stu-id="997ab-103">It is important that code executing in server environments such as SQL Server protect against asynchronous exceptions.</span></span> <span data-ttu-id="997ab-104">ここで説明するように、信頼性とは、SQL Server に限ったことではなく、.NET Framework バージョン 2.0 の環境で実行するホスト用に信頼性の高いコードを書くことです。</span><span class="sxs-lookup"><span data-stu-id="997ab-104">Reliability, as discussed here, is not specific to SQL Server but to writing reliable code for any host executing in a .NET Framework version 2.0 environment.</span></span> <span data-ttu-id="997ab-105">ただし、SQL Server はバージョン 2.0 の新しい信頼性機能を広範に使う初めてのサービスなので、例として使います。</span><span class="sxs-lookup"><span data-stu-id="997ab-105">However, SQL Server is the first service making extensive use of the new reliability features of version 2.0, so it is used as an example.</span></span>  
  
 <span data-ttu-id="997ab-106">SQL Server で実行されるコードは、他のサーバー環境より厳格な信頼性ガイドラインに対応する必要があります。</span><span class="sxs-lookup"><span data-stu-id="997ab-106">Code running in SQL Server must deal with more stringent reliability guidelines than other server environments.</span></span> <span data-ttu-id="997ab-107">これは、リソース消費での SQL Server の安定した動作のためです。</span><span class="sxs-lookup"><span data-stu-id="997ab-107">This is due to SQL Server’s steady operation at the edge of resource consumption.</span></span>  <span data-ttu-id="997ab-108"><xref:System.OutOfMemoryException> および <xref:System.Threading.ThreadAbortException> 例外は、SQL Server 環境では珍しくありません。</span><span class="sxs-lookup"><span data-stu-id="997ab-108"><xref:System.OutOfMemoryException> and <xref:System.Threading.ThreadAbortException> exceptions are not uncommon in the SQL Server environment.</span></span> <span data-ttu-id="997ab-109">一般に、これらのガイドラインでの主眼は、信頼性より、<xref:System.AppDomain> レベルのリサイクルが発生したときに完全に信頼されたマネージド コードが正常に失敗できるようにすることにあります。リサイクルは、サーバーが整合性と可用性を維持する主要な手段です。</span><span class="sxs-lookup"><span data-stu-id="997ab-109">These guidelines in general are focused less on reliability and more on allowing fully trusted managed code to fail gracefully in the face of <xref:System.AppDomain>-level recycling, which is the primary way the server maintains consistency and availability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="997ab-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="997ab-110">In This Section</span></span>  
 [<span data-ttu-id="997ab-111">SQL Server プログラミングとホスト保護属性</span><span class="sxs-lookup"><span data-stu-id="997ab-111">SQL Server Programming and Host Protection Attributes</span></span>](sql-server-programming-and-host-protection-attributes.md)  
 <span data-ttu-id="997ab-112">SQL Server が <xref:System.Security.Permissions.HostProtectionAttribute> 属性を使ってマネージド コードの実行を制限する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="997ab-112">Describes how the <xref:System.Security.Permissions.HostProtectionAttribute> attribute is used by SQL Server to restrict the execution of managed code.</span></span>  
  
 [<span data-ttu-id="997ab-113">信頼性に関するベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="997ab-113">Reliability Best Practices</span></span>](reliability-best-practices.md)  
 <span data-ttu-id="997ab-114">信頼性の要件を満たすコードを記述するためのガイドラインを提供します。</span><span class="sxs-lookup"><span data-stu-id="997ab-114">Provides guidelines for writing code that meets reliability requirements.</span></span>  
  
 [<span data-ttu-id="997ab-115">制約された実行領域</span><span class="sxs-lookup"><span data-stu-id="997ab-115">Constrained Execution Regions</span></span>](constrained-execution-regions.md)  
 <span data-ttu-id="997ab-116">制約された実行領域 (CER) の機能と動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="997ab-116">Describes the function and behavior of constrained execution regions (CERs).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="997ab-117">参照先</span><span class="sxs-lookup"><span data-stu-id="997ab-117">Reference</span></span>  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
