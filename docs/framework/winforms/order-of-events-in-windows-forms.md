---
title: Windows フォームのイベントの順序
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], order of
- focus event order
- application shutdown event order
- sequence [Windows Forms], of events
- validation events [Windows Forms], order of
- application startup event order
ms.assetid: e81db09b-4453-437f-b78a-62d7cd5c9829
ms.openlocfilehash: f581ca5ee1376251a593e7b8813ef4b0e0f41b64
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64655596"
---
# <a name="order-of-events-in-windows-forms"></a>Windows フォームのイベントの順序
Windows フォーム アプリケーションでイベントが発生する順序は、各イベントを順番に処理する必要がある開発者にとって重要な問題です。 フォームの構成要素を再描画するときなど、イベント処理に細心の注意が必要な状況では、実行時におけるイベントの正確な発生順序に気を配る必要があります。 このトピックでは、アプリケーションとコントロールの有効期間におけるいくつかの重要な段階での、イベントの順序について詳しく説明します。 特定の詳細については、マウス入力イベントの順序では、次を参照してください。 [Windows フォームにおけるマウス イベント](mouse-events-in-windows-forms.md)します。 Windows フォームのイベントの概要については、次を参照してください。[イベントの概要](events-overview-windows-forms.md)します。 イベント ハンドラーの構成の詳細については、次を参照してください。[イベント ハンドラーの概要](event-handlers-overview-windows-forms.md)します。  
  
## <a name="application-startup-and-shutdown-events"></a>アプリケーションのスタートアップ イベントとシャットダウン イベント。  
 <xref:System.Windows.Forms.Form> クラスおよび <xref:System.Windows.Forms.Control> クラスは、アプリケーションのスタートアップおよびシャットダウンに関連する一連のイベントを公開しています。 Windows フォーム アプリケーションが起動すると、メイン フォームのスタートアップ イベントが次の順序で発生します。  
  
- <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Activated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Shown?displayProperty=nameWithType>  
  
 アプリケーションを閉じると、メイン フォームのシャットダウン イベントが次の順序で発生します。  
  
- <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Closed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Deactivate?displayProperty=nameWithType>  
  
 <xref:System.Windows.Forms.Application> クラスの <xref:System.Windows.Forms.Application.ApplicationExit> イベントは、メイン フォームのシャットダウン イベントの後に発生します。  
  
> [!NOTE]
>  Visual Basic 2005 には、追加のアプリケーション イベント (<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> や <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType> など) があります。  
  
## <a name="focus-and-validation-events"></a>フォーカス イベントと検証イベント  
 キーボード (Tab、Shift + Tab など) を使用するか、<xref:System.Windows.Forms.Control.Select%2A> メソッドまたは <xref:System.Windows.Forms.Control.SelectNextControl%2A> メソッドを呼び出すか、<xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> プロパティを現在のフォームに設定してフォーカスを変更すると、次の順序で <xref:System.Windows.Forms.Control> クラスのフォーカス イベントが発生します。  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
 マウスの使用、または <xref:System.Windows.Forms.Control.Focus%2A> メソッドの呼び出しによってフォーカスを変更すると、次の順序で <xref:System.Windows.Forms.Control> クラスのフォーカス イベントが発生します。  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
## <a name="see-also"></a>関連項目

- [Windows フォーム内でのイベント ハンドラーの作成](creating-event-handlers-in-windows-forms.md)
