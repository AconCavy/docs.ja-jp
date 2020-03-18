---
ms.openlocfilehash: 8db115a46df3fcea103e8fa6896542d0116aa256
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804661"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a><span data-ttu-id="28bf1-101">VB.NET は、System.Windows Api の部分的な名前空間の修飾をサポートしなくなりました</span><span class="sxs-lookup"><span data-stu-id="28bf1-101">VB.NET no longer supports partial namespace qualification for System.Windows APIs</span></span>

|   |   |
|---|---|
|<span data-ttu-id="28bf1-102">説明</span><span class="sxs-lookup"><span data-stu-id="28bf1-102">Details</span></span>|<span data-ttu-id="28bf1-103">.NET Framework 4.5.2 以降では、VB.NET プロジェクトは、部分的に修飾された名前空間で System.Windows API を指定できません。</span><span class="sxs-lookup"><span data-stu-id="28bf1-103">Beginning in .NET Framework 4.5.2, VB.NET projects cannot specify System.Windows APIs with partially-qualified namespaces.</span></span> <span data-ttu-id="28bf1-104">たとえば、<code>Windows.Forms.DialogResult</code> の参照は失敗します。</span><span class="sxs-lookup"><span data-stu-id="28bf1-104">For example, referring to <code>Windows.Forms.DialogResult</code> will fail.</span></span> <span data-ttu-id="28bf1-105">代わりに、コードは、完全修飾名 (<xref:System.Windows.Forms.DialogResult>) を参照するか、特定の名前空間をインポートして、<xref:System.Windows.Forms.DialogResult?displayProperty=name> を参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="28bf1-105">Instead, code must refer to the fully qualified name (<xref:System.Windows.Forms.DialogResult>) or import the specific namespace and refer simply to <xref:System.Windows.Forms.DialogResult?displayProperty=name>.</span></span>|
|<span data-ttu-id="28bf1-106">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="28bf1-106">Suggestion</span></span>|<span data-ttu-id="28bf1-107"><code>System.Windows</code> API を単純な名前で参照するか (および関連する名前空間をインポートする)、完全修飾名で参照するように、コードを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="28bf1-107">Code should be updated to refer to <code>System.Windows</code> APIs either with simple names (and importing the relevant namespace) or with fully qualified names.</span></span>|
|<span data-ttu-id="28bf1-108">スコープ</span><span class="sxs-lookup"><span data-stu-id="28bf1-108">Scope</span></span>|<span data-ttu-id="28bf1-109">Minor</span><span class="sxs-lookup"><span data-stu-id="28bf1-109">Minor</span></span>|
|<span data-ttu-id="28bf1-110">バージョン</span><span class="sxs-lookup"><span data-stu-id="28bf1-110">Version</span></span>|<span data-ttu-id="28bf1-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="28bf1-111">4.5.2</span></span>|
|<span data-ttu-id="28bf1-112">[種類]</span><span class="sxs-lookup"><span data-stu-id="28bf1-112">Type</span></span>|<span data-ttu-id="28bf1-113">再ターゲット中</span><span class="sxs-lookup"><span data-stu-id="28bf1-113">Retargeting</span></span>|
