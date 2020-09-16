---
title: アプリケーションの構成
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 04ddce4755ce30b7d46c3bd54024af08361d96ad
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "90536082"
---
# <a name="configuring-your-application"></a>アプリケーションの構成
Windows Communication Foundation (WCF) では、.NET 構成システムを使用して、コンピューターとアプリケーションの両方のスコープでサービスを構成できます。  
  
 WCF によって定義された構成設定は、 `<system.serviceModel>` セクショングループにあります。 WCF サービスを構成する方法の詳細については、次のトピックを参照してください。  
  
- [サービスの構成](../configuring-services.md)  
  
- [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 アプリケーション定義の構成設定は、`<appSettings>` セクション グループで定義されています。 .NET 構成ファイルのアプリケーション設定の詳細については、「」を参照してください [\<appSettings>](/previous-versions/dotnet/netframework-4.0/ms228154(v=vs.100)) 。  
  
## <a name="using-the-configuration-editor"></a>構成エディターの使用  
 WCF [構成エディターツール (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md) を使用すると、管理者および開発者は、グラフィカルユーザーインターフェイスを使用して wcf サービスの構成設定を作成および変更できます。 このツールを使用すると、XML 構成ファイルを直接編集することなく、WCF のバインディング、動作、サービス、および診断の設定を管理できます。  
  
## <a name="editing-configuration-files-in-visual-studio"></a>Visual Studio の構成ファイルの編集  
 Visual Studio で WCF サービスプロジェクトの構成ファイルを編集するには、 **ソリューションエクスプローラー** で右クリックし、[ **Wcf 構成の編集** ] コンテキストメニュー項目を選択します。 これにより、 [構成エディターツール (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md)が起動します。  
  
> [!NOTE]
> **ソリューションエクスプローラー**で Wcf Web サービスプロジェクトの構成ファイルを右クリックして編集する場合は、[ **Wcf 構成の編集**] コンテキストメニュー項目が表示されないことに注意してください。 この問題を回避するには、[ **ツール** ] メニューをクリックし、[ **WCF サービス構成エディター**] を選択します。 その後、構成ファイルを右クリックし、[ **WCF 構成の編集** ] コンテキストメニュー項目を使用できます。  
  
## <a name="see-also"></a>関連項目

- [構成エディター ツール (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md)
- [サービスの構成](../configuring-services.md)
- [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md)
