---
title: クラス、構造体、およびインターフェイスの名前
ms.date: 10/22/2008
helpviewer_keywords:
- type names, guidelines
- classes [.NET Framework], names
- enumerations [.NET Framework], names
- names [.NET Framework], interfaces
- common type names
- names [.NET Framework], type names
- names [.NET Framework], classes
- interfaces [.NET Framework], names
- generic type parameters
ms.assetid: 87a4b0da-ed64-43b1-ac43-968576c444ce
author: KrzysztofCwalina
ms.openlocfilehash: 2ecd708ccb8eb91270e8ef9c174b8d7e599a2629
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353703"
---
# <a name="names-of-classes-structs-and-interfaces"></a><span data-ttu-id="c2ea6-102">クラス、構造体、およびインターフェイスの名前</span><span class="sxs-lookup"><span data-stu-id="c2ea6-102">Names of Classes, Structs, and Interfaces</span></span>
<span data-ttu-id="c2ea6-103">次に示す名前付けのガイドラインは、一般的な型の名前付けに適用されます。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-103">The naming guidelines that follow apply to general type naming.</span></span>  
  
 <span data-ttu-id="c2ea6-104">**✓ DO** 名前をクラスと構造体には名詞または名詞句を使用して pascal 表記を使用します。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-104">**✓ DO** name classes and structs with nouns or noun phrases, using PascalCasing.</span></span>  
  
 <span data-ttu-id="c2ea6-105">これにより、動詞句を使用して名前が付けられたメソッドの型名が区別されます。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-105">This distinguishes type names from methods, which are named with verb phrases.</span></span>  
  
 <span data-ttu-id="c2ea6-106">**✓ DO** 形容詞句、または場合によっては名詞または名詞句とインターフェイスの名前します。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-106">**✓ DO** name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span></span>  
  
 <span data-ttu-id="c2ea6-107">名詞と名詞句を使用することはほとんどなく、型がインターフェイスではなく抽象クラスであることを示している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-107">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span></span>  
  
 <span data-ttu-id="c2ea6-108">**X DO NOT** クラス名のプレフィックス ("C"など) を指定します。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-108">**X DO NOT** give class names a prefix (e.g., "C").</span></span>  
  
 <span data-ttu-id="c2ea6-109">**✓ CONSIDER** 基底クラスの名前のクラスを派生の名前を終了します。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-109">**✓ CONSIDER** ending the name of derived classes with the name of the base class.</span></span>  
  
 <span data-ttu-id="c2ea6-110">これは非常に読みやすく、リレーションシップについて明確に説明しています。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-110">This is very readable and explains the relationship clearly.</span></span> <span data-ttu-id="c2ea6-111">このコードの例としては、`ArgumentOutOfRangeException`があります。これは `Exception`の一種であり、`SerializableAttribute`であり、`Attribute`です。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-111">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span></span> <span data-ttu-id="c2ea6-112">ただし、このガイドラインを適用するには、適切な判断を使用することが重要です。たとえば、`Button` クラスは `Control` イベントの一種ですが、名前に `Control` は表示されません。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-112">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span></span>  
  
 <span data-ttu-id="c2ea6-113">**✓ DO** インターフェイス名のプレフィックス文字では、型がインターフェイスであることを示します。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-113">**✓ DO** prefix interface names with the letter I, to indicate that the type is an interface.</span></span>  
  
 <span data-ttu-id="c2ea6-114">たとえば、`IComponent` (わかりやすい名詞)、`ICustomAttributeProvider` (名詞句)、および `IPersistable` (形容詞) は、適切なインターフェイス名です。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-114">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span></span> <span data-ttu-id="c2ea6-115">他の型名と同様に、省略形を避けます。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-115">As with other type names, avoid abbreviations.</span></span>  
  
 <span data-ttu-id="c2ea6-116">**✓ DO** だけで、"I"プレフィックスのインターフェイスの名前、クラスがインターフェイスの標準的な実装であるクラス – インターフェイスのペアを定義するときに名前が異なることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-116">**✓ DO** ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span></span>  
  
## <a name="names-of-generic-type-parameters"></a><span data-ttu-id="c2ea6-117">ジェネリック型パラメーターの名前</span><span class="sxs-lookup"><span data-stu-id="c2ea6-117">Names of Generic Type Parameters</span></span>  
 <span data-ttu-id="c2ea6-118">ジェネリックが .NET Framework 2.0 に追加されました。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-118">Generics were added to .NET Framework 2.0.</span></span> <span data-ttu-id="c2ea6-119">この機能では、*型パラメーター*と呼ばれる新しい種類の識別子が導入されました。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-119">The feature introduced a new kind of identifier called *type parameter*.</span></span>  
  
 <span data-ttu-id="c2ea6-120">**✓ DO** 1 文字の名前が完全にわかり、わかりやすい名前と値を追加していない場合を除き、わかりやすい名前を持つジェネリック型パラメーターの名前します。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-120">**✓ DO** name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span></span>  
  
 <span data-ttu-id="c2ea6-121">**✓ CONSIDER** を使用して`T`の 1 文字の型パラメーターを 1 つの種類の型パラメーター名として。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-121">**✓ CONSIDER** using `T` as the type parameter name for types with one single-letter type parameter.</span></span>  
  
```csharp  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 <span data-ttu-id="c2ea6-122">**✓ DO** 説明的な型パラメーター名をプレフィックス`T`です。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-122">**✓ DO** prefix descriptive type parameter names with `T`.</span></span>  
  
```csharp  
public interface ISessionChannel<TSession> where TSession : ISession {  
    TSession Session { get; }  
}  
```  
  
 <span data-ttu-id="c2ea6-123">**✓ CONSIDER** 制約を示す名前、パラメーターの型パラメーター上に配置します。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-123">**✓ CONSIDER** indicating constraints placed on a type parameter in the name of the parameter.</span></span>  
  
 <span data-ttu-id="c2ea6-124">たとえば、`ISession` に制約されたパラメーターは `TSession`と呼ばれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-124">For example, a parameter constrained to `ISession` might be called `TSession`.</span></span>  
  
## <a name="names-of-common-types"></a><span data-ttu-id="c2ea6-125">共通型の名前</span><span class="sxs-lookup"><span data-stu-id="c2ea6-125">Names of Common Types</span></span>  
 <span data-ttu-id="c2ea6-126">**✓ DO** から派生または特定の .NET Framework 型を実装する型の名前を付けるときは、次の表に説明されているガイドラインに従ってください。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-126">**✓ DO** follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span></span>  
  
|<span data-ttu-id="c2ea6-127">基本型</span><span class="sxs-lookup"><span data-stu-id="c2ea6-127">Base Type</span></span>|<span data-ttu-id="c2ea6-128">派生/実装型のガイドライン</span><span class="sxs-lookup"><span data-stu-id="c2ea6-128">Derived/Implementing Type Guideline</span></span>|  
|---------------|------------------------------------------|  
|`System.Attribute`|<span data-ttu-id="c2ea6-129">**✓ DO** カスタム属性クラスの名前にサフィックス"Attribute"を追加します。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-129">**✓ DO** add the suffix "Attribute" to names of custom attribute classes.</span></span>|  
|`System.Delegate`|<span data-ttu-id="c2ea6-130">**✓ DO** イベントで使用されるデリゲートの名前にサフィックス"EventHandler"を追加します。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-130">**✓ DO** add the suffix "EventHandler" to names of delegates that are used in events.</span></span><br /><br /> <span data-ttu-id="c2ea6-131">**✓ DO** 以外のイベント ハンドラーとして使用されているデリゲートの名前に"Callback"サフィックスを追加します。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-131">**✓ DO** add the suffix "Callback" to names of delegates other than those used as event handlers.</span></span><br /><br /> <span data-ttu-id="c2ea6-132">**X DO NOT** 「代理」サフィックスをデリゲートに追加します。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-132">**X DO NOT** add the suffix "Delegate" to a delegate.</span></span>|  
|`System.EventArgs`|<span data-ttu-id="c2ea6-133">**✓ DO** "EventArgs です"というサフィックスを追加。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-133">**✓ DO** add the suffix "EventArgs."</span></span>|  
|`System.Enum`|<span data-ttu-id="c2ea6-134">**X DO NOT** 代わりに使用する言語でサポートされているキーワードを使用して; たとえば、C# の場合、次のように使用します。 このクラスから派生、`enum`キーワード。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-134">**X DO NOT** derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span></span><br /><br /> <span data-ttu-id="c2ea6-135">**X DO NOT** 「列挙」または"Flag"サフィックスを追加</span><span class="sxs-lookup"><span data-stu-id="c2ea6-135">**X DO NOT** add the suffix "Enum" or "Flag."</span></span>|  
|`System.Exception`|<span data-ttu-id="c2ea6-136">**✓ DO** "Exception"サフィックスを追加</span><span class="sxs-lookup"><span data-stu-id="c2ea6-136">**✓ DO** add the suffix "Exception."</span></span>|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|<span data-ttu-id="c2ea6-137">**✓ DO** 「ディクショナリ」というサフィックスを追加。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-137">**✓ DO** add the suffix "Dictionary."</span></span> <span data-ttu-id="c2ea6-138">`IDictionary` は特定の種類のコレクションであることに注意してくださいが、このガイドラインは、次に示す一般的なコレクションのガイドラインよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-138">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span></span>|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|<span data-ttu-id="c2ea6-139">**✓ DO** 「コレクション」サフィックスを追加</span><span class="sxs-lookup"><span data-stu-id="c2ea6-139">**✓ DO** add the suffix "Collection."</span></span>|  
|`System.IO.Stream`|<span data-ttu-id="c2ea6-140">**✓ DO** 「ストリームです」というサフィックスを追加。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-140">**✓ DO** add the suffix "Stream."</span></span>|  
|`CodeAccessPermission IPermission`|<span data-ttu-id="c2ea6-141">**✓ DO** 「権限」というサフィックスを追加。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-141">**✓ DO** add the suffix "Permission."</span></span>|  
  
## <a name="naming-enumerations"></a><span data-ttu-id="c2ea6-142">列挙型の名前付け</span><span class="sxs-lookup"><span data-stu-id="c2ea6-142">Naming Enumerations</span></span>  
 <span data-ttu-id="c2ea6-143">一般的に、列挙型の名前 (列挙型とも呼ばれます) は、標準的な型の名前付け規則に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-143">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span></span> <span data-ttu-id="c2ea6-144">ただし、列挙型に特に適用される追加のガイドラインがあります。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-144">However, there are additional guidelines that apply specifically to enums.</span></span>  
  
 <span data-ttu-id="c2ea6-145">**✓ DO** ビット フィールドがその値がない限り、列挙体の単数形の型名を使用します。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-145">**✓ DO** use a singular type name for an enumeration unless its values are bit fields.</span></span>  
  
 <span data-ttu-id="c2ea6-146">**✓ DO** ビット フィールドを持つ列挙体の複数形の型名を使用して値として、フラグ列挙型とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-146">**✓ DO** use a plural type name for an enumeration with bit fields as values, also called flags enum.</span></span>  
  
 <span data-ttu-id="c2ea6-147">**X DO NOT** 列挙型の型名で、「列挙」サフィックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-147">**X DO NOT** use an "Enum" suffix in enum type names.</span></span>  
  
 <span data-ttu-id="c2ea6-148">**X DO NOT** 「フラグを設定」を使用して、または"Flags"サフィックス列挙型では、名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-148">**X DO NOT** use "Flag" or "Flags" suffixes in enum type names.</span></span>  
  
 <span data-ttu-id="c2ea6-149">**X DO NOT** リッチ テキストの列挙型などの列挙値の名前 (例:"ad"ADO 列挙型の場合。)、"rtf"に対して、プレフィックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="c2ea6-149">**X DO NOT** use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span></span>  
  
 <span data-ttu-id="c2ea6-150">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="c2ea6-150">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="c2ea6-151">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="c2ea6-151">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2ea6-152">参照</span><span class="sxs-lookup"><span data-stu-id="c2ea6-152">See also</span></span>

- [<span data-ttu-id="c2ea6-153">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="c2ea6-153">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="c2ea6-154">名前付けのガイドライン</span><span class="sxs-lookup"><span data-stu-id="c2ea6-154">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
