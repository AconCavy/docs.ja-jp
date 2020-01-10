---
title: 演算子のオーバーロード
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
ms.openlocfilehash: 4cea3c17de40a873d977223f36b6dcef4f2c2d78
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709141"
---
# <a name="operator-overloads"></a><span data-ttu-id="12180-102">演算子のオーバーロード</span><span class="sxs-lookup"><span data-stu-id="12180-102">Operator Overloads</span></span>
<span data-ttu-id="12180-103">演算子のオーバーロードでは、フレームワーク型を組み込みの言語プリミティブとして表示できます。</span><span class="sxs-lookup"><span data-stu-id="12180-103">Operator overloads allow framework types to appear as if they were built-in language primitives.</span></span>  
  
 <span data-ttu-id="12180-104">一部の状況では許可および便利ですが、演算子のオーバーロードは慎重に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="12180-104">Although allowed and useful in some situations, operator overloads should be used cautiously.</span></span> <span data-ttu-id="12180-105">多くの場合、演算子のオーバーロードは不正使用されています。たとえば、framework デザイナーが、単純なメソッドである必要がある操作に対して演算子の使用を開始した場合などです。</span><span class="sxs-lookup"><span data-stu-id="12180-105">There are many cases in which operator overloading has been abused, such as when framework designers started to use operators for operations that should be simple methods.</span></span> <span data-ttu-id="12180-106">次のガイドラインは、演算子のオーバーロードを使用するタイミングと方法を決定するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="12180-106">The following guidelines should help you decide when and how to use operator overloading.</span></span>  
  
 <span data-ttu-id="12180-107">**X AVOID** を除く演算子のオーバー ロードを定義する必要があります (組み込み) のプリミティブ型と感じての種類でします。</span><span class="sxs-lookup"><span data-stu-id="12180-107">**X AVOID** defining operator overloads, except in types that should feel like primitive (built-in) types.</span></span>  
  
 <span data-ttu-id="12180-108">**✓ CONSIDER** 演算子のオーバー ロードを定義する型がプリミティブ型のように感じる必要があります。</span><span class="sxs-lookup"><span data-stu-id="12180-108">**✓ CONSIDER** defining operator overloads in a type that should feel like a primitive type.</span></span>  
  
 <span data-ttu-id="12180-109">たとえば、<xref:System.String?displayProperty=nameWithType> に `operator==` と `operator!=` が定義されているとします。</span><span class="sxs-lookup"><span data-stu-id="12180-109">For example, <xref:System.String?displayProperty=nameWithType> has `operator==` and `operator!=` defined.</span></span>  
  
 <span data-ttu-id="12180-110">**✓ DO** 番号を表す構造体で演算子オーバー ロードを定義する (など<xref:System.Decimal?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="12180-110">**✓ DO** define operator overloads in structs that represent numbers (such as <xref:System.Decimal?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="12180-111">**X DO NOT** 演算子のオーバー ロードを定義するときに分別して使用します。</span><span class="sxs-lookup"><span data-stu-id="12180-111">**X DO NOT** be cute when defining operator overloads.</span></span>  
  
 <span data-ttu-id="12180-112">演算子のオーバーロードは、操作の結果がすぐにわかる場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="12180-112">Operator overloading is useful in cases in which it is immediately obvious what the result of the operation will be.</span></span> <span data-ttu-id="12180-113">たとえば、ある <xref:System.DateTime> を別の `DateTime` から減算し、<xref:System.TimeSpan>を取得できるようにするのは理にかなっています。</span><span class="sxs-lookup"><span data-stu-id="12180-113">For example, it makes sense to be able to subtract one <xref:System.DateTime> from another `DateTime` and get a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="12180-114">ただし、2つのデータベースクエリを結合する場合や、shift 演算子を使用してストリームに書き込む場合は、論理和演算子を使用するのは適切ではありません。</span><span class="sxs-lookup"><span data-stu-id="12180-114">However, it is not appropriate to use the logical union operator to union two database queries, or to use the shift operator to write to a stream.</span></span>  
  
 <span data-ttu-id="12180-115">**X DO NOT** オーバー ロードを定義する型のオペランドの少なくとも 1 つがない限り、演算子がオーバー ロードを提供します。</span><span class="sxs-lookup"><span data-stu-id="12180-115">**X DO NOT** provide operator overloads unless at least one of the operands is of the type defining the overload.</span></span>  
  
 <span data-ttu-id="12180-116">**✓ DO** 対称的に演算子をオーバー ロードします。</span><span class="sxs-lookup"><span data-stu-id="12180-116">**✓ DO** overload operators in a symmetric fashion.</span></span>  
  
 <span data-ttu-id="12180-117">たとえば、`operator==`をオーバーロードする場合は、`operator!=`もオーバーロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="12180-117">For example, if you overload the `operator==`, you should also overload the `operator!=`.</span></span> <span data-ttu-id="12180-118">同様に、`operator<`をオーバーロードする場合は、`operator>`もオーバーロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="12180-118">Similarly, if you overload the `operator<`, you should also overload the `operator>`, and so on.</span></span>  
  
 <span data-ttu-id="12180-119">**✓ CONSIDER** 各オーバー ロードされた演算子に対応するフレンドリ名を持つメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="12180-119">**✓ CONSIDER** providing methods with friendly names that correspond to each overloaded operator.</span></span>  
  
 <span data-ttu-id="12180-120">多くの言語では、演算子のオーバーロードはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="12180-120">Many languages do not support operator overloading.</span></span> <span data-ttu-id="12180-121">このため、オーバーロード演算子には、同等の機能を提供するドメイン固有の適切な名前を持つ二次的なメソッドが含まれていることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="12180-121">For this reason, it is recommended that types that overload operators include a secondary method with an appropriate domain-specific name that provides equivalent functionality.</span></span>  
  
 <span data-ttu-id="12180-122">次の表に、演算子とそれに対応するわかりやすいメソッド名の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="12180-122">The following table contains a list of operators and the corresponding friendly method names.</span></span>  
  
|<span data-ttu-id="12180-123">C#演算子シンボル</span><span class="sxs-lookup"><span data-stu-id="12180-123">C# Operator Symbol</span></span>|<span data-ttu-id="12180-124">メタデータ名</span><span class="sxs-lookup"><span data-stu-id="12180-124">Metadata Name</span></span>|<span data-ttu-id="12180-125">[フレンドリ名]</span><span class="sxs-lookup"><span data-stu-id="12180-125">Friendly Name</span></span>|  
|-------------------------|-------------------|-------------------|  
|`N/A`|`op_Implicit`|`To<TypeName>/From<TypeName>`|  
|`N/A`|`op_Explicit`|`To<TypeName>/From<TypeName>`|  
|`+ (binary)`|`op_Addition`|`Add`|  
|`- (binary)`|`op_Subtraction`|`Subtract`|  
|`* (binary)`|`op_Multiply`|`Multiply`|  
|`/`|`op_Division`|`Divide`|  
|`%`|`op_Modulus`|`Mod or Remainder`|  
|`^`|`op_ExclusiveOr`|`Xor`|  
|`& (binary)`|`op_BitwiseAnd`|`BitwiseAnd`|  
|<code>&#124;</code>|`op_BitwiseOr`|`BitwiseOr`|  
|`&&`|`op_LogicalAnd`|`And`|  
|<code>&#124;&#124;</code>|`op_LogicalOr`|`Or`|  
|`=`|`op_Assign`|`Assign`|  
|`<<`|`op_LeftShift`|`LeftShift`|  
|`>>`|`op_RightShift`|`RightShift`|  
|`N/A`|`op_SignedRightShift`|`SignedRightShift`|  
|`N/A`|`op_UnsignedRightShift`|`UnsignedRightShift`|  
|`==`|`op_Equality`|`Equals`|  
|`!=`|`op_Inequality`|`Equals`|  
|`>`|`op_GreaterThan`|`CompareTo`|  
|`<`|`op_LessThan`|`CompareTo`|  
|`>=`|`op_GreaterThanOrEqual`|`CompareTo`|  
|`<=`|`op_LessThanOrEqual`|`CompareTo`|  
|`*=`|`op_MultiplicationAssignment`|`Multiply`|  
|`-=`|`op_SubtractionAssignment`|`Subtract`|  
|`^=`|`op_ExclusiveOrAssignment`|`Xor`|  
|`<<=`|`op_LeftShiftAssignment`|`LeftShift`|  
|`%=`|`op_ModulusAssignment`|`Mod`|  
|`+=`|`op_AdditionAssignment`|`Add`|  
|`&=`|`op_BitwiseAndAssignment`|`BitwiseAnd`|  
|<code>&#124;=</code>|`op_BitwiseOrAssignment`|`BitwiseOr`|  
|`,`|`op_Comma`|`Comma`|  
|`/=`|`op_DivisionAssignment`|`Divide`|  
|`--`|`op_Decrement`|`Decrement`|  
|`++`|`op_Increment`|`Increment`|  
|`- (unary)`|`op_UnaryNegation`|`Negate`|  
|`+ (unary)`|`op_UnaryPlus`|`Plus`|  
|`~`|`op_OnesComplement`|`OnesComplement`|  
  
### <a name="overloading-operator-"></a><span data-ttu-id="12180-126">オーバーロード演算子 = =</span><span class="sxs-lookup"><span data-stu-id="12180-126">Overloading Operator ==</span></span>  
 <span data-ttu-id="12180-127">`operator ==` のオーバーロードは非常に複雑です。</span><span class="sxs-lookup"><span data-stu-id="12180-127">Overloading `operator ==` is quite complicated.</span></span> <span data-ttu-id="12180-128">演算子のセマンティクスは、<xref:System.Object.Equals%2A?displayProperty=nameWithType>など、他のいくつかのメンバーと互換性がある必要があります。</span><span class="sxs-lookup"><span data-stu-id="12180-128">The semantics of the operator need to be compatible with several other members, such as <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="conversion-operators"></a><span data-ttu-id="12180-129">変換演算子</span><span class="sxs-lookup"><span data-stu-id="12180-129">Conversion Operators</span></span>  
 <span data-ttu-id="12180-130">変換演算子は、ある型から別の型への変換を可能にする単項演算子です。</span><span class="sxs-lookup"><span data-stu-id="12180-130">Conversion operators are unary operators that allow conversion from one type to another.</span></span> <span data-ttu-id="12180-131">演算子は、オペランドまたは戻り値の型のいずれかの静的メンバーとして定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="12180-131">The operators must be defined as static members on either the operand or the return type.</span></span> <span data-ttu-id="12180-132">変換演算子には、暗黙的と明示的の2種類があります。</span><span class="sxs-lookup"><span data-stu-id="12180-132">There are two types of conversion operators: implicit and explicit.</span></span>  
  
 <span data-ttu-id="12180-133">**X DO NOT** エンドユーザーでこのような変換が明確に予期されていない場合は、変換演算子を提供します。</span><span class="sxs-lookup"><span data-stu-id="12180-133">**X DO NOT** provide a conversion operator if such conversion is not clearly expected by the end users.</span></span>  
  
 <span data-ttu-id="12180-134">**X DO NOT** 型のドメインの外部の変換演算子を定義します。</span><span class="sxs-lookup"><span data-stu-id="12180-134">**X DO NOT** define conversion operators outside of a type’s domain.</span></span>  
  
 <span data-ttu-id="12180-135">たとえば、<xref:System.Int32>、<xref:System.Double>、および <xref:System.Decimal> はすべて数値型ですが、<xref:System.DateTime> はありません。</span><span class="sxs-lookup"><span data-stu-id="12180-135">For example, <xref:System.Int32>, <xref:System.Double>, and <xref:System.Decimal> are all numeric types, whereas <xref:System.DateTime> is not.</span></span> <span data-ttu-id="12180-136">したがって、`Double(long)` を `DateTime`に変換する変換演算子は存在しない必要があります。</span><span class="sxs-lookup"><span data-stu-id="12180-136">Therefore, there should be no conversion operator to convert a `Double(long)` to a `DateTime`.</span></span> <span data-ttu-id="12180-137">このような場合は、コンストラクターを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="12180-137">A constructor is preferred in such a case.</span></span>  
  
 <span data-ttu-id="12180-138">**X DO NOT** 変換が損失を伴う可能性がある場合は、暗黙的な変換演算子を提供します。</span><span class="sxs-lookup"><span data-stu-id="12180-138">**X DO NOT** provide an implicit conversion operator if the conversion is potentially lossy.</span></span>  
  
 <span data-ttu-id="12180-139">たとえば、`Double` の範囲が `Int32`よりも広いため、`Double` から `Int32` への暗黙的な変換を行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="12180-139">For example, there should not be an implicit conversion from `Double` to `Int32` because `Double` has a wider range than `Int32`.</span></span> <span data-ttu-id="12180-140">変換が損失する可能性がある場合でも、明示的な変換演算子を指定できます。</span><span class="sxs-lookup"><span data-stu-id="12180-140">An explicit conversion operator can be provided even if the conversion is potentially lossy.</span></span>  
  
 <span data-ttu-id="12180-141">**X DO NOT** 暗黙的なキャストから例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="12180-141">**X DO NOT** throw exceptions from implicit casts.</span></span>  
  
 <span data-ttu-id="12180-142">変換が行われていることを認識していない可能性があるため、エンドユーザーは何が起こっているかを理解することは非常に困難です。</span><span class="sxs-lookup"><span data-stu-id="12180-142">It is very difficult for end users to understand what is happening, because they might not be aware that a conversion is taking place.</span></span>  
  
 <span data-ttu-id="12180-143">**✓ DO** スロー<xref:System.InvalidCastException?displayProperty=nameWithType>でキャスト演算子への呼び出しが損失を伴う変換と演算子のコントラクトでは、非可逆の変換は許可されません。</span><span class="sxs-lookup"><span data-stu-id="12180-143">**✓ DO** throw <xref:System.InvalidCastException?displayProperty=nameWithType> if a call to a cast operator results in a lossy conversion and the contract of the operator does not allow lossy conversions.</span></span>  
  
 <span data-ttu-id="12180-144">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="12180-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="12180-145">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="12180-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12180-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="12180-146">See also</span></span>

- [<span data-ttu-id="12180-147">メンバーのデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="12180-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="12180-148">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="12180-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
