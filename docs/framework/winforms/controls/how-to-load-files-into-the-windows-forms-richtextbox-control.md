---
title: RichTextBox コントロールへのファイルの読み込み
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], displaying files
- examples [Windows Forms], text boxes
- .rtf files [Windows Forms], opening in RichTextBox control
- RTF files [Windows Forms], opening in RichTextBox control
- text files [Windows Forms], displaying in RichTextBox control
- .rtf files [Windows Forms], displaying in RichTextBox control
- RichTextBox control [Windows Forms], opening files
- RTF files [Windows Forms], displaying in RichTextBox control
ms.assetid: c03451be-f285-4428-a71a-c41e002cc919
ms.openlocfilehash: c31e004ea4cd0821b5f18f0ab0fe2708e6ac4b59
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736286"
---
# <a name="how-to-load-files-into-the-windows-forms-richtextbox-control"></a><span data-ttu-id="f9a92-102">方法 : Windows フォームの RichTextBox コントロールにファイルを読み込む</span><span class="sxs-lookup"><span data-stu-id="f9a92-102">How to: Load Files into the Windows Forms RichTextBox Control</span></span>

<span data-ttu-id="f9a92-103">Windows フォームの <xref:System.Windows.Forms.RichTextBox> コントロールには、プレーン テキスト、Unicode のプレーン テキスト、リッチ テキスト形式 (RTF) ファイルを表示できます。</span><span class="sxs-lookup"><span data-stu-id="f9a92-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display a plain-text, Unicode plain-text, or Rich-Text-Format (RTF) file.</span></span> <span data-ttu-id="f9a92-104">それには、 <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f9a92-104">To do so, call the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method.</span></span> <span data-ttu-id="f9a92-105">また、 <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> メソッドを使用してストリームからデータを読み込むこともできます。</span><span class="sxs-lookup"><span data-stu-id="f9a92-105">You can also use the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method to load data from a stream.</span></span> <span data-ttu-id="f9a92-106">詳細については、「 <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9a92-106">For more information, see <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span></span>

### <a name="to-load-a-file-into-the-richtextbox-control"></a><span data-ttu-id="f9a92-107">RichTextBox コントロールにファイルを読み込むには</span><span class="sxs-lookup"><span data-stu-id="f9a92-107">To load a file into the RichTextBox control</span></span>

1. <span data-ttu-id="f9a92-108"><xref:System.Windows.Forms.OpenFileDialog> コンポーネントを使用して、開くファイルのパスを決定します。</span><span class="sxs-lookup"><span data-stu-id="f9a92-108">Determine the path of the file to be opened using the <xref:System.Windows.Forms.OpenFileDialog> component.</span></span> <span data-ttu-id="f9a92-109">概要については、「 [OpenFileDialog コンポーネントの概要](openfiledialog-component-overview-windows-forms.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9a92-109">For an overview, see [OpenFileDialog Component Overview](openfiledialog-component-overview-windows-forms.md).</span></span>

2. <span data-ttu-id="f9a92-110">読み込むファイルと、必要に応じてファイルの種類を指定して、 <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> コントロールの <xref:System.Windows.Forms.RichTextBox> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f9a92-110">Call the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method of the <xref:System.Windows.Forms.RichTextBox> control, specifying the file to load and optionally a file type.</span></span> <span data-ttu-id="f9a92-111">次の例では、読み込むファイルは <xref:System.Windows.Forms.OpenFileDialog> コンポーネントの <xref:System.Windows.Forms.FileDialog.FileName%2A> プロパティから取得されます。</span><span class="sxs-lookup"><span data-stu-id="f9a92-111">In the example below, the file to load is taken from the <xref:System.Windows.Forms.OpenFileDialog> component's <xref:System.Windows.Forms.FileDialog.FileName%2A> property.</span></span> <span data-ttu-id="f9a92-112">引数にファイル名だけを指定してメソッドを呼び出すと、ファイルの種類は RTF と見なされます。</span><span class="sxs-lookup"><span data-stu-id="f9a92-112">If you call the method with a file name as its only argument, the file type will be assumed to be RTF.</span></span> <span data-ttu-id="f9a92-113">別の種類のファイルを指定するには、2 番目の引数として <xref:System.Windows.Forms.RichTextBoxStreamType> 列挙型の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="f9a92-113">To specify another file type, call the method with a value of the <xref:System.Windows.Forms.RichTextBoxStreamType> enumeration as its second argument.</span></span>

    <span data-ttu-id="f9a92-114">次の例では、ボタンがクリックされたときに <xref:System.Windows.Forms.OpenFileDialog> コンポーネントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f9a92-114">In the example below, the <xref:System.Windows.Forms.OpenFileDialog> component is shown when a button is clicked.</span></span> <span data-ttu-id="f9a92-115">次に、選択されたファイルが開き、 <xref:System.Windows.Forms.RichTextBox> コントロールに表示されます。</span><span class="sxs-lookup"><span data-stu-id="f9a92-115">The file selected is then opened and displayed in the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="f9a92-116">この例ではフォームにボタン`btnOpenFile`があることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="f9a92-116">This example assumes a form has a button,`btnOpenFile`.</span></span>

    ```vb
    Private Sub btnOpenFile_Click(ByVal sender As System.Object, _
       ByVal e As System.EventArgs) Handles btnOpenFile.Click
         If OpenFileDialog1.ShowDialog() = DialogResult.OK Then
           RichTextBox1.LoadFile(OpenFileDialog1.FileName, _
              RichTextBoxStreamType.RichText)
          End If
    End Sub
    ```

    ```csharp
    private void btnOpenFile_Click(object sender, System.EventArgs e)
    {
       if(openFileDialog1.ShowDialog() == DialogResult.OK)
       {
         richTextBox1.LoadFile(openFileDialog1.FileName, RichTextBoxStreamType.RichText);
       }
    }
    ```

    ```cpp
    private:
       void btnOpenFile_Click(System::Object ^  sender,
          System::EventArgs ^  e)
       {
          if(openFileDialog1->ShowDialog() == DialogResult::OK)
          {
             richTextBox1->LoadFile(openFileDialog1->FileName,
                RichTextBoxStreamType::RichText);
          }
       }
    ```

    <span data-ttu-id="f9a92-117">(ビジュアルC#、ビジュアルC++)フォームのコンストラクターに次のコードを配置して、イベントハンドラーを登録します。</span><span class="sxs-lookup"><span data-stu-id="f9a92-117">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>

    ```csharp
    this.btnOpenFile.Click += new System.EventHandler(this. btnOpenFile_Click);
    ```

    ```cpp
    this->btnOpenFile->Click += gcnew
       System::EventHandler(this, &Form1::btnOpenFile_Click);
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="f9a92-118">このプロセスを実行するには、アセンブリに対して <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> クラスで特権レベルが許可されていることが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="f9a92-118">To run this process, your assembly may require a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="f9a92-119">部分的に信頼されたコンテキストで実行している場合、プロセスは、特権がないため例外をスローする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f9a92-119">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="f9a92-120">詳細については、「 [Code Access Security Basics](../../misc/code-access-security-basics.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9a92-120">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f9a92-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9a92-121">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="f9a92-122">RichTextBox コントロール</span><span class="sxs-lookup"><span data-stu-id="f9a92-122">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="f9a92-123">Windows フォームで使用するコントロール</span><span class="sxs-lookup"><span data-stu-id="f9a92-123">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
