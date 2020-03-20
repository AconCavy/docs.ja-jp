---
title: Ilasm.exe (IL アセンブラー)
ms.date: 03/30/2017
helpviewer_keywords:
- MSIL generators
- metadata, MSIL Assembler
- MSIL Assembler
- portable executable files, MSIL Assembler
- PE files, MSIL Assembler
- MSIL
- Ilasm.exe
- verifying MSIL performance
ms.assetid: 4ca3a4f0-4400-47ce-8936-8e219961c76f
ms.openlocfilehash: cb995e78e534048043886070536ef0dd0a45c057
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "73105101"
---
# <a name="ilasmexe-il-assembler"></a><span data-ttu-id="801da-102">Ilasm.exe (IL アセンブラー)</span><span class="sxs-lookup"><span data-stu-id="801da-102">Ilasm.exe (IL Assembler)</span></span>

<span data-ttu-id="801da-103">IL アセンブラーは、ポータブル実行可能 (PE) ファイルを IL (Intermediate Language) から生成します</span><span class="sxs-lookup"><span data-stu-id="801da-103">The IL Assembler generates a portable executable (PE) file from intermediate language (IL).</span></span> <span data-ttu-id="801da-104">(IL の詳細については、「[マネージド実行プロセス](../../standard/managed-execution-process.md)」を参照してください)。IL と必要なメタデータを含む実行可能ファイルを実行すると、IL が予測どおりに動作するかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="801da-104">(For more information on IL, see [Managed Execution Process](../../standard/managed-execution-process.md).) You can run the resulting executable, which contains IL and the required metadata, to determine whether the IL performs as expected.</span></span>

<span data-ttu-id="801da-105">このツールは、Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="801da-105">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="801da-106">このツールを実行するには、Visual Studio 用開発者コマンド プロンプト (または Windows 7 の Visual Studio コマンド プロンプト) を使用します。</span><span class="sxs-lookup"><span data-stu-id="801da-106">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="801da-107">詳細については、「[Visual Studio 用開発者コマンド プロンプト](developer-command-prompt-for-vs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="801da-107">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="801da-108">コマンド プロンプトに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="801da-108">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="801da-109">構文</span><span class="sxs-lookup"><span data-stu-id="801da-109">Syntax</span></span>

```console
ilasm [options] filename [[options]filename...]
```

## <a name="parameters"></a><span data-ttu-id="801da-110">パラメーター</span><span class="sxs-lookup"><span data-stu-id="801da-110">Parameters</span></span>

| <span data-ttu-id="801da-111">引数</span><span class="sxs-lookup"><span data-stu-id="801da-111">Argument</span></span> | <span data-ttu-id="801da-112">説明</span><span class="sxs-lookup"><span data-stu-id="801da-112">Description</span></span> |
| -------- | ----------- |
|`filename`|<span data-ttu-id="801da-113">.il ソース ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="801da-113">The name of the .il source file.</span></span> <span data-ttu-id="801da-114">このファイルは、メタデータ宣言ディレクティブとシンボリック IL 命令で構成されます。</span><span class="sxs-lookup"><span data-stu-id="801da-114">This file consists of metadata declaration directives and symbolic IL instructions.</span></span> <span data-ttu-id="801da-115">複数のソース ファイル引数を指定すると、*Ilasm.exe* で 1 つの PE ファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="801da-115">Multiple source file arguments can be supplied to produce a single PE file with *Ilasm.exe*.</span></span> <span data-ttu-id="801da-116">**注:** .il ソース ファイルのコードの最後の行に、後続の空白または行末文字のいずれかがあることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="801da-116">**Note:** Ensure that the last line of code in the .il source file has either trailing white space or an end-of-line character.</span></span>|

| <span data-ttu-id="801da-117">オプション</span><span class="sxs-lookup"><span data-stu-id="801da-117">Option</span></span> | <span data-ttu-id="801da-118">説明</span><span class="sxs-lookup"><span data-stu-id="801da-118">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="801da-119">**/32bitpreferred**</span><span class="sxs-lookup"><span data-stu-id="801da-119">**/32bitpreferred**</span></span>|<span data-ttu-id="801da-120">32 ビット優先イメージ (PE32) を作成します。</span><span class="sxs-lookup"><span data-stu-id="801da-120">Creates a 32-bit-preferred image (PE32).</span></span>|
|<span data-ttu-id="801da-121">**/alignment:** `integer`</span><span class="sxs-lookup"><span data-stu-id="801da-121">**/alignment:** `integer`</span></span>|<span data-ttu-id="801da-122">NT オプション ヘッダーの FileAlignment を `integer` で指定された値に設定します。</span><span class="sxs-lookup"><span data-stu-id="801da-122">Sets FileAlignment to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="801da-123">このオプションは、ファイル指定されている .alignment IL ディレクティブをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="801da-123">If the .alignment IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="801da-124">**/appcontainer**</span><span class="sxs-lookup"><span data-stu-id="801da-124">**/appcontainer**</span></span>|<span data-ttu-id="801da-125">出力として、Windows アプリ コンテナー内で実行する *.dll* ファイルまたは *.exe* ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="801da-125">Produces a *.dll* or *.exe* file that runs in the Windows app container, as output.</span></span>|
|<span data-ttu-id="801da-126">**/arm**</span><span class="sxs-lookup"><span data-stu-id="801da-126">**/arm**</span></span>|<span data-ttu-id="801da-127">ターゲット プロセッサとして Advanced RISC Machine (ARM) を指定します。</span><span class="sxs-lookup"><span data-stu-id="801da-127">Specifies the Advanced RISC Machine (ARM) as the target processor.</span></span><br /><br /> <span data-ttu-id="801da-128">イメージのビット数を指定しない場合、既定は **/32bitpreferred**です。</span><span class="sxs-lookup"><span data-stu-id="801da-128">If no image bitness is specified, the default is **/32bitpreferred**.</span></span>|
|<span data-ttu-id="801da-129">**/base:** `integer`</span><span class="sxs-lookup"><span data-stu-id="801da-129">**/base:** `integer`</span></span>|<span data-ttu-id="801da-130">NT オプション ヘッダーの ImageBase を `integer` で指定された値に設定します。</span><span class="sxs-lookup"><span data-stu-id="801da-130">Sets ImageBase to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="801da-131">このオプションは、ファイルに指定されている .imagebase IL ディレクティブをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="801da-131">If the .imagebase IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="801da-132">**/clock**</span><span class="sxs-lookup"><span data-stu-id="801da-132">**/clock**</span></span>|<span data-ttu-id="801da-133">指定した .il ソース ファイルのコンパイル時間を計測して報告します。</span><span class="sxs-lookup"><span data-stu-id="801da-133">Measures and reports the following compilation times in milliseconds for the specified .il source file:</span></span><br /><br /> <span data-ttu-id="801da-134">**Total Run**: 後に続く特定の操作の実行に要した合計時間。</span><span class="sxs-lookup"><span data-stu-id="801da-134">**Total Run**: The total time spent performing all the specific operations that follow.</span></span><br /><br /> <span data-ttu-id="801da-135">**Startup**: ファイルを読み込み、開く。</span><span class="sxs-lookup"><span data-stu-id="801da-135">**Startup**: Loading and opening the file.</span></span><br /><br /> <span data-ttu-id="801da-136">**Emitting MD**:メタデータの出力。</span><span class="sxs-lookup"><span data-stu-id="801da-136">**Emitting MD**: Emitting metadata.</span></span><br /><br /> <span data-ttu-id="801da-137">**Ref to Def Resolution**: ファイルの定義への参照の解決。</span><span class="sxs-lookup"><span data-stu-id="801da-137">**Ref to Def Resolution**: Resolving references to definitions in the file.</span></span><br /><br /> <span data-ttu-id="801da-138">**CEE File Generation**: メモリ内のファイル イメージの生成。</span><span class="sxs-lookup"><span data-stu-id="801da-138">**CEE File Generation**: Generating the file image in memory.</span></span><br /><br /> <span data-ttu-id="801da-139">**PE File Writing**: PE へのイメージの書き込み。</span><span class="sxs-lookup"><span data-stu-id="801da-139">**PE File Writing**: Writing the image to a PE file.</span></span>|
|<span data-ttu-id="801da-140">**/debug**[:**IMPL**&#124;**OPT**]</span><span class="sxs-lookup"><span data-stu-id="801da-140">**/debug**[:**IMPL**&#124;**OPT**]</span></span>|<span data-ttu-id="801da-141">デバッグ情報 (ローカル変数と引数名、および行番号) を組み込みます。</span><span class="sxs-lookup"><span data-stu-id="801da-141">Includes debug information (local variable and argument names, and line numbers).</span></span> <span data-ttu-id="801da-142">PDB ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="801da-142">Creates a PDB file.</span></span><br /><br /> <span data-ttu-id="801da-143">**/debug** に値を追加しなければ、JIT の最適化が無効になり、PDB ファイルのシーケンス ポイントが使用されます。</span><span class="sxs-lookup"><span data-stu-id="801da-143">**/debug** with no additional value disables JIT optimization and uses sequence points from the PDB file.</span></span><br /><br /> <span data-ttu-id="801da-144">**IMPL** を指定すると、JIT 最適化が無効になり、暗黙のシーケンス ポイントが使用されます。</span><span class="sxs-lookup"><span data-stu-id="801da-144">**IMPL** disables JIT optimization and uses implicit sequence points.</span></span><br /><br /> <span data-ttu-id="801da-145">**OPT** を指定すると、JIT 最適化が有効になり、暗黙のシーケンス ポイントが使用されます。</span><span class="sxs-lookup"><span data-stu-id="801da-145">**OPT** enables JIT optimization and uses implicit sequence points.</span></span>|
|<span data-ttu-id="801da-146">**/dll**</span><span class="sxs-lookup"><span data-stu-id="801da-146">**/dll**</span></span>|<span data-ttu-id="801da-147">出力として *.dll* ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="801da-147">Produces a *.dll* file as output.</span></span>|
|<span data-ttu-id="801da-148">**/enc:** `file`</span><span class="sxs-lookup"><span data-stu-id="801da-148">**/enc:** `file`</span></span>|<span data-ttu-id="801da-149">指定されたソース ファイルからエディット コンティニュ デルタを作成します。</span><span class="sxs-lookup"><span data-stu-id="801da-149">Creates Edit-and-Continue deltas from the specified source file.</span></span><br /><br /> <span data-ttu-id="801da-150">この引数は教育機関専用のため、商業目的の使用はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="801da-150">This argument is for academic use only and is not supported for commercial use.</span></span>|
|<span data-ttu-id="801da-151">**/exe**</span><span class="sxs-lookup"><span data-stu-id="801da-151">**/exe**</span></span>|<span data-ttu-id="801da-152">出力として実行可能ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="801da-152">Produces an executable file as output.</span></span> <span data-ttu-id="801da-153">既定値です。</span><span class="sxs-lookup"><span data-stu-id="801da-153">This is the default.</span></span>|
|<span data-ttu-id="801da-154">**/flags:** `integer`</span><span class="sxs-lookup"><span data-stu-id="801da-154">**/flags:** `integer`</span></span>|<span data-ttu-id="801da-155">共通言語ランタイム ヘッダーの ImageFlags を `integer` で指定された値に設定します。</span><span class="sxs-lookup"><span data-stu-id="801da-155">Sets ImageFlags to the value specified by `integer` in the common language runtime header.</span></span> <span data-ttu-id="801da-156">このオプションは、ファイルに指定されている .corflags IL ディレクティブをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="801da-156">If the .corflags IL directive is specified in the file, this option overrides it.</span></span> <span data-ttu-id="801da-157">有効な *integer*の値の一覧については、CorHdr.h で COMIMAGE_FLAGS を参照してください。</span><span class="sxs-lookup"><span data-stu-id="801da-157">See CorHdr.h, COMIMAGE_FLAGS for a list of valid values for *integer*.</span></span>|
|<span data-ttu-id="801da-158">**/fold**</span><span class="sxs-lookup"><span data-stu-id="801da-158">**/fold**</span></span>|<span data-ttu-id="801da-159">複数の同じメソッド本体を 1 つに折りたたみます。</span><span class="sxs-lookup"><span data-stu-id="801da-159">Folds identical method bodies into one.</span></span>|
|<span data-ttu-id="801da-160">/**highentropyva**</span><span class="sxs-lookup"><span data-stu-id="801da-160">/**highentropyva**</span></span>|<span data-ttu-id="801da-161">高エントロピ ASLR (Address Space Layout Randomization) をサポートする出力実行可能プログラムを作成します。</span><span class="sxs-lookup"><span data-stu-id="801da-161">Produces an output executable that supports high-entropy address space layout randomization (ASLR).</span></span> <span data-ttu-id="801da-162">(既定では **/appcontainer**)。</span><span class="sxs-lookup"><span data-stu-id="801da-162">(Default for **/appcontainer**.)</span></span>|
|<span data-ttu-id="801da-163">**/include:** `includePath`</span><span class="sxs-lookup"><span data-stu-id="801da-163">**/include:** `includePath`</span></span>|<span data-ttu-id="801da-164">`#include`によってインクルードされるファイルの検索パスを設定します。</span><span class="sxs-lookup"><span data-stu-id="801da-164">Sets a path to search for files included with `#include`.</span></span>|
|<span data-ttu-id="801da-165">**/itanium**</span><span class="sxs-lookup"><span data-stu-id="801da-165">**/itanium**</span></span>|<span data-ttu-id="801da-166">ターゲット プロセッサとして Intel Itanium を指定します。</span><span class="sxs-lookup"><span data-stu-id="801da-166">Specifies Intel Itanium as the target processor.</span></span><br /><br /> <span data-ttu-id="801da-167">イメージのビット数を指定しない場合、既定は **/pe64**です。</span><span class="sxs-lookup"><span data-stu-id="801da-167">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="801da-168">**/key:** `keyFile`</span><span class="sxs-lookup"><span data-stu-id="801da-168">**/key:** `keyFile`</span></span>|<span data-ttu-id="801da-169">`filename` に含まれる秘密キーを使って、厳密な署名を持つ `keyFile` をコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="801da-169">Compiles `filename` with a strong signature using the private key contained in `keyFile`.</span></span>|
|<span data-ttu-id="801da-170">**/key:**  @`keySource`</span><span class="sxs-lookup"><span data-stu-id="801da-170">**/key:** @`keySource`</span></span>|<span data-ttu-id="801da-171">`filename` で生成された秘密キーを使って、厳密な署名を持つ `keySource` をコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="801da-171">Compiles `filename` with a strong signature using the private key produced at `keySource`.</span></span>|
|<span data-ttu-id="801da-172">**/listing**</span><span class="sxs-lookup"><span data-stu-id="801da-172">**/listing**</span></span>|<span data-ttu-id="801da-173">標準出力にリスティング ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="801da-173">Produces a listing file on the standard output.</span></span> <span data-ttu-id="801da-174">このオプションを省略すると、リスティング ファイルは生成されません。</span><span class="sxs-lookup"><span data-stu-id="801da-174">If you omit this option, no listing file is produced.</span></span><br /><br /> <span data-ttu-id="801da-175">このパラメーターは、.NET Framework 2.0 以降ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="801da-175">This parameter is not supported in the .NET Framework 2.0 or later.</span></span>|
|<span data-ttu-id="801da-176">**/mdv:** `versionString`</span><span class="sxs-lookup"><span data-stu-id="801da-176">**/mdv:** `versionString`</span></span>|<span data-ttu-id="801da-177">メタデータのバージョン文字列を設定します。</span><span class="sxs-lookup"><span data-stu-id="801da-177">Sets the metadata version string.</span></span>|
|<span data-ttu-id="801da-178">**/msv:** `major`.`minor`</span><span class="sxs-lookup"><span data-stu-id="801da-178">**/msv:** `major`.`minor`</span></span>|<span data-ttu-id="801da-179">メタデータのストリーム バージョンを設定します。ここで、 `major` と `minor` は整数です。</span><span class="sxs-lookup"><span data-stu-id="801da-179">Sets the metadata stream version, where `major` and `minor` are integers.</span></span>|
|<span data-ttu-id="801da-180">**/noautoinherit**</span><span class="sxs-lookup"><span data-stu-id="801da-180">**/noautoinherit**</span></span>|<span data-ttu-id="801da-181">基底クラスが指定されていない場合、 <xref:System.Object> からの既定の継承を無効にします。</span><span class="sxs-lookup"><span data-stu-id="801da-181">Disables default inheritance from <xref:System.Object> when no base class is specified.</span></span>|
|<span data-ttu-id="801da-182">**/nocorstub**</span><span class="sxs-lookup"><span data-stu-id="801da-182">**/nocorstub**</span></span>|<span data-ttu-id="801da-183">CORExeMain スタブの生成を抑止します。</span><span class="sxs-lookup"><span data-stu-id="801da-183">Suppresses generation of the CORExeMain stub.</span></span>|
|<span data-ttu-id="801da-184">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="801da-184">**/nologo**</span></span>|<span data-ttu-id="801da-185">Microsoft 著作権情報を表示しません。</span><span class="sxs-lookup"><span data-stu-id="801da-185">Suppresses the Microsoft startup banner display.</span></span>|
|<span data-ttu-id="801da-186">**/output:** `file.ext`</span><span class="sxs-lookup"><span data-stu-id="801da-186">**/output:** `file.ext`</span></span>|<span data-ttu-id="801da-187">出力ファイルの名前と拡張子を指定します。</span><span class="sxs-lookup"><span data-stu-id="801da-187">Specifies the output file name and extension.</span></span> <span data-ttu-id="801da-188">既定では、出力ファイルの名前は最初のソース ファイルの名前と同じです。</span><span class="sxs-lookup"><span data-stu-id="801da-188">By default, the output file name is the same as the name of the first source file.</span></span> <span data-ttu-id="801da-189">既定の拡張子は *.exe* です。</span><span class="sxs-lookup"><span data-stu-id="801da-189">The default extension is *.exe*.</span></span> <span data-ttu-id="801da-190">**/dll** オプションを指定した場合の既定の拡張子は *.dll* です。</span><span class="sxs-lookup"><span data-stu-id="801da-190">If you specify the **/dll** option, the default extension is *.dll*.</span></span> <span data-ttu-id="801da-191">**注:** **/output** :myfile.dll と指定しても **/dll** オプションは設定されません。</span><span class="sxs-lookup"><span data-stu-id="801da-191">**Note:** Specifying **/output**:myfile.dll does not set the **/dll** option.</span></span> <span data-ttu-id="801da-192">**/dll**を指定しないと、*myfile.dll* という名前の実行可能ファイルになります。</span><span class="sxs-lookup"><span data-stu-id="801da-192">If you do not specify **/dll**, the result will be an executable file named *myfile.dll*.</span></span>|
|<span data-ttu-id="801da-193">**/optimize**</span><span class="sxs-lookup"><span data-stu-id="801da-193">**/optimize**</span></span>|<span data-ttu-id="801da-194">長いインストラクションを短く最適化します。</span><span class="sxs-lookup"><span data-stu-id="801da-194">Optimizes long instructions to short.</span></span> <span data-ttu-id="801da-195">たとえば `br` を `br.s`にします。</span><span class="sxs-lookup"><span data-stu-id="801da-195">For example, `br` to `br.s`.</span></span>|
|<span data-ttu-id="801da-196">**/pe64**</span><span class="sxs-lookup"><span data-stu-id="801da-196">**/pe64**</span></span>|<span data-ttu-id="801da-197">64 ビットのイメージ (PE32+) を作成します。</span><span class="sxs-lookup"><span data-stu-id="801da-197">Creates a 64-bit image (PE32+).</span></span><br /><br /> <span data-ttu-id="801da-198">ターゲット プロセッサを指定しない場合、既定は `/itanium`です。</span><span class="sxs-lookup"><span data-stu-id="801da-198">If no target processor is specified, the default is `/itanium`.</span></span>|
|<span data-ttu-id="801da-199">**/pdb**</span><span class="sxs-lookup"><span data-stu-id="801da-199">**/pdb**</span></span>|<span data-ttu-id="801da-200">デバッグ情報の追跡を有効にせずに PDB ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="801da-200">Creates a PDB file without enabling debug information tracking.</span></span>|
|<span data-ttu-id="801da-201">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="801da-201">**/quiet**</span></span>|<span data-ttu-id="801da-202">クワイエット モードを指定します。アセンブリの進行状況はレポートされません。</span><span class="sxs-lookup"><span data-stu-id="801da-202">Specifies quiet mode; does not report assembly progress.</span></span>|
|<span data-ttu-id="801da-203">**/resource:** `file.res`</span><span class="sxs-lookup"><span data-stu-id="801da-203">**/resource:** `file.res`</span></span>|<span data-ttu-id="801da-204">指定した \*.res 形式のリソース ファイルを生成される *.exe* ファイルまたは *.dll* ファイルに組み込みます。</span><span class="sxs-lookup"><span data-stu-id="801da-204">Includes the specified resource file in \*.res format in the resulting *.exe* or *.dll* file.</span></span> <span data-ttu-id="801da-205">**/resource** オプションで指定できる .res ファイルは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="801da-205">Only one .res file can be specified with the **/resource** option.</span></span>|
|<span data-ttu-id="801da-206">**/ssver:** `int`.`int`</span><span class="sxs-lookup"><span data-stu-id="801da-206">**/ssver:** `int`.`int`</span></span>|<span data-ttu-id="801da-207">NT オプション ヘッダーのサブシステム バージョン番号を設定します。</span><span class="sxs-lookup"><span data-stu-id="801da-207">Sets the subsystem version number in the NT optional header.</span></span> <span data-ttu-id="801da-208">**/appcontainer** および **/arm** では、最小バージョン番号は 6.02 です。</span><span class="sxs-lookup"><span data-stu-id="801da-208">For **/appcontainer** and **/arm** the minimum version number is 6.02.</span></span>|
|<span data-ttu-id="801da-209">**/stack:** `stackSize`</span><span class="sxs-lookup"><span data-stu-id="801da-209">**/stack:** `stackSize`</span></span>|<span data-ttu-id="801da-210">NT Optional ヘッダーの SizeOfStackReserve 値を `stackSize`に設定します。</span><span class="sxs-lookup"><span data-stu-id="801da-210">Sets the SizeOfStackReserve value in the NT Optional header to `stackSize`.</span></span>|
|<span data-ttu-id="801da-211">**/stripreloc**</span><span class="sxs-lookup"><span data-stu-id="801da-211">**/stripreloc**</span></span>|<span data-ttu-id="801da-212">ベースの再配置が不要であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="801da-212">Specifies that no base relocations are needed.</span></span>|
|<span data-ttu-id="801da-213">**/subsystem:** `integer`</span><span class="sxs-lookup"><span data-stu-id="801da-213">**/subsystem:** `integer`</span></span>|<span data-ttu-id="801da-214">NT オプション ヘッダーのサブシステムを `integer` で指定された値に設定します。</span><span class="sxs-lookup"><span data-stu-id="801da-214">Sets subsystem to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="801da-215">このコマンドは、ファイルに指定されている .subsystem IL ディレクティブをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="801da-215">If the .subsystem IL directive is specified in the file, this command overrides it.</span></span> <span data-ttu-id="801da-216">有効な `integer` の値の一覧については、winnt.h で IMAGE_SUBSYSTEM を参照してください。</span><span class="sxs-lookup"><span data-stu-id="801da-216">See winnt.h, IMAGE_SUBSYSTEM for a list of valid values for `integer`.</span></span>|
|<span data-ttu-id="801da-217">**/x64**</span><span class="sxs-lookup"><span data-stu-id="801da-217">**/x64**</span></span>|<span data-ttu-id="801da-218">ターゲット プロセッサとして 64 ビットの AMD プロセッサを指定します。</span><span class="sxs-lookup"><span data-stu-id="801da-218">Specifies a 64-bit AMD processor as the target processor.</span></span><br /><br /> <span data-ttu-id="801da-219">イメージのビット数を指定しない場合、既定は **/pe64**です。</span><span class="sxs-lookup"><span data-stu-id="801da-219">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="801da-220">**/?**</span><span class="sxs-lookup"><span data-stu-id="801da-220">**/?**</span></span>|<span data-ttu-id="801da-221">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="801da-221">Displays command syntax and options for the tool.</span></span>|

> [!NOTE]
> <span data-ttu-id="801da-222">*Ilasm.exe* に関するすべてのオプションでは大文字と小文字が区別されず、先頭の 3 文字で認識されます。</span><span class="sxs-lookup"><span data-stu-id="801da-222">All options for *Ilasm.exe* are case-insensitive and recognized by the first three letters.</span></span> <span data-ttu-id="801da-223">たとえば、 **/lis** は **/listing** と等価であり、 **/res:** myresfile.res は **/resource:** myresfile.res と等価です。引数を伴うオプションの場合は、オプションと引数の間に区切り記号としてコロン (:) または等号 (=) を挿入できます。</span><span class="sxs-lookup"><span data-stu-id="801da-223">For example, **/lis** is equivalent to **/listing** and **/res**:myresfile.res is equivalent to **/resource**:myresfile.res. Options that specify arguments accept either a colon (:) or an equal sign (=) as the separator between the option and the argument.</span></span> <span data-ttu-id="801da-224">たとえば、 **/output**:*file.ext* は **/output**=*file.ext* と等価です。</span><span class="sxs-lookup"><span data-stu-id="801da-224">For example, **/output**:*file.ext* is equivalent to **/output**=*file.ext*.</span></span>

## <a name="remarks"></a><span data-ttu-id="801da-225">Remarks</span><span class="sxs-lookup"><span data-stu-id="801da-225">Remarks</span></span>

<span data-ttu-id="801da-226">IL アセンブラーは、IL ジェネレーターを設計および実装するツールの販売元を支援します。</span><span class="sxs-lookup"><span data-stu-id="801da-226">The IL Assembler helps tool vendors design and implement IL generators.</span></span> <span data-ttu-id="801da-227">ツールとコンパイラの開発者は、*Ilasm.exe* を使用することで、PE ファイル形式での IL の出力にかかわることなく、IL とメタデータの生成に集中できます。</span><span class="sxs-lookup"><span data-stu-id="801da-227">Using *Ilasm.exe*, tool and compiler developers can concentrate on IL and metadata generation without being concerned with emitting IL in the PE file format.</span></span>

<span data-ttu-id="801da-228">C# および Visual Basic など、ランタイムを対象とした他のコンパイラと同様に、*Ilasm.exe* も中間オブジェクト ファイルを生成しません。このため、PE ファイルを形成するためのリンク ステージが必要ありません。</span><span class="sxs-lookup"><span data-stu-id="801da-228">Similar to other compilers that target the runtime, such as C# and Visual Basic, *Ilasm.exe* does not produce intermediate object files and does not require a linking stage to form a PE file.</span></span>

<span data-ttu-id="801da-229">IL アセンブラーは、すべての既存メタデータ、およびランタイムを対象としたプログラミング言語の IL 機能を表現できます。</span><span class="sxs-lookup"><span data-stu-id="801da-229">The IL Assembler can express all the existing metadata and IL features of the programming languages that target the runtime.</span></span> <span data-ttu-id="801da-230">このため、このようなプログラミング言語で記述されたマネージド コードを IL アセンブラーで適切に表現し、*Ilasm.exe* でコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="801da-230">This allows managed code written in any of these programming languages to be adequately expressed in IL Assembler and compiled with *Ilasm.exe*.</span></span>

> [!NOTE]
> <span data-ttu-id="801da-231">.il ソース ファイルのコードの最後の行に、後続の空白または行末文字がない場合、コンパイルに失敗することがあります。</span><span class="sxs-lookup"><span data-stu-id="801da-231">Compilation might fail if the last line of code in the .il source file does not have either trailing white space or an end-of-line character.</span></span>

<span data-ttu-id="801da-232">*Ilasm.exe* と、その対をなすツール [*Ildasm.exe*](ildasm-exe-il-disassembler.md) を併用できます。</span><span class="sxs-lookup"><span data-stu-id="801da-232">You can use *Ilasm.exe* in conjunction with its companion tool, [*Ildasm.exe*](ildasm-exe-il-disassembler.md).</span></span> <span data-ttu-id="801da-233">*Ildasm.exe* は、IL コードを含む PE ファイルを使用して、*Ilasm.exe* への入力として適したテキスト ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="801da-233">*Ildasm.exe* takes a PE file that contains IL code and creates a text file suitable as input to *Ilasm.exe*.</span></span> <span data-ttu-id="801da-234">これは、必ずしもランタイム メタデータ属性のすべてをサポートしないプログラミング言語で記述されたコードをコンパイルするときなどに便利です。</span><span class="sxs-lookup"><span data-stu-id="801da-234">This is useful, for example, when compiling code in a programming language that does not support all the runtime metadata attributes.</span></span> <span data-ttu-id="801da-235">コードをコンパイルし、その出力を *Ildasm.exe* で実行した後、生成された IL テキスト ファイルを手作業で編集して足りない属性を追加できます。</span><span class="sxs-lookup"><span data-stu-id="801da-235">After compiling the code and running the output through *Ildasm.exe*, the resulting IL text file can be hand-edited to add the missing attributes.</span></span> <span data-ttu-id="801da-236">このテキスト ファイルを *Ilasm.exe* で実行すると、最終的な実行可能ファイルを生成できます。</span><span class="sxs-lookup"><span data-stu-id="801da-236">You can then run this text file through the *Ilasm.exe* to produce a final executable file.</span></span>

<span data-ttu-id="801da-237">この方法を使用して、異なるコンパイラによって生成された複数の PE ファイルから 1 つの PE ファイルを生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="801da-237">You can also use this technique to produce a single PE file from several PE files originally generated by different compilers.</span></span>

> [!NOTE]
> <span data-ttu-id="801da-238">現時点では、埋め込みのネイティブ コード (たとえば Visual C++ で生成された PE ファイル) を含む PE ファイルについては、この手法を使用できません。</span><span class="sxs-lookup"><span data-stu-id="801da-238">Currently, you cannot use this technique with PE files that contain embedded native code (for example, PE files produced by Visual C++).</span></span>

<span data-ttu-id="801da-239">この *Ildasm.exe* と *Ilasm.exe* の組み合わせをできる限り正確に使用するため、アセンブラーは、既定では、IL ソース内に記述されている可能性がある (または別のコンパイラによって出力される可能性がある) 長いエンコーディングを短いエンコーディングに置換しません。</span><span class="sxs-lookup"><span data-stu-id="801da-239">To make this combined use of *Ildasm.exe* and *Ilasm.exe* as accurate as possible, by default the assembler does not substitute short encodings for long ones you might have written in your IL sources (or that might be emitted by another compiler).</span></span> <span data-ttu-id="801da-240">可能な場合は、常に **/optimize** オプションを使用して、短いエンコーディングを置換します。</span><span class="sxs-lookup"><span data-stu-id="801da-240">Use the **/optimize** option to substitute short encodings wherever possible.</span></span>

> [!NOTE]
> <span data-ttu-id="801da-241">*Ildasm.exe* はディスク上のファイルについてだけ動作します。</span><span class="sxs-lookup"><span data-stu-id="801da-241">*Ildasm.exe* only operates on files on disk.</span></span> <span data-ttu-id="801da-242">グローバル アセンブリ キャッシュ内にインストールされたファイルについては動作しません。</span><span class="sxs-lookup"><span data-stu-id="801da-242">It does not operate on files installed in the global assembly cache.</span></span>

<span data-ttu-id="801da-243">IL の文法の詳細については、Windows SDK の asmparse.grammar ファイルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="801da-243">For more information about the grammar of IL, see the asmparse.grammar file in the Windows SDK.</span></span>

## <a name="version-information"></a><span data-ttu-id="801da-244">バージョン情報</span><span class="sxs-lookup"><span data-stu-id="801da-244">Version Information</span></span>

<span data-ttu-id="801da-245">.NET Framework 4.5 以降では、次に類似するコードを使用することで、インターフェイス実装にカスタム属性を追加できます。</span><span class="sxs-lookup"><span data-stu-id="801da-245">Starting with the .NET Framework 4.5, you can attach a custom attribute to an interface implementation by using code similar to the following:</span></span>

```il
.class interface public abstract auto ansi IMyInterface
{
  .method public hidebysig newslot abstract virtual
    instance int32 method1() cil managed
  {
  } // end of method IMyInterface::method1
} // end of class IMyInterface
.class public auto ansi beforefieldinit MyClass
  extends [mscorlib]System.Object
  implements IMyInterface
  {
    .interfaceimpl type IMyInterface
    .custom instance void
      [mscorlib]System.Diagnostics.DebuggerNonUserCodeAttribute::.ctor() = ( 01 00 00 00 )
      …
```

<span data-ttu-id="801da-246">.NET Framework 4.5 以降では、次のコードに示すように、未処理のバイナリ表現を使用することで、任意のマーシャリング BLOB (バイナリ ラージ オブジェクト) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="801da-246">Starting with the .NET Framework 4.5, you can specify an arbitrary marshal BLOB (binary large object) by using its raw binary representation, as shown in the following code:</span></span>

```il
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

<span data-ttu-id="801da-247">IL の文法の詳細については、Windows SDK の asmparse.grammar ファイルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="801da-247">For more information about the grammar of IL, see the asmparse.grammar file in the Windows SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="801da-248">使用例</span><span class="sxs-lookup"><span data-stu-id="801da-248">Examples</span></span>

<span data-ttu-id="801da-249">IL ファイル *myTestFile.il* をアセンブルして実行可能ファイル *myTestFile.exe* を生成するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="801da-249">The following command assembles the IL file *myTestFile.il* and produces the executable *myTestFile.exe*.</span></span>

```console
ilasm myTestFile
```

<span data-ttu-id="801da-250">IL ファイル *myTestFile.il* をアセンブルして *.dll* ファイル *myTestFile.dll* を生成するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="801da-250">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll
```

<span data-ttu-id="801da-251">IL ファイル *myTestFile.il* をアセンブルして *.dll* ファイル *myNewTestFile.dll* を生成するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="801da-251">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myNewTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

<span data-ttu-id="801da-252">コンソールに "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="801da-252">The following code example shows an extremely simple application that displays "Hello World!"</span></span> <span data-ttu-id="801da-253">記述するだけです。</span><span class="sxs-lookup"><span data-stu-id="801da-253">to the console.</span></span> <span data-ttu-id="801da-254">このコードのコンパイル後に [*Ildasm.exe*](ildasm-exe-il-disassembler.md) ツールを使用して、IL ファイルを生成できます。</span><span class="sxs-lookup"><span data-stu-id="801da-254">You can compile this code and then use the [*Ildasm.exe*](ildasm-exe-il-disassembler.md) tool to generate an IL file.</span></span>

```csharp
using System;

public class Hello
{
    public static void Main(String[] args)
    {
        Console.WriteLine("Hello World!");
    }
}
```

<span data-ttu-id="801da-255">次の IL コードの例は、前の C# のコード例に対応しています。</span><span class="sxs-lookup"><span data-stu-id="801da-255">The following IL code example corresponds to the previous C# code example.</span></span> <span data-ttu-id="801da-256">IL アセンブラー ツールを使うと、このコードをアセンブリにコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="801da-256">You can compile this code into an assembly using the IL Assembler tool.</span></span> <span data-ttu-id="801da-257">IL コードと C# コードの例は、どちらもコンソールに "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="801da-257">Both IL and C# code examples display "Hello World!"</span></span> <span data-ttu-id="801da-258">記述するだけです。</span><span class="sxs-lookup"><span data-stu-id="801da-258">to the console.</span></span>

```il
// Metadata version: v2.0.50215
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 2:0:0:0
}
.assembly sample
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module sample.exe
// MVID: {A224F460-A049-4A03-9E71-80A36DBBBCD3}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x02F20000

// =============== CLASS MEMBERS DECLARATION ===================

.class public auto ansi beforefieldinit Hello
       extends [mscorlib]System.Object
{
  .method public hidebysig static void  Main(string[] args) cil managed
  {
    .entrypoint
    // Code size       13 (0xd)
    .maxstack  8
    IL_0000:  nop
    IL_0001:  ldstr      "Hello World!"
    IL_0006:  call       void [mscorlib]System.Console::WriteLine(string)
    IL_000b:  nop
    IL_000c:  ret
  } // end of method Hello::Main

  .method public hidebysig specialname rtspecialname
          instance void  .ctor() cil managed
  {
    // Code size       7 (0x7)
    .maxstack  8
    IL_0000:  ldarg.0
    IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
    IL_0006:  ret
  } // end of method Hello::.ctor

} // end of class Hello
```

## <a name="see-also"></a><span data-ttu-id="801da-259">関連項目</span><span class="sxs-lookup"><span data-stu-id="801da-259">See also</span></span>

- [<span data-ttu-id="801da-260">ツール</span><span class="sxs-lookup"><span data-stu-id="801da-260">Tools</span></span>](index.md)
- [<span data-ttu-id="801da-261">*Ildasm.exe* (IL 逆アセンブラー)</span><span class="sxs-lookup"><span data-stu-id="801da-261">*Ildasm.exe* (IL Disassembler)</span></span>](ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="801da-262">マネージド実行プロセス</span><span class="sxs-lookup"><span data-stu-id="801da-262">Managed Execution Process</span></span>](../../standard/managed-execution-process.md)
- [<span data-ttu-id="801da-263">Visual Studio 用開発者コマンド プロンプト</span><span class="sxs-lookup"><span data-stu-id="801da-263">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
