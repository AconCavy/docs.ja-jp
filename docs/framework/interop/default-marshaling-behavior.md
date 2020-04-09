---
title: 既定のマーシャリングの動作
ms.date: 06/26/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, default
- interoperation with unmanaged code, marshaling
- marshaling behavior
ms.assetid: c0a9bcdf-3df8-4db3-b1b6-abbdb2af809a
ms.openlocfilehash: f7df323dacfbee3361fe75d831f1e87df328b194
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989221"
---
# <a name="default-marshaling-behavior"></a><span data-ttu-id="62a74-102">既定のマーシャリングの動作</span><span class="sxs-lookup"><span data-stu-id="62a74-102">Default Marshaling Behavior</span></span>
<span data-ttu-id="62a74-103">相互運用マーシャリングは、メソッドのパラメーターに関連付けられたデータが、マネージド メモリとアンマネージド メモリの間で渡されるときに、どのように動作するかを指示する規則に従って機能します。</span><span class="sxs-lookup"><span data-stu-id="62a74-103">Interop marshaling operates on rules that dictate how data associated with method parameters behaves as it passes between managed and unmanaged memory.</span></span> <span data-ttu-id="62a74-104">これらの組み込みの規則は、データ型の変換などのマーシャリング動作、呼び出し先が渡されたデータを変更してその変更を呼び出し元にこ返すことが可能かどうか、およびどのような状況のときにマーシャラーがパフォーマンスの最適化を実現するかを制御します。</span><span class="sxs-lookup"><span data-stu-id="62a74-104">These built-in rules control such marshaling activities as data type transformations, whether a callee can change data passed to it and return those changes to the caller, and under which circumstances the marshaler provides performance optimizations.</span></span>  
  
 <span data-ttu-id="62a74-105">このセクションでは、相互運用マーシャリング サービスの既定の動作特性を示します。</span><span class="sxs-lookup"><span data-stu-id="62a74-105">This section identifies the default behavioral characteristics of the interop marshaling service.</span></span> <span data-ttu-id="62a74-106">ここでは、配列、ブール型、char 型、デリゲート、クラス、オブジェクト、文字列、および構造体のマーシャリングに関する詳細情報を示します。</span><span class="sxs-lookup"><span data-stu-id="62a74-106">It presents detailed information on marshaling arrays, Boolean types, char types, delegates, classes, objects, strings, and structures.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="62a74-107">ジェネリック型のマーシャリングはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="62a74-107">Marshaling of generic types is not supported.</span></span> <span data-ttu-id="62a74-108">詳しくは、「[ジェネリック型を使用する相互運用](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62a74-108">For more information see, [Interoperating Using Generic Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100)).</span></span>  
  
## <a name="memory-management-with-the-interop-marshaler"></a><span data-ttu-id="62a74-109">相互運用マーシャラーによるメモリ管理</span><span class="sxs-lookup"><span data-stu-id="62a74-109">Memory management with the interop marshaler</span></span>  
 <span data-ttu-id="62a74-110">相互運用マーシャラーは、アンマネージ コードによって割り当てられたメモリを常に解放しようとします。</span><span class="sxs-lookup"><span data-stu-id="62a74-110">The interop marshaler always attempts to free memory allocated by unmanaged code.</span></span> <span data-ttu-id="62a74-111">この動作は、COM メモリの管理規則に準拠していますが、ネイティブ C++ を制御する規則とは異なります。</span><span class="sxs-lookup"><span data-stu-id="62a74-111">This behavior complies with COM memory management rules, but differs from the rules that govern native C++.</span></span>  
  
 <span data-ttu-id="62a74-112">ネイティブ C++ の動作 (メモリを解放しない) を予期している場合、ポインターのメモリを自動的に解放するプラットフォーム呼び出しを使用すると、混乱が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="62a74-112">Confusion can arise if you anticipate native C++ behavior (no memory freeing) when using platform invoke, which automatically frees memory for pointers.</span></span> <span data-ttu-id="62a74-113">たとえば、C++ DLL からの次のアンマネージ メソッドを呼び出しても、メモリは自動的に解放されません。</span><span class="sxs-lookup"><span data-stu-id="62a74-113">For example, calling the following unmanaged method from a C++ DLL does not automatically free any memory.</span></span>  
  
### <a name="unmanaged-signature"></a><span data-ttu-id="62a74-114">アンマネージ シグネチャ</span><span class="sxs-lookup"><span data-stu-id="62a74-114">Unmanaged signature</span></span>  
  
```cpp  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 <span data-ttu-id="62a74-115">ただし、メソッドをプラットフォーム呼び出しのプロトタイプとして定義する場合は、各 **BSTR** 型を <xref:System.String> 型に置き換えて、`MethodOne` を呼び出します。共通言語ランタイムは、`b` の解放を 2 回試行します。</span><span class="sxs-lookup"><span data-stu-id="62a74-115">However, if you define the method as a platform invoke prototype, replace each **BSTR** type with a <xref:System.String> type, and call `MethodOne`, the common language runtime attempts to free `b` twice.</span></span> <span data-ttu-id="62a74-116">**String** 型ではなく <xref:System.IntPtr> 型を使用することにより、マーシャリングの動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="62a74-116">You can change the marshaling behavior by using <xref:System.IntPtr> types rather than **String** types.</span></span>  
  
 <span data-ttu-id="62a74-117">ランタイムは、常に **CoTaskMemFree** メソッドを使用してメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="62a74-117">The runtime always uses the **CoTaskMemFree** method to free memory.</span></span> <span data-ttu-id="62a74-118">使用しているメモリが **CoTaskMemAlloc** メソッドで割り当てられていない場合、**IntPtr** を使用し、適切なメソッドを使用して手動でメモリを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62a74-118">If the memory you are working with was not allocated with the **CoTaskMemAlloc** method, you must use an **IntPtr** and free the memory manually using the appropriate method.</span></span> <span data-ttu-id="62a74-119">同様に、カーネル メモリへのポインターを返す **GetCommandLine** 関数を Kernel32.dll から使用するときなど、メモリを解放してはいけない状況のときには、自動的なメモリの解放を防止できます。</span><span class="sxs-lookup"><span data-stu-id="62a74-119">Similarly, you can avoid automatic memory freeing in situations where memory should never be freed, such as when using the **GetCommandLine** function from Kernel32.dll, which returns a pointer to kernel memory.</span></span> <span data-ttu-id="62a74-120">手動でメモリを解放する方法について詳しくは、「[Buffers サンプル](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62a74-120">For details on manually freeing memory, see the [Buffers Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100)).</span></span>  
  
## <a name="default-marshaling-for-classes"></a><span data-ttu-id="62a74-121">クラスに対する既定のマーシャリング</span><span class="sxs-lookup"><span data-stu-id="62a74-121">Default marshaling for classes</span></span>  
 <span data-ttu-id="62a74-122">クラスは、COM 相互運用でのみマーシャリングすることができ、常にインターフェイスとしてマーシャリングされます。</span><span class="sxs-lookup"><span data-stu-id="62a74-122">Classes can be marshaled only by COM interop and are always marshaled as interfaces.</span></span> <span data-ttu-id="62a74-123">クラスをマーシャリングするために使用されるインターフェイスが、クラス インターフェイスと呼ばれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="62a74-123">In some cases the interface used to marshal the class is known as the class interface.</span></span> <span data-ttu-id="62a74-124">選択したインターフェイスでクラス インターフェイスをオーバーライドする方法については、[クラス インターフェイスの概要を](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface)参照してください。</span><span class="sxs-lookup"><span data-stu-id="62a74-124">For information about overriding the class interface with an interface of your choice, see [Introducing the class interface](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
### <a name="passing-classes-to-com"></a><span data-ttu-id="62a74-125">クラスを COM に渡す</span><span class="sxs-lookup"><span data-stu-id="62a74-125">Passing Classes to COM</span></span>  
 <span data-ttu-id="62a74-126">マネージド クラスが COM に渡されると、相互運用マーシャラーは自動的にクラスを COM プロキシでラップし、プロキシによって生成されたクラス インターフェイスを COM メソッド呼び出しに渡します。</span><span class="sxs-lookup"><span data-stu-id="62a74-126">When a managed class is passed to COM, the interop marshaler automatically wraps the class with a COM proxy and passes the class interface produced by the proxy to the COM method call.</span></span> <span data-ttu-id="62a74-127">その後、プロキシは、クラス インターフェイス上のすべての呼び出しを、マネージド オブジェクトにデリゲートして戻します。</span><span class="sxs-lookup"><span data-stu-id="62a74-127">The proxy then delegates all calls on the class interface back to the managed object.</span></span> <span data-ttu-id="62a74-128">プロキシはまた、クラスによって明示的に実装されていない他のインターフェイスも公開します。</span><span class="sxs-lookup"><span data-stu-id="62a74-128">The proxy also exposes other interfaces that are not explicitly implemented by the class.</span></span> <span data-ttu-id="62a74-129">プロキシは、クラスの代わりに、**IUnknown** や **IDispatch** などのインターフェイスを自動的に実装します。</span><span class="sxs-lookup"><span data-stu-id="62a74-129">The proxy automatically implements interfaces such as **IUnknown** and **IDispatch** on behalf of the class.</span></span>  
  
### <a name="passing-classes-to-net-code"></a><span data-ttu-id="62a74-130">クラスを .NET Code に渡す</span><span class="sxs-lookup"><span data-stu-id="62a74-130">Passing Classes to .NET Code</span></span>  
 <span data-ttu-id="62a74-131">コクラスは、通常、COM のメソッド引数として使用されません。</span><span class="sxs-lookup"><span data-stu-id="62a74-131">Coclasses are not typically used as method arguments in COM.</span></span> <span data-ttu-id="62a74-132">代わりに、通常は既定のインターフェイスがコクラスの代わりに渡されます。</span><span class="sxs-lookup"><span data-stu-id="62a74-132">Instead, a default interface is usually passed in place of the coclass.</span></span>  
  
 <span data-ttu-id="62a74-133">インターフェイスがマネージド コードに渡されると、相互運用マーシャラーは、インターフェイスを適切なラッパーでラップし、そのラッパーをマネージド メソッドに渡すことを担当します。</span><span class="sxs-lookup"><span data-stu-id="62a74-133">When an interface is passed into managed code, the interop marshaler is responsible for wrapping the interface with the proper wrapper and passing the wrapper to the managed method.</span></span> <span data-ttu-id="62a74-134">どのラッパーを使用するかは難しい判断となることがあります。</span><span class="sxs-lookup"><span data-stu-id="62a74-134">Determining which wrapper to use can be difficult.</span></span> <span data-ttu-id="62a74-135">COM オブジェクトのすべてのインスタンスは、オブジェクトが実装するインターフェイスの数に関係なく、1 つの一意のラッパーを持ちます。</span><span class="sxs-lookup"><span data-stu-id="62a74-135">Every instance of a COM object has a single, unique wrapper, no matter how many interfaces the object implements.</span></span> <span data-ttu-id="62a74-136">たとえば、5 つの異なるインターフェイスを実装する 1 つの COM オブジェクトには 1 つのラッパーだけがあります。</span><span class="sxs-lookup"><span data-stu-id="62a74-136">For example, a single COM object that implements five distinct interfaces has only one wrapper.</span></span> <span data-ttu-id="62a74-137">同一のラッパーが、5 つのすべてのインターフェイスを公開します。</span><span class="sxs-lookup"><span data-stu-id="62a74-137">The same wrapper exposes all five interfaces.</span></span> <span data-ttu-id="62a74-138">COM オブジェクトの 2 つのインスタンスが作成される場合、ラッパーの 2 つのインスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="62a74-138">If two instances of the COM object are created, then two instances of the wrapper are created.</span></span>  
  
 <span data-ttu-id="62a74-139">ラッパーがその有効期間中は同じ型を維持するように、相互運用マーシャラーは、オブジェクトによって公開されるインターフェイスが初めてマーシャラーを介して渡されるときに、正しいラッパーを識別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62a74-139">For the wrapper to maintain the same type throughout its lifetime, the interop marshaler must identify the correct wrapper the first time an interface exposed by the object is passed through the marshaler.</span></span> <span data-ttu-id="62a74-140">マーシャラーは、オブジェクトが実装するインターフェイスの 1 つに注目することにより、オブジェクトを識別します。</span><span class="sxs-lookup"><span data-stu-id="62a74-140">The marshaler identifies the object by looking at one of the interfaces the object implements.</span></span>  
  
 <span data-ttu-id="62a74-141">たとえば、マーシャラーは、マネージド コードに渡されたインターフェイスをラップするために、クラス ラッパーを使用する必要があると判別します。</span><span class="sxs-lookup"><span data-stu-id="62a74-141">For example, the marshaler determines that the class wrapper should be used to wrap the interface that was passed into managed code.</span></span> <span data-ttu-id="62a74-142">インターフェイスが初めてマーシャラーを介して渡されるとき、マーシャラーは、インターフェイスが既知のオブジェクトからのものかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="62a74-142">When the interface is first passed through the marshaler, the marshaler checks whether the interface is coming from a known object.</span></span> <span data-ttu-id="62a74-143">このチェックは、以下の 2 つの状況で発生します。</span><span class="sxs-lookup"><span data-stu-id="62a74-143">This check occurs in two situations:</span></span>  
  
- <span data-ttu-id="62a74-144">インターフェイスは、他の場所で COM に渡された別のマネージド オブジェクトによって実装されています。</span><span class="sxs-lookup"><span data-stu-id="62a74-144">An interface is being implemented by another managed object that was passed to COM elsewhere.</span></span> <span data-ttu-id="62a74-145">マーシャラーは、マネージド オブジェクトによって公開されるインターフェイスを簡単に特定し、インターフェイスと実装を提供するマネージド オブジェクトとで突き合わせすることができます。</span><span class="sxs-lookup"><span data-stu-id="62a74-145">The marshaler can readily identify interfaces exposed by managed objects and is able to match the interface with the managed object that provides the implementation.</span></span> <span data-ttu-id="62a74-146">その後、マネージド オブジェクトはメソッドに渡され、ラッパーは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="62a74-146">The managed object is then passed to the method and no wrapper is needed.</span></span>  
  
- <span data-ttu-id="62a74-147">既ににラップされているオブジェクトは、インターフェイスを実装しています。</span><span class="sxs-lookup"><span data-stu-id="62a74-147">An object that has already been wrapped is implementing the interface.</span></span> <span data-ttu-id="62a74-148">このような状況かどうかを確認するために、マーシャラーは **IUnknown** インターフェイスのためにオブジェクトのクエリを実行して、返されたインターフェイスを既にラップされているその他のオブジェクトのインターフェイスと比較します。</span><span class="sxs-lookup"><span data-stu-id="62a74-148">To determine whether this is the case, the marshaler queries the object for its **IUnknown** interface and compares the returned interface to the interfaces of other objects that are already wrapped.</span></span> <span data-ttu-id="62a74-149">インターフェイスが別のラッパーのものと同じ場合、それらのオブジェクトには同じ ID があり、既存のラッパーがメソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="62a74-149">If the interface is the same as that of another wrapper, the objects have the same identity and the existing wrapper is passed to the method.</span></span>  
  
 <span data-ttu-id="62a74-150">インターフェイスが既知のオブジェクトからのものではない場合、マーシャラーは以下を実行します。</span><span class="sxs-lookup"><span data-stu-id="62a74-150">If an interface is not from a known object, the marshaler does the following:</span></span>  
  
1. <span data-ttu-id="62a74-151">マーシャラーは **IProvideClassInfo2** インターフェイスのためにオブジェクトのクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="62a74-151">The marshaler queries the object for the **IProvideClassInfo2** interface.</span></span> <span data-ttu-id="62a74-152">提供された場合、マーシャラーは、**IProvideClassInfo2.GetGUID** から返される CLSID を使用して、インターフェイスを提供するコクラスを識別します。</span><span class="sxs-lookup"><span data-stu-id="62a74-152">If provided, the marshaler uses the CLSID returned from **IProvideClassInfo2.GetGUID** to identify the coclass providing the interface.</span></span> <span data-ttu-id="62a74-153">CLSID によって、マーシャラーは、アセンブリが事前に登録されている場合にレジストリからラッパーを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="62a74-153">With the CLSID, the marshaler can locate the wrapper from the registry if the assembly has previously been registered.</span></span>  
  
2. <span data-ttu-id="62a74-154">マーシャラーは **IProvideClassInfo** インターフェイスのためにインターフェイスのクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="62a74-154">The marshaler queries the interface for the **IProvideClassInfo** interface.</span></span> <span data-ttu-id="62a74-155">提供された場合、マーシャラーは、**IProvideClassInfo.GetClassinfo** から返される **ITypeInfo** を使用して、インターフェイスを公開するクラスの CLSID を決定します。</span><span class="sxs-lookup"><span data-stu-id="62a74-155">If provided, the marshaler uses the **ITypeInfo** returned from **IProvideClassInfo.GetClassinfo** to determine the CLSID of the class exposing the interface.</span></span> <span data-ttu-id="62a74-156">マーシャラーは、CLSID を使用して、ラッパーのメタデータを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="62a74-156">The marshaler can use the CLSID to locate the metadata for the wrapper.</span></span>  
  
3. <span data-ttu-id="62a74-157">マーシャラーは、まだクラスを識別できない場合には、**System.__ComObject** と呼ばれるジェネリック ラッパー クラスを使用してインターフェイスをラップします。</span><span class="sxs-lookup"><span data-stu-id="62a74-157">If the marshaler still cannot identify the class, it wraps the interface with a generic wrapper class called **System.__ComObject**.</span></span>  
  
## <a name="default-marshaling-for-delegates"></a><span data-ttu-id="62a74-158">デリゲートに対する既定のマーシャリング</span><span class="sxs-lookup"><span data-stu-id="62a74-158">Default marshaling for delegates</span></span>  
 <span data-ttu-id="62a74-159">マネージド デリゲートは、呼び出し元のメカニズムに基づいて、COM インターフェイスまたは関数ポインターとしてマーシャリングされます。</span><span class="sxs-lookup"><span data-stu-id="62a74-159">A managed delegate is marshaled as a COM interface or as a function pointer, based on the calling mechanism:</span></span>  
  
- <span data-ttu-id="62a74-160">プラットフォーム呼び出しの場合、デリゲートは、既定でアンマネージ関数ポインターとしてマーシャリングされます。</span><span class="sxs-lookup"><span data-stu-id="62a74-160">For platform invoke, a delegate is marshaled as an unmanaged function pointer by default.</span></span>  
  
- <span data-ttu-id="62a74-161">COM 相互運用の場合、デリゲートは、既定で **_Delegate** 型の COM インターフェイスとしてマーシャリングされます。</span><span class="sxs-lookup"><span data-stu-id="62a74-161">For COM interop, a delegate is marshaled as a COM interface of type **_Delegate** by default.</span></span> <span data-ttu-id="62a74-162">**_Delegate** インターフェイスは Mscorlib.tlb のタイプ ライブラリで定義され、デリゲートが参照するメソッドの呼び出しを可能にする <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> メソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="62a74-162">The **_Delegate** interface is defined in the Mscorlib.tlb type library and contains the <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> method, which enables you to call the method that the delegate references.</span></span>  
  
 <span data-ttu-id="62a74-163">次の表は、マネージド デリゲート データ型のマーシャリング オプションを示しています。</span><span class="sxs-lookup"><span data-stu-id="62a74-163">The following table shows the marshaling options for the managed delegate data type.</span></span> <span data-ttu-id="62a74-164"><xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性は、デリゲートをマーシャリングする <xref:System.Runtime.InteropServices.UnmanagedType> 列挙値を提供します。</span><span class="sxs-lookup"><span data-stu-id="62a74-164">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal delegates.</span></span>  
  
|<span data-ttu-id="62a74-165">列挙型</span><span class="sxs-lookup"><span data-stu-id="62a74-165">Enumeration type</span></span>|<span data-ttu-id="62a74-166">アンマネージ形式の説明</span><span class="sxs-lookup"><span data-stu-id="62a74-166">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="62a74-167">**UnmanagedType.FunctionPtr**</span><span class="sxs-lookup"><span data-stu-id="62a74-167">**UnmanagedType.FunctionPtr**</span></span>|<span data-ttu-id="62a74-168">アンマネージ関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="62a74-168">An unmanaged function pointer.</span></span>|  
|<span data-ttu-id="62a74-169">**UnmanagedType.Interface**</span><span class="sxs-lookup"><span data-stu-id="62a74-169">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="62a74-170">Mscorlib.tlb で定義されている、**_Delegate** 型のインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="62a74-170">An interface of type **_Delegate**, as defined in Mscorlib.tlb.</span></span>|  
  
 <span data-ttu-id="62a74-171">`DelegateTestInterface` のメソッドが COM タイプ ライブラリにエクスポートされる、次のコード例を検討してください。</span><span class="sxs-lookup"><span data-stu-id="62a74-171">Consider the following example code in which the methods of `DelegateTestInterface` are exported to a COM type library.</span></span> <span data-ttu-id="62a74-172">**ref** (または **ByRef**) キーワードでマークされたデリゲートだけが、In/Out パラメーターとして渡されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="62a74-172">Notice that only delegates marked with the **ref** (or **ByRef**) keyword are passed as In/Out parameters.</span></span>  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
public interface DelegateTest {  
void m1(Delegate d);  
void m2([MarshalAs(UnmanagedType.Interface)] Delegate d);
void m3([MarshalAs(UnmanagedType.Interface)] ref Delegate d);
void m4([MarshalAs(UnmanagedType.FunctionPtr)] Delegate d);
void m5([MarshalAs(UnmanagedType.FunctionPtr)] ref Delegate d);
}  
```  
  
### <a name="type-library-representation"></a><span data-ttu-id="62a74-173">タイプ ライブラリの表現</span><span class="sxs-lookup"><span data-stu-id="62a74-173">Type library representation</span></span>  
  
```cpp  
importlib("mscorlib.tlb");  
interface DelegateTest : IDispatch {  
[id(…)] HRESULT m1([in] _Delegate* d);  
[id(…)] HRESULT m2([in] _Delegate* d);  
[id(…)] HRESULT m3([in, out] _Delegate** d);  
[id()] HRESULT m4([in] int d);  
[id()] HRESULT m5([in, out] int *d);  
   };  
```  
  
 <span data-ttu-id="62a74-174">他のアンマネージ関数ポインターが逆参照できるのと同様に、関数ポインターは逆参照できます。</span><span class="sxs-lookup"><span data-stu-id="62a74-174">A function pointer can be dereferenced, just as any other unmanaged function pointer can be dereferenced.</span></span>  

<span data-ttu-id="62a74-175">この例では、2 つのデリゲートが <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType> としてマーシャリングされると、その結果は `int` および `int` へのポインターとなります。</span><span class="sxs-lookup"><span data-stu-id="62a74-175">In this example, when the two delegates are marshaled as <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>, the result is an `int` and a pointer to an `int`.</span></span> <span data-ttu-id="62a74-176">デリゲートの型はマーシャリング中であるため、`int` はここでは、メモリ内のデリゲートのアドレスである void (`void*`) を指すポインターを表します。</span><span class="sxs-lookup"><span data-stu-id="62a74-176">Because delegate types are being marshaled, `int` here represents a pointer to a void (`void*`), which is the address of the delegate in memory.</span></span> <span data-ttu-id="62a74-177">つまり、この結果は 32 ビット Windows システムに固有のものとなります。`int` がここでは関数ポインターのサイズを表すからです。</span><span class="sxs-lookup"><span data-stu-id="62a74-177">In other words, this result is specific to 32-bit Windows systems, since `int` here represents the size of the function pointer.</span></span>

> [!NOTE]
> <span data-ttu-id="62a74-178">アンマネージド コードで保持されている、マネージド デリゲートへの関数ポインターに対する参照は、共通言語ランタイムがマネージド オブジェクトでガベージ コレクションを実行することを防止しません。</span><span class="sxs-lookup"><span data-stu-id="62a74-178">A reference to the function pointer to a managed delegate held by unmanaged code does not prevent the common language runtime from performing garbage collection on the managed object.</span></span>  
  
 <span data-ttu-id="62a74-179">たとえば、`SetChangeHandler` メソッドに渡される `cb` オブジェクトへの参照は `Test` メソッドの有効期間を超えて `cb` を有効のまま保持しないので、次のコードは正しくありません。</span><span class="sxs-lookup"><span data-stu-id="62a74-179">For example, the following code is incorrect because the reference to the `cb` object, passed to the `SetChangeHandler` method, does not keep `cb` alive beyond the life of the `Test` method.</span></span> <span data-ttu-id="62a74-180">`cb` オブジェクトでガベージ コレクションを実行した後、`SetChangeHandler` に渡された関数ポインターは無効になります。</span><span class="sxs-lookup"><span data-stu-id="62a74-180">Once the `cb` object is garbage collected, the function pointer passed to `SetChangeHandler` is no longer valid.</span></span>  
  
```csharp  
public class ExternalAPI {  
   [DllImport("External.dll")]  
   public static extern void SetChangeHandler(  
      [MarshalAs(UnmanagedType.FunctionPtr)]ChangeDelegate d);  
}  
public delegate bool ChangeDelegate([MarshalAs(UnmanagedType.LPWStr) string S);  
public class CallBackClass {  
   public bool OnChange(string S){ return true;}  
}  
internal class DelegateTest {  
   public static void Test() {  
      CallBackClass cb = new CallBackClass();  
      // Caution: The following reference on the cb object does not keep the
      // object from being garbage collected after the Main method
      // executes.  
      ExternalAPI.SetChangeHandler(new ChangeDelegate(cb.OnChange));
   }  
}  
```  
  
 <span data-ttu-id="62a74-181">予期しないガベージ コレクションを補正するために、呼び出し元は、アンマネージ関数ポインターの使用中は `cb` オブジェクトが有効のまま保持されるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="62a74-181">To compensate for unexpected garbage collection, the caller must ensure that the `cb` object is kept alive as long as the unmanaged function pointer is in use.</span></span> <span data-ttu-id="62a74-182">必要に応じて、次の例に示すように、関数ポインターが不要になった際にアンマネージド コードがマネージド コードに通知するようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="62a74-182">Optionally, you can have the unmanaged code notify the managed code when the function pointer is no longer needed, as the following example shows.</span></span>  
  
```csharp  
internal class DelegateTest {  
   CallBackClass cb;  
   // Called before ever using the callback function.  
   public static void SetChangeHandler() {  
      cb = new CallBackClass();  
      ExternalAPI.SetChangeHandler(new ChangeDelegate(cb.OnChange));  
   }  
   // Called after using the callback function for the last time.  
   public static void RemoveChangeHandler() {  
      // The cb object can be collected now. The unmanaged code is
      // finished with the callback function.  
      cb = null;  
   }  
}  
```  
  
## <a name="default-marshaling-for-value-types"></a><span data-ttu-id="62a74-183">値型に対する既定のマーシャリング</span><span class="sxs-lookup"><span data-stu-id="62a74-183">Default marshaling for value types</span></span>  
 <span data-ttu-id="62a74-184">整数や浮動小数点数など、ほとんどの値型は、[blittable](blittable-and-non-blittable-types.md) であり、マーシャリングを必要としません。</span><span class="sxs-lookup"><span data-stu-id="62a74-184">Most value types, such as integers and floating-point numbers, are [blittable](blittable-and-non-blittable-types.md) and do not require marshaling.</span></span> <span data-ttu-id="62a74-185">その他の [non-blittable](blittable-and-non-blittable-types.md) 型は、マネージド メモリとアンマネージド メモリに類似しない表現があり、マーシャリングが必要です。</span><span class="sxs-lookup"><span data-stu-id="62a74-185">Other [non-blittable](blittable-and-non-blittable-types.md) types have dissimilar representations in managed and unmanaged memory and do require marshaling.</span></span> <span data-ttu-id="62a74-186">さらに他の型は、相互運用性の境界を越えて、明示的な書式設定が必要です。</span><span class="sxs-lookup"><span data-stu-id="62a74-186">Still other types require explicit formatting across the interoperation boundary.</span></span>  
  
 <span data-ttu-id="62a74-187">このセクションでは、次の書式設定された値に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="62a74-187">This section provides information on the following formatted value types:</span></span>  
  
- [<span data-ttu-id="62a74-188">プラットフォーム呼び出しで使用される値型</span><span class="sxs-lookup"><span data-stu-id="62a74-188">Value Types Used in Platform Invoke</span></span>](#value-types-used-in-platform-invoke)  
  
- [<span data-ttu-id="62a74-189">COM 相互運用で使用される値型</span><span class="sxs-lookup"><span data-stu-id="62a74-189">Value Types Used in COM Interop</span></span>](#value-types-used-in-com-interop)  
  
 <span data-ttu-id="62a74-190">書式指定された型について説明することに加えて、このトピックでは、マーシャリング動作が通常ではない[システム値型](#system-value-types)について示します。</span><span class="sxs-lookup"><span data-stu-id="62a74-190">In addition to describing formatted types, this topic identifies [System Value Types](#system-value-types) that have unusual marshaling behavior.</span></span>  
  
 <span data-ttu-id="62a74-191">書式設定された型は、メモリ内のメンバーのレイアウトを明示的に制御するための情報を含む複合型です。</span><span class="sxs-lookup"><span data-stu-id="62a74-191">A formatted type is a complex type that contains information that explicitly controls the layout of its members in memory.</span></span> <span data-ttu-id="62a74-192">メンバーのレイアウト情報は、<xref:System.Runtime.InteropServices.StructLayoutAttribute> 属性を使用して示すことができます。</span><span class="sxs-lookup"><span data-stu-id="62a74-192">The member layout information is provided using the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="62a74-193">レイアウトは、次のいずれかの <xref:System.Runtime.InteropServices.LayoutKind> 列挙値です。</span><span class="sxs-lookup"><span data-stu-id="62a74-193">The layout can be one of the following <xref:System.Runtime.InteropServices.LayoutKind> enumeration values:</span></span>  
  
- <span data-ttu-id="62a74-194">**自動**</span><span class="sxs-lookup"><span data-stu-id="62a74-194">**LayoutKind.Auto**</span></span>  
  
     <span data-ttu-id="62a74-195">共通言語ランタイムで、効率を上げるのために、型のメンバーを自由に再配置できることを示します。</span><span class="sxs-lookup"><span data-stu-id="62a74-195">Indicates that the common language runtime is free to reorder the members of the type for efficiency.</span></span> <span data-ttu-id="62a74-196">ただし、値型がアンマネージ コードに渡されると、メンバーのレイアウトは予測可能です。</span><span class="sxs-lookup"><span data-stu-id="62a74-196">However, when a value type is passed to unmanaged code, the layout of the members is predictable.</span></span> <span data-ttu-id="62a74-197">このような構造体を自動的にマーシャリングしようとすると、例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="62a74-197">An attempt to marshal such a structure automatically causes an exception.</span></span>  
  
- <span data-ttu-id="62a74-198">**LayoutKind.Sequential**</span><span class="sxs-lookup"><span data-stu-id="62a74-198">**LayoutKind.Sequential**</span></span>  
  
     <span data-ttu-id="62a74-199">型のメンバーは、マネージド型定義での順序と同じ順序で、アンマネージド メモリにレイアウトされることを示します。</span><span class="sxs-lookup"><span data-stu-id="62a74-199">Indicates that the members of the type are to be laid out in unmanaged memory in the same order in which they appear in the managed type definition.</span></span>  
  
- <span data-ttu-id="62a74-200">**LayoutKind.Explicit**</span><span class="sxs-lookup"><span data-stu-id="62a74-200">**LayoutKind.Explicit**</span></span>  
  
     <span data-ttu-id="62a74-201">メンバーが、各フィールドに指定された <xref:System.Runtime.InteropServices.FieldOffsetAttribute> に基づいてレイアウトされることを示します。</span><span class="sxs-lookup"><span data-stu-id="62a74-201">Indicates that the members are laid out according to the <xref:System.Runtime.InteropServices.FieldOffsetAttribute> supplied with each field.</span></span>  
  
### <a name="value-types-used-in-platform-invoke"></a><span data-ttu-id="62a74-202">プラットフォーム呼び出しで使用される値型</span><span class="sxs-lookup"><span data-stu-id="62a74-202">Value Types Used in Platform Invoke</span></span>  
 <span data-ttu-id="62a74-203">次の例では、`Point` と `Rect` 型が、**StructLayoutAttribute** を使用してメンバーのレイアウト情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="62a74-203">In the following example the `Point` and `Rect` types provide member layout information using the **StructLayoutAttribute**.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
<StructLayout(LayoutKind.Sequential)> Public Structure Point  
   Public x As Integer  
   Public y As Integer  
End Structure  
<StructLayout(LayoutKind.Explicit)> Public Structure Rect  
   <FieldOffset(0)> Public left As Integer  
   <FieldOffset(4)> Public top As Integer  
   <FieldOffset(8)> Public right As Integer  
   <FieldOffset(12)> Public bottom As Integer  
End Structure  
```  
  
```csharp  
using System.Runtime.InteropServices;  
[StructLayout(LayoutKind.Sequential)]  
public struct Point {  
   public int x;  
   public int y;  
}
  
[StructLayout(LayoutKind.Explicit)]  
public struct Rect {  
   [FieldOffset(0)] public int left;  
   [FieldOffset(4)] public int top;  
   [FieldOffset(8)] public int right;  
   [FieldOffset(12)] public int bottom;  
}  
```  
  
 <span data-ttu-id="62a74-204">アンマネージ コードにマーシャリングされるとき、これらの書式指定された型は C スタイルの構造体としてマーシャリングされます。</span><span class="sxs-lookup"><span data-stu-id="62a74-204">When marshaled to unmanaged code, these formatted types are marshaled as C-style structures.</span></span> <span data-ttu-id="62a74-205">これは、構造体の引数を持つアンマネージ API を呼び出すための、簡単な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="62a74-205">This provides an easy way of calling an unmanaged API that has structure arguments.</span></span> <span data-ttu-id="62a74-206">たとえば、次のようにして、`POINT` と `RECT` 構造体を Microsoft Windows API **PtInRect** 関数に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="62a74-206">For example, the `POINT` and `RECT` structures can be passed to the Microsoft Windows API **PtInRect** function as follows:</span></span>  
  
```cpp  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="62a74-207">次のプラットフォーム呼び出し定義を使用して、構造体を渡すことができます</span><span class="sxs-lookup"><span data-stu-id="62a74-207">You can pass structures using the following platform invoke definition:</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function PtInRect Lib "User32.dll" (
        ByRef r As Rect, p As Point) As Boolean
End Class
```
  
```csharp
internal static class NativeMethods
{
   [DllImport("User32.dll")]
   internal static extern bool PtInRect(ref Rect r, Point p);
}
```
  
 <span data-ttu-id="62a74-208">アンマネージ API では、`RECT` へのポインターが関数に渡されることが予期されているので、`Rect` 値型は参照によって渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="62a74-208">The `Rect` value type must be passed by reference because the unmanaged API is expecting a pointer to a `RECT` to be passed to the function.</span></span> <span data-ttu-id="62a74-209">アンマネージ API では、`POINT` がスタックで渡されることが予期されているので、`Point` 値型は値によって渡します。</span><span class="sxs-lookup"><span data-stu-id="62a74-209">The `Point` value type is passed by value because the unmanaged API expects the `POINT` to be passed on the stack.</span></span> <span data-ttu-id="62a74-210">この微妙な違いは、非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="62a74-210">This subtle difference is very important.</span></span> <span data-ttu-id="62a74-211">参照は、ポインターとしてアンマネージ コードに渡されます。</span><span class="sxs-lookup"><span data-stu-id="62a74-211">References are passed to unmanaged code as pointers.</span></span> <span data-ttu-id="62a74-212">値は、スタックでアンマネージ コードに渡されます。</span><span class="sxs-lookup"><span data-stu-id="62a74-212">Values are passed to unmanaged code on the stack.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="62a74-213">書式設定された型が構造体としてマーシャリングされると、型内のフィールドだけがアクセス可能となります。</span><span class="sxs-lookup"><span data-stu-id="62a74-213">When a formatted type is marshaled as a structure, only the fields within the type are accessible.</span></span> <span data-ttu-id="62a74-214">型にメソッド、プロパティ、またはイベントがある場合、それらにはアンマネージ コードからアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="62a74-214">If the type has methods, properties, or events, they are inaccessible from unmanaged code.</span></span>  
  
 <span data-ttu-id="62a74-215">クラスも、固定のメンバー レイアウトがあれば、C スタイルの構造体としてアンマネージ コードにマーシャリングできます。</span><span class="sxs-lookup"><span data-stu-id="62a74-215">Classes can also be marshaled to unmanaged code as C-style structures, provided they have fixed member layout.</span></span> <span data-ttu-id="62a74-216">クラスのメンバー レイアウト情報も、<xref:System.Runtime.InteropServices.StructLayoutAttribute> 属性で提供されます。</span><span class="sxs-lookup"><span data-stu-id="62a74-216">The member layout information for a class is also provided with the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="62a74-217">固定レイアウトの値型と固定レイアウトのクラスの主な違いは、それらがアンマネージ コードにマーシャリングされる方法です。</span><span class="sxs-lookup"><span data-stu-id="62a74-217">The main difference between value types with fixed layout and classes with fixed layout is the way in which they are marshaled to unmanaged code.</span></span> <span data-ttu-id="62a74-218">値型は (スタックで) 値によって渡されるので、呼び出し先が型のメンバーに変更を加えても、その変更は呼び出し元に示されません。</span><span class="sxs-lookup"><span data-stu-id="62a74-218">Value types are passed by value (on the stack) and consequently any changes made to the members of the type by the callee are not seen by the caller.</span></span> <span data-ttu-id="62a74-219">参照型は参照によって渡される (型への参照がスタックで渡される) ので、呼び出し先が型の blittable 型のメンバーに加えるすべての変更は呼び出し元に示されます。</span><span class="sxs-lookup"><span data-stu-id="62a74-219">Reference types are passed by reference (a reference to the type is passed on the stack); consequently, all changes made to blittable-type members of a type by the callee are seen by the caller.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="62a74-220">参照型に非 blittable 型のメンバーがある場合、変換は 2 回必要となります。1 回目は引数がアンマネージ サイトに渡されるときで、2 回目は呼び出しから返されるときです。</span><span class="sxs-lookup"><span data-stu-id="62a74-220">If a reference type has members of non-blittable types, conversion is required twice: the first time when an argument is passed to the unmanaged side and the second time on return from the call.</span></span> <span data-ttu-id="62a74-221">この追加のオーバーヘッドがあるために、呼び出し先による変更を呼び出し元が参照できるようにする場合は、In/Out パラメーターを引数に明示的に適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62a74-221">Due to this added overhead, In/Out parameters must be explicitly applied to an argument if the caller wants to see changes made by the callee.</span></span>  
  
 <span data-ttu-id="62a74-222">次の例では、`SystemTime` クラスにシーケンシャル メンバー レイアウトがあり、それを Windows API **GetSystemTime** 関数に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="62a74-222">In the following example, the `SystemTime` class has sequential member layout and can be passed to the Windows API **GetSystemTime** function.</span></span>  
  
```vb  
<StructLayout(LayoutKind.Sequential)> Public Class SystemTime  
   Public wYear As System.UInt16  
   Public wMonth As System.UInt16  
   Public wDayOfWeek As System.UInt16  
   Public wDay As System.UInt16  
   Public wHour As System.UInt16  
   Public wMinute As System.UInt16  
   Public wSecond As System.UInt16  
   Public wMilliseconds As System.UInt16  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
   public class SystemTime {  
   public ushort wYear;
   public ushort wMonth;  
   public ushort wDayOfWeek;
   public ushort wDay;
   public ushort wHour;
   public ushort wMinute;
   public ushort wSecond;
   public ushort wMilliseconds;
}  
```  
  
 <span data-ttu-id="62a74-223">**GetSystemTime** 関数は次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="62a74-223">The **GetSystemTime** function is defined as follows:</span></span>  
  
```cpp  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="62a74-224">**GetSystemTime** に対する同等のプラットフォーム呼び出し定義は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="62a74-224">The equivalent platform invoke definition for **GetSystemTime** is as follows:</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (
        ByVal sysTime As SystemTime)
End Class
```
  
```csharp
internal static class NativeMethods
{
   [DllImport("Kernel32.dll", CharSet = CharSet.Auto)]
   internal static extern void GetSystemTime(SystemTime st);
}
```
  
 <span data-ttu-id="62a74-225">`SystemTime` は値型ではなくクラスなので、`SystemTime` 引数は参照引数として型指定されていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="62a74-225">Notice that the `SystemTime` argument is not typed as a reference argument because `SystemTime` is a class, not a value type.</span></span> <span data-ttu-id="62a74-226">値型とは異なり、クラスは常に参照によって渡されます。</span><span class="sxs-lookup"><span data-stu-id="62a74-226">Unlike value types, classes are always passed by reference.</span></span>  
  
 <span data-ttu-id="62a74-227">次のコード例は、`SetXY` と呼ばれるメソッドを持つ、異なる `Point` クラスを示しています。</span><span class="sxs-lookup"><span data-stu-id="62a74-227">The following code example shows a different `Point` class that has a method called `SetXY`.</span></span> <span data-ttu-id="62a74-228">型にはシーケンシャル レイアウトがあるため、それをアンマネージ コードに渡して、構造体としてマーシャリングすることができます。</span><span class="sxs-lookup"><span data-stu-id="62a74-228">Because the type has sequential layout, it can be passed to unmanaged code and marshaled as a structure.</span></span> <span data-ttu-id="62a74-229">ただし、`SetXY` メンバーは、オブジェクトが参照によって渡される場合でも、アンマネージ コードから呼び出すことができません。</span><span class="sxs-lookup"><span data-stu-id="62a74-229">However, the `SetXY` member is not callable from unmanaged code, even though the object is passed by reference.</span></span>  
  
```vb  
<StructLayout(LayoutKind.Sequential)> Public Class Point  
   Private x, y As Integer  
   Public Sub SetXY(x As Integer, y As Integer)  
      Me.x = x  
      Me.y = y  
   End Sub  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public class Point {  
   int x, y;  
   public void SetXY(int x, int y){
      this.x = x;  
      this.y = y;  
   }  
}  
```  
  
### <a name="value-types-used-in-com-interop"></a><span data-ttu-id="62a74-230">COM 相互運用で使用される値型</span><span class="sxs-lookup"><span data-stu-id="62a74-230">Value Types Used in COM Interop</span></span>  
 <span data-ttu-id="62a74-231">書式指定された型は、COM 相互運用のメソッドの呼び出しに渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="62a74-231">Formatted types can also be passed to COM interop method calls.</span></span> <span data-ttu-id="62a74-232">実際には、タイプ ライブラリにエクスポートされると、値型は構造体に自動的に変換されます。</span><span class="sxs-lookup"><span data-stu-id="62a74-232">In fact, when exported to a type library, value types are automatically converted to structures.</span></span> <span data-ttu-id="62a74-233">次の例に示すように、`Point` 値型は `Point` という名前の型定義 (typedef) になります。</span><span class="sxs-lookup"><span data-stu-id="62a74-233">As the following example shows, the `Point` value type becomes a type definition (typedef) with the name `Point`.</span></span> <span data-ttu-id="62a74-234">タイプ ライブラリ内の他の場所にある `Point` 値型へのすべての参照は、`Point` typedef に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="62a74-234">All references to the `Point` value type elsewhere in the type library are replaced with the `Point` typedef.</span></span>  
  
 <span data-ttu-id="62a74-235">**タイプ ライブラリ表現**</span><span class="sxs-lookup"><span data-stu-id="62a74-235">**Type library representation**</span></span>  
  
```cpp  
typedef struct tagPoint {  
   int x;  
   int y;  
} Point;  
interface _Graphics {  
   …  
   HRESULT SetPoint ([in] Point p)  
   HRESULT SetPointRef ([in,out] Point *p)  
   HRESULT GetPoint ([out,retval] Point *p)  
}  
```  
  
 <span data-ttu-id="62a74-236">値と参照をプラットフォーム呼び出しにマーシャリングする際に使用されるものと同じ規則が、COM インターフェイスを介してマーシャリングする際にも使用されます。</span><span class="sxs-lookup"><span data-stu-id="62a74-236">The same rules used to marshal values and references to platform invoke calls are used when marshaling through COM interfaces.</span></span> <span data-ttu-id="62a74-237">たとえば、`Point` 値型のインスタンスが .NET Framework から COM に渡されるとき、`Point` は値によって渡されます。</span><span class="sxs-lookup"><span data-stu-id="62a74-237">For example, when an instance of the `Point` value type is passed from the .NET Framework to COM, the `Point` is passed by value.</span></span> <span data-ttu-id="62a74-238">`Point` 値型が参照によって渡される場合、`Point` へのポインターはスタックで渡されます。</span><span class="sxs-lookup"><span data-stu-id="62a74-238">If the `Point` value type is passed by reference, a pointer to a `Point` is passed on the stack.</span></span> <span data-ttu-id="62a74-239">相互運用マーシャラーは、どちらの方向でも、より高いレベルの間接参照 (\*\*Point \*\* \*\*) はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="62a74-239">The interop marshaler does not support higher levels of indirection (**Point** \*\*) in either direction.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="62a74-240"><xref:System.Runtime.InteropServices.LayoutKind> 列挙値が **Explicit** に設定された構造体は、エクスポートされたタイプ ライブラリが明示的なレイアウトを表現できないので、COM 相互運用で使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="62a74-240">Structures having the <xref:System.Runtime.InteropServices.LayoutKind> enumeration value set to **Explicit** cannot be used in COM interop because the exported type library cannot express an explicit layout.</span></span>  
  
### <a name="system-value-types"></a><span data-ttu-id="62a74-241">システムの値型</span><span class="sxs-lookup"><span data-stu-id="62a74-241">System Value Types</span></span>  
 <span data-ttu-id="62a74-242"><xref:System> 名前空間には、ランタイムのプリミティブ型のボックス化された形式を表す、いくつかの値型があります。</span><span class="sxs-lookup"><span data-stu-id="62a74-242">The <xref:System> namespace has several value types that represent the boxed form of the runtime primitive types.</span></span> <span data-ttu-id="62a74-243">たとえば、値型 <xref:System.Int32?displayProperty=nameWithType> 構造体は、**ELEMENT_TYPE_I4** のボックス化された形式を表します。</span><span class="sxs-lookup"><span data-stu-id="62a74-243">For example, the value type <xref:System.Int32?displayProperty=nameWithType> structure represents the boxed form of **ELEMENT_TYPE_I4**.</span></span> <span data-ttu-id="62a74-244">これらの型は、書式設定された他の型のように構造体としてマーシャリングするのではなく、それらがボックス化するプリミティブ型と同じ方法でマーシャリングします。</span><span class="sxs-lookup"><span data-stu-id="62a74-244">Instead of marshaling these types as structures, as other formatted types are, you marshal them in the same way as the primitive types they box.</span></span> <span data-ttu-id="62a74-245">そのため、**System.Int32** は、**long** 型の 1 つのメンバーを含む構造体としてではなく、**ELEMENT_TYPE_I4** としてマーシャリングされます。</span><span class="sxs-lookup"><span data-stu-id="62a74-245">**System.Int32** is therefore marshaled as **ELEMENT_TYPE_I4** instead of as a structure containing a single member of type **long**.</span></span> <span data-ttu-id="62a74-246">次の表には、プリミティブ型のボックス化された表現である、**System** 名前空間にある値型の一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="62a74-246">The following table contains a list of the value types in the **System** namespace that are boxed representations of primitive types.</span></span>  
  
|<span data-ttu-id="62a74-247">システムの値型</span><span class="sxs-lookup"><span data-stu-id="62a74-247">System value type</span></span>|<span data-ttu-id="62a74-248">要素型</span><span class="sxs-lookup"><span data-stu-id="62a74-248">Element type</span></span>|  
|-----------------------|------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="62a74-249">**ELEMENT_TYPE_BOOLEAN**</span><span class="sxs-lookup"><span data-stu-id="62a74-249">**ELEMENT_TYPE_BOOLEAN**</span></span>|  
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="62a74-250">**ELEMENT_TYPE_I1**</span><span class="sxs-lookup"><span data-stu-id="62a74-250">**ELEMENT_TYPE_I1**</span></span>|  
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="62a74-251">**ELEMENT_TYPE_UI1**</span><span class="sxs-lookup"><span data-stu-id="62a74-251">**ELEMENT_TYPE_UI1**</span></span>|  
|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="62a74-252">**ELEMENT_TYPE_CHAR**</span><span class="sxs-lookup"><span data-stu-id="62a74-252">**ELEMENT_TYPE_CHAR**</span></span>|  
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="62a74-253">**ELEMENT_TYPE_I2**</span><span class="sxs-lookup"><span data-stu-id="62a74-253">**ELEMENT_TYPE_I2**</span></span>|  
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="62a74-254">**ELEMENT_TYPE_U2**</span><span class="sxs-lookup"><span data-stu-id="62a74-254">**ELEMENT_TYPE_U2**</span></span>|  
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="62a74-255">**ELEMENT_TYPE_I4**</span><span class="sxs-lookup"><span data-stu-id="62a74-255">**ELEMENT_TYPE_I4**</span></span>|  
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="62a74-256">**ELEMENT_TYPE_U4**</span><span class="sxs-lookup"><span data-stu-id="62a74-256">**ELEMENT_TYPE_U4**</span></span>|  
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="62a74-257">**ELEMENT_TYPE_I8**</span><span class="sxs-lookup"><span data-stu-id="62a74-257">**ELEMENT_TYPE_I8**</span></span>|  
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="62a74-258">**ELEMENT_TYPE_U8**</span><span class="sxs-lookup"><span data-stu-id="62a74-258">**ELEMENT_TYPE_U8**</span></span>|  
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="62a74-259">**ELEMENT_TYPE_R4**</span><span class="sxs-lookup"><span data-stu-id="62a74-259">**ELEMENT_TYPE_R4**</span></span>|  
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="62a74-260">**ELEMENT_TYPE_R8**</span><span class="sxs-lookup"><span data-stu-id="62a74-260">**ELEMENT_TYPE_R8**</span></span>|  
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="62a74-261">**ELEMENT_TYPE_STRING**</span><span class="sxs-lookup"><span data-stu-id="62a74-261">**ELEMENT_TYPE_STRING**</span></span>|  
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="62a74-262">**ELEMENT_TYPE_I**</span><span class="sxs-lookup"><span data-stu-id="62a74-262">**ELEMENT_TYPE_I**</span></span>|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="62a74-263">**ELEMENT_TYPE_U**</span><span class="sxs-lookup"><span data-stu-id="62a74-263">**ELEMENT_TYPE_U**</span></span>|  
  
 <span data-ttu-id="62a74-264">**System** 名前空間にある他の値型は、処理が異なります。</span><span class="sxs-lookup"><span data-stu-id="62a74-264">Some other value types in the **System** namespace are handled differently.</span></span> <span data-ttu-id="62a74-265">アンマネージ コードではこれらの型の形式が既に確立されているため、マーシャラーには、それらをマーシャリングするための特別な規則があります。</span><span class="sxs-lookup"><span data-stu-id="62a74-265">Because the unmanaged code already has well-established formats for these types, the marshaler has special rules for marshaling them.</span></span> <span data-ttu-id="62a74-266">次の表では、**System** 名前空間にある特殊な値型、およびそれらがマーシャリングされるアンマネージ型を一覧で示します。</span><span class="sxs-lookup"><span data-stu-id="62a74-266">The following table lists the special value types in the **System** namespace, as well as the unmanaged type they are marshaled to.</span></span>  
  
|<span data-ttu-id="62a74-267">システムの値型</span><span class="sxs-lookup"><span data-stu-id="62a74-267">System value type</span></span>|<span data-ttu-id="62a74-268">IDL 型</span><span class="sxs-lookup"><span data-stu-id="62a74-268">IDL type</span></span>|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="62a74-269">**日付**</span><span class="sxs-lookup"><span data-stu-id="62a74-269">**DATE**</span></span>|  
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="62a74-270">**10 進**</span><span class="sxs-lookup"><span data-stu-id="62a74-270">**DECIMAL**</span></span>|  
|<xref:System.Guid?displayProperty=nameWithType>|<span data-ttu-id="62a74-271">**Guid**</span><span class="sxs-lookup"><span data-stu-id="62a74-271">**GUID**</span></span>|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|<span data-ttu-id="62a74-272">**OLE_COLOR**</span><span class="sxs-lookup"><span data-stu-id="62a74-272">**OLE_COLOR**</span></span>|  
  
 <span data-ttu-id="62a74-273">次のコードでは、Stdole2 タイプ ライブラリにあるアンマネージ型の **DATE**、**GUID**、**DECIMAL**、および **OLE_COLOR** の定義を示します。</span><span class="sxs-lookup"><span data-stu-id="62a74-273">The following code shows the definition of the unmanaged types **DATE**, **GUID**, **DECIMAL**, and **OLE_COLOR** in the Stdole2 type library.</span></span>  
  
#### <a name="type-library-representation"></a><span data-ttu-id="62a74-274">タイプ ライブラリの表現</span><span class="sxs-lookup"><span data-stu-id="62a74-274">Type library representation</span></span>  
  
```cpp  
typedef double DATE;  
typedef DWORD OLE_COLOR;  
  
typedef struct tagDEC {  
    USHORT    wReserved;  
    BYTE      scale;  
    BYTE      sign;  
    ULONG     Hi32;  
    ULONGLONG Lo64;  
} DECIMAL;  
  
typedef struct tagGUID {  
    DWORD Data1;  
    WORD  Data2;  
    WORD  Data3;  
    BYTE  Data4[ 8 ];  
} GUID;  
```  
  
 <span data-ttu-id="62a74-275">次のコードでは、マネージド `IValueTypes` インターフェイスでの対応する定義を示します。</span><span class="sxs-lookup"><span data-stu-id="62a74-275">The following code shows the corresponding definitions in the managed `IValueTypes` interface.</span></span>  
  
```vb  
Public Interface IValueTypes  
   Sub M1(d As System.DateTime)  
   Sub M2(d As System.Guid)  
   Sub M3(d As System.Decimal)  
   Sub M4(d As System.Drawing.Color)  
End Interface  
```  
  
```csharp  
public interface IValueTypes {  
   void M1(System.DateTime d);  
   void M2(System.Guid d);  
   void M3(System.Decimal d);  
   void M4(System.Drawing.Color d);  
}  
```  
  
#### <a name="type-library-representation"></a><span data-ttu-id="62a74-276">タイプ ライブラリの表現</span><span class="sxs-lookup"><span data-stu-id="62a74-276">Type library representation</span></span>  
  
```cpp  
[…]  
interface IValueTypes : IDispatch {  
   HRESULT M1([in] DATE d);  
   HRESULT M2([in] GUID d);  
   HRESULT M3([in] DECIMAL d);  
   HRESULT M4([in] OLE_COLOR d);  
};  
```  
  
## <a name="see-also"></a><span data-ttu-id="62a74-277">関連項目</span><span class="sxs-lookup"><span data-stu-id="62a74-277">See also</span></span>

- [<span data-ttu-id="62a74-278">Blittable 型と非 Blittable 型</span><span class="sxs-lookup"><span data-stu-id="62a74-278">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- [<span data-ttu-id="62a74-279">コピーと固定</span><span class="sxs-lookup"><span data-stu-id="62a74-279">Copying and Pinning</span></span>](copying-and-pinning.md)
- [<span data-ttu-id="62a74-280">配列に対する既定のマーシャリング</span><span class="sxs-lookup"><span data-stu-id="62a74-280">Default Marshaling for Arrays</span></span>](default-marshaling-for-arrays.md)
- [<span data-ttu-id="62a74-281">オブジェクトに対する既定のマーシャリング</span><span class="sxs-lookup"><span data-stu-id="62a74-281">Default Marshaling for Objects</span></span>](default-marshaling-for-objects.md)
- [<span data-ttu-id="62a74-282">文字列に対する既定のマーシャリング</span><span class="sxs-lookup"><span data-stu-id="62a74-282">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
