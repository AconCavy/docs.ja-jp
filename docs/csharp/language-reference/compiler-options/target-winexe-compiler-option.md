---
description: -target:winexe (C# コンパイラ オプション)
title: -target:winexe (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
ms.openlocfilehash: 6e14a2aac427c7adfd69f66eaf624816b75f6ea2
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "91168934"
---
# <a name="-targetwinexe-c-compiler-options"></a>-target:winexe (C# コンパイラ オプション)

**-target:winexe** オプションを使用すると、実行可能な (EXE) Windows プログラムがコンパイラによって作成されます。  
  
## <a name="syntax"></a>構文  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a>解説  

 実行可能ファイルは、.exe という拡張子で作成されます。 Windows プログラムは、.NET ライブラリまたは Windows API のユーザー インターフェイスを提供するプログラムです。  
  
 コンソール アプリケーションを作成するには、[-target:exe](./target-exe-compiler-option.md) を使用します。  
  
 [-out](./out-compiler-option.md) オプションで指定しない限り、出力ファイル名は [Main](../../programming-guide/main-and-command-args/index.md) メソッドを含む入力ファイルと同じになります。  
  
 コマンド ラインで指定すると、次の **-out** オプションまたは [-target](./target-compiler-option.md) オプションまでのすべてのファイルが、Windows プログラムの作成に使用されます。  
  
 **Main** メソッドは、.exe ファイルにコンパイルされるソース コード ファイル内で 1 つだけ必要になります。 コードに **Main** メソッドを含むクラスが複数ある場合は、[-main](./main-compiler-option.md) オプションを使用して、**Main** メソッドを含めるクラスを指定できます。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1. プロジェクトの **[プロパティ]** ページを開きます。  
  
2. **[アプリケーション]** プロパティ ページをクリックします。  
  
3. **[出力の種類]** プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.OutputType%2A>」を参照してください。  
  
## <a name="example"></a>例  

 `in.cs` をコンパイルし、Windows プログラムを生成する例を次に示します。  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a>関連項目

- [-target (C# コンパイラ オプション)](./target-compiler-option.md)
- [C# コンパイラ オプション](./index.md)
