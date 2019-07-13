---
title: '方法: FontSizeConverter クラスを使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- FontSizeConverter objects [WPF]
- typography [WPF], FontSizeConverter objects
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
ms.openlocfilehash: f33a297ae07d5509d2b4d9a98636086ac433a57f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051040"
---
# <a name="how-to-use-the-fontsizeconverter-class"></a>方法: FontSizeConverter クラスを使用する
## <a name="example"></a>例  
 この例のインスタンスを作成する方法を示しています。<xref:System.Windows.FontSizeConverter>フォント サイズを変更するとします。  
  
 例では、呼び出されるカスタム メソッドを定義します。`changeSize`の内容を変換する、<xref:System.Windows.Controls.ListBoxItem>個別で定義されている、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]のインスタンスへのファイル<xref:System.Double>、以降に、<xref:System.String>します。 このメソッドは、<xref:System.Windows.Controls.ListBoxItem>に、<xref:System.Windows.FontSizeConverter>オブジェクトで、変換、<xref:System.Windows.Controls.ContentControl.Content%2A>の<xref:System.Windows.Controls.ListBoxItem>のインスタンスに<xref:System.Double>。 この値の値として戻されますが、<xref:System.Windows.Controls.TextBlock.FontSize%2A>のプロパティ、<xref:System.Windows.Controls.TextBlock>要素。  
  
 この例では、呼び出される 2 番目のカスタム メソッドも定義します`changeFamily`します。 このメソッドは変換、<xref:System.Windows.Controls.ContentControl.Content%2A>の<xref:System.Windows.Controls.ListBoxItem>を<xref:System.String>、しにその値を渡します、<xref:System.Windows.Controls.TextBlock.FontFamily%2A>のプロパティ、<xref:System.Windows.Controls.TextBlock>要素。  
  
 この例は実行できません。  
  
 [!code-csharp[FontSizeConverter#1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.FontSizeConverter>
