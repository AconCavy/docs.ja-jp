---
title: SYSLIB0005 警告
description: コンパイル時の警告 SYSLIB0005 が生成される旧型式について説明します。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 1263a4d327c735268f77ed56bdcea6a4cbed4bfa
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596368"
---
# <a name="syslib0005-the-global-assembly-cache-gac-is-not-supported"></a><span data-ttu-id="2eda5-103">SYSLIB0005: グローバル アセンブリ キャッシュ (GAC) はサポートされていません</span><span class="sxs-lookup"><span data-stu-id="2eda5-103">SYSLIB0005: The global assembly cache (GAC) is not supported</span></span>

<span data-ttu-id="2eda5-104">.NET Core および .NET 5.0 以降のバージョンでは、.NET Framework に存在していたグローバル アセンブリ キャッシュ (GAC) の概念がなくなりました。</span><span class="sxs-lookup"><span data-stu-id="2eda5-104">.NET Core and .NET 5.0 and later versions eliminate the concept of the global assembly cache (GAC) that was present in .NET Framework.</span></span> <span data-ttu-id="2eda5-105">開発者がこれらの API を使用しないようにするために、.NET 5.0 以降、一部の GAC 関連の API は古いものとしてマークされています。</span><span class="sxs-lookup"><span data-stu-id="2eda5-105">To help steer developers away from these APIs, some GAC-related APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="2eda5-106">これらの API を使用すると、コンパイル時に警告 `SYSLIB0005` が生成されます。</span><span class="sxs-lookup"><span data-stu-id="2eda5-106">Using these APIs generates warning `SYSLIB0005` at compile time.</span></span>

<span data-ttu-id="2eda5-107">次の GAC 関連の API は古いものとしてマークされています。</span><span class="sxs-lookup"><span data-stu-id="2eda5-107">The following GAC-related APIs are marked obsolete:</span></span>

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType>

  <span data-ttu-id="2eda5-108">ライブラリとアプリで実行時の動作を決定するために <xref:System.Reflection.Assembly.GlobalAssemblyCache> API を使用することはできません。これは、.NET Core および .NET 5 以降では常に `false` が返されるためです。</span><span class="sxs-lookup"><span data-stu-id="2eda5-108">Libraries and apps should not use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> API to make determinations about run-time behavior, as it always returns `false` in .NET Core and .NET 5+.</span></span>

## <a name="workarounds"></a><span data-ttu-id="2eda5-109">回避策</span><span class="sxs-lookup"><span data-stu-id="2eda5-109">Workarounds</span></span>

<span data-ttu-id="2eda5-110">アプリケーションによって <xref:System.Reflection.Assembly.GlobalAssemblyCache> プロパティのクエリが実行される場合は、呼び出しを削除することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="2eda5-110">If your application queries the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property, consider removing the call.</span></span> <span data-ttu-id="2eda5-111"><xref:System.Reflection.Assembly.GlobalAssemblyCache> 値を使用して、実行時に "GAC のアセンブリ" フローと "GAC に存在しないアセンブリ" フローのどちらかを選択する場合は、フローが .NET 5 以降のアプリケーションで引き続き意味を持つかどうかを再検討してください。</span><span class="sxs-lookup"><span data-stu-id="2eda5-111">If you use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> value to choose between an "assembly in the GAC"-flow vs. an "assembly not in the GAC"-flow at run time, reconsider whether the flow still makes sense for a .NET 5+ application.</span></span>

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="2eda5-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="2eda5-112">See also</span></span>

- [<span data-ttu-id="2eda5-113">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="2eda5-113">Global assembly cache</span></span>](../../../framework/app-domains/gac.md)