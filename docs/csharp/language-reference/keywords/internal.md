---
description: internal - C# リファレンス
title: internal - C# リファレンス
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: c66f4ff578e9864ebaf2b89ec03ce95f3cb2ba91
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168739"
---
# <a name="internal-c-reference"></a><span data-ttu-id="319aa-103">internal (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="319aa-103">internal (C# Reference)</span></span>

<span data-ttu-id="319aa-104">`internal` キーワードは、型と型のメンバーを示す[アクセス修飾子](./access-modifiers.md)です。</span><span class="sxs-lookup"><span data-stu-id="319aa-104">The `internal` keyword is an [access modifier](./access-modifiers.md) for types and type members.</span></span>
  
 > <span data-ttu-id="319aa-105">このページでは、`internal` アクセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="319aa-105">This page covers `internal` access.</span></span> <span data-ttu-id="319aa-106">`internal` キーワードも [`protected internal`](./protected-internal.md) アクセス修飾子に含まれます。</span><span class="sxs-lookup"><span data-stu-id="319aa-106">The `internal` keyword is also part of the [`protected internal`](./protected-internal.md) access modifier.</span></span>
  
<span data-ttu-id="319aa-107">internal 型またはメンバーは、次の例のように、同じアセンブリ内のファイルでのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="319aa-107">Internal types or members are accessible only within files in the same assembly, as in this example:</span></span>  
  
```csharp  
public class BaseClass
{  
    // Only accessible within the same assembly.
    internal static int x = 0;
}  
```  

 <span data-ttu-id="319aa-108">`internal` とその他のアクセス修飾子の比較については、「[アクセシビリティ レベル](./accessibility-levels.md)」と「[アクセス修飾子](../../programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="319aa-108">For a comparison of `internal` with the other access modifiers, see [Accessibility Levels](./accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="319aa-109">アセンブリについて詳しくは、「[.NET のアセンブリ](../../../standard/assembly/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="319aa-109">For more information about assemblies, see [Assemblies in .NET](../../../standard/assembly/index.md).</span></span>  
  
 <span data-ttu-id="319aa-110">一般的に、内部アクセスはコンポーネント ベースの開発で使用されます。これは、コンポーネントのグループを、アプリケーション コードの他の部分に公開することなくプライベートに連携させることができるためです。</span><span class="sxs-lookup"><span data-stu-id="319aa-110">A common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code.</span></span> <span data-ttu-id="319aa-111">たとえば、グラフィカル ユーザー インターフェイスを構築するためのフレームワークでは、内部アクセスによってメンバーを使用することで連携する `Control` クラスと `Form` クラスを提供できます。</span><span class="sxs-lookup"><span data-stu-id="319aa-111">For example, a framework for building graphical user interfaces could provide `Control` and `Form` classes that cooperate by using members with internal access.</span></span> <span data-ttu-id="319aa-112">これらは内部のメンバーなので、フレームワークを使用しているコードには公開されません。</span><span class="sxs-lookup"><span data-stu-id="319aa-112">Since these members are internal, they are not exposed to code that is using the framework.</span></span>  
  
 <span data-ttu-id="319aa-113">型またはメンバーが定義されているアセンブリの外側で、型またはメンバーを内部アクセスで参照するとエラーになります。</span><span class="sxs-lookup"><span data-stu-id="319aa-113">It is an error to reference a type or a member with internal access outside the assembly within which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="319aa-114">例</span><span class="sxs-lookup"><span data-stu-id="319aa-114">Example</span></span>  

 <span data-ttu-id="319aa-115">この例には、2 つのファイル (`Assembly1.cs` と `Assembly1_a.cs`) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="319aa-115">This example contains two files, `Assembly1.cs` and `Assembly1_a.cs`.</span></span> <span data-ttu-id="319aa-116">最初のファイルには、内部の基底クラス `BaseClass` が含まれています。</span><span class="sxs-lookup"><span data-stu-id="319aa-116">The first file contains an internal base class, `BaseClass`.</span></span> <span data-ttu-id="319aa-117">2 番目のファイルでは、`BaseClass` のインスタンス化を試行するとエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="319aa-117">In the second file, an attempt to instantiate `BaseClass` will produce an error.</span></span>  
  
```csharp  
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass
{  
   public static int intM = 0;  
}  
```  
  
```csharp  
// Assembly1_a.cs  
// Compile with: /reference:Assembly1.dll  
class TestAccess
{  
   static void Main()
   {  
      var myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="319aa-118">例</span><span class="sxs-lookup"><span data-stu-id="319aa-118">Example</span></span>  

 <span data-ttu-id="319aa-119">この例では、例 1 で使用したのと同じファイルを使用し、`BaseClass` のアクセシビリティ レベルを `public` に変更します。</span><span class="sxs-lookup"><span data-stu-id="319aa-119">In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`.</span></span> <span data-ttu-id="319aa-120">また、メンバー `intM` のアクセシビリティ レベルを `internal` に変更します。</span><span class="sxs-lookup"><span data-stu-id="319aa-120">Also change the accessibility level of the member `intM` to `internal`.</span></span> <span data-ttu-id="319aa-121">この場合、クラスのインスタンス化は可能ですが、内部メンバーへのアクセスはできません。</span><span class="sxs-lookup"><span data-stu-id="319aa-121">In this case, you can instantiate the class, but you cannot access the internal member.</span></span>  
  
```csharp  
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass
{  
   internal static int intM = 0;  
}  
```  
  
```csharp  
// Assembly2_a.cs  
// Compile with: /reference:Assembly2.dll  
public class TestAccess
{  
   static void Main()
   {  
      var myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="319aa-122">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="319aa-122">C# Language Specification</span></span>  

<span data-ttu-id="319aa-123">詳細については、「[C# 言語仕様](/dotnet/csharp/language-reference/language-specification/introduction)」の[宣言されたアクセシビリティ](~/_csharplang/spec/basic-concepts.md#declared-accessibility)に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="319aa-123">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="319aa-124">言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。</span><span class="sxs-lookup"><span data-stu-id="319aa-124">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="319aa-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="319aa-125">See also</span></span>

- [<span data-ttu-id="319aa-126">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="319aa-126">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="319aa-127">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="319aa-127">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="319aa-128">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="319aa-128">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="319aa-129">アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="319aa-129">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="319aa-130">アクセシビリティ レベル</span><span class="sxs-lookup"><span data-stu-id="319aa-130">Accessibility Levels</span></span>](./accessibility-levels.md)
- [<span data-ttu-id="319aa-131">修飾子</span><span class="sxs-lookup"><span data-stu-id="319aa-131">Modifiers</span></span>](index.md)
- [<span data-ttu-id="319aa-132">public</span><span class="sxs-lookup"><span data-stu-id="319aa-132">public</span></span>](./public.md)
- [<span data-ttu-id="319aa-133">private</span><span class="sxs-lookup"><span data-stu-id="319aa-133">private</span></span>](./private.md)
- [<span data-ttu-id="319aa-134">protected</span><span class="sxs-lookup"><span data-stu-id="319aa-134">protected</span></span>](./protected.md)
