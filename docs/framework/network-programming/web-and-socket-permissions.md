---
title: Web およびソケットのアクセス許可
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- positions [.NET Framework], accepting
- sockets, permissions
- network, permissions
- Internet, permissions
- Network Resources
- SocketPermission class, about SocketPermission class
- positions [.NET Framework], connecting
- WebPermission class, about WebPermission class
- permissions [.NET Framework], sockets
- security [.NET Framework], Internet
- positions [.NET Framework], granting
ms.assetid: d51ad8cb-03ae-4a51-bfcd-cfcf6b98afa9
ms.openlocfilehash: d1b993acbf20eac244e596075c3f826bba3211a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "71046862"
---
# <a name="web-and-socket-permissions"></a><span data-ttu-id="c1b3c-102">Web およびソケットのアクセス許可</span><span class="sxs-lookup"><span data-stu-id="c1b3c-102">Web and Socket Permissions</span></span>
<span data-ttu-id="c1b3c-103"><xref:System.Net> 名前空間を使用したアプリケーションのインターネット セキュリティは、<xref:System.Net.WebPermission> クラスと <xref:System.Net.SocketPermission> クラスで提供されます。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-103">Internet security for applications using the <xref:System.Net> namespace is provided by the <xref:System.Net.WebPermission> and <xref:System.Net.SocketPermission> classes.</span></span> <span data-ttu-id="c1b3c-104">**WebPermission** クラスは、URI からデータを要求するか、URI をインターネットに提供するアプリケーションの権限を制御します。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-104">The **WebPermission** class controls an application's right to request data from a URI or to serve a URI to the Internet.</span></span> <span data-ttu-id="c1b3c-105">**SocketPermission** クラスは、ソケットのホスト、ポート番号、およびトランスポート プロトコルに基づいて、アプリケーションが <xref:System.Net.Sockets.Socket> を使用してローカル ポートでデータを受け入れる権利、または別のアドレスでトランスポート プロトコルを使用してリモート デバイスに接続する権利を制御します。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-105">The **SocketPermission** class controls an application's right to use a <xref:System.Net.Sockets.Socket> to accept data on a local port or to contact remote devices using a transport protocol at another address, based on the host, port number, and transport protocol of the socket.</span></span>  
  
 <span data-ttu-id="c1b3c-106">使用するアクセス許可クラスは、アプリケーションの種類によって変わります。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-106">Which permission class you use depends on your application type.</span></span> <span data-ttu-id="c1b3c-107"><xref:System.Net.WebRequest> とその子孫を使用するアプリケーションでアクセス許可を管理するには、**WebPermission** クラスを使用するようにします。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-107">Applications that use <xref:System.Net.WebRequest> and its descendants should use the **WebPermission** class to manage permissions.</span></span> <span data-ttu-id="c1b3c-108">ソケットレベルのアクセスを使用するアプリケーションでアクセス許可を管理するには、**SocketPermission** クラスを使用するようにします。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-108">Applications that use socket-level access should use the **SocketPermission** class to manage permissions.</span></span>  
  
 <span data-ttu-id="c1b3c-109">**WebPermission** と **SocketPermission** は、受け入れと接続という 2 つのアクセス許可を定義します。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-109">**WebPermission** and **SocketPermission** define two permissions: accept and connect.</span></span> <span data-ttu-id="c1b3c-110">受け入れは、別のパーティーからの受信接続に応答する権利をアプリケーションに付与します。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-110">Accept grants the application the right to answer an incoming connection from another party.</span></span> <span data-ttu-id="c1b3c-111">接続は、別のパーティーへの接続を開始する権利をアプリケーションに付与します。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-111">Connect grants the application the right to initiate a connection to another party.</span></span>  
  
 <span data-ttu-id="c1b3c-112">**SocketPermission** インスタンスの場合、受け入れとは、アプリケーションがローカル トランスポート アドレスで受信接続を受け入れ可能であることを意味し、接続とは、アプリケーションが何らかのリモート (またはローカル) トランスポート アドレスに接続できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-112">For **SocketPermission** instances, accept means that an application can accept incoming connections on a local transport address; connect means that an application can connect to some remote (or local) transport address.</span></span>  
  
 <span data-ttu-id="c1b3c-113">**WebPermission** インスタンスの場合、受け入れとは、**WebPermission** が制御する URI を世界にエクスポートできることを意味し、接続とは、アプリケーションがその URI (リモートまたはローカル) にアクセスできることを意味します。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-113">For **WebPermission** instances, accept means that an application can export the URI controlled by the **WebPermission** to the world; connect means that an application can access that URI (whether it is remote or local).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1b3c-114">参照</span><span class="sxs-lookup"><span data-stu-id="c1b3c-114">See also</span></span>

- [<span data-ttu-id="c1b3c-115">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c1b3c-115">Security</span></span>](../../standard/security/index.md)
- [<span data-ttu-id="c1b3c-116">ネットワーク プログラミングにおけるセキュリティ</span><span class="sxs-lookup"><span data-stu-id="c1b3c-116">Security in Network Programming</span></span>](security-in-network-programming.md)
