---
ms.openlocfilehash: 0d6847b7a937094f36efae70ae450cc37824221d
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955559"
---
### <a name="assembly-related-api-behavior-changes-for-single-file-publishing-format"></a><span data-ttu-id="cc64d-101">単一ファイル発行形式のアセンブリ関連 API 動作の変更</span><span class="sxs-lookup"><span data-stu-id="cc64d-101">Assembly-related API behavior changes for single-file publishing format</span></span>

<span data-ttu-id="cc64d-102">アセンブリのファイルの場所に関連する複数の API は、単一ファイルの公開形式で呼び出されたときに動作が変更されます。</span><span class="sxs-lookup"><span data-stu-id="cc64d-102">Multiple APIs related to an assembly's file location have behavior changes when they're invoked in a single-file publishing format.</span></span>

#### <a name="change-description"></a><span data-ttu-id="cc64d-103">変更内容</span><span class="sxs-lookup"><span data-stu-id="cc64d-103">Change description</span></span>

<span data-ttu-id="cc64d-104">.NET 5.0 以降のバージョンの単一ファイル公開では、バンドルされたアセンブリは、ディスクに展開されるのではなく、メモリから読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="cc64d-104">In single-file publishing for .NET 5.0 and later versions, bundled assemblies are loaded from memory instead of extracted to disk.</span></span> <span data-ttu-id="cc64d-105">単一ファイルで公開されたアプリの場合、これは、特定の場所関連の API が .NET 5.0 以降で以前のバージョンの .NET とは異なる値を返すことを意味します。</span><span class="sxs-lookup"><span data-stu-id="cc64d-105">For single-file published apps, this means that certain location-related APIs return different values on .NET 5.0 and later than on previous versions of .NET.</span></span> <span data-ttu-id="cc64d-106">変更点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cc64d-106">The changes are as follows:</span></span>

| <span data-ttu-id="cc64d-107">API</span><span class="sxs-lookup"><span data-stu-id="cc64d-107">API</span></span> | <span data-ttu-id="cc64d-108">以前のバージョン</span><span class="sxs-lookup"><span data-stu-id="cc64d-108">Previous versions</span></span> | <span data-ttu-id="cc64d-109">.NET 5.0 以降</span><span class="sxs-lookup"><span data-stu-id="cc64d-109">.NET 5.0 and later</span></span> |
| - | - | - |
| <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> | <span data-ttu-id="cc64d-110">展開された DLL ファイル パスを返します</span><span class="sxs-lookup"><span data-stu-id="cc64d-110">Returns extracted DLL file path</span></span> | <span data-ttu-id="cc64d-111">バンドルされたアセンブリに対して空の文字列を返します</span><span class="sxs-lookup"><span data-stu-id="cc64d-111">Returns empty string for bundled assemblies</span></span> |
| <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> | <span data-ttu-id="cc64d-112">展開された DLL ファイル パスを返します</span><span class="sxs-lookup"><span data-stu-id="cc64d-112">Returns extracted DLL file path</span></span> | <span data-ttu-id="cc64d-113">バンドルされたアセンブリの例外をスローします</span><span class="sxs-lookup"><span data-stu-id="cc64d-113">Throws exception for bundled assemblies</span></span> |
| <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType> | <span data-ttu-id="cc64d-114">バンドルされたアセンブリの `null` を返します</span><span class="sxs-lookup"><span data-stu-id="cc64d-114">Returns `null` for bundled assemblies</span></span> | <span data-ttu-id="cc64d-115">バンドルされたアセンブリの例外をスローします</span><span class="sxs-lookup"><span data-stu-id="cc64d-115">Throws exception for bundled assemblies</span></span> |
| `Environment.GetCommandLineArgs()[0]` | <span data-ttu-id="cc64d-116">値はエントリ ポイント DLL の名前です</span><span class="sxs-lookup"><span data-stu-id="cc64d-116">Value is the name of the entry point DLL</span></span> | <span data-ttu-id="cc64d-117">値はホストの実行可能ファイルの名前です</span><span class="sxs-lookup"><span data-stu-id="cc64d-117">Value is the name of the host executable</span></span> |
| <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> | <span data-ttu-id="cc64d-118">値は一時的な展開ディレクトリです</span><span class="sxs-lookup"><span data-stu-id="cc64d-118">Value is the temporary extraction directory</span></span> | <span data-ttu-id="cc64d-119">値は、ホストの実行可能ファイルの格納ディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="cc64d-119">Value is the containing directory of the host executable</span></span> |

#### <a name="version-introduced"></a><span data-ttu-id="cc64d-120">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="cc64d-120">Version introduced</span></span>

<span data-ttu-id="cc64d-121">5.0</span><span class="sxs-lookup"><span data-stu-id="cc64d-121">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cc64d-122">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="cc64d-122">Recommended action</span></span>

<span data-ttu-id="cc64d-123">1 つのファイルとして公開する場合は、アセンブリのファイルの場所に依存しないようにします。</span><span class="sxs-lookup"><span data-stu-id="cc64d-123">Avoid dependencies on the file location of assemblies when publishing as a single file.</span></span>

#### <a name="category"></a><span data-ttu-id="cc64d-124">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="cc64d-124">Category</span></span>

- <span data-ttu-id="cc64d-125">Core .NET ライブラリ</span><span class="sxs-lookup"><span data-stu-id="cc64d-125">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cc64d-126">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="cc64d-126">Affected APIs</span></span>

- <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType>
- <xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType>
- <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Reflection.Assembly.Location`
- `P:System.Reflection.Assembly.CodeBase`
- `M:System.Reflection.Assembly.GetFile(System.String)`
- `M:System.Environment.GetCommandLineArgs`
- `P:System.AppContext.BaseDirectory`

-->
