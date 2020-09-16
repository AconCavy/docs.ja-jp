---
title: 1 秒あたりの失敗した呼び出し
ms.date: 03/30/2017
ms.assetid: 81c88073-8e32-4520-a71a-2c56b71ee515
ms.openlocfilehash: a50d1881040f248d7c58e82ce2e477b51591c2f3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553585"
---
# <a name="calls-faulted-per-second"></a><span data-ttu-id="34579-102">1 秒あたりの失敗した呼び出し</span><span class="sxs-lookup"><span data-stu-id="34579-102">Calls Faulted Per Second</span></span>
<span data-ttu-id="34579-103">カウンター名 : 1 秒あたりの失敗した呼び出し</span><span class="sxs-lookup"><span data-stu-id="34579-103">Counter Name: Calls Faulted Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="34579-104">説明</span><span class="sxs-lookup"><span data-stu-id="34579-104">Description</span></span>  
 <span data-ttu-id="34579-105">この操作への呼び出しに失敗した回数です (1 秒あたり)。</span><span class="sxs-lookup"><span data-stu-id="34579-105">Number of calls that returned faults to this operation in a second.</span></span>  
  
 <span data-ttu-id="34579-106">このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。</span><span class="sxs-lookup"><span data-stu-id="34579-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="34579-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="34579-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="34579-108">Windows Communication Foundation (WCF) アプリケーションでは、サービスメソッドは SOAP エラーメッセージを使用して処理エラー情報を通信します。</span><span class="sxs-lookup"><span data-stu-id="34579-108">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="34579-109">SOAP エラーは、サービス操作のメタデータに含まれるメッセージ型であり、堅牢かつインタラクティブに実行できるようにクライアントが使用するエラー コントラクトを作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="34579-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="34579-110">SOAP エラーは XML 形式でクライアントに渡されるので、相互運用性の面でも優れています。</span><span class="sxs-lookup"><span data-stu-id="34579-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34579-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="34579-111">See also</span></span>

- [<span data-ttu-id="34579-112">コントラクトおよびサービスのエラーの指定と処理</span><span class="sxs-lookup"><span data-stu-id="34579-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
