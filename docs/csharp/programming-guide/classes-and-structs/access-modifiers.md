---
title: アクセス修飾子 - C# プログラミング ガイド
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: 0d8e536902317c1e5b00dadde069dd6242189088
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705666"
---
# <a name="access-modifiers-c-programming-guide"></a><span data-ttu-id="06e8c-102">アクセス修飾子 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="06e8c-102">Access Modifiers (C# Programming Guide)</span></span>
<span data-ttu-id="06e8c-103">すべての型とそのメンバーには、アクセシビリティ レベルがあります。同じアセンブリ (または他のアセンブリ) にある他のコードからそれらの型やそのメンバーを利用できるかどうかは、アクセシビリティ レベルによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="06e8c-103">All types and type members have an accessibility level, which controls whether they can be used from other code in your assembly or other assemblies.</span></span> <span data-ttu-id="06e8c-104">型またはメンバーにはその宣言時に、以下のアクセス修飾子を使ってアクセシビリティを指定できます。</span><span class="sxs-lookup"><span data-stu-id="06e8c-104">You can use the following access modifiers to specify the accessibility of a type or member when you declare it:</span></span>  
  
 [<span data-ttu-id="06e8c-105">public</span><span class="sxs-lookup"><span data-stu-id="06e8c-105">public</span></span>](../../language-reference/keywords/public.md)  
 <span data-ttu-id="06e8c-106">この型またはメンバーには、同じアセンブリ内の他のコードや、そのアセンブリを参照する別のアセンブリ内の任意のコードからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="06e8c-106">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span> 
  
 [<span data-ttu-id="06e8c-107">private</span><span class="sxs-lookup"><span data-stu-id="06e8c-107">private</span></span>](../../language-reference/keywords/private.md)  
 <span data-ttu-id="06e8c-108">この型またはメンバーには、同じクラス内または同じ構造体内のコードからのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="06e8c-108">The type or member can be accessed only by code in the same class or struct.</span></span>  
  
 [<span data-ttu-id="06e8c-109">protected</span><span class="sxs-lookup"><span data-stu-id="06e8c-109">protected</span></span>](../../language-reference/keywords/protected.md)  
 <span data-ttu-id="06e8c-110">この型またはメンバーには、同じクラス内のコードか、そのクラスから派生したクラス内のコードからのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="06e8c-110">The type or member can be accessed only by code in the same class, or in a class that is derived from that class.</span></span>  
 [<span data-ttu-id="06e8c-111">internal</span><span class="sxs-lookup"><span data-stu-id="06e8c-111">internal</span></span>](../../language-reference/keywords/internal.md)  
 <span data-ttu-id="06e8c-112">この型またはメンバーには、同じアセンブリ内の任意のコードからアクセスできますが、別のアセンブリからはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="06e8c-112">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>  
  
 <span data-ttu-id="06e8c-113">[protected internal](../../language-reference/keywords/protected-internal.md) この型またはメンバーには、それが宣言されているアセンブリ内の任意のコードからアクセスできるほか、別のアセンブリの派生クラス内からアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="06e8c-113">[protected internal](../../language-reference/keywords/protected-internal.md) The type or member can be accessed by any code in the assembly in which it is declared, or from within a derived class in another assembly.</span></span> 

 <span data-ttu-id="06e8c-114">[private protected](../../language-reference/keywords/private-protected.md) この型またはメンバーには、同じクラスのコードか、そのクラスから派生した型のコードによって、その宣言アセンブリ内でのみ、アクセスできます。</span><span class="sxs-lookup"><span data-stu-id="06e8c-114">[private protected](../../language-reference/keywords/private-protected.md) The type or member can be accessed only within its declaring assembly, by code in the same class or in a type that is derived from that class.</span></span>
  
 <span data-ttu-id="06e8c-115">次の例は、型とメンバーにアクセス修飾子を指定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="06e8c-115">The following examples demonstrate how to specify access modifiers on a type and member:</span></span>  
  
 [!code-csharp[csProgGuideObjects#72](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#72)]  
  
 <span data-ttu-id="06e8c-116">コンテキストに関係なくすべての型またはすべてのメンバーにどのようなアクセス修飾子でも使用できるというわけではありません。型のメンバーのアクセシビリティが、それを含んでいる型のアクセシビリティによって制約を受ける場合もあります。</span><span class="sxs-lookup"><span data-stu-id="06e8c-116">Not all access modifiers can be used by all types or members in all contexts, and in some cases the accessibility of a type member is constrained by the accessibility of its containing type.</span></span> <span data-ttu-id="06e8c-117">以降のセクションでは、アクセシビリティについてさらに詳しく取り上げます。</span><span class="sxs-lookup"><span data-stu-id="06e8c-117">The following sections provide more details about accessibility.</span></span>  
  
## <a name="class-and-struct-accessibility"></a><span data-ttu-id="06e8c-118">クラスと構造体のアクセシビリティ</span><span class="sxs-lookup"><span data-stu-id="06e8c-118">Class and Struct Accessibility</span></span>  
 <span data-ttu-id="06e8c-119">名前空間に直接宣言されている (つまり、他のクラスや構造体の入れ子にされていない) クラスと構造体には、public または internal を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="06e8c-119">Classes and structs that are declared directly within a namespace (in other words, that are not nested within other classes or structs) can be either public or internal.</span></span> <span data-ttu-id="06e8c-120">アクセス修飾子が指定されなかった場合は、既定で internal が適用されます。</span><span class="sxs-lookup"><span data-stu-id="06e8c-120">Internal is the default if no access modifier is specified.</span></span>  
  
 <span data-ttu-id="06e8c-121">構造体のメンバー (入れ子にされているクラスや構造体も含む) は public、internal、private のいずれかとして宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="06e8c-121">Struct members, including nested classes and structs, can be declared as public, internal, or private.</span></span> <span data-ttu-id="06e8c-122">クラスのメンバー (入れ子にされているクラスや構造体も含む) は public、protected internal、protected、internal、private protected、private のいずれかとして宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="06e8c-122">Class members, including nested classes and structs, can be public, protected internal, protected, internal, private protected or private.</span></span> <span data-ttu-id="06e8c-123">クラスのメンバーと構造体のメンバー (入れ子にされているクラスや構造体も含む) には、既定で private のアクセス レベルが指定されます。</span><span class="sxs-lookup"><span data-stu-id="06e8c-123">The access level for class members and struct members, including nested classes and structs, is private by default.</span></span> <span data-ttu-id="06e8c-124">入れ子にされた型のうち、private が指定されているものには、それを含んでいる型の外部からはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="06e8c-124">Private nested types are not accessible from outside the containing type.</span></span>  
  
 <span data-ttu-id="06e8c-125">派生クラスに、その基本型を超えるアクセシビリティを割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="06e8c-125">Derived classes cannot have greater accessibility than their base types.</span></span> <span data-ttu-id="06e8c-126">つまり、internal クラス `A` から派生したクラス `B` を public にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="06e8c-126">In other words, you cannot have a public class `B` that derives from an internal class `A`.</span></span> <span data-ttu-id="06e8c-127">仮にそれが許容されるならば、`A` が public になると考えられます。`A` のすべての protected メンバーと internal メンバーに派生クラスからアクセスできることになるからです。</span><span class="sxs-lookup"><span data-stu-id="06e8c-127">If this were allowed, it would have the effect of making `A` public, because all protected or internal members of `A` are accessible from the derived class.</span></span>  
  
 <span data-ttu-id="06e8c-128">InternalsVisibleToAttribute を使うと、internal 型へのアクセスを他の特定のアセンブリに許可することができます。</span><span class="sxs-lookup"><span data-stu-id="06e8c-128">You can enable specific other assemblies to access your internal types by using the InternalsVisibleToAttribute.</span></span> <span data-ttu-id="06e8c-129">詳細については、[Friend アセンブリ](../../../standard/assembly/friend.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="06e8c-129">For more information, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
## <a name="class-and-struct-member-accessibility"></a><span data-ttu-id="06e8c-130">クラスと構造体のメンバーのアクセシビリティ</span><span class="sxs-lookup"><span data-stu-id="06e8c-130">Class and Struct Member Accessibility</span></span>  
 <span data-ttu-id="06e8c-131">クラスのメンバー (入れ子にされているクラスや構造体も含む) は、6 種類あるアクセス修飾子をどれでも使って宣言できます。</span><span class="sxs-lookup"><span data-stu-id="06e8c-131">Class members (including nested classes and structs) can be declared with any of the six types of access.</span></span> <span data-ttu-id="06e8c-132">構造体のメンバーを protected として宣言することはできません。構造体は継承をサポートしていないためです。</span><span class="sxs-lookup"><span data-stu-id="06e8c-132">Struct members cannot be declared as protected because structs do not support inheritance.</span></span>  
  
 <span data-ttu-id="06e8c-133">通常、メンバーのアクセシビリティが、それを含んでいる型のアクセシビリティを超えることはありません。</span><span class="sxs-lookup"><span data-stu-id="06e8c-133">Normally, the accessibility of a member is not greater than the accessibility of the type that contains it.</span></span> <span data-ttu-id="06e8c-134">ただし、internal クラスの public メンバーには、そのアセンブリの外部からアクセスできる場合もあります。そのメンバーがインターフェイスのメソッドを実装している場合や public な基本クラスに定義されている仮想メソッドをオーバーライドしている場合がそれに該当します。</span><span class="sxs-lookup"><span data-stu-id="06e8c-134">However, a public member of an internal class might be accessible from outside the assembly if the member implements interface methods or overrides virtual methods that are defined in a public base class.</span></span>  
  
 <span data-ttu-id="06e8c-135">フィールド、プロパティ、イベントのいずれかに該当するメンバーの型には、メンバー自体と同じかそれ以上のアクセシビリティが必要です。</span><span class="sxs-lookup"><span data-stu-id="06e8c-135">The type of any member that is a field, property, or event must be at least as accessible as the member itself.</span></span> <span data-ttu-id="06e8c-136">同様に、メソッド、インデクサー、デリゲートのいずれかに該当するメンバーの戻り値の型とパラメーターの型には、メンバー自体と同じかそれ以上のアクセシビリティが必要です。</span><span class="sxs-lookup"><span data-stu-id="06e8c-136">Similarly, the return type and the parameter types of any member that is a method, indexer, or delegate must be at least as accessible as the member itself.</span></span> <span data-ttu-id="06e8c-137">たとえば、クラス `C` を返すメソッド `M` を public にするためには、`C` も public である必要があります。</span><span class="sxs-lookup"><span data-stu-id="06e8c-137">For example, you cannot have a public method `M` that returns a class `C` unless `C` is also public.</span></span> <span data-ttu-id="06e8c-138">同様に、`A` が private として宣言されている場合、`A` 型のプロパティを protected にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="06e8c-138">Likewise, you cannot have a protected property of type `A` if `A` is declared as private.</span></span>  
  
 <span data-ttu-id="06e8c-139">ユーザー定義の演算子は、必ず public かつ静的として宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="06e8c-139">User-defined operators must always be declared as public and static.</span></span> <span data-ttu-id="06e8c-140">詳細については、「[演算子のオーバーロード](../../language-reference/operators/operator-overloading.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06e8c-140">For more information, see [Operator overloading](../../language-reference/operators/operator-overloading.md).</span></span>  
  
 <span data-ttu-id="06e8c-141">アクセシビリティ修飾子をファイナライザーに割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="06e8c-141">Finalizers cannot have accessibility modifiers.</span></span>  
  
 <span data-ttu-id="06e8c-142">クラスまたは構造体のメンバーにアクセス レベルを設定するには、該当するキーワードをメンバーの宣言に追加します。その例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="06e8c-142">To set the access level for a class or struct member, add the appropriate keyword to the member declaration, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideObjects#73](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#73)]  
  
> [!NOTE]
> <span data-ttu-id="06e8c-143">protected internal のアクセシビリティ レベルは、"protected AND internal" ではなく "protected OR internal" という意味になります。</span><span class="sxs-lookup"><span data-stu-id="06e8c-143">The protected internal accessibility level means protected OR internal, not protected AND internal.</span></span> <span data-ttu-id="06e8c-144">つまり、protected internal のメンバーには、同じアセンブリ内の任意のクラス (派生クラスも含む) からアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="06e8c-144">In other words, a protected internal member can be accessed from any class in the same assembly, including derived classes.</span></span> <span data-ttu-id="06e8c-145">同じアセンブリ内の派生クラスのみにアクセシビリティを限定するには、クラス自体は internal として宣言し、そのメンバーを protected として宣言します。</span><span class="sxs-lookup"><span data-stu-id="06e8c-145">To limit accessibility to only derived classes in the same assembly, declare the class itself internal, and declare its members as protected.</span></span> <span data-ttu-id="06e8c-146">また、C# 7.2 以降、外側のクラスを internal にしなくても、private protected アクセス修飾子を利用して同じ結果を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="06e8c-146">Also, starting with C# 7.2, you can use the private protected access modifier to achieve the same result without need to make the containing class internal.</span></span>  
  
## <a name="other-types"></a><span data-ttu-id="06e8c-147">その他の型</span><span class="sxs-lookup"><span data-stu-id="06e8c-147">Other Types</span></span>  
 <span data-ttu-id="06e8c-148">名前空間内に直接宣言されたインターフェイスは、public または internal として宣言できます。クラスや構造体と同様、インターフェイスの既定のアクセス レベルは internal になります。</span><span class="sxs-lookup"><span data-stu-id="06e8c-148">Interfaces declared directly within a namespace can be declared as public or internal and, just like classes and structs, interfaces default to internal access.</span></span> <span data-ttu-id="06e8c-149">インターフェイスのメンバーは常に public です。他の型がクラスや構造体にアクセスできるようにすることがインターフェイスの目的であるためです。</span><span class="sxs-lookup"><span data-stu-id="06e8c-149">Interface members are always public because the purpose of an interface is to enable other types to access a class or struct.</span></span> <span data-ttu-id="06e8c-150">インターフェイスのメンバーにアクセス修飾子を適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="06e8c-150">No access modifiers can be applied to interface members.</span></span>  
  
 <span data-ttu-id="06e8c-151">列挙型のメンバーは常に public となり、アクセス修飾子を適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="06e8c-151">Enumeration members are always public, and no access modifiers can be applied.</span></span>  
  
 <span data-ttu-id="06e8c-152">デリゲートの振る舞いは、クラスおよび構造体と似ています。</span><span class="sxs-lookup"><span data-stu-id="06e8c-152">Delegates behave like classes and structs.</span></span> <span data-ttu-id="06e8c-153">既定では、名前空間内に直接宣言されているときには internal アクセスが、入れ子にされているときは private アクセスが適用されます。</span><span class="sxs-lookup"><span data-stu-id="06e8c-153">By default, they have internal access when declared directly within a namespace, and private access when nested.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="06e8c-154">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="06e8c-154">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="06e8c-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="06e8c-155">See also</span></span>

- [<span data-ttu-id="06e8c-156">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="06e8c-156">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="06e8c-157">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="06e8c-157">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="06e8c-158">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="06e8c-158">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="06e8c-159">private</span><span class="sxs-lookup"><span data-stu-id="06e8c-159">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="06e8c-160">public</span><span class="sxs-lookup"><span data-stu-id="06e8c-160">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="06e8c-161">internal</span><span class="sxs-lookup"><span data-stu-id="06e8c-161">internal</span></span>](../../language-reference/keywords/internal.md)
- [<span data-ttu-id="06e8c-162">protected</span><span class="sxs-lookup"><span data-stu-id="06e8c-162">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="06e8c-163">protected internal</span><span class="sxs-lookup"><span data-stu-id="06e8c-163">protected internal</span></span>](../../language-reference/keywords/protected-internal.md)
- [<span data-ttu-id="06e8c-164">private protected</span><span class="sxs-lookup"><span data-stu-id="06e8c-164">private protected</span></span>](../../language-reference/keywords/private-protected.md)
- [<span data-ttu-id="06e8c-165">class</span><span class="sxs-lookup"><span data-stu-id="06e8c-165">class</span></span>](../../language-reference/keywords/class.md)
- [<span data-ttu-id="06e8c-166">struct</span><span class="sxs-lookup"><span data-stu-id="06e8c-166">struct</span></span>](../../language-reference/keywords/struct.md)
- [<span data-ttu-id="06e8c-167">interface</span><span class="sxs-lookup"><span data-stu-id="06e8c-167">interface</span></span>](../../language-reference/keywords/interface.md)
