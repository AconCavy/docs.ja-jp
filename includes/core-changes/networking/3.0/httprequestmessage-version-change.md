---
ms.openlocfilehash: 5ad9c494fd02059e05cc744aad3b06cfc9399995
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451891"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a><span data-ttu-id="168cd-101">HttpRequestMessage.Version の既定値が 1.1 に変更された</span><span class="sxs-lookup"><span data-stu-id="168cd-101">Default value of HttpRequestMessage.Version changed to 1.1</span></span>

<span data-ttu-id="168cd-102"><xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> プロパティの既定値が 2.0 から 1.1 に変更されました。</span><span class="sxs-lookup"><span data-stu-id="168cd-102">The default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property has changed from 2.0 to 1.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="168cd-103">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="168cd-103">Version introduced</span></span>

<span data-ttu-id="168cd-104">3.0</span><span class="sxs-lookup"><span data-stu-id="168cd-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="168cd-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="168cd-105">Change description</span></span>

<span data-ttu-id="168cd-106">.NET Core 1.0 から 2.0 では、<xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> プロパティの既定値は 1.1 です。</span><span class="sxs-lookup"><span data-stu-id="168cd-106">In .NET Core 1.0 through 2.0, the default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is 1.1.</span></span> <span data-ttu-id="168cd-107">.NET Core 2.1 以降では、2.1 に変更されました。</span><span class="sxs-lookup"><span data-stu-id="168cd-107">Starting with .NET Core 2.1, it was changed to 2.1.</span></span>

<span data-ttu-id="168cd-108">.NET Core 3.0 以降では、<xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> プロパティによって返される既定のバージョン番号は再び 1.1 になりました。</span><span class="sxs-lookup"><span data-stu-id="168cd-108">Starting with .NET Core 3.0, the default version number returned by the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is once again 1.1.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="168cd-109">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="168cd-109">Recommended action</span></span>

<span data-ttu-id="168cd-110">既定値 2.0 を返す <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> プロパティに依存している場合は、コードを更新します。</span><span class="sxs-lookup"><span data-stu-id="168cd-110">Update your code if it depends on the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property returning a default value of 2.0.</span></span>

#### <a name="category"></a><span data-ttu-id="168cd-111">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="168cd-111">Category</span></span>

<span data-ttu-id="168cd-112">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="168cd-112">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="168cd-113">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="168cd-113">Affected APIs</span></span>

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-->
