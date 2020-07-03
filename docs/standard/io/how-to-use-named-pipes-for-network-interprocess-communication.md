---
title: '方法: ネットワークのプロセス間通信で名前付きパイプを使用する'
description: パイプ サーバーとネットワーク内の 1 つ以上のパイプ クライアントとの間でのプロセス間通信に名前付きパイプを使用する 2 つの例を参照します。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- message-based communication [.NET Framework], named pipes
- named pipes [.NET Framework]
- pipes [.NET Framework]
- multiple connections via named pipes
- network communications [.NET Framework], named pipes
- impersonation [.NET Framework], named pipes
- full duplex communication [.NET Framework], named pipes
ms.assetid: 4e4d7e64-9f1b-4026-98f7-20488ac7b42b
ms.openlocfilehash: a529d1d44a903df36099a59e07f4582554d230f2
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662564"
---
# <a name="how-to-use-named-pipes-for-network-interprocess-communication"></a><span data-ttu-id="3266d-103">方法: ネットワークのプロセス間通信で名前付きパイプを使用する</span><span class="sxs-lookup"><span data-stu-id="3266d-103">How to: Use Named Pipes for Network Interprocess Communication</span></span>
<span data-ttu-id="3266d-104">名前付きパイプは、パイプ サーバーと 1 つ以上のパイプ クライアントとの間でのプロセス間通信を提供します。</span><span class="sxs-lookup"><span data-stu-id="3266d-104">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="3266d-105">名前付きパイプには、ローカル コンピューター上のプロセス間通信を提供する匿名パイプと比較して、より多くの機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="3266d-105">They offer more functionality than anonymous pipes, which provide interprocess communication on a local computer.</span></span> <span data-ttu-id="3266d-106">名前付きパイプは、ネットワーク上の複数のサーバー インスタンスでの全二重通信、メッセージ ベースの通信、およびクライアント偽装をサポートしています。偽装を使用すると、プロセスを接続してリモート サーバー上で独自のアクセス許可セットを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3266d-106">Named pipes support full duplex communication over a network and multiple server instances, message-based communication, and client impersonation, which enables connecting processes to use their own set of permissions on remote servers.</span></span>  
  
 <span data-ttu-id="3266d-107">名前付きパイプを実装するには、<xref:System.IO.Pipes.NamedPipeServerStream> クラスと <xref:System.IO.Pipes.NamedPipeClientStream> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="3266d-107">To implement name pipes, use the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3266d-108">例</span><span class="sxs-lookup"><span data-stu-id="3266d-108">Example</span></span>  
 <span data-ttu-id="3266d-109"><xref:System.IO.Pipes.NamedPipeServerStream> クラスを使用して、名前付きパイプを作成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3266d-109">The following example demonstrates how to create a named pipe by using the <xref:System.IO.Pipes.NamedPipeServerStream> class.</span></span> <span data-ttu-id="3266d-110">この例では、サーバー プロセスは 4 つのスレッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="3266d-110">In this example, the server process creates four threads.</span></span> <span data-ttu-id="3266d-111">各スレッドは、1 つのクライアント接続を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="3266d-111">Each thread can accept a client connection.</span></span> <span data-ttu-id="3266d-112">接続されたクライアント プロセスは、サーバーにファイル名を提供します。</span><span class="sxs-lookup"><span data-stu-id="3266d-112">The connected client process then supplies the server with a file name.</span></span> <span data-ttu-id="3266d-113">クライアントに十分なアクセス許可がある場合は、サーバー プロセスはファイルを開き、その内容をクライアントに送り返します。</span><span class="sxs-lookup"><span data-stu-id="3266d-113">If the client has sufficient permissions, the server process opens the file and sends its contents back to the client.</span></span>  
  
 [!code-cpp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="3266d-114">例</span><span class="sxs-lookup"><span data-stu-id="3266d-114">Example</span></span>  
 <span data-ttu-id="3266d-115">次の例は、<xref:System.IO.Pipes.NamedPipeClientStream> クラスを使用するクライアント プロセスを示したものです。</span><span class="sxs-lookup"><span data-stu-id="3266d-115">The following example shows the client process, which uses the <xref:System.IO.Pipes.NamedPipeClientStream> class.</span></span> <span data-ttu-id="3266d-116">クライアントはサーバー プロセスに接続し、サーバーにファイル名を送信します。</span><span class="sxs-lookup"><span data-stu-id="3266d-116">The client connects to the server process and sends a file name to the server.</span></span> <span data-ttu-id="3266d-117">この例では偽装を使用しているため、クライアント アプリケーションを実行している ID はファイルにアクセスする権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3266d-117">The example uses impersonation, so the identity that is running the client application must have permission to access the file.</span></span> <span data-ttu-id="3266d-118">サーバーは、ファイルの内容をクライアントに送り返します。</span><span class="sxs-lookup"><span data-stu-id="3266d-118">The server then sends the contents of the file back to the client.</span></span> <span data-ttu-id="3266d-119">その後、ファイルの内容がコンソールに表示されます。</span><span class="sxs-lookup"><span data-stu-id="3266d-119">The file contents are then displayed to the console.</span></span>  
  
 [!code-csharp[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="robust-programming"></a><span data-ttu-id="3266d-120">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="3266d-120">Robust Programming</span></span>  
 <span data-ttu-id="3266d-121">ここで例示したクライアント プロセスとサーバー プロセスは、同じコンピューターで実行することを意図しているため、<xref:System.IO.Pipes.NamedPipeClientStream> オブジェクトには、`"."` というサーバー名が提供されます。</span><span class="sxs-lookup"><span data-stu-id="3266d-121">The client and server processes in this example are intended to run on the same computer, so the server name provided to the <xref:System.IO.Pipes.NamedPipeClientStream> object is `"."`.</span></span> <span data-ttu-id="3266d-122">クライアント プロセスとサーバー プロセスを異なるコンピューター上で実行する場合、`"."` はサーバー プロセスを実行するコンピューターのネットワーク名で置換されます。</span><span class="sxs-lookup"><span data-stu-id="3266d-122">If the client and server processes were on separate computers, `"."` would be replaced with the network name of the computer that runs the server process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3266d-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="3266d-123">See also</span></span>

- <xref:System.Security.Principal.TokenImpersonationLevel>
- <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName%2A>
- [<span data-ttu-id="3266d-124">パイプ</span><span class="sxs-lookup"><span data-stu-id="3266d-124">Pipes</span></span>](pipe-operations.md)
- [<span data-ttu-id="3266d-125">方法: ローカルのプロセス間通信で匿名パイプを使用する</span><span class="sxs-lookup"><span data-stu-id="3266d-125">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
