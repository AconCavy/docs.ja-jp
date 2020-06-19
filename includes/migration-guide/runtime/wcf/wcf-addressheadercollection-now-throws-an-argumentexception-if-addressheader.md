---
ms.openlocfilehash: fa2a856911c7dcf81a39b7682a62a86c35328037
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275061"
---
### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a><span data-ttu-id="94437-101">addressHeader 要素が null の場合、WCF AddressHeaderCollection で ArgumentException がスローされるようになった</span><span class="sxs-lookup"><span data-stu-id="94437-101">WCF AddressHeaderCollection now throws an ArgumentException if an addressHeader element is null</span></span>

|   |   |
|---|---|
|<span data-ttu-id="94437-102">説明</span><span class="sxs-lookup"><span data-stu-id="94437-102">Details</span></span>|<span data-ttu-id="94437-103">.NET Framework 4.7.1 以降では、要素のいずれかが <code>null</code> の場合、<xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> コンストラクターで <xref:System.ArgumentException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="94437-103">Starting with the .NET Framework 4.7.1, the <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> constructor throws an <xref:System.ArgumentException> if one of the elements is <code>null</code>.</span></span> <span data-ttu-id="94437-104">.NET Framework 4.7 以前のバージョンでは、例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="94437-104">In the .NET Framework 4.7 and earlier versions, no exception is thrown.</span></span>|
|<span data-ttu-id="94437-105">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="94437-105">Suggestion</span></span>|<span data-ttu-id="94437-106">.NET Framework 4.7.1 以降のバージョンでこの変更に関する互換性の問題が発生した場合は、次の行を app.config ファイルの <code>&lt;runtime&gt;</code> セクションに追加することで、無効にできます。</span><span class="sxs-lookup"><span data-stu-id="94437-106">If you encounter compatibility issues with this change on the .NET Framework 4.7.1 or a later version, you can opt-out of it by adding the following line to the <code>&lt;runtime&gt;</code> section of the app.config file::</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="94437-107">スコープ</span><span class="sxs-lookup"><span data-stu-id="94437-107">Scope</span></span>|<span data-ttu-id="94437-108">マイナー</span><span class="sxs-lookup"><span data-stu-id="94437-108">Minor</span></span>|
|<span data-ttu-id="94437-109">バージョン</span><span class="sxs-lookup"><span data-stu-id="94437-109">Version</span></span>|<span data-ttu-id="94437-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="94437-110">4.7.1</span></span>|
|<span data-ttu-id="94437-111">種類</span><span class="sxs-lookup"><span data-stu-id="94437-111">Type</span></span>|<span data-ttu-id="94437-112">ランタイム</span><span class="sxs-lookup"><span data-stu-id="94437-112">Runtime</span></span>|
|<span data-ttu-id="94437-113">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="94437-113">Affected APIs</span></span>|<ul><li><xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})></li></ul>|
