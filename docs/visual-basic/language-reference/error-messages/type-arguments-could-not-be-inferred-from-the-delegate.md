---
title: 型引数をデリゲートから推論できませんでした
ms.date: 07/20/2015
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
ms.openlocfilehash: f29e92c8245e33c0418d9a387070b03f645c331e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362749"
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a><span data-ttu-id="12c1e-102">型引数をデリゲートから推論できませんでした</span><span class="sxs-lookup"><span data-stu-id="12c1e-102">Type arguments could not be inferred from the delegate</span></span>
<span data-ttu-id="12c1e-103">代入ステートメントは、 `AddressOf` を使用してジェネリック プロシージャのアドレスをデリゲートに割り当てますが、ジェネリック プロシージャに型引数を指定していません。</span><span class="sxs-lookup"><span data-stu-id="12c1e-103">An assignment statement uses `AddressOf` to assign the address of a generic procedure to a delegate, but it does not supply any type arguments to the generic procedure.</span></span>  
  
 <span data-ttu-id="12c1e-104">通常、ジェネリック型を呼び出す場合は、ジェネリック型が定義する型パラメーターごとに型引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="12c1e-104">Normally, when you invoke a generic type, you supply a type argument for each type parameter that the generic type defines.</span></span> <span data-ttu-id="12c1e-105">型引数を指定しない場合、コンパイラは型パラメーターに渡される型を推論しようとします。</span><span class="sxs-lookup"><span data-stu-id="12c1e-105">If you do not supply any type arguments, the compiler attempts to infer the types to be passed to the type parameters.</span></span> <span data-ttu-id="12c1e-106">コンテキストにコンパイラが型を推論するのに十分な情報が提供されていない場合は、エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="12c1e-106">If the context does not provide enough information for the compiler to infer the types, an error is generated.</span></span>  
  
 <span data-ttu-id="12c1e-107">**エラー ID:** BC36564</span><span class="sxs-lookup"><span data-stu-id="12c1e-107">**Error ID:** BC36564</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="12c1e-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="12c1e-108">To correct this error</span></span>  
  
- <span data-ttu-id="12c1e-109">ジェネリック プロシージャの型引数を `AddressOf` 式で指定します。</span><span class="sxs-lookup"><span data-stu-id="12c1e-109">Specify the type arguments for the generic procedure in the `AddressOf` expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12c1e-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="12c1e-110">See also</span></span>

- [<span data-ttu-id="12c1e-111">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="12c1e-111">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="12c1e-112">AddressOf 演算子</span><span class="sxs-lookup"><span data-stu-id="12c1e-112">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="12c1e-113">Generic Procedures in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="12c1e-113">Generic Procedures in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-procedures.md)
- [<span data-ttu-id="12c1e-114">型リスト</span><span class="sxs-lookup"><span data-stu-id="12c1e-114">Type List</span></span>](../statements/type-list.md)
- [<span data-ttu-id="12c1e-115">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="12c1e-115">Extension Methods</span></span>](../../programming-guide/language-features/procedures/extension-methods.md)
