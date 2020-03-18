---
title: 同期サーバー ソケットの使用
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- synchronous server sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- server sockets
- receiving data, sockets
- Socket class, synchronous server sockets
- protocols, sockets
- sockets, synchronous server sockets
- Internet, sockets
ms.assetid: d1ce882e-653e-41f5-9289-844ec855b804
ms.openlocfilehash: cbc02c755ceefa8f31439f121a98978b82f33fa2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047031"
---
# <a name="using-a-synchronous-server-socket"></a><span data-ttu-id="52306-102">同期サーバー ソケットの使用</span><span class="sxs-lookup"><span data-stu-id="52306-102">Using a Synchronous Server Socket</span></span>
<span data-ttu-id="52306-103">同期サーバー ソケットは、ソケットで接続要求が受け取られるまでアプリケーションの実行を一時停止させます。</span><span class="sxs-lookup"><span data-stu-id="52306-103">Synchronous server sockets suspend the execution of the application until a connection request is received on the socket.</span></span> <span data-ttu-id="52306-104">同期ソケットは動作のためにネットワークを多用するアプリケーションには適しませんが、単純なネットワーク アプリケーションには適しています。</span><span class="sxs-lookup"><span data-stu-id="52306-104">Synchronous server sockets are not suitable for applications that make heavy use of the network in their operation, but they can be suitable for simple network applications.</span></span>  
  
 <span data-ttu-id="52306-105"><xref:System.Net.Sockets.Socket> メソッドと <xref:System.Net.Sockets.Socket.Bind%2A> メソッドを利用してエンドポイントで待ち受けるように <xref:System.Net.Sockets.Socket.Listen%2A> を設定したら、<xref:System.Net.Sockets.Socket.Accept%2A> メソッドを利用し、入ってくる接続要求を受け取る準備が完了となります。</span><span class="sxs-lookup"><span data-stu-id="52306-105">After a <xref:System.Net.Sockets.Socket> is set to listen on an endpoint using the <xref:System.Net.Sockets.Socket.Bind%2A> and <xref:System.Net.Sockets.Socket.Listen%2A> methods, it is ready to accept incoming connection requests using the <xref:System.Net.Sockets.Socket.Accept%2A> method.</span></span> <span data-ttu-id="52306-106">**Accept** メソッドが呼び出されると、接続要求が受け取られるまで、アプリケーションは一時停止となります。</span><span class="sxs-lookup"><span data-stu-id="52306-106">The application is suspended until a connection request is received when the **Accept** method is called.</span></span>  
  
 <span data-ttu-id="52306-107">接続要求が受け取られると、**Accept** は、接続元のクライアントに関連付けられている新しい **Socket** インスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="52306-107">When a connection request is received, **Accept** returns a new **Socket** instance that is associated with the connecting client.</span></span> <span data-ttu-id="52306-108">次の例では、クライアントからデータを読み込み、コンソールに表示し、クライアントにデータをエコー バックしています。</span><span class="sxs-lookup"><span data-stu-id="52306-108">The following example reads data from the client, displays it on the console, and echoes the data back to the client.</span></span> <span data-ttu-id="52306-109">**Socket** からは、いかなるメッセージング プロトコルも指定されません。そのため、文字列 "\<EOF>" はメッセージ データの終わりに印を付けます。</span><span class="sxs-lookup"><span data-stu-id="52306-109">The **Socket** does not specify any messaging protocol, so the string "\<EOF>" marks the end of the message data.</span></span> <span data-ttu-id="52306-110">**という名前の**Socket`listener` が初期化され、エンドポイントにバインドされていると想定しています。</span><span class="sxs-lookup"><span data-stu-id="52306-110">It assumes that a **Socket** named `listener` has been initialized and bound to an endpoint.</span></span>  
  
```vb  
Console.WriteLine("Waiting for a connection...")  
Dim handler As Socket = listener.Accept()  
Dim data As String = Nothing  
  
While True  
    bytes = New Byte(1024) {}  
    Dim bytesRec As Integer = handler.Receive(bytes)  
    data += Encoding.ASCII.GetString(bytes, 0, bytesRec)  
    If data.IndexOf("<EOF>") > - 1 Then  
        Exit While  
    End If  
End While  
  
Console.WriteLine("Text received : {0}", data)  
  
Dim msg As Byte() = Encoding.ASCII.GetBytes(data)  
handler.Send(msg)  
handler.Shutdown(SocketShutdown.Both)  
handler.Close()  
```  
  
```csharp  
Console.WriteLine("Waiting for a connection...");  
Socket handler = listener.Accept();  
String data = null;  
  
while (true) {  
    bytes = new byte[1024];  
    int bytesRec = handler.Receive(bytes);  
    data += Encoding.ASCII.GetString(bytes,0,bytesRec);  
    if (data.IndexOf("<EOF>") > -1) {  
        break;  
    }  
}  
  
Console.WriteLine( "Text received : {0}", data);  
  
byte[] msg = Encoding.ASCII.GetBytes(data);  
handler.Send(msg);  
handler.Shutdown(SocketShutdown.Both);  
handler.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="52306-111">参照</span><span class="sxs-lookup"><span data-stu-id="52306-111">See also</span></span>

- [<span data-ttu-id="52306-112">非同期サーバー ソケットの使用</span><span class="sxs-lookup"><span data-stu-id="52306-112">Using an Asynchronous Server Socket</span></span>](using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="52306-113">同期サーバー ソケットの例</span><span class="sxs-lookup"><span data-stu-id="52306-113">Synchronous Server Socket Example</span></span>](synchronous-server-socket-example.md)
- [<span data-ttu-id="52306-114">リッスン (ソケットで)</span><span class="sxs-lookup"><span data-stu-id="52306-114">Listening with Sockets</span></span>](listening-with-sockets.md)
