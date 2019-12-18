---
title: WCF 開発者向けの gRPC-gRPC の負荷分散
description: GRPC サービスを使用するロードバランサーの選択。
ms.date: 09/02/2019
ms.openlocfilehash: 215c0983146bbf9168f01956d64733f80cea6faf
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711175"
---
# <a name="load-balancing-grpc"></a>GRPC の負荷分散

GRPC アプリケーションの一般的な展開には、サービスの同じインスタンスが多数含まれており、復元性と水平方向のスケーラビリティが提供されます。 負荷分散では、これらのインスタンスに着信要求を分散して、使用可能なすべてのリソースを完全に使用します。 この負荷分散をクライアントに対して非表示にするには、プロキシロードバランサーサーバーを使用してクライアントからの要求を処理し、バックエンドインスタンスにルーティングするのが一般的です。

ロードバランサーは、操作対象の*レイヤー*に応じて分類されます。 レイヤー4のロードバランサーは、TCP ソケット、接続、パケットなどを使用して、*トランスポート*レベルで動作します。 レイヤー7のロードバランサーは、*アプリケーション*レベルで動作します。具体的には、grpc アプリケーションの HTTP/2 要求を処理します。

## <a name="l4-load-balancers"></a>L4 ロードバランサー

L4 ロードバランサーは、クライアントからの TCP 接続要求を受け入れ、いずれかのバックエンドインスタンスへの別の接続を開いて、実際の処理を行わずに2つの接続間でデータをコピーします。 L4 は優れたパフォーマンスと短い待機時間を提供しますが、制御やインテリジェンスはほとんどありません。 クライアントが接続を開いたままにしている限り、すべての要求は同じバックエンドインスタンスに送られます。

 [Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/)は、L4 ロードバランサーの一例です。

## <a name="l7-load-balancers"></a>L7 ロードバランサー

L7 ロードバランサーは、クライアントが接続を保持する時間に関係なく、受信 HTTP/2 要求を解析し、要求ごとにバックエンドインスタンスに渡します。

L7 ロードバランサーの例:

- [NGINX](https://www.nginx.com/)
- [HAProxy](https://www.haproxy.com/)
- [Traefik](https://traefik.io/)

目安として、L7 ロードバランサーは gRPC やその他の HTTP/2 アプリケーションに最適な選択肢です (通常は HTTP アプリケーションの場合)。 L4 ロードバランサーは gRPC アプリケーションで*動作*しますが、主に低待機時間と低いオーバーヘッドが重要な場合に役立ちます。

> [!IMPORTANT]
> このドキュメントの執筆時点では、一部の L7 ロードバランサーは、ヘッダーの末尾など、gRPC サービスで必要とされる HTTP/2 仕様のすべての部分をサポートしていません。

TLS 暗号化を使用している場合、ロードバランサーは TLS 接続を終了し、暗号化されていない要求をバックエンドアプリケーションに渡すことができます。また、暗号化された要求をに渡すこともできます。 どちらの場合も、ロードバランサーは、サーバーの公開キーと秘密キーを使用して構成する必要があります。これにより、処理要求の暗号化が解除されます。

バックエンドサービスで HTTP/2 要求を処理するように構成する方法については、お使いのロードバランサーのドキュメントを参照してください。

## <a name="load-balancing-within-kubernetes"></a>Kubernetes 内での負荷分散

Kubernetes の内部サービス間の負荷分散の詳細については[、サービスメッシュに関するセクション](service-mesh.md)を参照してください。

>[!div class="step-by-step"]
>[前へ](service-mesh.md)
>[次へ](application-performance-management.md)