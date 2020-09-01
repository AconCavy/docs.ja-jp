---
description: -appconfig (C# コンパイラ オプション)
title: -appconfig (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
ms.openlocfilehash: 287d41105199057add1dad78d480b083adb745b2
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2020
ms.locfileid: "89126113"
---
# <a name="-appconfig-c-compiler-options"></a><span data-ttu-id="3a88e-103">-appconfig (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="3a88e-103">-appconfig (C# Compiler Options)</span></span>
<span data-ttu-id="3a88e-104">**-appconfig** コンパイラ オプションを利用すると、C# アプリケーションで、アセンブリのバインド時に共通言語ランタイム (CLR) にアセンブリのアプリケーション構成 (app.config) ファイルの場所を指定できます。</span><span class="sxs-lookup"><span data-stu-id="3a88e-104">The **-appconfig** compiler option enables a C# application to specify the location of an assembly's application configuration (app.config) file to the common language runtime (CLR) at assembly binding time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a88e-105">構文</span><span class="sxs-lookup"><span data-stu-id="3a88e-105">Syntax</span></span>  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="3a88e-106">引数</span><span class="sxs-lookup"><span data-stu-id="3a88e-106">Arguments</span></span>  
 `file`  
 <span data-ttu-id="3a88e-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="3a88e-107">Required.</span></span> <span data-ttu-id="3a88e-108">アセンブリ バインド設定を含むアプリケーション構成ファイル。</span><span class="sxs-lookup"><span data-stu-id="3a88e-108">The application configuration file that contains assembly binding settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a88e-109">注釈</span><span class="sxs-lookup"><span data-stu-id="3a88e-109">Remarks</span></span>  
 <span data-ttu-id="3a88e-110">**-appconfig** の用途の 1 つは、1 つのアセンブリが特定の参照アセンブリの .NET Framework バージョンと .NET Framework for Silverlight バージョンの両方を同時に参照する必要がある高度なシナリオです。</span><span class="sxs-lookup"><span data-stu-id="3a88e-110">One use of **-appconfig** is advanced scenarios in which an assembly has to reference both the .NET Framework version and the .NET Framework for Silverlight version of a particular reference assembly at the same time.</span></span> <span data-ttu-id="3a88e-111">たとえば、WPF (Windows Presentation Foundation) で作成された XAML デザイナーにおいて、デザイナーのユーザー インターフェイスとして WPF デスクトップを参照すると共に、Silverlight に組み込まれている WPF のサブセットも参照する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="3a88e-111">For example, a XAML designer written in Windows Presentation Foundation (WPF) might have to reference both the WPF Desktop, for the designer's user interface, and the subset of WPF that is included with Silverlight.</span></span> <span data-ttu-id="3a88e-112">同じデザイナー アセンブリで両方のアセンブリにアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a88e-112">The same designer assembly has to access both assemblies.</span></span> <span data-ttu-id="3a88e-113">既定では、この 2 つのアセンブリはアセンブリ バインディングで同等と見なされるため、別々に参照するとコンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="3a88e-113">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span>  
  
 <span data-ttu-id="3a88e-114">**-appconfig** コンパイラ オプションを利用すると、`<supportPortability>` タグを利用して既定の動作を無効にする app.config ファイルの場所を指定できます。次の例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3a88e-114">The **-appconfig** compiler option enables you to specify the location of an app.config file that disables the default behavior by using a `<supportPortability>` tag, as shown in the following example.</span></span>  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 <span data-ttu-id="3a88e-115">このコンパイラは、CLR のアセンブリ バインド ロジックにファイルの場所を渡します。</span><span class="sxs-lookup"><span data-stu-id="3a88e-115">The compiler passes the location of the file to the CLR's assembly-binding logic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3a88e-116">Microsoft Build Engine (MSBuild) を利用してアプリケーションを構築する場合、プロパティ タグを .csproj ファイルに追加し、**-appconfig** コンパイラ オプションを設定できます。</span><span class="sxs-lookup"><span data-stu-id="3a88e-116">If you are using the Microsoft Build Engine (MSBuild) to build your application, you can set the **-appconfig** compiler option by adding a property tag to the .csproj file.</span></span> <span data-ttu-id="3a88e-117">プロジェクトに既に設定されている app.config ファイルを使用するには、プロパティ タグ `<UseAppConfigForCompiler>` を .csproj ファイルに追加し、その値を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="3a88e-117">To use the app.config file that is already set in the project, add property tag `<UseAppConfigForCompiler>` to the .csproj file and set its value to `true`.</span></span> <span data-ttu-id="3a88e-118">異なる app.config ファイルを指定するには、プロパティ タグ `<AppConfigForCompiler>` を追加し、その値をファイルの場所に設定します。</span><span class="sxs-lookup"><span data-stu-id="3a88e-118">To specify a different app.config file, add property tag `<AppConfigForCompiler>` and set its value to the location of the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a88e-119">例</span><span class="sxs-lookup"><span data-stu-id="3a88e-119">Example</span></span>  
 <span data-ttu-id="3a88e-120">.NET Framework と .NET Framework for Silverlight の両方の実装に存在する .NET Framework アセンブリについて、その両方の実装をアプリケーションで参照できるようにする app.config ファイルの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3a88e-120">The following example shows an app.config file that enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="3a88e-121">**-appconfig** コンパイラ オプションにより、この app.config ファイルの場所が指定されます。</span><span class="sxs-lookup"><span data-stu-id="3a88e-121">The **-appconfig** compiler option specifies the location of this app.config file.</span></span>  
  
```xml  
<configuration>  
      <runtime>  
      <assemblyBinding>  
            <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
            <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
      </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3a88e-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="3a88e-122">See also</span></span>

- [<span data-ttu-id="3a88e-123">\<supportPortability> 要素</span><span class="sxs-lookup"><span data-stu-id="3a88e-123">\<supportPortability> Element</span></span>](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)
- [<span data-ttu-id="3a88e-124">アルファベット順の C# コンパイラ オプションの一覧</span><span class="sxs-lookup"><span data-stu-id="3a88e-124">C# Compiler Options Listed Alphabetically</span></span>](./listed-alphabetically.md)
