---
title: 例:データ バインド時の例外の処理
ms.date: 03/30/2017
ms.assetid: bd63ed96-9853-46dc-ade5-7bd1b0f39110
ms.openlocfilehash: b774d1bce4f4d1c03258ed44b27d3871e7c5275f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2020
ms.locfileid: "79181020"
---
# <a name="example-handling-exceptions-when-binding-data"></a><span data-ttu-id="2df6b-102">例:データ バインド時の例外の処理</span><span class="sxs-lookup"><span data-stu-id="2df6b-102">Example: Handling Exceptions When Binding Data</span></span>
> [!NOTE]
> <span data-ttu-id="2df6b-103">このトピックでは、プレリリース ソフトウェアである .NET Native Developer Preview について述べています。</span><span class="sxs-lookup"><span data-stu-id="2df6b-103">This topic refers to the .NET Native Developer Preview, which is pre-release software.</span></span> <span data-ttu-id="2df6b-104">プレビュー版は、[Microsoft Connect Web サイト](https://go.microsoft.com/fwlink/?LinkId=394611)からダウンロードできます (登録が必要です)。</span><span class="sxs-lookup"><span data-stu-id="2df6b-104">You can download the preview from the [Microsoft Connect website](https://go.microsoft.com/fwlink/?LinkId=394611) (requires registration).</span></span>  
  
 <span data-ttu-id="2df6b-105">次の例は、.NET ネイティブツールチェーンを使用してコンパイルされたアプリがデータをバインドしようとしたときにスローされる[MissingMetadataException](missingmetadataexception-class-net-native.md)例外を解決する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="2df6b-105">The following example shows how to resolve a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception that is thrown when an app compiled with the .NET Native tool chain tries to bind data.</span></span> <span data-ttu-id="2df6b-106">例外情報は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2df6b-106">Here’s the exception information:</span></span>  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:
App.ViewModels.MainPageVM  
```  
  
 <span data-ttu-id="2df6b-107">関連付けられている呼び出し履歴は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2df6b-107">Here's the associated call stack:</span></span>  
  
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
  
## <a name="what-was-the-app-doing"></a><span data-ttu-id="2df6b-108">アプリが行っていた動作は何か</span><span class="sxs-lookup"><span data-stu-id="2df6b-108">What was the app doing?</span></span>  
 <span data-ttu-id="2df6b-109">スタックのベースでは、名前空間のフレームは、 <xref:Windows.UI.Xaml?displayProperty=nameWithType> XAML レンダリングエンジンが実行されていたことを示します。</span><span class="sxs-lookup"><span data-stu-id="2df6b-109">At the base of the stack, frames from the <xref:Windows.UI.Xaml?displayProperty=nameWithType> namespace indicate that the XAML rendering engine was running.</span></span>   <span data-ttu-id="2df6b-110"><xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> メソッドの使用は、そのメタデータが削除された型での、プロパティ値のリフレクション ベースのルックアップを示します。</span><span class="sxs-lookup"><span data-stu-id="2df6b-110">The use of the <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> method indicates a reflection-based lookup of a property’s value on the type whose metadata was removed.</span></span>  
  
 <span data-ttu-id="2df6b-111">メタデータ ディレクティブを提供するための最初の手順は、型の `serialize` メタデータを追加して、そのプロパティすべてをアクセス可能にすることです。</span><span class="sxs-lookup"><span data-stu-id="2df6b-111">The first step in providing a metadata directive would be to add `serialize` metadata for the type so that its properties are all accessible:</span></span>  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a><span data-ttu-id="2df6b-112">特殊なケースかどうか</span><span class="sxs-lookup"><span data-stu-id="2df6b-112">Is this an isolated case?</span></span>  
 <span data-ttu-id="2df6b-113">このシナリオでは、ある `ViewModel` について、データ バインディングに不完全なメタデータが含まれる場合、他のものにも同じことが該当する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2df6b-113">In this scenario, if data binding has incomplete metadata for one `ViewModel`, it may for others, too.</span></span>  <span data-ttu-id="2df6b-114">アプリのビュー モデルがすべて `App.ViewModels` 名前空間内にあるようにコードが作成されている場合、より一般的なランタイム ディレクティブを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2df6b-114">If the code is structured in a way that the app’s view models are all in the `App.ViewModels` namespace, you could use a more general runtime directive:</span></span>  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a><span data-ttu-id="2df6b-115">リフレクションを使用しないようにコードを書き換えることができるか</span><span class="sxs-lookup"><span data-stu-id="2df6b-115">Could the code be rewritten to not use reflection?</span></span>  
 <span data-ttu-id="2df6b-116">データ バインディングではリフレクションが多用されるため、リフレクションを使用しないようにコードを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="2df6b-116">Because data binding is reflection-intensive, changing the code to avoid reflection isn’t feasible.</span></span>  
  
 <span data-ttu-id="2df6b-117">ただし、`ViewModel` を XAML ページに指定して、ツール チェーンがコンパイル時にプロパティ バインディングを正しい型に関連付けて、ランタイム ディレクティブを使用せずにメタデータを保持できるようにする方法はあります。</span><span class="sxs-lookup"><span data-stu-id="2df6b-117">However, there are ways to specify the `ViewModel` to the XAML page so that the tool chain can associate property bindings with the correct type at compile time and keep the metadata without using a runtime directive.</span></span>  <span data-ttu-id="2df6b-118">たとえば、 <xref:Windows.UI.Xaml.Data.BindableAttribute?displayProperty=nameWithType> プロパティに属性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="2df6b-118">For example, you could apply the <xref:Windows.UI.Xaml.Data.BindableAttribute?displayProperty=nameWithType> attribute on properties.</span></span> <span data-ttu-id="2df6b-119">これにより、XAML コンパイラが必要なルックアップ情報を生成するようになり、Default.rd.xml ファイルのランタイム ディレクティブが不要になります。</span><span class="sxs-lookup"><span data-stu-id="2df6b-119">This causes the XAML compiler to generate the required lookup information and avoids requiring a runtime directive in the Default.rd.xml file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2df6b-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="2df6b-120">See also</span></span>

- [<span data-ttu-id="2df6b-121">はじめに</span><span class="sxs-lookup"><span data-stu-id="2df6b-121">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="2df6b-122">例:動的プログラミングのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="2df6b-122">Example: Troubleshooting Dynamic Programming</span></span>](example-troubleshooting-dynamic-programming.md)
