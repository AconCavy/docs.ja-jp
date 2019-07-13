---
title: Model-View-View Model を利用した汎用性のあるクラス ライブラリの使用
ms.date: 07/18/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Portable Class Library [.NET Framework], and MVVM
- MVVM, and Portable Class Library
ms.assetid: 41a0b9f8-15a2-431a-bc35-e310b2953b03
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b53be90764c6537fb27cb1b5ed781a68e69effa0
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504675"
---
# <a name="using-portable-class-library-with-model-view-view-model"></a>Model-View-View Model を利用した汎用性のあるクラス ライブラリの使用
.NET Framework を使用して[ポータブル クラス ライブラリ](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)モデル-ビュー-ビュー モデル (MVVM) パターンを実装して、複数のプラットフォームでアセンブリを共有します。

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 MVVM では、基になるビジネス ロジックからユーザー インターフェイスを分離するアプリケーション パターンです。 Visual Studio 2012 のポータブル クラス ライブラリ プロジェクトでモデルとビュー モデル クラスを実装し、さまざまなプラットフォーム用にカスタマイズされたビューを作成できます。 このアプローチでは、データを記述できます。 モデルとビジネス ロジックを 1 回だけ、.NET Framework、Silverlight、Windows Phone のコードを使用および[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]アプリは、次の図に示すようにします。

 ![プラットフォーム間で共有アセンブリの MVVM を使用したポータブル クラス ライブラリを示します。](./media/using-portable-class-library-with-model-view-view-model/mvvm-share-assemblies-across-platforms.png)

 このトピックでは、MVVM パターンに関する一般的な情報は提供されません。 ポータブル クラス ライブラリを使用して、MVVM を実装する方法についての情報を提供するだけです。 MVVM の詳細については、次を参照してください。、 [MVVM クイック スタートで、wpf、Prism ライブラリ 5.0 が使用して](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40))します。

## <a name="classes-that-support-mvvm"></a>MVVM をサポートするクラス
 .NET Framework 4.5 を対象とする場合[!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]Silverlight、またはポータブル クラス ライブラリ プロジェクトの Windows Phone 7.5 次のクラスは、MVVM パターンを実装します。

- <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> クラス

- <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> クラス

- <xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> クラス

- <xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> クラス

- <xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> クラス

- <xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> クラス

- <xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> クラス

- <xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> クラス

- <xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> クラス

- <xref:System.Windows.Input.ICommand?displayProperty=nameWithType> クラス

- すべてのクラス、<xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType>名前空間

## <a name="implementing-mvvm"></a>MVVM の実装
 MVVM を実装するには、通常を作成するモデルとビュー モデルの両方でポータブル クラス ライブラリ プロジェクトでは、ポータブル クラス ライブラリ プロジェクトがポータブルでないプロジェクトを参照できないためです。 モデルとビュー モデルは、同じプロジェクト内、または別のプロジェクトを指定できます。 個別のプロジェクトを使用する場合は、モデル プロジェクトにビューのモデル プロジェクトからの参照を追加します。

 モデルをコンパイルし、モデル プロジェクトを表示すると後、は、ビューを含むアプリでそれらのアセンブリを参照します。 ビューは、ビュー モデルとのみやり取りをする場合のみ、ビュー モデルを含むアセンブリを参照する必要があります。

### <a name="model"></a>モデル
 次の例では、ポータブル クラス ライブラリ プロジェクトである単純なモデル クラスを示します。

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 次の例では、設定、取得、およびポータブル クラス ライブラリ プロジェクト内のデータを更新する簡単な方法を示します。 実際のアプリでは、Windows Communication Foundation (WCF) サービスなどのソースからデータを取得します。

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a>ビュー モデル
 MVVM パターンを実装するときに、ビュー モデルの基本クラスが頻繁に追加されます。 次の例では、基本クラスを示します。

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 実装、<xref:System.Windows.Input.ICommand>インターフェイスは、MVVM パターンでよく使用されます。 <xref:System.Windows.Input.ICommand> インターフェイスを実装する例を次に示します。

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 次の例では、簡略化されたビュー モデルを示します。

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a>表示  
 .NET Framework 4.5 アプリから[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]アプリ、Silverlight ベースのアプリまたは Windows Phone 7.5 アプリの場合は、モデルとビュー モデル プロジェクトを含むアセンブリを参照することができます。  対話するビューを作成するには、ビュー モデルを使用します。 取得し、ビュー モデルからデータを更新する Windows Presentation Foundation (WPF) アプリを簡略化されたは、次の例です。 Windows Phone、Silverlight で同様のビューを作成または[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]アプリ。  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a>関連項目

- [ポータブル クラス ライブラリ](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
