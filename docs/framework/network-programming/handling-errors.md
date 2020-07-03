---
title: エラー処理
description: WebRequest と WebResponse によってスローされるシステムおよび Web 固有の例外について学習します。 問題を理解して解決するには、Status プロパティを使用します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Internet, WebRequest and WebResponse classes exceptions
- Status property
- WebExceptions class, about WebExceptions class
- Timeout enumeration member
- ConnectFailure enumeration member
- TrustFailure enumeration member
- WebRequest class, exceptions
- requesting data from Internet, error handling
- Success enumeration member
- receiving data, errors
- ProtocolError enumeration member
- downloading Internet resources, error handling
- WebResponse class, exceptions
- SendFailure enumeration member
- errors [.NET Framework], WebRequest and WebResponse classes exceptions
- sending data, errors
- response to Internet request, error handling
- NameResolutionFailure enumeration member
- KeepAliveFailure enumeration member
- network resources, WebRequest and WebResponse classes exceptions
- RequestCanceled enumeration member
- ReceiveFailure enumeration member
- ServerProtocolViolation enumeration member
- ConnectionClosed enumeration member
- SecureChannelFailure enumeration member
ms.assetid: 657141cd-5cf5-4fdb-a4b2-4c040eba84b5
ms.openlocfilehash: 786b2bd8bc4d1b394bcfe920053b2f4f55d1cdea
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502575"
---
# <a name="handling-errors"></a><span data-ttu-id="b722d-104">エラー処理</span><span class="sxs-lookup"><span data-stu-id="b722d-104">Handling Errors</span></span>

<span data-ttu-id="b722d-105"><xref:System.Net.WebRequest> および <xref:System.Net.WebResponse> クラスでは、システム例外 (<xref:System.ArgumentException> など) と Web 固有の例外 (<xref:System.Net.WebRequest.GetResponse%2A> メソッドでスローされる <xref:System.Net.WebException>) の両方がスローされます。</span><span class="sxs-lookup"><span data-stu-id="b722d-105">The <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes throw both system exceptions (such as <xref:System.ArgumentException>) and Web-specific exceptions (which are <xref:System.Net.WebException> thrown by the <xref:System.Net.WebRequest.GetResponse%2A> method).</span></span>  
  
<span data-ttu-id="b722d-106">各 **WebException** には、<xref:System.Net.WebExceptionStatus> 列挙体からの値を含む <xref:System.Net.WebException.Status%2A> プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="b722d-106">Each **WebException** includes a <xref:System.Net.WebException.Status%2A> property that contains a value from the <xref:System.Net.WebExceptionStatus> enumeration.</span></span> <span data-ttu-id="b722d-107">**Status** プロパティを調べることで、発生したエラーを特定し、エラーを解決するための適切な手順を実行することができます。</span><span class="sxs-lookup"><span data-stu-id="b722d-107">You can examine the **Status** property to determine the error that occurred and take the proper steps to resolve the error.</span></span>  
  
<span data-ttu-id="b722d-108">**Status** プロパティの有効な値を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="b722d-108">The following table describes the possible values for the **Status** property.</span></span>  
  
|<span data-ttu-id="b722d-109">Status</span><span class="sxs-lookup"><span data-stu-id="b722d-109">Status</span></span>|<span data-ttu-id="b722d-110">説明</span><span class="sxs-lookup"><span data-stu-id="b722d-110">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b722d-111">ConnectFailure</span><span class="sxs-lookup"><span data-stu-id="b722d-111">ConnectFailure</span></span>|<span data-ttu-id="b722d-112">トランスポート レベルでリモート サービスに接続できませんでした。</span><span class="sxs-lookup"><span data-stu-id="b722d-112">The remote service could not be contacted at the transport level.</span></span>|  
|<span data-ttu-id="b722d-113">ConnectionClosed</span><span class="sxs-lookup"><span data-stu-id="b722d-113">ConnectionClosed</span></span>|<span data-ttu-id="b722d-114">接続は処理の途中で中断されました。</span><span class="sxs-lookup"><span data-stu-id="b722d-114">The connection was closed prematurely.</span></span>|  
|<span data-ttu-id="b722d-115">KeepAliveFailure</span><span class="sxs-lookup"><span data-stu-id="b722d-115">KeepAliveFailure</span></span>|<span data-ttu-id="b722d-116">サーバーは、Keep-alive ヘッダーの設定による接続を閉じました。</span><span class="sxs-lookup"><span data-stu-id="b722d-116">The server closed a connection made with the Keep-alive header set.</span></span>|  
|<span data-ttu-id="b722d-117">NameResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="b722d-117">NameResolutionFailure</span></span>|<span data-ttu-id="b722d-118">ドメイン サービスがホスト名を解決できませんでした。</span><span class="sxs-lookup"><span data-stu-id="b722d-118">The name service could not resolve the host name.</span></span>|  
|<span data-ttu-id="b722d-119">ProtocolError</span><span class="sxs-lookup"><span data-stu-id="b722d-119">ProtocolError</span></span>|<span data-ttu-id="b722d-120">サーバーから受信された応答は完全でしたが、プロトコル レベルのエラーが示されています。</span><span class="sxs-lookup"><span data-stu-id="b722d-120">The response received from the server was complete but indicated an error at the protocol level.</span></span>|  
|<span data-ttu-id="b722d-121">ReceiveFailure</span><span class="sxs-lookup"><span data-stu-id="b722d-121">ReceiveFailure</span></span>|<span data-ttu-id="b722d-122">完全な応答がリモート サーバーから受信されませんでした。</span><span class="sxs-lookup"><span data-stu-id="b722d-122">A complete response was not received from the remote server.</span></span>|  
|<span data-ttu-id="b722d-123">RequestCanceled</span><span class="sxs-lookup"><span data-stu-id="b722d-123">RequestCanceled</span></span>|<span data-ttu-id="b722d-124">要求は取り消されました。</span><span class="sxs-lookup"><span data-stu-id="b722d-124">The request was canceled.</span></span>|  
|<span data-ttu-id="b722d-125">SecureChannelFailure</span><span class="sxs-lookup"><span data-stu-id="b722d-125">SecureChannelFailure</span></span>|<span data-ttu-id="b722d-126">セキュリティで保護されたチャネル リンクでエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="b722d-126">An error occurred in a secure channel link.</span></span>|  
|<span data-ttu-id="b722d-127">SendFailure</span><span class="sxs-lookup"><span data-stu-id="b722d-127">SendFailure</span></span>|<span data-ttu-id="b722d-128">リモート サーバーに完全な要求を送信できませでした。</span><span class="sxs-lookup"><span data-stu-id="b722d-128">A complete request could not be sent to the remote server.</span></span>|  
|<span data-ttu-id="b722d-129">ServerProtocolViolation</span><span class="sxs-lookup"><span data-stu-id="b722d-129">ServerProtocolViolation</span></span>|<span data-ttu-id="b722d-130">サーバーの応答が有効な HTTP 応答ではありません。</span><span class="sxs-lookup"><span data-stu-id="b722d-130">The server response was not a valid HTTP response.</span></span>|  
|<span data-ttu-id="b722d-131">成功</span><span class="sxs-lookup"><span data-stu-id="b722d-131">Success</span></span>|<span data-ttu-id="b722d-132">エラーは発生しませんでした。</span><span class="sxs-lookup"><span data-stu-id="b722d-132">No error was encountered.</span></span>|  
|<span data-ttu-id="b722d-133">Timeout</span><span class="sxs-lookup"><span data-stu-id="b722d-133">Timeout</span></span>|<span data-ttu-id="b722d-134">要求に対して設定されたタイムアウト時間内で応答が受信されませんでした。</span><span class="sxs-lookup"><span data-stu-id="b722d-134">No response was received within the time-out set for the request.</span></span>|  
|<span data-ttu-id="b722d-135">TrustFailure</span><span class="sxs-lookup"><span data-stu-id="b722d-135">TrustFailure</span></span>|<span data-ttu-id="b722d-136">サーバー証明書を検証できませんでした。</span><span class="sxs-lookup"><span data-stu-id="b722d-136">A server certificate could not be validated.</span></span>|  
|<span data-ttu-id="b722d-137">MessageLengthLimitExceeded</span><span class="sxs-lookup"><span data-stu-id="b722d-137">MessageLengthLimitExceeded</span></span>|<span data-ttu-id="b722d-138">要求の送信時またはサーバーから応答の受信時に指定された制限を超えるメッセージが受信されました。</span><span class="sxs-lookup"><span data-stu-id="b722d-138">A message was received that exceeded the specified limit when sending a request or receiving a response from the server.</span></span>|  
|<span data-ttu-id="b722d-139">保留</span><span class="sxs-lookup"><span data-stu-id="b722d-139">Pending</span></span>|<span data-ttu-id="b722d-140">内部非同期要求が保留中です。</span><span class="sxs-lookup"><span data-stu-id="b722d-140">An internal asynchronous request is pending.</span></span>|  
|<span data-ttu-id="b722d-141">PipelineFailure</span><span class="sxs-lookup"><span data-stu-id="b722d-141">PipelineFailure</span></span>|<span data-ttu-id="b722d-142">この値は .NET Framework インフラストラクチャをサポートします。独自に作成したコードで直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="b722d-142">This value supports the .NET Framework infrastructure and is not intended to be used directly in your code.</span></span>|  
|<span data-ttu-id="b722d-143">ProxyNameResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="b722d-143">ProxyNameResolutionFailure</span></span>|<span data-ttu-id="b722d-144">ネーム リゾルバー サービスがプロキシ ホスト名を解決できませんでした。</span><span class="sxs-lookup"><span data-stu-id="b722d-144">The name resolver service could not resolve the proxy host name.</span></span>|  
|<span data-ttu-id="b722d-145">UnknownError</span><span class="sxs-lookup"><span data-stu-id="b722d-145">UnknownError</span></span>|<span data-ttu-id="b722d-146">不明な種類の例外が発生しました。</span><span class="sxs-lookup"><span data-stu-id="b722d-146">An exception of unknown type has occurred.</span></span>|  
  
<span data-ttu-id="b722d-147">**Status** プロパティが **WebExceptionStatus.ProtocolError** である場合は、サーバーからの応答を含む **WebResponse** を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b722d-147">When the **Status** property is **WebExceptionStatus.ProtocolError**, a **WebResponse** that contains the response from the server is available.</span></span> <span data-ttu-id="b722d-148">この応答を調べることで、プロトコル エラーの実際の原因を判別できます。</span><span class="sxs-lookup"><span data-stu-id="b722d-148">You can examine this response to determine the actual source of the protocol error.</span></span>  
  
<span data-ttu-id="b722d-149">次の例は、**WebException** をキャッチする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b722d-149">The following example shows how to catch a **WebException**.</span></span>  
  
```csharp  
try
{  
    // Create a request instance.  
    WebRequest myRequest =
    WebRequest.Create("http://www.contoso.com");  
    // Get the response.  
    WebResponse myResponse = myRequest.GetResponse();  
    //Get a readable stream from the server.
    Stream sr = myResponse.GetResponseStream();  
  
    //Read from the stream and write any data to the console.  
    bytesread = sr.Read( myBuffer, 0, length);  
    while( bytesread > 0 )
    {  
        for (int i=0; i<bytesread; i++) {  
            Console.Write( "{0}", myBuffer[i]);  
        }  
        Console.WriteLine();  
        bytesread = sr.Read( myBuffer, 0, length);  
    }  
    sr.Close();  
    myResponse.Close();  
}  
catch (WebException webExcp)
{  
    // If you reach this point, an exception has been caught.  
    Console.WriteLine("A WebException has been caught.");  
    // Write out the WebException message.  
    Console.WriteLine(webExcp.ToString());  
    // Get the WebException status code.  
    WebExceptionStatus status =  webExcp.Status;  
    // If status is WebExceptionStatus.ProtocolError,
    //   there has been a protocol error and a WebResponse
    //   should exist. Display the protocol error.  
    if (status == WebExceptionStatus.ProtocolError) {  
        Console.Write("The server returned protocol error ");  
        // Get HttpWebResponse so that you can check the HTTP status code.  
        HttpWebResponse httpResponse = (HttpWebResponse)webExcp.Response;  
        Console.WriteLine((int)httpResponse.StatusCode + " - "  
           + httpResponse.StatusCode);  
    }  
}  
catch (Exception e)
{  
    // Code to catch other exceptions goes here.  
}  
```  
  
```vb  
Try  
    ' Create a request instance.  
    Dim myRequest As WebRequest = WebRequest.Create("http://www.contoso.com")  
    ' Get the response.  
    Dim myResponse As WebResponse = myRequest.GetResponse()  
    'Get a readable stream from the server.
    Dim sr As Stream = myResponse.GetResponseStream()  
  
    Dim i As Integer
    'Read from the stream and write any data to the console.  
    bytesread = sr.Read(myBuffer, 0, length)  
    While bytesread > 0  
        For i = 0 To bytesread - 1  
            Console.Write("{0}", myBuffer(i))  
        Next i  
        Console.WriteLine()  
        bytesread = sr.Read(myBuffer, 0, length)  
    End While  
    sr.Close()  
    myResponse.Close()  
Catch webExcp As WebException  
    ' If you reach this point, an exception has been caught.  
    Console.WriteLine("A WebException has been caught.")  
    ' Write out the WebException message.  
    Console.WriteLine(webExcp.ToString())  
    ' Get the WebException status code.  
    Dim status As WebExceptionStatus = webExcp.Status  
    ' If status is WebExceptionStatus.ProtocolError,
    '   there has been a protocol error and a WebResponse
    '   should exist. Display the protocol error.  
    If status = WebExceptionStatus.ProtocolError Then  
        Console.Write("The server returned protocol error ")  
        ' Get HttpWebResponse so that you can check the HTTP status code.  
        Dim httpResponse As HttpWebResponse = _  
           CType(webExcp.Response, HttpWebResponse)  
        Console.WriteLine(CInt(httpResponse.StatusCode).ToString() & _  
           " - " & httpResponse.StatusCode.ToString())  
    End If  
Catch e As Exception  
    ' Code to catch other exceptions goes here.  
End Try  
```  
  
<span data-ttu-id="b722d-150">Windows ソケットでエラーが発生した場合、<xref:System.Net.Sockets.Socket> クラスを使用するアプリケーションは <xref:System.Net.Sockets.SocketException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="b722d-150">Applications that use the <xref:System.Net.Sockets.Socket> class throw <xref:System.Net.Sockets.SocketException> when errors occur on the Windows socket.</span></span> <span data-ttu-id="b722d-151"><xref:System.Net.Sockets.TcpClient>、<xref:System.Net.Sockets.TcpListener>、および <xref:System.Net.Sockets.UdpClient> は **Socket** クラスに基づくものであり、同様に **SocketExceptions** をスローします。</span><span class="sxs-lookup"><span data-stu-id="b722d-151">The <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes are built on top of the **Socket** class and throw **SocketExceptions** as well.</span></span>  
  
<span data-ttu-id="b722d-152">**SocketException** がスローされると、**SocketException** クラスは <xref:System.Net.Sockets.SocketException.ErrorCode%2A> プロパティを、最後に発生したオペレーティング システムのソケット エラーに設定します。</span><span class="sxs-lookup"><span data-stu-id="b722d-152">When a **SocketException** is thrown, the **SocketException** class sets the <xref:System.Net.Sockets.SocketException.ErrorCode%2A> property to the last operating system socket error that occurred.</span></span> <span data-ttu-id="b722d-153">ソケット エラー コードの詳細については、MSDN の Winsock 2.0 API エラー コードに関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b722d-153">For more information about socket error codes, see the Winsock 2.0 API error code documentation in MSDN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b722d-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="b722d-154">See also</span></span>

- [<span data-ttu-id="b722d-155">.NET での例外の処理とスロー</span><span class="sxs-lookup"><span data-stu-id="b722d-155">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="b722d-156">データの要求</span><span class="sxs-lookup"><span data-stu-id="b722d-156">Requesting Data</span></span>](requesting-data.md)
