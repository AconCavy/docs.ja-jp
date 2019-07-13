---
title: '方法: クリップボードからデータを取得する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pasting Clipboard data
- Clipboard [Windows Forms], retrieving data
ms.assetid: 99612537-2c8a-449f-aab5-2b3b28d656e7
ms.openlocfilehash: 868afc36f08571d16285d0df52f6d1cad8c9c7a6
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348212"
---
# <a name="how-to-retrieve-data-from-the-clipboard"></a>方法: クリップボードからデータを取得する
<xref:System.Windows.Forms.Clipboard>クラスは、Windows オペレーティング システムのクリップボード機能との対話に使用できるメソッドを提供します。 多くのアプリケーションは、クリップボードをデータの一時的なリポジトリとして使用されます。 たとえば、ワード プロセッサでは、切り取りと貼り付けの操作中に、クリップボードを使用します。 クリップボードも別に 1 つのアプリケーションから情報を転送するために役立ちます。  
  
 一部のアプリケーションでは、データを使用できる可能性のあるその他のアプリケーションの数を増やすには、複数の形式でのクリップボードにデータを保存します。 クリップボードの形式は、形式を識別する文字列です。 特定の形式を使用するアプリケーションでは、クリップボードに関連付けられているデータを取得できます。 <xref:System.Windows.Forms.DataFormats>クラスは、使用する定義済みの形式名を提供します。 独自の形式名を使用してもまたはその形式として、オブジェクトの型を使用できます。 クリップボードにデータを追加する方法の詳細については、次を参照してください。[方法。クリップボードにデータを追加](how-to-add-data-to-the-clipboard.md)します。  
  
 特定の形式でデータがクリップボードに含まれるかどうかを判断するのいずれかの操作を使用して、 `Contains`*形式*メソッドまたは<xref:System.Windows.Forms.Clipboard.GetData%2A>メソッド。 クリップボードからデータを取得するには、いずれかを使用、 `Get`*形式*メソッドまたは<xref:System.Windows.Forms.Clipboard.GetData%2A>メソッド。 これらのメソッドは、.NET Framework 2.0 の新機能です。  
  
 .NET Framework 2.0 より前のバージョンを使用して、クリップボードからデータにアクセスするには、使用、<xref:System.Windows.Forms.Clipboard.GetDataObject%2A?displayProperty=nameWithType>メソッドと、返されたメソッドを呼び出す<xref:System.Windows.Forms.IDataObject>します。 たとえば、呼び出す特定の形式が返されるオブジェクトで使用できるかどうかを確認するのには<xref:System.Windows.Forms.IDataObject.GetDataPresent%2A>メソッド。  
  
> [!NOTE]
>  すべての Windows ベースのアプリケーションでは、システムのクリップボードを共有します。 そのため、別のアプリケーションに切り替えた場合に、内容は変更される可能性が。  
>   
>  <xref:System.Windows.Forms.Clipboard>クラスは、シングル スレッド アパートメント (STA) モードに設定するスレッドでのみ使用できます。 このクラスを使用することを確認、`Main`メソッドが設定されて、<xref:System.STAThreadAttribute>属性。  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-single-common-format"></a>1 つの一般的な形式でクリップボードからデータを取得するには  
  
1. 使用して、 <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>、 <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A>、 <xref:System.Windows.Forms.Clipboard.GetImage%2A>、または<xref:System.Windows.Forms.Clipboard.GetText%2A>メソッド。 必要に応じて、使用、対応する`Contains`*形式*データが特定の形式で使用できるかどうかを判断するには、最初のメソッド。 これらのメソッドは、.NET Framework 2.0 でのみ使用できます。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-custom-format"></a>カスタム形式でクリップボードからデータを取得するには  
  
1. 使用して、<xref:System.Windows.Forms.Clipboard.GetData%2A>メソッドをカスタム形式名を使用します。 このメソッドは、.NET Framework 2.0 でのみ使用できます。  
  
     定義済みの形式名を使用することも、<xref:System.Windows.Forms.Clipboard.SetData%2A>メソッド。 詳細については、「 <xref:System.Windows.Forms.DataFormats> 」を参照してください。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-multiple-formats"></a>複数の形式でクリップボードからデータを取得するには  
  
1. <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> メソッドを使用します。 このメソッドを使用して、.NET Framework 2.0 より前のバージョンでクリップボードからデータを取得する必要があります。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>関連項目

- [ドラッグ アンド ドロップ操作とクリップボードのサポート](drag-and-drop-operations-and-clipboard-support.md)
- [方法: データをクリップボードに追加します。](how-to-add-data-to-the-clipboard.md)
