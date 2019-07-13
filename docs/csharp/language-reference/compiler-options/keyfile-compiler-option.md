---
title: -keyfile (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
ms.openlocfilehash: 3e11cbca004aedd7d4f992abf2f766de4f4f5935
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344651"
---
# <a name="-keyfile-c-compiler-options"></a>-keyfile (C# コンパイラ オプション)
暗号化キーを格納するファイル名を指定します。  
  
## <a name="syntax"></a>構文  
  
```console  
-keyfile:file  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|----------|----------------|  
|`file`|厳密な名前のキーを格納するファイルの名前。|  
  
## <a name="remarks"></a>解説  
 このオプションを指定すると、コンパイラは、指定したファイルからアセンブリ マニフェストに公開キーを挿入し、最終的なアセンブリに秘密キーで署名します。 キー ファイルを生成するには、コマンド ラインで「sn -k `file`」と入力します。  
  
 **-target:module** を指定してコンパイルした場合は、キー ファイルの名前がモジュールに保持され、[-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) でアセンブリをコンパイルすると作成されるアセンブリに組み込まれます。  
  
 また、暗号化情報を [-keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md) でコンパイラに渡すことができます。 部分的に署名されたアセンブリを作成する場合は、[-delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) を使います。  
  
 同じコンパイルで (コマンド ライン オプションまたはカスタム属性によって) -keyfile と -keycontainer を両方とも指定すると、コンパイラは最初にキー コンテナーを試します。 それが成功すると、アセンブリはキー コンテナーの情報で署名されます。 キー コンテナーが見つからない場合、コンパイラは -keyfile で指定されたファイルを検索します。 ファイルが検出された場合、アセンブリはキー ファイルの情報で署名され、キー情報はキー コンテナーにインストールされるため (sn -i と同様)、次のコンパイル時にはキー コンテナーが有効になります。  
  
 キー ファイルには公開キーだけが含まれる場合があることに注意してください。  
  
 詳しくは、「[厳密な名前付きアセンブリの作成と使用](../../../framework/app-domains/create-and-use-strong-named-assemblies.md)」および「[アセンブリへの遅延署名](../../../framework/app-domains/delay-sign-assembly.md)」をご覧ください。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1. プロジェクトの **[プロパティ]** ページを開きます。  
  
2. **[署名]** プロパティ ページをクリックします。  
  
3. **[厳密な名前のキー ファイルを選択してください]** プロパティを変更します。  
  
 このコンパイラ オプションには、プログラムで <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A> を使ってアクセスできます。  
  
## <a name="see-also"></a>関連項目

- [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)
- [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)
