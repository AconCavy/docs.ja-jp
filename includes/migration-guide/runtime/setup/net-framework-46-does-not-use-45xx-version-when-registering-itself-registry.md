---
ms.openlocfilehash: ee5070a1a4c58d6c1282ba47c921436ca22722ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858435"
---
### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a><span data-ttu-id="dffd3-101">.NET Framework 4.6 は、自分自身をレジストリに登録するときに 4.5.x.x バージョンを使用しない</span><span class="sxs-lookup"><span data-stu-id="dffd3-101">The .NET Framework 4.6 does not use a 4.5.x.x version when registering itself in the registry</span></span>

|   |   |
|---|---|
|<span data-ttu-id="dffd3-102">説明</span><span class="sxs-lookup"><span data-stu-id="dffd3-102">Details</span></span>|<span data-ttu-id="dffd3-103">予想されるように、.NET Framework 4.6 に対してレジストリ (<code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) に設定されるバージョン キーは、"4.5" ではなく "4.6" で始まります。</span><span class="sxs-lookup"><span data-stu-id="dffd3-103">As one might expect, the version key set in the registry (at <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) for the .NET Framework 4.6 begins with '4.6', not '4.5'.</span></span> <span data-ttu-id="dffd3-104">これらのレジストリ キーに依存してコンピューターにインストールされている .NET Framework のバージョンを特定するアプリは、4.6 が可能な新しいバージョンであり、前の 4.5.x リリースと互換性があることを認識するように、更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dffd3-104">Apps that depend on these registry keys to know which .NET Framework versions are installed on a machine should be updated to understand that 4.6 is a new possible version, and one that is compatible with previous 4.5.x releases.</span></span>|
|<span data-ttu-id="dffd3-105">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="dffd3-105">Suggestion</span></span>|<span data-ttu-id="dffd3-106">4\.5 のレジストリ キーを検索することによって .NET Framework 4.5 のインストールを調べるアプリを、4.6 も受け付けるように更新します。</span><span class="sxs-lookup"><span data-stu-id="dffd3-106">Update apps probing for a .NET Framework 4.5 install by looking for 4.5 registry keys to also accept 4.6.</span></span>|
|<span data-ttu-id="dffd3-107">スコープ</span><span class="sxs-lookup"><span data-stu-id="dffd3-107">Scope</span></span>|<span data-ttu-id="dffd3-108">エッジ</span><span class="sxs-lookup"><span data-stu-id="dffd3-108">Edge</span></span>|
|<span data-ttu-id="dffd3-109">バージョン</span><span class="sxs-lookup"><span data-stu-id="dffd3-109">Version</span></span>|<span data-ttu-id="dffd3-110">4.6</span><span class="sxs-lookup"><span data-stu-id="dffd3-110">4.6</span></span>|
|<span data-ttu-id="dffd3-111">[種類]</span><span class="sxs-lookup"><span data-stu-id="dffd3-111">Type</span></span>|<span data-ttu-id="dffd3-112">ランタイム</span><span class="sxs-lookup"><span data-stu-id="dffd3-112">Runtime</span></span>|
