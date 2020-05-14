---
title: 変数 '<variablename>' の型は、外側のスコープ内のフィールドにバインドされているため、推論できません。
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: e56529919945558df178e18a83a895a79bfe4919
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512724"
---
# <a name="the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a><span data-ttu-id="9b0bb-102">変数 '\<variablename>' の型は、外側のスコープ内のフィールドにバインドされているため、推論できません</span><span class="sxs-lookup"><span data-stu-id="9b0bb-102">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope</span></span>

<span data-ttu-id="9b0bb-103">変数 '\<variablename>' の型は、外側のスコープ内のフィールドにバインドされているため、推論できません。</span><span class="sxs-lookup"><span data-stu-id="9b0bb-103">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope.</span></span> <span data-ttu-id="9b0bb-104">'\<variablename>' の名前を変更するか、完全修飾名 (例: 'Me.variablename' や 'MyBase.variablename') を使用してください。</span><span class="sxs-lookup"><span data-stu-id="9b0bb-104">Either change the name of '\<variablename>', or use the fully qualified name (for example, 'Me.variablename' or 'MyBase.variablename').</span></span>

<span data-ttu-id="9b0bb-105">コードのループ制御変数は、クラスまたは他の外側のスコープ内のフィールドと同じ名前を持っています。</span><span class="sxs-lookup"><span data-stu-id="9b0bb-105">A loop control variable in your code has the same name as a field of the class or other enclosing scope.</span></span> <span data-ttu-id="9b0bb-106">制御変数は、`As` 句なしで使用されるため、外側のスコープ内のフィールドにバインドされ、コンパイラがこれに対して新しい変数を作成したり、その型を推論したりすることはありません。</span><span class="sxs-lookup"><span data-stu-id="9b0bb-106">Because the control variable is used without an `As` clause, it is bound to the field in the enclosing scope, and the compiler does not create a new variable for it or infer its type.</span></span>

<span data-ttu-id="9b0bb-107">次の例では、`Index` (`For` ステートメントの制御変数) が、`Index` クラスの `Customer` フィールドにバインドされています。</span><span class="sxs-lookup"><span data-stu-id="9b0bb-107">In the following example, `Index`, the control variable in the `For` statement, is bound to the `Index` field in the `Customer` class.</span></span> <span data-ttu-id="9b0bb-108">コンパイラが制御変数 `Index` に対して新しい変数を作成したり、その型を推論したりすることはありません。</span><span class="sxs-lookup"><span data-stu-id="9b0bb-108">The compiler does not create a new variable for the control variable `Index` or infer its type.</span></span>

```vb
Class Customer

    ' The class has a field named Index.
    Private Index As Integer

    Sub Main()

    ' The following line will raise this warning.
        For Index = 1 To 10
            ' ...
        Next

    End Sub
End Class
```

<span data-ttu-id="9b0bb-109">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="9b0bb-109">By default, this message is a warning.</span></span> <span data-ttu-id="9b0bb-110">警告を表示しない方法や、警告をエラーとして扱う方法については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b0bb-110">For information about how to hide warnings or how to treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

<span data-ttu-id="9b0bb-111">**エラー ID:** BC42110</span><span class="sxs-lookup"><span data-stu-id="9b0bb-111">**Error ID:** BC42110</span></span>

### <a name="to-address-this-warning"></a><span data-ttu-id="9b0bb-112">この警告に対処するには</span><span class="sxs-lookup"><span data-stu-id="9b0bb-112">To address this warning</span></span>

- <span data-ttu-id="9b0bb-113">ループ制御変数の名前を、クラスのフィールドの名前とは異なる識別子に変更して、この変数をローカルにします。</span><span class="sxs-lookup"><span data-stu-id="9b0bb-113">Make the loop control variable local by changing its name to an identifier that is not also the name of a field of the class.</span></span>

  ```vb
  For I = 1 To 10
  ```

- <span data-ttu-id="9b0bb-114">変数名の前に `Me.` を付けることにより、クラス フィールドにループ制御変数がバインドされていることを明確にします。</span><span class="sxs-lookup"><span data-stu-id="9b0bb-114">Clarify that the loop control variable binds to the class field by prefixing `Me.` to the variable name.</span></span>

  ```vb
  For Me.Index = 1 To 10
  ```

- <span data-ttu-id="9b0bb-115">ローカル型の推定ではなく `As` 句を使用して、ループ制御変数に型を指定します。</span><span class="sxs-lookup"><span data-stu-id="9b0bb-115">Instead of relying on local type inference, use an `As` clause to specify a type for the loop control variable.</span></span>

  ```vb
  For Index As Integer = 1 To 10
  ```

## <a name="example"></a><span data-ttu-id="9b0bb-116">例</span><span class="sxs-lookup"><span data-stu-id="9b0bb-116">Example</span></span>
 <span data-ttu-id="9b0bb-117">次のコードは、上の例に最初の修正を行ったものです。</span><span class="sxs-lookup"><span data-stu-id="9b0bb-117">The following code shows the earlier example with the first correction in place.</span></span>

```vb
Class Customer

    ' The class has a field named Index.
    Private Index As Integer

    Sub Main()

        For I = 1 To 10
            ' ...
        Next

    End Sub
End Class
```

## <a name="see-also"></a><span data-ttu-id="9b0bb-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b0bb-118">See also</span></span>

- [<span data-ttu-id="9b0bb-119">Option Infer ステートメント</span><span class="sxs-lookup"><span data-stu-id="9b0bb-119">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="9b0bb-120">For Each...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="9b0bb-120">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="9b0bb-121">For...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="9b0bb-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="9b0bb-122">方法: オブジェクトの現在のインスタンスを参照する</span><span class="sxs-lookup"><span data-stu-id="9b0bb-122">How to: Refer to the Current Instance of an Object</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [<span data-ttu-id="9b0bb-123">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="9b0bb-123">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="9b0bb-124">Me、My、MyBase、および MyClass</span><span class="sxs-lookup"><span data-stu-id="9b0bb-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
