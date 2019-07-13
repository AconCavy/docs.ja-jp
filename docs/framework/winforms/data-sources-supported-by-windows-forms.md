---
title: Windows フォームがサポートするデータ ソース
ms.date: 03/30/2017
helpviewer_keywords:
- collections [Windows Forms], binding to
- OLE DB providers [Windows Forms], Windows Forms
- DataTable class [Windows Forms], binding and Windows Forms
- Windows Forms, data binding
- DataView class [Windows Forms], binding and Windows Forms
- DataViewManager class [Windows Forms], binding and Windows Forms
- Windows Forms, source data
- arrays [Windows Forms]
- data sources [Windows Forms]
- data providers [Windows Forms]
- DataSet class [Windows Forms], binding and Windows Forms
- data [Windows Forms], data providers
ms.assetid: 3d2c43f6-462b-4d35-9c86-13e9afe012e1
ms.openlocfilehash: 6782261953fb5df94498deefb261407a2f0ba33a
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882396"
---
# <a name="data-sources-supported-by-windows-forms"></a>Windows フォームがサポートするデータ ソース
これまでは、データ バインディングは、データベースに格納されたデータを活用するためにアプリケーション内で使用されています。 Windows フォーム データ バインドでは、特定の最小要件を満たしている限り、配列やコレクションなど、他の構造のデータだけでなく、データベースからデータにアクセスすることができます。  
  
## <a name="structures-to-bind-to"></a>連結するには構造体  
 単純なから Windows フォームで、構造体のさまざまなにバインドできます ADO.NET データ テーブル (複合バインディング) などの複雑な一覧にオブジェクト (単純バインディング)。 単純なバインディングで Windows フォームでは単純なオブジェクトのパブリック プロパティにバインドをサポートします。 一般に Windows フォームのリストに基づくバインディングではオブジェクトをサポートしている必要があります、<xref:System.Collections.IList>インターフェイスまたは<xref:System.ComponentModel.IListSource>インターフェイス。 さらからにバインドしている場合、<xref:System.Windows.Forms.BindingSource>コンポーネントをサポートするオブジェクトにバインドすることができます、<xref:System.Collections.IEnumerable>インターフェイス。 データ バインディングに関連するインターフェイスの詳細については、次を参照してください。[データ バインディングに関連するインターフェイス](interfaces-related-to-data-binding.md)します。  
  
 Windows フォームにバインドすることができます、構造体を次に示します。  
  
 <xref:System.Windows.Forms.BindingSource>  
 A<xref:System.Windows.Forms.BindingSource>最も一般的な Windows フォームのデータ ソースは、データ ソースと Windows フォーム コントロールの間のプロキシは機能します。 一般的な<xref:System.Windows.Forms.BindingSource>使用パターンが、コントロールにバインドするには、<xref:System.Windows.Forms.BindingSource>バインドと、<xref:System.Windows.Forms.BindingSource>データ ソース (たとえば、ADO.NET のデータ テーブルまたはビジネス オブジェクト) にします。 <xref:System.Windows.Forms.BindingSource>を有効にして、データ バインディングのサポートのレベルを改善するサービスを提供します。 たとえば、Windows フォームのリスト ベースのコントロールなど、<xref:System.Windows.Forms.DataGridView>と<xref:System.Windows.Forms.ComboBox>へのバインドを直接サポートしていない<xref:System.Collections.IEnumerable>データ ソースをバインディングでは、このシナリオを有効にした、 <xref:System.Windows.Forms.BindingSource>。 ここで、<xref:System.Windows.Forms.BindingSource>は変換をデータ ソース、<xref:System.Collections.IList>します。  
  
 単純なオブジェクト  
 Windows フォームを使用して、オブジェクトのインスタンスでのパブリック プロパティにデータ バインド コントロールのプロパティのサポート、<xref:System.Windows.Forms.Binding>型。 Windows フォーム バインディング リスト ベースのコントロールのようサポートも、<xref:System.Windows.Forms.ListControl>インスタンス オブジェクト、<xref:System.Windows.Forms.BindingSource>使用されます。  
  
 配列またはコレクション  
 データ ソースとして機能し、一覧を実装する必要があります、<xref:System.Collections.IList>インターフェイスは 1 つの例のインスタンスである配列になります、<xref:System.Array>クラス。 配列の詳細については、次を参照してください。[方法。(Visual Basic) のオブジェクトの配列を作成する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/487y7874(v=vs.100))します。  
  
 一般に、使用する必要があります<xref:System.ComponentModel.BindingList%601>データ バインド オブジェクトのリストを作成する場合。 <xref:System.ComponentModel.BindingList%601> ジェネリック バージョンは、<xref:System.ComponentModel.IBindingList>インターフェイス。 <xref:System.ComponentModel.IBindingList>インターフェイスは、拡張、<xref:System.Collections.IList>プロパティ、メソッド、および双方向データ バインドに必要なイベントを追加することでインターフェイス。  
  
 <xref:System.Collections.IEnumerable>  
 Windows フォーム コントロールのみをサポートするデータ ソースにバインドできる、<xref:System.Collections.IEnumerable>インターフェイスを通じてバインドされている場合、<xref:System.Windows.Forms.BindingSource>コンポーネント。  
  
 ADO.NET データ オブジェクト  
 ADO.NET には、さまざまなデータ構造のバインドに適してが用意されています。 その面の知識と複雑さでそれぞれ異なります。  
  
- <xref:System.Data.DataColumn>。 A<xref:System.Data.DataColumn>の不可欠な要素には、<xref:System.Data.DataTable>列の数がテーブルを構成することで、します。 各<xref:System.Data.DataColumn>が、<xref:System.Data.DataColumn.DataType%2A>列が (たとえば、車を説明した表に、自動車の作成) を保持するデータの種類を決定するプロパティ。 コントロールを単純なバインドことができます (など、<xref:System.Windows.Forms.TextBox>コントロールの<xref:System.Windows.Forms.Control.Text%2A>プロパティ) のデータ テーブル内の列にします。  
  
- <xref:System.Data.DataTable>。 A<xref:System.Data.DataTable>行と ADO.NET での列を含む、テーブルの表現です。 データ テーブルに 2 つのコレクションが含まれています: <xref:System.Data.DataColumn>、(最終的にそのテーブルに入力できるデータの種類を決定) する特定のテーブル内のデータの列を表すと<xref:System.Data.DataRow>、特定のテーブル内のデータの行を表します。 複雑にバインドするコントロールをデータ テーブルに含まれる情報を (バインドなど、<xref:System.Windows.Forms.DataGridView>データ テーブル コントロール)。 バインドすると、ただし、<xref:System.Data.DataTable>テーブルの既定のビューに本当にバインドします。  
  
- <xref:System.Data.DataView>。 A<xref:System.Data.DataView>はフィルター処理や並べ替えが 1 つのデータ テーブルのカスタマイズされたビューです。 データ ビューは、「スナップショット」複雑なバインド コントロールで使用されるデータです。 できます単純バインドまたはデータ ビューでは、データへの複雑なバインドがクリーンで更新のデータ ソースではなく、データの固定「画像」にバインドすることに注意してください。  
  
- <xref:System.Data.DataSet>。 A<xref:System.Data.DataSet>テーブル、リレーションシップ、およびデータベース内のデータの制約のコレクションです。 できますが単純なバインドまたは複合バインド、データセット内のデータには、既定値にバインドすることに注意してください<xref:System.Data.DataViewManager>の<xref:System.Data.DataSet>(次の箇条書きをご覧ください)。  
  
- <xref:System.Data.DataViewManager>。 A<xref:System.Data.DataViewManager>全体のカスタマイズされたビューは、<xref:System.Data.DataSet>に似ています、<xref:System.Data.DataView>が含まれている関係を使用します。 <xref:System.Data.DataViewManager.DataViewSettings%2A>コレクション、および設定できます既定のフィルターされたビューの並べ替えオプションを<xref:System.Data.DataViewManager>が、特定のテーブル。  
  
## <a name="see-also"></a>関連項目

- [Windows フォーム データ バインドの変更通知](change-notification-in-windows-forms-data-binding.md)
- [データ連結と Windows フォーム](data-binding-and-windows-forms.md)
- [Windows フォームでのデータ バインディング](windows-forms-data-binding.md)
