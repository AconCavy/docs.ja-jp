---
title: XML ファイルの処理 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
ms.openlocfilehash: ab05db770f312a362e26f17df684f6f4f49c0eb3
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586740"
---
# <a name="processing-the-xml-file-visual-basic"></a>XML ファイルの処理 (Visual Basic)
コンパイラは、ドキュメントを生成するためにタグ付けされたコードのコンストラクトごとに、ID 文字列を生成します。 (コードをタグ付けする方法については、次を参照してください[XML コメント タグ](../../../visual-basic/language-reference/xmldoc/index.md)。)。ID 文字列によって、コンストラクトは一意に識別されます。 XML ファイルを処理するプログラムは、対応する .NET Framework メタデータ/リフレクション項目を識別するために、ID 文字列を使用できます。  
  
 XML ファイルは、コードの階層表現ではありません。各要素に対して生成された ID を持つ単純なリストになります。  
  
 コンパイラは、次の規則に基づいて ID 文字列を生成します。  
  
- 文字列に空白は配置されません。  
  
- ID 文字列の最初の部分は、単一の文字とそれに続くコロンで識別されるメンバーの種類を示します。 次のメンバーの種類が使用されます。  
  
|文字|説明|  
|---|---|  
|N|namespace<br /><br /> 名前空間をドキュメントのコメントを追加することはできませんが、それらへの CREF 参照を行うことができますが、サポートされています。|  
|T|型: `Class`、 `Module`、 `Interface`、 `Structure`、 `Enum`、 `Delegate`|  
|F|フィールド: `Dim`|  
|P|プロパティ: `Property` (既定のプロパティを含む)|  
|M|方法: `Sub`、 `Function`、 `Declare`、 `Operator`|  
|E|イベント: `Event`|  
|!|エラー文字列<br /><br /> あとに続く文字列で、エラーの情報を示します。 Visual Basic コンパイラでは、解決できないリンクのエラー情報を生成します。|  
  
- 2 番目の部分、 `String` 、名前空間のルートにある項目の完全修飾の名前を指定します。 項目、その外側の型および名前空間の名前は、ピリオドで区切られます。 シャープ記号で置き換えられますが、項目自体の名前にピリオドが含まれている場合 (#)。 項目の名前には番号記号がないことが前提です。 たとえば、完全修飾名の`String`コンス トラクターになる`System.String.#ctor`します。  
  
- プロパティおよびメソッドについては、メソッドに引数がある場合は、引数のリストをかっこで囲み、メソッドに続けて指定します。 引数がない場合は、かっこはありません。 引数はコンマで区切られます。 各引数のエンコーディングに依存して直接 .NET Framework のシグネチャでのエンコード方法。  
  
## <a name="example"></a>例  
 次のコードは、クラスの ID の文字列し、そのメンバーが生成されます。  
  
 [!code-vb[VbVbcnXmlDocComments#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#10)]  
  
## <a name="see-also"></a>関連項目

- [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
- [方法: XML ドキュメントを作成します。](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
