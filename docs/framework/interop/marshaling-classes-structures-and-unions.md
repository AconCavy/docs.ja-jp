---
title: クラス、構造体、および共用体のマーシャリング
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, classes
- marshaling, unions
- marshaling, structures
- marshaling, samples
- data marshaling, structures
- platform invoke, marshaling data
- marshaling, classes
- data marshaling, unions
- data marshaling, samples
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: 027832a2-9b43-4fd9-9b45-7f4196261a4e
ms.openlocfilehash: d761d8ed7488e99f29d4844d061867915a624b96
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960005"
---
# <a name="marshaling-classes-structures-and-unions"></a><span data-ttu-id="0da5a-102">クラス、構造体、および共用体のマーシャリング</span><span class="sxs-lookup"><span data-stu-id="0da5a-102">Marshaling Classes, Structures, and Unions</span></span>

<span data-ttu-id="0da5a-103">クラスと構造体は、.NET Framework では類似しています。</span><span class="sxs-lookup"><span data-stu-id="0da5a-103">Classes and structures are similar in the .NET Framework.</span></span> <span data-ttu-id="0da5a-104">どちらもフィールド、プロパティ、およびイベントを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-104">Both can have fields, properties, and events.</span></span> <span data-ttu-id="0da5a-105">静的メソッドと非静的メソッドを持つこともできます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-105">They can also have static and nonstatic methods.</span></span> <span data-ttu-id="0da5a-106">1 つの重要な違いは、構造体は値型でクラスは参照型であることです。</span><span class="sxs-lookup"><span data-stu-id="0da5a-106">One notable difference is that structures are value types and classes are reference types.</span></span>

<span data-ttu-id="0da5a-107">次の表は、クラス、構造体、および共用体のマーシャリング オプションをリストし、それぞれの使用方法を説明し、対応するプラットフォーム呼び出しサンプルへのリンクを示しています。</span><span class="sxs-lookup"><span data-stu-id="0da5a-107">The following table lists marshaling options for classes, structures, and unions; describes their usage; and provides a link to the corresponding platform invoke sample.</span></span>

|<span data-ttu-id="0da5a-108">の型</span><span class="sxs-lookup"><span data-stu-id="0da5a-108">Type</span></span>|<span data-ttu-id="0da5a-109">説明</span><span class="sxs-lookup"><span data-stu-id="0da5a-109">Description</span></span>|<span data-ttu-id="0da5a-110">［サンプル］</span><span class="sxs-lookup"><span data-stu-id="0da5a-110">Sample</span></span>|
|----------|-----------------|------------|
|<span data-ttu-id="0da5a-111">値によるクラス。</span><span class="sxs-lookup"><span data-stu-id="0da5a-111">Class by value.</span></span>|<span data-ttu-id="0da5a-112">整数のメンバーを含むクラスは、管理対象クラスと同じように、In/Out パラメーターとして渡します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-112">Passes a class with integer members as an In/Out parameter, like the managed case.</span></span>|[<span data-ttu-id="0da5a-113">SysTime サンプル</span><span class="sxs-lookup"><span data-stu-id="0da5a-113">SysTime sample</span></span>](#systime-sample)|
|<span data-ttu-id="0da5a-114">値による構造体。</span><span class="sxs-lookup"><span data-stu-id="0da5a-114">Structure by value.</span></span>|<span data-ttu-id="0da5a-115">In パラメーターとして構造体を渡します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-115">Passes structures as In parameters.</span></span>|[<span data-ttu-id="0da5a-116">構造体のサンプル</span><span class="sxs-lookup"><span data-stu-id="0da5a-116">Structures sample</span></span>](#structures-sample)|
|<span data-ttu-id="0da5a-117">参照による構造体</span><span class="sxs-lookup"><span data-stu-id="0da5a-117">Structure by reference.</span></span>|<span data-ttu-id="0da5a-118">In/Out パラメーターとして構造体を渡します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-118">Passes structures as In/Out parameters.</span></span>|<span data-ttu-id="0da5a-119">[OSInfo のサンプル](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0da5a-119">[OSInfo sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))</span></span>|
|<span data-ttu-id="0da5a-120">入れ子になった構造体を含む構造体 (フラット化)。</span><span class="sxs-lookup"><span data-stu-id="0da5a-120">Structure with nested structures (flattened).</span></span>|<span data-ttu-id="0da5a-121">アンマネージ関数で入れ子になった構造体を含む構造体を表すクラスを渡します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-121">Passes a class that represents a structure with nested structures in the unmanaged function.</span></span> <span data-ttu-id="0da5a-122">マネージド プロトタイプで構造体は 1 つの大きな構造体にフラット化されます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-122">The structure is flattened to one big structure in the managed prototype.</span></span>|[<span data-ttu-id="0da5a-123">FindFile サンプル</span><span class="sxs-lookup"><span data-stu-id="0da5a-123">FindFile sample</span></span>](#findfile-sample)|
|<span data-ttu-id="0da5a-124">別の構造体へのポインターを持つ構造体。</span><span class="sxs-lookup"><span data-stu-id="0da5a-124">Structure with a pointer to another structure.</span></span>|<span data-ttu-id="0da5a-125">2 番目の構造体へのポインターをメンバーとして含む構造体を渡します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-125">Passes a structure that contains a pointer to a second structure as a member.</span></span>|[<span data-ttu-id="0da5a-126">構造体のサンプル</span><span class="sxs-lookup"><span data-stu-id="0da5a-126">Structures Sample</span></span>](#structures-sample)|
|<span data-ttu-id="0da5a-127">値による整数のある構造体の配列。</span><span class="sxs-lookup"><span data-stu-id="0da5a-127">Array of structures with integers by value.</span></span>|<span data-ttu-id="0da5a-128">In/Out パラメーターとして整数のみを含む構造体の配列を渡します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-128">Passes an array of structures that contain only integers as an In/Out parameter.</span></span> <span data-ttu-id="0da5a-129">配列のメンバーを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-129">Members of the array can be changed.</span></span>|[<span data-ttu-id="0da5a-130">配列のサンプル</span><span class="sxs-lookup"><span data-stu-id="0da5a-130">Arrays Sample</span></span>](marshaling-different-types-of-arrays.md)|
|<span data-ttu-id="0da5a-131">参照による整数と文字列のある構造体の配列。</span><span class="sxs-lookup"><span data-stu-id="0da5a-131">Array of structures with integers and strings by reference.</span></span>|<span data-ttu-id="0da5a-132">Out パラメーターとして整数と文字列を含む構造体の配列を渡します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-132">Passes an array of structures that contain integers and strings as an Out parameter.</span></span> <span data-ttu-id="0da5a-133">呼び出された関数は、配列のメモリを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-133">The called function allocates memory for the array.</span></span>|[<span data-ttu-id="0da5a-134">OutArrayOfStructs サンプル</span><span class="sxs-lookup"><span data-stu-id="0da5a-134">OutArrayOfStructs Sample</span></span>](#outarrayofstructs-sample)|
|<span data-ttu-id="0da5a-135">値型の共用体。</span><span class="sxs-lookup"><span data-stu-id="0da5a-135">Unions with value types.</span></span>|<span data-ttu-id="0da5a-136">値型 (整数および倍精度) の共用体を渡します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-136">Passes unions with value types (integer and double).</span></span>|[<span data-ttu-id="0da5a-137">共用体のサンプル</span><span class="sxs-lookup"><span data-stu-id="0da5a-137">Unions sample</span></span>](#unions-sample)|
|<span data-ttu-id="0da5a-138">混合型の共用体。</span><span class="sxs-lookup"><span data-stu-id="0da5a-138">Unions with mixed types.</span></span>|<span data-ttu-id="0da5a-139">混合型 (整数および文字列) の共用体を渡します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-139">Passes unions with mixed types (integer and string).</span></span>|[<span data-ttu-id="0da5a-140">共用体のサンプル</span><span class="sxs-lookup"><span data-stu-id="0da5a-140">Unions sample</span></span>](#unions-sample)|
|<span data-ttu-id="0da5a-141">構造体の null 値。</span><span class="sxs-lookup"><span data-stu-id="0da5a-141">Null values in structure.</span></span>|<span data-ttu-id="0da5a-142">値型への参照の代わりに null 参照 (Visual Basic では **Nothing**) を渡します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-142">Passes a null reference (**Nothing** in Visual Basic) instead of a reference to a value type.</span></span>|<span data-ttu-id="0da5a-143">[HandleRef サンプル](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="0da5a-143">[HandleRef sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))</span></span>|

## <a name="structures-sample"></a><span data-ttu-id="0da5a-144">構造体のサンプル</span><span class="sxs-lookup"><span data-stu-id="0da5a-144">Structures sample</span></span>

<span data-ttu-id="0da5a-145">このサンプルでは、2 番目の構造体を指す構造体を渡す方法、埋め込み構造体のある構造体を渡す方法、および埋め込み配列のある構造体を渡す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-145">This sample demonstrates how to pass a structure that points to a second structure, pass a structure with an embedded structure, and pass a structure with an embedded array.</span></span>  
  
<span data-ttu-id="0da5a-146">Structs のサンプルで使用するアンマネージ関数とその元の関数宣言を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-146">The Structs sample uses the following unmanaged functions, shown with their original function declaration:</span></span>

- <span data-ttu-id="0da5a-147">PinvokeLib.dll からエクスポートされる **TestStructInStruct**。</span><span class="sxs-lookup"><span data-stu-id="0da5a-147">**TestStructInStruct** exported from PinvokeLib.dll.</span></span>

    ```cpp
    int TestStructInStruct(MYPERSON2* pPerson2);
    ```

- <span data-ttu-id="0da5a-148">PinvokeLib.dll からエクスポートされる **TestStructInStruct3**。</span><span class="sxs-lookup"><span data-stu-id="0da5a-148">**TestStructInStruct3** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestStructInStruct3(MYPERSON3 person3);
    ```

- <span data-ttu-id="0da5a-149">PinvokeLib.dll からエクスポートされる **TestArrayInStruct**。</span><span class="sxs-lookup"><span data-stu-id="0da5a-149">**TestArrayInStruct** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestArrayInStruct(MYARRAYSTRUCT* pStruct);
    ```

<span data-ttu-id="0da5a-150">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) はカスタム アンマネージ ライブラリであり、上記の関数および 4 つの構造体 **MYPERSON**、**MYPERSON2**、**MYPERSON3**、および **MYARRAYSTRUCT** に関する実装を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-150">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and four structures: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, and **MYARRAYSTRUCT**.</span></span> <span data-ttu-id="0da5a-151">これらの構造体には次の要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-151">These structures contain the following elements:</span></span>

```cpp
typedef struct _MYPERSON
{
   char* first;
   char* last;
} MYPERSON, *LP_MYPERSON;

typedef struct _MYPERSON2
{
   MYPERSON* person;
   int age;
} MYPERSON2, *LP_MYPERSON2;

typedef struct _MYPERSON3
{
   MYPERSON person;
   int age;
} MYPERSON3;

typedef struct _MYARRAYSTRUCT
{
   bool flag;
   int vals[ 3 ];
} MYARRAYSTRUCT;
```

<span data-ttu-id="0da5a-152">マネージド `MyPerson`、`MyPerson2`、`MyPerson3`、および `MyArrayStruct` 構造体には、以下の特性があります。</span><span class="sxs-lookup"><span data-stu-id="0da5a-152">The managed `MyPerson`, `MyPerson2`, `MyPerson3`, and `MyArrayStruct` structures have the following characteristic:</span></span>

- <span data-ttu-id="0da5a-153">`MyPerson` には文字列メンバーだけが含まれます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-153">`MyPerson` contains only string members.</span></span> <span data-ttu-id="0da5a-154">[CharSet](specifying-a-character-set.md) フィールドは、アンマネージ関数に渡されるとき、文字列を ANSI 形式に設定します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-154">The [CharSet](specifying-a-character-set.md) field sets the strings to ANSI format when passed to the unmanaged function.</span></span>

- <span data-ttu-id="0da5a-155">`MyPerson2` には、`MyPerson` 構造体への **IntPtr** が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-155">`MyPerson2` contains an **IntPtr** to the `MyPerson` structure.</span></span> <span data-ttu-id="0da5a-156">コードが **unsafe** とマークされている場合を除いて、.NET Framework アプリケーションではポインターを使用しないため、**IntPtr** 型は元のポインターをアンマネージ構造体に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-156">The **IntPtr** type replaces the original pointer to the unmanaged structure because .NET Framework applications do not use pointers unless the code is marked **unsafe**.</span></span>

- <span data-ttu-id="0da5a-157">`MyPerson3` には `MyPerson` が埋め込み構造体として含まれます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-157">`MyPerson3` contains `MyPerson` as an embedded structure.</span></span> <span data-ttu-id="0da5a-158">別の構造体に埋め込まれた構造体は、埋め込み構造体の要素をメインの構造体に直接配置することでフラット化することができます。またはこのサンプルのように、埋め込み構造体のままにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-158">A structure embedded within another structure can be flattened by placing the elements of the embedded structure directly into the main structure, or it can be left as an embedded structure, as is done in this sample.</span></span>

- <span data-ttu-id="0da5a-159">`MyArrayStruct` には整数の配列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-159">`MyArrayStruct` contains an array of integers.</span></span> <span data-ttu-id="0da5a-160"><xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性は <xref:System.Runtime.InteropServices.UnmanagedType> 列挙値を **ByValArray** に設定します。これは配列内の要素の数を示すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-160">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration value to **ByValArray**, which is used to indicate the number of elements in the array.</span></span>

<span data-ttu-id="0da5a-161">このサンプル内のすべての構造体で、各メンバーが出現する順番でメモリ内に順次配列されることを保証するために、<xref:System.Runtime.InteropServices.StructLayoutAttribute> 属性が適用されています。</span><span class="sxs-lookup"><span data-stu-id="0da5a-161">For all structures in this sample, the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is applied to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>

<span data-ttu-id="0da5a-162">`NativeMethods` クラスには、`App` クラスによって呼び出される `TestStructInStruct`、`TestStructInStruct3`、および `TestArrayInStruct` メソッドのマネージド プロトタイプが含まれます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-162">The `NativeMethods` class contains managed prototypes for the `TestStructInStruct`, `TestStructInStruct3`, and `TestArrayInStruct` methods called by the `App` class.</span></span> <span data-ttu-id="0da5a-163">各プロトタイプは、1 つのパラメーターを以下のように宣言します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-163">Each prototype declares a single parameter, as follows:</span></span>

- <span data-ttu-id="0da5a-164">`TestStructInStruct` は型 `MyPerson2` への参照をそのパラメーターとして宣言します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-164">`TestStructInStruct` declares a reference to type `MyPerson2` as its parameter.</span></span>

- <span data-ttu-id="0da5a-165">`TestStructInStruct3` は型 `MyPerson3` をそのパラメーターとして宣言し、パラメーターを値によって渡します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-165">`TestStructInStruct3` declares type `MyPerson3` as its parameter and passes the parameter by value.</span></span>

- <span data-ttu-id="0da5a-166">`TestArrayInStruct` は型 `MyArrayStruct` への参照をそのパラメーターとして宣言します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-166">`TestArrayInStruct` declares a reference to type `MyArrayStruct` as its parameter.</span></span>

<span data-ttu-id="0da5a-167">メソッドへの引数としての構造体は、パラメーターに **ref** (Visual Basic では **ByRef**) キーワードが含まれない限り、値によって渡されます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-167">Structures as arguments to methods are passed by value unless the parameter contains the **ref** (**ByRef** in Visual Basic) keyword.</span></span> <span data-ttu-id="0da5a-168">たとえば、`TestStructInStruct` メソッドは型 `MyPerson2` のオブジェクトへの参照 (アドレスの値) をアンマネージ コードに渡します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-168">For example, the `TestStructInStruct` method passes a reference (the value of an address) to an object of type `MyPerson2` to unmanaged code.</span></span> <span data-ttu-id="0da5a-169">`MyPerson2` が指定する構造体を操作するために、サンプルは指定したサイズのバッファーを作成し、<xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> と <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> のメソッドを結合することでそのアドレスを返します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-169">To manipulate the structure that `MyPerson2` points to, the sample creates a buffer of a specified size and returns its address by combining the <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="0da5a-170">次に、サンプルはマネージド構造体の内容をアンマネージド バッファーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="0da5a-170">Next, the sample copies the content of the managed structure to the unmanaged buffer.</span></span> <span data-ttu-id="0da5a-171">最後に、サンプルは <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> メソッドを使用してアンマネージド バッファーからマネージド オブジェクトにデータをマーシャリングし、<xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> メソッドを使用してメモリのアンマネージド ブロックを解放します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-171">Finally, the sample uses the <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> method to marshal data from the unmanaged buffer to a managed object and the <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> method to free the unmanaged block of memory.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="0da5a-172">プロトタイプの宣言</span><span class="sxs-lookup"><span data-stu-id="0da5a-172">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#23](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
[!code-csharp[Conceptual.Interop.Marshaling#23](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
[!code-vb[Conceptual.Interop.Marshaling#23](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]

### <a name="calling-functions"></a><span data-ttu-id="0da5a-173">関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="0da5a-173">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#24](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
[!code-csharp[Conceptual.Interop.Marshaling#24](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
[!code-vb[Conceptual.Interop.Marshaling#24](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]

## <a name="findfile-sample"></a><span data-ttu-id="0da5a-174">FindFile サンプル</span><span class="sxs-lookup"><span data-stu-id="0da5a-174">FindFile sample</span></span>

<span data-ttu-id="0da5a-175">このサンプルでは、2 番目の埋め込み構造体を含む構造体をアンマネージ関数に渡す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-175">This sample demonstrates how to pass a structure that contains a second, embedded structure to an unmanaged function.</span></span> <span data-ttu-id="0da5a-176">また、<xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性を使用して構造体内に固定長配列を宣言する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-176">It also demonstrates how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to declare a fixed-length array within the structure.</span></span> <span data-ttu-id="0da5a-177">このサンプルでは、埋め込み構造体の要素が親の構造体に追加されます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-177">In this sample, the embedded structure elements are added to the parent structure.</span></span> <span data-ttu-id="0da5a-178">フラット化しない埋め込み構造体のサンプルについては、「[構造体のサンプル](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0da5a-178">For a sample of an embedded structure that is not flattened, see [Structures Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span></span>

<span data-ttu-id="0da5a-179">FindFile のサンプルで使用するアンマネージ関数とその元の関数宣言を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-179">The FindFile sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="0da5a-180">Kernel32.dll からエクスポートされる **FindFirstFile**。</span><span class="sxs-lookup"><span data-stu-id="0da5a-180">**FindFirstFile** exported from Kernel32.dll.</span></span>

    ```cpp
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);
    ```

<span data-ttu-id="0da5a-181">関数に渡された元の構造体には、次に示す要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0da5a-181">The original structure passed to the function contains the following elements:</span></span>

```cpp
typedef struct _WIN32_FIND_DATA
{
  DWORD    dwFileAttributes;
  FILETIME ftCreationTime;
  FILETIME ftLastAccessTime;
  FILETIME ftLastWriteTime;
  DWORD    nFileSizeHigh;
  DWORD    nFileSizeLow;
  DWORD    dwReserved0;
  DWORD    dwReserved1;
  TCHAR    cFileName[ MAX_PATH ];
  TCHAR    cAlternateFileName[ 14 ];
} WIN32_FIND_DATA, *PWIN32_FIND_DATA;
```

<span data-ttu-id="0da5a-182">このサンプルでは、`FindData` クラスに、元の構造体と埋め込み構造体の各要素に対応するデータ メンバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0da5a-182">In this sample, the `FindData` class contains a corresponding data member for each element of the original structure and the embedded structure.</span></span> <span data-ttu-id="0da5a-183">このクラスは、元の 2 つの文字バッファーを文字列に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-183">In place of two original character buffers, the class substitutes strings.</span></span> <span data-ttu-id="0da5a-184">**MarshalAsAttribute** は <xref:System.Runtime.InteropServices.UnmanagedType> 列挙を **ByValTStr** に設定します。これは、アンマネージ構造体に出現するインラインの固定長文字配列を識別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-184">**MarshalAsAttribute** sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged structures.</span></span>

<span data-ttu-id="0da5a-185">`NativeMethods` クラスには `FindFirstFile` メソッドのマネージド プロトタイプが含まれます。このメソッドは `FindData` クラスをパラメーターとして渡します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-185">The `NativeMethods` class contains a managed prototype of the `FindFirstFile` method, which passes the `FindData` class as a parameter.</span></span> <span data-ttu-id="0da5a-186">参照型のクラスは既定では In パラメーターとして渡されるため、パラメーターは <xref:System.Runtime.InteropServices.InAttribute> と <xref:System.Runtime.InteropServices.OutAttribute> の属性で宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0da5a-186">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="0da5a-187">プロトタイプの宣言</span><span class="sxs-lookup"><span data-stu-id="0da5a-187">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#17](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
[!code-csharp[Conceptual.Interop.Marshaling#17](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
[!code-vb[Conceptual.Interop.Marshaling#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]

### <a name="calling-functions"></a><span data-ttu-id="0da5a-188">関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="0da5a-188">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#18](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
[!code-csharp[Conceptual.Interop.Marshaling#18](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]

## <a name="unions-sample"></a><span data-ttu-id="0da5a-189">Unions サンプル</span><span class="sxs-lookup"><span data-stu-id="0da5a-189">Unions sample</span></span>

<span data-ttu-id="0da5a-190">このサンプルでは、値型のみを含む構造体、および値型と文字列を含む構造体を、共用体が予期されているアンマネージ関数のパラメーターとして渡す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-190">This sample demonstrates how to pass structures containing only value types, and structures containing a value type and a string as parameters to an unmanaged function expecting a union.</span></span> <span data-ttu-id="0da5a-191">共用体は、2 つ以上の変数が共有できるメモリ位置を表します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-191">A union represents a memory location that can be shared by two or more variables.</span></span>

<span data-ttu-id="0da5a-192">Unions のサンプルで使用するアンマネージ関数とその元の関数宣言を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-192">The Unions sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="0da5a-193">PinvokeLib.dll からエクスポートされる **TestUnion**。</span><span class="sxs-lookup"><span data-stu-id="0da5a-193">**TestUnion** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestUnion(MYUNION u, int type);
    ```

<span data-ttu-id="0da5a-194">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) はカスタム アンマネージ ライブラリであり、上記の関数および 2 つの共用体 **MYUNION** および **MYUNION2** に関する実装を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-194">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed function and two unions, **MYUNION** and **MYUNION2**.</span></span> <span data-ttu-id="0da5a-195">共用体には以下の要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-195">The unions contain the following elements:</span></span>

```cpp
union MYUNION
{
    int number;
    double d;
}

union MYUNION2
{
    int i;
    char str[128];
};
```

<span data-ttu-id="0da5a-196">マネージド コードでは、共用体は構造体として定義されます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-196">In managed code, unions are defined as structures.</span></span> <span data-ttu-id="0da5a-197">`MyUnion` 構造体には、メンバーとして整数と倍精度の 2 つの値型が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-197">The `MyUnion` structure contains two value types as its members: an integer and a double.</span></span> <span data-ttu-id="0da5a-198"><xref:System.Runtime.InteropServices.StructLayoutAttribute> 属性は、各データ メンバーの正確な位置を制御するために設定されます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-198">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to control the precise position of each data member.</span></span> <span data-ttu-id="0da5a-199"><xref:System.Runtime.InteropServices.FieldOffsetAttribute> 属性は、共用体のアンマネージ表現内に、フィールドの物理的な位置を指定します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-199">The <xref:System.Runtime.InteropServices.FieldOffsetAttribute> attribute provides the physical position of fields within the unmanaged representation of a union.</span></span> <span data-ttu-id="0da5a-200">両方のメンバーに同じオフセット値があるので、メンバーはメモリの同じ部分を定義できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0da5a-200">Notice that both members have the same offset values, so the members can define the same piece of memory.</span></span>

<span data-ttu-id="0da5a-201">`MyUnion2_1` と `MyUnion2_2` には、それぞれ値型 (整数) と文字列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0da5a-201">`MyUnion2_1` and `MyUnion2_2` contain a value type (integer) and a string, respectively.</span></span> <span data-ttu-id="0da5a-202">マネージド コードでは、値型と参照型が重複することは許可されません。</span><span class="sxs-lookup"><span data-stu-id="0da5a-202">In managed code, value types and reference types are not permitted to overlap.</span></span> <span data-ttu-id="0da5a-203">このサンプルでは、同じアンマネージ関数を呼び出すときに呼び出し元が両方の型を使用できるようにするため、メソッドのオーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-203">This sample uses method overloading to enable the caller to use both types when calling the same unmanaged function.</span></span> <span data-ttu-id="0da5a-204">`MyUnion2_1` のレイアウトは明示的で、正確なオフセット値を持っています。</span><span class="sxs-lookup"><span data-stu-id="0da5a-204">The layout of `MyUnion2_1` is explicit and has a precise offset value.</span></span> <span data-ttu-id="0da5a-205">これに対し、`MyUnion2_2` にはシーケンシャル レイアウトがあります。参照型では明示的なレイアウトが許可されていないためです。</span><span class="sxs-lookup"><span data-stu-id="0da5a-205">In contrast, `MyUnion2_2` has a sequential layout, because explicit layouts are not permitted with reference types.</span></span> <span data-ttu-id="0da5a-206"><xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性は <xref:System.Runtime.InteropServices.UnmanagedType> 列挙を **ByValTStr** に設定します。これは、共用体のアンマネージ表現に出現するインラインの固定長文字配列を識別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-206">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged representation of the union.</span></span>

<span data-ttu-id="0da5a-207">`NativeMethods` クラスには、`TestUnion` と `TestUnion2` メソッドのプロトタイプが含まれます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-207">The `NativeMethods` class contains the prototypes for the `TestUnion` and `TestUnion2` methods.</span></span> <span data-ttu-id="0da5a-208">`TestUnion2` は `MyUnion2_1` または `MyUnion2_2` をパラメーターとして宣言するためにオーバーロードされています。</span><span class="sxs-lookup"><span data-stu-id="0da5a-208">`TestUnion2` is overloaded to declare `MyUnion2_1` or `MyUnion2_2` as parameters.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="0da5a-209">プロトタイプの宣言</span><span class="sxs-lookup"><span data-stu-id="0da5a-209">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#28](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
[!code-csharp[Conceptual.Interop.Marshaling#28](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
[!code-vb[Conceptual.Interop.Marshaling#28](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]

### <a name="calling-functions"></a><span data-ttu-id="0da5a-210">関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="0da5a-210">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#29](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
[!code-csharp[Conceptual.Interop.Marshaling#29](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
[!code-vb[Conceptual.Interop.Marshaling#29](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]

## <a name="systime-sample"></a><span data-ttu-id="0da5a-211">SysTime サンプル</span><span class="sxs-lookup"><span data-stu-id="0da5a-211">SysTime sample</span></span>

<span data-ttu-id="0da5a-212">このサンプルでは、構造体へのポインターを要求する、クラスへのポインターをアンマネージ関数に渡す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-212">This sample demonstrates how to pass a pointer to a class to an unmanaged function that expects a pointer to a structure.</span></span>

<span data-ttu-id="0da5a-213">SysTime のサンプルで使用するアンマネージ関数とその元の関数宣言を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-213">The SysTime sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="0da5a-214">Kernel32.dll からエクスポートされる **GetSystemTime**。</span><span class="sxs-lookup"><span data-stu-id="0da5a-214">**GetSystemTime** exported from Kernel32.dll.</span></span>

    ```cpp
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);
    ```

<span data-ttu-id="0da5a-215">関数に渡された元の構造体には、次に示す要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0da5a-215">The original structure passed to the function contains the following elements:</span></span>

```cpp
typedef struct _SYSTEMTIME {
    WORD wYear;
    WORD wMonth;
    WORD wDayOfWeek;
    WORD wDay;
    WORD wHour;
    WORD wMinute;
    WORD wSecond;
    WORD wMilliseconds;
} SYSTEMTIME, *PSYSTEMTIME;
```

<span data-ttu-id="0da5a-216">このサンプルでは、`SystemTime` クラスの中には、クラス メンバーとして表される、元の構造体の要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-216">In this sample, the `SystemTime` class contains the elements of the original structure represented as class members.</span></span> <span data-ttu-id="0da5a-217">各メンバーが出現する順番でメモリ内に順次配列されることを保証するために、 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-217">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>

<span data-ttu-id="0da5a-218">`NativeMethods` クラスには `GetSystemTime` メソッドのマネージド プロトタイプが含まれます。このメソッドは既定では `SystemTime` クラスを In/Out パラメーターとして渡します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-218">The `NativeMethods` class contains a managed prototype of the `GetSystemTime` method, which passes the `SystemTime` class as an In/Out parameter by default.</span></span> <span data-ttu-id="0da5a-219">参照型のクラスは既定では In パラメーターとして渡されるため、パラメーターは <xref:System.Runtime.InteropServices.InAttribute> と <xref:System.Runtime.InteropServices.OutAttribute> の属性で宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0da5a-219">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span> <span data-ttu-id="0da5a-220">呼び出し元が結果を受け取るには、これらの[方向属性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))を明示的に適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0da5a-220">For the caller to receive the results, these [directional attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) must be applied explicitly.</span></span> <span data-ttu-id="0da5a-221">`App` クラスは、`SystemTime` クラスの新しいインスタンスを作成して、そのデータ フィールドにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="0da5a-221">The `App` class creates a new instance of the `SystemTime` class and accesses its data fields.</span></span>

### <a name="code-samples"></a><span data-ttu-id="0da5a-222">コード サンプル</span><span class="sxs-lookup"><span data-stu-id="0da5a-222">Code Samples</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#25](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
[!code-csharp[Conceptual.Interop.Marshaling#25](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
[!code-vb[Conceptual.Interop.Marshaling#25](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]

## <a name="outarrayofstructs-sample"></a><span data-ttu-id="0da5a-223">OutArrayOfStructs サンプル</span><span class="sxs-lookup"><span data-stu-id="0da5a-223">OutArrayOfStructs sample</span></span>

<span data-ttu-id="0da5a-224">このサンプルでは、整数および文字列をアンマネージ関数への Out パラメーターとして含む構造体の配列を渡す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-224">This sample shows how to pass an array of structures that contains integers and strings as Out parameters to an unmanaged function.</span></span>

<span data-ttu-id="0da5a-225">このサンプルでは、<xref:System.Runtime.InteropServices.Marshal> クラスを使用することにより、およびアンセーフ コードを使用することにより、ネイティブ関数を呼び出す方法を例示します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-225">This sample demonstrates how to call a native function by using the <xref:System.Runtime.InteropServices.Marshal> class and by using unsafe code.</span></span>

<span data-ttu-id="0da5a-226">このサンプルでは、[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) で定義されていて、ソース ファイルにも含まれている、ラッパー関数とプラットフォーム呼び出しを使用します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-226">This sample uses a wrapper functions and platform invokes defined in [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), also provided in the source files.</span></span> <span data-ttu-id="0da5a-227">これは `TestOutArrayOfStructs` 関数および `MYSTRSTRUCT2` 構造を使用します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-227">It uses the `TestOutArrayOfStructs` function and the `MYSTRSTRUCT2` structure.</span></span> <span data-ttu-id="0da5a-228">構造体には次の要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-228">The structure contains the following elements:</span></span>

```cpp
typedef struct _MYSTRSTRUCT2
{
   char* buffer;
   UINT size;
} MYSTRSTRUCT2;
```

<span data-ttu-id="0da5a-229">`MyStruct` クラスには ANSI 文字の文字列オブジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0da5a-229">The `MyStruct` class contains a string object of ANSI characters.</span></span> <span data-ttu-id="0da5a-230"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> フィールドは ANSI 形式を指定します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-230">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field specifies ANSI format.</span></span> <span data-ttu-id="0da5a-231">`MyUnsafeStruct` は、文字列の代わりに <xref:System.IntPtr> 型を含む構造体です。</span><span class="sxs-lookup"><span data-stu-id="0da5a-231">`MyUnsafeStruct`, is a structure containing an <xref:System.IntPtr> type instead of a string.</span></span>

<span data-ttu-id="0da5a-232">`NativeMethods` クラスには、オーバーロードされた `TestOutArrayOfStructs` プロトタイプ メソッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-232">The `NativeMethods` class contains the overloaded `TestOutArrayOfStructs` prototype method.</span></span> <span data-ttu-id="0da5a-233">メソッドでポインターをパラメーターとして宣言している場合、クラスには `unsafe` キーワードでマークを付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="0da5a-233">If a method declares a pointer as a parameter, the class should be marked with the `unsafe` keyword.</span></span> <span data-ttu-id="0da5a-234">Visual Basic ではアンセーフ コードを使用できないので、オーバーロードされたメソッド、unsafe 修飾子、および `MyUnsafeStruct` 構造体は不要です。</span><span class="sxs-lookup"><span data-stu-id="0da5a-234">Because Visual Basic cannot use unsafe code, the overloaded method, unsafe modifier, and the `MyUnsafeStruct` structure are unnecessary.</span></span>

<span data-ttu-id="0da5a-235">`App` クラスは、配列を渡すために必要なすべてのタスクを実行する、`UsingMarshaling` メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-235">The `App` class implements the `UsingMarshaling` method, which performs all the tasks necessary to pass the array.</span></span> <span data-ttu-id="0da5a-236">配列には、データが呼び出し先から呼び出し元に渡されることを示すため、`out` (Visual Basic では `ByRef`) キーワードでマークが付けられます。</span><span class="sxs-lookup"><span data-stu-id="0da5a-236">The array is marked with the `out` (`ByRef` in Visual Basic) keyword to indicate that data passes from callee to caller.</span></span> <span data-ttu-id="0da5a-237">実装は、以下の <xref:System.Runtime.InteropServices.Marshal> クラス メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-237">The implementation uses the following <xref:System.Runtime.InteropServices.Marshal> class methods:</span></span>

- <span data-ttu-id="0da5a-238"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> は、アンマネージド バッファーからマネージド オブジェクトにデータをマーシャリングします。</span><span class="sxs-lookup"><span data-stu-id="0da5a-238"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> to marshal data from the unmanaged buffer to a managed object.</span></span>

- <span data-ttu-id="0da5a-239"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> は、構造体で文字列用に予約されていたメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-239"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> to release the memory reserved for strings in the structure.</span></span>

- <span data-ttu-id="0da5a-240"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> は、配列用に予約されていたメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="0da5a-240"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> to release the memory reserved for the array.</span></span>

<span data-ttu-id="0da5a-241">前述のとおり、C# にはアンセーフ コードを使用できますが、Visual Basic には使用できません。</span><span class="sxs-lookup"><span data-stu-id="0da5a-241">As previously mentioned, C# allows unsafe code and Visual Basic does not.</span></span> <span data-ttu-id="0da5a-242">C# サンプルで、`UsingUnsafePointer` は、<xref:System.Runtime.InteropServices.Marshal> クラスの代わりにポインターを使用して `MyUnsafeStruct` 構造体を含む配列を戻す、代替のメソッドの実装です。</span><span class="sxs-lookup"><span data-stu-id="0da5a-242">In the C# sample, `UsingUnsafePointer` is an alternative method implementation that uses pointers instead of the <xref:System.Runtime.InteropServices.Marshal> class to pass back the array containing the `MyUnsafeStruct` structure.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="0da5a-243">プロトタイプの宣言</span><span class="sxs-lookup"><span data-stu-id="0da5a-243">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#20](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
[!code-csharp[Conceptual.Interop.Marshaling#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
[!code-vb[Conceptual.Interop.Marshaling#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]

### <a name="calling-functions"></a><span data-ttu-id="0da5a-244">関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="0da5a-244">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#21](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
[!code-csharp[Conceptual.Interop.Marshaling#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
[!code-vb[Conceptual.Interop.Marshaling#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]

## <a name="see-also"></a><span data-ttu-id="0da5a-245">参照</span><span class="sxs-lookup"><span data-stu-id="0da5a-245">See also</span></span>

- [<span data-ttu-id="0da5a-246">プラットフォーム呼び出しによるデータのマーシャリング</span><span class="sxs-lookup"><span data-stu-id="0da5a-246">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
- [<span data-ttu-id="0da5a-247">マーシャリング (文字列の)</span><span class="sxs-lookup"><span data-stu-id="0da5a-247">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="0da5a-248">さまざまな型の配列のマーシャリング</span><span class="sxs-lookup"><span data-stu-id="0da5a-248">Marshaling Different Types of Arrays</span></span>](marshaling-different-types-of-arrays.md)
