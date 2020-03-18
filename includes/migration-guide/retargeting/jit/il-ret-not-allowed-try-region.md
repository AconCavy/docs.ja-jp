---
ms.openlocfilehash: 1687b1b9a1a6861f9569a0e29426de7f32ffc32b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804475"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a><span data-ttu-id="2cd8d-101">try 領域で IL ret が許可されない</span><span class="sxs-lookup"><span data-stu-id="2cd8d-101">IL ret not allowed in a try region</span></span>

|   |   |
|---|---|
|<span data-ttu-id="2cd8d-102">説明</span><span class="sxs-lookup"><span data-stu-id="2cd8d-102">Details</span></span>|<span data-ttu-id="2cd8d-103">JIT64 Just-In-Time コンパイラとは異なり、(.NET Framework 4.6 で使用される) RyuJIT では、try 領域で IL ret 命令が許可されません。</span><span class="sxs-lookup"><span data-stu-id="2cd8d-103">Unlike the JIT64 just-in-time compiler, RyuJIT (used in .NET Framework 4.6) does not allow an IL ret instruction in a try region.</span></span> <span data-ttu-id="2cd8d-104">ECMA-335 仕様により try 領域から戻ることは許可されておらず、そうした IL を生成する既知のマネージド コンパイラはありません。</span><span class="sxs-lookup"><span data-stu-id="2cd8d-104">Returning from a try region is disallowed by the ECMA-335 specification, and no known managed compiler generates such IL.</span></span> <span data-ttu-id="2cd8d-105">ただし、JIT64 コンパイラは、リフレクション出力を使用して生成される場合にはこうした IL を実行します。</span><span class="sxs-lookup"><span data-stu-id="2cd8d-105">However, the JIT64 compiler will execute such IL if it is generated using reflection emit.</span></span>|
|<span data-ttu-id="2cd8d-106">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="2cd8d-106">Suggestion</span></span>|<span data-ttu-id="2cd8d-107">try 領域に ret オペコードを含む IL をアプリが生成する場合、そのアプリでは .NET Framework 4.5 を対象にして以前の JIT を使用し、この中断を回避できます。</span><span class="sxs-lookup"><span data-stu-id="2cd8d-107">If an app is generating IL that includes a ret opcode in a try region, the app may target .NET Framework 4.5 to use the old JIT and avoid this break.</span></span> <span data-ttu-id="2cd8d-108">あるいは、try 領域の後に戻るように生成後の IL を更新できます。</span><span class="sxs-lookup"><span data-stu-id="2cd8d-108">Alternatively, the generated IL may be updated to return after the try region.</span></span>|
|<span data-ttu-id="2cd8d-109">スコープ</span><span class="sxs-lookup"><span data-stu-id="2cd8d-109">Scope</span></span>|<span data-ttu-id="2cd8d-110">エッジ</span><span class="sxs-lookup"><span data-stu-id="2cd8d-110">Edge</span></span>|
|<span data-ttu-id="2cd8d-111">バージョン</span><span class="sxs-lookup"><span data-stu-id="2cd8d-111">Version</span></span>|<span data-ttu-id="2cd8d-112">4.6</span><span class="sxs-lookup"><span data-stu-id="2cd8d-112">4.6</span></span>|
|<span data-ttu-id="2cd8d-113">[種類]</span><span class="sxs-lookup"><span data-stu-id="2cd8d-113">Type</span></span>|<span data-ttu-id="2cd8d-114">再ターゲット中</span><span class="sxs-lookup"><span data-stu-id="2cd8d-114">Retargeting</span></span>|
