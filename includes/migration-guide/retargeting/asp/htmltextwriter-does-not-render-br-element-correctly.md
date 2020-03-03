---
ms.openlocfilehash: 0ab6be6f2c6d8ebbe67051e4e3f967a325e654c8
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804482"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a>HtmlTextWriter で `<br/>` 要素が正しく表示されない

|   |   |
|---|---|
|説明|.NET Framework 4.6 以降では、<xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> と <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> を <code>&lt;BR /&gt;</code> 要素を指定して呼び出すと、<code>&lt;BR /&gt;</code> を 1 つだけ (2 つではなく) 正しく挿入します。|
|提案される解決策|アプリが余分な <code>&lt;BR /&gt;</code> タグに依存している場合は、<xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> をもう一度呼び出す必要があります。 この動作の変更は、.NET Framework 4.6 以降を対象とするアプリにのみ影響するので、以前の動作を得るためには、以前のバージョンの .NET Framework を対象とするという方法もあります。|
|スコープ|エッジ|
|Version|4.6|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType></li></ul>|

