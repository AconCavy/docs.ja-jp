---
title: 1 秒あたりの不明なトランザクション操作
ms.date: 03/30/2017
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
ms.openlocfilehash: 59186b1fc113bb87264a8b946cfee2719ff50b62
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550600"
---
# <a name="transacted-operations-in-doubt-per-second"></a><span data-ttu-id="d7e40-102">1 秒あたりの不明なトランザクション操作</span><span class="sxs-lookup"><span data-stu-id="d7e40-102">Transacted Operations In Doubt Per Second</span></span>
<span data-ttu-id="d7e40-103">カウンター名 : 1 秒あたりの不明なトランザクション操作。</span><span class="sxs-lookup"><span data-stu-id="d7e40-103">Counter Name: Transacted Operations In Doubt Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d7e40-104">説明</span><span class="sxs-lookup"><span data-stu-id="d7e40-104">Description</span></span>  
 <span data-ttu-id="d7e40-105">このサービスでの 1 秒あたりの結果が不明なランザクション操作の数です。</span><span class="sxs-lookup"><span data-stu-id="d7e40-105">Number of transactional operations with an in-doubt outcome in this service in a second.</span></span>  
  
 <span data-ttu-id="d7e40-106">このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。</span><span class="sxs-lookup"><span data-stu-id="d7e40-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="d7e40-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="d7e40-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
