---
title: '方法 : ファイルを削除する'
ms.date: 07/20/2015
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
ms.openlocfilehash: 57182f1a1d92b7fe954fd26b32c5e4b1107823ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348781"
---
# <a name="how-to-delete-a-file-in-visual-basic"></a><span data-ttu-id="d6ae3-102">方法: Visual Basic でファイルを削除する</span><span class="sxs-lookup"><span data-stu-id="d6ae3-102">How to: Delete a File in Visual Basic</span></span>

<span data-ttu-id="d6ae3-103">`DeleteFile` オブジェクトの `My.Computer.FileSystem` メソッドを使用すると、ファイルを削除することができます。</span><span class="sxs-lookup"><span data-stu-id="d6ae3-103">The `DeleteFile` method of the `My.Computer.FileSystem` object allows you to delete a file.</span></span> <span data-ttu-id="d6ae3-104">削除したファイルを**ごみ箱**に送るかどうか、ファイルを削除することをユーザーに確認するかどうか、ユーザーが操作をキャンセルした場合の処理方法などが、オプションとして用意されています。</span><span class="sxs-lookup"><span data-stu-id="d6ae3-104">Among the options it offers are: whether to send the deleted file to the **Recycle Bin**, whether to ask the user to confirm that the file should be deleted, and what to do when the user cancels the operation.</span></span>  
  
### <a name="to-delete-a-text-file"></a><span data-ttu-id="d6ae3-105">テキスト ファイルを削除するには</span><span class="sxs-lookup"><span data-stu-id="d6ae3-105">To delete a text file</span></span>  
  
- <span data-ttu-id="d6ae3-106">`DeleteFile` メソッドを使用してファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="d6ae3-106">Use the `DeleteFile` method to delete the file.</span></span> <span data-ttu-id="d6ae3-107">次のコードは、`test.txt` という名前のファイルを削除する方法の例です。</span><span class="sxs-lookup"><span data-stu-id="d6ae3-107">The following code demonstrates how to delete the file named `test.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#22)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a><span data-ttu-id="d6ae3-108">テキスト ファイルを削除して、ユーザーがファイルを削除することを確認するには</span><span class="sxs-lookup"><span data-stu-id="d6ae3-108">To delete a text file and ask the user to confirm that the file should be deleted</span></span>  
  
- <span data-ttu-id="d6ae3-109">`DeleteFile` を `showUI` に設定し、`AllDialogs` メソッドを使用してファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="d6ae3-109">Use the `DeleteFile` method to delete the file, setting `showUI` to `AllDialogs`.</span></span> <span data-ttu-id="d6ae3-110">次のコードは、`test.txt` という名前のファイルを、ユーザーに削除するファイルを確認した上で削除する方法の例です。</span><span class="sxs-lookup"><span data-stu-id="d6ae3-110">The following code demonstrates how to delete the file named `test.txt` and allow the user to confirm that the file should be deleted.</span></span>  
  
     [!code-vb[VbFileIOMisc#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#9)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a><span data-ttu-id="d6ae3-111">テキスト ファイルを削除してごみ箱に送るには</span><span class="sxs-lookup"><span data-stu-id="d6ae3-111">To delete a text file and send it to the Recycle Bin</span></span>  
  
- <span data-ttu-id="d6ae3-112">`DeleteFile` パラメーターに `SendToRecycleBin` を指定し、`recycle` メソッドを使用してファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="d6ae3-112">Use the `DeleteFile` method to delete the file, specifying `SendToRecycleBin` for the `recycle` parameter.</span></span> <span data-ttu-id="d6ae3-113">次のコードは、`test.txt` という名前のファイルを削除して**ごみ箱**に送る方法の例です。</span><span class="sxs-lookup"><span data-stu-id="d6ae3-113">The following code demonstrates how to delete the file named `test.txt` and send it to the **Recycle Bin**.</span></span>  
  
     [!code-vb[VbFileIOMisc#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#10)]  
  
## <a name="robust-programming"></a><span data-ttu-id="d6ae3-114">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="d6ae3-114">Robust Programming</span></span>  

 <span data-ttu-id="d6ae3-115">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d6ae3-115">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="d6ae3-116">パスが正しくない。長さが 0 の文字列である、空白だけが含まれている、使用できない文字が含まれている、デバイス パスである (先頭が \\\\.\\)、のいずれかの理由が考えられる (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="d6ae3-116">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="d6ae3-117">パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="d6ae3-117">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="d6ae3-118">パスがシステムで定義されている最大長を超えている (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="d6ae3-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="d6ae3-119">パス内のファイル名またはフォルダー名にコロン (:) が含まれている、または形式が無効である (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="d6ae3-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="d6ae3-120">ファイルが使用中の場合 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="d6ae3-120">The file is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="d6ae3-121">ユーザーがパスを参照するのに必要なアクセス許可がない (<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="d6ae3-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="d6ae3-122">ファイルが存在しない (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="d6ae3-122">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="d6ae3-123">ファイルの削除に必要なアクセス許可がユーザーにないか、またはファイルが読み取り専用である (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="d6ae3-123">The user does not have permission to delete the file, or the file is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="d6ae3-124">部分信頼の状況下で、必要なアクセス許可がユーザーにない (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="d6ae3-124">A partial-trust situation exists in which the user does not have sufficient permissions (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="d6ae3-125">ユーザーが操作を取り消し、`onUserCancel` が `ThrowException` に設定されている (<xref:System.OperationCanceledException>)。</span><span class="sxs-lookup"><span data-stu-id="d6ae3-125">The user cancelled the operation and `onUserCancel` is set to `ThrowException` (<xref:System.OperationCanceledException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6ae3-126">参照</span><span class="sxs-lookup"><span data-stu-id="d6ae3-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.UIOption>
- <xref:Microsoft.VisualBasic.FileIO.RecycleOption>
- [<span data-ttu-id="d6ae3-127">方法: ディレクトリにあるファイルのコレクションを取得する</span><span class="sxs-lookup"><span data-stu-id="d6ae3-127">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
