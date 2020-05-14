---
title: Expression は値であるため、代入式のターゲットにすることはできません。
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: d5aae4d30abbf9ed2af260412352a5e0452e0dcc
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/26/2019
ms.locfileid: "68513033"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a><span data-ttu-id="bee8f-102">Expression は値であるため、代入式のターゲットにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="bee8f-102">Expression is a value and therefore cannot be the target of an assignment</span></span>

<span data-ttu-id="bee8f-103">ステートメントで式に値を代入しようとしています。</span><span class="sxs-lookup"><span data-stu-id="bee8f-103">A statement attempts to assign a value to an expression.</span></span> <span data-ttu-id="bee8f-104">実行時に値を代入できるのは、書き込み可能な変数、プロパティ、または配列要素だけです。</span><span class="sxs-lookup"><span data-stu-id="bee8f-104">You can assign a value only to a writable variable, property, or array element at run time.</span></span> <span data-ttu-id="bee8f-105">次の例では、このエラーがどのように発生する可能性があるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="bee8f-105">The following example illustrates how this error can occur.</span></span>

```vb
Dim yesterday As Integer
ReadOnly maximum As Integer = 45
yesterday + 1 = DatePart(DateInterval.Day, Now)
' The preceding line is an ERROR because of an expression on the left.
maximum = 50
' The preceding line is an ERROR because maximum is declared ReadOnly.
```

<span data-ttu-id="bee8f-106">同様の例は、プロパティや配列要素にも当てはまる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bee8f-106">Similar examples could apply to properties and array elements.</span></span>

<span data-ttu-id="bee8f-107">**間接アクセス。**</span><span class="sxs-lookup"><span data-stu-id="bee8f-107">**Indirect Access.**</span></span> <span data-ttu-id="bee8f-108">値の型による間接アクセスによって、このエラーが発生することもあります。</span><span class="sxs-lookup"><span data-stu-id="bee8f-108">Indirect access through a value type can also generate this error.</span></span> <span data-ttu-id="bee8f-109">次のコード例を考えてみます。ここでは、<xref:System.Windows.Forms.Control.Location%2A> 経由で間接的にアクセスすることによって、<xref:System.Drawing.Point> の値を設定しようとしています。</span><span class="sxs-lookup"><span data-stu-id="bee8f-109">Consider the following code example, which attempts to set the value of <xref:System.Drawing.Point> by accessing it indirectly through <xref:System.Windows.Forms.Control.Location%2A>.</span></span>

```vb
' Assume this code runs inside Form1.
Dim exitButton As New System.Windows.Forms.Button()
exitButton.Text = "Exit this form"
exitButton.Location.X = 140
' The preceding line is an ERROR because of no storage for Location.
```

<span data-ttu-id="bee8f-110">前の例の最後のステートメントは、<xref:System.Windows.Forms.Control.Location%2A> プロパティによって返される <xref:System.Drawing.Point> 構造体の一時的な割り当てのみを作成しているため、失敗します。</span><span class="sxs-lookup"><span data-stu-id="bee8f-110">The last statement of the preceding example fails because it creates only a temporary allocation for the <xref:System.Drawing.Point> structure returned by the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span> <span data-ttu-id="bee8f-111">構造体は値の型であり、一時的な構造体は、ステートメントの実行後に保持されません。</span><span class="sxs-lookup"><span data-stu-id="bee8f-111">A structure is a value type, and the temporary structure is not retained after the statement runs.</span></span> <span data-ttu-id="bee8f-112">この問題を解決するには、<xref:System.Windows.Forms.Control.Location%2A> の変数を宣言して使用します。これにより、<xref:System.Drawing.Point> 構造体のより永続的な割り当てが作成されます。</span><span class="sxs-lookup"><span data-stu-id="bee8f-112">The problem is resolved by declaring and using a variable for <xref:System.Windows.Forms.Control.Location%2A>, which creates a more permanent allocation for the <xref:System.Drawing.Point> structure.</span></span> <span data-ttu-id="bee8f-113">次の例に、前の例の最後のステートメントを置き換えることができるコードを示しています。</span><span class="sxs-lookup"><span data-stu-id="bee8f-113">The following example shows code that can replace the last statement of the preceding example.</span></span>

```vb
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)
exitButton.Location = exitLocation
```

<span data-ttu-id="bee8f-114">**エラー ID:** BC30068</span><span class="sxs-lookup"><span data-stu-id="bee8f-114">**Error ID:** BC30068</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="bee8f-115">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="bee8f-115">To correct this error</span></span>

- <span data-ttu-id="bee8f-116">ステートメントで式に値を代入している場合は、式を 1 つの書き込み可能な変数、プロパティ、または配列要素に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="bee8f-116">If the statement assigns a value to an expression, replace the expression with a single writable variable, property, or array element.</span></span>

- <span data-ttu-id="bee8f-117">ステートメントで値の型 (通常は構造体) を介して間接的にアクセスしている場合は、値の型を保持する変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="bee8f-117">If the statement makes indirect access through a value type (usually a structure), create a variable to hold the value type.</span></span>

- <span data-ttu-id="bee8f-118">変数に適切な構造体 (またはその他の値の型) を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="bee8f-118">Assign the appropriate structure (or other value type) to the variable.</span></span>

- <span data-ttu-id="bee8f-119">変数を使用してプロパティにアクセスし、それに値を代入します。</span><span class="sxs-lookup"><span data-stu-id="bee8f-119">Use the variable to access the property to assign it a value.</span></span>

## <a name="see-also"></a><span data-ttu-id="bee8f-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="bee8f-120">See also</span></span>

- [<span data-ttu-id="bee8f-121">演算子および式</span><span class="sxs-lookup"><span data-stu-id="bee8f-121">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="bee8f-122">ステートメント</span><span class="sxs-lookup"><span data-stu-id="bee8f-122">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="bee8f-123">プロシージャのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="bee8f-123">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
