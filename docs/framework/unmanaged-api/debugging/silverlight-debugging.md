---
title: Silverlight デバッグ
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d20bc002e52c3c6a42b45c0d1c5d559e65dc52c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763664"
---
# <a name="silverlight-debugging"></a>Silverlight デバッグ
このセクションのトピックでは、Windows オペレーティング システム上または Macintosh プラットフォーム上で動作している Silverlight ベースのアプリケーションのデバッグをサポートするために共通言語ランタイム (CLR: Common Language Runtime) で提供される環境とインターフェイスについて説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [EnumerateCLRs 関数](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 プロセスで CLR を列挙するメカニズムを提供します。  
  
 [CloseCLREnumeration 関数](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 によって返されるハンドルの配列内にある有効な CLR 継続スタートアップ イベントを閉じ、 [EnumerateCLRs 関数](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)、ハンドルおよび文字列パス配列のメモリを解放します。  
  
 [CreateCoreClrDebugTarget 関数](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 プロセスおよびランタイムの列挙のためのリモート ターゲットへの接続を作成します。  
  
 [CreateCordbObject 関数](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 リモート プロセスでマネージド デバッグ セッションをインスタンス化するための機能を提供するデバッガー インターフェイスを作成します。  
  
 [CreateVersionStringFromModule 関数](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 対象プロセス内の CLR パスからバージョン文字列を作成します。  
  
 [CreateDebuggingInterfaceFromVersion 関数](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 返された CLR バージョン文字列を受け入れる[CreateVersionStringFromModule 関数](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)関数、および対応するデバッガー インターフェイスを返します。  
  
 [CoreClrDebugProcInfo 構造体](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 リモート コンピューターで実行されているプロセスを表します。  
  
 [CoreClrDebugRuntimeInfo 構造体](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 リモート コンピューター上のプロセスに読み込まれる CLR インスタンスを表します。  
  
 [GetStartupNotificationEvent 関数](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 指定された対象プロセスに読み込まれている任意の共通言語ランタイム (CLR: Common Language Runtime) によって通知されるイベント ハンドルを作成または開きます。  
  
 [ICoreClrDebugTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 プロセスおよびランタイムの列挙のためのリモート ターゲットへの接続を作成します。  
  
 [InitDbgTransportManager 関数](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 プロセスおよびランタイムの列挙のためにリモート ターゲットに接続するよう、トランスポート マネージャーを初期化します。  
  
 [ShutdownDbgTransportManager 関数](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 リモート ターゲット コンピューターへの接続のためにトランスポート マネージャーをシャットダウンします。  
  
## <a name="see-also"></a>関連項目

- [デバッグ コクラス](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ グローバル静的関数](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
- [列挙型のデバッグ](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [デバッグ構造体](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
