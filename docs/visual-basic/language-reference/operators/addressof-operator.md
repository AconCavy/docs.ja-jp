---
title: AddressOf 演算子
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: edce7d4a2268bd311045ea4972672fe8fd2600ea
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874895"
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="eb69a-102">AddressOf 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb69a-102">AddressOf Operator (Visual Basic)</span></span>

<span data-ttu-id="eb69a-103">特定のプロシージャを参照するデリゲート インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="eb69a-103">Creates a delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb69a-104">構文</span><span class="sxs-lookup"><span data-stu-id="eb69a-104">Syntax</span></span>  
  
```vb  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="eb69a-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="eb69a-105">Parts</span></span>  

 `procedurename`  
 <span data-ttu-id="eb69a-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="eb69a-106">Required.</span></span> <span data-ttu-id="eb69a-107">新しく作成されたデリゲートによって参照されるプロシージャを指定します。</span><span class="sxs-lookup"><span data-stu-id="eb69a-107">Specifies the procedure to be referenced by the newly created delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb69a-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="eb69a-108">Remarks</span></span>  

 <span data-ttu-id="eb69a-109">`AddressOf` 演算子では、`procedurename` によって指定されたサブまたは関数を指すデリゲートを作成します。</span><span class="sxs-lookup"><span data-stu-id="eb69a-109">The `AddressOf` operator creates a delegate that points to the sub or function specified by `procedurename`.</span></span> <span data-ttu-id="eb69a-110">指定されたプロシージャがインスタンス メソッドの場合、デリゲートはインスタンスとメソッドの両方を参照します。</span><span class="sxs-lookup"><span data-stu-id="eb69a-110">When the specified procedure is an instance method then the delegate refers to both the instance and the method.</span></span> <span data-ttu-id="eb69a-111">次に、デリゲートが呼び出されると、指定したインスタンスの指定したメソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="eb69a-111">Then, when the  delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="eb69a-112">`AddressOf` 演算子は、デリゲート コンストラクターのオペランドとして使用することも、コンパイラによってデリゲートの型を決定できるコンテキストで使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="eb69a-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb69a-113">例</span><span class="sxs-lookup"><span data-stu-id="eb69a-113">Example</span></span>  

 <span data-ttu-id="eb69a-114">この例では、`AddressOf` 演算子を使用して、ボタンの `Click` イベントを処理するデリゲートを指定します。</span><span class="sxs-lookup"><span data-stu-id="eb69a-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="eb69a-115">例</span><span class="sxs-lookup"><span data-stu-id="eb69a-115">Example</span></span>  

 <span data-ttu-id="eb69a-116">次の例では、`AddressOf` 演算子を使用して、スレッドのスタートアップ関数を指定します。</span><span class="sxs-lookup"><span data-stu-id="eb69a-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="eb69a-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb69a-117">See also</span></span>

- [<span data-ttu-id="eb69a-118">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="eb69a-118">Declare Statement</span></span>](../statements/declare-statement.md)
- [<span data-ttu-id="eb69a-119">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="eb69a-119">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="eb69a-120">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="eb69a-120">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="eb69a-121">デリゲート</span><span class="sxs-lookup"><span data-stu-id="eb69a-121">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
