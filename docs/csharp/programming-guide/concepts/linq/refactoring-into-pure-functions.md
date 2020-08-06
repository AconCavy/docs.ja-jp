---
title: 純粋関数へのリファクタリング (C#)
description: 純粋関数を使用してコードをリファクターする方法について説明します。 コード例を参照し、使用可能なその他のリソースを確認してください。
ms.date: 07/20/2015
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: cc5dd26923e2edaed34c8f1b742b3dfa1e935e68
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87300229"
---
# <a name="refactoring-into-pure-functions-c"></a><span data-ttu-id="69907-104">純粋関数へのリファクタリング (C#)</span><span class="sxs-lookup"><span data-stu-id="69907-104">Refactoring Into Pure Functions (C#)</span></span>

<span data-ttu-id="69907-105">純粋関数型変換で重要なのは、純粋関数を使用してコードをリファクターする方法を理解することです。</span><span class="sxs-lookup"><span data-stu-id="69907-105">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="69907-106">関数型プログラミングでの命名には、一般に純粋関数を使用してプログラムをリファクターする方法が使用されます。</span><span class="sxs-lookup"><span data-stu-id="69907-106">The common nomenclature in functional programming is that you refactor programs using pure functions.</span></span> <span data-ttu-id="69907-107">Visual Basic および C++ では、この処理がそれぞれの言語の関数を使用して行われます。</span><span class="sxs-lookup"><span data-stu-id="69907-107">In Visual Basic and C++, this aligns with the use of functions in the respective languages.</span></span> <span data-ttu-id="69907-108">ただし C# では、関数がメソッドと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="69907-108">However, in C#, functions are called methods.</span></span> <span data-ttu-id="69907-109">ここでは、純粋関数が C# のメソッドとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="69907-109">For the purposes of this discussion, a pure function is implemented as a method in C#.</span></span>  
  
 <span data-ttu-id="69907-110">このセクションで既に説明したように、純粋関数には 2 つの実用的な特性があります。</span><span class="sxs-lookup"><span data-stu-id="69907-110">As noted previously in this section, a pure function has two useful characteristics:</span></span>  
  
- <span data-ttu-id="69907-111">副作用がありません。</span><span class="sxs-lookup"><span data-stu-id="69907-111">It has no side effects.</span></span> <span data-ttu-id="69907-112">この関数は、関数の外部にある変数やあらゆる型のデータを一切変更しません。</span><span class="sxs-lookup"><span data-stu-id="69907-112">The function does not change any variables or the data of any type outside of the function.</span></span>  
  
- <span data-ttu-id="69907-113">一貫性があります。</span><span class="sxs-lookup"><span data-stu-id="69907-113">It is consistent.</span></span> <span data-ttu-id="69907-114">同じ入力データを与えられると、常に同じ出力値を返します。</span><span class="sxs-lookup"><span data-stu-id="69907-114">Given the same set of input data, it will always return the same output value.</span></span>  
  
 <span data-ttu-id="69907-115">関数型プログラミングに移行するには、既存のコードをリファクターして不要な副作用や外部依存関係を排除するのが 1 つの方法です。</span><span class="sxs-lookup"><span data-stu-id="69907-115">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="69907-116">この方法で、既存のコードの純粋関数バージョンを作成できます。</span><span class="sxs-lookup"><span data-stu-id="69907-116">In this way, you can create pure function versions of existing code.</span></span>  
  
 <span data-ttu-id="69907-117">このトピックでは、純粋関数の特徴とそれ以外の関数の特徴について説明します。</span><span class="sxs-lookup"><span data-stu-id="69907-117">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="69907-118">「[チュートリアル: WordprocessingML ドキュメント内のコンテンツの操作 (C#)](./shape-of-wordprocessingml-documents.md)」チュートリアルでは、WordprocessingML ドキュメントの操作方法を説明し、純粋関数を使用してリファクターする方法を示す 2 つの例を紹介しています。</span><span class="sxs-lookup"><span data-stu-id="69907-118">The [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](./shape-of-wordprocessingml-documents.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="69907-119">副作用と外部依存関係の排除</span><span class="sxs-lookup"><span data-stu-id="69907-119">Eliminating Side Effects and External Dependencies</span></span>  
 <span data-ttu-id="69907-120">次の例に示す 2 つの非純粋関数と 1 つの純粋関数を参照して、その違いを確認してください。</span><span class="sxs-lookup"><span data-stu-id="69907-120">The following examples contrast two non-pure functions and a pure function.</span></span>  
  
### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="69907-121">クラス メンバーを変更する非純粋関数</span><span class="sxs-lookup"><span data-stu-id="69907-121">Non-Pure Function that Changes a Class Member</span></span>  
 <span data-ttu-id="69907-122">次のコードの `HyphenatedConcat` 関数は、クラス内の `aMember` データ メンバーを変更するため、純粋関数ではありません。</span><span class="sxs-lookup"><span data-stu-id="69907-122">In the following code, the `HyphenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>  
  
```csharp  
public class Program  
{  
    private static string aMember = "StringOne";  
  
    public static void HyphenatedConcat(string appendStr)  
    {  
        aMember += '-' + appendStr;  
    }  
  
    public static void Main()  
    {  
        HyphenatedConcat("StringTwo");  
        Console.WriteLine(aMember);  
    }  
}  
```  
  
 <span data-ttu-id="69907-123">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="69907-123">This code produces the following output:</span></span>  
  
```output  
StringOne-StringTwo  
```  
  
 <span data-ttu-id="69907-124">この場合、変更されるデータに `public` アクセスと `private` アクセスのどちらがあるか、またはこのデータが `static` メンバーとインスタンス メンバーのどちらであるかは関係ありません。</span><span class="sxs-lookup"><span data-stu-id="69907-124">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a `static` member or an instance member.</span></span> <span data-ttu-id="69907-125">純粋関数は、関数の外部にあるデータを一切変更しません。</span><span class="sxs-lookup"><span data-stu-id="69907-125">A pure function does not change any data outside of the function.</span></span>  
  
### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="69907-126">引数を変更する非純粋関数</span><span class="sxs-lookup"><span data-stu-id="69907-126">Non-Pure Function that Changes an Argument</span></span>  
 <span data-ttu-id="69907-127">同じ関数の次のバージョンは、そのパラメーターである `sb` の内容を変更するため、純粋関数ではありません。</span><span class="sxs-lookup"><span data-stu-id="69907-127">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>  
  
```csharp  
public class Program  
{  
    public static void HyphenatedConcat(StringBuilder sb, String appendStr)  
    {  
        sb.Append('-' + appendStr);  
    }  
  
    public static void Main()  
    {  
        StringBuilder sb1 = new StringBuilder("StringOne");  
        HyphenatedConcat(sb1, "StringTwo");  
        Console.WriteLine(sb1);  
    }  
}  
```  
  
 <span data-ttu-id="69907-128">このバージョンのプログラムは、最初のバージョンと同じ出力を生成します。これは、`HyphenatedConcat` 関数が <xref:System.Text.StringBuilder.Append%2A> メンバー関数を呼び出して最初のパラメーターの値 (状態) を変更したためです。</span><span class="sxs-lookup"><span data-stu-id="69907-128">This version of the program produces the same output as the first version, because the `HyphenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="69907-129">`HyphenatedConcat` はパラメーターを値で渡しますが、それでもこの変更は行われるので注意してください。</span><span class="sxs-lookup"><span data-stu-id="69907-129">Note that this alteration occurs despite that fact that `HyphenatedConcat` uses call-by-value parameter passing.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="69907-130">参照型の場合、パラメーターを値で渡すと、渡されるオブジェクトへの参照がコピーされて渡されます。</span><span class="sxs-lookup"><span data-stu-id="69907-130">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="69907-131">このコピーは、参照変数が新しいオブジェクトに割り当てられるまで、元の参照と同じインスタンス データに関連付けられたままとなります。</span><span class="sxs-lookup"><span data-stu-id="69907-131">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="69907-132">パラメーターを変更する場合に、必ずしも関数に参照を渡す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="69907-132">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>  
  
### <a name="pure-function"></a><span data-ttu-id="69907-133">純粋関数</span><span class="sxs-lookup"><span data-stu-id="69907-133">Pure Function</span></span>  
<span data-ttu-id="69907-134">次のバージョンのプログラムは、`HyphenatedConcat` 関数を純粋関数として実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="69907-134">This next version of the program shows how to implement the `HyphenatedConcat` function as a pure function.</span></span>  
  
```csharp  
class Program  
{  
    public static string HyphenatedConcat(string s, string appendStr)  
    {  
        return (s + '-' + appendStr);  
    }  
  
    public static void Main(string[] args)  
    {  
        string s1 = "StringOne";  
        string s2 = HyphenatedConcat(s1, "StringTwo");  
        Console.WriteLine(s2);  
    }  
}  
```  
  
 <span data-ttu-id="69907-135">このバージョンも、同じ出力行 `StringOne-StringTwo` を生成します。</span><span class="sxs-lookup"><span data-stu-id="69907-135">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="69907-136">この連結された値を保持するために、中間変数 `s2` が使用されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="69907-136">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>  
  
 <span data-ttu-id="69907-137">ローカルには純粋ではないが (つまりローカル変数を宣言して変更する)、グローバルには純粋である関数を作成すると、非常に便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="69907-137">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="69907-138">このような関数は、必要に応じて構成できる特性を多く備えていますが、関数型プログラミングの複雑な表現方法の一部 (単純なループによる処理を行う場合は再帰を使用する必要があるなど) が省かれています。</span><span class="sxs-lookup"><span data-stu-id="69907-138">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>  
  
## <a name="standard-query-operators"></a><span data-ttu-id="69907-139">標準クエリ演算子</span><span class="sxs-lookup"><span data-stu-id="69907-139">Standard Query Operators</span></span>  
 <span data-ttu-id="69907-140">標準クエリ演算子の重要な特性は、純粋関数として実装される点です。</span><span class="sxs-lookup"><span data-stu-id="69907-140">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>  
  
 <span data-ttu-id="69907-141">詳細については、「[標準クエリ演算子の概要 (C#)](./standard-query-operators-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69907-141">For more information, see [Standard Query Operators Overview (C#)](./standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69907-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="69907-142">See also</span></span>

- [<span data-ttu-id="69907-143">純粋関数型変換の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="69907-143">Introduction to Pure Functional Transformations (C#)</span></span>](./introduction-to-pure-functional-transformations.md)
- [<span data-ttu-id="69907-144">関数型プログラミングと命令型プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="69907-144">Functional Programming vs. Imperative Programming (C#)</span></span>](./functional-programming-vs-imperative-programming.md)
