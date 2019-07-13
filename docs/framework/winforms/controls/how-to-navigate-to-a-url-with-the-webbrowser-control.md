---
title: '方法: WebBrowser コントロールで URL に移動する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- WebBrowser.Navigate
helpviewer_keywords:
- WebBrowser control [Windows Forms], examples
- URLs [Windows Forms], navigating to
- WebBrowser control [Windows Forms], navigating to URLs
- examples [Windows Forms], WebBrowser control
ms.assetid: b3ec38cb-f509-4d0b-bd79-9f3611259c62
ms.openlocfilehash: bee16a388d823f74bc9c88bc34b510d2a5907393
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649222"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a>方法: WebBrowser コントロールで URL に移動する
次のコード例は、移動する方法を示します、<xref:System.Windows.Forms.WebBrowser>コントロールを特定の URL。  
  
 調べるには、新しいドキュメントが完全に読み込まれるときに、処理、<xref:System.Windows.Forms.WebBrowser.DocumentCompleted>イベント。 このイベントのデモについては、次を参照してください。[方法。WebBrowser コントロールで印刷](how-to-print-with-a-webbrowser-control.md)します。  
  
## <a name="example"></a>例  
  
```vb  
Me.webBrowser1.Navigate("http://www.microsoft.com")  
```  
  
```csharp  
this.webBrowser1.Navigate("http://www.microsoft.com");  
```  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- `webBrowser1` という名前の <xref:System.Windows.Forms.WebBrowser> コントロール。  
  
- `System` アセンブリおよび `System.Windows.Forms` アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [WebBrowser コントロール](webbrowser-control-windows-forms.md)
- [方法: WebBrowser コントロールを使用して印刷します。](how-to-print-with-a-webbrowser-control.md)
