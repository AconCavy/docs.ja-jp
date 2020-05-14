---
title: <type1>'<typename>' は、インターフェイス '<interfacename>' に対して '<methodname>' を実装しなければなりません。
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: c387b0225375f4675042bef593b23a084305b4fd
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591592"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a><span data-ttu-id="3c896-102">\<type1>'\<typename>' は、インターフェイス '\<interfacename>' に対して '\<methodname>' を実装しなければなりません</span><span class="sxs-lookup"><span data-stu-id="3c896-102">\<type1>'\<typename>' must implement '\<methodname>' for interface '\<interfacename>'</span></span>
<span data-ttu-id="3c896-103">クラスまたは構造体では、インターフェイスを実装することが要求されますが、インターフェイスによって定義されるプロシージャは実装しません。</span><span class="sxs-lookup"><span data-stu-id="3c896-103">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="3c896-104">インターフェイスのすべてのメンバーを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c896-104">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="3c896-105">**エラー ID:** BC30149</span><span class="sxs-lookup"><span data-stu-id="3c896-105">**Error ID:** BC30149</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3c896-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="3c896-106">To correct this error</span></span>  
  
1. <span data-ttu-id="3c896-107">インターフェイスで定義されているものと同じ名前およびシグネチャを持つプロシージャを宣言します。</span><span class="sxs-lookup"><span data-stu-id="3c896-107">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="3c896-108">少なくとも `End Function` または `End Sub` ステートメントを含めてください。</span><span class="sxs-lookup"><span data-stu-id="3c896-108">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>  
  
2. <span data-ttu-id="3c896-109">`Function` または `Sub` ステートメントの末尾に `Implements` 句を追加します。</span><span class="sxs-lookup"><span data-stu-id="3c896-109">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="3c896-110">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="3c896-110">For example:</span></span>  
  
    ```vb  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3c896-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c896-111">See also</span></span>

- [<span data-ttu-id="3c896-112">Implements ステートメント</span><span class="sxs-lookup"><span data-stu-id="3c896-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="3c896-113">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3c896-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
