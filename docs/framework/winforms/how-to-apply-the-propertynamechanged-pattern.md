---
title: '方法: PropertyNameChanged パターンを適用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- data binding [Windows Forms], custom controls
- PropertyNameChanged pattern [Windows Forms], applying
ms.assetid: aa47ddf6-5223-40c4-833f-a78992194836
ms.openlocfilehash: 01afa713e97206ea192ba55dc2affad20163f872
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665262"
---
# <a name="how-to-apply-the-propertynamechanged-pattern"></a>方法: PropertyNameChanged パターンを適用する
次のコード例は、適用する方法を示します、 *PropertyName*Changed パターンをカスタム コントロール。 Windows フォーム データ バインディング エンジンで使用されるカスタム コントロールを実装する場合は、このパターンを適用します。  
  
## <a name="example"></a>例  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 上記のコード例をコンパイルするには。  
  
- 空のコード ファイルには、コードを貼り付けます。 含む Windows フォームでのカスタム コントロールを使用する必要があります、`Main`メソッド。  
  
## <a name="see-also"></a>関連項目

- [方法: INotifyPropertyChanged インターフェイスを実装します。](how-to-implement-the-inotifypropertychanged-interface.md)
- [Windows フォーム データ バインドの変更通知](change-notification-in-windows-forms-data-binding.md)
- [Windows フォームでのデータ バインディング](windows-forms-data-binding.md)
