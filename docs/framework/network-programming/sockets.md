---
title: ソケット
ms.date: 03/30/2017
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- Windows Sockets
- sockets, about sockets
- Socket class, about Socket class
- sockets
- requesting data from Internet, sockets
- network, sockets
- receiving data, sockets
- protocols, sockets
- Internet, sockets
ms.assetid: 10d22735-bd37-42c1-a2be-c1932f979a7d
ms.openlocfilehash: 4a1b18f2c31bf8dad8cf32e2e5205cf3008e7b18
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136046"
---
# <a name="sockets"></a>ソケット
<xref:System.Net.Sockets> 名前空間には、Windows ソケット インターフェイスのマネージド実装が含まれます。 <xref:System.Net> 名前空間のその他すべてのネットワーク アクセス クラスは、ソケットのこの実装の上に構築されます。  
  
 .NET Framework <xref:System.Net.Sockets.Socket> クラスは、Winsock32 API が提供するソケット サービスのマネージ コード版です。 ほとんどの場合、**Socket** クラス メソッドはネイティブ Win32 の該当メソッドにデータをマーシャリングし、必要なセキュリティ チェックがあればそれを処理します。  
  
 **Socket** クラスは、同期と非同期という 2 つの基本モードに対応しています。 同期モードの場合、ネットワーク操作 (<xref:System.Net.Sockets.Socket.Send%2A> や <xref:System.Net.Sockets.Socket.Receive%2A> など) を実行する関数の呼び出しは、操作の完了を待ってから、呼び出し元のプログラムにコントロールを返します。 非同期モードの場合、このような呼び出しはすぐに返されます。  
  
## <a name="see-also"></a>関連項目

- [方法: ソケットを作成する](../../../docs/framework/network-programming/how-to-create-a-socket.md)

- [アプリケーション プロトコルの使用](../../../docs/framework/network-programming/using-application-protocols.md)
