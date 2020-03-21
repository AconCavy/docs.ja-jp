---
title: グラフィックス レンダリングのレジストリ設定
ms.date: 03/30/2017
helpviewer_keywords:
- rendering graphics [WPF], registry settings
- rendering graphics [WPF]
- rendering graphics [WPF], troubleshooting
- troubleshooting graphics rendering [WPF]
- graphics [WPF], rendering
ms.assetid: f4b41b42-327d-407c-b398-3ed5f505df8b
ms.openlocfilehash: 642dfdd784af4b85672cf5b0c8e60079763f4c47
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112285"
---
# <a name="graphics-rendering-registry-settings"></a>グラフィックス レンダリングのレジストリ設定
ここでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションに影響を与える [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] グラフィックス レンダリングのレジストリ設定の概要を示します。  

<a name="overview"></a>
## <a name="when-to-use-graphics-rendering-registry-settings"></a>グラフィックス レンダリングのレジストリ設定を使用する場合  
 これらのレジストリ設定は、トラブルシューティング、デバッグ、製品サポートの目的で提供されています。 レジストリの変更はすべての [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションに影響するため、アプリケーションでは、これらのレジストリ キーを自動的に変更したり、インストール時に変更したりしないでください。  
  
<a name="xpdmandwddm"></a>
## <a name="what-are-xpdm-and-wddm"></a>XPDM と WDDM について  
 グラフィックス レンダリングのレジストリの一部の設定は、ビデオ カードが XPDM ドライバーまたは WDDM ドライバーのどちらを使用するかによって既定値が異なります。 XPDM は、Windows XP ディスプレイ ドライバー モデルと WDDM は、Windows ディスプレイ ドライバー モデルです。 WDDM は、Windows Vista および Windows 7 を実行しているコンピューターで使用できます。 XPDM は、Windows Vista、Windows XP、および Windows サーバー 2003 を実行しているコンピュータで使用できます。 WDDM の詳細については[、「Windows ディスプレイ ドライバー モデル (WDDM) デザイン ガイド](/windows-hardware/drivers/display/windows-vista-display-driver-model-design-guide)」を参照してください。  
  
<a name="registry_settings"></a>
## <a name="registry-settings"></a>レジストリ設定  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の描画を制御するためのレジストリ設定が 4 つあります。  
  
|設定|説明|  
|-------------|-----------------|  
|**Disable Hardware Acceleration Option (ハードウェア高速化オプションを無効にする)**|ハードウェア高速化を有効にするかどうかを指定します。|  
|**Maximum Multisample Value (最大マルチサンプル値)**|アンチエイリアシング 3D コンテンツのマルチサンプリングの度合いを指定します。|  
|**Required Video Driver Date Setting (ビデオ ドライバーの日付設定が必須)**|2004 年 11 月より前にリリースされたドライバーについて、ハードウェア高速化を無効にするかどうかを指定します。|  
|**Use Reference Rasterizer Option (リファレンス ラスタライザー オプションを使用する)**|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でリファレンス ラスタライザーを使用するかどうかを指定します。|  
  
 これらの設定には、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] レジストリ設定の参照方法を認識する外部構成ユーティリティを使用してアクセスできます。 これらの設定は、Windows レジストリ エディタを使用して値に直接アクセスすることによって作成または変更することもできます。  
  
<a name="disablehardwareacceleration"></a>
## <a name="disable-hardware-acceleration-option"></a>Disable Hardware Acceleration Option (ハードウェアの高速化オプションを無効にする)  
  
|レジストリ キー|値の型|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\DisableHWAcceleration`|DWORD|  
  
 **[disable hardware acceleration option]** (ハードウェアの高速化オプションを無効にする) を使用すると、デバッグとテストの目的でハードウェアの高速化を無効にできます。 アプリケーションにレンダリング アーティファクトが見られる場合は、ハードウェアの高速化を無効にしてみてください。 アーティファクトが消える場合は、ビデオ ドライバーの問題である可能性があります。  
  
 **[disable hardware acceleration option]** (ハードウェアの高速化オプションを無効にする) は、0 か 1 の DWORD 値です。 値が 1 の場合、ハードウェアの高速化は無効になります。 値が 0 の場合、システムがハードウェアの高速化の要件を満たしていれば、ハードウェアの高速化が有効になります。詳しくは、「[グラフィックスの描画層](../advanced/graphics-rendering-tiers.md)」をご覧ください。  
  
<a name="maxmultisample"></a>
## <a name="maximum-multisample-value"></a>Maximum Multisample Value (最大マルチサンプル値)  
  
|レジストリ キー|値の型|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\MaxMultisampleType`|DWORD|  
  
 **最大マルチサンプル値**を使用すると、3D コンテンツのアンチエイリアスの最大量を調整できます。 このレベルを使用して、Windows Vista で 3D アンチエイリアスを無効にします。  
  
 **[maximum multisample value]** (最大マルチサンプル値) は 0 から 16 の DWORD 値です。 値 0 は、3D コンテンツのマルチサンプルアンチエイリアスを無効にすることを指定し、16 の値は、ビデオ カードでサポートされている場合、最大 16 倍のマルチサンプル アンチエイリアスを使用しようとします。 XPDM ドライバを使用するコンピュータでこのレジストリ キー値を設定すると、アプリケーションが大量のビデオ メモリを使用し、3D レンダリングのパフォーマンスが低下し、レンダリング エラーや安定性が生じる可能性があります。問題。  
  
 このレジストリ キーを設定しないと、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の既定値は、XPDM ドライバーでは 0、WDDM ドライバーでは 4 になります。  
  
<a name="requiredvideodriverdatesetting"></a>
## <a name="required-video-driver-date-setting"></a>Required Video Driver Date Setting (ビデオ ドライバーの日付設定が必須)  
  
|レジストリ キー|値の型|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\RequiredVideoDriverDate`|String|  
  
 2004 年 11 月、マイクロソフトはドライバ テスト ガイドラインの新しいバージョンをリリースしました。この日付以降に書かれたドライバは、より良い安定性を提供します。 既定では、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、これらのドライバーに対してはハードウェアの高速化パイプラインを使用し、この日より前に公開された XPDM ドライバーについてはソフトウェア レンダリングを使用します。  
  
 **[required video driver date setting]** (ビデオ ドライバーの日付設定が必須) を使用すると、XPDM ドライバーに対して最低限の代わりの日付を指定できます。 使用するビデオ ドライバーが十分に安定して [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] をサポートすることが確実な場合にのみ、2004 年 11 月より前の日付を指定してください。  
  
 必須のビデオ ドライバーの設定では、次の形式の文字列を使用します。  
  
| |  
|-|  
|*YYYY* `/` *MM* `/` *DD*|  
  
 *YYYY* は 4 桁の年、*MM* は 2 桁の月、*DD* は 2 桁の日です。 この値を設定しないと、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は必要なビデオ ドライバーの日付として 2004 年 11 月を使用します。  
  
<a name="usereferencerasterizeroption"></a>
## <a name="use-reference-rasterizer-option"></a>Use Reference Rasterizer Option (リファレンス ラスタライザー オプションを使用する)  
  
|レジストリ キー|値の型|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\UseReferenceRasterizer`|DWORD|  
  
 **参照ラスタライザーを使用するオプション**を使用すると[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、デバッグ用にシミュレートされたハードウェア レンダリング[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]モードに強制的に移行できます。  
  
 リファレンス ラスタライザーは非常に低速ですが、ビデオ ドライバーをバイパスし、ドライバーの問題によって発生するレンダリングの問題を回避します。 このため、リファレンス ラスタライザーを使用すると、レンダリングの問題の原因がビデオ ドライバーかどうかを判断できます。 d3dref9.dll ファイルは、システム パス内の場所やアプリケーションのローカル ディレクトリなど、アプリケーションがアクセスできる場所に存在する必要があります。  
  
 **[use reference rasterizer option]** (リファレンス ラスタライザー オプションを使用する) は、DWORD 値を受け取ります。 値 0 は、リファレンス ラスタライザーを使用しないことを示します。 他の 0 以外の値は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] にリファレンス ラスタライザーの使用を強制します。  
  
## <a name="see-also"></a>関連項目

- [グラフィックスの描画層](../advanced/graphics-rendering-tiers.md)
- [WPF グラフィックス レンダリングの概要](wpf-graphics-rendering-overview.md)
