---
title: ジャグ配列 - C# プログラミング ガイド
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 56013f0143d5efcb31a476909cb6e92504ff0dbc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705705"
---
# <a name="jagged-arrays-c-programming-guide"></a><span data-ttu-id="f82c3-102">ジャグ配列 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="f82c3-102">Jagged Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="f82c3-103">ジャグ配列とは、その要素も配列である配列です。</span><span class="sxs-lookup"><span data-stu-id="f82c3-103">A jagged array is an array whose elements are arrays.</span></span> <span data-ttu-id="f82c3-104">ジャグ配列の要素には、異なるディメンションとサイズを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f82c3-104">The elements of a jagged array can be of different dimensions and sizes.</span></span> <span data-ttu-id="f82c3-105">ジャグ配列は、"配列の配列" と呼ばれることがあります。</span><span class="sxs-lookup"><span data-stu-id="f82c3-105">A jagged array is sometimes called an "array of arrays."</span></span> <span data-ttu-id="f82c3-106">次の例では、ジャグ配列の宣言、初期化、およびアクセスの方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f82c3-106">The following examples show how to declare, initialize, and access jagged arrays.</span></span>  
  
 <span data-ttu-id="f82c3-107">次の 3 つの要素を持つ 1 次元配列の宣言では、それぞれが整数の 1 次元配列になっています。</span><span class="sxs-lookup"><span data-stu-id="f82c3-107">The following is a declaration of a single-dimensional array that has three elements, each of which is a single-dimensional array of integers:</span></span>  
  
 [!code-csharp[csProgGuideArrays#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#19)]  
  
 <span data-ttu-id="f82c3-108">`jaggedArray` を使用する前に、その要素を初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f82c3-108">Before you can use `jaggedArray`, its elements must be initialized.</span></span> <span data-ttu-id="f82c3-109">次のように要素を初期化することができます。</span><span class="sxs-lookup"><span data-stu-id="f82c3-109">You can initialize the elements like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#20)]  
  
 <span data-ttu-id="f82c3-110">各要素は、整数の 1 次元配列です。</span><span class="sxs-lookup"><span data-stu-id="f82c3-110">Each of the elements is a single-dimensional array of integers.</span></span> <span data-ttu-id="f82c3-111">最初の要素は 5 つの整数の配列で、2 番目の要素は 4 つの整数の配列であり、3 番目の要素は 2 つの整数の配列です。</span><span class="sxs-lookup"><span data-stu-id="f82c3-111">The first element is an array of 5 integers, the second is an array of 4 integers, and the third is an array of 2 integers.</span></span>  
  
 <span data-ttu-id="f82c3-112">初期化子を使って配列の要素に値を格納することもできます。この場合、配列のサイズは不要です。</span><span class="sxs-lookup"><span data-stu-id="f82c3-112">It is also possible to use initializers to fill the array elements with values, in which case you do not need the array size.</span></span> <span data-ttu-id="f82c3-113">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="f82c3-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#21)]  
  
 <span data-ttu-id="f82c3-114">次のように宣言時に配列を初期化することもできます。</span><span class="sxs-lookup"><span data-stu-id="f82c3-114">You can also initialize the array upon declaration like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#22)]  
  
 <span data-ttu-id="f82c3-115">次の短い形式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f82c3-115">You can use the following shorthand form.</span></span> <span data-ttu-id="f82c3-116">要素の既定の初期化はないので、`new` 演算子を要素の初期化から省略することはできません。</span><span class="sxs-lookup"><span data-stu-id="f82c3-116">Notice that you cannot omit the `new` operator from the elements initialization because there is no default initialization for the elements:</span></span>  
  
 [!code-csharp[csProgGuideArrays#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#23)]  
  
 <span data-ttu-id="f82c3-117">ジャグ配列は配列の配列です。そのため、配列要素は参照型で、`null` に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="f82c3-117">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
 <span data-ttu-id="f82c3-118">これらの例のように配列の各要素にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="f82c3-118">You can access individual array elements like these examples:</span></span>  
  
 [!code-csharp[csProgGuideArrays#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#24)]  
  
 <span data-ttu-id="f82c3-119">ジャグ配列と多次元配列を混在させることができます。</span><span class="sxs-lookup"><span data-stu-id="f82c3-119">It is possible to mix jagged and multidimensional arrays.</span></span> <span data-ttu-id="f82c3-120">異なるサイズの 3 つの 2 次元の配列要素を含む 1 次元のジャグ配列の宣言と初期化を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f82c3-120">The following is a declaration and initialization of a single-dimensional jagged array that contains three two-dimensional array elements of different sizes.</span></span> <span data-ttu-id="f82c3-121">2 次元配列の詳細については、「[多次元配列](./multidimensional-arrays.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f82c3-121">For more information about two-dimensional arrays, see [Multidimensional Arrays](./multidimensional-arrays.md).</span></span>  
  
 [!code-csharp[csProgGuideArrays#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#25)]  
  
 <span data-ttu-id="f82c3-122">この例に示すように個々の要素にアクセスすることができます。この場合、最初の配列の要素 `[1,0]` の値 (値 `5`) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f82c3-122">You can access individual elements as shown in this example, which displays the value of the element `[1,0]` of the first array (value `5`):</span></span>  
  
 [!code-csharp[csProgGuideArrays#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#26)]  
  
 <span data-ttu-id="f82c3-123">メソッド `Length` は、ジャグ配列に含まれる配列の数を返します。</span><span class="sxs-lookup"><span data-stu-id="f82c3-123">The method `Length` returns the number of arrays contained in the jagged array.</span></span> <span data-ttu-id="f82c3-124">たとえば、前の配列を宣言し、次のコマンド ラインを実行したとします。</span><span class="sxs-lookup"><span data-stu-id="f82c3-124">For example, assuming you have declared the previous array, this line:</span></span>  
  
 [!code-csharp[csProgGuideArrays#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#27)]  
  
 <span data-ttu-id="f82c3-125">この場合は値 3 が返されます。</span><span class="sxs-lookup"><span data-stu-id="f82c3-125">returns a value of 3.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f82c3-126">例</span><span class="sxs-lookup"><span data-stu-id="f82c3-126">Example</span></span>

 <span data-ttu-id="f82c3-127">この例では、要素自体が配列である配列を構築します。</span><span class="sxs-lookup"><span data-stu-id="f82c3-127">This example builds an array whose elements are themselves arrays.</span></span> <span data-ttu-id="f82c3-128">配列の要素のそれぞれのサイズが異なります。</span><span class="sxs-lookup"><span data-stu-id="f82c3-128">Each one of the array elements has a different size.</span></span>  
  
 [!code-csharp[csProgGuideArrays#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#18)]  
  
## <a name="see-also"></a><span data-ttu-id="f82c3-129">参照</span><span class="sxs-lookup"><span data-stu-id="f82c3-129">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="f82c3-130">C# プログラミングガイド</span><span class="sxs-lookup"><span data-stu-id="f82c3-130">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f82c3-131">配列</span><span class="sxs-lookup"><span data-stu-id="f82c3-131">Arrays</span></span>](./index.md)
- [<span data-ttu-id="f82c3-132">1 次元配列</span><span class="sxs-lookup"><span data-stu-id="f82c3-132">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="f82c3-133">多次元配列</span><span class="sxs-lookup"><span data-stu-id="f82c3-133">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
