---
title: '方法: ログ ファイルを開いて情報を追加する'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET Framework], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
ms.openlocfilehash: 025c35344b9262e1f2fa6da87b68e46e21a54222
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291826"
---
# <a name="how-to-open-and-append-to-a-log-file"></a><span data-ttu-id="dec8c-102">方法: ログ ファイルを開いて情報を追加する</span><span class="sxs-lookup"><span data-stu-id="dec8c-102">How to: Open and append to a log file</span></span>
<span data-ttu-id="dec8c-103"><xref:System.IO.StreamWriter> および <xref:System.IO.StreamReader> は、ストリームから文字の書き込んだり、読み取りを行います。</span><span class="sxs-lookup"><span data-stu-id="dec8c-103"><xref:System.IO.StreamWriter> and <xref:System.IO.StreamReader> write characters to and read characters from streams.</span></span> <span data-ttu-id="dec8c-104">次のコード例は、入力用に *log.txt* ファイルを開くか、まだファイルがない場合、ファイルを作成し、ファイルの末尾に情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="dec8c-104">The following code example opens the *log.txt* file for input, or creates it if it doesn't exist, and appends log information to the end of the file.</span></span> <span data-ttu-id="dec8c-105">次に、ファイルの内容が表示用に標準出力に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="dec8c-105">The example then writes the contents of the file to standard output for display.</span></span>

<span data-ttu-id="dec8c-106">この例の代わりとして、情報を 1 つの文字列または文字列配列として格納し、<xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> または <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> メソッドを使用して同じ機能を実現できます。</span><span class="sxs-lookup"><span data-stu-id="dec8c-106">As an alternative to this example, you could store the information as a single string or string array, and use the <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> or <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> method to achieve the same functionality.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dec8c-107">Visual Basic を使用するユーザーは、ログ ファイルの作成またはログ ファイルへの書き込みのために、<xref:Microsoft.VisualBasic.Logging.Log> クラスまたは <xref:Microsoft.VisualBasic.FileIO.FileSystem> クラスによって提供されるメソッドまたはプロパティを使用することを選択できます。</span><span class="sxs-lookup"><span data-stu-id="dec8c-107">Visual Basic users may choose to use the methods and properties provided by the <xref:Microsoft.VisualBasic.Logging.Log> class or <xref:Microsoft.VisualBasic.FileIO.FileSystem> class for creating or writing to log files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dec8c-108">例</span><span class="sxs-lookup"><span data-stu-id="dec8c-108">Example</span></span>  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="dec8c-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="dec8c-109">See also</span></span>

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="dec8c-110">方法: ディレクトリとファイルを列挙する</span><span class="sxs-lookup"><span data-stu-id="dec8c-110">How to: Enumerate directories and files</span></span>](how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="dec8c-111">方法: 新しく作成されたデータ ファイルに対して読み書きする</span><span class="sxs-lookup"><span data-stu-id="dec8c-111">How to: Read and write to a newly created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="dec8c-112">方法: ファイルからテキストを読み取る</span><span class="sxs-lookup"><span data-stu-id="dec8c-112">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="dec8c-113">方法: テキストのファイルへの書き込み</span><span class="sxs-lookup"><span data-stu-id="dec8c-113">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="dec8c-114">方法: 文字列からの文字の読み取り</span><span class="sxs-lookup"><span data-stu-id="dec8c-114">How to: Read characters from a string</span></span>](how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="dec8c-115">方法: 文字列への文字の書き込み</span><span class="sxs-lookup"><span data-stu-id="dec8c-115">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="dec8c-116">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="dec8c-116">File and stream I/O</span></span>](index.md)
