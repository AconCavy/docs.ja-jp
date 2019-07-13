---
title: .NET アプリケーションの配置をサポートするための Firefox のアドオン
ms.date: 03/30/2017
helpviewer_keywords:
- Firefox add-ons for .NET application deployment
- WPF plug-in for Firefox
- .NET application deployment [WPF], deploying with Firefox add-ons
- .NET Framework Assistant for Firefox
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
ms.openlocfilehash: 39f4548bfe9e505c1369a0de8262560070fd6221
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833915"
---
# <a name="firefox-add-ons-to-support-net-application-deployment"></a>.NET アプリケーションの配置をサポートするための Firefox のアドオン
Firefox と、.NET Framework Assistant for Firefox プラグイン Windows Presentation Foundation (WPF) を有効にする[!INCLUDE[TLA#tla_winfxwebapp#plural](../../../../includes/tlasharptla-winfxwebappsharpplural-md.md)]、loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、Mozilla Firefox ブラウザーを使用する ClickOnce アプリケーションとします。  
  
## <a name="wpf-plug-in-for-firefox"></a>WPF Firefox プラグイン  
 有効にした WPF プラグイン Firefox[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]や loose[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]に移動して、または Firefox ブラウザーで HTML IFRAME の最上位で実行するファイル。 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]は、 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Web サーバーにパブリッシュして内で起動できるアプリケーションには、ブラウザーがサポートされています。 Loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] XAML 専用ファイルに移動し、XML ファイルと同様に、サポートされているブラウザーに表示されることです。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]プラグインの Firefox は、.NET Framework 3.5 でインストールします。 Window 7 は、.NET Framework 3.5 が含まれていますには含まれません、 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Firefox 用のプラグイン。 インストールすることはできません、 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Windows 7、Firefox 用のプラグイン。  
  
 .NET Framework 4 を含まない、 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Firefox 用のプラグイン。 ただし、.NET Framework 3.5 と .NET Framework 4 の両方がインストールされている場合、WPF の Firefox プラグインは、.NET Framework 3.5 と共にインストールされます。 そのため、WPF ホストは、framework の正しいバージョンを読み込むため、.NET Framework 4 アプリケーションは実行されます。 詳細については、次を参照してください。 [WPF ホスト (PresentationHost.exe)](wpf-host-presentationhost-exe.md)します。  
  
## <a name="net-framework-assistant-for-firefox"></a>.NET Framework Assistant for Firefox  
 Firefox ブラウザーから実行するスタンドアロンの ClickOnce アプリケーションを .NET Framework Assistant for Firefox にできます。 .NET Framework Assistant の Firefox 関数、Firefox ブラウザーの前後にインストールされているときに同じです。 Firefox ブラウザーを起動し、.NET Framework 3.5 SP1 がインストールされている、Firefox を検索し、Firefox の .NET Framework Assistant をインストールします。 ユーザーは、.NET Framework Assistant for Firefox では、次の操作を構成できます。  
  
- ClickOnce アプリケーションを実行する前に確認します。  
  
- インストールされているすべてのバージョンの .NET Framework または最新バージョンのみを報告します。  
  
 Firefox 用 .NET Framework Assistant は、.NET Framework 3.5 SP1 に含まれています。 Firefox 用の .NET Framework Assistant の削除方法の詳細については、次を参照してください。 [Firefox 用の .NET Framework Assistant の削除方法](https://go.microsoft.com/fwlink/?LinkId=177944)します。  
  
## <a name="see-also"></a>関連項目

- [WPF アプリケーションの配置](deploying-a-wpf-application-wpf.md)
- [WPF XAML ブラウザー アプリケーションの概要](wpf-xaml-browser-applications-overview.md)
- [Firefox に対応した WPF プラグインがインストールされているかどうかを確認する](how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)
