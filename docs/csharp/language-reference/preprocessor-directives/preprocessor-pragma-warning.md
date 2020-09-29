---
description: '#pragma warning - C# リファレンス'
title: '#pragma warning - C# リファレンス'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 5b67d384e37a5e509ce8ebcc5ddeb16a4437ea2b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168531"
---
# <a name="pragma-warning-c-reference"></a>#pragma 警告 (C# リファレンス)

`#pragma warning` を使用すると、特定の警告を有効または無効にすることができます。  
  
## <a name="syntax"></a>構文  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a>パラメーター  

 `warning-list`  
 警告番号のコンマ区切りのリスト。 "CS" というプレフィックスは省略可能です。  
  
 警告番号が指定されていないと、`disable` はすべての警告を無効にし、`restore` はすべての警告を有効にします。  
  
> [!NOTE]
> Visual Studio で警告番号を調べるには、プロジェクトをビルドし、**[出力]** ウィンドウで警告番号を探してください。  
  
## <a name="example"></a>例  
  
```csharp
// pragma_warning.cs  
using System;  
  
#pragma warning disable 414, CS3021  
[CLSCompliant(false)]  
public class C  
{  
    int i = 1;  
    static void Main()  
    {  
    }  
}  
#pragma warning restore CS3021  
[CLSCompliant(false)]  // CS3021  
public class D  
{  
    int i = 1;  
    public static void F()  
    {  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# プリプロセッサ ディレクティブ](./index.md)
- [C# コンパイラ エラー](../compiler-messages/index.md)
