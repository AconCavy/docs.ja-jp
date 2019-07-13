---
title: '方法: 依存関係プロパティを実装する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
ms.openlocfilehash: e2f18cb3941be2ebf4315a844c05b91ff49c6aa2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757457"
---
# <a name="how-to-implement-a-dependency-property"></a>方法: 依存関係プロパティを実装する
バックアップを作成する方法を示します、[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]プロパティを<xref:System.Windows.DependencyProperty>フィールド、ため、依存関係プロパティを定義します。 独自に定義したプロパティが [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のさまざまな機能、たとえばスタイル、データ バインディング、継承、アニメーション、既定値をサポートできるようにするには、そのプロパティを依存関係プロパティとして実装します。  
  
## <a name="example"></a>例  
 次の例は、呼び出すことによって、依存関係プロパティを登録する最初の<xref:System.Windows.DependencyProperty.Register%2A>メソッド。 名前を格納するを使用して、依存関係プロパティの特性である必要がある識別子フィールドの名前、<xref:System.Windows.DependencyProperty.Name%2A>依存関係プロパティの一部として選択した、<xref:System.Windows.DependencyProperty.Register%2A>呼び出し、リテラル文字列により追加された`Property`します。 たとえばとの依存関係プロパティを登録する場合、<xref:System.Windows.DependencyProperty.Name%2A>の`Location`、依存関係プロパティを定義する識別子フィールドを指定する必要がありますし、`LocationProperty`します。  
  
 この例では、依存関係プロパティの名前とその[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]アクセサーが`State`; 識別子フィールドは`StateProperty`; プロパティの型は<xref:System.Boolean>; 依存関係プロパティを登録する型が`MyStateControl`。  
  
 このパターンに従って名前が付けられていない場合は、定義したプロパティがデザイナーから正しく報告されず、プロパティ システムのスタイル適用の一部が予期したとおりに動作しなくなる可能性があります。  
  
 依存関係プロパティの既定のメタデータを指定することもできます。 `State` 依存関係プロパティの既定値を `false` として登録する例を次に示します。  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 単にプライベート フィールドを使用して [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] プロパティを補足するのではなく依存関係プロパティを実装する理由とその方法の詳細については、「[依存関係プロパティの概要](dependency-properties-overview.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [依存関係プロパティの概要](dependency-properties-overview.md)
- [方法トピック](properties-how-to-topics.md)
