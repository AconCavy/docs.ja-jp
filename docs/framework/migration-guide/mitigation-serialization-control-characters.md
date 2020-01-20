---
title: DataContractJsonSerializer での制御文字のシリアル化
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: 209f7827e61ef72de1d64fad46dc9f241fa6edef
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346569"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="0653f-102">軽減策:DataContractJsonSerializer での制御文字のシリアル化</span><span class="sxs-lookup"><span data-stu-id="0653f-102">Mitigation: Serialization of control characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="0653f-103">.NET Framework 4.7 以降では、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> での制御文字のシリアル化の方法が、ECMAScript V6 および V8 に準拠するように変更されました。</span><span class="sxs-lookup"><span data-stu-id="0653f-103">Starting with the .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span> 
 
## <a name="impact"></a><span data-ttu-id="0653f-104">影響</span><span class="sxs-lookup"><span data-stu-id="0653f-104">Impact</span></span>

<span data-ttu-id="0653f-105">.NET framework 4.6.2 以前のバージョンでは、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> で、ECMAScript V6 および V8 標準と互換性がある方法で `\b`、`\f`、`\t` などの一部の特殊制御文字がシリアル化されませんでした。</span><span class="sxs-lookup"><span data-stu-id="0653f-105">In the .NET framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="0653f-106">.NET Framework 4.7 以降のバージョンの .NET Framework を対象とするアプリの場合、これらの制御文字のシリアル化は ECMAScript V6 および V8 と互換性があります。</span><span class="sxs-lookup"><span data-stu-id="0653f-106">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="0653f-107">影響を受ける API は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0653f-107">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 

## <a name="mitigation"></a><span data-ttu-id="0653f-108">軽減策</span><span class="sxs-lookup"><span data-stu-id="0653f-108">Mitigation</span></span>

<span data-ttu-id="0653f-109">.NET Framework 4.7 以降のバージョンの .NET Framework を対象とするアプリの場合、この動作は既定で有効になります。</span><span class="sxs-lookup"><span data-stu-id="0653f-109">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="0653f-110">この動作が望ましくない場合は、app.config または web.config ファイルの `<runtime>` セクションに次の行を追加して、この機能を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="0653f-110">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a><span data-ttu-id="0653f-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="0653f-111">See also</span></span>

- [<span data-ttu-id="0653f-112">アプリケーションの互換性</span><span class="sxs-lookup"><span data-stu-id="0653f-112">Application compatibility</span></span>](application-compatibility.md)
