---
description: '#elif - C# リファレンス'
title: '#elif - C# リファレンス'
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: 383c143792a39bb3abcd255804360ad5e2f8ef74
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168700"
---
# <a name="elif-c-reference"></a>#elif (C# リファレンス)

`#elif` を使用すると、複合条件付きディレクティブを作成できます。 `#elif` 式が評価されるのは、先行するディレクティブ式 [#if](./preprocessor-if.md) および `#elif` (オプション) が `true` と評価されなかった場合です。 `#elif` 式が `true` と評価された場合は、`#elif` と次の条件付きディレクティブの間にあるすべてのコードが、コンパイラによって評価されます。 次に例を示します。  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 複数のシンボルを評価するときには、`==` (等値)、`!=` (非等値)、`&&` (AND)、および `||` (OR) の演算子を使用できます。 シンボルと演算子は、かっこを使用してグループ化できます。  
  
## <a name="remarks"></a>注釈  

 `#elif` では、次のように記述した場合と同じ結果が得られます。  
  
```csharp
#else  
#if  
```  
  
 `#elif` を使用する方が簡単です。`#if` には対になる [#endif](./preprocessor-endif.md) が必要ですが、`#elif` では対応する `#endif` が不要なためです。  
  
 `#elif` の使用例については、「[#if](./preprocessor-if.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# プリプロセッサ ディレクティブ](./index.md)
