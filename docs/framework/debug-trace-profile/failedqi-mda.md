---
title: failedQI MDA
ms.date: 03/30/2017
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fec1bfb402f3b394ceb36590c3a880f82c5cb101
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052793"
---
# <a name="failedqi-mda"></a>failedQI MDA
`failedQI` マネージド デバッグ アシスタント (MDA: Managed Debugging Asssitant) は、ランタイムがランタイム呼び出し可能ラッパー (RCW: Runtime Callable Wrapper) の代わりに COM インターフェイス ポインター上の `QueryInterface` を呼び出し、その `QueryInterface` 呼び出しに失敗するとアクティブ化されます。  
  
## <a name="symptoms"></a>症状  
 RCW でのキャストに失敗します。または、RCW からの COM 呼び出しが予期せず失敗します。  
  
## <a name="cause"></a>原因  
  
- 正しくないコンテキストから呼び出しが実行されました。  
  
- 呼び出しが正しくないコンテキストで試行されたため、登録されたプロキシが `QueryInterface` 呼び出しに失敗しています。  
  
- OLE 所有のプロキシがエラー HRESULT を返しました。  
  
## <a name="resolution"></a>解決策  
 COM 規則についての MSDN ドキュメントを参照してください。  
  
## <a name="effect-on-the-runtime"></a>ランタイムへの影響  
 `QueryInterface` 呼び出しに失敗すると、コンテキストが切り替えられ、エラー時に正しくないコンテキストであったことを確認するために、`QueryInterface` 呼び出しが再試行されます。  
  
## <a name="output"></a>出力  
 インターフェイスのマネージド名、インターフェイスの GUID、およびエラー HRESULT です。  
  
## <a name="configuration"></a>構成  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [マネージド デバッグ アシスタントによるエラーの診断](diagnosing-errors-with-managed-debugging-assistants.md)
- [相互運用マーシャリング](../interop/interop-marshaling.md)
