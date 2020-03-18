---
title: '方法: ローカルのプロセス間通信で匿名パイプを使用する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- anonymous pipes [.NET Framework]
- parent-child communication [.NET Framework]
- pipes [.NET Framework]
- one-way communication [.NET Framework]
- local computer communication [.NET Framework], pipes
ms.assetid: e7773c77-c646-4a01-8a96-a003d59fc4c9
ms.openlocfilehash: ea4aee60d090a56eb0cf3f2a81c1b05c04806d4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "77627995"
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a><span data-ttu-id="a449d-102">方法: ローカルのプロセス間通信で匿名パイプを使用する</span><span class="sxs-lookup"><span data-stu-id="a449d-102">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>
<span data-ttu-id="a449d-103">匿名パイプは、ローカル コンピューターでのプロセス間通信を実現します。</span><span class="sxs-lookup"><span data-stu-id="a449d-103">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="a449d-104">名前付きパイプと比較して提供する機能は少なくなりますが、オーバーヘッドも小さくなります。</span><span class="sxs-lookup"><span data-stu-id="a449d-104">They offer less functionality than named pipes, but also require less overhead.</span></span> <span data-ttu-id="a449d-105">匿名パイプを使用して、ローカル コンピューター上で容易にプロセス間通信を実行できます。</span><span class="sxs-lookup"><span data-stu-id="a449d-105">You can use anonymous pipes to make interprocess communication on a local computer easier.</span></span> <span data-ttu-id="a449d-106">匿名パイプを使用してネットワーク経由の通信を行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="a449d-106">You cannot use anonymous pipes for communication over a network.</span></span>  
  
 <span data-ttu-id="a449d-107">匿名パイプを実装するには、<xref:System.IO.Pipes.AnonymousPipeServerStream> クラスと <xref:System.IO.Pipes.AnonymousPipeClientStream> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="a449d-107">To implement anonymous pipes, use the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a449d-108">例</span><span class="sxs-lookup"><span data-stu-id="a449d-108">Example</span></span>  
 <span data-ttu-id="a449d-109">次に、匿名パイプを使用して、親プロセスから子プロセスに文字列を送信する方法の例を示します。</span><span class="sxs-lookup"><span data-stu-id="a449d-109">The following example demonstrates a way to send a string from a parent process to a child process using anonymous pipes.</span></span> <span data-ttu-id="a449d-110">この例では、<xref:System.IO.Pipes.AnonymousPipeServerStream> の <xref:System.IO.Pipes.PipeDirection> 値を使用して、親プロセス内に <xref:System.IO.Pipes.PipeDirection.Out> オブジェクトを作成しています。</span><span class="sxs-lookup"><span data-stu-id="a449d-110">This example creates an <xref:System.IO.Pipes.AnonymousPipeServerStream> object in a parent process with a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.Out>.</span></span> <span data-ttu-id="a449d-111">次に、親プロセスは、クライアント ハンドルを使用して子プロセスを作成し、<xref:System.IO.Pipes.AnonymousPipeClientStream> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="a449d-111">The parent process then creates a child process by using a client handle to create an <xref:System.IO.Pipes.AnonymousPipeClientStream> object.</span></span> <span data-ttu-id="a449d-112">子プロセスには、<xref:System.IO.Pipes.PipeDirection> の <xref:System.IO.Pipes.PipeDirection.In> 値が指定されています。</span><span class="sxs-lookup"><span data-stu-id="a449d-112">The child process has a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.In>.</span></span>  
  
 <span data-ttu-id="a449d-113">次に、親プロセスはユーザー指定の文字列を子プロセスに送信します。</span><span class="sxs-lookup"><span data-stu-id="a449d-113">The parent process then sends a user-supplied string to the child process.</span></span> <span data-ttu-id="a449d-114">この文字列は、子プロセスのコンソールに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a449d-114">The string is displayed to the console in the child process.</span></span>  
  
 <span data-ttu-id="a449d-115">サーバー プロセスの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a449d-115">The following example shows the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]
  
## <a name="example"></a><span data-ttu-id="a449d-116">例</span><span class="sxs-lookup"><span data-stu-id="a449d-116">Example</span></span>  
 <span data-ttu-id="a449d-117">クライアント プロセスの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a449d-117">The following example shows the client process.</span></span> <span data-ttu-id="a449d-118">サーバー プロセスはクライアント プロセスを開始し、開始したプロセスをクライアント ハンドルに渡します。</span><span class="sxs-lookup"><span data-stu-id="a449d-118">The server process starts the client process and gives that process a client handle.</span></span> <span data-ttu-id="a449d-119">クライアント コードから生成される実行可能ファイルの名前は `pipeClient.exe` とします。サーバー プロセスを実行する前に、このファイルをサーバーの実行可能ファイルと同じディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="a449d-119">The resulting executable from the client code should be named `pipeClient.exe` and be copied to the same directory as the server executable before running the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="a449d-120">参照</span><span class="sxs-lookup"><span data-stu-id="a449d-120">See also</span></span>

- [<span data-ttu-id="a449d-121">パイプ</span><span class="sxs-lookup"><span data-stu-id="a449d-121">Pipes</span></span>](../../../docs/standard/io/pipe-operations.md)
- [<span data-ttu-id="a449d-122">方法: ネットワークのプロセス間通信で名前付きパイプを使用する</span><span class="sxs-lookup"><span data-stu-id="a449d-122">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
