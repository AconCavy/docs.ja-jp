---
title: 例:データ バインド時の例外の処理
ms.date: 03/30/2017
ms.assetid: bd63ed96-9853-46dc-ade5-7bd1b0f39110
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f7c40d1a179c29c3b92ca37848db6d1383e5d2d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049888"
---
# <a name="example-handling-exceptions-when-binding-data"></a>例:データ バインド時の例外の処理
> [!NOTE]
> このトピックでは、プレリリース ソフトウェアである .NET Native Developer Preview について述べています。 プレビュー版は、[Microsoft Connect Web サイト](https://go.microsoft.com/fwlink/?LinkId=394611)からダウンロードできます (登録が必要です)。  
  
 次の例は、.NET ネイティブツールチェーンを使用してコンパイルされたアプリがデータをバインドしようとしたときにスローされる[MissingMetadataException](missingmetadataexception-class-net-native.md)例外を解決する方法を示しています。 例外情報は次のとおりです。  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:   
App.ViewModels.MainPageVM  
```  
  
 関連付けられている呼び出し履歴は次のとおりです。  
  
```output
Reflection::Execution::ReflectionDomainSetupImplementation.CreateNonInvokabilityException+0x238  
Reflection::Core::ReflectionDomain.CreateNonInvokabilityException+0x2e  
Reflection::Core::Execution::ExecutionEnvironment.+0x316  
System::Reflection::Runtime::PropertyInfos::RuntimePropertyInfo.GetValue+0x1cb  
System::Reflection::PropertyInfo.GetValue+0x22  
System::Runtime::InteropServices::WindowsRuntime::CustomPropertyImpl.GetValue+0x42  
App!$66_Interop::McgNative.Func_IInspectable_IInspectable+0x158  
App!$66_Interop::McgNative::__vtable_Windows_UI_Xaml_Data__ICustomProperty.GetValue__STUB+0x46  
Windows_UI_Xaml!DirectUI::PropertyProviderPropertyAccess::GetValue+0x3f   
Windows_UI_Xaml!DirectUI::PropertyAccessPathStep::GetValue+0x31   
Windows_UI_Xaml!DirectUI::PropertyPathListener::ConnectPathStep+0x113  
```  
  
## <a name="what-was-the-app-doing"></a>アプリが行っていた動作は何か  
 スタックのベースでは、 <xref:Windows.UI.Xaml?displayProperty=nameWithType>名前空間のフレームは、XAML レンダリングエンジンが実行されていたことを示します。   <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> メソッドの使用は、そのメタデータが削除された型での、プロパティ値のリフレクション ベースのルックアップを示します。  
  
 メタデータ ディレクティブを提供するための最初の手順は、型の `serialize` メタデータを追加して、そのプロパティすべてをアクセス可能にすることです。  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a>特殊なケースかどうか  
 このシナリオでは、ある `ViewModel` について、データ バインディングに不完全なメタデータが含まれる場合、他のものにも同じことが該当する可能性があります。  アプリのビュー モデルがすべて `App.ViewModels` 名前空間内にあるようにコードが作成されている場合、より一般的なランタイム ディレクティブを使用できます。  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a>リフレクションを使用しないようにコードを書き換えることができるか  
 データ バインディングではリフレクションが多用されるため、リフレクションを使用しないようにコードを変更することはできません。  
  
 ただし、`ViewModel` を XAML ページに指定して、ツール チェーンがコンパイル時にプロパティ バインディングを正しい型に関連付けて、ランタイム ディレクティブを使用せずにメタデータを保持できるようにする方法はあります。  たとえば、プロパティに<xref:Windows.UI.Xaml.Data.BindableAttribute?displayProperty=nameWithType>属性を適用できます。 これにより、XAML コンパイラが必要なルックアップ情報を生成するようになり、Default.rd.xml ファイルのランタイム ディレクティブが不要になります。  
  
## <a name="see-also"></a>関連項目

- [はじめに](getting-started-with-net-native.md)
- [例:トラブルシューティング (動的プログラミング)](example-troubleshooting-dynamic-programming.md)
