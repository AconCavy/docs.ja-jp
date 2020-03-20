---
title: Peverify.exe (PEVerify ツール)
ms.date: 03/30/2017
helpviewer_keywords:
- portable executable files, PEVerify
- verifying MSIL and metadata
- PEVerify tool
- type safety requirements
- MSIL
- PEverify.exe
- PE files, PEVerify
ms.assetid: f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa
ms.openlocfilehash: 9d5f8c80937c36e975d42d6efb0a83295cb28be9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "73104978"
---
# <a name="peverifyexe-peverify-tool"></a><span data-ttu-id="d1fb2-102">Peverify.exe (PEVerify ツール)</span><span class="sxs-lookup"><span data-stu-id="d1fb2-102">Peverify.exe (PEVerify Tool)</span></span>
<span data-ttu-id="d1fb2-103">PEVerify ツールは、Microsoft Intermediate Language (MSIL) を生成する開発者 (コンパイラの作成者、スクリプト エンジンの開発者など) が、生成する MSIL コードと関連メタデータがタイプ セーフ要件を満たしているかどうかを確認する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-103">The PEVerify tool helps developers who generate Microsoft intermediate language (MSIL) (such as compiler writers, script engine developers, and so on) to determine whether their MSIL code and associated metadata meet type safety requirements.</span></span> <span data-ttu-id="d1fb2-104">一部のコンパイラでは、特定の言語構成を使用しなかった場合にだけ、検査可能でタイプ セーフなコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-104">Some compilers generate verifiably type-safe code only if you avoid using certain language constructs.</span></span> <span data-ttu-id="d1fb2-105">このようなコンパイラを使用している場合、生成したコードがタイプ セーフかどうかを確認する必要があると思う開発者もいるはずです。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-105">If, as a developer, you are using such a compiler, you may want to verify that you have not compromised the type safety of your code.</span></span> <span data-ttu-id="d1fb2-106">そのような場合は、ファイルに対して PEVerify ツールを実行し、MSIL とメタデータを検査できます。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-106">In this situation, you can run the PEVerify tool on your files to check the MSIL and metadata.</span></span>  
  
 <span data-ttu-id="d1fb2-107">このツールは、Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="d1fb2-108">このツールを実行するには、Visual Studio 用開発者コマンド プロンプト (または Windows 7 の Visual Studio コマンド プロンプト) を使用します。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-108">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="d1fb2-109">詳細については、「[Visual Studio 用開発者コマンド プロンプト](developer-command-prompt-for-vs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-109">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="d1fb2-110">コマンド プロンプトに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-110">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1fb2-111">構文</span><span class="sxs-lookup"><span data-stu-id="d1fb2-111">Syntax</span></span>  
  
```console  
peverify filename [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1fb2-112">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d1fb2-112">Parameters</span></span>  
  
|<span data-ttu-id="d1fb2-113">引数</span><span class="sxs-lookup"><span data-stu-id="d1fb2-113">Argument</span></span>|<span data-ttu-id="d1fb2-114">説明</span><span class="sxs-lookup"><span data-stu-id="d1fb2-114">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="d1fb2-115">*ファイル名*</span><span class="sxs-lookup"><span data-stu-id="d1fb2-115">*filename*</span></span>|<span data-ttu-id="d1fb2-116">MSIL とメタデータを検査する対象のポータブル実行可能 (PE) ファイル。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-116">The portable executable (PE) file for which to check the MSIL and metadata.</span></span>|  
  
|<span data-ttu-id="d1fb2-117">オプション</span><span class="sxs-lookup"><span data-stu-id="d1fb2-117">Option</span></span>|<span data-ttu-id="d1fb2-118">説明</span><span class="sxs-lookup"><span data-stu-id="d1fb2-118">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="d1fb2-119">**/break=** *maxErrorCount*</span><span class="sxs-lookup"><span data-stu-id="d1fb2-119">**/break=** *maxErrorCount*</span></span>|<span data-ttu-id="d1fb2-120">*maxErrorCount* エラーが発生した後で検査を中止します。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-120">Aborts verification after *maxErrorCount* errors.</span></span><br /><br /> <span data-ttu-id="d1fb2-121">このパラメーターは、.NET Framework Version 2.0 以降ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-121">This parameter is not supported in .NET Framework version 2.0 or later.</span></span>|  
|<span data-ttu-id="d1fb2-122">**/clock**</span><span class="sxs-lookup"><span data-stu-id="d1fb2-122">**/clock**</span></span>|<span data-ttu-id="d1fb2-123">次の検査時間をミリ秒単位で計測して報告します。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-123">Measures and reports the following verification times in milliseconds:</span></span><br /><br /> <span data-ttu-id="d1fb2-124">**MD Val. cycle**</span><span class="sxs-lookup"><span data-stu-id="d1fb2-124">**MD Val. cycle**</span></span><br /> <span data-ttu-id="d1fb2-125">メタデータ検証サイクル</span><span class="sxs-lookup"><span data-stu-id="d1fb2-125">Metadata validation cycle</span></span><br /><br /> <span data-ttu-id="d1fb2-126">**MD Val. pure**</span><span class="sxs-lookup"><span data-stu-id="d1fb2-126">**MD Val. pure**</span></span><br /> <span data-ttu-id="d1fb2-127">メタデータ検証のみ</span><span class="sxs-lookup"><span data-stu-id="d1fb2-127">Metadata validation pure</span></span><br /><br /> <span data-ttu-id="d1fb2-128">**IL Ver. cycle**</span><span class="sxs-lookup"><span data-stu-id="d1fb2-128">**IL Ver. cycle**</span></span><br /> <span data-ttu-id="d1fb2-129">Microsoft Intermediate Language (MSIL) 検証サイクル</span><span class="sxs-lookup"><span data-stu-id="d1fb2-129">Microsoft intermediate language (MSIL) verification cycle</span></span><br /><br /> <span data-ttu-id="d1fb2-130">**IL Ver pure**</span><span class="sxs-lookup"><span data-stu-id="d1fb2-130">**IL Ver pure**</span></span><br /> <span data-ttu-id="d1fb2-131">MSIL 検証のみ</span><span class="sxs-lookup"><span data-stu-id="d1fb2-131">MSIL verification pure</span></span><br /><br /> <span data-ttu-id="d1fb2-132">**MD Val. cycle** 時間および **IL Ver. cycle** 時間には、必要なスタートアップ手順およびシャットダウン手順を実行するために必要な時間が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-132">The **MD Val. cycle** and **IL Ver. cycle** times include the time required to perform necessary startup and shutdown procedures.</span></span> <span data-ttu-id="d1fb2-133">**MD Val. pure** 時間および **IL Ver pure** 時間は、検査または検証だけを行うために要する時間を反映します。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-133">The **MD Val. pure** and **IL Ver pure** times reflect the time required to perform the validation or verification only.</span></span>|  
|<span data-ttu-id="d1fb2-134">**/help**</span><span class="sxs-lookup"><span data-stu-id="d1fb2-134">**/help**</span></span>|<span data-ttu-id="d1fb2-135">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="d1fb2-136">**/hresult**</span><span class="sxs-lookup"><span data-stu-id="d1fb2-136">**/hresult**</span></span>|<span data-ttu-id="d1fb2-137">エラーコードを 16 進形式で表示します。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-137">Displays error codes in hexadecimal format.</span></span>|  
|<span data-ttu-id="d1fb2-138">**/ignore=** *hex.code* [, *hex.code*]</span><span class="sxs-lookup"><span data-stu-id="d1fb2-138">**/ignore=** *hex.code* [, *hex.code*]</span></span>|<span data-ttu-id="d1fb2-139">指定したエラー コードを無視します。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-139">Ignores the specified error codes.</span></span>|  
|<span data-ttu-id="d1fb2-140">**/ignore=@** *responseFile*</span><span class="sxs-lookup"><span data-stu-id="d1fb2-140">**/ignore=@** *responseFile*</span></span>|<span data-ttu-id="d1fb2-141">指定した応答ファイル内に一覧表示されているエラー コードを無視します。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-141">Ignores the error codes listed in the specified response file.</span></span>|  
|<span data-ttu-id="d1fb2-142">**/il**</span><span class="sxs-lookup"><span data-stu-id="d1fb2-142">**/il**</span></span>|<span data-ttu-id="d1fb2-143">*filename* で指定したアセンブリに実装されているメソッドに対して、MSIL がタイプ セーフかどうかを検査します。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-143">Performs MSIL type safety verification checks for methods implemented in the assembly specified by *filename*.</span></span> <span data-ttu-id="d1fb2-144">**/quiet** オプションを指定した場合を除き、検出された問題ごとに詳細な説明が返されます。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-144">The tool returns detailed descriptions for each problem found unless you specify the **/quiet** option.</span></span>|  
|<span data-ttu-id="d1fb2-145">**/md**</span><span class="sxs-lookup"><span data-stu-id="d1fb2-145">**/md**</span></span>|<span data-ttu-id="d1fb2-146">*filename* で指定したアセンブリに対して、メタデータを検証します。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-146">Performs metadata validation checks on the assembly specified by *filename*.</span></span> <span data-ttu-id="d1fb2-147">この場合、ファイル内のすべてのメタデータ構造が検証され、検出された問題がすべて報告されます。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-147">This walks the full metadata structure within the file and reports all validation problems encountered.</span></span>|  
|<span data-ttu-id="d1fb2-148">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="d1fb2-148">**/nologo**</span></span>|<span data-ttu-id="d1fb2-149">製品バージョンと著作権情報を表示しません。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-149">Suppresses the display of product version and copyright information.</span></span>|  
|<span data-ttu-id="d1fb2-150">**/nosymbols**</span><span class="sxs-lookup"><span data-stu-id="d1fb2-150">**/nosymbols**</span></span>|<span data-ttu-id="d1fb2-151">.NET Framework Version 2.0 で、後方互換性のために行番号を表示しません。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-151">In the .NET Framework version 2.0, suppresses line numbers for backward compatibility.</span></span>|  
|<span data-ttu-id="d1fb2-152">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="d1fb2-152">**/quiet**</span></span>|<span data-ttu-id="d1fb2-153">クワイエット モードを指定します。このモードでは、検査により検出された問題の報告が簡略化されます。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-153">Specifies quiet mode; suppresses output of the verification problem reports.</span></span> <span data-ttu-id="d1fb2-154">ファイルがタイプ セーフかどうかは報告されますが、タイプ セーフでない場合に、その問題に関する情報は報告されません。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-154">Peverify.exe still reports whether the file is type safe, but does not report information on problems preventing type safety verification.</span></span>|  
|`/transparent`|<span data-ttu-id="d1fb2-155">透過的なメソッドのみを検証します。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-155">Verify only the transparent methods.</span></span>|  
|<span data-ttu-id="d1fb2-156">**/unique**</span><span class="sxs-lookup"><span data-stu-id="d1fb2-156">**/unique**</span></span>|<span data-ttu-id="d1fb2-157">繰り返し発生するエラー コードを無視します。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-157">Ignores repeating error codes.</span></span>|  
|<span data-ttu-id="d1fb2-158">**/verbose**</span><span class="sxs-lookup"><span data-stu-id="d1fb2-158">**/verbose**</span></span>|<span data-ttu-id="d1fb2-159">.NET Framework Version 2.0 で、MSIL 検証メッセージに追加情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-159">In the .NET Framework version 2.0, displays additional information in MSIL verification messages.</span></span>|  
|<span data-ttu-id="d1fb2-160">**/?**</span><span class="sxs-lookup"><span data-stu-id="d1fb2-160">**/?**</span></span>|<span data-ttu-id="d1fb2-161">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-161">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1fb2-162">Remarks</span><span class="sxs-lookup"><span data-stu-id="d1fb2-162">Remarks</span></span>  
 <span data-ttu-id="d1fb2-163">共通言語ランタイムは、セキュリティ機構や分離機構の実施を簡単にするために、アプリケーション コードがタイプ セーフに実行されることに依存しています。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-163">The common language runtime relies on the type-safe execution of application code to help enforce security and isolation mechanisms.</span></span> <span data-ttu-id="d1fb2-164">通常、[検査可能でタイプ セーフ](../../standard/security/key-security-concepts.md#type-safety-and-security)なコード以外のコードは実行できません。しかし、信頼できるが検査を実行できないコードを実行可能にするセキュリティ ポリシーを設定することはできます。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-164">Normally, code that is not [verifiably type safe](../../standard/security/key-security-concepts.md#type-safety-and-security) cannot run, although you can set security policy to allow the execution of trusted but unverifiable code.</span></span>  
  
 <span data-ttu-id="d1fb2-165">**/md** と **/il** のいずれのオプションも指定しない場合は、両方の種類の検査が実行されます。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-165">If neither the **/md** nor **/il** options are specified, Peverify.exe performs both types of checks.</span></span> <span data-ttu-id="d1fb2-166">まず、 **/md** オプションによる検査が実行されます。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-166">Peverify.exe performs **/md** checks first.</span></span> <span data-ttu-id="d1fb2-167">エラーが検出されない場合は、 **/il** オプションによる検査が実行されます。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-167">If there are no errors, **/il** checks are made.</span></span> <span data-ttu-id="d1fb2-168">**/md** と **/il** の両方のオプションを指定した場合は、メタデータの検査でエラーが検出された場合でも、 **/il** オプションによる検査が実行されます。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-168">If you specify both **/md** and **/il**, **/il** checks are made even if there are errors in the metadata.</span></span> <span data-ttu-id="d1fb2-169">つまり、メタデータの検査でエラーが検出されないときは、**peverify** *filename* は **peverify** *filename* **/md** **/il** と同等です。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-169">Thus, if there are no metadata errors, **peverify** *filename* is equivalent to **peverify** *filename* **/md** **/il**.</span></span>  
  
 <span data-ttu-id="d1fb2-170">Peverify.exe は、データ フローの分析と、メタデータの有効性に関する多数の規則のリストに基づいて、MSIL に対する包括的な検査を実行します。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-170">Peverify.exe performs comprehensive MSIL verification checks based on dataflow analysis plus a list of several hundred rules on valid metadata.</span></span> <span data-ttu-id="d1fb2-171">Peverify.exe によって実行される検査の詳細については、Windows SDK の Tools Developers Guide フォルダー内にある "Metadata Validation Specification" (メタデータ検証仕様) と "MSIL Instruction Set Specification" (MSIL 命令セット仕様) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-171">For detailed information on the checks Peverify.exe performs, see the "Metadata Validation Specification" and the "MSIL Instruction Set Specification" in the Tools Developers Guide folder in the Windows SDK.</span></span>  
  
 <span data-ttu-id="d1fb2-172">.NET Framework Version 2.0 以降では、`byref`、`dup`、`ldsflda`、`ldflda`、`ldelema`、および `call` の各 MSIL 命令を使用して指定する検証可能な `unbox` 戻り値をサポートします。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-172">Note that the .NET Framework version 2.0 or later supports verifiable `byref` returns specified using the following MSIL instructions: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` and `unbox`.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="d1fb2-173">使用例</span><span class="sxs-lookup"><span data-stu-id="d1fb2-173">Examples</span></span>  
 <span data-ttu-id="d1fb2-174">アセンブリ `myAssembly.exe` に実装されているメソッドに対して、メタデータの有効性および MSIL がタイプ セーフかどうかについて検査するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-174">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span>  
  
```console  
peverify myAssembly.exe /md /il  
```  
  
 <span data-ttu-id="d1fb2-175">上記の要求が正常に終了した場合は、次のメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-175">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```output
All classes and methods in myAssembly.exe Verified  
```  
  
 <span data-ttu-id="d1fb2-176">アセンブリ `myAssembly.exe` に実装されているメソッドに対して、メタデータの有効性および MSIL がタイプ セーフかどうかについて検査するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-176">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="d1fb2-177">このツールは、これらの検査に要する時間を表示します。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-177">The tool displays the time required to perform these checks.</span></span>  
  
```console  
peverify myAssembly.exe /md /il /clock  
```  
  
 <span data-ttu-id="d1fb2-178">上記の要求が正常に終了した場合は、次のメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-178">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```output
All classes and methods in myAssembly.exe Verified  
Timing: Total run     320 msec  
        MD Val.cycle  40 msec  
        MD Val.pure   10 msec  
        IL Ver.cycle  270 msec  
        IL Ver.pure   230 msec  
```  
  
 <span data-ttu-id="d1fb2-179">アセンブリ `myAssembly.exe` に実装されているメソッドに対して、メタデータの有効性および MSIL がタイプ セーフかどうかについて検査するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-179">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="d1fb2-180">しかし、Peverify.exe は、最大エラー カウントである 100 に達すると、停止します。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-180">Peverify.exe stops, however, when it reaches the maximum error count of 100.</span></span> <span data-ttu-id="d1fb2-181">このツールは、指定されたエラー コードも無視します。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-181">The tool also ignores the specified error codes.</span></span>  
  
```console  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 <span data-ttu-id="d1fb2-182">上記の例と結果は同じですが、無視するエラー コードを応答ファイル `ignoreErrors.rsp` に指定するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-182">The following command produces the same result as the above previous example, but specifies the error codes to ignore in the response file `ignoreErrors.rsp`.</span></span>  
  
```console  
peverify myAssembly.exe /break=100 /ignore@ignoreErrors.rsp  
```  
  
 <span data-ttu-id="d1fb2-183">この応答ファイルには、エラー コードの一覧をコンマで区切って指定できます。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-183">The response file can contain a comma-separated list of error codes.</span></span>  
  
```text
0x12345678, 0xABCD1234  
```  
  
 <span data-ttu-id="d1fb2-184">また、エラー コードを 1 行に 1 つという形式で指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="d1fb2-184">Alternatively, the response file can be formatted with one error code per line.</span></span>  
  
```text
0x12345678  
0xABCD1234  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1fb2-185">関連項目</span><span class="sxs-lookup"><span data-stu-id="d1fb2-185">See also</span></span>

- [<span data-ttu-id="d1fb2-186">ツール</span><span class="sxs-lookup"><span data-stu-id="d1fb2-186">Tools</span></span>](index.md)
- [<span data-ttu-id="d1fb2-187">検証可能なタイプ セーフ コードの作成</span><span class="sxs-lookup"><span data-stu-id="d1fb2-187">Writing Verifiably Type-Safe Code</span></span>](../misc/code-access-security-basics.md#typesafe_code)
- [<span data-ttu-id="d1fb2-188">タイプ セーフとセキュリティ</span><span class="sxs-lookup"><span data-stu-id="d1fb2-188">Type Safety and Security</span></span>](../../standard/security/key-security-concepts.md#type-safety-and-security)
- [<span data-ttu-id="d1fb2-189">Visual Studio 用開発者コマンド プロンプト</span><span class="sxs-lookup"><span data-stu-id="d1fb2-189">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
