---
title: '方法: コンマ区切りのテキスト ファイルを読み取る'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- reading text files [Visual Basic], comma-delimited
- text files [Visual Basic], reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
ms.openlocfilehash: ba62a0226a1a83326cbc7ab393d135763a7c7cb2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411643"
---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a><span data-ttu-id="9c304-102">方法: Visual Basic でコンマ区切りのテキスト ファイルを読み取る</span><span class="sxs-lookup"><span data-stu-id="9c304-102">How to: read from comma-delimited text files in Visual Basic</span></span>

<span data-ttu-id="9c304-103">`TextFieldParser` オブジェクトには、構造化されたテキスト ファイル (ログなど) を簡単にかつ効率的に解析する方法が備わっています。</span><span class="sxs-lookup"><span data-stu-id="9c304-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="9c304-104">区切り形式のファイルか、固定幅フィールドのテキストを使用したファイルかは、`TextFieldType` プロパティで定義します。</span><span class="sxs-lookup"><span data-stu-id="9c304-104">The `TextFieldType` property defines whether it is a delimited file or one with fixed-width fields of text.</span></span>  
  
### <a name="to-parse-a-comma-delimited-text-file"></a><span data-ttu-id="9c304-105">コンマ区切りテキスト ファイルを解析するには</span><span class="sxs-lookup"><span data-stu-id="9c304-105">To parse a comma delimited text file</span></span>  
  
1. <span data-ttu-id="9c304-106">新しい `TextFieldParser` を作成します。</span><span class="sxs-lookup"><span data-stu-id="9c304-106">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="9c304-107">次のコードは、`MyReader` という名前の `TextFieldParser` を作成し、`test.txt` ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="9c304-107">The following code creates the `TextFieldParser` named `MyReader` and opens the file `test.txt`.</span></span>  
  
     [!code-vb[VbFileIORead#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#15)]  
  
2. <span data-ttu-id="9c304-108">`TextField` 型と区切り記号を定義します。</span><span class="sxs-lookup"><span data-stu-id="9c304-108">Define the `TextField` type and delimiter.</span></span> <span data-ttu-id="9c304-109">次のコードは、`TextFieldType` プロパティを `Delimited`、区切り記号を "," として定義します。</span><span class="sxs-lookup"><span data-stu-id="9c304-109">The following code defines the `TextFieldType` property as `Delimited` and the delimiter as ",".</span></span>  
  
     [!code-vb[VbFileIORead#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#16)]  
  
3. <span data-ttu-id="9c304-110">ファイル内のフィールドをループします。</span><span class="sxs-lookup"><span data-stu-id="9c304-110">Loop through the fields in the file.</span></span> <span data-ttu-id="9c304-111">破損している行が見つかった場合は、エラーを報告して解析を続行します。</span><span class="sxs-lookup"><span data-stu-id="9c304-111">If any lines are corrupt, report an error and continue parsing.</span></span> <span data-ttu-id="9c304-112">次のコードは、ファイル内をループし、各フィールド順次表示して、不正にフォーマットされているフィールドをレポートします。</span><span class="sxs-lookup"><span data-stu-id="9c304-112">The following code loops through the file, displaying each field in turn and reporting any fields that are formatted incorrectly.</span></span>  
  
     [!code-vb[VbFileIORead#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#17)]  
  
4. <span data-ttu-id="9c304-113">`While` ブロックと `Using` ブロックをそれぞれ `End While` と `End Using` で閉じます。</span><span class="sxs-lookup"><span data-stu-id="9c304-113">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#18)]  
  
## <a name="example"></a><span data-ttu-id="9c304-114">例</span><span class="sxs-lookup"><span data-stu-id="9c304-114">Example</span></span>  

 <span data-ttu-id="9c304-115">次のコードは、`test.txt` ファイルから読み取りを行う例です。</span><span class="sxs-lookup"><span data-stu-id="9c304-115">This example reads from the file `test.txt`.</span></span>  
  
 [!code-vb[VbFileIORead#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a><span data-ttu-id="9c304-116">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="9c304-116">Robust programming</span></span>  

 <span data-ttu-id="9c304-117">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9c304-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="9c304-118">指定された形式で行を解析できない (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>)。</span><span class="sxs-lookup"><span data-stu-id="9c304-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="9c304-119">例外の原因となった行が例外メッセージで報告され、その行に含まれているテキストには <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> プロパティが代入されます。</span><span class="sxs-lookup"><span data-stu-id="9c304-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned the text contained in the line.</span></span>  
  
- <span data-ttu-id="9c304-120">指定されたファイルが存在しない (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="9c304-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="9c304-121">部分信頼の状況下で、ファイルにアクセスするために必要なアクセス許可がユーザーにない。</span><span class="sxs-lookup"><span data-stu-id="9c304-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="9c304-122">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="9c304-122">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="9c304-123">パスが長すぎる (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="9c304-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="9c304-124">ファイルにアクセスする十分なアクセス許可がユーザーにない (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="9c304-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c304-125">参照</span><span class="sxs-lookup"><span data-stu-id="9c304-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="9c304-126">方法: 固定幅のテキスト ファイルを読み取る</span><span class="sxs-lookup"><span data-stu-id="9c304-126">How to: Read From Fixed-width Text Files</span></span>](how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="9c304-127">方法: 複数の書式を持つテキスト ファイルを読み取る</span><span class="sxs-lookup"><span data-stu-id="9c304-127">How to: Read From Text Files with Multiple Formats</span></span>](how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="9c304-128">TextFieldParser オブジェクトによるテキスト ファイルの解析</span><span class="sxs-lookup"><span data-stu-id="9c304-128">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="9c304-129">チュートリアル: Visual Basic によるファイルとディレクトリの操作</span><span class="sxs-lookup"><span data-stu-id="9c304-129">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="9c304-130">トラブルシューティング : テキスト ファイルの読み取りと書き込み</span><span class="sxs-lookup"><span data-stu-id="9c304-130">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)
