---
title: コンストラクター '<name>' はそれ自体を呼び出すことはできません。
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 8459ee7fec6d761161a721c88ccdc88e513fc95f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936696"
---
# <a name="constructor-name-cannot-call-itself"></a><span data-ttu-id="eb30e-102">コンストラクター '\<name>' はそれ自体を呼び出すことはできません</span><span class="sxs-lookup"><span data-stu-id="eb30e-102">Constructor '\<name>' cannot call itself</span></span>
<span data-ttu-id="eb30e-103">クラスまたは構造体の `Sub New` プロシージャはそれ自体を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="eb30e-103">A `Sub New` procedure in a class or structure calls itself.</span></span>  
  
 <span data-ttu-id="eb30e-104">コンストラクターの目的は、クラスまたは構造体が最初に作成されたときにそのインスタンスを初期化することです。</span><span class="sxs-lookup"><span data-stu-id="eb30e-104">The purpose of a constructor is to initialize an instance of a class or structure when it is first created.</span></span> <span data-ttu-id="eb30e-105">クラスまたは構造体には、すべてに異なるパラメーター リストが含まれていれば、複数のコンストラクターを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="eb30e-105">A class or structure can have several constructors, provided they all have different parameter lists.</span></span> <span data-ttu-id="eb30e-106">コンストラクターは、別のコンストラクターを呼び出して、独自の機能だけでなくその機能も実行することができます。</span><span class="sxs-lookup"><span data-stu-id="eb30e-106">A constructor is permitted to call another constructor to perform its functionality in addition to its own.</span></span> <span data-ttu-id="eb30e-107">ただし、コンストラクターがそれ自体を呼び出す場合は意味がありません。許可されている場合、実際にはこれは無限再帰になります。</span><span class="sxs-lookup"><span data-stu-id="eb30e-107">But it is meaningless for a constructor to call itself, and in fact it would result in infinite recursion if permitted.</span></span>  
  
 <span data-ttu-id="eb30e-108">**エラー ID:** BC30298</span><span class="sxs-lookup"><span data-stu-id="eb30e-108">**Error ID:** BC30298</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="eb30e-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="eb30e-109">To correct this error</span></span>  
  
1. <span data-ttu-id="eb30e-110">呼び出されるコンストラクターのパラメーター リストを確認します。</span><span class="sxs-lookup"><span data-stu-id="eb30e-110">Check the parameter list of the constructor being called.</span></span> <span data-ttu-id="eb30e-111">これは、呼び出しを行うコンストラクターのものと異なる必要があります。</span><span class="sxs-lookup"><span data-stu-id="eb30e-111">It should be different from that of the constructor making the call.</span></span>  
  
2. <span data-ttu-id="eb30e-112">別のコンストラクターを呼び出さない場合は、`Sub New` 呼び出しを完全に削除します。</span><span class="sxs-lookup"><span data-stu-id="eb30e-112">If you do not intend to call a different constructor, remove the `Sub New` call entirely.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb30e-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb30e-113">See also</span></span>

- [<span data-ttu-id="eb30e-114">オブジェクトの有効期間:オブジェクトの作成と破棄</span><span class="sxs-lookup"><span data-stu-id="eb30e-114">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
