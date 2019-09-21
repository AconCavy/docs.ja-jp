---
title: <compiler> 要素
ms.date: 08/14/2018
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler
helpviewer_keywords:
- compiler configuration elements, <compiler> element
- <compiler> element
- compiler configuration attributes
- compiler element
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
ms.openlocfilehash: a19cf8182cdb338fd8596ef38311916de0daae37
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168942"
---
# <a name="compiler-element"></a>\<compiler> 要素

言語プロバイダーのコンパイラ構成属性を指定します。

[ **\<configuration>** ](../configuration-element.md)  
&nbsp;&nbsp;[ **\<システムの codedom >** ](system-codedom-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<コンパイラの >** ](compilers-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<コンパイラの >**  

## <a name="syntax"></a>構文

```xml
<compiler
  language="languageName[;...;...]"
  extension="fileExtension[;...;...]"
  type="typeName, assemblyName"
  warningLevel="number"
  compilerOptions="option1 option2"
/>
```

## <a name="attributes-and-elements"></a>属性および要素

以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

|属性|説明|
|---------------|-----------------|
|`compilerOptions`|省略可能な属性です。<br /><br /> コンパイル用の追加のコンパイラ固有の引数を指定します。 `compilerOptions`属性の値は、通常、コンパイラのコンパイラオプションのトピックに示されています。|
|`extension`|必須の属性です。<br /><br /> 言語プロバイダーのソースファイルで使用されるファイル名拡張子のセミコロン区切りのリストを提供します。 たとえば、".cs" のようになります。|
|`language`|必須の属性です。<br /><br /> 言語プロバイダーでサポートされている言語名のセミコロン区切りのリストを提供します。 たとえば、"c#; cs; csharp" のようになります。|
|`type`|必須の属性です。<br /><br /> プロバイダーの実装を含むアセンブリの名前を含む、言語プロバイダーの型名を指定します。 型名は、 [「完全修飾型名の指定](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)」で定義されている要件を満たしている必要があります。|
|`warningLevel`|省略可能な属性です。<br /><br /> 既定のコンパイラの警告レベルを指定します。言語プロバイダーがコンパイル警告をエラーとして扱うレベルを決定します。|

### <a name="child-elements"></a>子要素

|要素|説明|
|-------------|-----------------|
|[\<providerOption > 要素](provideroption-element.md)|言語プロバイダーのコンパイラバージョン属性を指定します。|

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|[\<configuration> 要素](../configuration-element.md)|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|
|[\<system.string > 要素](system-codedom-element.md)|使用可能な言語プロバイダーのコンパイラ構成設定を指定します。|
|[\<compilers> 要素](compilers-element.md)|コンパイラ構成要素のコンテナー0 個以上含む`<compiler>`要素。|

## <a name="remarks"></a>Remarks

各`<compiler>`要素は、特定の言語プロバイダーのコンパイラ構成属性を指定します。 プロバイダーは、特定<xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>の言語のクラスを拡張し`<compiler>`ます。要素は、言語プロバイダーのコンパイラとコードジェネレーターの設定を定義します。

.NET Framework は、マシン構成ファイル (Machine.config) 内でコンパイラの初期設定を定義します。 開発者やコンパイラ ベンダーは、新しい <xref:System.CodeDom.Compiler.CodeDomProvider> の実装のために構成設定を追加することができます。 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> メソッドを使用して、プログラムによってコンピューターの言語プロバイダーとコンパイラ構成の設定を列挙します。

アプリケーションまたは Web 構成ファイル内のコンパイラ要素は、マシン構成ファイル内の設定を補完またはオーバーライドできます。 同じ言語名または同じファイル拡張子に対して複数のプロバイダー実装が構成されている場合、最後に一致した構成によって、その言語名またはファイル拡張子に対して以前に構成されたすべてのプロバイダーがオーバーライドされます。

## <a name="configuration-file"></a>構成ファイル

この要素は、マシン構成ファイルおよびアプリケーション構成ファイルで使用できます。

## <a name="example"></a>例

次の例は、一般的なコンパイラ構成要素を示しています。

```xml
<configuration>
  <system.codedom>
    <compilers>
      <!-- zero or more compiler elements -->
      <compiler
        language="c#;cs;csharp"
        extension=".cs"
        type="Microsoft.CSharp.CSharpCodeProvider, System,
          Version=2.0.3600.0, Culture=neutral,
          PublicKeyToken=b77a5c561934e089"
        compilerOptions="/optimize"
        warningLevel="1" />
    </compilers>
  </system.codedom>
</configuration>
```

## <a name="see-also"></a>関連項目

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [構成ファイル スキーマ](../index.md)
- [\<compilers> 要素](compilers-element.md)
- [完全修飾型名の指定](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- [コンパイル用コンパイラのコンパイラ要素 (ASP.NET Settings スキーマ)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))
