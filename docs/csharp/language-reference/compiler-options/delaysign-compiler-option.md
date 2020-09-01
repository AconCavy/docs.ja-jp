---
description: -delaysign (C# コンパイラ オプション)
title: -delaysign (C# コンパイラ オプション)
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: 5512ebeca4672f5d69852ab07c3f3fa40c305327
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125840"
---
# <a name="-delaysign-c-compiler-options"></a><span data-ttu-id="cb012-103">-delaysign (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="cb012-103">-delaysign (C# Compiler Options)</span></span>

<span data-ttu-id="cb012-104">このオプションを使用すると、出力ファイルに署名用のスペースが予約され、デジタル署名を後で追加できるようになります。</span><span class="sxs-lookup"><span data-stu-id="cb012-104">This option causes the compiler to reserve space in the output file so that a digital signature can be added later.</span></span>

## <a name="syntax"></a><span data-ttu-id="cb012-105">構文</span><span class="sxs-lookup"><span data-stu-id="cb012-105">Syntax</span></span>

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a><span data-ttu-id="cb012-106">引数</span><span class="sxs-lookup"><span data-stu-id="cb012-106">Arguments</span></span>

<span data-ttu-id="cb012-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="cb012-107">`+` &#124; `-`</span></span>

<span data-ttu-id="cb012-108">完全署名されたアセンブリを作成する場合は、 **-delaysign-** を使用します。</span><span class="sxs-lookup"><span data-stu-id="cb012-108">Use **-delaysign-** if you want a fully signed assembly.</span></span> <span data-ttu-id="cb012-109">アセンブリに公開キーだけを含める場合は、**-delaysign+** を使用します。</span><span class="sxs-lookup"><span data-stu-id="cb012-109">Use **-delaysign+** if you only want to place the public key in the assembly.</span></span> <span data-ttu-id="cb012-110">既定値は **-delaysign-** です。</span><span class="sxs-lookup"><span data-stu-id="cb012-110">The default is **-delaysign-**.</span></span>

## <a name="remarks"></a><span data-ttu-id="cb012-111">注釈</span><span class="sxs-lookup"><span data-stu-id="cb012-111">Remarks</span></span>

<span data-ttu-id="cb012-112">**-delaysign** オプションは、[-keyfile](./keyfile-compiler-option.md) または [-keycontainer](./keycontainer-compiler-option.md) と共に使用しない場合、無効になります。</span><span class="sxs-lookup"><span data-stu-id="cb012-112">The **-delaysign** option has no effect unless used with [-keyfile](./keyfile-compiler-option.md) or [-keycontainer](./keycontainer-compiler-option.md).</span></span>

<span data-ttu-id="cb012-113">**-delaysign** オプションと **-publicsign** オプションは相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="cb012-113">The **-delaysign** and **-publicsign** options are mutually exclusive.</span></span>

<span data-ttu-id="cb012-114">アセンブリに完全に署名するように指定すると、コンパイラはマニフェスト (アセンブリ メタデータ) を含むファイルをハッシュし、秘密キーでそのハッシュに署名します。</span><span class="sxs-lookup"><span data-stu-id="cb012-114">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="cb012-115">その処理により、マニフェストを含むファイルに格納されるデジタル署名が作成されます。</span><span class="sxs-lookup"><span data-stu-id="cb012-115">That operation creates a digital signature which is stored in the file that contains the manifest.</span></span> <span data-ttu-id="cb012-116">アセンブリを遅延署名に設定すると、コンパイラは署名の計算も格納も行いませんが、後で署名を追加できるようにファイルに領域を確保します。</span><span class="sxs-lookup"><span data-stu-id="cb012-116">When an assembly is delay signed, the compiler does not compute and store the signature, but reserves space in the file so the signature can be added later.</span></span>

<span data-ttu-id="cb012-117">たとえば、**-delaysign+** を指定すると、テスト時にはアセンブリをグローバル キャッシュに格納できます。</span><span class="sxs-lookup"><span data-stu-id="cb012-117">For example, using **-delaysign+** allows a tester to put the assembly in the global cache.</span></span> <span data-ttu-id="cb012-118">テスト後に、[アセンブリ リンカー](../../../framework/tools/al-exe-assembly-linker.md) ユーティリティを使用してアセンブリに秘密キーを配置することにより、そのアセンブリに完全署名できます。</span><span class="sxs-lookup"><span data-stu-id="cb012-118">After testing, you can fully sign the assembly by placing the private key in the assembly using the [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) utility.</span></span>

<span data-ttu-id="cb012-119">詳しくは、「[厳密な名前付きアセンブリの作成と使用](../../../standard/assembly/create-use-strong-named.md)」および「[アセンブリへの遅延署名](../../../standard/assembly/delay-sign.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cb012-119">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="cb012-120">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="cb012-120">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="cb012-121">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="cb012-121">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="cb012-122">**[遅延署名のみ]** プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="cb012-122">Modify the **Delay sign only** property.</span></span>

<span data-ttu-id="cb012-123">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.DelaySign%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb012-123">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb012-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb012-124">See also</span></span>

- [<span data-ttu-id="cb012-125">C# の -publicsign オプション</span><span class="sxs-lookup"><span data-stu-id="cb012-125">C# -publicsign option</span></span>](publicsign-compiler-option.md)
- [<span data-ttu-id="cb012-126">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="cb012-126">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="cb012-127">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="cb012-127">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
