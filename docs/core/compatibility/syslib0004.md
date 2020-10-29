---
title: SYSLIB0004 警告
description: コンパイル時の警告 SYSLIB0004 が生成される旧型式について説明します。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: ba7cd8a890a89000b241d286c9d8069ba1398849
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333131"
---
# <a name="syslib0004-the-constrained-execution-region-cer-feature-is-not-supported"></a>SYSLIB0004: 制約された実行領域 (CER) 機能はサポートされていません

[制約された実行領域 (CER)](../../framework/performance/constrained-execution-regions.md) 機能は、.NET Framework でのみサポートされています。 そのため、さまざまな CER 関連 API は、.NET 5.0 以降、古いものとしてマークされています。 これらの API を使用すると、コンパイル時に警告 `SYSLIB0004` が生成されます。

次の CER 関連の API は旧型式です。

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup(System.Runtime.CompilerServices.RuntimeHelpers.TryCode,System.Runtime.CompilerServices.RuntimeHelpers.CleanupCode,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegionsNoOP?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareContractedDelegate(System.Delegate)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ProbeForSufficientStack?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Cer?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Consistency?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute?displayProperty=nameWithType>

## <a name="see-also"></a>関連項目

- [制約された実行領域](../../framework/performance/constrained-execution-regions.md)
