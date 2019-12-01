---
ms.openlocfilehash: 86cdb845c436f424bbcc70e0736568031143b204
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567463"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="9856c-101">Microsoft.VisualBasic.Constants.vbNewLine は古い</span><span class="sxs-lookup"><span data-stu-id="9856c-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="9856c-102"><xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> 定数は、.NET Core 3.0 Preview 8 以降では[廃止](xref:System.ObsoleteAttribute)としてマークされています。</span><span class="sxs-lookup"><span data-stu-id="9856c-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked [Obsolete](xref:System.ObsoleteAttribute) starting with .NET Core 3.0 Preview 8.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9856c-103">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="9856c-103">Version introduced</span></span>

<span data-ttu-id="9856c-104">3.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="9856c-104">3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="9856c-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="9856c-105">Change description</span></span>

<span data-ttu-id="9856c-106">.NET Core 3.0 Preview 8 以降では、[廃止](xref:System.ObsoleteAttribute)属性が <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> 定数に適用されています。</span><span class="sxs-lookup"><span data-stu-id="9856c-106">Starting with .NET Core 3.0 Preview 8, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant.</span></span> <span data-ttu-id="9856c-107">その定数を使用すると、コンパイラの警告が発生します。</span><span class="sxs-lookup"><span data-stu-id="9856c-107">Use of the constant produces a compiler warning.</span></span> <span data-ttu-id="9856c-108">.NET Core と .NET Framework の両方の以前のリリースでは、廃止としてマークされていませんでした。</span><span class="sxs-lookup"><span data-stu-id="9856c-108">In previous releases of both .NET Core and .NET Framework, it was not marked as obsolete.</span></span>

<span data-ttu-id="9856c-109">この変更は、Visual Basic をマルチプラットフォーム開発用の言語としてサポートするために行われました。</span><span class="sxs-lookup"><span data-stu-id="9856c-109">This change was made to support Visual Basic as a language for multi-platform development.</span></span> <span data-ttu-id="9856c-110">`vbNewLine` 定数は、Windows での改行文字シーケンスである `\r\n` と同等です。</span><span class="sxs-lookup"><span data-stu-id="9856c-110">The `vbNewLine` constant is equivalent to `\r\n`, the newline character sequence on Windows.</span></span> <span data-ttu-id="9856c-111">Unix ベースのシステムでは、改行文字は `\n` です。</span><span class="sxs-lookup"><span data-stu-id="9856c-111">On Unix-based systems, the newline character is `\n`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9856c-112">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="9856c-112">Recommended action</span></span>

<span data-ttu-id="9856c-113">`vbNewLine` に対する[廃止](xref:System.ObsoleteAttribute)属性メッセージには、次の推奨事項が含まれています。</span><span class="sxs-lookup"><span data-stu-id="9856c-113">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for `vbNewLine` includes the following recommendation:</span></span>

> <span data-ttu-id="9856c-114">キャリッジ リターンとライン フィードの場合は、[vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf) を使用します。</span><span class="sxs-lookup"><span data-stu-id="9856c-114">For a carriage return and line feed, use [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf).</span></span> <span data-ttu-id="9856c-115">現在のプラットフォームの改行の場合は、<xref:System.Environment.NewLine?displayProperty=nameWithType> を使用します。</span><span class="sxs-lookup"><span data-stu-id="9856c-115">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="9856c-116">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="9856c-116">Category</span></span>

<span data-ttu-id="9856c-117">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9856c-117">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9856c-118">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="9856c-118">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
