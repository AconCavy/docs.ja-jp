---
title: ビットごとの演算子とシフト演算子 - C# リファレンス
description: 整数型のオペランドに対してビットごとの論理演算またはシフト演算を実行する C# の演算子について説明します。
ms.date: 04/18/2019
author: pkulikov
f1_keywords:
- ~_CSharpKeyword
- <<_CSharpKeyword
- '>>_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
- <<=_CSharpKeyword
- '>>=_CSharpKeyword'
helpviewer_keywords:
- bitwise logical operators [C#]
- shift operators [C#]
- tilde operator [C#]
- one's complement operator [C#]
- bitwise complement operator [C#]
- ~ operator [C#]
- left shift operator [C#]
- << operator [C#]
- right shift operator [C#]
- '>> operator [C#]'
- bitwise logical AND operator [C#]
- ampersand operator [C#]
- '& operator [C#]'
- bitwise logical exclusive OR operator [C#]
- bitwise logical XOR operator [C#]
- ^ operator [C#]
- bitwise logical OR operator [C#]
- '| operator [C#]'
ms.openlocfilehash: 99181855fdf8e937676e44e8b347510f9405aa3d
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916904"
---
# <a name="bitwise-and-shift-operators-c-reference"></a><span data-ttu-id="de04f-103">ビットごとの演算子とシフト演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="de04f-103">Bitwise and shift operators (C# reference)</span></span>

<span data-ttu-id="de04f-104">以下の演算子では、[整数型](../builtin-types/integral-numeric-types.md)または [char](../builtin-types/char.md) 型のオペランドに対してビットごとの演算またはシフト演算が実行されます。</span><span class="sxs-lookup"><span data-stu-id="de04f-104">The following operators perform bitwise or shift operations with operands of the [integral numeric types](../builtin-types/integral-numeric-types.md) or the [char](../builtin-types/char.md) type:</span></span>

- <span data-ttu-id="de04f-105">単項 [`~` (ビットごとの補数)](#bitwise-complement-operator-) 演算子</span><span class="sxs-lookup"><span data-stu-id="de04f-105">Unary [`~` (bitwise complement)](#bitwise-complement-operator-) operator</span></span>
- <span data-ttu-id="de04f-106">2 項 [`<<` (左シフト)](#left-shift-operator-) および [`>>` (右シフト)](#right-shift-operator-) シフト演算子</span><span class="sxs-lookup"><span data-stu-id="de04f-106">Binary [`<<` (left shift)](#left-shift-operator-) and [`>>` (right shift)](#right-shift-operator-) shift operators</span></span>
- <span data-ttu-id="de04f-107">2 項 [`&` (論理 AND)](#logical-and-operator-)、[`|` (論理 OR)](#logical-or-operator-)、および [`^` (論理排他的 OR)](#logical-exclusive-or-operator-) 演算子</span><span class="sxs-lookup"><span data-stu-id="de04f-107">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators</span></span>

<span data-ttu-id="de04f-108">これらの演算子は、`int`、`uint`、`long`、`ulong` 型に対して定義されています。</span><span class="sxs-lookup"><span data-stu-id="de04f-108">Those operators are defined for the `int`, `uint`, `long`, and `ulong` types.</span></span> <span data-ttu-id="de04f-109">両方のオペランドが他の整数型 (`sbyte`、`byte`、`short`、`ushort`、`char`) の場合、それらの値は `int` 型に変換され、演算の結果もその型になります。</span><span class="sxs-lookup"><span data-stu-id="de04f-109">When both operands are of other integral types (`sbyte`, `byte`, `short`, `ushort`, or `char`), their values are converted to the `int` type, which is also the result type of an operation.</span></span> <span data-ttu-id="de04f-110">オペランドが異なる整数型の場合、それらの値は最も近い含んでいる整数型に変換されます。</span><span class="sxs-lookup"><span data-stu-id="de04f-110">When operands are of different integral types, their values are converted to the closest containing integral type.</span></span> <span data-ttu-id="de04f-111">詳しくは、「[C# 言語仕様](~/_csharplang/spec/introduction.md)」の「[数値の上位変換](~/_csharplang/spec/expressions.md#numeric-promotions)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="de04f-111">For more information, see the [Numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="de04f-112">`&`、`|`、`^` の各演算子は、`bool` 型のオペランドに対しても定義されています。</span><span class="sxs-lookup"><span data-stu-id="de04f-112">The `&`, `|`, and `^` operators are also defined for operands of the `bool` type.</span></span> <span data-ttu-id="de04f-113">詳しくは、「[ブール論理演算子](boolean-logical-operators.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="de04f-113">For more information, see [Boolean logical operators](boolean-logical-operators.md).</span></span>

<span data-ttu-id="de04f-114">ビットごとの演算子およびシフト演算が原因でオーバーフローが発生することはなく、[checked と unchecked](../keywords/checked-and-unchecked.md) のコンテキストで同じ結果が生成されることはありません。</span><span class="sxs-lookup"><span data-stu-id="de04f-114">Bitwise and shift operations never cause overflow and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="bitwise-complement-operator-"></a><span data-ttu-id="de04f-115">ビットごとの補数演算子 ~</span><span class="sxs-lookup"><span data-stu-id="de04f-115">Bitwise complement operator ~</span></span>

<span data-ttu-id="de04f-116">`~` 演算子では、各ビットを反転させることにより、オペランドのビットごとの補数が生成されます。</span><span class="sxs-lookup"><span data-stu-id="de04f-116">The `~` operator produces a bitwise complement of its operand by reversing each bit:</span></span>

[!code-csharp-interactive[bitwise NOT](snippets/shared/BitwiseAndShiftOperators.cs#BitwiseComplement)]

<span data-ttu-id="de04f-117">`~` シンボルはファイナライザーの宣言にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="de04f-117">You can also use the `~` symbol to declare finalizers.</span></span> <span data-ttu-id="de04f-118">詳細については、「[Finalizers](../../programming-guide/classes-and-structs/destructors.md)」 (ファイナライザー) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de04f-118">For more information, see [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span></span>

## <a name="left-shift-operator-"></a><span data-ttu-id="de04f-119">左シフト演算子 \<\<</span><span class="sxs-lookup"><span data-stu-id="de04f-119">Left-shift operator \<\<</span></span>

<span data-ttu-id="de04f-120">`<<` 演算子では、左側のオペランドが、[右側のオペランドで定義されたビット数](#shift-count-of-the-shift-operators)だけ左にシフトされます。</span><span class="sxs-lookup"><span data-stu-id="de04f-120">The `<<` operator shifts its left-hand operand left by the [number of bits defined by its right-hand operand](#shift-count-of-the-shift-operators).</span></span>

<span data-ttu-id="de04f-121">次の例に示すように、左シフト演算子では、結果の型の範囲外にある上位ビットは破棄され、空の下位ビット位置は、ゼロに設定されます。</span><span class="sxs-lookup"><span data-stu-id="de04f-121">The left-shift operation discards the high-order bits that are outside the range of the result type and sets the low-order empty bit positions to zero, as the following example shows:</span></span>

[!code-csharp-interactive[left shift](snippets/shared/BitwiseAndShiftOperators.cs#LeftShift)]

<span data-ttu-id="de04f-122">シフト演算子は `int`、`uint`、`long`、`ulong` 型に対してのみ定義されるので、演算の結果には常に少なくとも 32 ビットが含まれます。</span><span class="sxs-lookup"><span data-stu-id="de04f-122">Because the shift operators are defined only for the `int`, `uint`, `long`, and `ulong` types, the result of an operation always contains at least 32 bits.</span></span> <span data-ttu-id="de04f-123">左側のオペランドが別の整数型 (`sbyte`、`byte`、`short`、`ushort`、`char`) の場合、次の例で示すように、その値は `int` 型に変換されます。</span><span class="sxs-lookup"><span data-stu-id="de04f-123">If the left-hand operand is of another integral type (`sbyte`, `byte`, `short`, `ushort`, or `char`), its value is converted to the `int` type, as the following example shows:</span></span>

[!code-csharp-interactive[left shift with promotion](snippets/shared/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

<span data-ttu-id="de04f-124">`<<` 演算子の右側のオペランドでのシフト数の定義方法については、「[シフト演算子のシフト数](#shift-count-of-the-shift-operators)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="de04f-124">For information about how the right-hand operand of the `<<` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="right-shift-operator-"></a><span data-ttu-id="de04f-125">右シフト演算子 >></span><span class="sxs-lookup"><span data-stu-id="de04f-125">Right-shift operator >></span></span>

<span data-ttu-id="de04f-126">`>>` 演算子では、左側のオペランドが、[右側のオペランドで定義されたビット数](#shift-count-of-the-shift-operators)だけ右にシフトされます。</span><span class="sxs-lookup"><span data-stu-id="de04f-126">The `>>` operator shifts its left-hand operand right by the [number of bits defined by its right-hand operand](#shift-count-of-the-shift-operators).</span></span>

<span data-ttu-id="de04f-127">次の例で示すように、右シフト演算では、下位ビットが破棄されます。</span><span class="sxs-lookup"><span data-stu-id="de04f-127">The right-shift operation discards the low-order bits, as the following example shows:</span></span>

[!code-csharp-interactive[right shift](snippets/shared/BitwiseAndShiftOperators.cs#RightShift)]

<span data-ttu-id="de04f-128">空の上位ビット位置は、左側のオペランドの型に基づいて次のように設定されます。</span><span class="sxs-lookup"><span data-stu-id="de04f-128">The high-order empty bit positions are set based on the type of the left-hand operand as follows:</span></span>

- <span data-ttu-id="de04f-129">左側のオペランドの型が `int` または `long` である場合、右シフト演算子では、"*算術*" シフトが実行されます: 左側のオペランドの最上位ビット (符号ビット) の値が空の上位ビット位置に反映されます。</span><span class="sxs-lookup"><span data-stu-id="de04f-129">If the left-hand operand is of type `int` or `long`, the right-shift operator performs an *arithmetic* shift: the value of the most significant bit (the sign bit) of the left-hand operand is propagated to the high-order empty bit positions.</span></span> <span data-ttu-id="de04f-130">つまり、左側のオペランドが負でない場合は空の上位ビット位置が 0 に設定され、負の場合は 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="de04f-130">That is, the high-order empty bit positions are set to zero if the left-hand operand is non-negative and set to one if it's negative.</span></span>

  [!code-csharp-interactive[arithmetic right shift](snippets/shared/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- <span data-ttu-id="de04f-131">左側のオペランドの型が `uint` または `ulong` である場合、右シフト演算子では、"*論理*" シフトが実行されます: 空の上位ビット位置は常に 0 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="de04f-131">If the left-hand operand is of type `uint` or `ulong`, the right-shift operator performs a *logical* shift: the high-order empty bit positions are always set to zero.</span></span>

  [!code-csharp-interactive[logical right shift](snippets/shared/BitwiseAndShiftOperators.cs#LogicalRightShift)]

<span data-ttu-id="de04f-132">`>>` 演算子の右側のオペランドでのシフト数の定義方法については、「[シフト演算子のシフト数](#shift-count-of-the-shift-operators)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="de04f-132">For information about how the right-hand operand of the `>>` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="logical-and-operator-amp"></a><a name="logical-and-operator-"></a> <span data-ttu-id="de04f-133">論理 AND 演算子 &amp;</span><span class="sxs-lookup"><span data-stu-id="de04f-133">Logical AND operator &amp;</span></span>

<span data-ttu-id="de04f-134">`&` 演算子では、そのオペランドのビットごとの論理 AND が計算されます。</span><span class="sxs-lookup"><span data-stu-id="de04f-134">The `&` operator computes the bitwise logical AND of its operands:</span></span>

[!code-csharp-interactive[bitwise AND](snippets/shared/BitwiseAndShiftOperators.cs#BitwiseAnd)]

<span data-ttu-id="de04f-135">`bool` オペランドの場合、`&` 演算子がそのオペランドの[論理 AND](boolean-logical-operators.md#logical-and-operator-) を計算します。</span><span class="sxs-lookup"><span data-stu-id="de04f-135">For `bool` operands, the `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="de04f-136">単項 `&` 演算子は[アドレス演算子](pointer-related-operators.md#address-of-operator-)です。</span><span class="sxs-lookup"><span data-stu-id="de04f-136">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="de04f-137">論理排他的 OR 演算子: ^</span><span class="sxs-lookup"><span data-stu-id="de04f-137">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="de04f-138">`^` 演算子では、そのオペランドのビットごとの論理排他的 OR (ビットごとの論理 XOR とも呼ばれます) が計算されます。</span><span class="sxs-lookup"><span data-stu-id="de04f-138">The `^` operator computes the bitwise logical exclusive OR, also known as the bitwise logical XOR, of its operands:</span></span>

[!code-csharp-interactive[bitwise XOR](snippets/shared/BitwiseAndShiftOperators.cs#BitwiseXor)]

<span data-ttu-id="de04f-139">`bool` オペランドの場合、`^` 演算子がそのオペランドの[論理排他的 OR](boolean-logical-operators.md#logical-exclusive-or-operator-) を計算します。</span><span class="sxs-lookup"><span data-stu-id="de04f-139">For `bool` operands, the `^` operator computes the [logical exclusive OR](boolean-logical-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="de04f-140">論理 OR 演算子 |</span><span class="sxs-lookup"><span data-stu-id="de04f-140">Logical OR operator |</span></span>

<span data-ttu-id="de04f-141">`|` 演算子では、そのオペランドのビットごとの論理 OR が計算されます。</span><span class="sxs-lookup"><span data-stu-id="de04f-141">The `|` operator computes the bitwise logical OR of its operands:</span></span>

[!code-csharp-interactive[bitwise OR](snippets/shared/BitwiseAndShiftOperators.cs#BitwiseOr)]

<span data-ttu-id="de04f-142">`bool` オペランドの場合、`|` 演算子がそのオペランドの[論理 OR](boolean-logical-operators.md#logical-or-operator-) を計算します。</span><span class="sxs-lookup"><span data-stu-id="de04f-142">For `bool` operands, the `|` operator computes the [logical OR](boolean-logical-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="de04f-143">複合代入。</span><span class="sxs-lookup"><span data-stu-id="de04f-143">Compound assignment</span></span>

<span data-ttu-id="de04f-144">2 項演算子 `op` の場合、フォームの複合代入式</span><span class="sxs-lookup"><span data-stu-id="de04f-144">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="de04f-145">上記の式は、次の式と同じです。</span><span class="sxs-lookup"><span data-stu-id="de04f-145">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="de04f-146">ただし、`x` が評価されるのは 1 回だけです。</span><span class="sxs-lookup"><span data-stu-id="de04f-146">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="de04f-147">次の例では、ビットごとの演算子およびシフト演算子を使った複合代入の使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="de04f-147">The following example demonstrates the usage of compound assignment with bitwise and shift operators:</span></span>

[!code-csharp-interactive[compound assignment](snippets/shared/BitwiseAndShiftOperators.cs#CompoundAssignment)]

<span data-ttu-id="de04f-148">[数値の上位変換](~/_csharplang/spec/expressions.md#numeric-promotions)のため、`op` 演算の結果は、`x` の型 `T` に暗黙的に変換できない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="de04f-148">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="de04f-149">そのような場合、`op` が定義済みの演算子であり、演算の結果が `x` の型 `T` に明示的に変換できる場合、`x op= y` の形式の複合代入式は、`x` が 1 回だけ評価される点を除き、`x = (T)(x op y)` と等価です。</span><span class="sxs-lookup"><span data-stu-id="de04f-149">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="de04f-150">次の例は、その動作を示します。</span><span class="sxs-lookup"><span data-stu-id="de04f-150">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](snippets/shared/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a><span data-ttu-id="de04f-151">演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="de04f-151">Operator precedence</span></span>

<span data-ttu-id="de04f-152">次のビットごとの演算子およびシフト演算子の一覧は、優先度が高い順に並べられています。</span><span class="sxs-lookup"><span data-stu-id="de04f-152">The following list orders bitwise and shift operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="de04f-153">ビットごとの補数演算子 `~`</span><span class="sxs-lookup"><span data-stu-id="de04f-153">Bitwise complement operator `~`</span></span>
- <span data-ttu-id="de04f-154">シフト演算子 `<<` および `>>`</span><span class="sxs-lookup"><span data-stu-id="de04f-154">Shift operators `<<` and `>>`</span></span>
- <span data-ttu-id="de04f-155">論理 AND 演算子 `&`</span><span class="sxs-lookup"><span data-stu-id="de04f-155">Logical AND operator `&`</span></span>
- <span data-ttu-id="de04f-156">論理排他的 OR 演算子 `^`</span><span class="sxs-lookup"><span data-stu-id="de04f-156">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="de04f-157">論理 OR 演算子 `|`</span><span class="sxs-lookup"><span data-stu-id="de04f-157">Logical OR operator `|`</span></span>

<span data-ttu-id="de04f-158">演算子の優先順位によって定められた評価の順序を変更するには、かっこ `()` を使用します。</span><span class="sxs-lookup"><span data-stu-id="de04f-158">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](snippets/shared/BitwiseAndShiftOperators.cs#Precedence)]

<span data-ttu-id="de04f-159">優先度順に並べられた C# 演算子の完全な一覧については、[C# 演算子](index.md)に関する記事の「[演算子の優先順位](index.md#operator-precedence)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="de04f-159">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="shift-count-of-the-shift-operators"></a><span data-ttu-id="de04f-160">シフト演算子のシフト数</span><span class="sxs-lookup"><span data-stu-id="de04f-160">Shift count of the shift operators</span></span>

<span data-ttu-id="de04f-161">シフト演算子 `<<` および `>>` の場合、右側のオペランドの型は、`int` であるか、または `int` への[事前に定義された暗黙的な数値変換](../builtin-types/numeric-conversions.md#implicit-numeric-conversions)を持つ型にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="de04f-161">For the shift operators `<<` and `>>`, the type of the right-hand operand must be `int` or a type that has a [predefined implicit numeric conversion](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) to `int`.</span></span>

<span data-ttu-id="de04f-162">`x << count` および `x >> count` の式では、実際のシフト数は次のように `x` の型によって異なります。</span><span class="sxs-lookup"><span data-stu-id="de04f-162">For the `x << count` and `x >> count` expressions, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="de04f-163">`x` の型が `int` または `uint` である場合、シフト数は、右側のオペランドの下位 *5* ビットで定義されます。</span><span class="sxs-lookup"><span data-stu-id="de04f-163">If the type of `x` is `int` or `uint`, the shift count is defined by the low-order *five* bits of the right-hand operand.</span></span> <span data-ttu-id="de04f-164">つまり、シフト数は `count & 0x1F` (または `count & 0b_1_1111`) から計算されます。</span><span class="sxs-lookup"><span data-stu-id="de04f-164">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="de04f-165">`x` の型が `long` または `ulong` である場合、シフト数は、右側のオペランドの下位 *6* ビットで定義されます。</span><span class="sxs-lookup"><span data-stu-id="de04f-165">If the type of `x` is `long` or `ulong`, the shift count is defined by the low-order *six* bits of the right-hand operand.</span></span> <span data-ttu-id="de04f-166">つまり、シフト数は `count & 0x3F` (または `count & 0b_11_1111`) から計算されます。</span><span class="sxs-lookup"><span data-stu-id="de04f-166">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="de04f-167">次の例は、その動作を示します。</span><span class="sxs-lookup"><span data-stu-id="de04f-167">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](snippets/shared/BitwiseAndShiftOperators.cs#ShiftCount)]

> [!NOTE]
> <span data-ttu-id="de04f-168">前の例で示したように、右側のオペランドの値が左側のオペランドのビット数よりも大きい場合でも、シフト演算の結果が 0 以外になることがあります。</span><span class="sxs-lookup"><span data-stu-id="de04f-168">As the preceding example shows, the result of a shift operation can be non-zero even if the value of the right-hand operand is greater than the number of bits in the left-hand operand.</span></span>

## <a name="enumeration-logical-operators"></a><span data-ttu-id="de04f-169">列挙論理演算子</span><span class="sxs-lookup"><span data-stu-id="de04f-169">Enumeration logical operators</span></span>

<span data-ttu-id="de04f-170">`~`、`&`、`|`、`^` の演算子は、任意の[列挙](../builtin-types/enum.md)型でもサポートされます。</span><span class="sxs-lookup"><span data-stu-id="de04f-170">The `~`, `&`, `|`, and `^` operators are also supported by any [enumeration](../builtin-types/enum.md) type.</span></span> <span data-ttu-id="de04f-171">オペランドが同じ列挙型の場合、基になっている整数型の対応する値に対して、論理演算が実行されます。</span><span class="sxs-lookup"><span data-stu-id="de04f-171">For operands of the same enumeration type, a logical operation is performed on the corresponding values of the underlying integral type.</span></span> <span data-ttu-id="de04f-172">たとえば、基になる型が `U` である列挙型 `T` の任意の `x` と `y` に対して、式 `x & y` では式 `(T)((U)x & (U)y)` と同じ結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="de04f-172">For example, for any `x` and `y` of an enumeration type `T` with an underlying type `U`, the `x & y` expression produces the same result as the `(T)((U)x & (U)y)` expression.</span></span>

<span data-ttu-id="de04f-173">通常、ビットごとの論理演算子は、[Flags](xref:System.FlagsAttribute) 属性で定義されている列挙型で使います。</span><span class="sxs-lookup"><span data-stu-id="de04f-173">You typically use bitwise logical operators with an enumeration type that is defined with the [Flags](xref:System.FlagsAttribute) attribute.</span></span> <span data-ttu-id="de04f-174">詳しくは、「[列挙型](../builtin-types/enum.md)」記事の「[ビット フラグとしての列挙型](../builtin-types/enum.md#enumeration-types-as-bit-flags)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="de04f-174">For more information, see the [Enumeration types as bit flags](../builtin-types/enum.md#enumeration-types-as-bit-flags) section of the [Enumeration types](../builtin-types/enum.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="de04f-175">演算子のオーバーロード可/不可</span><span class="sxs-lookup"><span data-stu-id="de04f-175">Operator overloadability</span></span>

<span data-ttu-id="de04f-176">ユーザー定義型では、`~`、`<<`、`>>`、`&`、`|`、`^` の各演算子を[オーバーロード](operator-overloading.md)できます。</span><span class="sxs-lookup"><span data-stu-id="de04f-176">A user-defined type can [overload](operator-overloading.md) the `~`, `<<`, `>>`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="de04f-177">2 項演算子をオーバーロードすると、対応する複合代入演算子も暗黙的にオーバーロードされます。</span><span class="sxs-lookup"><span data-stu-id="de04f-177">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="de04f-178">ユーザー定義型は、複合代入演算子を明示的にオーバーロードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="de04f-178">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="de04f-179">ユーザー定義型 `T` で `<<` または `>>` 演算子をオーバーロードする場合、左側のオペランドの型は `T` である必要があり、右側のオペランドの型は `int` である必要があります。</span><span class="sxs-lookup"><span data-stu-id="de04f-179">If a user-defined type `T` overloads the `<<` or `>>` operator, the type of the left-hand operand must be `T` and the type of the right-hand operand must be `int`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="de04f-180">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="de04f-180">C# language specification</span></span>

<span data-ttu-id="de04f-181">詳細については、「[C# 言語仕様](~/_csharplang/spec/introduction.md)」の次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="de04f-181">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="de04f-182">ビットごとの補数演算子</span><span class="sxs-lookup"><span data-stu-id="de04f-182">Bitwise complement operator</span></span>](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [<span data-ttu-id="de04f-183">シフト演算子</span><span class="sxs-lookup"><span data-stu-id="de04f-183">Shift operators</span></span>](~/_csharplang/spec/expressions.md#shift-operators)
- [<span data-ttu-id="de04f-184">論理演算子</span><span class="sxs-lookup"><span data-stu-id="de04f-184">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="de04f-185">複合代入</span><span class="sxs-lookup"><span data-stu-id="de04f-185">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="de04f-186">数値の上位変換</span><span class="sxs-lookup"><span data-stu-id="de04f-186">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="de04f-187">参照</span><span class="sxs-lookup"><span data-stu-id="de04f-187">See also</span></span>

- [<span data-ttu-id="de04f-188">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="de04f-188">C# reference</span></span>](../index.md)
- [<span data-ttu-id="de04f-189">C# の演算子と式</span><span class="sxs-lookup"><span data-stu-id="de04f-189">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="de04f-190">ブール論理演算子</span><span class="sxs-lookup"><span data-stu-id="de04f-190">Boolean logical operators</span></span>](boolean-logical-operators.md)
