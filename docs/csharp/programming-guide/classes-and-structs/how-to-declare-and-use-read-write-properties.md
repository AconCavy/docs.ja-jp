---
title: 読み取り/書き込みプロパティを宣言および使用する方法 - C# プログラミング ガイド
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 4b9db5f15746ab9a1f42239150c6783154723371
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170287"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a><span data-ttu-id="a5a9e-102">読み取り/書き込みプロパティを宣言および使用する方法 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="a5a9e-102">How to declare and use read write properties (C# Programming Guide)</span></span>
<span data-ttu-id="a5a9e-103">プロパティは、オブジェクトのデータへの保護されていない、制御されず未確認のアクセスに伴うリスクなしにパブリック データ メンバーの利便性を提供します。</span><span class="sxs-lookup"><span data-stu-id="a5a9e-103">Properties provide the convenience of public data members without the risks that come with unprotected, uncontrolled, and unverified access to an object's data.</span></span> <span data-ttu-id="a5a9e-104">これは*アクセサー*を通じて行われます。アクセサーは、基になるデータ メンバーの値を割り当てたり、取得したりする特殊なメソッドです。</span><span class="sxs-lookup"><span data-stu-id="a5a9e-104">This is accomplished through *accessors*: special methods that assign and retrieve values from the underlying data member.</span></span> <span data-ttu-id="a5a9e-105">[set](../../language-reference/keywords/set.md) アクセサーはデータ メンバーの割り当てを可能にし、[get](../../language-reference/keywords/get.md) アクセサーはデータ メンバーの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="a5a9e-105">The [set](../../language-reference/keywords/set.md) accessor enables data members to be assigned, and the [get](../../language-reference/keywords/get.md) accessor retrieves data member values.</span></span>  
  
 <span data-ttu-id="a5a9e-106">このサンプルでは、`Person` (string) および `Name` (int) という 2 つのプロパティを持つ `Age` クラスを示します。</span><span class="sxs-lookup"><span data-stu-id="a5a9e-106">This sample shows a `Person` class that has two properties: `Name` (string) and `Age` (int).</span></span> <span data-ttu-id="a5a9e-107">両方のプロパティは `get` および `set` アクセサーを提供するため、読み取り/書き込みプロパティと見なされます。</span><span class="sxs-lookup"><span data-stu-id="a5a9e-107">Both properties provide `get` and `set` accessors, so they are considered read/write properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5a9e-108">例</span><span class="sxs-lookup"><span data-stu-id="a5a9e-108">Example</span></span>  
 [!code-csharp[csProgGuideObjects#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#33)]  
  
## <a name="robust-programming"></a><span data-ttu-id="a5a9e-109">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="a5a9e-109">Robust Programming</span></span>  
 <span data-ttu-id="a5a9e-110">前述の例では、`Name` および `Age` プロパティは[パブリック](../../language-reference/keywords/public.md)であり、`get` および `set` アクセサーの両方が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a5a9e-110">In the previous example, the `Name` and `Age` properties are [public](../../language-reference/keywords/public.md) and include both a `get` and a `set` accessor.</span></span> <span data-ttu-id="a5a9e-111">そのため、任意のオブジェクトがこれらのプロパティを読み書きできます。</span><span class="sxs-lookup"><span data-stu-id="a5a9e-111">This allows any object to read and write these properties.</span></span> <span data-ttu-id="a5a9e-112">ただし、アクセサーのいずれかを除外することが望ましい場合もあります。</span><span class="sxs-lookup"><span data-stu-id="a5a9e-112">It is sometimes desirable, however, to exclude one of the accessors.</span></span> <span data-ttu-id="a5a9e-113">たとえば、次のように `set` アクセサーを省略すると、プロパティが読み取り専用になります。</span><span class="sxs-lookup"><span data-stu-id="a5a9e-113">Omitting the `set` accessor, for example, makes the property read-only:</span></span>  
  
 [!code-csharp[csProgGuideObjects#87](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#87)]  
  
 <span data-ttu-id="a5a9e-114">また、一方のアクセサーをパブリックに公開し、もう一方を private または protected にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="a5a9e-114">Alternatively, you can expose one accessor publicly but make the other private or protected.</span></span> <span data-ttu-id="a5a9e-115">詳細については、「[アクセサーのアクセシビリティの制限 (C# プログラミング ガイド)](./restricting-accessor-accessibility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5a9e-115">For more information, see [Asymmetric Accessor Accessibility](./restricting-accessor-accessibility.md).</span></span>  
  
 <span data-ttu-id="a5a9e-116">プロパティを宣言すると、プロパティをクラスのフィールドのように使用できます。</span><span class="sxs-lookup"><span data-stu-id="a5a9e-116">Once the properties are declared, they can be used as if they were fields of the class.</span></span> <span data-ttu-id="a5a9e-117">そのため、プロパティ値の取得と設定の両方で、次のように自然な構文を使用できます。</span><span class="sxs-lookup"><span data-stu-id="a5a9e-117">This allows for a very natural syntax when both getting and setting the value of a property, as in the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#35)]  
  
 <span data-ttu-id="a5a9e-118">プロパティの `set` メソッドでは、特殊な `value` 変数を使用できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a5a9e-118">Note that in a property `set` method a special `value` variable is available.</span></span> <span data-ttu-id="a5a9e-119">この変数には、ユーザーが指定した値が含まれます。たとえば、次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="a5a9e-119">This variable contains the value that the user specified, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#36)]  
  
 <span data-ttu-id="a5a9e-120">`Age` オブジェクトの `Person` プロパティの値を増分する場合は、次のような簡潔な構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="a5a9e-120">Notice the clean syntax for incrementing the `Age` property on a `Person` object:</span></span>  
  
 [!code-csharp[csProgGuideObjects#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#37)]  
  
 <span data-ttu-id="a5a9e-121">`set` メソッドと `get` メソッドがそれぞれ使用されてプロパティがモデル化されている場合、上記と同じ内容のコードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a5a9e-121">If separate `set` and `get` methods were used to model properties, the equivalent code might look like this:</span></span>  
  
```csharp  
person.SetAge(person.GetAge() + 1);
```  
  
 <span data-ttu-id="a5a9e-122">この例では、`ToString` メソッドが次のようにオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="a5a9e-122">The `ToString` method is overridden in this example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#38)]  
  
 <span data-ttu-id="a5a9e-123">プログラムでは `ToString` が明示的に使用されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a5a9e-123">Notice that `ToString` is not explicitly used in the program.</span></span> <span data-ttu-id="a5a9e-124">既定では、`WriteLine` 呼び出しによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a5a9e-124">It is invoked by default by the `WriteLine` calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5a9e-125">参照</span><span class="sxs-lookup"><span data-stu-id="a5a9e-125">See also</span></span>

- [<span data-ttu-id="a5a9e-126">C# プログラミングガイド</span><span class="sxs-lookup"><span data-stu-id="a5a9e-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a5a9e-127">Properties</span><span class="sxs-lookup"><span data-stu-id="a5a9e-127">Properties</span></span>](./properties.md)
- [<span data-ttu-id="a5a9e-128">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="a5a9e-128">Classes and Structs</span></span>](./index.md)
