---
title: 'アセンブリを作成できません : <error message>'
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 5776755a57fbc2b0086b1c9b6cfbb2f2b7eb03fa
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197275"
---
# <a name="unable-to-emit-assembly-error-message"></a><span data-ttu-id="3e503-102">アセンブリを作成できません: \<error message></span><span class="sxs-lookup"><span data-stu-id="3e503-102">Unable to emit assembly: \<error message></span></span>

<span data-ttu-id="3e503-103">Visual Basic コンパイラは、マニフェストを伴うアセンブリを生成するためにアセンブリ リンカー (*Al.exe*、Alink とも呼ばれます) を呼び出し、アセンブリを作成する出力段階でリンカーからエラーが報告されます。</span><span class="sxs-lookup"><span data-stu-id="3e503-103">The Visual Basic compiler calls the Assembly Linker (*Al.exe*, also known as Alink) to generate an assembly with a manifest, and the linker reports an error in the emission stage of creating the assembly.</span></span>

<span data-ttu-id="3e503-104">**エラー ID:** BC30145</span><span class="sxs-lookup"><span data-stu-id="3e503-104">**Error ID:** BC30145</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="3e503-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="3e503-105">To correct this error</span></span>

1. <span data-ttu-id="3e503-106">引用符で囲まれたエラー メッセージを調べ、トピック「[Al.exe](../../../framework/tools/al-exe-assembly-linker.md)」でより詳細な説明とアドバイスを参照します。</span><span class="sxs-lookup"><span data-stu-id="3e503-106">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) for further explanation and advice.</span></span>

2. <span data-ttu-id="3e503-107">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md) または [Sn.exe (厳密名ツール)](../../../framework/tools/sn-exe-strong-name-tool.md) を使用して、手動でアセンブリに署名してみてください。</span><span class="sxs-lookup"><span data-stu-id="3e503-107">Try signing the assembly manually, using either the [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) or the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>

3. <span data-ttu-id="3e503-108">エラーが続く場合は、状況に関する情報を収集し、マイクロソフト プロダクト サポート サービスに通知してください。</span><span class="sxs-lookup"><span data-stu-id="3e503-108">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="3e503-109">アセンブリを手動で署名するには</span><span class="sxs-lookup"><span data-stu-id="3e503-109">To sign the assembly manually</span></span>

1. <span data-ttu-id="3e503-110">[Sn.exe (厳密名ツール)](../../../framework/tools/sn-exe-strong-name-tool.md) を使用して、公開キーと秘密キーのペア ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="3e503-110">Use the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) to create a public/private key pair file.</span></span>

   <span data-ttu-id="3e503-111">このファイルは *.snk* の拡張子を持ちます。</span><span class="sxs-lookup"><span data-stu-id="3e503-111">This file has an *.snk* extension.</span></span>

2. <span data-ttu-id="3e503-112">エラーが発生している COM 参照をプロジェクトから削除します。</span><span class="sxs-lookup"><span data-stu-id="3e503-112">Delete the COM reference that is generating the error from your project.</span></span>

3. <span data-ttu-id="3e503-113">[Visual Studio の開発者コマンド プロンプト](../../../framework/tools/developer-command-prompt-for-vs.md)を開きます。</span><span class="sxs-lookup"><span data-stu-id="3e503-113">Open the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).</span></span>

   <span data-ttu-id="3e503-114">Windows 10 で、タスク バーの検索ボックスに「**開発者コマンド プロンプト**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="3e503-114">In Windows 10, enter **Developer command prompt** into the search box on the task bar.</span></span> <span data-ttu-id="3e503-115">次に、結果の一覧から **VS 2017 用開発者コマンド プロンプト**を選択します。</span><span class="sxs-lookup"><span data-stu-id="3e503-115">Then, select **Developer Command Prompt for VS 2017** from the results list.</span></span>

4. <span data-ttu-id="3e503-116">アセンブリ ラッパーを格納するディレクトリに、ディレクトリを変更します。</span><span class="sxs-lookup"><span data-stu-id="3e503-116">Change the directory to the directory where you want to place your assembly wrapper.</span></span>

5. <span data-ttu-id="3e503-117">次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="3e503-117">Enter the following command:</span></span>

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   <span data-ttu-id="3e503-118">入力できる実際のコマンドの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3e503-118">An example of the actual command you might enter is:</span></span>

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > <span data-ttu-id="3e503-119">パスやファイルに空白が含まれている場合には、二重引用符を使用します。</span><span class="sxs-lookup"><span data-stu-id="3e503-119">Use double quotation marks if a path or file contains spaces.</span></span>

6. <span data-ttu-id="3e503-120">Visual Studio で、作成したファイルに .NET アセンブリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="3e503-120">In Visual Studio, add a .NET Assembly reference to the file you just created.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e503-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e503-121">See also</span></span>

- [<span data-ttu-id="3e503-122">Al.exe</span><span class="sxs-lookup"><span data-stu-id="3e503-122">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="3e503-123">Sn.exe (厳密名ツール)</span><span class="sxs-lookup"><span data-stu-id="3e503-123">Sn.exe (Strong Name Tool)</span></span>](../../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="3e503-124">方法: 公開キーと秘密キーのキー ペアを作成する</span><span class="sxs-lookup"><span data-stu-id="3e503-124">How to: Create a Public-Private Key Pair</span></span>](../../../standard/assembly/create-public-private-key-pair.md)
- [<span data-ttu-id="3e503-125">ご意見</span><span class="sxs-lookup"><span data-stu-id="3e503-125">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
