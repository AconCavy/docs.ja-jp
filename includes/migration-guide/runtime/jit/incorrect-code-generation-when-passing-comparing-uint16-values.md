---
ms.openlocfilehash: ad624a665dbe8e989ea05acc20213809e515e6ac
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804417"
---
### <a name="incorrect-code-generation-when-passing-and-comparing-uint16-values"></a>UInt16 値を渡して比較する場合にコード生成が正しく行われません

|   |   |
|---|---|
|説明|.NET Framework 4.7 で変更が導入されたため、.NET Framework 4.7 で実行されているアプリケーションの JIT コンパイラによって生成されたコードが 2 つの <code>T:System.UInt16</code> 値を正しく比較しない場合があります。 詳細については、GitHub.com の「[Issue #11508:Silent bad codegen when passing and comparing ushort args](https://github.com/dotnet/coreclr/issues/11508)」 (問題 #11508: ushort の引数を渡して比較する場合のサイレントかつ不適切な codegen) を参照してください。|
|提案される解決策|.NET Framework 4.7 で 16 ビットの符号なし値を比較したときに問題が検出された場合は、.NET Framework 4.7.1 にアップグレードしてください。|
|スコープ|エッジ|
|Version|4.7|
|型|ランタイム|
