---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 2fe1834c3e92c3eff016ffd7857a0473eb2e8b3a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788857"
---
# <a name="-recurse"></a>-recurse
指定されたディレクトリまたはプロジェクト ディレクトリのいずれかのすべての子ディレクトリ内のソース コード ファイルをコンパイルします。  
  
## <a name="syntax"></a>構文  
  
```  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>引数  
 `dir`  
 任意。 検索を開始するディレクトリ。 指定しない場合、プロジェクト ディレクトリで検索を開始します。  
  
 `file`  
 必須。 検索するファイル。 ワイルドカード文字を使用できます。  
  
## <a name="remarks"></a>Remarks  
 `-recurse` を使用せずにプロジェクト ディレクトリ内の一致するすべてのファイルをコンパイルするには、ワイルドカードを使用できます。 出力ファイル名が指定されない場合、コンパイラは処理する最初の入力ファイルに基づいて出力ファイル名を決定します。 これは一般に、コンパイルされるファイルの一覧をアルファベット順に表示したときの先頭のファイルです。 この理由から、出力ファイルは `-out` オプションを使用して指定するのが最善です。  
  
> [!NOTE]
>  `-recurse`オプションは、Visual Studio 開発環境内からは使用できません。 コマンドラインからコンパイルする場合にのみ使用可能なです。  
  
## <a name="example"></a>例  
 次のコマンドは、現在のディレクトリ内のすべての Visual Basic ファイルをコンパイルします。  
  
```console
vbc *.vb  
```  
  
 次のコマンドですべての Visual Basic ファイルのコンパイル、`Test\ABC`ディレクトリと、その下には、そのディレクトリし、生成`Test.ABC.dll`します。  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-除外 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
