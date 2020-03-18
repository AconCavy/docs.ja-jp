---
title: '軽減策: 製品のバージョン管理'
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
ms.openlocfilehash: 64a68d2b79a0a3ccdd806949ffd6cb3760974390
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457812"
---
# <a name="mitigation-product-versioning"></a><span data-ttu-id="4a307-102">軽減策: 製品のバージョン管理</span><span class="sxs-lookup"><span data-stu-id="4a307-102">Mitigation: Product Versioning</span></span>

<span data-ttu-id="4a307-103">.NET Framework 4.6 以降のバージョンでは、製品のバージョン管理が .NET Framework の以前のリリース (.NET Framework 4、4.5、4.5.1、4.5.2) から変更されました。</span><span class="sxs-lookup"><span data-stu-id="4a307-103">In the .NET Framework 4.6 and later, product versioning has changed from the previous releases of the .NET Framework (the .NET Framework 4, 4.5, 4.5.1, and 4.5.2).</span></span>

## <a name="product-versioning-changes"></a><span data-ttu-id="4a307-104">製品のバージョン管理の変更点</span><span class="sxs-lookup"><span data-stu-id="4a307-104">Product versioning changes</span></span>

<span data-ttu-id="4a307-105">変更の詳細は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4a307-105">The following are the detailed changes:</span></span>

- <span data-ttu-id="4a307-106">`Version` キーの `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` 値エントリの形式は、.NET Framework 4.6 とそのポイント リリースの場合は `4.6.`*xxxxx* に、.NET Framework 4.7 の場合は `4.7.`*xxxxx* にそれぞれ変更されました。</span><span class="sxs-lookup"><span data-stu-id="4a307-106">The value of the `Version` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key has changed to `4.6.`*xxxxx* for the .NET Framework 4.6 and its point releases, and to `4.7.`*xxxxx* for the .NET Framework 4.7.</span></span> <span data-ttu-id="4a307-107">.NET Framework 4.5、4.5.1、および 4.5.2 では `4.5.`*xxxxx* という形式でした。</span><span class="sxs-lookup"><span data-stu-id="4a307-107">In the .NET Framework 4.5, 4.5.1, and 4.5.2, it had the format `4.5.`*xxxxx*.</span></span>

- <span data-ttu-id="4a307-108">.NET Framework ファイルにおけるファイルおよび製品のバージョン管理は、.NET Framework 4.6 とそのポイント リリースの場合は以前のスキーマのバージョン管理 `4.0.30319.x` から `4.6.X.0` に、.NET Framework 4.7 とそのポイント リリースの場合は `4.7.X.0` にそれぞれ変更されました。</span><span class="sxs-lookup"><span data-stu-id="4a307-108">The file and product versioning for .NET Framework files has changed from the earlier versioning scheme of `4.0.30319.x` to `4.6.X.0` for the .NET Framework 4.6 and its point releases, and to `4.7.X.0` for the .NET Framework 4.7 and its point releases.</span></span> <span data-ttu-id="4a307-109">ファイルを右クリックしてファイルの **[プロパティ]** を表示すると、これらの新しい値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4a307-109">You can see these new values when you view the file's **Properties** after right-clicking on a file.</span></span>

- <span data-ttu-id="4a307-110">マネージド アセンブリの <xref:System.Reflection.AssemblyFileVersionAttribute> 属性と <xref:System.Reflection.AssemblyInformationalVersionAttribute> 属性の <xref:System.Version> 値は、.NET Framework 4.6 とそのポイント リリースの場合は `4.6.X.0` という形式、.NET Framework 4.7 の場合は `4.7.X.0` という形式になります。</span><span class="sxs-lookup"><span data-stu-id="4a307-110">The <xref:System.Reflection.AssemblyFileVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes for managed assemblies have <xref:System.Version> values in the form `4.6.X.0` for the .NET Framework 4.6 and its point releases, and `4.7.X.0` for the .NET Framework 4.7.</span></span>

- <span data-ttu-id="4a307-111">.NET Framework 4.6 以降では、<xref:System.Environment.Version%2A?displayProperty=nameWithType> プロパティによって固定のバージョン文字列 `4.0.30319.42000` が返されます。</span><span class="sxs-lookup"><span data-stu-id="4a307-111">Starting with .NET Framework 4.6, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns the fixed version string `4.0.30319.42000`.</span></span> <span data-ttu-id="4a307-112">.NET Framework 4、4.5、4.5.1、4.5.2 では、`4.0.30319.xxxxx` という形式のバージョン文字列が返されます。ここでの `xxxxx` は 42000 より小さいです (例: "4.0.30319.18010")。</span><span class="sxs-lookup"><span data-stu-id="4a307-112">In the .NET Framework 4, 4.5, 4.5.1, and 4.5.2, it returns version strings in the format `4.0.30319.xxxxx` where `xxxxx` is less than 42000 (for example, "4.0.30319.18010").</span></span> <span data-ttu-id="4a307-113">アプリケーションのコードで <xref:System.Environment.Version%2A?displayProperty=nameWithType> プロパティに新しい依存関係を設定することは推奨していないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4a307-113">Note that we do not recommend application code taking any new dependency on the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property.</span></span>

### <a name="handling-the-product-versioning-changes"></a><span data-ttu-id="4a307-114">製品のバージョン管理の変更に対する処置</span><span class="sxs-lookup"><span data-stu-id="4a307-114">Handling the product versioning changes</span></span>

<span data-ttu-id="4a307-115">一般に、.NET Framework のランタイムのバージョンやインストール ディレクトリを検出する際、アプリケーションは推奨される技法に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a307-115">In general, applications should depend on the recommended techniques for detecting such things as the runtime version of the .NET Framework and the installation directory:</span></span>

- <span data-ttu-id="4a307-116">.NET Framework のランタイムのバージョンを検出するには、「[方法 : インストールされている .NET Framework バージョンを確認する](how-to-determine-which-versions-are-installed.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a307-116">To detect the runtime version of the .NET Framework, see [How to: Determine Which .NET Framework Versions Are Installed](how-to-determine-which-versions-are-installed.md).</span></span>

- <span data-ttu-id="4a307-117">.NET Framework のインストール パスを確認するには、`InstallPath` キーの `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` エントリの値を使用します。</span><span class="sxs-lookup"><span data-stu-id="4a307-117">To determine the installation path for the .NET Framework, use the value of the `InstallPath` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="4a307-118">サブキー名は、`NET Framework Setup` ではなく `.NET Framework Setup` です。</span><span class="sxs-lookup"><span data-stu-id="4a307-118">The subkey name is `NET Framework Setup`, not `.NET Framework Setup`.</span></span>

- <span data-ttu-id="4a307-119">.NET Framework の共通言語ランタイムへのディレクトリ パスを確認するには、<xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4a307-119">To determine the directory path to the .NET Framework common language runtime, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="4a307-120">CLR のバージョンを取得するには、<xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4a307-120">To get the CLR version, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> method.</span></span>   <span data-ttu-id="4a307-121">.NET Framework 4 とそのポイント リリース (.NET Framework 4.5、4.5.1、4.5.2、および .NET Framework 4.6、4.6.1、4.6.2、4.7) の場合、それによって文字列 `v4.0.30319` が返されます。</span><span class="sxs-lookup"><span data-stu-id="4a307-121">For the .NET Framework 4 and its point releases (the .NET Framework 4.5, 4.5.1, 4.5.2, and .NET Framework 4.6, 4.6.1, 4.6.2, and 4.7), it returns the string `v4.0.30319`.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a307-122">参照</span><span class="sxs-lookup"><span data-stu-id="4a307-122">See also</span></span>

- [<span data-ttu-id="4a307-123">アプリケーションの互換性</span><span class="sxs-lookup"><span data-stu-id="4a307-123">Application compatibility</span></span>](application-compatibility.md)
