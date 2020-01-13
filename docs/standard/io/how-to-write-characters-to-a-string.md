---
title: '方法: 文字列への文字の書き込み'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET Framework], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
ms.openlocfilehash: b53513ef0b373cdde7703eddcd182ab7fd15cb9b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706622"
---
# <a name="how-to-write-characters-to-a-string"></a><span data-ttu-id="ab146-102">方法: 文字列への文字の書き込み</span><span class="sxs-lookup"><span data-stu-id="ab146-102">How to: Write characters to a string</span></span>
<span data-ttu-id="ab146-103">次のコード例では、文字列の配列から同期または非同期的に文字が書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="ab146-103">The following code examples write characters synchronously or asynchronously from a character array into a string.</span></span>  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a><span data-ttu-id="ab146-104">例:コンソール アプリで文字を同時に書き込む</span><span class="sxs-lookup"><span data-stu-id="ab146-104">Example: Write characters synchronously in a console app</span></span>  
 <span data-ttu-id="ab146-105">次の例では、<xref:System.IO.StringWriter> を使用し、5 つの文字が <xref:System.Text.StringBuilder> オブジェクトに同時に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="ab146-105">The following example uses a <xref:System.IO.StringWriter> to write five characters synchronously to a <xref:System.Text.StringBuilder> object.</span></span> 
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a><span data-ttu-id="ab146-106">例:WPF アプリで文字を非同期で書き込む</span><span class="sxs-lookup"><span data-stu-id="ab146-106">Example: Write characters asynchronously in a WPF app</span></span> 
 <span data-ttu-id="ab146-107">次の例は WPF アプリの裏側にあるコードです。</span><span class="sxs-lookup"><span data-stu-id="ab146-107">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="ab146-108">ウィンドウを読み込むと、<xref:System.Windows.Controls.TextBox> コントロールから非同期的にすべての文字を読み取り、配列に格納します。</span><span class="sxs-lookup"><span data-stu-id="ab146-108">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="ab146-109">次に、<xref:System.Windows.Controls.TextBlock> コントロールの個別の行に各文字または空白文字が非同期で書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="ab146-109">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ab146-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab146-110">See also</span></span>

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [<span data-ttu-id="ab146-111">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="ab146-111">File and stream I/O</span></span>](../../../docs/standard/io/index.md)  
- [<span data-ttu-id="ab146-112">非同期ファイル I/O</span><span class="sxs-lookup"><span data-stu-id="ab146-112">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [<span data-ttu-id="ab146-113">方法: ディレクトリとファイルを列挙する</span><span class="sxs-lookup"><span data-stu-id="ab146-113">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="ab146-114">方法: 新しく作成されたデータ ファイルに対して読み書きする</span><span class="sxs-lookup"><span data-stu-id="ab146-114">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="ab146-115">方法: ログ ファイルを開いて情報を追加する</span><span class="sxs-lookup"><span data-stu-id="ab146-115">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="ab146-116">方法: ファイルからテキストを読み取る</span><span class="sxs-lookup"><span data-stu-id="ab146-116">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="ab146-117">方法: テキストのファイルへの書き込み</span><span class="sxs-lookup"><span data-stu-id="ab146-117">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="ab146-118">方法: 文字列からの文字の読み取り</span><span class="sxs-lookup"><span data-stu-id="ab146-118">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
