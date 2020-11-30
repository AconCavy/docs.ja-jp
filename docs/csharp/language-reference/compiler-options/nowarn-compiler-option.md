---
description: -nowarn (C# コンパイラ オプション)
title: -nowarn (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
ms.openlocfilehash: 31a7ee5eacb2e7cd6b24c4a2276ce6e07fcc67e1
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "91194025"
---
# <a name="-nowarn-c-compiler-options"></a>-nowarn (C# コンパイラ オプション)

**-nowarn** オプションを使用すると、コンパイラから警告が出力されないようにすることができます。 警告番号が複数ある場合は、コンマで区切ります。  
  
## <a name="syntax"></a>構文  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a>引数  

 `number1`, `number2`  
 コンパイラで表示しないようにする警告番号。  
  
## <a name="remarks"></a>注釈  

 警告 ID の数値だけを指定します。 たとえば、CS0028 を抑制する場合は、`-nowarn:28` と指定します。  
  
 `-nowarn` に渡された警告番号が以前のリリースでは有効であったが、今はコンパイラから削除されている場合、コンパイラはその番号を自動的に無視します。 たとえば、CS0679 は Visual Studio .NET 2002 のコンパイラでは有効でしたが、その後削除されました。  
  
 `-nowarn` オプションでは、次の警告は抑制されません。  
  
- コンパイラの警告 (レベル 1) CS2002  
  
- コンパイラの警告 (レベル 1) CS2023  
  
- コンパイラの警告 (レベル 1) CS2029  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1. プロジェクトの **[プロパティ]** ページを開きます。 詳細については、「[[ビルド] ページ (プロジェクト デザイナー) (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)」を参照してください。  
  
2. **[ビルド]** プロパティ ページをクリックします。  
  
3. [**警告の表示なし**] プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.DelaySign%2A>」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [C# コンパイラ オプション](./index.md)
- [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)
- [C# コンパイラ エラー](../compiler-messages/index.md)
