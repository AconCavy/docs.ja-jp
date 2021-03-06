---
ms.openlocfilehash: b648aee35ff44730f545f0fa06f4e0a86615dece
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606340"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a>HttpUtility.JavaScriptStringEncode でアンパサンドがエスケープされる

#### <a name="details"></a>説明

.NET Framework 4.5 以降では、<xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> でアンパサンド (&amp;) 文字がエスケープされます。

#### <a name="suggestion"></a>提案される解決策

アプリがこのメソッドの以前の動作に依存している場合、構成ファイルの [ASP.NET appSettings 要素](/previous-versions/aspnet/hh975440(v=vs.120)) に aspnet:JavaScriptDoNotEncodeAmpersand 設定を追加できます。

| 名前    | [値]       |
|:--------|:------------|
| スコープ   |マイナー|
|バージョン|4.5|
|種類|ランタイム|

#### <a name="affected-apis"></a>影響を受ける API

- <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType>
- <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Web.HttpUtility.JavaScriptStringEncode(System.String)`
- `M:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)`

-->
