---
title: Windows システムのファイル パス形式
ms.date: 06/06/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O, long paths
- long paths
- path formats, Windows
ms.openlocfilehash: 258cf59fb8383fe131f4a0e78dac6189e1d9c91e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337674"
---
# <a name="file-path-formats-on-windows-systems"></a><span data-ttu-id="b7377-102">Windows システムのファイル パス形式</span><span class="sxs-lookup"><span data-stu-id="b7377-102">File path formats on Windows systems</span></span>

<span data-ttu-id="b7377-103"><xref:System.IO> 名前空間の型の多くのメンバーには `path` パラメーターが含まれています。このパラメーターによって、ファイル システム リソースの絶対パスまたは相対パスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b7377-103">Members of many of the types in the <xref:System.IO> namespace include a `path` parameter that lets you specify an absolute or relative path to a file system resource.</span></span> <span data-ttu-id="b7377-104">このパスはその後、[Windows ファイル システム API](/windows/desktop/fileio/file-systems) に渡されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-104">This path is then passed to [Windows file system APIs](/windows/desktop/fileio/file-systems).</span></span> <span data-ttu-id="b7377-105">このトピックでは、Windows システムで利用できるファイル パスの形式について説明します。</span><span class="sxs-lookup"><span data-stu-id="b7377-105">This topic discusses the formats for file paths that you can use on Windows systems.</span></span>

## <a name="traditional-dos-paths"></a><span data-ttu-id="b7377-106">従来の DOS パス</span><span class="sxs-lookup"><span data-stu-id="b7377-106">Traditional DOS paths</span></span>

<span data-ttu-id="b7377-107">標準 DOS パスは 3 つの要素で構成できます。</span><span class="sxs-lookup"><span data-stu-id="b7377-107">A standard DOS path can consist of three components:</span></span>

- <span data-ttu-id="b7377-108">ボリュームまたはドライブ文字とそれに続くボリューム区切り記号 (`:`)。</span><span class="sxs-lookup"><span data-stu-id="b7377-108">A volume or drive letter followed by the volume separator (`:`).</span></span>
- <span data-ttu-id="b7377-109">ディレクトリ名。</span><span class="sxs-lookup"><span data-stu-id="b7377-109">A directory name.</span></span> <span data-ttu-id="b7377-110">[ディレクトリ区切り文字](<xref:System.IO.Path.DirectorySeparatorChar>)によって、入れ子になっているディレクトリ階層内でサブディレクトリが分割されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-110">The [directory separator character](<xref:System.IO.Path.DirectorySeparatorChar>) separates subdirectories within the nested directory hierarchy.</span></span>
- <span data-ttu-id="b7377-111">任意のファイル名。</span><span class="sxs-lookup"><span data-stu-id="b7377-111">An optional filename.</span></span> <span data-ttu-id="b7377-112">[ディレクトリ区切り文字](<xref:System.IO.Path.DirectorySeparatorChar>)によって、ファイル パスとファイル名が分割されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-112">The [directory separator character](<xref:System.IO.Path.DirectorySeparatorChar>) separates the file path and the filename.</span></span>

<span data-ttu-id="b7377-113">3 つのコンポーネントがすべて存在する場合、パスは絶対パスになります。</span><span class="sxs-lookup"><span data-stu-id="b7377-113">If all three components are present, the path is absolute.</span></span> <span data-ttu-id="b7377-114">ボリュームまたはドライブ文字が指定されておらず、ディレクトリ名が[ディレクトリ区切り文字](<xref:System.IO.Path.DirectorySeparatorChar>)で始まる場合、パスは現在のドライブのルートからの相対パスとなります。</span><span class="sxs-lookup"><span data-stu-id="b7377-114">If no volume or drive letter is specified and the directory name begins with the [directory separator character](<xref:System.IO.Path.DirectorySeparatorChar>), the path is relative from the root of the current drive.</span></span> <span data-ttu-id="b7377-115">それ以外の場合、パスは現在のディレクトリに相対となります。</span><span class="sxs-lookup"><span data-stu-id="b7377-115">Otherwise, the path is relative to the current directory.</span></span> <span data-ttu-id="b7377-116">次の表では、想定されるディレクトリとファイル パスをいくつかまとめています。</span><span class="sxs-lookup"><span data-stu-id="b7377-116">The following table shows some possible directory and file paths.</span></span>

|<span data-ttu-id="b7377-117">パス</span><span class="sxs-lookup"><span data-stu-id="b7377-117">Path</span></span>  |<span data-ttu-id="b7377-118">説明</span><span class="sxs-lookup"><span data-stu-id="b7377-118">Description</span></span>  |
| -- | -- |
| `C:\Documents\Newsletters\Summer2018.pdf` | <span data-ttu-id="b7377-119">ドライブ C: のルートからの絶対ファイル パス。</span><span class="sxs-lookup"><span data-stu-id="b7377-119">An absolute file path from the root of drive C:</span></span> |
| `\Program Files\Custom Utilities\StringFinder.exe` | <span data-ttu-id="b7377-120">現在のドライブのルートからの絶対パス。</span><span class="sxs-lookup"><span data-stu-id="b7377-120">An absolute path from the root of the current drive.</span></span> |
| `2018\January.xlsx` | <span data-ttu-id="b7377-121">現在のディレクトリのサブディレクトリにあるファイルへの相対パス。</span><span class="sxs-lookup"><span data-stu-id="b7377-121">A relative path to a file in a subdirectory of the current directory.</span></span> |
| `..\Publications\TravelBrochure.pdf` | <span data-ttu-id="b7377-122">現在のディレクトリと同等になるディレクトリにあるファイルへの相対パス。</span><span class="sxs-lookup"><span data-stu-id="b7377-122">A relative path to file in a directory that is a peer of the current directory.</span></span> |
| `C:\Projects\apilibrary\apilibrary.sln` | <span data-ttu-id="b7377-123">ドライブ C: のルートからのファイルへの絶対パス。</span><span class="sxs-lookup"><span data-stu-id="b7377-123">An absolute path to a file from the root of drive C:</span></span> |
| `C:Projects\apilibrary\apilibrary.sln` | <span data-ttu-id="b7377-124">C: ドライブの現在のディレクトリからの相対パス。</span><span class="sxs-lookup"><span data-stu-id="b7377-124">A relative path from the current directory of the C: drive.</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="b7377-125">最後の 2 つのパスの違いにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="b7377-125">Note the difference between the last two paths.</span></span> <span data-ttu-id="b7377-126">いずれも任意のボリューム指定子を指定しますが (いずれの場合も C:)、最後から 2 番目のパスが指定ボリュームのルートから始まるのに対し、最後のパスは指定ボリュームのルートから始まりません。</span><span class="sxs-lookup"><span data-stu-id="b7377-126">Both specify the optional volume specifier (C: in both cases), but the first begins with the root of the specified volume, whereas the second does not.</span></span> <span data-ttu-id="b7377-127">結果として、最後から 2 番目のパスがドライブ C: のルート ディレクトリからの絶対パスであるのに対し、最後のパスはドライブ C: の現在のディレクトリからの相対パスになります。</span><span class="sxs-lookup"><span data-stu-id="b7377-127">As result, the first is an absolute path from the root directory of drive C:, whereas the second is a relative path from the current directory of drive C:.</span></span> <span data-ttu-id="b7377-128">最後から 2 番目のパス形式を意図しているときに最後のパス形式を使用することが、Windows ファイル パス関連のバグの共通の源になっています。</span><span class="sxs-lookup"><span data-stu-id="b7377-128">Use of the second form when the first is intended is a common source of bugs that involve Windows file paths.</span></span>

<span data-ttu-id="b7377-129"><xref:System.IO.Path.IsPathFullyQualified%2A?displayProperty=nameWthType> メソッドを呼び出すことで、ファイルが完全修飾であるかどうかを判断できます。完全修飾の場合、パスが現在のディレクトリに依存せず、現在のディレクトリが変更されても完全修飾のパスは変わりません。</span><span class="sxs-lookup"><span data-stu-id="b7377-129">You can determine whether a file path is fully qualified (that is, it the path is independent of the current directory and does not change when the current directory changes) by calling the <xref:System.IO.Path.IsPathFullyQualified%2A?displayProperty=nameWthType> method.</span></span> <span data-ttu-id="b7377-130">そのようなパスには相対ディレクトリのセグメント (`.` や `..`) が含まれている可能性があり、解決後のパスが常に同じ場所を指す場合、完全修飾できることにご留意ください。</span><span class="sxs-lookup"><span data-stu-id="b7377-130">Note that such a path can include relative directory segments (`.` and `..`) and still be fully qualified if the resolved path always points to the same location.</span></span>

<span data-ttu-id="b7377-131">次の例では、絶対パスと相対パスの違いを示します。</span><span class="sxs-lookup"><span data-stu-id="b7377-131">The following example illustrates the difference between absolute and relative paths.</span></span> <span data-ttu-id="b7377-132">ディレクトリ D:\FY2018\ が存在すること、この例を実行する前に、コマンド プロンプトから D:\ に現在のディレクトリを設定していないことを想定しています。</span><span class="sxs-lookup"><span data-stu-id="b7377-132">It assumes that the directory D:\FY2018\ exists, and that you haven't set any current directory for D:\ from the command prompt before running the example.</span></span>

[!code-csharp[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/cs/paths.cs)]
[!code-vb[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/vb/paths.vb)]

## <a name="unc-paths"></a><span data-ttu-id="b7377-133">UNC パス</span><span class="sxs-lookup"><span data-stu-id="b7377-133">UNC paths</span></span>

<span data-ttu-id="b7377-134">UNC (汎用命名規則) パスはネットワーク リソースへのアクセスに利用され、次の形式になっています。</span><span class="sxs-lookup"><span data-stu-id="b7377-134">Universal naming convention (UNC) paths, which are used to access network resources, have the following format:</span></span>

- <span data-ttu-id="b7377-135">サーバーまたはホストの名前。先頭に \\\\ が付きます。</span><span class="sxs-lookup"><span data-stu-id="b7377-135">A server or host name, which is prefaced by \\\\.</span></span> <span data-ttu-id="b7377-136">サーバー名は、NetBIOS マシン名か IP/FQDN アドレス (IPv4 と v6 に対応) にすることができます。</span><span class="sxs-lookup"><span data-stu-id="b7377-136">The server name can be a NetBIOS machine name or an IP/FQDN address (IPv4 as well as v6 are supported).</span></span>
- <span data-ttu-id="b7377-137">共有名。ホスト名とは \\ で区切られます。</span><span class="sxs-lookup"><span data-stu-id="b7377-137">A share name, which is separated from the host name by \\.</span></span> <span data-ttu-id="b7377-138">サーバーと共有名を合わせてボリュームになります。</span><span class="sxs-lookup"><span data-stu-id="b7377-138">Together, the server and share name make up the volume.</span></span>
- <span data-ttu-id="b7377-139">ディレクトリ名。</span><span class="sxs-lookup"><span data-stu-id="b7377-139">A directory name.</span></span> <span data-ttu-id="b7377-140">[ディレクトリ区切り文字](<xref:System.IO.Path.DirectorySeparatorChar>)によって、入れ子になっているディレクトリ階層内でサブディレクトリが分割されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-140">The [directory separator character](<xref:System.IO.Path.DirectorySeparatorChar>) separates subdirectories within the nested directory hierarchy.</span></span>
- <span data-ttu-id="b7377-141">任意のファイル名。</span><span class="sxs-lookup"><span data-stu-id="b7377-141">An optional filename.</span></span> <span data-ttu-id="b7377-142">[ディレクトリ区切り文字](<xref:System.IO.Path.DirectorySeparatorChar>)によって、ファイル パスとファイル名が分割されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-142">The [directory separator character](<xref:System.IO.Path.DirectorySeparatorChar>) separates the file path and the filename.</span></span>

<span data-ttu-id="b7377-143">UNC パスの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b7377-143">The following are some examples of UNC paths:</span></span>

|<span data-ttu-id="b7377-144">パス</span><span class="sxs-lookup"><span data-stu-id="b7377-144">Path</span></span>  |<span data-ttu-id="b7377-145">説明</span><span class="sxs-lookup"><span data-stu-id="b7377-145">Description</span></span>  |
| -- | -- |
| `\\system07\C$\` | <span data-ttu-id="b7377-146">`system07` の C: のルート ディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="b7377-146">The root directory of the C: drive on `system07`.</span></span> |
| `\\Server2\Share\Test\Foo.txt` | <span data-ttu-id="b7377-147">\\\\Server2\\Share ボリュームの Test ディレクトリの Foo.txt ファイル。</span><span class="sxs-lookup"><span data-stu-id="b7377-147">The Foo.txt file in the Test directory of the \\\\Server2\\Share volume.</span></span>|

<span data-ttu-id="b7377-148">UNC パスは常に完全修飾にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7377-148">UNC paths must always be fully qualified.</span></span> <span data-ttu-id="b7377-149">相対ディレクトリ セグメント (`.` や `..`) を含めることができますが、そのようなセグメントは完全修飾パスの一部にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7377-149">They can include relative directory segments (`.` and `..`), but these must be part of a fully qualified path.</span></span> <span data-ttu-id="b7377-150">相対パスは、UNC パスをドライブ文字にマッピングする方法でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="b7377-150">You can use relative paths only by mapping a UNC path to a drive letter.</span></span>

## <a name="dos-device-paths"></a><span data-ttu-id="b7377-151">DOS デバイス パス</span><span class="sxs-lookup"><span data-stu-id="b7377-151">DOS device paths</span></span>

<span data-ttu-id="b7377-152">Windows オペレーティング システムには、ファイルを含む、すべてのリソースを指す統一オブジェクト モデルがあります。</span><span class="sxs-lookup"><span data-stu-id="b7377-152">The Windows operating system has a unified object model that points to all resources, including files.</span></span> <span data-ttu-id="b7377-153">これらのオブジェクト パスにはコンソール ウィンドウからアクセスできます。また、これらのオブジェクト パスは、DOS と UNC のレガシ パスがマッピングされているシンボリック リンクの特別なフォルダーを介して Win32 層に公開されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-153">These object paths are accessible from the console window and are exposed to the Win32 layer through a special folder of symbolic links that legacy DOS and UNC paths are mapped to.</span></span> <span data-ttu-id="b7377-154">この特別なフォルダーには、DOS デバイス パス構文を介してアクセスできます。この構文は次のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="b7377-154">This special folder is accessed via the DOS device path syntax, which is one of:</span></span>

`\\.\C:\Test\Foo.txt`
`\\?\C:\Test\Foo.txt`

<span data-ttu-id="b7377-155">ドライブ文字でドライブを識別できるだけでなく、ボリューム GUID を使用してボリュームを識別できます。</span><span class="sxs-lookup"><span data-stu-id="b7377-155">In addition to identifying a drive by its drive letter, you can identify a volume by using its volume GUID.</span></span> <span data-ttu-id="b7377-156">次のような形式になります。</span><span class="sxs-lookup"><span data-stu-id="b7377-156">This takes the form:</span></span>

`\\.\Volume{b75e2c83-0000-0000-0000-602f00000000}\Test\Foo.txt`
`\\?\Volume{b75e2c83-0000-0000-0000-602f00000000}\Test\Foo.txt`

> [!NOTE]
> <span data-ttu-id="b7377-157">DOS デバイス パス構文は、Windows で実行されている .NET 実装でサポートされます。 .NET Core は 1.1 以降、.NET Framework は 4.6.2 以降となります。</span><span class="sxs-lookup"><span data-stu-id="b7377-157">DOS device path syntax is supported on .NET implementations running on Windows starting with .NET Core 1.1 and .NET Framework 4.6.2.</span></span>

<span data-ttu-id="b7377-158">DOS デバイス パスは次の要素から構成されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-158">The DOS device path consists of the following components:</span></span>

- <span data-ttu-id="b7377-159">デバイス パス指定子 (`\\.\` か `\\?\`)。この指定子により、DOS デバイス パスとしてパスが識別されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-159">The device path specifier (`\\.\` or `\\?\`), which identifies the path as a DOS device path.</span></span>

   > [!NOTE]
   > <span data-ttu-id="b7377-160">`\\?\` は、あらゆるバージョンの .NET Core とバージョン 4.6.2 以降の .NET Framework でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="b7377-160">The `\\?\` is supported in all versions of .NET Core and in the .NET Framework starting with version 4.6.2.</span></span>

- <span data-ttu-id="b7377-161">"実際の" デバイス オブジェクトへのシンボリック リンク (ドライブ名の場合は C:、ボリュームの GUID の場合は Volume{b75e2c83-0000-0000-0000-602f00000000})。</span><span class="sxs-lookup"><span data-stu-id="b7377-161">A symbolic link to the "real" device object (C: in the case of a drive name, or Volume{b75e2c83-0000-0000-0000-602f00000000} in the case of a volume GUID).</span></span>

   <span data-ttu-id="b7377-162">デバイス パス指定子の後の最初のセグメントによって、ボリュームまたはドライブが識別されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-162">The first segment of the DOS device path after the device path specifier identifies the volume or drive.</span></span> <span data-ttu-id="b7377-163">(たとえば、`\\?\C:\` や `\\.\BootPartition\`)。</span><span class="sxs-lookup"><span data-stu-id="b7377-163">(For example, `\\?\C:\` and `\\.\BootPartition\`.)</span></span>

   <span data-ttu-id="b7377-164">UNC のためのリンク (わかりやすいことに `UNC`) が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-164">There is a specific link for UNCs that is called, not surprisingly, `UNC`.</span></span> <span data-ttu-id="b7377-165">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="b7377-165">For example:</span></span>

  `\\.\UNC\Server\Share\Test\Foo.txt`
  `\\?\UNC\Server\Share\Test\Foo.txt`

    <span data-ttu-id="b7377-166">デバイス UNC の場合、サーバー/共有の部分がボリュームになります。</span><span class="sxs-lookup"><span data-stu-id="b7377-166">For device UNCs, the server/share portion forms the volume.</span></span> <span data-ttu-id="b7377-167">たとえば、`\\?\server1\e:\utilities\\filecomparer\` では、サーバー/共有部分は server1\utilities です。</span><span class="sxs-lookup"><span data-stu-id="b7377-167">For example, in `\\?\server1\e:\utilities\\filecomparer\`, the server/share portion is server1\utilities.</span></span> <span data-ttu-id="b7377-168">相対ディレクトリ セグメントのある <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> のようなメソッドを呼び出すとき、これは重要です。ボリュームを通り過ぎて移動することはできません。</span><span class="sxs-lookup"><span data-stu-id="b7377-168">This is significant when calling a method such as <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> with relative directory segments; it is never possible to navigate past the volume.</span></span>

<span data-ttu-id="b7377-169">DOS デバイス パスは定義によって完全修飾されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-169">DOS device paths are fully qualified by definition.</span></span> <span data-ttu-id="b7377-170">相対ディレクトリ セグメント (`.` や `..`) は許可されません。</span><span class="sxs-lookup"><span data-stu-id="b7377-170">Relative directory segments (`.` and `..`) are not allowed.</span></span> <span data-ttu-id="b7377-171">現在のディレクトリが使用されることはありません。</span><span class="sxs-lookup"><span data-stu-id="b7377-171">Current directories never enter into their usage.</span></span>

## <a name="example-ways-to-refer-to-the-same-file"></a><span data-ttu-id="b7377-172">例:同じファイルを参照する方法</span><span class="sxs-lookup"><span data-stu-id="b7377-172">Example: Ways to refer to the same file</span></span>

<span data-ttu-id="b7377-173">次の例では、<xref:System.IO> 名前空間で API を使用するとき、あるファイルを参照する方法をいくつか示しています。</span><span class="sxs-lookup"><span data-stu-id="b7377-173">The following example illustrates some of the ways in which you can refer to a file when using the APIs in the <xref:System.IO> namespace.</span></span> <span data-ttu-id="b7377-174">この例では <xref:System.IO.FileInfo> オブジェクトをインスタンス化し、その <xref:System.IO.FileInfo.Name> プロパティと <xref:System.IO.FileInfo.Length> プロパティを使用してファイルの名前と長さを表示します。</span><span class="sxs-lookup"><span data-stu-id="b7377-174">The example instantiates a <xref:System.IO.FileInfo> object and uses its <xref:System.IO.FileInfo.Name> and <xref:System.IO.FileInfo.Length> properties to display the filename and the length of the file.</span></span>

[!code-csharp[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/cs/file-refs.cs)]
[!code-vb[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/vb/file-refs.vb)]

## <a name="path-normalization"></a><span data-ttu-id="b7377-175">パスの正規化</span><span class="sxs-lookup"><span data-stu-id="b7377-175">Path normalization</span></span>

<span data-ttu-id="b7377-176">Windows API に渡されるパスはほとんどすべて正規化されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-176">Almost all paths passed to Windows APIs are normalized.</span></span> <span data-ttu-id="b7377-177">正規化の間、Windows では次の手順が実行されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-177">During normalization, Windows performs the following steps:</span></span>

- <span data-ttu-id="b7377-178">パスを識別します。</span><span class="sxs-lookup"><span data-stu-id="b7377-178">Identifies the path.</span></span>
- <span data-ttu-id="b7377-179">部分的に修飾された (相対) パスに現在のディレクトリが適用されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-179">Applies the current directory to partially qualified (relative) paths.</span></span>
- <span data-ttu-id="b7377-180">コンポーネントとディレクトリの区切り記号を正規化します。</span><span class="sxs-lookup"><span data-stu-id="b7377-180">Canonicalizes component and directory separators.</span></span>
- <span data-ttu-id="b7377-181">相対ディレクトリ コンポーネントを評価します (現在のディレクトリの場合は `.`、親ディレクトリの場合は `..`)。</span><span class="sxs-lookup"><span data-stu-id="b7377-181">Evaluates relative directory components (`.` for the current directory and `..` for the parent directory).</span></span>
- <span data-ttu-id="b7377-182">特定の文字をトリミングします。</span><span class="sxs-lookup"><span data-stu-id="b7377-182">Trims certain characters.</span></span>

<span data-ttu-id="b7377-183">この正規化は暗黙的に行われますが、<xref:System.IO.Path.GetFullPath%2A?displayProperty=nameWithType> メソッドを呼び出すことで明示的に行うことができます。このメソッドは [GetFullPathName() 関数](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea)の呼び出しをラップします。</span><span class="sxs-lookup"><span data-stu-id="b7377-183">This normalization happens implicitly, but you can do it explicitly by calling the <xref:System.IO.Path.GetFullPath%2A?displayProperty=nameWithType> method, which wraps a call to the  [GetFullPathName() function](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea).</span></span> <span data-ttu-id="b7377-184">Windows [GetFullPathName() 関数](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) を P/Invoke で直接呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="b7377-184">You can also call the Windows [GetFullPathName() function](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) directly using P/Invoke.</span></span>

### <a name="identifying-the-path"></a><span data-ttu-id="b7377-185">パスの識別</span><span class="sxs-lookup"><span data-stu-id="b7377-185">Identifying the path</span></span>

<span data-ttu-id="b7377-186">パス正規化の最初の手順は、パスの種類の識別です。</span><span class="sxs-lookup"><span data-stu-id="b7377-186">The first step in path normalization is identifying the type of path.</span></span> <span data-ttu-id="b7377-187">パスはいくつかあるカテゴリの 1 つに分類されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-187">Paths fall into one of a few categories:</span></span>

- <span data-ttu-id="b7377-188">パスはデバイス パスです。つまり、2 つの区切り記号で始まり、疑問符かピリオドが続きます (`\\?` または `\\.`)。</span><span class="sxs-lookup"><span data-stu-id="b7377-188">They are device paths; that is, they begin with two separators and a question mark or period (`\\?` or `\\.`).</span></span>
- <span data-ttu-id="b7377-189">パスは UNC パスです。つまり、2 つの区切り記号で始まります。疑問符やピリオドは付きません。</span><span class="sxs-lookup"><span data-stu-id="b7377-189">They are UNC paths; that is, they begin with two separators without a question mark or period.</span></span>
- <span data-ttu-id="b7377-190">パスは完全修飾 DOS パスです。つまり、ドライブ文字で始まり、ボリューム区切り記号、コンポーネント区切り記号が続きます (`C:\`)。</span><span class="sxs-lookup"><span data-stu-id="b7377-190">They are fully qualified DOS paths; that is, they begin with a drive letter, a volume separator, and a component separator (`C:\`).</span></span>
- <span data-ttu-id="b7377-191">レガシ デバイスを示します (`CON`、`LPT1`)。</span><span class="sxs-lookup"><span data-stu-id="b7377-191">They designate a legacy device (`CON`, `LPT1`).</span></span>
- <span data-ttu-id="b7377-192">現在のドライブのルートに相対です。つまり、1 つのコンポーネント区切り記号で始まります (`\`)。</span><span class="sxs-lookup"><span data-stu-id="b7377-192">They are relative to the root of the current drive; that is, they begin with a single component separator (`\`).</span></span>
- <span data-ttu-id="b7377-193">指定ドライブの現在のディレクトリに相対です。つまり、ドライブ文字で始まり、ボリューム区切り記号が続きますが、コンポーネント区切り記号はありません (`C:`)。</span><span class="sxs-lookup"><span data-stu-id="b7377-193">They are relative to the current directory of a specified drive; that is, they begin with a drive letter, a volume separator, and no component separator (`C:`).</span></span>
- <span data-ttu-id="b7377-194">現在のディレクトリに相対です。つまり、パスの最初の要素は問われません (`temp\testfile.txt`)。</span><span class="sxs-lookup"><span data-stu-id="b7377-194">They are relative to the current directory; that is, they begin with anything else (`temp\testfile.txt`).</span></span>

<span data-ttu-id="b7377-195">パスの種類によって、現在のディレクトリが何らかの方法で適用されるかどうかが決まります。</span><span class="sxs-lookup"><span data-stu-id="b7377-195">The type of the path determines whether or not a current directory is applied in some way.</span></span> <span data-ttu-id="b7377-196">パスの "ルート" も決定されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-196">It also determines what the "root" of the path is.</span></span>

### <a name="handling-legacy-devices"></a><span data-ttu-id="b7377-197">レガシ デバイスの取り扱い</span><span class="sxs-lookup"><span data-stu-id="b7377-197">Handling legacy devices</span></span>

<span data-ttu-id="b7377-198">パスが `CON`、`COM1`、`LPT1` など、レガシ DOS デバイスの場合、`\\.\` を先頭に付けることでデバイス パスに変換した上で返されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-198">If the path is a legacy DOS device such as `CON`, `COM1`, or `LPT1`, it is converted into a device path by prepending `\\.\` and returned.</span></span>

<span data-ttu-id="b7377-199"><xref:System.IO.Path.GetFullPath(System.String)?displayProperty=nameWithType> メソッドは、レガシ デバイス名で始まるパスを常にレガシ デバイスとして解釈します。</span><span class="sxs-lookup"><span data-stu-id="b7377-199">A path that begins with a legacy device name is always interpreted as a legacy device by the <xref:System.IO.Path.GetFullPath(System.String)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b7377-200">たとえば、`CON.TXT` の DOS デバイス パスは `\\.\CON` であり、`COM1.TXT\file1.txt` の DOS デバイス パスは `\\.\COM1` です。</span><span class="sxs-lookup"><span data-stu-id="b7377-200">For example, the DOS device path for `CON.TXT` is `\\.\CON`, and the DOS device path for `COM1.TXT\file1.txt` is `\\.\COM1`.</span></span>

### <a name="applying-the-current-directory"></a><span data-ttu-id="b7377-201">現在のディレクトリを適用する</span><span class="sxs-lookup"><span data-stu-id="b7377-201">Applying the current directory</span></span>

<span data-ttu-id="b7377-202">パスが完全修飾ではない場合、Windows はそのパスに現在のディレクトリを適用します。</span><span class="sxs-lookup"><span data-stu-id="b7377-202">If a path isn't fully qualified, Windows applies the current directory to it.</span></span> <span data-ttu-id="b7377-203">UNC とデバイス パスの場合、現在のディレクトリは適用されません。</span><span class="sxs-lookup"><span data-stu-id="b7377-203">UNCs and device paths do not have the current directory applied.</span></span> <span data-ttu-id="b7377-204">区切り記号 (C:\\) を使用するフル ドライブの場合も適用されません。</span><span class="sxs-lookup"><span data-stu-id="b7377-204">Neither does a full drive with separator C:\\.</span></span>

<span data-ttu-id="b7377-205">パスが 1 つのコンポーネント区切り記号で始まる場合、現在のディレクトリからのドライブが適用されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-205">If the path starts with a single component separator, the drive from the current directory is applied.</span></span> <span data-ttu-id="b7377-206">たとえば、ファイル パスが `\utilities` で、現在のディレクトリが `C:\temp\` の場合、正規化の結果、`C:\utilities` になります。</span><span class="sxs-lookup"><span data-stu-id="b7377-206">For example, if the file path is `\utilities` and the current directory is `C:\temp\`, normalization produces `C:\utilities`.</span></span>

<span data-ttu-id="b7377-207">パスがドライブ文字で始まり、ボリューム区切り記号が続くが、コンポーネント区切り記号はない場合、指定ドライブのコマンド シェルから設定された最後の現在のディレクトリが適用されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-207">If the path starts with a drive letter, volume separator, and no component separator, the last current directory set from the command shell for the specified drive is applied.</span></span> <span data-ttu-id="b7377-208">最後の現在のディレクトリが設定されなかった場合、ドライブだけが適用されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-208">If the last current directory was not set, the drive alone is applied.</span></span> <span data-ttu-id="b7377-209">たとえば、ファイル パスが `D:sources`、現在のディレクトリが `C:\Documents\`、ドライブ D: の最後の現在のディレクトリが `D:\sources\` の場合、結果は `D:\sources\sources` になります。</span><span class="sxs-lookup"><span data-stu-id="b7377-209">For example, if the file path is `D:sources`, the current directory is `C:\Documents\`, and the last current directory on drive D: was `D:\sources\`, the result is `D:\sources\sources`.</span></span> <span data-ttu-id="b7377-210">プログラムやスクリプト ロジックでエラーが出るとき、一般的に、このような "ドライブ相対" パスが原因となります。</span><span class="sxs-lookup"><span data-stu-id="b7377-210">These "drive relative" paths are a common source of program and script logic errors.</span></span> <span data-ttu-id="b7377-211">文字やコロンで始まるパスは相対ではないと考えることは明らかに正しくありません。</span><span class="sxs-lookup"><span data-stu-id="b7377-211">Assuming that a path beginning with a letter and a colon isn't relative is obviously not correct.</span></span>

<span data-ttu-id="b7377-212">パスが区切り記号以外で始まる場合、現在のドライブと現在のディレクトリが適用されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-212">If the path starts with something other than a separator, the current drive and current directory are applied.</span></span> <span data-ttu-id="b7377-213">たとえば、パスが `filecompare` で、現在のディレクトリが `C:\utilities\` の場合、結果は `C:\utilities\filecompare\` です。</span><span class="sxs-lookup"><span data-stu-id="b7377-213">For example, if the path is `filecompare` and the current directory is `C:\utilities\`, the result is `C:\utilities\filecompare\`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b7377-214">マルチスレッド アプリケーションの場合 (つまり、ほとんどのアプリケーションでは)、現在のディレクトリはプロセスごとの設定となるため、相対パスは危険です。</span><span class="sxs-lookup"><span data-stu-id="b7377-214">Relative paths are dangerous in multithreaded applications (that is, most applications) because the current directory is a per-process setting.</span></span> <span data-ttu-id="b7377-215">スレッドによって現在のディレクトリが変更されることは、いつでも起こりえることです。</span><span class="sxs-lookup"><span data-stu-id="b7377-215">Any thread can change the current directory at any time.</span></span> <span data-ttu-id="b7377-216">.NET Core 2.1 以降、<xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> メソッドを呼び出し、絶対パスに対して解決する場合、相対パスと基本パス (現在のディレクトリ) から絶対パスを取得できます。</span><span class="sxs-lookup"><span data-stu-id="b7377-216">Starting with .NET Core 2.1, you can call the <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> method to get an absolute path from a relative path and the base path (the current directory) that you want to resolve it against.</span></span>

### <a name="canonicalizing-separators"></a><span data-ttu-id="b7377-217">区切り記号の正規化</span><span class="sxs-lookup"><span data-stu-id="b7377-217">Canonicalizing separators</span></span>

<span data-ttu-id="b7377-218">フォワード スラッシュ (`/`) はすべて標準の Windows 区切り記号であるバック スラッシュ (`\`) に変換されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-218">All forward slashes (`/`) are converted into the standard Windows separator, the back slash (`\`).</span></span> <span data-ttu-id="b7377-219">フォワード スラッシュがあるとき、最初の 2 つのスラッシュに続くスラッシュはすべて 1 つのスラッシュにまとめられます。</span><span class="sxs-lookup"><span data-stu-id="b7377-219">If they are present, a series of slashes that follow the first two slashes are collapsed into a single slash.</span></span>

### <a name="evaluating-relative-components"></a><span data-ttu-id="b7377-220">相対コンポーネントを評価する</span><span class="sxs-lookup"><span data-stu-id="b7377-220">Evaluating relative components</span></span>

<span data-ttu-id="b7377-221">パスが処理されるとき、1 つか 2 つのピリオド (`.` や `..`) で構成されているコンポーネントやセグメントがあればそれは評価されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-221">As the path is processed, any components or segments that are composed of a single or a double period (`.` or `..`) are evaluated:</span></span>

- <span data-ttu-id="b7377-222">ピリオドが 1 つの場合、現在のセグメントが削除されます。現在のディレクトリを参照するためです。</span><span class="sxs-lookup"><span data-stu-id="b7377-222">For a single period, the current segment is removed, since it refers to the current directory.</span></span>

- <span data-ttu-id="b7377-223">ピリオドが 2 つの場合、現在のセグメントと親セグメントが削除されます。二重ピリオドは親ディレクトリを参照するためです。</span><span class="sxs-lookup"><span data-stu-id="b7377-223">For a double period, the current segment and the parent segment are removed, since the double period refers to the parent directory.</span></span>

   <span data-ttu-id="b7377-224">親ディレクトリは、それがパスのルートを通らない場合にのみ削除されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-224">Parent directories are only removed if they aren't past the root of the path.</span></span> <span data-ttu-id="b7377-225">パスのルートは、パスの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="b7377-225">The root of the path depends on the type of path.</span></span> <span data-ttu-id="b7377-226">DOS パスの場合はドライブ (`C:\`)、UNC の場合はサーバー/共有 (`\\Server\Share`)、デバイス パスの場合はデバイス パス プレフィックス (`\\?\` または `\\.\`) となります。</span><span class="sxs-lookup"><span data-stu-id="b7377-226">It is the drive (`C:\`) for DOS paths, the server/share for UNCs (`\\Server\Share`), and the device path prefix for device paths (`\\?\` or `\\.\`).</span></span>

### <a name="trimming-characters"></a><span data-ttu-id="b7377-227">文字のトリミング</span><span class="sxs-lookup"><span data-stu-id="b7377-227">Trimming characters</span></span>

<span data-ttu-id="b7377-228">一連の区切り記号や相対セグメントが削除されることを確認しましたが、それに加え、正規化の間、一部の追加文字が削除されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-228">Along with the runs of separators and relative segments removed earlier, some additional characters are removed during normalization:</span></span>

- <span data-ttu-id="b7377-229">セグメントがシングル ピリオドで終わる場合、そのピリオドは削除されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-229">If a segment ends in a single period, that period is removed.</span></span> <span data-ttu-id="b7377-230">(シングルまたはダブル ピリオドのセグメントは前の手順で正規化されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-230">(A segment of a single or double period is normalized in the previous step.</span></span> <span data-ttu-id="b7377-231">ピリオドが 3 つ以上のセグメントは正規化されません。実際には、有効なファイル/ディレクトリ名です。)</span><span class="sxs-lookup"><span data-stu-id="b7377-231">A segment of three or more periods is not normalized and is actually a valid file/directory name.)</span></span>

- <span data-ttu-id="b7377-232">パスの終わりが区切り記号ではない場合、後ろに続くピリオドとスペース (U+0020) はすべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-232">If the path doesn't end in a separator, all trailing periods and spaces (U+0020) are removed.</span></span> <span data-ttu-id="b7377-233">最後のセグメントがシングルまたはダブル ピリオドの場合、上記の相対コンポーネント ルールに該当します。</span><span class="sxs-lookup"><span data-stu-id="b7377-233">If the last segment is simply a single or double period, it falls under the relative components rule above.</span></span>

   <span data-ttu-id="b7377-234">このルールによると、スペースの後に区切り記号を追加することで、スペースが後ろに続くディレクトリ名を作成できます。</span><span class="sxs-lookup"><span data-stu-id="b7377-234">This rule means that you can create a directory name with a trailing space by adding a trailing separator after the space.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="b7377-235">スペースが後ろに続くディレクトリやファイル名は**決して**作成しないでください。</span><span class="sxs-lookup"><span data-stu-id="b7377-235">You should **never** create a directory or filename with a trailing space.</span></span> <span data-ttu-id="b7377-236">後続スペースはディレクトリへのアクセスを困難または不可能にします。一般的に、名前に後続スペースが含まれるディレクトリやファイルを処理しようとすると、アプリケーションは失敗します。</span><span class="sxs-lookup"><span data-stu-id="b7377-236">Trailing spaces can make it difficult or impossible to access a directory, and applications commonly fail when attempting to handle directories or files whose names include trailing spaces.</span></span>

## <a name="skipping-normalization"></a><span data-ttu-id="b7377-237">正規化の省略</span><span class="sxs-lookup"><span data-stu-id="b7377-237">Skipping normalization</span></span>

<span data-ttu-id="b7377-238">通常、Windows API に渡されるパスはすべて、[GetFullPathName 関数](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea)に (効果的に) 渡され、正規化されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-238">Normally, any path passed to a Windows API is (effectively) passed to the [GetFullPathName function](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) and normalized.</span></span> <span data-ttu-id="b7377-239">重要な例外が 1 つあります。ピリオドではなく疑問符から始まるデバイス パスです。</span><span class="sxs-lookup"><span data-stu-id="b7377-239">There is one important exception: a device path that begins with a question mark instead of a period.</span></span> <span data-ttu-id="b7377-240">厳密に `\\?\` で始まらない限り (正規のバックスラッシュが使われていることに注目してください)、パスは正規化されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-240">Unless the path starts exactly with `\\?\` (note the use of the canonical backslash), it is normalized.</span></span>

<span data-ttu-id="b7377-241">正規化の省略が必要となる理由について考えてみます。</span><span class="sxs-lookup"><span data-stu-id="b7377-241">Why would you want to skip normalization?</span></span> <span data-ttu-id="b7377-242">大きな理由が 3 つあります。</span><span class="sxs-lookup"><span data-stu-id="b7377-242">There are three major reasons:</span></span>

1. <span data-ttu-id="b7377-243">通常は利用できないが正当なパスにアクセスするため。</span><span class="sxs-lookup"><span data-stu-id="b7377-243">To get access to paths that are normally unavailable but are legal.</span></span> <span data-ttu-id="b7377-244">たとえば、`hidden.` というファイルまたはディレクトリには他の方法ではアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="b7377-244">A file or directory called `hidden.`, for example, is impossible to access in any other way.</span></span>

1. <span data-ttu-id="b7377-245">既に正規化している場合、省略することでパフォーマンスを改善するため。</span><span class="sxs-lookup"><span data-stu-id="b7377-245">To improve performance by skipping normalization if you've already normalized.</span></span>

1. <span data-ttu-id="b7377-246">.NET Framework でのみ、259 文字を超えるパスの場合、パス長の `MAX_PATH` チェックを省略できます。</span><span class="sxs-lookup"><span data-stu-id="b7377-246">On the .NET Framework only, to skip the `MAX_PATH` check for path length to allow for paths that are greater than 259 characters.</span></span> <span data-ttu-id="b7377-247">一部例外がありますが、ほとんどの API でこれが可能です。</span><span class="sxs-lookup"><span data-stu-id="b7377-247">Most APIs allow this, with some exceptions.</span></span>

> [!NOTE]
> <span data-ttu-id="b7377-248">.NET Core は長いパスを暗黙的に処理し、`MAX_PATH` チェックを実行しません。</span><span class="sxs-lookup"><span data-stu-id="b7377-248">.NET Core handles long paths implicitly and does not perform a `MAX_PATH` check.</span></span> <span data-ttu-id="b7377-249">`MAX_PATH` は .NET Framework にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-249">The `MAX_PATH` check applies only to the .NET Framework.</span></span>

<span data-ttu-id="b7377-250">正規化と MAX_PATH チェックの省略は、2 つのデバイス パス構文の間の唯一の違いです。それ以外、この 2 つは同じです。</span><span class="sxs-lookup"><span data-stu-id="b7377-250">Skipping normalization and max path checks is the only difference between the two device path syntaxes; they are otherwise identical.</span></span> <span data-ttu-id="b7377-251">正規化の省略には注意してください。"普通の" アプリケーションでは処理できないパスが簡単に作られてしまいます。</span><span class="sxs-lookup"><span data-stu-id="b7377-251">Be careful with skipping normalization, since you can easily create paths that are difficult for "normal" applications to deal with.</span></span>

<span data-ttu-id="b7377-252">`\\?\` で始まるパスは、[GetFullPathName 関数](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea)に明示的に渡す場合、正規化されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-252">Paths that start with `\\?\` are still normalized if you explicitly pass them to the [GetFullPathName function](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea).</span></span>

<span data-ttu-id="b7377-253">`MAX_PATH` 文字を超えるパスは `\\?\` なしで [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="b7377-253">You can pass paths of more than `MAX_PATH` characters to [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) without `\\?\`.</span></span> <span data-ttu-id="b7377-254">Windows で処理できる最大文字列サイズまで、任意の長さのパスがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="b7377-254">It supports arbitrary length paths up to the maximum string size that Windows can handle.</span></span>

## <a name="case-and-the-windows-file-system"></a><span data-ttu-id="b7377-255">大文字/小文字の区別と Windows ファイル システム</span><span class="sxs-lookup"><span data-stu-id="b7377-255">Case and the Windows file system</span></span>

<span data-ttu-id="b7377-256">Windows を使っていないユーザーや開発者がとまどうことには、Windows ファイル システムではパス名とディレクトリ名で大文字と小文字が区別されないという特徴があります。</span><span class="sxs-lookup"><span data-stu-id="b7377-256">A peculiarity of the Windows file system that non-Windows users and developers find confusing is that path and directory names are case-insensitive.</span></span> <span data-ttu-id="b7377-257">つまり、ディレクトリ名とファイル名は、それが作成されたときの大文字/小文字の使い分けを反映します。</span><span class="sxs-lookup"><span data-stu-id="b7377-257">That is, directory and file names reflect the casing of the strings used when they are created.</span></span> <span data-ttu-id="b7377-258">たとえば、次のメソッドを呼び出すと、</span><span class="sxs-lookup"><span data-stu-id="b7377-258">For example, the method call</span></span>

```csharp
Directory.Create("TeStDiReCtOrY");
```

```vb
Directory.Create("TeStDiReCtOrY")
```

<span data-ttu-id="b7377-259">TeStDiReCtOrY という名前のディレクトリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-259">creates a directory named TeStDiReCtOrY.</span></span> <span data-ttu-id="b7377-260">ディレクトリやファイルの名前を変更し、大文字を小文字に変えるか、小文字を大文字に変えると、その名前変更時の大文字/小文字の使い方がディレクトリ名またはファイル名に反映されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-260">If you rename a directory or file to change its case, the directory or file name reflects the case of the string used when you rename it.</span></span> <span data-ttu-id="b7377-261">たとえば、次のコードでは test.txt というファイルの名前が Test.txt に変更されます。</span><span class="sxs-lookup"><span data-stu-id="b7377-261">For example, the following code renames a file named test.txt to Test.txt:</span></span>

[!code-csharp[case-and-renaming](~/samples/snippets/standard/io/file-names/cs/rename.cs)]
[!code-vb[case-and-renaming](~/samples/snippets/standard/io/file-names/vb/rename.vb)]

<span data-ttu-id="b7377-262">しかしながら、ディレクトリ名とファイル名の比較では、大文字と小文字が区別されません。</span><span class="sxs-lookup"><span data-stu-id="b7377-262">However, directory and file name comparisons are case-insensitive.</span></span> <span data-ttu-id="b7377-263">"test.txt" という名前のファイルを検索すると、.NET ファイル システム API は比較で大文字/小文字の使い方を無視します。</span><span class="sxs-lookup"><span data-stu-id="b7377-263">If you search for a file named "test.txt", .NET file system APIs ignore case in the comparison.</span></span> <span data-ttu-id="b7377-264">Test.txt、TEST.TXT、test.TXT、大文字と小文字のその他すべての組み合わせが "test.txt" に一致します。</span><span class="sxs-lookup"><span data-stu-id="b7377-264">Test.txt, TEST.TXT, test.TXT, and any other combination of upper- and lowercase letters will match "test.txt".</span></span>
