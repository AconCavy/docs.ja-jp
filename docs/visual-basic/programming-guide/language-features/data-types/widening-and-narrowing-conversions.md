---
title: Widening and Narrowing Conversions
ms.date: 07/20/2015
helpviewer_keywords:
- widening conversions [Visual Basic]
- narrowing conversions [Visual Basic]
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- conversions [Visual Basic], exceptions during conversion
- type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], data type
- conversions [Visual Basic], narrowing
- type conversion [Visual Basic], narrowing
- data type conversion [Visual Basic], widening
- data type conversion [Visual Basic], narrowing
- changing data types [Visual Basic]
- type conversion [Visual Basic], widening
- data type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], widening
ms.assetid: 058c3152-6c28-4268-af44-2209e774f0bd
ms.openlocfilehash: c0e10f5593ce5c81002233516444e415571541f3
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058535"
---
# <a name="widening-and-narrowing-conversions-visual-basic"></a><span data-ttu-id="bb9bd-102">拡大変換と縮小変換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb9bd-102">Widening and Narrowing Conversions (Visual Basic)</span></span>

<span data-ttu-id="bb9bd-103">型変換に関する重要な考慮事項は、変換結果が変換先のデータ型の範囲内に収まるかどうかです。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-103">An important consideration with a type conversion is whether the result of the conversion is within the range of the destination data type.</span></span>  
  
 <span data-ttu-id="bb9bd-104">"*拡大変換*" では、値が元のデータのあらゆる値を収容できるデータ型に変更されます。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-104">A *widening conversion* changes a value to a data type that can allow for any possible value of the original data.</span></span>  <span data-ttu-id="bb9bd-105">拡大変換では変換元の値が保持されますが、その表現が変化する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-105">Widening conversions preserve the source value but can change its representation.</span></span> <span data-ttu-id="bb9bd-106">そのようになるのは、整数型から `Decimal`、または `Char` から `String` に変換した場合です。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-106">This occurs if you convert from an integral type to `Decimal`, or from `Char` to `String`.</span></span>  
  
 <span data-ttu-id="bb9bd-107">*縮小変換* により、有効値の一部を保持できない可能性のあるデータ型に値が変更されます。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-107">A *narrowing conversion* changes a value to a data type that might not be able to hold some of the possible values.</span></span> <span data-ttu-id="bb9bd-108">たとえば、小数値を整数型に変換すると丸められます。また、`Boolean` に変換される数値型は `True` または `False` に縮小されます。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-108">For example, a fractional value is rounded when it is converted to an integral type, and a numeric type being converted to `Boolean` is reduced to either `True` or `False`.</span></span>  
  
## <a name="widening-conversions"></a><span data-ttu-id="bb9bd-109">拡大変換</span><span class="sxs-lookup"><span data-stu-id="bb9bd-109">Widening Conversions</span></span>  

 <span data-ttu-id="bb9bd-110">次の表は、標準の拡大変換を示しています。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-110">The following table shows the standard widening conversions.</span></span>  
  
|<span data-ttu-id="bb9bd-111">データの種類</span><span class="sxs-lookup"><span data-stu-id="bb9bd-111">Data type</span></span>|<span data-ttu-id="bb9bd-112">拡大変換先のデータ型<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="bb9bd-112">Widens to data types <sup>1</sup></span></span>|  
|---|---|  
|[<span data-ttu-id="bb9bd-113">SByte</span><span class="sxs-lookup"><span data-stu-id="bb9bd-113">SByte</span></span>](../../../language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="bb9bd-114">`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="bb9bd-114">`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="bb9bd-115">Byte</span><span class="sxs-lookup"><span data-stu-id="bb9bd-115">Byte</span></span>](../../../language-reference/data-types/byte-data-type.md)|<span data-ttu-id="bb9bd-116">`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long`、`ULong`、`Decimal`、`Single`、`Double`</span><span class="sxs-lookup"><span data-stu-id="bb9bd-116">`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="bb9bd-117">Short</span><span class="sxs-lookup"><span data-stu-id="bb9bd-117">Short</span></span>](../../../language-reference/data-types/short-data-type.md)|<span data-ttu-id="bb9bd-118">`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="bb9bd-118">`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="bb9bd-119">UShort</span><span class="sxs-lookup"><span data-stu-id="bb9bd-119">UShort</span></span>](../../../language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="bb9bd-120">`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="bb9bd-120">`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="bb9bd-121">Integer</span><span class="sxs-lookup"><span data-stu-id="bb9bd-121">Integer</span></span>](../../../language-reference/data-types/integer-data-type.md)|<span data-ttu-id="bb9bd-122">`Integer`、`Long`、`Decimal`、`Single`、`Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="bb9bd-122">`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="bb9bd-123">UInteger</span><span class="sxs-lookup"><span data-stu-id="bb9bd-123">UInteger</span></span>](../../../language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="bb9bd-124">`UInteger`、`Long`、`ULong`、`Decimal`、`Single`、`Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="bb9bd-124">`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="bb9bd-125">Long</span><span class="sxs-lookup"><span data-stu-id="bb9bd-125">Long</span></span>](../../../language-reference/data-types/long-data-type.md)|<span data-ttu-id="bb9bd-126">`Long`、`Decimal`、`Single`、`Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="bb9bd-126">`Long`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="bb9bd-127">ULong</span><span class="sxs-lookup"><span data-stu-id="bb9bd-127">ULong</span></span>](../../../language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="bb9bd-128">`ULong`、`Decimal`、`Single`、`Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="bb9bd-128">`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="bb9bd-129">Decimal</span><span class="sxs-lookup"><span data-stu-id="bb9bd-129">Decimal</span></span>](../../../language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="bb9bd-130">`Decimal`、`Single`、`Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="bb9bd-130">`Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="bb9bd-131">Single</span><span class="sxs-lookup"><span data-stu-id="bb9bd-131">Single</span></span>](../../../language-reference/data-types/single-data-type.md)|<span data-ttu-id="bb9bd-132">`Single`、`Double`</span><span class="sxs-lookup"><span data-stu-id="bb9bd-132">`Single`, `Double`</span></span>|  
|[<span data-ttu-id="bb9bd-133">Double</span><span class="sxs-lookup"><span data-stu-id="bb9bd-133">Double</span></span>](../../../language-reference/data-types/double-data-type.md)|`Double`|  
|<span data-ttu-id="bb9bd-134">任意の列挙型 ([Enum](../../../language-reference/statements/enum-statement.md))</span><span class="sxs-lookup"><span data-stu-id="bb9bd-134">Any enumerated type ([Enum](../../../language-reference/statements/enum-statement.md))</span></span>|<span data-ttu-id="bb9bd-135">基になる整数型、および基になる型が拡大変換される任意の型。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-135">Its underlying integral type and any type to which the underlying type widens.</span></span>|  
|[<span data-ttu-id="bb9bd-136">Char</span><span class="sxs-lookup"><span data-stu-id="bb9bd-136">Char</span></span>](../../../language-reference/data-types/char-data-type.md)|<span data-ttu-id="bb9bd-137">`Char`、`String`</span><span class="sxs-lookup"><span data-stu-id="bb9bd-137">`Char`, `String`</span></span>|  
|<span data-ttu-id="bb9bd-138">`Char` 配列</span><span class="sxs-lookup"><span data-stu-id="bb9bd-138">`Char` array</span></span>|<span data-ttu-id="bb9bd-139">`Char` 配列、`String`</span><span class="sxs-lookup"><span data-stu-id="bb9bd-139">`Char` array, `String`</span></span>|  
|<span data-ttu-id="bb9bd-140">任意の型</span><span class="sxs-lookup"><span data-stu-id="bb9bd-140">Any type</span></span>|[<span data-ttu-id="bb9bd-141">オブジェクト</span><span class="sxs-lookup"><span data-stu-id="bb9bd-141">Object</span></span>](../../../language-reference/data-types/object-data-type.md)|  
|<span data-ttu-id="bb9bd-142">任意の派生型</span><span class="sxs-lookup"><span data-stu-id="bb9bd-142">Any derived type</span></span>|<span data-ttu-id="bb9bd-143">派生元の任意の基本型<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="bb9bd-143">Any base type from which it is derived <sup>3</sup>.</span></span>|  
|<span data-ttu-id="bb9bd-144">任意の型</span><span class="sxs-lookup"><span data-stu-id="bb9bd-144">Any type</span></span>|<span data-ttu-id="bb9bd-145">実装する任意のインターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb9bd-145">Any interface it implements.</span></span>|  
|[<span data-ttu-id="bb9bd-146">Nothing</span><span class="sxs-lookup"><span data-stu-id="bb9bd-146">Nothing</span></span>](../../../language-reference/nothing.md)|<span data-ttu-id="bb9bd-147">任意のデータ型またはオブジェクト型</span><span class="sxs-lookup"><span data-stu-id="bb9bd-147">Any data type or object type.</span></span>|  
  
 <span data-ttu-id="bb9bd-148"><sup>1</sup> 定義により、すべてのデータ型がそれ自体に拡大変換されます。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-148"><sup>1</sup> By definition, every data type widens to itself.</span></span>  
  
 <span data-ttu-id="bb9bd-149"><sup>2</sup> `Integer`、`UInteger`、`Long`、`ULong`、または `Decimal` から `Single` または `Double` への変換では、精度が失われることがありますが、大きさは失われません。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-149"><sup>2</sup> Conversions from `Integer`, `UInteger`, `Long`, `ULong`, or `Decimal` to `Single` or `Double` might result in loss of precision, but never in loss of magnitude.</span></span> <span data-ttu-id="bb9bd-150">この意味で、情報の損失は発生しません。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-150">In this sense they do not incur information loss.</span></span>  
  
 <span data-ttu-id="bb9bd-151"><sup>3</sup> 派生型からその基本型の 1 つに変換することが拡大と見なされるのは意外かもしれません。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-151"><sup>3</sup> It might seem surprising that a conversion from a derived type to one of its base types is widening.</span></span> <span data-ttu-id="bb9bd-152">理由は、派生型には基本型のすべてのメンバーが含まれており、基本型のインスタンスとしての資格を満たすためです。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-152">The justification is that the derived type contains all the members of the base type, so it qualifies as an instance of the base type.</span></span> <span data-ttu-id="bb9bd-153">逆方向の場合、基本型には、派生型によって定義される新しいメンバーは含まれません。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-153">In the opposite direction, the base type does not contain any new members defined by the derived type.</span></span>  
  
 <span data-ttu-id="bb9bd-154">拡大変換は実行時に必ず成功し、データの損失が発生することはありません。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-154">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="bb9bd-155">[Option Strict ステートメント](../../../language-reference/statements/option-strict-statement.md)で、型チェック スイッチが `On` と `Off` のどちらに設定されていても、これらは常に暗黙で実行できます。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-155">You can always perform them implicitly, whether the [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md) sets the type checking switch to `On` or to `Off`.</span></span>  
  
## <a name="narrowing-conversions"></a><span data-ttu-id="bb9bd-156">縮小変換</span><span class="sxs-lookup"><span data-stu-id="bb9bd-156">Narrowing Conversions</span></span>  

 <span data-ttu-id="bb9bd-157">標準的な縮小変換には、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-157">The standard narrowing conversions include the following:</span></span>  
  
- <span data-ttu-id="bb9bd-158">前の表に示した拡大変換の逆方向 (すべての型のそれ自体への拡大変換を除く)</span><span class="sxs-lookup"><span data-stu-id="bb9bd-158">The reverse directions of the widening conversions in the preceding table (except that every type widens to itself)</span></span>  
  
- <span data-ttu-id="bb9bd-159">[Boolean](../../../language-reference/data-types/boolean-data-type.md) と任意の数値型の間での双方向の変換</span><span class="sxs-lookup"><span data-stu-id="bb9bd-159">Conversions in either direction between [Boolean](../../../language-reference/data-types/boolean-data-type.md) and any numeric type</span></span>  
  
- <span data-ttu-id="bb9bd-160">任意の数値型から任意の列挙型 (`Enum`) への変換</span><span class="sxs-lookup"><span data-stu-id="bb9bd-160">Conversions from any numeric type to any enumerated type (`Enum`)</span></span>  
  
- <span data-ttu-id="bb9bd-161">[String](../../../language-reference/data-types/string-data-type.md) と、任意の数値型、`Boolean`、または [Date](../../../language-reference/data-types/date-data-type.md) の間での双方向の変換</span><span class="sxs-lookup"><span data-stu-id="bb9bd-161">Conversions in either direction between [String](../../../language-reference/data-types/string-data-type.md) and any numeric type, `Boolean`, or [Date](../../../language-reference/data-types/date-data-type.md)</span></span>  
  
- <span data-ttu-id="bb9bd-162">データ型またはオブジェクト型から、派生元の型への変換</span><span class="sxs-lookup"><span data-stu-id="bb9bd-162">Conversions from a data type or object type to a type derived from it</span></span>  
  
 <span data-ttu-id="bb9bd-163">縮小変換は実行時に必ず成功するとは限らず、失敗したり、データの損失が発生したりする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-163">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="bb9bd-164">エラーが発生するのは、変換先のデータ型が、変換された値を受け取ることができない場合です。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-164">An error occurs if the destination data type cannot receive the value being converted.</span></span> <span data-ttu-id="bb9bd-165">たとえば、数値変換でオーバーフローが発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-165">For example, a numeric conversion can result in an overflow.</span></span> <span data-ttu-id="bb9bd-166">[Option Strict ステートメント](../../../language-reference/statements/option-strict-statement.md)で型チェック スイッチを `Off` に設定しない限り、縮小変換を暗黙に実行することはコンパイラによって許可されません。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-166">The compiler does not allow you to perform narrowing conversions implicitly unless the [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md) sets the type checking switch to `Off`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bb9bd-167">`For Each…Next` コレクション内の要素からループ制御変数への変換では、縮小変換エラーが抑制されます。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-167">The narrowing-conversion error is suppressed for conversions from the elements in a `For Each…Next` collection to the loop control variable.</span></span> <span data-ttu-id="bb9bd-168">詳細と例については、「[For Each...Next ステートメント](../../../language-reference/statements/for-each-next-statement.md)」の縮小変換に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-168">For more information and examples, see the "Narrowing Conversions" section in [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md).</span></span>  
  
### <a name="when-to-use-narrowing-conversions"></a><span data-ttu-id="bb9bd-169">縮小変換を使用する場合</span><span class="sxs-lookup"><span data-stu-id="bb9bd-169">When to Use Narrowing Conversions</span></span>  

 <span data-ttu-id="bb9bd-170">縮小変換を使用するのは、変換元の値を変換先データ型に変換することができ、エラーやデータの損失が発生しないとわかっている場合です。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-170">You use a narrowing conversion when you know the source value can be converted to the destination data type without error or data loss.</span></span> <span data-ttu-id="bb9bd-171">たとえば、"True" または "False" のいずれかが含まれていることがわかっている `String` がある場合、`CBool` キーワードを使用して `Boolean` に変換できます。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-171">For example, if you have a `String` that you know contains either "True" or "False," you can use the `CBool` keyword to convert it to `Boolean`.</span></span>  
  
## <a name="exceptions-during-conversion"></a><span data-ttu-id="bb9bd-172">変換時の例外</span><span class="sxs-lookup"><span data-stu-id="bb9bd-172">Exceptions During Conversion</span></span>  

 <span data-ttu-id="bb9bd-173">拡大変換は常に成功するため、例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-173">Because widening conversions always succeed, they do not throw exceptions.</span></span> <span data-ttu-id="bb9bd-174">縮小変換では、エラーが発生した場合によくスローされるのは次の例外です。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-174">Narrowing conversions, when they fail, most commonly throw the following exceptions:</span></span>  
  
- <span data-ttu-id="bb9bd-175"><xref:System.InvalidCastException> — 2 つの型の間に変換が定義されていない場合</span><span class="sxs-lookup"><span data-stu-id="bb9bd-175"><xref:System.InvalidCastException> — if no conversion is defined between the two types</span></span>  
  
- <span data-ttu-id="bb9bd-176"><xref:System.OverflowException> — (整数型のみ) 変換後の値が、変換先の型に対して大きすぎる場合</span><span class="sxs-lookup"><span data-stu-id="bb9bd-176"><xref:System.OverflowException> — (integral types only) if the converted value is too large for the target type</span></span>  
  
 <span data-ttu-id="bb9bd-177">クラスまたは構造体によって、そのクラスまたは構造体との間の変換演算子として使用される [CType 関数](../../../language-reference/functions/ctype-function.md)が定義されている場合、その `CType` によって該当する例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-177">If a class or structure defines a [CType Function](../../../language-reference/functions/ctype-function.md) to serve as a conversion operator to or from that class or structure, that `CType` can throw any exception it deems appropriate.</span></span> <span data-ttu-id="bb9bd-178">また、この `CType` が Visual Basic 関数または .NET Framework メソッドを呼び出して、さらにさまざまな例外がスローされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-178">In addition, that `CType` might call Visual Basic functions or .NET Framework methods, which in turn could throw a variety of exceptions.</span></span>  
  
## <a name="changes-during-reference-type-conversions"></a><span data-ttu-id="bb9bd-179">参照型変換時の変更</span><span class="sxs-lookup"><span data-stu-id="bb9bd-179">Changes During Reference Type Conversions</span></span>  

 <span data-ttu-id="bb9bd-180">"*参照型*" からの変換では、ポインターが値にコピーされるだけです。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-180">A conversion from a *reference type* copies only the pointer to the value.</span></span> <span data-ttu-id="bb9bd-181">値そのものがコピーされたり変更されたりすることはありません。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-181">The value itself is neither copied nor changed in any way.</span></span> <span data-ttu-id="bb9bd-182">変更できるのは、ポインターを保持している変数のデータ型だけです。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-182">The only thing that can change is the data type of the variable holding the pointer.</span></span> <span data-ttu-id="bb9bd-183">次の例では、データ型は派生クラスから基本クラスに変換されますが、両方の変数が参照するオブジェクトは変更されません。</span><span class="sxs-lookup"><span data-stu-id="bb9bd-183">In the following example, the data type is converted from the derived class to its base class, but the object that both variables now point to is unchanged.</span></span>  
  
```vb  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a><span data-ttu-id="bb9bd-184">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb9bd-184">See also</span></span>

- [<span data-ttu-id="bb9bd-185">データの種類</span><span class="sxs-lookup"><span data-stu-id="bb9bd-185">Data Types</span></span>](index.md)
- [<span data-ttu-id="bb9bd-186">Visual Basic における型変換</span><span class="sxs-lookup"><span data-stu-id="bb9bd-186">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="bb9bd-187">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="bb9bd-187">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="bb9bd-188">文字列とその他の型との変換</span><span class="sxs-lookup"><span data-stu-id="bb9bd-188">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="bb9bd-189">方法: Visual Basic でオブジェクトを別の型に変換する</span><span class="sxs-lookup"><span data-stu-id="bb9bd-189">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="bb9bd-190">配列変換</span><span class="sxs-lookup"><span data-stu-id="bb9bd-190">Array Conversions</span></span>](array-conversions.md)
- [<span data-ttu-id="bb9bd-191">データの種類</span><span class="sxs-lookup"><span data-stu-id="bb9bd-191">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="bb9bd-192">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="bb9bd-192">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
