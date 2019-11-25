---
title: ファイルとディレクトリの操作
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], reading text
- reading files [Visual Basic], text
- I/O [Visual Basic], walkthroughs
- text, writing to files
- text, reading from files
- reading text from files [Visual Basic], walkthroughs
- Visual Basic code, file access
- files [Visual Basic], writing text
- I/O [Visual Basic], writing text to files
- file access, walkthroughs
- writing to files [Visual Basic], walkthroughs
- I/O [Visual Basic], reading text from files
ms.assetid: cae77565-9f78-4e46-8e42-eb2f9f8e1ffd
ms.openlocfilehash: 83dc6ce0d29c1c368c36b51fc84ecad34d72e01f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333804"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a><span data-ttu-id="3e0f3-102">チュートリアル: Visual Basic によるファイルとディレクトリの操作</span><span class="sxs-lookup"><span data-stu-id="3e0f3-102">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>

<span data-ttu-id="3e0f3-103">このチュートリアルでは、Visual Basic でのファイル I/O の基礎について概説します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-103">This walkthrough provides an introduction to the fundamentals of file I/O in Visual Basic.</span></span> <span data-ttu-id="3e0f3-104">具体的には、ディレクトリ内のテキスト ファイルをリストして調査する小さなアプリケーションを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-104">It describes how to create a small application that lists and examines text files in a directory.</span></span> <span data-ttu-id="3e0f3-105">このアプリケーションは、選択された各テキスト ファイルについて、ファイルの属性とコンテンツの最初の行を取得します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-105">For each selected text file, the application provides file attributes and the first line of content.</span></span> <span data-ttu-id="3e0f3-106">ログ ファイルに情報を書き込むオプションもあります。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-106">There is an option to write information to a log file.</span></span>  
  
 <span data-ttu-id="3e0f3-107">このチュートリアルでは、Visual Basic で利用可能な、`My.Computer.FileSystem Object` のメンバーを使用します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-107">This walkthrough uses members of the `My.Computer.FileSystem Object`, which are available in Visual Basic.</span></span> <span data-ttu-id="3e0f3-108">詳細については、「<xref:Microsoft.VisualBasic.FileIO.FileSystem>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-108">See <xref:Microsoft.VisualBasic.FileIO.FileSystem> for more information.</span></span> <span data-ttu-id="3e0f3-109">チュートリアルの最後では、<xref:System.IO> 名前空間のクラスを使用する同等の例を示します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-109">At the end of the walkthrough, an equivalent example is provided that uses classes from the <xref:System.IO> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a><span data-ttu-id="3e0f3-110">プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="3e0f3-110">To create the project</span></span>  
  
1. <span data-ttu-id="3e0f3-111">**[ファイル]** メニューの **[新しいプロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-111">On the **File** menu, click **New Project**.</span></span>  
  
     <span data-ttu-id="3e0f3-112">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-112">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="3e0f3-113">**[インストールされたテンプレート]** ペインで、 **[Visual Basic]** を展開し、 **[Windows]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-113">In the **Installed Templates** pane, expand **Visual Basic**, and then click **Windows**.</span></span> <span data-ttu-id="3e0f3-114">中央の **[テンプレート]** ペインで、 **[Windows フォーム アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-114">In the **Templates** pane in the middle, click **Windows Forms Application**.</span></span>  
  
3. <span data-ttu-id="3e0f3-115">**[名前]** ボックスに「`FileExplorer`」と入力してプロジェクト名を設定し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-115">In the **Name** box, type `FileExplorer` to set the project name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="3e0f3-116">Visual Studio の**ソリューション エクスプローラー**にプロジェクトが追加され、Windows フォーム デザイナーが開きます。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-116">Visual Studio adds the project to **Solution Explorer**, and the Windows Forms Designer opens.</span></span>  
  
4. <span data-ttu-id="3e0f3-117">次の表にあるコントロールをフォームに追加し、それらのプロパティに対応する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-117">Add the controls in the following table to the form, and set the corresponding values for their properties.</span></span>  
  
    |<span data-ttu-id="3e0f3-118">Control</span><span class="sxs-lookup"><span data-stu-id="3e0f3-118">Control</span></span>|<span data-ttu-id="3e0f3-119">プロパティ</span><span class="sxs-lookup"><span data-stu-id="3e0f3-119">Property</span></span>|<span data-ttu-id="3e0f3-120">値</span><span class="sxs-lookup"><span data-stu-id="3e0f3-120">Value</span></span>|  
    |-------------|--------------|-----------|  
    |<span data-ttu-id="3e0f3-121">**ListBox**</span><span class="sxs-lookup"><span data-stu-id="3e0f3-121">**ListBox**</span></span>|<span data-ttu-id="3e0f3-122">**Name**</span><span class="sxs-lookup"><span data-stu-id="3e0f3-122">**Name**</span></span>|`filesListBox`|  
    |<span data-ttu-id="3e0f3-123">**Button**</span><span class="sxs-lookup"><span data-stu-id="3e0f3-123">**Button**</span></span>|<span data-ttu-id="3e0f3-124">**Name**</span><span class="sxs-lookup"><span data-stu-id="3e0f3-124">**Name**</span></span><br /><br /> <span data-ttu-id="3e0f3-125">**[テキスト]**</span><span class="sxs-lookup"><span data-stu-id="3e0f3-125">**Text**</span></span>|`browseButton`<br /><br /> <span data-ttu-id="3e0f3-126">**参照**</span><span class="sxs-lookup"><span data-stu-id="3e0f3-126">**Browse**</span></span>|  
    |<span data-ttu-id="3e0f3-127">**Button**</span><span class="sxs-lookup"><span data-stu-id="3e0f3-127">**Button**</span></span>|<span data-ttu-id="3e0f3-128">**Name**</span><span class="sxs-lookup"><span data-stu-id="3e0f3-128">**Name**</span></span><br /><br /> <span data-ttu-id="3e0f3-129">**[テキスト]**</span><span class="sxs-lookup"><span data-stu-id="3e0f3-129">**Text**</span></span>|`examineButton`<br /><br /> <span data-ttu-id="3e0f3-130">**調査**</span><span class="sxs-lookup"><span data-stu-id="3e0f3-130">**Examine**</span></span>|  
    |<span data-ttu-id="3e0f3-131">**CheckBox**</span><span class="sxs-lookup"><span data-stu-id="3e0f3-131">**CheckBox**</span></span>|<span data-ttu-id="3e0f3-132">**Name**</span><span class="sxs-lookup"><span data-stu-id="3e0f3-132">**Name**</span></span><br /><br /> <span data-ttu-id="3e0f3-133">**[テキスト]**</span><span class="sxs-lookup"><span data-stu-id="3e0f3-133">**Text**</span></span>|`saveCheckBox`<br /><br /> <span data-ttu-id="3e0f3-134">**結果の保存**</span><span class="sxs-lookup"><span data-stu-id="3e0f3-134">**Save Results**</span></span>|  
    |<span data-ttu-id="3e0f3-135">**FolderBrowserDialog**</span><span class="sxs-lookup"><span data-stu-id="3e0f3-135">**FolderBrowserDialog**</span></span>|<span data-ttu-id="3e0f3-136">**Name**</span><span class="sxs-lookup"><span data-stu-id="3e0f3-136">**Name**</span></span>|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a><span data-ttu-id="3e0f3-137">フォルダーを選択し、フォルダー内のファイルをリストするには</span><span class="sxs-lookup"><span data-stu-id="3e0f3-137">To select a folder, and list files in a folder</span></span>  
  
1. <span data-ttu-id="3e0f3-138">フォーム上のコントロールをダブルクリックして、`browseButton` の `Click` イベント ハンドラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-138">Create a `Click` event handler for `browseButton` by double-clicking the control on the form.</span></span> <span data-ttu-id="3e0f3-139">コード エディターが開きます。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-139">The Code Editor opens.</span></span>  
  
2. <span data-ttu-id="3e0f3-140">`Click` イベント ハンドラーに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-140">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     <span data-ttu-id="3e0f3-141">`FolderBrowserDialog1.ShowDialog` 呼び出しにより、 **[フォルダーの参照]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-141">The `FolderBrowserDialog1.ShowDialog` call opens the **Browse For Folder** dialog box.</span></span> <span data-ttu-id="3e0f3-142">ユーザーが **[OK]** をクリックすると、次の手順で追加する `ListFiles` メソッドに <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> プロパティが引数として渡されます。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-142">After the user clicks **OK**, the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property is sent as an argument to the `ListFiles` method, which is added in the next step.</span></span>  
  
3. <span data-ttu-id="3e0f3-143">次の `ListFiles` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-143">Add the following `ListFiles` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     <span data-ttu-id="3e0f3-144">このコードでは、まず最初に **ListBox** をクリアします。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-144">This code first clears the **ListBox**.</span></span>  
  
     <span data-ttu-id="3e0f3-145">次に、<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> メソッドによって、ディレクトリ内の各ファイルを表す文字列のコレクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-145">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> method then retrieves a collection of strings, one for each file in the directory.</span></span> <span data-ttu-id="3e0f3-146">`GetFiles` メソッドは、検索パターンの引数を受け取り、特定のパターンに一致するファイルを取得します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-146">The `GetFiles` method accepts a search pattern argument to retrieve files that match a particular pattern.</span></span> <span data-ttu-id="3e0f3-147">この例では、拡張子 .txt が付いているファイルのみが返されます。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-147">In this example, only files that have the extension .txt are returned.</span></span>  
  
     <span data-ttu-id="3e0f3-148">その後、`GetFiles` メソッドによって返された文字列が、**ListBox** に追加されます。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-148">The strings that are returned by the `GetFiles` method are then added to the **ListBox**.</span></span>  
  
4. <span data-ttu-id="3e0f3-149">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-149">Run the application.</span></span> <span data-ttu-id="3e0f3-150">**[参照]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-150">Click the **Browse** button.</span></span> <span data-ttu-id="3e0f3-151">**[フォルダーの参照]** ダイアログ ボックスで、.txt ファイルが含まれているフォルダーを参照し、そのフォルダーを選択して **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-151">In the **Browse For Folder** dialog box, browse to a folder that contains .txt files, and then select the folder and click **OK**.</span></span>  
  
     <span data-ttu-id="3e0f3-152">`ListBox` に、選択したフォルダー内のファイルが追加されます。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-152">The `ListBox` contains a list of .txt files in the selected folder.</span></span>  
  
5. <span data-ttu-id="3e0f3-153">アプリケーションの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-153">Stop running the application.</span></span>  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a><span data-ttu-id="3e0f3-154">テキスト ファイルからファイルの属性とコンテンツを取得するには</span><span class="sxs-lookup"><span data-stu-id="3e0f3-154">To obtain attributes of a file, and content from a text file</span></span>  
  
1. <span data-ttu-id="3e0f3-155">フォーム上のコントロールをダブルクリックして、`examineButton` の `Click` イベント ハンドラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-155">Create a `Click` event handler for `examineButton` by double-clicking the control on the form.</span></span>  
  
2. <span data-ttu-id="3e0f3-156">`Click` イベント ハンドラーに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-156">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     <span data-ttu-id="3e0f3-157">このコードは、`ListBox` で選択された項目を検証します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-157">The code verifies that an item is selected in the `ListBox`.</span></span> <span data-ttu-id="3e0f3-158">その後、`ListBox` からファイル パスのエントリを取得します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-158">It then obtains the file path entry from the `ListBox`.</span></span> <span data-ttu-id="3e0f3-159"><xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> メソッドを使用して、ファイルがまだ存在するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-159">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> method is used to check whether the file still exists.</span></span>  
  
     <span data-ttu-id="3e0f3-160">ファイル パスは引数として `GetTextForOutput` メソッドに送られます (このメソッドは次の手順で追加します)。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-160">The file path is sent as an argument to the `GetTextForOutput` method, which is added in the next step.</span></span> <span data-ttu-id="3e0f3-161">このメソッドは、ファイル情報を含んだ文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-161">This method returns a string that contains file information.</span></span> <span data-ttu-id="3e0f3-162">ファイル情報は、**MessageBox** に表示されます。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-162">The file information appears in a **MessageBox**.</span></span>  
  
3. <span data-ttu-id="3e0f3-163">次の `GetTextForOutput` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-163">Add the following `GetTextForOutput` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     <span data-ttu-id="3e0f3-164">このコードでは、<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> メソッドを使用してファイル パラメーターを取得します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-164">The code uses the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method to obtain file parameters.</span></span> <span data-ttu-id="3e0f3-165">ファイル パラメーターは、<xref:System.Text.StringBuilder> に追加されます。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-165">The file parameters are added to a <xref:System.Text.StringBuilder>.</span></span>  
  
     <span data-ttu-id="3e0f3-166"><xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> メソッドは、ファイルの内容を <xref:System.IO.StreamReader> に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-166">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> method reads the file contents into a <xref:System.IO.StreamReader>.</span></span> <span data-ttu-id="3e0f3-167">コンテンツの最初の行が `StreamReader` から取得され、`StringBuilder` に追加されます。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-167">The first line of the contents is obtained from the `StreamReader` and is added to the `StringBuilder`.</span></span>  
  
4. <span data-ttu-id="3e0f3-168">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-168">Run the application.</span></span> <span data-ttu-id="3e0f3-169">**[参照]** をクリックし、.txt ファイルが含まれているフォルダーを参照します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-169">Click **Browse**, and browse to a folder that contains .txt files.</span></span> <span data-ttu-id="3e0f3-170">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-170">Click **OK**.</span></span>  
  
     <span data-ttu-id="3e0f3-171">`ListBox` でファイルを選択し、 **[調査]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-171">Select a file in the `ListBox`, and then click **Examine**.</span></span> <span data-ttu-id="3e0f3-172">`MessageBox` にファイル情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-172">A `MessageBox` shows the file information.</span></span>  
  
5. <span data-ttu-id="3e0f3-173">アプリケーションの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-173">Stop running the application.</span></span>  
  
### <a name="to-add-a-log-entry"></a><span data-ttu-id="3e0f3-174">ログ エントリを追加するには</span><span class="sxs-lookup"><span data-stu-id="3e0f3-174">To add a log entry</span></span>  
  
1. <span data-ttu-id="3e0f3-175">`examineButton_Click` イベント ハンドラーの末尾に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-175">Add the following code to the end of the `examineButton_Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     <span data-ttu-id="3e0f3-176">このコードは、ログ ファイルのパスを設定して、選択したファイルと同じディレクトリにログ ファイルを配置します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-176">The code sets the log file path to put the log file in the same directory as that of the selected file.</span></span> <span data-ttu-id="3e0f3-177">ログ エントリのテキストは現在の日付と時刻に設定され、その後にファイル情報が記録されます。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-177">The text of the log entry is set to the current date and time followed by the file information.</span></span>  
  
     <span data-ttu-id="3e0f3-178">`append` 引数を `True` に設定した <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> メソッドを使用して、ログ エントリを作成します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-178">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method, with the `append` argument set to `True`, is used to create the log entry.</span></span>  
  
2. <span data-ttu-id="3e0f3-179">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-179">Run the application.</span></span> <span data-ttu-id="3e0f3-180">テキスト ファイルを参照し、`ListBox` でファイルを選択して、 **[結果の保存]** チェック ボックスをオンにした後、 **[調査]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-180">Browse to a text file, select it in the `ListBox`, select the **Save Results** check box, and then click **Examine**.</span></span> <span data-ttu-id="3e0f3-181">ログ エントリが `log.txt` ファイルに書き込まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-181">Verify that the log entry is written to the `log.txt` file.</span></span>  
  
3. <span data-ttu-id="3e0f3-182">アプリケーションの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-182">Stop running the application.</span></span>  
  
### <a name="to-use-the-current-directory"></a><span data-ttu-id="3e0f3-183">現在のディレクトリを使用するには</span><span class="sxs-lookup"><span data-stu-id="3e0f3-183">To use the current directory</span></span>  
  
1. <span data-ttu-id="3e0f3-184">フォームをダブルクリックして、`Form1_Load` のイベント ハンドラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-184">Create an event handler for `Form1_Load` by double-clicking the form.</span></span>  
  
2. <span data-ttu-id="3e0f3-185">イベント ハンドラーに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-185">Add the following code to the event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     <span data-ttu-id="3e0f3-186">このコードは、フォルダー ブラウザーの既定のディレクトリを現在のディレクトリに設定します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-186">This code sets the default directory of the folder browser to the current directory.</span></span>  
  
3. <span data-ttu-id="3e0f3-187">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-187">Run the application.</span></span> <span data-ttu-id="3e0f3-188">**[参照]** を最初にクリックすると、 **[フォルダーの参照]** ダイアログ ボックスが開き、現在のディレクトリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-188">When you click **Browse** the first time, the **Browse For Folder** dialog box opens to the current directory.</span></span>  
  
4. <span data-ttu-id="3e0f3-189">アプリケーションの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-189">Stop running the application.</span></span>  
  
### <a name="to-selectively-enable-controls"></a><span data-ttu-id="3e0f3-190">コントロールを選択的に有効化するには</span><span class="sxs-lookup"><span data-stu-id="3e0f3-190">To selectively enable controls</span></span>  
  
1. <span data-ttu-id="3e0f3-191">次の `SetEnabled` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-191">Add the following `SetEnabled` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     <span data-ttu-id="3e0f3-192">`SetEnabled` メソッドは、`ListBox` で項目が選択されているかどうかに応じて、コントロールを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-192">The `SetEnabled` method enables or disables controls depending on whether an item is selected in the `ListBox`.</span></span>  
  
2. <span data-ttu-id="3e0f3-193">フォーム上の `ListBox` コントロールをダブルクリックして、`filesListBox` の `SelectedIndexChanged` イベント ハンドラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-193">Create a `SelectedIndexChanged` event handler for `filesListBox` by double-clicking the `ListBox` control on the form.</span></span>  
  
3. <span data-ttu-id="3e0f3-194">新しい `filesListBox_SelectedIndexChanged` イベント ハンドラーで、`SetEnabled` に対する呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-194">Add a call to `SetEnabled` in the new `filesListBox_SelectedIndexChanged` event handler.</span></span>  
  
4. <span data-ttu-id="3e0f3-195">`browseButton_Click` イベント ハンドラーの末尾に、`SetEnabled` に対する呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-195">Add a call to `SetEnabled` at the end of the `browseButton_Click` event handler.</span></span>  
  
5. <span data-ttu-id="3e0f3-196">`Form1_Load` イベント ハンドラーの末尾に、`SetEnabled` に対する呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-196">Add a call to `SetEnabled` at the end of the `Form1_Load` event handler.</span></span>  
  
6. <span data-ttu-id="3e0f3-197">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-197">Run the application.</span></span> <span data-ttu-id="3e0f3-198">`ListBox` で項目が選択されていない場合は、 **[結果の保存**] チェック ボックスと **[調査]** ボタンが無効になります。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-198">The **Save Results** check box and the **Examine** button are disabled if an item is not selected in the `ListBox`.</span></span>  
  
## <a name="full-example-using-mycomputerfilesystem"></a><span data-ttu-id="3e0f3-199">My.Computer.FileSystem を使用した完全な例</span><span class="sxs-lookup"><span data-stu-id="3e0f3-199">Full example using My.Computer.FileSystem</span></span>  

 <span data-ttu-id="3e0f3-200">完全な例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-200">Following is the complete example.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a><span data-ttu-id="3e0f3-201">System.IO を使用した完全な例</span><span class="sxs-lookup"><span data-stu-id="3e0f3-201">Full example using System.IO</span></span>  

 <span data-ttu-id="3e0f3-202">次に示す同等の例では、`My.Computer.FileSystem` オブジェクトではなく、<xref:System.IO> 名前空間のクラスを使用しています。</span><span class="sxs-lookup"><span data-stu-id="3e0f3-202">The following equivalent example uses classes from the <xref:System.IO> namespace instead of using `My.Computer.FileSystem` objects.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a><span data-ttu-id="3e0f3-203">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e0f3-203">See also</span></span>

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [<span data-ttu-id="3e0f3-204">チュートリアル: .NET Framework のメソッドによるファイル操作</span><span class="sxs-lookup"><span data-stu-id="3e0f3-204">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)
