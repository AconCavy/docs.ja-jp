---
title: 引数 'NPer' は 0 より大きくなければなりません
ms.date: 07/20/2015
f1_keywords:
- vbrRate_NPerMustBeGTZero
ms.assetid: d49242df-dbd1-4b26-bd8c-ed56d24fdfcd
ms.openlocfilehash: f0185e30cb711472105955f5febf8d7702b29c72
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/23/2020
ms.locfileid: "91087142"
---
# <a name="argument-nper-must-be-greater-than-zero"></a><span data-ttu-id="84bf5-102">引数 'NPer' は 0 より大きくなければなりません</span><span class="sxs-lookup"><span data-stu-id="84bf5-102">Argument 'NPer' must be greater than zero</span></span>

<span data-ttu-id="84bf5-103">`NPer` 関数 (定期定額払いおよび固定金利に基づいて年金の期間を指定する `Double` を返します) には、0 を超える引数が必要です。</span><span class="sxs-lookup"><span data-stu-id="84bf5-103">The `NPer` function, which returns a `Double` specifying the number of periods for an annuity based on periodic fixed payments and a fixed interest rate, requires an argument greater than zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="84bf5-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="84bf5-104">To correct this error</span></span>  
  
- <span data-ttu-id="84bf5-105">式の引数のスペルを確認します。</span><span class="sxs-lookup"><span data-stu-id="84bf5-105">Check the spelling of arguments in the expression.</span></span> <span data-ttu-id="84bf5-106">変数名のスペルが間違っていると、0 に初期化される数値型の変数が暗黙的に生成されることがあります。</span><span class="sxs-lookup"><span data-stu-id="84bf5-106">A misspelled variable name can implicitly create a numeric variable that is initialized to zero.</span></span>  
  
- <span data-ttu-id="84bf5-107">式の変数 (特に、他のプロシージャから引数としてプロシージャに渡されたもの) に対してこれまで実行した操作を確認します。</span><span class="sxs-lookup"><span data-stu-id="84bf5-107">Check previous operations on variables in the expression, especially those passed into the procedure as arguments from other procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84bf5-108">こちらもご覧ください</span><span class="sxs-lookup"><span data-stu-id="84bf5-108">See also</span></span>

- [<span data-ttu-id="84bf5-109">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="84bf5-109">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
