---
title: '方法: WebRequest クラスを使用してデータを送信する'
description: .NET Framework の WebRequest クラスを使用してサーバーにデータを送信する方法について学習します。 この手順は、通常、Web ページにデータを投稿するときに使用されます。
ms.date: 03/25/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
ms.openlocfilehash: 4b353250fec778ee8b352f13de6d7faaf15c13ee
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502445"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a><span data-ttu-id="1fcf8-104">方法: WebRequest クラスを使用してデータを送信する</span><span class="sxs-lookup"><span data-stu-id="1fcf8-104">How to: Send data by using the WebRequest class</span></span>

<span data-ttu-id="1fcf8-105">次の手順では、サーバーにデータを送信するための手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-105">The following procedure describes the steps to send data to a server.</span></span> <span data-ttu-id="1fcf8-106">この手順は、通常、Web ページへのデータをポストするときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-106">This procedure is commonly used to post data to a Web page.</span></span>

## <a name="to-send-data-to-a-host-server"></a><span data-ttu-id="1fcf8-107">ホスト サーバーにデータを送信するには</span><span class="sxs-lookup"><span data-stu-id="1fcf8-107">To send data to a host server</span></span>

1. <span data-ttu-id="1fcf8-108">スクリプトや ASP.NET ページなど、データを受け取るリソースの URI を指定して <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> を呼び出すことによって <xref:System.Net.WebRequest> インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-108">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource, such as a script or ASP.NET page, that accepts data.</span></span> <span data-ttu-id="1fcf8-109">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-109">For example:</span></span>

    ```csharp
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")
    ```

    > [!NOTE]
    > <span data-ttu-id="1fcf8-110">.NET Framework は、*http:* 、*https:* 、*ftp:* 、*file:* で始まる URI に対応する <xref:System.Net.WebRequest> と <xref:System.Net.WebResponse> クラスから派生したプロトコル固有のクラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-110">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>

    <span data-ttu-id="1fcf8-111">プロトコル固有のプロパティを設定する必要がある場合、<xref:System.Net.WebRequest> または <xref:System.Net.WebResponse> オブジェクトをプロトコル固有のオブジェクトの種類にキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-111">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="1fcf8-112">詳細については、「[プラグ可能なプロトコルのプログラミング](programming-pluggable-protocols.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-112">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span>

2. <span data-ttu-id="1fcf8-113">`WebRequest` オブジェクトで必要なプロパティ値を設定します。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-113">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="1fcf8-114">たとえば、認証を有効にするには、<xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> プロパティを <xref:System.Net.NetworkCredential> クラスのインスタンスに設定します。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-114">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. <span data-ttu-id="1fcf8-115">HTTP `POST` メソッドなど、要求と共にデータを送信することを許可するプロトコル メソッドを指定します。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-115">Specify a protocol method that permits data to be sent with a request, such as the HTTP `POST` method:</span></span>

    ```csharp
    request.Method = "POST";
    ```

    ```vb
    request.Method = "POST"
    ```

4. <span data-ttu-id="1fcf8-116">要求で含めるバイト数に <xref:System.Web.HttpRequest.ContentLength> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-116">Set the <xref:System.Web.HttpRequest.ContentLength> property to the number of bytes you're including with your request.</span></span> <span data-ttu-id="1fcf8-117">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-117">For example:</span></span>

    ```csharp
    request.ContentLength = byteArray.Length;
    ```

    ```vb
    request.ContentLength = byteArray.Length
    ```

5. <span data-ttu-id="1fcf8-118"><xref:System.Web.HttpRequest.ContentType> プロパティに適切な値を設定します。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-118">Set the <xref:System.Web.HttpRequest.ContentType> property to an appropriate value.</span></span> <span data-ttu-id="1fcf8-119">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-119">For example:</span></span>

    ```csharp
    request.ContentType = "application/x-www-form-urlencoded";
    ```

    ```vb
    request.ContentType = "application/x-www-form-urlencoded"
    ```

6. <span data-ttu-id="1fcf8-120"><xref:System.Net.WebRequest.GetRequestStream%2A> メソッドを呼び出すことで、要求のデータを保持するストリームを取得します。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-120">Get the stream that holds request data by calling the <xref:System.Net.WebRequest.GetRequestStream%2A> method.</span></span> <span data-ttu-id="1fcf8-121">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-121">For example:</span></span>

    ```csharp
    Stream dataStream = request.GetRequestStream();
    ```

    ```vb
    Dim dataStream As Stream = request.GetRequestStream()
    ```

7. <span data-ttu-id="1fcf8-122">`GetRequestStream` メソッドによって返される <xref:System.IO.Stream> オブジェクトにデータを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-122">Write the data to the <xref:System.IO.Stream> object returned by the `GetRequestStream` method.</span></span> <span data-ttu-id="1fcf8-123">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-123">For example:</span></span>

    ```csharp
    dataStream.Write(byteArray, 0, byteArray.Length);
    ```

    ```vb
    dataStream.Write(byteArray, 0, byteArray.Length)
    ```

8. <span data-ttu-id="1fcf8-124"><xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> メソッドを呼び出すことで、要求のストリームを閉じます。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-124">Close the request stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="1fcf8-125">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-125">For example:</span></span>

    ```csharp
    dataStream.Close();
    ```

    ```vb
    dataStream.Close()
    ```

9. <span data-ttu-id="1fcf8-126"><xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> を呼び出してサーバーに要求を送信します。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-126">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1fcf8-127">このメソッドは、サーバーの応答を格納するオブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-127">This method returns an object containing the server's response.</span></span> <span data-ttu-id="1fcf8-128">返された `WebResponse` オブジェクトの型は、要求の URI のスキームで決定されます。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-128">The returned `WebResponse` object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="1fcf8-129">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-129">For example:</span></span>

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

10. <span data-ttu-id="1fcf8-130">`WebResponse` オブジェクトのプロパティにアクセスするか、またはそれをプロトコル固有インスタンスにキャストして、プロトコル固有のプロパティを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-130">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span>

    <span data-ttu-id="1fcf8-131">たとえば、<xref:System.Net.HttpWebResponse> の HTTP 固有のプロパティにアクセスするには、`WebResponse` オブジェクトを <xref:System.Net.HttpWebResponse> 参照にキャストします。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-131">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an <xref:System.Net.HttpWebResponse> reference.</span></span> <span data-ttu-id="1fcf8-132">次のコード例では、応答で送信される HTTP 固有の <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> プロパティを表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-132">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>

    ```csharp
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)
    ```

11. <span data-ttu-id="1fcf8-133">サーバーによって送信された応答データを格納しているストリームを取得するには、`WebResponse` オブジェクトの <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-133">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method of your `WebResponse` object.</span></span> <span data-ttu-id="1fcf8-134">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-134">For example:</span></span>

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

12. <span data-ttu-id="1fcf8-135">応答オブジェクトからデータを読み取った後に、<xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> メソッドを使用してそのオブジェクトを閉じるか、<xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> メソッドを使用して応答ストリームを閉じます。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-135">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="1fcf8-136">応答またはストリームのいずれかを閉じないと、アプリケーションからサーバーへの接続が不足し、追加の要求を処理できなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-136">If you don't close either the response or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="1fcf8-137">`WebResponse.Close` メソッドは応答を閉じるときに `Stream.Close` を呼び出すため、応答とストリーム オブジェクトの両方で `Close` を呼び出す必要はありませんが、呼び出しても害はありません。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-137">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="1fcf8-138">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-138">For example:</span></span>

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a><span data-ttu-id="1fcf8-139">例</span><span class="sxs-lookup"><span data-stu-id="1fcf8-139">Example</span></span>

<span data-ttu-id="1fcf8-140">次の例は、Web サーバーにデータを送信し、その応答内のデータを読み取る方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="1fcf8-140">The following example shows how to send data to a web server and read the data in its response:</span></span>

[!code-csharp[SendDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/SendDataUsingWebRequest/cs/WebRequestPostExample.cs)]
[!code-vb[SendDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/SendDataUsingWebRequest/vb/WebRequestPostExample.vb)]

## <a name="see-also"></a><span data-ttu-id="1fcf8-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="1fcf8-141">See also</span></span>

- [<span data-ttu-id="1fcf8-142">インターネット要求の作成</span><span class="sxs-lookup"><span data-stu-id="1fcf8-142">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="1fcf8-143">ネットワーク上でストリームを使用する</span><span class="sxs-lookup"><span data-stu-id="1fcf8-143">Using streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="1fcf8-144">プロキシを介したインターネットへのアクセス</span><span class="sxs-lookup"><span data-stu-id="1fcf8-144">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="1fcf8-145">データの要求</span><span class="sxs-lookup"><span data-stu-id="1fcf8-145">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="1fcf8-146">方法: WebRequest クラスを使用してデータを要求する</span><span class="sxs-lookup"><span data-stu-id="1fcf8-146">How to: Request data by using the WebRequest class</span></span>](how-to-request-data-using-the-webrequest-class.md)
