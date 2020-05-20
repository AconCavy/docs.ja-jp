---
title: プラグ可能なプロトコルのプログラミング
ms.date: 03/30/2017
helpviewer_keywords:
- downloading Internet resources, pluggable protocols
- WebRequest class, pluggable protocols
- response to Internet request, pluggable protocols
- WebResponse class, pluggable protocols
- sending data, pluggable protocols
- network resources, pluggable protocols
- Internet, pluggable protocols
- programming pluggable protocols
- pluggable protocols, programming
- requesting data from Internet, pluggable protocols
- receiving data, pluggable protocols
- protocols, pluggable
ms.assetid: 66ef8456-7576-4e97-8956-959b216373db
ms.openlocfilehash: 94dfedd317782b9e518df02c84d9af55b1ef2b69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047398"
---
# <a name="programming-pluggable-protocols"></a><span data-ttu-id="35fb1-102">プラグ可能なプロトコルのプログラミング</span><span class="sxs-lookup"><span data-stu-id="35fb1-102">Programming Pluggable Protocols</span></span>
<span data-ttu-id="35fb1-103">抽象クラスの <xref:System.Net.WebRequest> と <xref:System.Net.WebResponse> は、プラグ可能なプロトコルの基礎を提供します。</span><span class="sxs-lookup"><span data-stu-id="35fb1-103">The abstract <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide the base for pluggable protocols.</span></span> <span data-ttu-id="35fb1-104">アプリケーションでは、<xref:System.Net.WebRequest> と <xref:System.Net.WebResponse> からプロトコル固有のクラスを派生することにより、使うプロトコルを指定しなくても、インターネット リソースにデータを要求して応答を読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="35fb1-104">By deriving protocol-specific classes from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, an application can request data from an Internet resource and read the response without specifying the protocol being used.</span></span>  
  
 <span data-ttu-id="35fb1-105">プロトコル固有の <xref:System.Net.WebRequest> を作成するには、その前に Create メソッドを登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35fb1-105">Before you can create a protocol-specific <xref:System.Net.WebRequest>, you must register its Create method.</span></span> <span data-ttu-id="35fb1-106"><xref:System.Net.WebRequest> の静的 <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> メソッドを使って、特定のインターネット スキーム、スキームとサーバー、またはスキームとサーバーとパスに対する要求のセットを処理するための、<xref:System.Net.WebRequest> の子孫を登録します。</span><span class="sxs-lookup"><span data-stu-id="35fb1-106">Use the static <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> method of <xref:System.Net.WebRequest> to register a <xref:System.Net.WebRequest> descendant to handle a set of requests to a particular Internet scheme, to a scheme and server, or to a scheme, server, and path.</span></span>  
  
 <span data-ttu-id="35fb1-107">ほとんどの場合は、<xref:System.Net.WebRequest> クラスのメソッドとプロパティを使ってデータを送受信できます。</span><span class="sxs-lookup"><span data-stu-id="35fb1-107">In most cases you will be able to send and receive data using the methods and properties of the <xref:System.Net.WebRequest> class.</span></span> <span data-ttu-id="35fb1-108">ただし、プロトコル固有のプロパティにアクセスする必要がある場合は、<xref:System.Net.WebRequest> を特定の派生クラス インスタンスに型キャストできます。</span><span class="sxs-lookup"><span data-stu-id="35fb1-108">However, if you need to access protocol-specific properties, you can typecast a <xref:System.Net.WebRequest> to a specific derived-class instance.</span></span>  
  
 <span data-ttu-id="35fb1-109">プラグ可能なプロトコルを利用するには、<xref:System.Net.WebRequest> の子孫で、プロトコル固有のプロパティを設定する必要がない既定の要求-応答トランザクションを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35fb1-109">To take advantage of pluggable protocols, your <xref:System.Net.WebRequest> descendants must provide a default request-and-response transaction that does not require protocol-specific properties to be set.</span></span> <span data-ttu-id="35fb1-110">たとえば、HTTP 用の <xref:System.Net.WebRequest> クラスを実装する <xref:System.Net.HttpWebRequest> クラスは、既定で `GET` 要求を提供し、Web サーバーから返されたストリームを含む <xref:System.Net.HttpWebResponse> を返します。</span><span class="sxs-lookup"><span data-stu-id="35fb1-110">For example, the <xref:System.Net.HttpWebRequest> class, which implements the <xref:System.Net.WebRequest> class for HTTP, provides a `GET` request by default and returns an <xref:System.Net.HttpWebResponse> that contains the stream returned from the Web server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35fb1-111">参照</span><span class="sxs-lookup"><span data-stu-id="35fb1-111">See also</span></span>

- [<span data-ttu-id="35fb1-112">WebRequest からの派生</span><span class="sxs-lookup"><span data-stu-id="35fb1-112">Deriving from WebRequest</span></span>](deriving-from-webrequest.md)
- [<span data-ttu-id="35fb1-113">WebResponse からの派生</span><span class="sxs-lookup"><span data-stu-id="35fb1-113">Deriving from WebResponse</span></span>](deriving-from-webresponse.md)
- [<span data-ttu-id="35fb1-114">.NET Framework のネットワーク プログラミング</span><span class="sxs-lookup"><span data-stu-id="35fb1-114">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="35fb1-115">方法: WebRequest を型キャストしてプロトコル固有のプロパティにアクセスする</span><span class="sxs-lookup"><span data-stu-id="35fb1-115">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>](how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
