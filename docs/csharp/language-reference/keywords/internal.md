---
title: internal - C# リファレンス
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: e5a5ca18828b689241abbb6d80c5adc51efb073c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173602"
---
# <a name="internal-c-reference"></a><span data-ttu-id="4b909-102">internal (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="4b909-102">internal (C# Reference)</span></span>
<span data-ttu-id="4b909-103">`internal` キーワードは、型と型のメンバーを示す[アクセス修飾子](./access-modifiers.md)です。</span><span class="sxs-lookup"><span data-stu-id="4b909-103">The `internal` keyword is an [access modifier](./access-modifiers.md) for types and type members.</span></span>
  
 > <span data-ttu-id="4b909-104">このページでは、`internal` アクセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4b909-104">This page covers `internal` access.</span></span> <span data-ttu-id="4b909-105">`internal` キーワードも [`protected internal`](./protected-internal.md) アクセス修飾子に含まれます。</span><span class="sxs-lookup"><span data-stu-id="4b909-105">The `internal` keyword is also part of the [`protected internal`](./protected-internal.md) access modifier.</span></span>
  
<span data-ttu-id="4b909-106">internal 型またはメンバーは、次の例のように、同じアセンブリ内のファイルでのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="4b909-106">Internal types or members are accessible only within files in the same assembly, as in this example:</span></span>  
  
```csharp  
public class BaseClass
{  
    // Only accessible within the same assembly.
    internal static int x = 0;
}  
```  

 <span data-ttu-id="4b909-107">`internal` とその他のアクセス修飾子の比較については、「[アクセシビリティ レベル](./accessibility-levels.md)」と「[アクセス修飾子](../../programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b909-107">For a comparison of `internal` with the other access modifiers, see [Accessibility Levels](./accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="4b909-108">アセンブリについて詳しくは、「[.NET のアセンブリ](../../../standard/assembly/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4b909-108">For more information about assemblies, see [Assemblies in .NET](../../../standard/assembly/index.md).</span></span>  
  
 <span data-ttu-id="4b909-109">一般的に、内部アクセスはコンポーネント ベースの開発で使用されます。これは、コンポーネントのグループを、アプリケーション コードの他の部分に公開することなくプライベートに連携させることができるためです。</span><span class="sxs-lookup"><span data-stu-id="4b909-109">A common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code.</span></span> <span data-ttu-id="4b909-110">たとえば、グラフィカル ユーザー インターフェイスを構築するためのフレームワークでは、内部アクセスによってメンバーを使用することで連携する `Control` クラスと `Form` クラスを提供できます。</span><span class="sxs-lookup"><span data-stu-id="4b909-110">For example, a framework for building graphical user interfaces could provide `Control` and `Form` classes that cooperate by using members with internal access.</span></span> <span data-ttu-id="4b909-111">これらは内部のメンバーなので、フレームワークを使用しているコードには公開されません。</span><span class="sxs-lookup"><span data-stu-id="4b909-111">Since these members are internal, they are not exposed to code that is using the framework.</span></span>  
  
 <span data-ttu-id="4b909-112">型またはメンバーが定義されているアセンブリの外側で、型またはメンバーを内部アクセスで参照するとエラーになります。</span><span class="sxs-lookup"><span data-stu-id="4b909-112">It is an error to reference a type or a member with internal access outside the assembly within which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b909-113">例</span><span class="sxs-lookup"><span data-stu-id="4b909-113">Example</span></span>  
 <span data-ttu-id="4b909-114">この例には、2 つのファイル (`Assembly1.cs` と `Assembly1_a.cs`) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4b909-114">This example contains two files, `Assembly1.cs` and `Assembly1_a.cs`.</span></span> <span data-ttu-id="4b909-115">最初のファイルには、内部の基底クラス `BaseClass` が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4b909-115">The first file contains an internal base class, `BaseClass`.</span></span> <span data-ttu-id="4b909-116">2 番目のファイルでは、`BaseClass` のインスタンス化を試行するとエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="4b909-116">In the second file, an attempt to instantiate `BaseClass` will produce an error.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="4b909-117">例</span><span class="sxs-lookup"><span data-stu-id="4b909-117">Example</span></span>  
 <span data-ttu-id="4b909-118">この例では、例 1 で使用したのと同じファイルを使用し、`BaseClass` のアクセシビリティ レベルを `public` に変更します。</span><span class="sxs-lookup"><span data-stu-id="4b909-118">In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`.</span></span> <span data-ttu-id="4b909-119">また、メンバー `intM` のアクセシビリティ レベルを `internal` に変更します。</span><span class="sxs-lookup"><span data-stu-id="4b909-119">Also change the accessibility level of the member `intM` to `internal`.</span></span> <span data-ttu-id="4b909-120">この場合、クラスのインスタンス化は可能ですが、内部メンバーへのアクセスはできません。</span><span class="sxs-lookup"><span data-stu-id="4b909-120">In this case, you can instantiate the class, but you cannot access the internal member.</span></span>  
  
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
  
## <a name="c-language-specification"></a><span data-ttu-id="4b909-121">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="4b909-121">C# Language Specification</span></span>  

<span data-ttu-id="4b909-122">詳細については、「[C# 言語仕様](~/_csharplang/spec/basic-concepts.md#declared-accessibility)」の[宣言されたアクセシビリティ](/dotnet/csharp/language-reference/language-specification/introduction)に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b909-122">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="4b909-123">言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。</span><span class="sxs-lookup"><span data-stu-id="4b909-123">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4b909-124">参照</span><span class="sxs-lookup"><span data-stu-id="4b909-124">See also</span></span>

- [<span data-ttu-id="4b909-125">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="4b909-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4b909-126">C# プログラミングガイド</span><span class="sxs-lookup"><span data-stu-id="4b909-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4b909-127">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="4b909-127">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="4b909-128">アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="4b909-128">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="4b909-129">アクセシビリティ レベル</span><span class="sxs-lookup"><span data-stu-id="4b909-129">Accessibility Levels</span></span>](./accessibility-levels.md)
- [<span data-ttu-id="4b909-130">修飾子</span><span class="sxs-lookup"><span data-stu-id="4b909-130">Modifiers</span></span>](index.md)
- [<span data-ttu-id="4b909-131">public</span><span class="sxs-lookup"><span data-stu-id="4b909-131">public</span></span>](./public.md)
- [<span data-ttu-id="4b909-132">private</span><span class="sxs-lookup"><span data-stu-id="4b909-132">private</span></span>](./private.md)
- [<span data-ttu-id="4b909-133">protected</span><span class="sxs-lookup"><span data-stu-id="4b909-133">protected</span></span>](./protected.md)
