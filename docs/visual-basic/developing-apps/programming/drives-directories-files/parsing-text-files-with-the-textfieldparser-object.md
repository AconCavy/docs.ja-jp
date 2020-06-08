---
title: TextFieldParser オブジェクトによるテキスト ファイルの解析
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, using
- I/O [Visual Basic], parsing files
- files [Visual Basic], parsing
ms.assetid: fc31d6e6-af0c-403f-8a00-d556b2c57567
ms.openlocfilehash: 7b2cb0dd39d14dd94db661cc9cbacf99edf0e778
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406678"
---
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a><span data-ttu-id="abd35-102">TextFieldParser オブジェクトによるテキスト ファイルの解析 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="abd35-102">Parsing text files with the TextFieldParser object (Visual Basic)</span></span>

<span data-ttu-id="abd35-103">`TextFieldParser` オブジェクトを使用すると、ログ ファイルやレガシ データベース情報など、区切り文字や幅に応じて複数列に区切られたテキストとして構造化されている巨大なファイルを解析および処理できます。</span><span class="sxs-lookup"><span data-stu-id="abd35-103">The `TextFieldParser` object allows you to parse and process very large file that are structured as delimited-width columns of text, such as log files or legacy database information.</span></span> <span data-ttu-id="abd35-104">テキスト ファイルを `TextFieldParser` で解析するのは、テキスト ファイルを反復処理するのと同様です。解析メソッドでテキストのフィールドを抽出するのは、区切り文字の付いた文字列を文字列操作メソッドでトークン化するのと同様です。</span><span class="sxs-lookup"><span data-stu-id="abd35-104">Parsing a text file with `TextFieldParser` is similar to iterating over a text file, while the parse method to extract fields of text is similar to string manipulation methods used to tokenize delimited strings.</span></span>  
  
## <a name="parsing-different-types-of-text-files"></a><span data-ttu-id="abd35-105">さまざまな種類のテキスト ファイルの解析</span><span class="sxs-lookup"><span data-stu-id="abd35-105">Parsing different types of text files</span></span>  

 <span data-ttu-id="abd35-106">テキスト ファイルは、コンマやタブ空白などの文字で可変幅のフィールドに区切られている場合があります。</span><span class="sxs-lookup"><span data-stu-id="abd35-106">Text files may have fields of various width, delimited by a character such as a comma or a tab space.</span></span> <span data-ttu-id="abd35-107">次の例のように、`TextFieldType` および区切り記号を定義します。この例では、`SetDelimiters` メソッドを使用して、タブ区切りのテキスト ファイルを定義しています。</span><span class="sxs-lookup"><span data-stu-id="abd35-107">Define `TextFieldType` and the delimiter, as in the following example, which uses the `SetDelimiters` method to define a tab-delimited text file:</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#21)]  
  
 <span data-ttu-id="abd35-108">また、テキスト ファイルによっては、固定幅のフィールドを持つ場合もあります。</span><span class="sxs-lookup"><span data-stu-id="abd35-108">Other text files may have field widths that are fixed.</span></span> <span data-ttu-id="abd35-109">その場合には、次の例のように、`TextFieldType` を `FixedWidth` と定義して、各フィールドの幅を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="abd35-109">In such cases, you need to define the `TextFieldType` as `FixedWidth` and define the widths of each field, as in the following example.</span></span> <span data-ttu-id="abd35-110">この例では、`SetFieldWidths` メソッドを使用して、テキストの列を定義しています。最初の列は幅が 5 文字、2 番目の列は 10 文字、3 番目の列は 11 文字、4 番目の列は可変幅です。</span><span class="sxs-lookup"><span data-stu-id="abd35-110">This example uses the `SetFieldWidths` method to define the columns of text: the first column is 5 characters wide, the second is 10, the third is 11, and the fourth is of variable width.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#22)]  
  
 <span data-ttu-id="abd35-111">書式を定義したら、`ReadFields` メソッドを使用して各行を順番に処理して、ファイルに対するループ処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="abd35-111">Once the format is defined, you can loop through the file, using the `ReadFields` method to process each line in turn.</span></span>  
  
 <span data-ttu-id="abd35-112">フィールドが指定の書式に一致しない場合には、<xref:Microsoft.VisualBasic.FileIO.MalformedLineException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="abd35-112">If a field does not match the specified format, a <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> exception is thrown.</span></span> <span data-ttu-id="abd35-113">この例外がスローされた場合、`ErrorLine` プロパティと `ErrorLineNumber` プロパティに、例外の原因になったテキストと、そのテキストの行番号が保持されます。</span><span class="sxs-lookup"><span data-stu-id="abd35-113">When such exceptions are thrown, the `ErrorLine` and `ErrorLineNumber` properties hold the text causing the exception and the line number of that text.</span></span>  
  
## <a name="parsing-files-with-multiple-formats"></a><span data-ttu-id="abd35-114">複数の書式を持つファイルの解析</span><span class="sxs-lookup"><span data-stu-id="abd35-114">Parsing files with multiple formats</span></span>  

 <span data-ttu-id="abd35-115">`TextFieldParser` オブジェクトの `PeekChars` メソッドを使用すると、各フィールドを読み取る前にチェックできます。これにより、フィールドに対して複数の書式を定義して、適切に対応できます。</span><span class="sxs-lookup"><span data-stu-id="abd35-115">The `PeekChars` method of the `TextFieldParser` object can be used to check each field before reading it, allowing you to define multiple formats for the fields and react accordingly.</span></span> <span data-ttu-id="abd35-116">詳細については、「[方法: 複数の書式を持つテキスト ファイルを読み取る](how-to-read-from-text-files-with-multiple-formats.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abd35-116">For more information, see [How to: Read From Text Files with Multiple Formats](how-to-read-from-text-files-with-multiple-formats.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abd35-117">参照</span><span class="sxs-lookup"><span data-stu-id="abd35-117">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFieldParser%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ReadFields%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLineNumber%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.FieldWidths%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.HasFieldsEnclosedInQuotes%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.LineNumber%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TrimWhiteSpace%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetFieldWidths%2A>
