---
description: '#define - C# リファレンス'
title: '#define - C# リファレンス'
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: 961c20c091a4a6d7da421d94500abd41d2d60a5b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160503"
---
# <a name="define-c-reference"></a>#define (C# リファレンス)

`#define` は、シンボルを定義するために使用します。 次の例に示すように、定義したシンボルを式として [#if](./preprocessor-if.md) ディレクティブに渡すと、式は `true` と評価されます。  

 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a>注釈  
  
> [!NOTE]
> `#define` ディレクティブを使用して、通常 C および C++ で行うように定数値を宣言することはできません。 C# の定数は、クラスまたは構造体の静的メンバーとして定義することができます。 そのような定数がいくつかある場合は、それを保持するための "Constants" クラスを個別に作成することを検討してください。  
  
 シンボルを使用して、コンパイル条件を指定できます。 シンボルは、[#if](./preprocessor-if.md) または [#elif](./preprocessor-elif.md) で評価できます。 また、<xref:System.Diagnostics.ConditionalAttribute> を使用して、条件付きコンパイルを実行することもできます。  
  
 シンボルを定義することはできますが、シンボルに値は代入できません。 `#define` ディレクティブは、ファイル内で、プリプロセッサ ディレクティブではない他の命令よりも前に記述する必要があります。  
  
 シンボルは、[-define](../compiler-options/define-compiler-option.md) コンパイラ オプションでも定義できます。 [#undef](./preprocessor-undef.md) を使うと、シンボルを未定義状態にできます。  
  
 `-define` または `#define` で定義されたシンボルは、同じ名前の変数とは競合しません。 変数名をプリプロセッサ ディレクティブに渡すことはできません。シンボルはプリプロセッサ ディレクティブだけで評価されます。  
  
 `#define` で定義されたシンボルのスコープは、そのシンボルが定義されたファイル内だけです。  
  
 次の例に示すように、`#define` ディレクティブは、ファイルの先頭で指定する必要があります。  
  
```csharp  
#define DEBUG  
//#define TRACE  
#undef TRACE  
  
using System;  
  
public class TestDefine  
{  
    static void Main()  
    {  
#if (DEBUG)  
        Console.WriteLine("Debugging is enabled.");  
#endif  
  
#if (TRACE)  
     Console.WriteLine("Tracing is enabled.");  
#endif  
    }  
}  
// Output:  
// Debugging is enabled.  
```  
  
 シンボルの定義を解除する方法の例については、「[#undef](./preprocessor-undef.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# プリプロセッサ ディレクティブ](./index.md)
- [const](../keywords/const.md)
- [方法: トレースとデバッグを指定して条件付きコンパイルを実行する](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
- [#undef](./preprocessor-undef.md)
- [#if](./preprocessor-if.md)
