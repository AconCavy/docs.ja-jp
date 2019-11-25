---
title: アプリケーション開発での PNRP
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
ms.openlocfilehash: f9a408fbd7fbbb77c0fd5208926f4b06fcf23b38
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428205"
---
# <a name="pnrp-in-application-development"></a><span data-ttu-id="e7c20-102">アプリケーション開発での PNRP</span><span class="sxs-lookup"><span data-stu-id="e7c20-102">PNRP in Application Development</span></span>
<span data-ttu-id="e7c20-103">Windows Vista では、ネットワーク アプリケーションは、簡単な PNRP アプリケーション プログラミング インターフェイス (API) を通して名前発行および名前解決機能にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e7c20-103">In Windows Vista, networking applications can access name publication and resolution functions through a simplified PNRP application programming interface (API).</span></span>  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a><span data-ttu-id="e7c20-104">ピア名解決プロトコルの実装</span><span class="sxs-lookup"><span data-stu-id="e7c20-104">Implementing the Peer Name Resolution Protocol</span></span>  
 <span data-ttu-id="e7c20-105">簡略化された PNRP API では、名前とアドレスを登録するためにクラウドを明示的に指定することはありません。PNRP コンポーネントは、参加する適切なクラウドと、クラウド内で公開するアドレスを、自動的に決定ます。</span><span class="sxs-lookup"><span data-stu-id="e7c20-105">With the simplified PNRP API, clouds are not explicitly specified to register the name and addresses; the PNRP component automatically determines the appropriate clouds to join and the addresses to publish within the clouds.</span></span>  
  
 <span data-ttu-id="e7c20-106">Windows Vista の非常に簡略化された PNRP 名前解決では、Windows Sockets 関数 getaddrinfo() に PNRP 名が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="e7c20-106">For highly simplified PNRP name resolution in Windows Vista, PNRP names are now integrated into the getaddrinfo() Windows Sockets function.</span></span> <span data-ttu-id="e7c20-107">PNRP を使って名前を IPv6 アドレスに変換する場合、getaddrinfo() 関数を使って完全修飾ドメイン名 (FQDN) name.prnp.net を解決できます。ここで name は解決されるピア名です。</span><span class="sxs-lookup"><span data-stu-id="e7c20-107">To use PNRP to resolve a name to an IPv6 address, applications can use the getaddrinfo() function to resolve the Fully Qualified Domain Name (FQDN) name.prnp.net, in which name is peer name being resolved.</span></span> <span data-ttu-id="e7c20-108">pnrp.net ドメインは、PNRP 名前解決のために Windows Vista で予約されているドメインです。</span><span class="sxs-lookup"><span data-stu-id="e7c20-108">The pnrp.net domain is a reserved domain in Windows Vista for PNRP name resolution.</span></span>  
  
 <span data-ttu-id="e7c20-109">PeerToPeer アプリケーション間でのメッセージの受け渡しは、依然として PeerChannel や WCF の[大規模データとストリーミング](../wcf/feature-details/large-data-and-streaming.md)などの、基盤のアーキテクチャによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="e7c20-109">Message passing between PeerToPeer applications is still handled by underlying architectures such as PeerChannel and WCF [Large Data and Streaming](../wcf/feature-details/large-data-and-streaming.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7c20-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="e7c20-110">See also</span></span>

- <xref:System.Net.PeerToPeer>
