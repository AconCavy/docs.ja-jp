---
title: ジェネリックと属性 - C# プログラミング ガイド
description: ジェネリック型に属性を適用する方法について説明します。 コード例を参照し、使用可能なその他のリソースを確認してください。
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 17556af2e1bc2963de953cea242d7000509acbcd
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299878"
---
# <a name="generics-and-attributes-c-programming-guide"></a><span data-ttu-id="c3a08-104">ジェネリックと属性 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="c3a08-104">Generics and Attributes (C# Programming Guide)</span></span>
<span data-ttu-id="c3a08-105">属性は、非ジェネリック型の場合と同様に、ジェネリック型に適用できます。</span><span class="sxs-lookup"><span data-stu-id="c3a08-105">Attributes can be applied to generic types in the same way as non-generic types.</span></span> <span data-ttu-id="c3a08-106">属性の適用については、「[属性](../concepts/attributes/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c3a08-106">For more information on applying attributes, see [Attributes](../concepts/attributes/index.md).</span></span>  
  
 <span data-ttu-id="c3a08-107">カスタム属性は、型引数が与えられないオープン ジェネリック型と、すべての型パラメーターに引数が与えられる、構築クローズ ジェネリック型のみ参照が許可されます。</span><span class="sxs-lookup"><span data-stu-id="c3a08-107">Custom attributes are only permitted to reference open generic types, which are generic types for which no type arguments are supplied, and closed constructed generic types, which supply arguments for all type parameters.</span></span>  
  
 <span data-ttu-id="c3a08-108">次の例では、このカスタム属性が使用されています。</span><span class="sxs-lookup"><span data-stu-id="c3a08-108">The following examples use this custom attribute:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#48)]  
  
 <span data-ttu-id="c3a08-109">属性は、オープン ジェネリック型を参照できます。</span><span class="sxs-lookup"><span data-stu-id="c3a08-109">An attribute can reference an open generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#49)]  
  
 <span data-ttu-id="c3a08-110">適切な数のコンマを利用し、複数の型パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="c3a08-110">Specify multiple type parameters using the appropriate number of commas.</span></span> <span data-ttu-id="c3a08-111">この例では、`GenericClass2` には 2 つの型パラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="c3a08-111">In this example, `GenericClass2` has two type parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#50)]  
  
 <span data-ttu-id="c3a08-112">属性は、構築クローズ ジェネリック型を参照できます。</span><span class="sxs-lookup"><span data-stu-id="c3a08-112">An attribute can reference a closed constructed generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#51)]  
  
 <span data-ttu-id="c3a08-113">ジェネリック型パラメーターを参照する属性は、コンパイル時エラーを引き起こします。</span><span class="sxs-lookup"><span data-stu-id="c3a08-113">An attribute that references a generic type parameter will cause a compile-time error:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#52)]  
  
 <span data-ttu-id="c3a08-114">ジェネリック型は <xref:System.Attribute> から継承できません。</span><span class="sxs-lookup"><span data-stu-id="c3a08-114">A generic type cannot inherit from <xref:System.Attribute>:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#53)]  
  
 <span data-ttu-id="c3a08-115">実行時にジェネリック型または型パラメーターに関する情報を取得するには、<xref:System.Reflection> のメソッドを利用できます。</span><span class="sxs-lookup"><span data-stu-id="c3a08-115">To obtain information about a generic type or type parameter at run time, you can use the methods of <xref:System.Reflection>.</span></span> <span data-ttu-id="c3a08-116">詳細については、「[ジェネリックとリフレクション](./generics-and-reflection.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c3a08-116">For more information, see [Generics and Reflection](./generics-and-reflection.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3a08-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="c3a08-117">See also</span></span>

- [<span data-ttu-id="c3a08-118">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="c3a08-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c3a08-119">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="c3a08-119">Generics</span></span>](./index.md)
- [<span data-ttu-id="c3a08-120">属性</span><span class="sxs-lookup"><span data-stu-id="c3a08-120">Attributes</span></span>](../../../standard/attributes/index.md)
