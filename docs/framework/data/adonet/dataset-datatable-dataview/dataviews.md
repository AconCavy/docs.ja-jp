---
title: DataView
ms.date: 03/30/2017
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
ms.openlocfilehash: 1b202af052c05ed9dc671fa20c9c366f280ec5c7
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774166"
---
# <a name="dataviews"></a>DataView
<xref:System.Data.DataView> では、<xref:System.Data.DataTable> に格納されているデータのさまざまなビューを作成できます。この機能は、データ連結アプリケーションで頻繁に使用されます。 **DataView**を使用すると、異なる並べ替え順序を持つテーブルのデータを公開したり、行の状態またはフィルター式に基づいてデータをフィルター処理したりすることができます。

 **DataView**は、基になる**DataTable**のデータの動的ビューを提供します。コンテンツ、順序、およびメンバーシップには、発生した変更が反映されます。 この動作は、特定のフィルターまたは並べ替え順序に基づいてテーブルから <xref:System.Data.DataRow> 配列を返す**DataTable**の**Select**メソッドとは異なります。このコンテンツには、基になるテーブルに対する変更が反映されますが、そのメンバーシップと順序が反映されます。静的のままです。 **DataView**の動的機能は、データバインディングアプリケーションに最適です。

 **DataView**を使用すると、データベースビューと同じように、データの1つのセットを動的に表示できます。このビューでは、さまざまな並べ替えとフィルター処理の基準を適用できます。 ただし、データベースビューとは異なり、 **DataView**はテーブルとして扱うことができず、結合テーブルのビューを提供することもできません。 また、ソーステーブルに存在する列を除外したり、ソーステーブルに存在しない列 (計算列など) を追加したりすることはできません。

 @No__t_0 を使用すると、**データセット**内のすべてのテーブルのビュー設定を管理できます。 **DataViewManager**を使用すると、各テーブルの既定の表示設定を簡単に管理できます。 コントロールを**データセット**の複数のテーブルにバインドする場合は、 **DataViewManager**へのバインドが最適な選択肢です。

## <a name="in-this-section"></a>このセクションの内容
 [DataView の作成](creating-a-dataview.md)**DataTable**の**DataView**を作成する方法について説明します。

 [データの並べ替えとフィルター処理](sorting-and-filtering-data.md)特定のフィルター条件を満たすデータ行のサブセットを返す**DataView**のプロパティを設定する方法、または特定の並べ替え順序でデータを返す方法について説明します。

 [Datarow と datarowview](datarows-and-datarowviews.md)**DataView**によって公開されるデータにアクセスする方法について説明します。

 [検索 (行](finding-rows.md)を)**DataView**内の特定の行を検索する方法について説明します。

 [Childviews とリレーション](childviews-and-relations.md)**DataView**を使用して親子関係からデータのビューを作成する方法について説明します。

 [DataViews の変更](modifying-dataviews.md)更新を有効または無効にするなど、 **DataView**を使用して基になる**DataTable**のデータを変更する方法について説明します。

 [DataView イベントの処理](handling-dataview-events.md)**DataView**の内容または順序が更新されるときに、 **ListChanged**イベントを使用して通知を受け取る方法について説明します。

 [DataViews の管理](managing-dataviews.md)**DataViewManager**を使用して、**データセット**内の各テーブルの**DataView**設定を管理する方法について説明します。

## <a name="related-sections"></a>関連項目
 [ASP.NET Web アプリケーション](https://docs.microsoft.com/previous-versions/655cec97(v=vs.100))ASP.NET アプリケーション、Web フォーム、および Web サービスを作成するための概要と詳細な手順について説明します。

 [Windows アプリケーション](https://docs.microsoft.com/previous-versions/ms184421(v=vs.100))Windows フォームとコンソールアプリケーションの操作に関する詳細情報を提供します。

 [データセット、datatable、および DataViews](index.md)**DataSet**オブジェクトと、それを使用してアプリケーションデータを管理する方法について説明します。

 [Datatable](datatables.md)**DataTable**オブジェクトと、それを単独で、または**データセット**の一部として管理するために使用する方法について説明します。

 [ADO.NET](../index.md)ADO.NET のアーキテクチャとコンポーネントについて説明します。また、ADO.NET を使用して既存のデータソースにアクセスし、アプリケーションデータを管理する方法について説明します。

## <a name="see-also"></a>関連項目

- [ADO.NET の概要](../ado-net-overview.md)
