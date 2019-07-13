---
title: '方法: ファイル、文字列、または Stream (Visual Basic) から XML を読み込む'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 097c766fc9efbc810859ab693d3b26f5c1db57ec
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64598332"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a>方法: ファイル、文字列、または Stream (Visual Basic) から XML を読み込む
作成することができます[XML リテラル](../../../../visual-basic/language-reference/xml-literals/index.md)しをいくつかのメソッドを使用して、ファイル、文字列またはストリームなどの外部ソースからコンテンツを設定します。 次の例では、これらのメソッドが表示されます。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-load-xml-from-a-file"></a>ファイルから XML を読み込めません  
  
- XML リテラルなどを設定する、<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>オブジェクトを使用して、ファイルから、`Load`メソッド。 このメソッドは、入力としてファイル パス、テキストのストリームまたは XML ストリームを受け取ることができます。  
  
     次のコード例の使用を示しています、<xref:System.Xml.Linq.XDocument.Load%28System.String%29>メソッドを<xref:System.Xml.Linq.XDocument>テキスト ファイルから XML を持つオブジェクト。  
  
     [!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]  
  
### <a name="to-load-xml-from-a-string"></a>文字列から XML を読み込めません  
  
- XML リテラルなどを設定する、<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>オブジェクト、文字列から使用することができます、`Parse`メソッド。  
  
     次のコード例の使用を示しています、<xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType>メソッドを<xref:System.Xml.Linq.XDocument>xml 文字列からのオブジェクト。  
  
     [!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]  
  
### <a name="to-load-xml-from-a-stream"></a>ストリームから XML を読み込めません  
  
- XML リテラルなどを設定する、<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>オブジェクト、ストリームから使用することができます、`Load`メソッドまたは<xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>メソッド。  
  
 次のコード例の使用を示しています、<xref:System.Xml.Linq.XNode.ReadFrom%2A>メソッドを<xref:System.Xml.Linq.XDocument>XML ストリームから XML を持つオブジェクト。  
  
 [!code-vb[VbXMLSamples#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#46)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>
- [XML リテラル](../../../../visual-basic/language-reference/xml-literals/index.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Visual Basic での XML の操作](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
