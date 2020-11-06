---
title: 共通言語ランタイムでの型の転送
description: 型の転送を使用すると、別の .NET アセンブリに型を移動する際に、元のアセンブリを使用するアプリケーションを再コンパイルする必要がありません。
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
dev_langs:
- csharp
- cpp
ms.openlocfilehash: cd166068993fb5d1a5164615de3926a06dda8098
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687673"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>共通言語ランタイムでの型の転送

型の転送を使用すると、別のアセンブリに型を移動する際に、元のアセンブリを使用するアプリケーションを再コンパイルする必要がありません。  
  
 たとえば、 *Utility.dll* というアセンブリ内の `Example` クラスをアプリケーションが使用しているとします。 その場合、 *Utility.dll* の開発者がアセンブリをリファクタリングすることになった際には、その過程で `Example` クラスが別のアセンブリに移動される可能性があります。 *Utility.dll* の旧バージョンが *Utility.dll* の新バージョンとそのコンパニオン アセンブリに置き換えられると、`Example` クラスを使用するアプリケーションは、新しいバージョンの *Utility.dll* で `Example` クラスを見つけられないために失敗します。  
  
 *Utility.dll* の開発者は、<xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> 属性を使用して、`Example` クラスの要求を転送することで、この問題を回避できます。 この属性が新バージョンの *Utility.dll* に適用されている場合、`Example` クラスに対する要求は、現在このクラスを含んでいるアセンブリに転送されます。 既存のアプリケーションは、再コンパイルを必要とすることなく正常に機能し続けます。

## <a name="forward-a-type"></a>型の転送

 型の転送は 4 つの手順で行います。  
  
1. 型のソース コードを、元のアセンブリから転送先のアセンブリに移動します。  

2. 配置に使用される型のアセンブリで、移動された型の <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> を追加します。 次のコードは、移動された `Example` という型の属性を示しています。  

   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```

   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  

3. 型の現在の場所であるアセンブリをコンパイルします。  

4. 型の現在の場所であるアセンブリへの参照を指定して、型の元の場所であるアセンブリを再コンパイルします。 たとえば、C# ファイルをコマンド ラインからコンパイルする場合は、[-reference (C# コンパイラ オプション)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) オプションを使用して、型の現在の場所であるアセンブリを指定します。 C++ では、ソース ファイルで [#using](/cpp/preprocessor/hash-using-directive-cpp) ディレクティブを使用して、型の現在の場所であるアセンブリを指定します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [型の転送 (C++/CLI)](/cpp/windows/type-forwarding-cpp-cli)
- [#using ディレクティブ](/cpp/preprocessor/hash-using-directive-cpp)
