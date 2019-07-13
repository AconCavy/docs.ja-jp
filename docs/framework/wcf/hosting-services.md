---
title: ホスティング サービス
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF]
ms.assetid: 192be927-6be2-4fda-98f0-e513c4881acc
ms.openlocfilehash: b1a0a07876e9cc111e8c5eef56f208d7bf2cb49f
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487708"
---
# <a name="hosting-services"></a>ホスティング サービス
アクティブにするには、サービスを作成してそのコンテキストと有効期間を制御するランタイム環境内で、サービスをホストする必要があります。 マネージ コードをサポートする任意の Windows プロセスで実行するのには、Windows Communication Foundation (WCF) サービスが設計されています。  
  
 WCF には、サービス指向アプリケーションを構築するための統一プログラミング モデルが用意されています。 このプログラミング モデルには一貫性があり、サービスが展開されるランタイム環境に影響されません。 これは実際には、ホスト オプションにかかわらず、サービスのコードがほぼ同じになることを意味しています。  
  
 これらのホスト オプションの範囲は、コンソール アプリケーション内部での実行から、Windows サービスのようなサーバー環境、インターネット インフォメーション サービス (IIS) または Windows プロセス アクティブ化サービス (WAS) で管理されるワーカー プロセス内での実行までさまざまです。 開発者は、サービスの展開要件を満たすホスト環境を選択します。 このような要件は、アプリケーションを展開するプラットフォーム、メッセージの送受信を行うトランスポート、適切な可用性を保証するために必要なプロセスのリサイクルや管理、その他、管理上または信頼性上の要件から導き出されます。 ホスト オプションの情報とガイドラインについて、次のセクションで説明します。  
  
## <a name="hosting-options"></a>ホスト オプション  
  
#### <a name="self-hosting-in-a-managed-application"></a>マネージド アプリケーションにおける自己ホスト  
 任意のマネージ アプリケーションでは、WCF サービスをホストすることができます。 これは、展開に必要なインフラストラクチャが最小限になるため、最も柔軟なオプションです。 マネージド アプリケーション コード内にサービスのコードを埋め込み、続いて <xref:System.ServiceModel.ServiceHost> のインスタンスを作成して開き、サービスを有効にします。 詳細については、「[方法 :マネージ アプリケーションで WCF サービスをホスト](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)します。  
  
 このオプションは、2 つの一般的なシナリオを有効にします。コンソール アプリケーションと Windows Presentation Foundation (WPF) または Windows フォーム (WinForms) に基づいてなどのリッチ クライアント アプリケーション内で実行される WCF サービス。 コンソール アプリケーション内部の WCF サービス ホストは、アプリケーションの開発フェーズ中に一般的に便利です。 コンソール アプリケーションにより、アプリケーション内部で起こっている状況を見極めるための情報のデバッグやトレースが容易になり、新しい場所にアプリケーションをコピーして移動することも簡単に行うことができます。 このホスト オプションでは、外部と通信するために、WPF と WinForms アプリケーションなどのリッチ クライアント アプリケーションを簡単にします。 たとえば、WPF を使用して、ユーザー インターフェイスともその他のクライアントに接続して、情報を共有できるようにする WCF サービスをホストするピア ツー ピア コラボレーション クライアントです。  
  
#### <a name="managed-windows-services"></a>マネージド Windows サービス  
 このホスト オプションがいるため、サービスのプロセス有効期間はサービス コントロール マネージャー (SCM) によって制御されます (旧 NT サービス) をマネージ Windows サービスとして、WCF サービスをホストするアプリケーション ドメイン (AppDomain) に登録することで構成されていますWindows サービスです。 自己ホスト オプションと同様、この種類のホスト環境では、ホスト コードをアプリケーションの一部として記述する必要があります。 サービスはから継承することによって、両方の Windows サービスとは、WCF サービスとしてを実装は、<xref:System.ServiceProcess.ServiceBase>クラスだけでなく、wcf サービス コントラクト インターフェイス。 次に <xref:System.ServiceModel.ServiceHost> を作成し、オーバーライドされた <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> メソッドで開き、オーバーライドされた <xref:System.ServiceProcess.ServiceBase.OnStop> メソッドで閉じます。 また、 <xref:System.Configuration.Install.Installer> から継承されるインストーラー クラスも実装し、プログラムが Installutil.exe ツールによって Windows サービスとしてインストールされるようにする必要があります。 詳細については、「[方法 :マネージ Windows サービスでの WCF サービスをホスト](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)します。 マネージ Windows サービスのホスト オプションで有効になっているシナリオがないメッセージがアクティブ化の安全な環境で IIS の外部でホストされている実行時間の長い WCF サービスのです。 サービスの有効期限は代わりにオペレーティング システムによって制御されます。 このホスト オプションは Windows のすべてのバージョンで使用できます。  
  
#### <a name="internet-information-services-iis"></a>インターネット インフォメーション サービス (IIS)  
 IIS ホスト オプションを使用して、ASP.NET 統合は、プロセス リサイクル、アイドル シャット ダウン、処理状況の監視、およびメッセージに基づくアクティベーションなど、これらのテクノロジを提供する機能を使用します。 [!INCLUDE[wxp](../../../includes/wxp-md.md)] および [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] オペレーティング システムでは、高可用性と高スケーラビリティが求められる Web サービス アプリケーションのホストには、このオプションが適切なソリューションとなります。 IIS では、顧客がエンタープライズ クラスのサーバー製品に求める統合された管理性も提供されます。 このホスト オプションでは、IIS が正しく構成されている必要がありますが、アプリケーションの一部としてホスト コードを書く必要はありません。 IIS を構成する方法の詳細については、WCF サービスをホストしている参照してください[方法。IIS で WCF サービスをホスト](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)します。  
  
 IIS でホストされるサービスは HTTP トランスポートしか使用できません。 IIS 5.1 の実装では、 [!INCLUDE[wxp](../../../includes/wxp-md.md)]にいくつかの制限がありました。 WCF サービスの上の IIS 5.1 によって提供されるメッセージに基づくアクティベーション[!INCLUDE[wxp](../../../includes/wxp-md.md)]からの通信にポート 80 を使用して同じコンピューター上の他の自己ホスト型 WCF サービスをブロックします。 WCF サービスの IIS 6.0 でホストされている場合は、他のアプリケーションと同じ AppDomain/アプリケーション プール/ワーカー プロセスで実行できます[!INCLUDE[ws2003](../../../includes/ws2003-md.md)]します。 IIS 6.0 で IIS 5.1 とは異なり、同じマシンで実行されている他の自己ホスト型 WCF サービスとポート 80 を共有できます WCF および IIS 6.0 は、カーネル モードの HTTP スタック (HTTP.sys) を使用するためです。  
  
#### <a name="windows-process-activation-service-was"></a>Windows プロセス アクティブ化サービス (WAS)  
 Windows プロセス アクティブ化サービス (WAS) とは、 [!INCLUDE[lserver](../../../includes/lserver-md.md)] でも使用できる [!INCLUDE[wv](../../../includes/wv-md.md)]用の新しいプロセス アクティブ化機構です。 使い慣れた IIS 6.0 プロセス モデル (アプリケーション プールとメッセージ ベースのプロセス アクティベーション) が保持され、アクティブ化から HTTP に対する依存関係を削除する機能 (迅速な障害保護、正常性監視、および再利用) などがこれをホストしています。アーキテクチャです。 IIS 7.0 では、WAS を使用して、HTTP 経由でメッセージ ベースのアクティブ化を実現します。 その他の WCF コンポーネントは、WCF がサポートするその他のプロトコル経由で、TCP、MSMQ、名前付きパイプなど、メッセージ ベースのライセンス認証を提供する WAS にも接続します。 これにより、IIS のプロセスのリサイクル、迅速な障害保護、一般的な構成システムなど、これまで HTTP ベースのアプリケーションのみで利用可能だった IIS 機能を、通信プロトコルを使用するアプリケーションでも使用できるようになりました。  
  
 このホスト オプションでは、WAS が正しく構成されている必要がありますが、アプリケーションの一部としてホスト コードを書く必要はありません。 構成する方法の詳細についてをホストしていたは、次を参照してください。[方法。WAS で WCF サービスをホスト](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)します。  
  
## <a name="choosing-a-hosting-environment"></a>ホスト環境の選択  
 次の表に、各ホスト オプションに関連する主な利点とシナリオの要点をまとめます。  
  
|ホスト環境|一般的なシナリオ|主な利点と制限|  
|-------------------------|----------------------|----------------------------------|  
|マネージド アプリケーション ("自己ホスト")|コンソール アプリケーションを開発時に使用します。<br />豊富な WinForm と WPF クライアント アプリケーションがサービスにアクセスします。|柔軟です。<br />展開が容易です。<br />-サービスのエンタープライズ ソリューションです。|  
|Windows サービス (従来 NT サービスと呼ばれていたもの)|-IIS の外部でホストされている実行時間の長い WCF サービス。|サービス プロセスの有効期間がないメッセージがアクティブ化、オペレーティング システムによって制御されます。<br />-Windows のすべてのバージョンでサポートされています。<br />-セキュリティで保護された環境。|  
|IIS 5.1, IIS 6.0|-実行されている WCF サービス サイド バイ サイドで ASP.NET コンテンツの HTTP プロトコルを使用して、インターネット上。|-プロセスのリサイクルします。<br />-アイドル シャット ダウンします。<br />-正常性の監視を処理します。<br />-メッセージ ベースのアクティブ化します。<br />-HTTP のみ。|  
|Windows プロセス アクティブ化サービス (WAS)|-さまざまなトランスポート プロトコルを使用してインターネットに IIS をインストールしなくても、WCF サービスを実行します。|IIS は必要ありません。<br />-プロセスのリサイクルします。<br />-アイドル シャット ダウンします。<br />-正常性の監視を処理します。<br />-メッセージ ベースのアクティブ化します。<br />-HTTP、TCP、名前付きパイプ、および MSMQ で動作します。|  
|IIS 7.0|-ASP.NET コンテンツを持つ WCF サービスを実行します。<br />-さまざまなトランスポート プロトコルを使用して、インターネット上の WCF サービスを実行します。|-が利点があります。<br />-ASP.NET と IIS のコンテンツと統合されています。|  
  
 ホスト環境の選択は、その展開先の Windows のバージョン、メッセージの送信に必要なトランスポート、および必要となるプロセスとアプリケーション ドメインのリサイクルの種類に依存します。 次の表に、これらの要件に関連するデータをまとめます。  
  
|ホスト環境|プラットフォームの可用性|サポートされるトランスポート|プロセスと AppDomain のリサイクル|  
|-------------------------|---------------------------|--------------------------|-------------------------------------|  
|マネージド アプリケーション ("自己ホスト")|[!INCLUDE[wxp](../../../includes/wxp-md.md)], [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], [!INCLUDE[wv](../../../includes/wv-md.md)],<br /><br /> [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP、<br /><br /> net.tcp、<br /><br /> net.pipe、<br /><br /> net.msmq|いいえ|  
|Windows サービス (従来 NT サービスと呼ばれていたもの)|[!INCLUDE[wxp](../../../includes/wxp-md.md)], [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], [!INCLUDE[wv](../../../includes/wv-md.md)],<br /><br /> [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP、<br /><br /> net.tcp、<br /><br /> net.pipe、<br /><br /> net.msmq|いいえ|  
|IIS 5.1|[!INCLUDE[wxp](../../../includes/wxp-md.md)]|HTTP|[はい]|  
|IIS 6.0|[!INCLUDE[ws2003](../../../includes/ws2003-md.md)]|HTTP|[はい]|  
|Windows プロセス アクティブ化サービス (WAS)|[!INCLUDE[wv](../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP、<br /><br /> net.tcp、<br /><br /> net.pipe、<br /><br /> net.msmq|[はい]|  
  
 信頼されていないホストからサービスや拡張機能を実行すると、セキュリティが損なわれるので注意してください。 また、偽装して <xref:System.ServiceModel.ServiceHost> を開くと、アプリケーションは、ユーザーの <xref:System.Security.Principal.WindowsIdentity> をキャッシュするなどして、ユーザーがログオフしていないことを確認する必要があります。  
  
## <a name="see-also"></a>関連項目

- [システム要件](../../../docs/framework/wcf/wcf-system-requirements.md)
- [基本的なプログラミング ライフサイクル](../../../docs/framework/wcf/basic-programming-lifecycle.md)
- [サービス コントラクトの実装](../../../docs/framework/wcf/implementing-service-contracts.md)
- [方法: IIS で WCF サービスをホストします。](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
- [方法: WAS で WCF サービスをホストします。](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)
- [方法: マネージ Windows サービスでの WCF サービスをホストします。](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)
- [方法: マネージ アプリケーションで WCF サービスをホストします。](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
