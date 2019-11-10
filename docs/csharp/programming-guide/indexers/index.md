---
title: インデクサー - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: 02dc8c21b86438c801fb151d9f02a223b60d6197
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423228"
---
# <a name="indexers-c-programming-guide"></a>インデクサー (C# プログラミング ガイド)

インデクサーを使用すると、配列と同じようにクラスまたは構造体のインスタンスにインデックスを作成することができます。 インデックス値は、型またはインスタンス メンバーの明示的な指定なしで設定または取得できます。 インデクサーは[プロパティ](../classes-and-structs/properties.md)と似ていますが、そのアクセサーがパラメーターを取る点が異なります。  

 次の例は、値の割り当てと取得を行う単純な [get](../../language-reference/keywords/get.md) アクセサー メソッドと [set](../../language-reference/keywords/set.md) アクセサー メソッドを持つジェネリック クラスを定義します。 `Program` クラスは、文字列の格納用にこのクラスのインスタンスを作成します。  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
> その他の例については、「[関連セクション](./index.md#BKMK_RelatedSections)」を参照してください。  
  
## <a name="expression-body-definitions"></a>式の本文の定義  
 
通常は、インデクサーの get または set アクセサーは、値を返すか値を設定する単一のステートメントで構成します。 式の本文のメンバーは、このシナリオをサポートする簡略化された構文を提供します。 C# 6 以降、読み取り専用インデクサーは、次の例のように、式の本文のメンバーとして実装することができます。

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

式の本文は `=>` で導入され、`get` キーワードは使用されないことに注意してください。 

C# 7.0 以降、get アクセサーと set アクセサーのどちらも、式の本文のメンバーとして実装できます。 この場合、`get` キーワードと `set` キーワードの両方を使用する必要があります。 次に例を示します。

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a>インデクサーの概要  
  
- インデクサーを使用すると、配列と同じようにオブジェクトにインデックスを作成することができます。  
  
- `get` アクセサーは値を返します。 `set` アクセサーは値を割り当てます。  
  
- [this](../../language-reference/keywords/this.md) キーワードは、インデクサーの定義に使用されます。  
  
- [value](../../language-reference/keywords/value.md) キーワードは、`set` インデクサーによって割り当てられる値の定義に使用されます。  
  
- インデクサーは、整数値でインデックスを指定する必要はありません。個々の検索メカニズムの定義方法によります。  
  
- インデクサーはオーバーロードすることができます。  
  
- インデクサーには、2 次元配列にアクセスする場合など、複数の仮パラメーターを指定できます。  
  
## <a name="BKMK_RelatedSections"></a> 関連セクション  
  
- [インデクサーの使用](./using-indexers.md)  
  
- [インターフェイスのインデクサー](./indexers-in-interfaces.md)  
  
- [プロパティとインデクサーの比較](./comparison-between-properties-and-indexers.md)  
  
- [アクセサーのアクセシビリティの制限](../classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a>C# 言語仕様  

詳細については、「[C# 言語の仕様](/dotnet/csharp/language-reference/language-specification/introduction)」の「[インデクサー](~/_csharplang/spec/classes.md#indexers)」を参照してください。 言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [プロパティ](../classes-and-structs/properties.md)
