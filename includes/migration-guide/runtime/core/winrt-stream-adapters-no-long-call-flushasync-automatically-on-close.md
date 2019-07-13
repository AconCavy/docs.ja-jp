---
ms.openlocfilehash: 60759e3d03137bb5983703cbf04719ba4946cb6e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804442"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a>終了時に WinRT ストリーム アダプターで FlushAsync が自動的に呼び出されなくなりました

|   |   |
|---|---|
|説明|Windows ストア アプリの Windows ランタイム ストリーム アダプターで、Dispose メソッドから FlushAsync メソッドが呼び出されなくなりました。|
|提案される解決策|この変更は透過的である必要があります。 開発者は次のようなコードを記述して以前の動作を復元できます。<pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>|
|スコープ|透明|
|Version|4.5.1|
|型|ランタイム|
