---
title: ランタイム情報 ETW イベント
ms.date: 03/30/2017
helpviewer_keywords:
- runtime information events [.NET Framework]
- ETW, runtime information events
ms.assetid: 68b4edbc-7f3b-45f6-ab75-4fd066d6af9a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6ab3844b293d09cec02236fb9befd836aa4113ea
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046226"
---
# <a name="runtime-information-etw-events"></a>ランタイム情報 ETW イベント
これらの ETW イベントは、SKU、バージョン番号、ランタイムのアクティブ化の方法、起動時に使用されたコマンド ライン パラメーター、GUID (該当する場合) などのランタイムに関する情報をログに記録します。 1 つのプロセスで複数のランタイムが実行されている場合は、これらのイベントの情報 (ClrInstanceID) によって、ランタイムのあいまいさを解消できます。  
  
 次の表に、2 つのランタイム情報イベントを示します。 これらのイベントは、任意のキーワードまたはマスクで発生させることができます (詳細については、「 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md)」を参照してください)。  
  
|イベント|イベント ID|プロバイダー|説明|  
|-----------|--------------|--------------|-----------------|  
|`RuntimeInformationEvent`|187|CLRRuntime|ランタイムが読み込まれたときに発生します。|  
|`RuntimeInformationDCStart`|187|CLRRundown|読み込まれているランタイムを列挙します。|  
  
 次の表にイベント データを示します。  
  
|フィールド名|データ型|説明|  
|----------------|---------------|-----------------|  
|ClrInstanceID|win:UInt16|CLR または CoreCLR のインスタンスの一意の ID。|  
|Sku|win:UInt16|1 – デスクトップ CLR。<br /><br /> 2 – CoreCLR。|  
|BclVersion – メジャー バージョン|win:UInt16|mscorlib.dll のメジャー バージョン。|  
|BclVersion – マイナー バージョン|win:UInt16|mscorlib.dll のマイナー バージョン番号。|  
|BclVersion – ビルド番号|win:UInt16|mscorlib.dll のビルド番号。|  
|BclVersion – QFE|win:UInt16|mscorlib.dll の修正プログラムのバージョン番号。|  
|VMVersion – メジャー バージョン|win:UInt16|clr.dll または coreclr.dll (SKU によって決まる) のバージョン。|  
|VMVersion – マイナー バージョン|win:UInt16|clr.dll または coreclr.dll (SKU によって決まる) のマイナー バージョン。|  
|VMVersion – ビルド番号|win:UInt16|clr.dll または coreclr.dll のビルド番号。|  
|VMVersion – QFE|win:UInt16|clr.dll または coreclr.dll の修正プログラムのバージョン番号。|  
|StartupFlags|win:UInt32|mscoree.h で定義された起動フラグ。|  
|StartupMode|win:UInt8|0x01 - マネージド実行可能ファイル。<br /><br /> 0x02 - ホストされた CLR。<br /><br /> 0x04 - C++ マネージド相互運用。<br /><br /> 0x08 - COM アクティブ化。<br /><br /> 0x10 - その他。|  
|実行中|win:UnicodeString|StartupMode=0x01 の場合のみ null 以外。|  
|ComObjectGUID|win:GUID|StartupMode=0x08 の場合のみ null 以外。|  
|RuntimeDLLPath|win:UnicodeString|プロセスに読み込まれた CLR .dll ファイルへのパス。|  
  
## <a name="see-also"></a>関連項目

- [CLR ETW イベント](clr-etw-events.md)
