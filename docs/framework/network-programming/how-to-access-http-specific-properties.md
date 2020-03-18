---
title: '方法: HTTP 固有のプロパティにアクセスする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8848c7e-f5c5-4d42-b86d-9951ff8f4146
ms.openlocfilehash: 68ad6b2c55cd5cc467e53441caa778ea10b994fb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180852"
---
# <a name="how-to-access-http-specific-properties"></a><span data-ttu-id="c1cd1-102">方法: HTTP 固有のプロパティにアクセスする</span><span class="sxs-lookup"><span data-stu-id="c1cd1-102">How to: Access HTTP-Specific Properties</span></span>
<span data-ttu-id="c1cd1-103">このサンプルでは、HTTP の **Keep-alive** 動作を無効にして、Web サーバーからプロトコル バージョン番号を取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c1cd1-103">This sample shows how to turn off the HTTP **Keep-alive** behavior and get the protocol version number from the Web server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1cd1-104">例</span><span class="sxs-lookup"><span data-stu-id="c1cd1-104">Example</span></span>  
  
```vb  
Dim HttpWReq As HttpWebRequest= _  
    CType(WebRequest.Create("http://www.contoso.com"), HttpWebRequest)  
' Turn off connection keep-alives.  
HttpWReq.KeepAlive = False  
  
Dim HttpWResp As HttpWebResponse = _  
    CType(HttpWReq.GetResponse(), HttpWebResponse)  
  
' Get the HTTP protocol version number returned by the server.  
Dim ver As String = HttpWResp.ProtocolVersion.ToString()  
HttpWResp.Close()  
```  
  
```csharp  
HttpWebRequest HttpWReq =
    (HttpWebRequest)WebRequest.Create("http://www.contoso.com");  
// Turn off connection keep-alives.  
HttpWReq.KeepAlive = false;  
  
HttpWebResponse HttpWResp = (HttpWebResponse)HttpWReq.GetResponse();  
  
// Get the HTTP protocol version number returned by the server.  
String ver = HttpWResp.ProtocolVersion.ToString();  
HttpWResp.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c1cd1-105">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="c1cd1-105">Compiling the Code</span></span>  
 <span data-ttu-id="c1cd1-106">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c1cd1-106">This example requires:</span></span>  
  
- <span data-ttu-id="c1cd1-107">**System.Net** 名前空間の参照。</span><span class="sxs-lookup"><span data-stu-id="c1cd1-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1cd1-108">参照</span><span class="sxs-lookup"><span data-stu-id="c1cd1-108">See also</span></span>

- [<span data-ttu-id="c1cd1-109">プロキシを介したインターネットへのアクセス</span><span class="sxs-lookup"><span data-stu-id="c1cd1-109">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="c1cd1-110">アプリケーション プロトコルの使用</span><span class="sxs-lookup"><span data-stu-id="c1cd1-110">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="c1cd1-111">HTTP</span><span class="sxs-lookup"><span data-stu-id="c1cd1-111">HTTP</span></span>](http.md)
