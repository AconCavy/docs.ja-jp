---
title: WCF サービス ホストの自動起動の制御
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 2033e693003d0b50bcdada428e4a5f451b3ad67e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255079"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>WCF サービス ホストの自動起動の制御

複数のプロジェクトを含む同じ Visual Studio ソリューションで別のプロジェクトをデバッグするときに、WCF サービスライブラリプロジェクトの Windows Communication Foundation (WCF) サービスホスト (WcfSvcHost.exe) の自動起動機能を制御できます。  
  
 これを行うには、 **ソリューションエクスプローラー** で Wcf サービスプロジェクトを右クリックし、[ **プロパティ**] をクリックして、[ **wcf オプション** ] タブをクリックします。既定では、[ **同じソリューションで別のプロジェクトをデバッグするときに WCF サービスホストを開始する** ] チェックボックスがオンになっています。 このチェックボックスをオフにすると、同じソリューションで別のプロジェクトがデバッグされるときに、この特定のプロジェクトの WCF サービスホストが起動されないようにすることができます。  
  
 この動作は、F5 キーによるデバッグや、このプロジェクトへのサービス参照の追加の機能には影響を与えません。  
  
 このオプションは、次のプロジェクトで使用できます。  
  
- WCF サービスライブラリプロジェクト。  
  
- シーケンシャル ワークフロー サービス ライブラリ プロジェクト  
  
- ステート マシン ワークフロー サービス ライブラリ プロジェクト  
  
- 配信サービス ライブラリ プロジェクト  
  
## <a name="see-also"></a>関連項目

- [WCF サービス ホスト (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
