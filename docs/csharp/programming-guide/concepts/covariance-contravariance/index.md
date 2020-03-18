---
title: 共変性と反変性 (C#)
ms.date: 07/20/2015
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
ms.openlocfilehash: 80b4d703bb88d0bf1f7f48236c21b7698017e7f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "79169871"
---
# <a name="covariance-and-contravariance-c"></a><span data-ttu-id="2f489-102">共変性と反変性 (C#)</span><span class="sxs-lookup"><span data-stu-id="2f489-102">Covariance and Contravariance (C#)</span></span>
<span data-ttu-id="2f489-103">C# では、共変性と反変性により、配列型、デリゲート型、およびジェネリック型引数の暗黙の参照変換が可能になります。</span><span class="sxs-lookup"><span data-stu-id="2f489-103">In C#, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="2f489-104">共変性は代入互換性を維持し、反変性はこれを反転させます。</span><span class="sxs-lookup"><span data-stu-id="2f489-104">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>  
  
 <span data-ttu-id="2f489-105">次のコードでは、代入互換性、共変性、および反変性の違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="2f489-105">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>  
  
```csharp  
// Assignment compatibility.
string str = "test";  
// An object of a more derived type is assigned to an object of a less derived type.
object obj = str;  
  
// Covariance.
IEnumerable<string> strings = new List<string>();  
// An object that is instantiated with a more derived type argument
// is assigned to an object instantiated with a less derived type argument.
// Assignment compatibility is preserved.
IEnumerable<object> objects = strings;  
  
// Contravariance.
// Assume that the following method is in the class:
// static void SetObject(object o) { }
Action<object> actObject = SetObject;  
// An object that is instantiated with a less derived type argument
// is assigned to an object instantiated with a more derived type argument.
// Assignment compatibility is reversed.
Action<string> actString = actObject;  
```  
  
 <span data-ttu-id="2f489-106">配列の共変性により、強い派生型の配列から弱い派生型の配列への暗黙の型変換が可能になります。</span><span class="sxs-lookup"><span data-stu-id="2f489-106">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="2f489-107">ただし、次のコード例に示すように、この操作はタイプ セーフではありません。</span><span class="sxs-lookup"><span data-stu-id="2f489-107">But this operation is not type safe, as shown in the following code example.</span></span>  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 <span data-ttu-id="2f489-108">メソッド グループの共変性と反変性のサポートにより、メソッド シグネチャをデリゲート型と一致させることができます。</span><span class="sxs-lookup"><span data-stu-id="2f489-108">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="2f489-109">これにより、一致するシグネチャを持つメソッドだけでなく、デリゲート型で指定された型よりも強い派生型 (共変性) を返すメソッドや、弱い派生型 (反変性) のパラメーターを受け取るメソッドを、デリゲートに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="2f489-109">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="2f489-110">詳細については、「[デリゲートの変性 (C#)](./variance-in-delegates.md)」および「[デリゲートの変性の使用 (C#)](./using-variance-in-delegates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f489-110">For more information, see [Variance in Delegates (C#)](./variance-in-delegates.md) and [Using Variance in Delegates (C#)](./using-variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="2f489-111">次のコード例は、メソッド グループでの共変性と反変性のサポートを示しています。</span><span class="sxs-lookup"><span data-stu-id="2f489-111">The following code example shows covariance and contravariance support for method groups.</span></span>  
  
```csharp  
static object GetObject() { return null; }  
static void SetObject(object obj) { }  
  
static string GetString() { return ""; }  
static void SetString(string str) { }  
  
static void Test()  
{  
    // Covariance. A delegate specifies a return type as object,  
    // but you can assign a method that returns a string.  
    Func<object> del = GetString;  
  
    // Contravariance. A delegate specifies a parameter type as string,  
    // but you can assign a method that takes an object.  
    Action<string> del2 = SetObject;  
}  
```  
  
 <span data-ttu-id="2f489-112">.NET Framework 4 以降では、C# でジェネリック インターフェイスと汎用デリゲートでの共変性と反変性がサポートされ、ジェネリック型パラメーターの暗黙の型変換が可能になっています。</span><span class="sxs-lookup"><span data-stu-id="2f489-112">In .NET Framework 4 or newer C# supports covariance and contravariance in generic interfaces and delegates and allows for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="2f489-113">詳細については、「[ジェネリック インターフェイスの変性 (C#)](./variance-in-generic-interfaces.md)」および「[デリゲートの変性 (C#)](./variance-in-delegates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f489-113">For more information, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md) and [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="2f489-114">次のコード例は、ジェネリック インターフェイスの暗黙の参照変換を示しています。</span><span class="sxs-lookup"><span data-stu-id="2f489-114">The following code example shows implicit reference conversion for generic interfaces.</span></span>  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 <span data-ttu-id="2f489-115">ジェネリック インターフェイスや汎用デリゲートは、そのジェネリック パラメーターが共変または反変として宣言されている場合、*バリアント*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="2f489-115">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="2f489-116">C# では、独自のバリアント インターフェイスおよびデリゲートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="2f489-116">C# enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="2f489-117">詳細については、「[バリアント ジェネリック インターフェイスの作成 (C#)](./creating-variant-generic-interfaces.md)」および「[デリゲートの分散 (C#)](./variance-in-delegates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f489-117">For more information, see [Creating Variant Generic Interfaces (C#)](./creating-variant-generic-interfaces.md) and [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="2f489-118">関連トピック</span><span class="sxs-lookup"><span data-stu-id="2f489-118">Related Topics</span></span>  
  
|<span data-ttu-id="2f489-119">タイトル</span><span class="sxs-lookup"><span data-stu-id="2f489-119">Title</span></span>|<span data-ttu-id="2f489-120">[説明]</span><span class="sxs-lookup"><span data-stu-id="2f489-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="2f489-121">ジェネリック インターフェイスの変性 (C#)</span><span class="sxs-lookup"><span data-stu-id="2f489-121">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)|<span data-ttu-id="2f489-122">ジェネリック インターフェイスでの共変性と反変性について説明し、.NET Framework でのバリアント ジェネリック インターフェイスの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="2f489-122">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|  
|[<span data-ttu-id="2f489-123">バリアント ジェネリック インターフェイスの作成 (C#)</span><span class="sxs-lookup"><span data-stu-id="2f489-123">Creating Variant Generic Interfaces (C#)</span></span>](./creating-variant-generic-interfaces.md)|<span data-ttu-id="2f489-124">カスタムのバリアント インターフェイスを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2f489-124">Shows how to create custom variant interfaces.</span></span>|  
|[<span data-ttu-id="2f489-125">ジェネリック コレクションに対するインターフェイスでの変性の使用 (C#)</span><span class="sxs-lookup"><span data-stu-id="2f489-125">Using Variance in Interfaces for Generic Collections (C#)</span></span>](./using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="2f489-126"><xref:System.Collections.Generic.IEnumerable%601> および <xref:System.IComparable%601> インターフェイスでの共変性と反変性のサポートがコードの再利用にどのように役立つかを示します。</span><span class="sxs-lookup"><span data-stu-id="2f489-126">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|  
|[<span data-ttu-id="2f489-127">デリゲートの変性 (C#)</span><span class="sxs-lookup"><span data-stu-id="2f489-127">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)|<span data-ttu-id="2f489-128">汎用および非汎用デリゲートでの共変性と反変性について説明し、.NET Framework でのバリアント汎用デリゲートの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="2f489-128">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|  
|[<span data-ttu-id="2f489-129">デリゲートの変性の使用 (C#)</span><span class="sxs-lookup"><span data-stu-id="2f489-129">Using Variance in Delegates (C#)</span></span>](./using-variance-in-delegates.md)|<span data-ttu-id="2f489-130">非汎用デリゲートでの共変性と反変性のサポートを使用して、メソッド シグネチャをデリゲート型に一致させる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2f489-130">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|  
|[<span data-ttu-id="2f489-131">Func および Action 汎用デリゲートでの分散の使用 (C#)</span><span class="sxs-lookup"><span data-stu-id="2f489-131">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="2f489-132">`Func` および `Action` デリゲートでの共変性と反変性のサポートがコードの再利用にどのように役立つかを示します。</span><span class="sxs-lookup"><span data-stu-id="2f489-132">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
