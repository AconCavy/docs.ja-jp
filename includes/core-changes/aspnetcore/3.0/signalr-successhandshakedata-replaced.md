---
ms.openlocfilehash: fa0f54404d1e14afa6ce48a425c984a48498a1ee
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394084"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a><span data-ttu-id="1520b-101">SignalR: HandshakeProtocol.SuccessHandshakeData が置き換えられました</span><span class="sxs-lookup"><span data-stu-id="1520b-101">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>

<span data-ttu-id="1520b-102">[HandshakeProtocol.SuccessHandshakeData](https://github.com/aspnet/AspNetCore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) フィールドが削除され、特定の `IHubProtocol` が指定された場合に適切なハンドシェイク応答を生成するヘルパー メソッドに置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="1520b-102">The [HandshakeProtocol.SuccessHandshakeData](https://github.com/aspnet/AspNetCore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) field was removed and replaced with a helper method that generates a successful handshake response given a specific `IHubProtocol`.</span></span> 

#### <a name="version-introduced"></a><span data-ttu-id="1520b-103">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="1520b-103">Version introduced</span></span>

<span data-ttu-id="1520b-104">3.0</span><span class="sxs-lookup"><span data-stu-id="1520b-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="1520b-105">以前の動作</span><span class="sxs-lookup"><span data-stu-id="1520b-105">Old behavior</span></span>

<span data-ttu-id="1520b-106">`HandshakeProtocol.SuccessHandshakeData` は、`public static ReadOnlyMemory<byte>` フィールドでした。</span><span class="sxs-lookup"><span data-stu-id="1520b-106">`HandshakeProtocol.SuccessHandshakeData` was a `public static ReadOnlyMemory<byte>` field.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="1520b-107">新しい動作</span><span class="sxs-lookup"><span data-stu-id="1520b-107">New behavior</span></span>

<span data-ttu-id="1520b-108">`HandshakeProtocol.SuccessHandshakeData` は、指定されたプロトコルに基づいて `ReadOnlyMemory<byte>` を返す `static` `GetSuccessfulHandshake(IHubProtocol protocol)` メソッドに置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="1520b-108">`HandshakeProtocol.SuccessHandshakeData` has been replaced by a `static` `GetSuccessfulHandshake(IHubProtocol protocol)` method that returns a `ReadOnlyMemory<byte>` based on the specified protocol.</span></span> 

#### <a name="reason-for-change"></a><span data-ttu-id="1520b-109">変更理由</span><span class="sxs-lookup"><span data-stu-id="1520b-109">Reason for change</span></span>

<span data-ttu-id="1520b-110">ハンドシェイク_応答_に、選択したプロトコルによって変化する非定数の追加フィールドが加えられました。</span><span class="sxs-lookup"><span data-stu-id="1520b-110">Additional fields were added to the handshake _response_ that are non-constant and change depending on the selected protocol.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1520b-111">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="1520b-111">Recommended action</span></span>

<span data-ttu-id="1520b-112">なし。</span><span class="sxs-lookup"><span data-stu-id="1520b-112">None.</span></span> <span data-ttu-id="1520b-113">この型は、ユーザー コードから使用するように設計されていません。</span><span class="sxs-lookup"><span data-stu-id="1520b-113">This type isn't designed for use from user code.</span></span> <span data-ttu-id="1520b-114">これは `public` であり、SignalR サーバーとクライアントの間で共有できます。</span><span class="sxs-lookup"><span data-stu-id="1520b-114">It's `public`, so it can be shared between the SignalR server and client.</span></span> <span data-ttu-id="1520b-115">また、.NET で記述されたユーザーの SignalR クライアントによって使用されることもあります。</span><span class="sxs-lookup"><span data-stu-id="1520b-115">It may also be used by customer SignalR clients written in .NET.</span></span> <span data-ttu-id="1520b-116">SignalR の**ユーザー**は、この変更による影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="1520b-116">**Users** of SignalR shouldn't be affected by this change.</span></span>

#### <a name="category"></a><span data-ttu-id="1520b-117">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="1520b-117">Category</span></span>

<span data-ttu-id="1520b-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1520b-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1520b-119">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="1520b-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->