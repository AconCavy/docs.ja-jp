---
title: '方法: フォント ファミリとフォントを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- font families [Windows Forms], constructing
- fonts [Windows Forms], constructing
ms.assetid: d3a4a223-9492-4b54-9afd-db1c31c3cefd
ms.openlocfilehash: 2d609525858c7a8ff77c0b86900b4fc7d6b4e39a
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505948"
---
# <a name="how-to-construct-font-families-and-fonts"></a>方法: フォント ファミリとフォントを作成する
GDI + でさまざまなスタイルも同じタイプフェイスのフォントのフォント ファミリにグループ化します。 たとえば、Arial フォント ファミリには、次のフォントが含まれています。  
  
- Arial 通常  
  
- Arial 太字  
  
- Arial 斜体  
  
- Arial 太字斜体  
  
 GDI + 形式のファミリの 4 つのスタイルを使用します。 通常、太字、斜体と太字斜体します。 など、形容詞*を絞り込む*と*丸め*スタイル; とは見なされませんではなく、ファミリ名の一部であります。 たとえば、ゴシックは、次のメンバーを持つフォント ファミリです。  
  
- Arial 狭い通常  
  
- Arial ナロー太字  
  
- Arial 狭い斜体  
  
- Arial 狭い太字斜体  
  
 GDI + を使用してテキストを描画する前に作成する必要があります、<xref:System.Drawing.FontFamily>オブジェクトと<xref:System.Drawing.Font>オブジェクト。 <xref:System.Drawing.FontFamily>オブジェクト (たとえば、Arial) 書体を指定して、<xref:System.Drawing.Font>オブジェクトは、サイズ、スタイル、および単位を指定します。  
  
## <a name="example"></a>例  
 次の例では、標準のスタイル、サイズが 16 ピクセルの Arial フォントを作成します。 次のコードに渡される最初の引数、<xref:System.Drawing.Font.%23ctor%2A>コンス トラクターは、<xref:System.Drawing.FontFamily>オブジェクト。 2 番目の引数には、4 番目の引数によって識別される単位でのフォントのサイズを指定します。 3 番目の引数は、スタイルを識別します。  
  
 <xref:System.Drawing.GraphicsUnit.Pixel> メンバーである、<xref:System.Drawing.GraphicsUnit>列挙型、および<xref:System.Drawing.FontStyle.Regular>のメンバーである、<xref:System.Drawing.FontStyle>列挙体。  
  
 [!code-csharp[System.Drawing.FontsAndText#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.FontsAndText#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されています。 また必要が<xref:System.Windows.Forms.PaintEventArgs> `e`、はのパラメーター<xref:System.Windows.Forms.PaintEventHandler>します。  
  
## <a name="see-also"></a>関連項目

- [フォントとテキストの使用](using-fonts-and-text.md)
- [Windows フォームにおけるグラフィックスと描画](graphics-and-drawing-in-windows-forms.md)
