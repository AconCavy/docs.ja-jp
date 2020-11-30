---
description: -target:winmdobj (C# コンパイラ オプション)
title: -target:winmdobj (C# コンパイラ オプション)
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: a13e2da02698209a514e716d65c1df3508cf1508
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "91171404"
---
# <a name="-targetwinmdobj-c-compiler-options"></a>-target:winmdobj (C# コンパイラ オプション)

**-target:winmdobj** コンパイラ オプションを使用すると、コンパイラは、Windows ランタイム バイナリ (.winmd) ファイルに変換できる .winmdobj 中間ファイルを作成します。 .winmd ファイルは、マネージド言語プログラムだけでなく JavaScript および C++ プログラムでも使用できます。  
  
## <a name="syntax"></a>構文  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a>解説  

 **winmdobj** 設定は、中間モジュールが必要であることをコンパイラに通知します。 これに対し、Visual Studio が C# クラス ライブラリを .winmdobj ファイルとしてコンパイルします。 .winmdobj ファイルは <xref:Microsoft.Build.Tasks.WinMDExp> エクスポート ツールで送信され、Windows メタデータ ファイル (.winmd) が生成されます。 .winmd ファイルには、元のライブラリのコードと WinMD メタデータの両方が含まれています。メタデータは、JavaScript または C++、および Windows ランタイムで使用されます。  
  
 **-target:winmdobj** コンパイラ オプションを使用してコンパイルされたファイルの出力は、WimMDExp エクスポート ツール用の入力としてのみ使用するように設計されています。 .winmdobj ファイル自体は直接参照されません。  
  
 [-out](./out-compiler-option.md) オプションを使用しない限り、出力ファイル名は最初の入力ファイルと同じになります。 [Main](../../programming-guide/main-and-command-args/index.md) メソッドは必要ありません。  
  
 コマンド プロンプトで -target:winmdobj オプションを指定すると、次の **-out** または [-target:module](./target-module-compiler-option.md) オプションまでのすべてのファイルが、Windows プログラムを作成するために使用されます。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a>Windows ストア アプリ用に Visual Studio IDE でこのコンパイラ オプションを設定するには  
  
1. **ソリューション エクスプローラー** で、プロジェクトのショートカット メニューを開き、 **[プロパティ]** を選択します。  
  
2. **[アプリケーション]** タブを選択します。  
  
3. **[出力の種類]** リストで、**[WinMD ファイル]** を選択します。  
  
     **[WinMD ファイル]** オプションは、Windows 8.x Store アプリ テンプレートでのみ使用できます。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.OutputType%2A>」を参照してください。  
  
## <a name="example"></a>例  

 次のコマンドは .winmdobj 中間ファイルに `filename.cs` をコンパイルします。  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a>関連項目

- [-target (C# コンパイラ オプション)](./target-compiler-option.md)
- [C# コンパイラ オプション](./index.md)
