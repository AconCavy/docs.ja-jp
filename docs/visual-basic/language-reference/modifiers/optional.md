---
title: ［オプション］
ms.date: 07/20/2015
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
ms.openlocfilehash: a16dae35bf4bc84d95501624c4f023f390a8dda8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351434"
---
# <a name="optional-visual-basic"></a><span data-ttu-id="c76f1-102">Optional (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c76f1-102">Optional (Visual Basic)</span></span>

<span data-ttu-id="c76f1-103">プロシージャを呼び出すときにプロシージャ引数を省略できることを指定します。</span><span class="sxs-lookup"><span data-stu-id="c76f1-103">Specifies that a procedure argument can be omitted when the procedure is called.</span></span>

## <a name="remarks"></a><span data-ttu-id="c76f1-104">コメント</span><span class="sxs-lookup"><span data-stu-id="c76f1-104">Remarks</span></span>

<span data-ttu-id="c76f1-105">省略可能なパラメーターごとに、そのパラメーターの既定値として定数式を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c76f1-105">For each optional parameter, you must specify a constant expression as the default value of that parameter.</span></span> <span data-ttu-id="c76f1-106">式が[Nothing](../../../visual-basic/language-reference/nothing.md)と評価された場合、値のデータ型の既定値がパラメーターの既定値として使用されます。</span><span class="sxs-lookup"><span data-stu-id="c76f1-106">If the expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the default value of the value data type is used as the default value of the parameter.</span></span>

<span data-ttu-id="c76f1-107">パラメーターリストに省略可能なパラメーターが含まれている場合は、その後に続くすべてのパラメーターも省略可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c76f1-107">If the parameter list contains an optional parameter, every parameter that follows it must also be optional.</span></span>

<span data-ttu-id="c76f1-108">`Optional` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="c76f1-108">The `Optional` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="c76f1-109">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="c76f1-109">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)

- [<span data-ttu-id="c76f1-110">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="c76f1-110">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- [<span data-ttu-id="c76f1-111">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="c76f1-111">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- [<span data-ttu-id="c76f1-112">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="c76f1-112">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

> [!NOTE]
> <span data-ttu-id="c76f1-113">省略可能なパラメーターを指定して、または使用せずにプロシージャを呼び出すと、位置または名前によって引数を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="c76f1-113">When calling a procedure with or without optional parameters, you can pass arguments by position or by name.</span></span> <span data-ttu-id="c76f1-114">詳細については、「[位置と名前による引数の引き渡し](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c76f1-114">For more information, see [Passing Arguments by Position and by Name](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span></span>

> [!NOTE]
> <span data-ttu-id="c76f1-115">オーバーロードを使用して、省略可能なパラメーターを持つプロシージャを定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="c76f1-115">You can also define a procedure with optional parameters by using overloading.</span></span> <span data-ttu-id="c76f1-116">省略可能なパラメーターが1つある場合は、2つのオーバーロードされたバージョンのプロシージャを定義できます。1つはパラメーターを受け取り、もう1つはパラメーターを受け入れません。</span><span class="sxs-lookup"><span data-stu-id="c76f1-116">If you have one optional parameter, you can define two overloaded versions of the procedure, one that accepts the parameter and one that doesn’t.</span></span> <span data-ttu-id="c76f1-117">詳細については、「 [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c76f1-117">For more information, see [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>

## <a name="example"></a><span data-ttu-id="c76f1-118">例</span><span class="sxs-lookup"><span data-stu-id="c76f1-118">Example</span></span>

<span data-ttu-id="c76f1-119">次の例では、省略可能なパラメーターを持つプロシージャを定義します。</span><span class="sxs-lookup"><span data-stu-id="c76f1-119">The following example defines a procedure that has an optional parameter.</span></span>

```vb
Public Function FindMatches(ByRef values As List(Of String),
                            ByVal searchString As String,
                            Optional ByVal matchCase As Boolean = False) As List(Of String)

    Dim results As IEnumerable(Of String)

    If matchCase Then
        results = From v In values
                  Where v.Contains(searchString)
    Else
        results = From v In values
                  Where UCase(v).Contains(UCase(searchString))
    End If

    Return results.ToList()
End Function
```

## <a name="example"></a><span data-ttu-id="c76f1-120">例</span><span class="sxs-lookup"><span data-stu-id="c76f1-120">Example</span></span>

<span data-ttu-id="c76f1-121">次の例では、位置によって渡される引数と、名前で渡される引数を使用してプロシージャを呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c76f1-121">The following example demonstrates how to call a procedure with arguments passed by position and with arguments passed by name.</span></span> <span data-ttu-id="c76f1-122">プロシージャには、2つの省略可能なパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="c76f1-122">The procedure has two optional parameters.</span></span>

[!code-vb[VbVbalrKeywords#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class8.vb#21)]

## <a name="see-also"></a><span data-ttu-id="c76f1-123">参照</span><span class="sxs-lookup"><span data-stu-id="c76f1-123">See also</span></span>

- [<span data-ttu-id="c76f1-124">パラメーター リスト</span><span class="sxs-lookup"><span data-stu-id="c76f1-124">Parameter List</span></span>](../../../visual-basic/language-reference/statements/parameter-list.md)
- [<span data-ttu-id="c76f1-125">省略可能なパラメーター</span><span class="sxs-lookup"><span data-stu-id="c76f1-125">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="c76f1-126">キーワード</span><span class="sxs-lookup"><span data-stu-id="c76f1-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
