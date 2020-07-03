---
title: TCP サービスの使用
description: TcpClient クラスによって、TCP を使用してデータを要求し、受信するソケットを作成するための詳細が抽出されます。 .NET Framework ストリーム処理を使用してデータを読み書きします。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- requesting data from Internet, TCP
- receiving data, TCP
- TcpClient class, about TcpClient class
- data requests, TCP
- application protocols, TCP
- network resources, TCP
- sending data, TCP
- TCP
- protocols, TCP
- Internet, TCP
ms.assetid: d2811830-3bcb-495c-b82d-cda9cf919aad
ms.openlocfilehash: 329701e8f11ca7f87c40ee8b2cc6a337435242b5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501964"
---
# <a name="using-tcp-services"></a><span data-ttu-id="467e7-104">TCP サービスの使用</span><span class="sxs-lookup"><span data-stu-id="467e7-104">Using TCP Services</span></span>

<span data-ttu-id="467e7-105"><xref:System.Net.Sockets.TcpClient> クラスは、TCP を使用してインターネット リソースのデータを要求します。</span><span class="sxs-lookup"><span data-stu-id="467e7-105">The <xref:System.Net.Sockets.TcpClient> class requests data from an Internet resource using TCP.</span></span> <span data-ttu-id="467e7-106">**TcpClient** のメソッドとプロパティは、TCP を使用したデータの要求と受信用に <xref:System.Net.Sockets.Socket> を作成する詳細を抽象化します。</span><span class="sxs-lookup"><span data-stu-id="467e7-106">The methods and properties of **TcpClient** abstract the details for creating a <xref:System.Net.Sockets.Socket> for requesting and receiving data using TCP.</span></span> <span data-ttu-id="467e7-107">リモート デバイスへの接続はストリームとして表されるため、.NET Framework のストリーム処理技術を使用してデータの読み取りと書き込みを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="467e7-107">Because the connection to the remote device is represented as a stream, data can be read and written with .NET Framework stream-handling techniques.</span></span>

<span data-ttu-id="467e7-108">TCP プロトコルは、リモート エンドポイントとの接続を確立してから、その接続を使用してデータ パケットを送受信します。</span><span class="sxs-lookup"><span data-stu-id="467e7-108">The TCP protocol establishes a connection with a remote endpoint and then uses that connection to send and receive data packets.</span></span> <span data-ttu-id="467e7-109">TCP は、データ パケットをエンドポイントに送信し、受信時に正しい順序で構成されるようにする処理を担当します。</span><span class="sxs-lookup"><span data-stu-id="467e7-109">TCP is responsible for ensuring that data packets are sent to the endpoint and assembled in the correct order when they arrive.</span></span>

<span data-ttu-id="467e7-110">TCP 接続を確立するには、必要なサービスをホストするネットワーク デバイスのアドレスを知っている必要があります。また、サービスが通信に使用する TCP ポートも知っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="467e7-110">To establish a TCP connection, you must know the address of the network device hosting the service you need and you must know the TCP port that the service uses to communicate.</span></span> <span data-ttu-id="467e7-111">Internet Assigned Numbers Authority (IANA) では、一般的なサービスのポート番号が定義されています (「[Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)」 (サービス名および転送プロトコル ポート番号レジストリ) を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="467e7-111">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="467e7-112">IANA の一覧に掲載されていないサービスが、1,024 から 65,535 の範囲のポート番号を使用している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="467e7-112">Services not on the Iana list can have port numbers in the range 1,024 to 65,535.</span></span>

<span data-ttu-id="467e7-113">TCP ポート 13 でタイム サーバーに接続するように **TcpClient** を設定する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="467e7-113">The following example demonstrates setting up a **TcpClient** to connect to a time server on TCP port 13:</span></span>

```vb
Imports System.Net.Sockets
Imports System.Text

Public Class TcpTimeClient
    Private const portNum As Integer = 13
    Private const hostName As String = "host.contoso.com"

    ' Entry point  that delegates to C-style main Private Function.
    Public Overloads Shared Sub Main()
        System.Environment.ExitCode = _
            Main(System.Environment.GetCommandLineArgs())
    End Sub

    Overloads Public Shared Function Main(args As String()) As Integer
        Try
            Dim client As New TcpClient(hostName, portNum)

            Dim ns As NetworkStream = client.GetStream()

            Dim bytes(1024) As Byte
            Dim bytesRead As Integer = ns.Read(bytes, 0, bytes.Length)

            Console.WriteLine(Encoding.ASCII.GetString(bytes, 0, bytesRead))

        Catch e As Exception
            Console.WriteLine(e.ToString())
        End Try

        client.Close()

        Return 0
    End Function
End Class
```

```csharp
using System;
using System.Net.Sockets;
using System.Text;

public class TcpTimeClient
{
    private const int portNum = 13;
    private const string hostName = "host.contoso.com";

    public static int Main(String[] args)
    {
        try
        {
            var client = new TcpClient(hostName, portNum);

            NetworkStream ns = client.GetStream();

            byte[] bytes = new byte[1024];
            int bytesRead = ns.Read(bytes, 0, bytes.Length);

            Console.WriteLine(Encoding.ASCII.GetString(bytes,0,bytesRead));

            client.Close();

        }
        catch (Exception e)
        {
            Console.WriteLine(e.ToString());
        }

        return 0;
    }
}
```

<span data-ttu-id="467e7-114"><xref:System.Net.Sockets.TcpListener> を使用して、受信要求の TCP ポートを監視します。次に、クライアントへの接続を管理する **Socket** または **TcpClient** を作成します。</span><span class="sxs-lookup"><span data-stu-id="467e7-114"><xref:System.Net.Sockets.TcpListener> is used to monitor a TCP port for incoming requests and then create either a **Socket** or a **TcpClient** that manages the connection to the client.</span></span> <span data-ttu-id="467e7-115"><xref:System.Net.Sockets.TcpListener.Start%2A> メソッドでリッスンが有効になり、<xref:System.Net.Sockets.TcpListener.Stop%2A> メソッドでポートのリッスンが無効になります。</span><span class="sxs-lookup"><span data-stu-id="467e7-115">The <xref:System.Net.Sockets.TcpListener.Start%2A> method enables listening, and the <xref:System.Net.Sockets.TcpListener.Stop%2A> method disables listening on the port.</span></span> <span data-ttu-id="467e7-116"><xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> メソッドは受信接続要求を受け取り、**TcpClient** を作成して要求を処理します。<xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> メソッドは受信接続要求を受け取り、**Socket** を作成して要求を処理します。</span><span class="sxs-lookup"><span data-stu-id="467e7-116">The <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> method accepts incoming connection requests and creates a **TcpClient** to handle the request, and the <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> method accepts incoming connection requests and creates a **Socket** to handle the request.</span></span>

<span data-ttu-id="467e7-117">**TcpListener** を使用して TCP ポート 13 を監視するネットワーク タイム サーバーを作成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="467e7-117">The following example demonstrates creating a network time server using a **TcpListener** to monitor TCP port 13.</span></span> <span data-ttu-id="467e7-118">受信接続要求が受け取られると、タイム サーバーはホスト サーバーの現在の日時で応答します。</span><span class="sxs-lookup"><span data-stu-id="467e7-118">When an incoming connection request is accepted, the time server responds with the current date and time from the host server.</span></span>

```vb
Imports System.Net
Imports System.Net.Sockets
Imports System.Text

Public Class TcpTimeServer

    Private const portNum As Integer = 13

    ' Entry point that delegates to C-style main Private Function.
    Public Overloads Shared Sub Main()
        System.Environment.ExitCode = _
            Main(System.Environment.GetCommandLineArgs())
    End Sub

    Overloads Public Shared Function Main(args As String()) As Integer
        Dim done As Boolean = False

        Dim listener As New TcpListener(IPAddress.Any, portNum)

        listener.Start()

        While Not done
            Console.Write("Waiting for connection...")
            Dim client As TcpClient = listener.AcceptTcpClient()

            Console.WriteLine("Connection accepted.")
            Dim ns As NetworkStream = client.GetStream()

            Dim byteTime As Byte() = _
                Encoding.ASCII.GetBytes(DateTime.Now.ToString())

            Try
                ns.Write(byteTime, 0, byteTime.Length)
                ns.Close()
                client.Close()
            Catch e As Exception
                Console.WriteLine(e.ToString())
            End Try
        End While

        listener.Stop()

        Return 0
    End Function
End Class
```

```csharp
using System;
using System.Net;
using System.Net.Sockets;
using System.Text;

public class TcpTimeServer
{

    private const int portNum = 13;

    public static int Main(String[] args)
    {
        bool done = false;

        var listener = new TcpListener(IPAddress.Any, portNum);

        listener.Start();

        while (!done)
        {
            Console.Write("Waiting for connection...");
            TcpClient client = listener.AcceptTcpClient();

            Console.WriteLine("Connection accepted.");
            NetworkStream ns = client.GetStream();

            byte[] byteTime = Encoding.ASCII.GetBytes(DateTime.Now.ToString());

            try
            {
                ns.Write(byteTime, 0, byteTime.Length);
                ns.Close();
                client.Close();
            }
            catch (Exception e)
            {
                Console.WriteLine(e.ToString());
            }
        }

        listener.Stop();

        return 0;
    }

}
```
