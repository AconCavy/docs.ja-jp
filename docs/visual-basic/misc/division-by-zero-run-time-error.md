---
title: 0 による除算 (Visual Basic 実行時エラー)
ms.date: 07/20/2015
f1_keywords:
- vbrID11
ms.assetid: 5b9bc5d6-792e-48bc-a974-012e07ad95f3
ms.openlocfilehash: 2dc36123478c0946b3ba5931dcc283acc08920cc
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/23/2020
ms.locfileid: "91084360"
---
# <a name="division-by-zero-visual-basic-run-time-error"></a><span data-ttu-id="b8899-102">0 による除算 (Visual Basic 実行時エラー)</span><span class="sxs-lookup"><span data-stu-id="b8899-102">Division by zero (Visual Basic Run-Time Error)</span></span>

<span data-ttu-id="b8899-103">除数として使用する式の値が 0 です。</span><span class="sxs-lookup"><span data-stu-id="b8899-103">An expression being used as a divisor has a value of zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b8899-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="b8899-104">To correct this error</span></span>  
  
1. <span data-ttu-id="b8899-105">式の変数のスペルを確認します。</span><span class="sxs-lookup"><span data-stu-id="b8899-105">Check the spelling of variables in the expression.</span></span> <span data-ttu-id="b8899-106">変数名のスペルが間違っていると、0 に初期化される数値型の変数が暗黙的に生成されることがあります。</span><span class="sxs-lookup"><span data-stu-id="b8899-106">A misspelled variable name can implicitly create a numeric variable that is initialized to zero.</span></span>  
  
2. <span data-ttu-id="b8899-107">式の変数 (特に、他のプロシージャから引数としてプロシージャに渡されたもの) に対してこれまで実行した操作を確認します。</span><span class="sxs-lookup"><span data-stu-id="b8899-107">Check previous operations on variables in the expression, especially those passed into the procedure as arguments from other procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8899-108">こちらもご覧ください</span><span class="sxs-lookup"><span data-stu-id="b8899-108">See also</span></span>

- [<span data-ttu-id="b8899-109">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="b8899-109">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
