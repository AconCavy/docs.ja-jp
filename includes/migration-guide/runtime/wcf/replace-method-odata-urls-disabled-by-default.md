---
ms.openlocfilehash: 6dc3669433804a4524c18d5a932f9879343ab508
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804365"
---
### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a>OData URL の Replace メソッドが既定で無効になる

|   |   |
|---|---|
|説明|.NET Framework 4.5 以降では、OData URL の Replace メソッドは既定では無効です。 OData Replace が無効のとき (既定)、replace 関数を含むユーザー要求 (一般的ではない) は失敗します。|
|提案される解決策|Replace メソッドが必要な場合 (一般的ではない)、構成設定 (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=name>) によって再び有効にできます。 ただし、有効になった replace メソッドはセキュリティの脆弱性を開くことがあり、慎重にレビューしてから使用する必要があります。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Data.Services.DataService%601?displayProperty=nameWithType></li></ul>|
