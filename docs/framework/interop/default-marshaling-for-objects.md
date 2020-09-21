---
title: オブジェクトに対する既定のマーシャリング
description: オブジェクトに対する既定のマーシャリングについて説明します。 マーシャリング オプションを確認します。 オブジェクトをインターフェイスまたはバリアントに、バリアントをオブジェクトに、および ByRef バリアントをマーシャリングします。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- objects, interop marshaling
- interop marshaling, objects
ms.assetid: c2ef0284-b061-4e12-b6d3-6a502b9cc558
ms.openlocfilehash: 3e07ceef62d97db4206f530aa0859b101fe41a11
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555095"
---
# <a name="default-marshaling-for-objects"></a><span data-ttu-id="c7ede-105">オブジェクトに対する既定のマーシャリング</span><span class="sxs-lookup"><span data-stu-id="c7ede-105">Default Marshaling for Objects</span></span>

<span data-ttu-id="c7ede-106"><xref:System.Object?displayProperty=nameWithType> として型指定されているパラメーターおよびフィールドを、次のいずれかの型としてアンマネージ コードに公開できます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-106">Parameters and fields typed as <xref:System.Object?displayProperty=nameWithType> can be exposed to unmanaged code as one of the following types:</span></span>

- <span data-ttu-id="c7ede-107">オブジェクトがパラメーターの場合にはバリアント。</span><span class="sxs-lookup"><span data-stu-id="c7ede-107">A variant when the object is a parameter.</span></span>

- <span data-ttu-id="c7ede-108">オブジェクトが構造体フィールドの場合にはインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="c7ede-108">An interface when the object is a structure field.</span></span>

<span data-ttu-id="c7ede-109">オブジェクト型のマーシャリングは COM 相互運用機能のみでサポートされます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-109">Only COM interop supports marshaling for object types.</span></span> <span data-ttu-id="c7ede-110">既定の動作では、オブジェクトは COM バリアントにマーシャリングされます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-110">The default behavior is to marshal objects to COM variants.</span></span> <span data-ttu-id="c7ede-111">これらの規則は **Object** 型のみに適用され、**Object** クラスから派生した、厳密に型指定されたオブジェクトには適用されません。</span><span class="sxs-lookup"><span data-stu-id="c7ede-111">These rules apply only to the type **Object** and do not apply to strongly typed objects that derive from the **Object** class.</span></span>

## <a name="marshaling-options"></a><span data-ttu-id="c7ede-112">マーシャリング オプション</span><span class="sxs-lookup"><span data-stu-id="c7ede-112">Marshaling Options</span></span>

<span data-ttu-id="c7ede-113">**Object** データ型のマーシャリング オプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="c7ede-113">The following table shows the marshaling options for the **Object** data type.</span></span> <span data-ttu-id="c7ede-114"><xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性は、オブジェクトをマーシャリングするための <xref:System.Runtime.InteropServices.UnmanagedType> 列挙値をいくつか提供します。</span><span class="sxs-lookup"><span data-stu-id="c7ede-114">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal objects.</span></span>

|<span data-ttu-id="c7ede-115">列挙型</span><span class="sxs-lookup"><span data-stu-id="c7ede-115">Enumeration type</span></span>|<span data-ttu-id="c7ede-116">アンマネージ形式の説明</span><span class="sxs-lookup"><span data-stu-id="c7ede-116">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|<span data-ttu-id="c7ede-117">**UnmanagedType.Struct**</span><span class="sxs-lookup"><span data-stu-id="c7ede-117">**UnmanagedType.Struct**</span></span><br /><br /> <span data-ttu-id="c7ede-118">(パラメーターの既定値)</span><span class="sxs-lookup"><span data-stu-id="c7ede-118">(default for parameters)</span></span>|<span data-ttu-id="c7ede-119">COM スタイルのバリアント。</span><span class="sxs-lookup"><span data-stu-id="c7ede-119">A COM-style variant.</span></span>|
|<span data-ttu-id="c7ede-120">**UnmanagedType.Interface**</span><span class="sxs-lookup"><span data-stu-id="c7ede-120">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="c7ede-121">可能な場合は **IDispatch** インターフェイス。それ以外の場合は **IUnknown** インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="c7ede-121">An **IDispatch** interface, if possible; otherwise, an **IUnknown** interface.</span></span>|
|<span data-ttu-id="c7ede-122">**UnmanagedType.IUnknown**</span><span class="sxs-lookup"><span data-stu-id="c7ede-122">**UnmanagedType.IUnknown**</span></span><br /><br /> <span data-ttu-id="c7ede-123">(フィールドの既定値)</span><span class="sxs-lookup"><span data-stu-id="c7ede-123">(default for fields)</span></span>|<span data-ttu-id="c7ede-124">**IUnknown** インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="c7ede-124">An **IUnknown** interface.</span></span>|
|<span data-ttu-id="c7ede-125">**UnmanagedType.IDispatch**</span><span class="sxs-lookup"><span data-stu-id="c7ede-125">**UnmanagedType.IDispatch**</span></span>|<span data-ttu-id="c7ede-126">**IDispatch** インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="c7ede-126">An **IDispatch** interface.</span></span>|

<span data-ttu-id="c7ede-127">次の例は、`MarshalObject` のマネージド インターフェイス定義を示しています。</span><span class="sxs-lookup"><span data-stu-id="c7ede-127">The following example shows the managed interface definition for `MarshalObject`.</span></span>

```vb
Interface MarshalObject
   Sub SetVariant(o As Object)
   Sub SetVariantRef(ByRef o As Object)
   Function GetVariant() As Object

   Sub SetIDispatch( <MarshalAs(UnmanagedType.IDispatch)> o As Object)
   Sub SetIDispatchRef(ByRef <MarshalAs(UnmanagedType.IDispatch)> o _
      As Object)
   Function GetIDispatch() As <MarshalAs(UnmanagedType.IDispatch)> Object
   Sub SetIUnknown( <MarshalAs(UnmanagedType.IUnknown)> o As Object)
   Sub SetIUnknownRef(ByRef <MarshalAs(UnmanagedType.IUnknown)> o _
      As Object)
   Function GetIUnknown() As <MarshalAs(UnmanagedType.IUnknown)> Object
End Interface
```

```csharp
interface MarshalObject {
   void SetVariant(Object o);
   void SetVariantRef(ref Object o);
   Object GetVariant();

   void SetIDispatch ([MarshalAs(UnmanagedType.IDispatch)]Object o);
   void SetIDispatchRef([MarshalAs(UnmanagedType.IDispatch)]ref Object o);
   [MarshalAs(UnmanagedType.IDispatch)] Object GetIDispatch();
   void SetIUnknown ([MarshalAs(UnmanagedType.IUnknown)]Object o);
   void SetIUnknownRef([MarshalAs(UnmanagedType.IUnknown)]ref Object o);
   [MarshalAs(UnmanagedType.IUnknown)] Object GetIUnknown();
}
```

<span data-ttu-id="c7ede-128">次のコードでは、`MarshalObject` インターフェイスをタイプ ライブラリにエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="c7ede-128">The following code exports the `MarshalObject` interface to a type library.</span></span>

```cpp
interface MarshalObject {
   HRESULT SetVariant([in] VARIANT o);
   HRESULT SetVariantRef([in,out] VARIANT *o);
   HRESULT GetVariant([out,retval] VARIANT *o)
   HRESULT SetIDispatch([in] IDispatch *o);
   HRESULT SetIDispatchRef([in,out] IDispatch **o);
   HRESULT GetIDispatch([out,retval] IDispatch **o)
   HRESULT SetIUnknown([in] IUnknown *o);
   HRESULT SetIUnknownRef([in,out] IUnknown **o);
   HRESULT GetIUnknown([out,retval] IUnknown **o)
}
```

> [!NOTE]
> <span data-ttu-id="c7ede-129">相互運用マーシャラーは、バリアント内に割り当てられたオブジェクトがある場合は、呼び出しの後で自動的にそのオブジェクトを解放します。</span><span class="sxs-lookup"><span data-stu-id="c7ede-129">The interop marshaler automatically frees any allocated object inside the variant after the call.</span></span>

<span data-ttu-id="c7ede-130">次の例は、フォーマットされた値型を示しています。</span><span class="sxs-lookup"><span data-stu-id="c7ede-130">The following example shows a formatted value type.</span></span>

```vb
Public Structure ObjectHolder
   Dim o1 As Object
   <MarshalAs(UnmanagedType.IDispatch)> Public o2 As Object
End Structure
```

```csharp
public struct ObjectHolder {
   Object o1;
   [MarshalAs(UnmanagedType.IDispatch)]public Object o2;
}
```

<span data-ttu-id="c7ede-131">次のコードでは、フォーマットされた型をタイプ ライブラリにエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="c7ede-131">The following code exports the formatted type to a type library.</span></span>

```cpp
struct ObjectHolder {
   VARIANT o1;
   IDispatch *o2;
}
```

## <a name="marshaling-object-to-interface"></a><span data-ttu-id="c7ede-132">インターフェイスへのオブジェクトのマーシャリング</span><span class="sxs-lookup"><span data-stu-id="c7ede-132">Marshaling Object to Interface</span></span>

<span data-ttu-id="c7ede-133">オブジェクトがインターフェイスとして COM に公開される場合、そのインターフェイスはマネージド型 <xref:System.Object> 用のクラス インターフェイス ( **_Object** インターフェイス) となります。</span><span class="sxs-lookup"><span data-stu-id="c7ede-133">When an object is exposed to COM as an interface, that interface is the class interface for the managed type <xref:System.Object> (the **_Object** interface).</span></span> <span data-ttu-id="c7ede-134">このインターフェイスは、結果のタイプ ライブラリでは、**IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) または **IUnknown** (**UnmanagedType.IUnknown**) として型指定されます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-134">This interface is typed as an **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) or an **IUnknown** (**UnmanagedType.IUnknown**) in the resulting type library.</span></span> <span data-ttu-id="c7ede-135">COM クライアントは、マネージド クラスのメンバー、または派生クラスによって実装されるメンバーを **_Object** インターフェイス経由で動的に呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-135">COM clients can dynamically invoke the members of the managed class or any members implemented by its derived classes through the **_Object** interface.</span></span> <span data-ttu-id="c7ede-136">クライアントは **QueryInterface** を呼び出して、マネージド型によって明示的に実装された他の任意のインターフェイスを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-136">The client can also call **QueryInterface** to obtain any other interface explicitly implemented by the managed type.</span></span>

## <a name="marshaling-object-to-variant"></a><span data-ttu-id="c7ede-137">バリアントへのオブジェクトのマーシャリング</span><span class="sxs-lookup"><span data-stu-id="c7ede-137">Marshaling Object to Variant</span></span>

<span data-ttu-id="c7ede-138">オブジェクトがバリアントにマーシャリングされる場合、内部バリアント型は次の規則に従って実行時に決定されます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-138">When an object is marshaled to a variant, the internal variant type is determined at run time, based on the following rules:</span></span>

- <span data-ttu-id="c7ede-139">オブジェクト参照が null (Visual Basic では **Nothing**) の場合、オブジェクトは **VT_EMPTY** 型のバリアントにマーシャリングされます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-139">If the object reference is null (**Nothing** in Visual Basic), the object is marshaled to a variant of type **VT_EMPTY**.</span></span>

- <span data-ttu-id="c7ede-140">オブジェクトが、次の表にリストされているいずれかの型のインスタンスである場合、結果として生成されるバリアント型は、表に示されている、マーシャラーに組み込まれている規則によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-140">If the object is an instance of any type listed in the following table, the resulting variant type is determined by the rules built into the marshaler and shown in the table.</span></span>

- <span data-ttu-id="c7ede-141">マーシャリング動作を明示的に制御する必要があるその他のオブジェクトは、<xref:System.IConvertible> インターフェイスを実装できます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-141">Other objects that need to explicitly control the marshaling behavior can implement the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="c7ede-142">その場合、バリアント型は <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> メソッドから返される型コードによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-142">In that case, the variant type is determined by the type code returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c7ede-143">それ以外の場合、オブジェクトは **VT_UNKNOWN** 型のバリアントとしてマーシャリングされます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-143">Otherwise, the object is marshaled as a variant of type **VT_UNKNOWN**.</span></span>

### <a name="marshaling-system-types-to-variant"></a><span data-ttu-id="c7ede-144">バリアントへのシステム型のマーシャリング</span><span class="sxs-lookup"><span data-stu-id="c7ede-144">Marshaling System Types to Variant</span></span>

<span data-ttu-id="c7ede-145">次の表に、マネージド オブジェクト型とそれに対応する COM バリアント型を示します。</span><span class="sxs-lookup"><span data-stu-id="c7ede-145">The following table shows managed object types and their corresponding COM variant types.</span></span> <span data-ttu-id="c7ede-146">これらの型は、呼び出されるメソッドのシグネチャが <xref:System.Object?displayProperty=nameWithType> 型の場合にのみ変換されます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-146">These types are converted only when the signature of the method being called is of type <xref:System.Object?displayProperty=nameWithType>.</span></span>

|<span data-ttu-id="c7ede-147">オブジェクトの種類</span><span class="sxs-lookup"><span data-stu-id="c7ede-147">Object type</span></span>|<span data-ttu-id="c7ede-148">COM バリアント型</span><span class="sxs-lookup"><span data-stu-id="c7ede-148">COM variant type</span></span>|
|-----------------|----------------------|
|<span data-ttu-id="c7ede-149">null オブジェクト参照 (Visual Basic では **Nothing**)。</span><span class="sxs-lookup"><span data-stu-id="c7ede-149">Null object reference (**Nothing** in Visual Basic).</span></span>|<span data-ttu-id="c7ede-150">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="c7ede-150">**VT_EMPTY**</span></span>|
|<xref:System.DBNull?displayProperty=nameWithType>|<span data-ttu-id="c7ede-151">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="c7ede-151">**VT_NULL**</span></span>|
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|<span data-ttu-id="c7ede-152">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="c7ede-152">**VT_ERROR**</span></span>|
|<xref:System.Reflection.Missing?displayProperty=nameWithType>|<span data-ttu-id="c7ede-153">**VT_ERROR** と **E_PARAMNOTFOUND**</span><span class="sxs-lookup"><span data-stu-id="c7ede-153">**VT_ERROR** with **E_PARAMNOTFOUND**</span></span>|
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|<span data-ttu-id="c7ede-154">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="c7ede-154">**VT_DISPATCH**</span></span>|
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|<span data-ttu-id="c7ede-155">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="c7ede-155">**VT_UNKNOWN**</span></span>|
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|<span data-ttu-id="c7ede-156">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="c7ede-156">**VT_CY**</span></span>|
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="c7ede-157">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="c7ede-157">**VT_BOOL**</span></span>|
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="c7ede-158">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="c7ede-158">**VT_I1**</span></span>|
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="c7ede-159">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="c7ede-159">**VT_UI1**</span></span>|
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="c7ede-160">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="c7ede-160">**VT_I2**</span></span>|
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="c7ede-161">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="c7ede-161">**VT_UI2**</span></span>|
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="c7ede-162">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="c7ede-162">**VT_I4**</span></span>|
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="c7ede-163">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="c7ede-163">**VT_UI4**</span></span>|
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="c7ede-164">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="c7ede-164">**VT_I8**</span></span>|
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="c7ede-165">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="c7ede-165">**VT_UI8**</span></span>|
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="c7ede-166">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="c7ede-166">**VT_R4**</span></span>|
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="c7ede-167">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="c7ede-167">**VT_R8**</span></span>|
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="c7ede-168">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="c7ede-168">**VT_DECIMAL**</span></span>|
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="c7ede-169">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="c7ede-169">**VT_DATE**</span></span>|
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="c7ede-170">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="c7ede-170">**VT_BSTR**</span></span>|
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="c7ede-171">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="c7ede-171">**VT_INT**</span></span>|
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="c7ede-172">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="c7ede-172">**VT_UINT**</span></span>|
|<xref:System.Array?displayProperty=nameWithType>|<span data-ttu-id="c7ede-173">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="c7ede-173">**VT_ARRAY**</span></span>|

<span data-ttu-id="c7ede-174">上の例で定義した `MarshalObject` インターフェイスを使用して、次のコード例ではさまざまな型のバリアントを COM サーバーに渡す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c7ede-174">Using the `MarshalObject` interface defined in the previous example, the following code example demonstrates how to pass various types of variants to a COM server.</span></span>

```vb
Dim mo As New MarshalObject()
mo.SetVariant(Nothing)         ' Marshal as variant of type VT_EMPTY.
mo.SetVariant(System.DBNull.Value) ' Marshal as variant of type VT_NULL.
mo.SetVariant(CInt(27))        ' Marshal as variant of type VT_I2.
mo.SetVariant(CLng(27))        ' Marshal as variant of type VT_I4.
mo.SetVariant(CSng(27.0))      ' Marshal as variant of type VT_R4.
mo.SetVariant(CDbl(27.0))      ' Marshal as variant of type VT_R8.
```

```csharp
MarshalObject mo = new MarshalObject();
mo.SetVariant(null);            // Marshal as variant of type VT_EMPTY.
mo.SetVariant(System.DBNull.Value); // Marshal as variant of type VT_NULL.
mo.SetVariant((int)27);          // Marshal as variant of type VT_I2.
mo.SetVariant((long)27);          // Marshal as variant of type VT_I4.
mo.SetVariant((single)27.0);   // Marshal as variant of type VT_R4.
mo.SetVariant((double)27.0);   // Marshal as variant of type VT_R8.
```

<span data-ttu-id="c7ede-175"><xref:System.Runtime.InteropServices.ErrorWrapper>、<xref:System.Runtime.InteropServices.DispatchWrapper>、<xref:System.Runtime.InteropServices.UnknownWrapper>、および <xref:System.Runtime.InteropServices.CurrencyWrapper> などのラッパー クラスを使用すると、対応するマネージド型を持たない COM 型をマーシャリングできます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-175">COM types that do not have corresponding managed types can be marshaled using wrapper classes such as <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, and <xref:System.Runtime.InteropServices.CurrencyWrapper>.</span></span> <span data-ttu-id="c7ede-176">次のコード例では、これらのラッパーを使用して、さまざまな型のバリアントを COM サーバーに渡す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c7ede-176">The following code example demonstrates how to use these wrappers to pass various types of variants to a COM server.</span></span>

```vb
Imports System.Runtime.InteropServices
' Pass inew as a variant of type VT_UNKNOWN interface.
mo.SetVariant(New UnknownWrapper(inew))
' Pass inew as a variant of type VT_DISPATCH interface.
mo.SetVariant(New DispatchWrapper(inew))
' Pass a value as a variant of type VT_ERROR interface.
mo.SetVariant(New ErrorWrapper(&H80054002))
' Pass a value as a variant of type VT_CURRENCY interface.
mo.SetVariant(New CurrencyWrapper(New Decimal(5.25)))
```

```csharp
using System.Runtime.InteropServices;
// Pass inew as a variant of type VT_UNKNOWN interface.
mo.SetVariant(new UnknownWrapper(inew));
// Pass inew as a variant of type VT_DISPATCH interface.
mo.SetVariant(new DispatchWrapper(inew));
// Pass a value as a variant of type VT_ERROR interface.
mo.SetVariant(new ErrorWrapper(0x80054002));
// Pass a value as a variant of type VT_CURRENCY interface.
mo.SetVariant(new CurrencyWrapper(new Decimal(5.25)));
```

<span data-ttu-id="c7ede-177">ラッパー クラスは、<xref:System.Runtime.InteropServices> 名前空間で定義されます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-177">The wrapper classes are defined in the <xref:System.Runtime.InteropServices> namespace.</span></span>

### <a name="marshaling-the-iconvertible-interface-to-variant"></a><span data-ttu-id="c7ede-178">バリアントへの IConvertible インターフェイスのマーシャリング</span><span class="sxs-lookup"><span data-stu-id="c7ede-178">Marshaling the IConvertible Interface to Variant</span></span>

<span data-ttu-id="c7ede-179">前のセクションでリストしたもの以外の型は、<xref:System.IConvertible> インターフェイスを実装することにより、型のマーシャリング方法を制御できます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-179">Types other than those listed in the previous section can control how they are marshaled by implementing the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="c7ede-180">オブジェクトが **IConvertible** インターフェイスを実装する場合、その COM バリアント型は <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> メソッドから返された <xref:System.TypeCode> 列挙体の値によって実行時に決定されます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-180">If the object implements the **IConvertible** interface, the COM variant type is determined at run time by the value of the <xref:System.TypeCode> enumeration returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="c7ede-181">次の表に、**TypeCode** 列挙体に対して有効な値と、それぞれの値に対応する COM バリアント型を示します。</span><span class="sxs-lookup"><span data-stu-id="c7ede-181">The following table shows the possible values for the **TypeCode** enumeration and the corresponding COM variant type for each value.</span></span>

|<span data-ttu-id="c7ede-182">TypeCode</span><span class="sxs-lookup"><span data-stu-id="c7ede-182">TypeCode</span></span>|<span data-ttu-id="c7ede-183">COM バリアント型</span><span class="sxs-lookup"><span data-stu-id="c7ede-183">COM variant type</span></span>|
|--------------|----------------------|
|<span data-ttu-id="c7ede-184">**TypeCode.Empty**</span><span class="sxs-lookup"><span data-stu-id="c7ede-184">**TypeCode.Empty**</span></span>|<span data-ttu-id="c7ede-185">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="c7ede-185">**VT_EMPTY**</span></span>|
|<span data-ttu-id="c7ede-186">**TypeCode.Object**</span><span class="sxs-lookup"><span data-stu-id="c7ede-186">**TypeCode.Object**</span></span>|<span data-ttu-id="c7ede-187">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="c7ede-187">**VT_UNKNOWN**</span></span>|
|<span data-ttu-id="c7ede-188">**TypeCode.DBNull**</span><span class="sxs-lookup"><span data-stu-id="c7ede-188">**TypeCode.DBNull**</span></span>|<span data-ttu-id="c7ede-189">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="c7ede-189">**VT_NULL**</span></span>|
|<span data-ttu-id="c7ede-190">**TypeCode.Boolean**</span><span class="sxs-lookup"><span data-stu-id="c7ede-190">**TypeCode.Boolean**</span></span>|<span data-ttu-id="c7ede-191">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="c7ede-191">**VT_BOOL**</span></span>|
|<span data-ttu-id="c7ede-192">**TypeCode.Char**</span><span class="sxs-lookup"><span data-stu-id="c7ede-192">**TypeCode.Char**</span></span>|<span data-ttu-id="c7ede-193">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="c7ede-193">**VT_UI2**</span></span>|
|<span data-ttu-id="c7ede-194">**TypeCode.Sbyte**</span><span class="sxs-lookup"><span data-stu-id="c7ede-194">**TypeCode.Sbyte**</span></span>|<span data-ttu-id="c7ede-195">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="c7ede-195">**VT_I1**</span></span>|
|<span data-ttu-id="c7ede-196">**TypeCode.Byte**</span><span class="sxs-lookup"><span data-stu-id="c7ede-196">**TypeCode.Byte**</span></span>|<span data-ttu-id="c7ede-197">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="c7ede-197">**VT_UI1**</span></span>|
|<span data-ttu-id="c7ede-198">**TypeCode.Int16**</span><span class="sxs-lookup"><span data-stu-id="c7ede-198">**TypeCode.Int16**</span></span>|<span data-ttu-id="c7ede-199">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="c7ede-199">**VT_I2**</span></span>|
|<span data-ttu-id="c7ede-200">**TypeCode.UInt16**</span><span class="sxs-lookup"><span data-stu-id="c7ede-200">**TypeCode.UInt16**</span></span>|<span data-ttu-id="c7ede-201">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="c7ede-201">**VT_UI2**</span></span>|
|<span data-ttu-id="c7ede-202">**TypeCode.Int32**</span><span class="sxs-lookup"><span data-stu-id="c7ede-202">**TypeCode.Int32**</span></span>|<span data-ttu-id="c7ede-203">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="c7ede-203">**VT_I4**</span></span>|
|<span data-ttu-id="c7ede-204">**TypeCode.UInt32**</span><span class="sxs-lookup"><span data-stu-id="c7ede-204">**TypeCode.UInt32**</span></span>|<span data-ttu-id="c7ede-205">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="c7ede-205">**VT_UI4**</span></span>|
|<span data-ttu-id="c7ede-206">**TypeCode.Int64**</span><span class="sxs-lookup"><span data-stu-id="c7ede-206">**TypeCode.Int64**</span></span>|<span data-ttu-id="c7ede-207">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="c7ede-207">**VT_I8**</span></span>|
|<span data-ttu-id="c7ede-208">**TypeCode.UInt64**</span><span class="sxs-lookup"><span data-stu-id="c7ede-208">**TypeCode.UInt64**</span></span>|<span data-ttu-id="c7ede-209">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="c7ede-209">**VT_UI8**</span></span>|
|<span data-ttu-id="c7ede-210">**TypeCode.Single**</span><span class="sxs-lookup"><span data-stu-id="c7ede-210">**TypeCode.Single**</span></span>|<span data-ttu-id="c7ede-211">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="c7ede-211">**VT_R4**</span></span>|
|<span data-ttu-id="c7ede-212">**TypeCode.Double**</span><span class="sxs-lookup"><span data-stu-id="c7ede-212">**TypeCode.Double**</span></span>|<span data-ttu-id="c7ede-213">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="c7ede-213">**VT_R8**</span></span>|
|<span data-ttu-id="c7ede-214">**TypeCode.Decimal**</span><span class="sxs-lookup"><span data-stu-id="c7ede-214">**TypeCode.Decimal**</span></span>|<span data-ttu-id="c7ede-215">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="c7ede-215">**VT_DECIMAL**</span></span>|
|<span data-ttu-id="c7ede-216">**TypeCode.DateTime**</span><span class="sxs-lookup"><span data-stu-id="c7ede-216">**TypeCode.DateTime**</span></span>|<span data-ttu-id="c7ede-217">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="c7ede-217">**VT_DATE**</span></span>|
|<span data-ttu-id="c7ede-218">**TypeCode.String**</span><span class="sxs-lookup"><span data-stu-id="c7ede-218">**TypeCode.String**</span></span>|<span data-ttu-id="c7ede-219">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="c7ede-219">**VT_BSTR**</span></span>|
|<span data-ttu-id="c7ede-220">サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c7ede-220">Not supported.</span></span>|<span data-ttu-id="c7ede-221">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="c7ede-221">**VT_INT**</span></span>|
|<span data-ttu-id="c7ede-222">サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c7ede-222">Not supported.</span></span>|<span data-ttu-id="c7ede-223">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="c7ede-223">**VT_UINT**</span></span>|
|<span data-ttu-id="c7ede-224">サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c7ede-224">Not supported.</span></span>|<span data-ttu-id="c7ede-225">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="c7ede-225">**VT_ARRAY**</span></span>|
|<span data-ttu-id="c7ede-226">サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c7ede-226">Not supported.</span></span>|<span data-ttu-id="c7ede-227">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="c7ede-227">**VT_RECORD**</span></span>|
|<span data-ttu-id="c7ede-228">サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c7ede-228">Not supported.</span></span>|<span data-ttu-id="c7ede-229">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="c7ede-229">**VT_CY**</span></span>|
|<span data-ttu-id="c7ede-230">サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c7ede-230">Not supported.</span></span>|<span data-ttu-id="c7ede-231">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="c7ede-231">**VT_VARIANT**</span></span>|

<span data-ttu-id="c7ede-232">COM バリアントの値は、**IConvertible.To** *Type* インターフェイスを呼び出すことによって決定されます。この **To** *Type* は、**IConvertible.GetTypeCode** から返された型に対応する変換ルーチンです。</span><span class="sxs-lookup"><span data-stu-id="c7ede-232">The value of the COM variant is determined by calling the **IConvertible.To** *Type* interface, where **To** *Type* is the conversion routine that corresponds to the type that was returned from **IConvertible.GetTypeCode**.</span></span> <span data-ttu-id="c7ede-233">たとえば、**IConvertible.GetTypeCode** から **TypeCode.Double** を返すオブジェクトは、**VT_R8** 型の COM バリアントとしてマーシャリングされます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-233">For example, an object that returns **TypeCode.Double** from **IConvertible.GetTypeCode** is marshaled as a COM variant of type **VT_R8**.</span></span> <span data-ttu-id="c7ede-234">バリアントの値 (COM バリアントの **dblVal** フィールド内に格納される) は、**IConvertible** インターフェイスにキャストし、<xref:System.IConvertible.ToDouble%2A> メソッドを呼び出すことで取得できます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-234">You can obtain the value of the variant (stored in the **dblVal** field of the COM variant) by casting to the **IConvertible** interface and calling the <xref:System.IConvertible.ToDouble%2A> method.</span></span>

## <a name="marshaling-variant-to-object"></a><span data-ttu-id="c7ede-235">オブジェクトへのバリアントのマーシャリング</span><span class="sxs-lookup"><span data-stu-id="c7ede-235">Marshaling Variant to Object</span></span>

<span data-ttu-id="c7ede-236">バリアントをオブジェクトにマーシャリングする場合、マーシャリングされるバリアントの型、および場合によっては値で、生成されるオブジェクトの型が決まります。</span><span class="sxs-lookup"><span data-stu-id="c7ede-236">When marshaling a variant to an object, the type, and sometimes the value, of the marshaled variant determines the type of object produced.</span></span> <span data-ttu-id="c7ede-237">次の表に、各バリアント型とそれに対応するオブジェクト型を示します。オブジェクト型はバリアントが COM から .NET Framework に渡されるときにマーシャラーによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-237">The following table identifies each variant type and the corresponding object type that the marshaler creates when a variant is passed from COM to the .NET Framework.</span></span>

|<span data-ttu-id="c7ede-238">COM バリアント型</span><span class="sxs-lookup"><span data-stu-id="c7ede-238">COM variant type</span></span>|<span data-ttu-id="c7ede-239">オブジェクトの種類</span><span class="sxs-lookup"><span data-stu-id="c7ede-239">Object type</span></span>|
|----------------------|-----------------|
|<span data-ttu-id="c7ede-240">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="c7ede-240">**VT_EMPTY**</span></span>|<span data-ttu-id="c7ede-241">null オブジェクト参照 (Visual Basic では **Nothing**)。</span><span class="sxs-lookup"><span data-stu-id="c7ede-241">Null object reference (**Nothing** in Visual Basic).</span></span>|
|<span data-ttu-id="c7ede-242">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="c7ede-242">**VT_NULL**</span></span>|<xref:System.DBNull?displayProperty=nameWithType>|
|<span data-ttu-id="c7ede-243">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="c7ede-243">**VT_DISPATCH**</span></span>|<span data-ttu-id="c7ede-244">**System.__ComObject**、または (pdispVal == null) の場合は null</span><span class="sxs-lookup"><span data-stu-id="c7ede-244">**System.__ComObject** or null if (pdispVal == null)</span></span>|
|<span data-ttu-id="c7ede-245">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="c7ede-245">**VT_UNKNOWN**</span></span>|<span data-ttu-id="c7ede-246">**System.__ComObject**、または (punkVal == null) の場合は null</span><span class="sxs-lookup"><span data-stu-id="c7ede-246">**System.__ComObject** or null if (punkVal == null)</span></span>|
|<span data-ttu-id="c7ede-247">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="c7ede-247">**VT_ERROR**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|<span data-ttu-id="c7ede-248">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="c7ede-248">**VT_BOOL**</span></span>|<xref:System.Boolean?displayProperty=nameWithType>|
|<span data-ttu-id="c7ede-249">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="c7ede-249">**VT_I1**</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|<span data-ttu-id="c7ede-250">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="c7ede-250">**VT_UI1**</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|<span data-ttu-id="c7ede-251">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="c7ede-251">**VT_I2**</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|<span data-ttu-id="c7ede-252">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="c7ede-252">**VT_UI2**</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|<span data-ttu-id="c7ede-253">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="c7ede-253">**VT_I4**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|<span data-ttu-id="c7ede-254">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="c7ede-254">**VT_UI4**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|<span data-ttu-id="c7ede-255">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="c7ede-255">**VT_I8**</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|<span data-ttu-id="c7ede-256">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="c7ede-256">**VT_UI8**</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|
|<span data-ttu-id="c7ede-257">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="c7ede-257">**VT_R4**</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|<span data-ttu-id="c7ede-258">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="c7ede-258">**VT_R8**</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|<span data-ttu-id="c7ede-259">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="c7ede-259">**VT_DECIMAL**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|
|<span data-ttu-id="c7ede-260">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="c7ede-260">**VT_DATE**</span></span>|<xref:System.DateTime?displayProperty=nameWithType>|
|<span data-ttu-id="c7ede-261">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="c7ede-261">**VT_BSTR**</span></span>|<xref:System.String?displayProperty=nameWithType>|
|<span data-ttu-id="c7ede-262">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="c7ede-262">**VT_INT**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|<span data-ttu-id="c7ede-263">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="c7ede-263">**VT_UINT**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|<span data-ttu-id="c7ede-264">**VT_ARRAY** &#124; **VT_** \*</span><span class="sxs-lookup"><span data-stu-id="c7ede-264">**VT_ARRAY** &#124; **VT_**\*</span></span>|<xref:System.Array?displayProperty=nameWithType>|
|<span data-ttu-id="c7ede-265">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="c7ede-265">**VT_CY**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|
|<span data-ttu-id="c7ede-266">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="c7ede-266">**VT_RECORD**</span></span>|<span data-ttu-id="c7ede-267">対応するボックス化された値型。</span><span class="sxs-lookup"><span data-stu-id="c7ede-267">Corresponding boxed value type.</span></span>|
|<span data-ttu-id="c7ede-268">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="c7ede-268">**VT_VARIANT**</span></span>|<span data-ttu-id="c7ede-269">サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c7ede-269">Not supported.</span></span>|

<span data-ttu-id="c7ede-270">COM からマネージド コードに渡された後で COM に返されるバリアント型が、呼び出し中に同じバリアント型を維持しないことがあります。</span><span class="sxs-lookup"><span data-stu-id="c7ede-270">Variant types passed from COM to managed code and then back to COM might not retain the same variant type for the duration of the call.</span></span> <span data-ttu-id="c7ede-271">**VT_DISPATCH** 型のバリアントが COM から .NET Framework に渡される場合、どのようになるかを考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="c7ede-271">Consider what happens when a variant of type **VT_DISPATCH** is passed from COM to the .NET Framework.</span></span> <span data-ttu-id="c7ede-272">マーシャリング時に、バリアントは <xref:System.Object?displayProperty=nameWithType> に変換されます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-272">During marshaling, the variant is converted to a <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c7ede-273">その後、**Object** が COM に返される場合は、**VT_UNKNOWN** 型のバリアントにマーシャリングされます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-273">If the **Object** is then passed back to COM, it is marshaled back to a variant of type **VT_UNKNOWN**.</span></span> <span data-ttu-id="c7ede-274">オブジェクトをマネージド コードから COM にマーシャリングするときに、生成されるバリアントの型が、最初にオブジェクトを生成するときに使用したバリアントの型と同じになる保証はありません。</span><span class="sxs-lookup"><span data-stu-id="c7ede-274">There is no guarantee that the variant produced when an object is marshaled from managed code to COM will be the same type as the variant initially used to produce the object.</span></span>

## <a name="marshaling-byref-variants"></a><span data-ttu-id="c7ede-275">ByRef バリアントのマーシャリング</span><span class="sxs-lookup"><span data-stu-id="c7ede-275">Marshaling ByRef Variants</span></span>

<span data-ttu-id="c7ede-276">バリアント自体を値渡し、または参照渡しすることはできますが、**VT_BYREF** フラグを任意のバリアント型と併用した場合は、そのバリアントの内容を値渡しではなく、参照渡しすることを指定できます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-276">Although variants themselves can be passed by value or by reference, the **VT_BYREF** flag can also be used with any variant type to indicate that the contents of the variant are being passed by reference instead of by value.</span></span> <span data-ttu-id="c7ede-277">バリアントの参照渡しによるマーシャリングと、**VT_BYREF** フラグの設定によるバリアントのマーシャリングとの違いがわかりづらい場合がああります。</span><span class="sxs-lookup"><span data-stu-id="c7ede-277">The difference between marshaling variants by reference and marshaling a variant with the **VT_BYREF** flag set can be confusing.</span></span> <span data-ttu-id="c7ede-278">その違いを次の図で明確にします。</span><span class="sxs-lookup"><span data-stu-id="c7ede-278">The following illustration clarifies the differences:</span></span>

<span data-ttu-id="c7ede-279">![スタックに渡されたバリアントを示す図。](./media/default-marshaling-for-objects/interop-variant-passed-value-reference.gif)</span><span class="sxs-lookup"><span data-stu-id="c7ede-279">![Diagram that shows variant passed on the stack.](./media/default-marshaling-for-objects/interop-variant-passed-value-reference.gif)</span></span>
<span data-ttu-id="c7ede-280">値渡しされるバリアントと参照渡しされるバリアント</span><span class="sxs-lookup"><span data-stu-id="c7ede-280">Variants passed by value and by reference</span></span>

<span data-ttu-id="c7ede-281">**オブジェクトとバリアントを値渡しでマーシャリングする場合の既定の動作**</span><span class="sxs-lookup"><span data-stu-id="c7ede-281">**Default behavior for marshaling objects and variants by value**</span></span>

- <span data-ttu-id="c7ede-282">オブジェクトをマネージド コードから COM に渡す場合、そのオブジェクトの内容は、「[バリアントへのオブジェクトのマーシャリング](#marshaling-object-to-variant)」で定義されている規則を使用して、マーシャラーによって作成される新しいバリアントにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-282">When passing objects from managed code to COM, the contents of the object are copied into a new variant created by the marshaler, using the rules defined in [Marshaling Object to Variant](#marshaling-object-to-variant).</span></span> <span data-ttu-id="c7ede-283">アンマネージ側でバリアントに対して行われた変更の内容は、呼び出しから制御が返されるときに、元のオブジェクトには反映されません。</span><span class="sxs-lookup"><span data-stu-id="c7ede-283">Changes made to the variant on the unmanaged side are not propagated back to the original object on return from the call.</span></span>

- <span data-ttu-id="c7ede-284">バリアントを COM からマネージド コードに渡す場合、そのバリアントの内容は、「[オブジェクトへのバリアントのマーシャリング](#marshaling-variant-to-object)」で定義されている規則を使用して、新規作成されるオブジェクトにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-284">When passing variants from COM to managed code, the contents of the variant are copied to a newly created object, using the rules defined in [Marshaling Variant to Object](#marshaling-variant-to-object).</span></span> <span data-ttu-id="c7ede-285">マネージド側でオブジェクトに対して行われた変更の内容は、呼び出しから制御が返されるときに、元のバリアントには反映されません。</span><span class="sxs-lookup"><span data-stu-id="c7ede-285">Changes made to the object on the managed side are not propagated back to the original variant on return from the call.</span></span>

<span data-ttu-id="c7ede-286">**オブジェクトとバリアントを参照渡しでマーシャリングする場合の既定の動作**</span><span class="sxs-lookup"><span data-stu-id="c7ede-286">**Default behavior for marshaling objects and variants by reference**</span></span>

<span data-ttu-id="c7ede-287">変更内容を呼び出し元に反映させるには、パラメーターを参照渡しする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7ede-287">To propagate changes back to the caller, the parameters must be passed by reference.</span></span> <span data-ttu-id="c7ede-288">たとえば、C# でキーワード **ref** (Visual Basic マネージド コードの場合は **ByRef**) を使用すると、パラメーターを参照渡しできます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-288">For example, you can use the **ref** keyword in C# (or **ByRef** in Visual Basic managed code) to pass parameters by reference.</span></span> <span data-ttu-id="c7ede-289">COM の場合、参照パラメーターは **variant \*** などのポインターを使用して渡されます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-289">In COM, reference parameters are passed using a pointer such as a **variant \***.</span></span>

- <span data-ttu-id="c7ede-290">オブジェクトを COM に参照渡しする場合、マーシャラーは呼び出しを行う前に新しいバリアントを作成し、オブジェクト参照の内容をそのバリアントにコピーします。</span><span class="sxs-lookup"><span data-stu-id="c7ede-290">When passing an object to COM by reference, the marshaler creates a new variant and copies the contents of the object reference into the variant before the call is made.</span></span> <span data-ttu-id="c7ede-291">このバリアントはアンマネージ関数に渡されます。ここで、バリアントの内容を自由に変更できます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-291">The variant is passed to the unmanaged function where the user is free to change the contents of the variant.</span></span> <span data-ttu-id="c7ede-292">呼び出しから制御が返されるときに、アンマネージ側でバリアントが変更されている場合には、その内容が元のオブジェクトに反映されます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-292">On return from the call, any changes made to the variant on the unmanaged side are propagated back to the original object.</span></span> <span data-ttu-id="c7ede-293">バリアントの型が、呼び出しに渡されたバリアントの型と異なる場合、変更内容は別の型のオブジェクトに反映されます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-293">If the type of the variant differs from the type of the variant passed to the call, then the changes are propagated back to an object of a different type.</span></span> <span data-ttu-id="c7ede-294">つまり、呼び出しに渡したオブジェクトの型が、呼び出しから返されるオブジェクトの型と異なることがあります。</span><span class="sxs-lookup"><span data-stu-id="c7ede-294">That is, the type of the object passed into the call can differ from the type of the object returned from the call.</span></span>

- <span data-ttu-id="c7ede-295">バリアントをマネージド コードに参照渡しする場合、マーシャラーは呼び出しを行う前に、新しいオブジェクトを作成し、バリアントの内容をそのオブジェクトにコピーします。</span><span class="sxs-lookup"><span data-stu-id="c7ede-295">When passing a variant to managed code by reference, the marshaler creates a new object and copies the contents of the variant into the object before making the call.</span></span> <span data-ttu-id="c7ede-296">オブジェクトへの参照がマネージド関数に渡されます。ここで、オブジェクトを自由に変更できます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-296">A reference to the object is passed to the managed function, where the user is free to change the object.</span></span> <span data-ttu-id="c7ede-297">呼び出しから制御が返されるときに、参照先オブジェクトが変更されている場合には、その内容が元のバリアントに反映されます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-297">On return from the call, any changes made to the referenced object are propagated back to the original variant.</span></span> <span data-ttu-id="c7ede-298">オブジェクトの型が、呼び出しに渡されたオブジェクトの型と異なる場合、元のバリアントの型が変更され、値がそのバリアントに反映されます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-298">If the type of the object differs from the type of the object passed in to the call, the type of the original variant is changed and the value is propagated back into the variant.</span></span> <span data-ttu-id="c7ede-299">ここでも、呼び出しに渡されたバリアントの型が、呼び出しから返されるバリアントの型と異なることがあります。</span><span class="sxs-lookup"><span data-stu-id="c7ede-299">Again, the type of the variant passed into the call can differ from the type of the variant returned from the call.</span></span>

 <span data-ttu-id="c7ede-300">**VT_BYREF フラグの設定によるバリアントのマーシャリングの既定の動作**</span><span class="sxs-lookup"><span data-stu-id="c7ede-300">**Default behavior for marshaling a variant with the VT_BYREF flag set**</span></span>

- <span data-ttu-id="c7ede-301">マネージド コードに値渡しされるバリアントに **VT_BYREF** フラグを設定することにより、そのバリアントに値ではなく、参照が含まれることを示すことができます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-301">A variant being passed to managed code by value can have the **VT_BYREF** flag set to indicate that the variant contains a reference instead of a value.</span></span> <span data-ttu-id="c7ede-302">この場合でも、バリアントは値渡しされるため、オブジェクトにマーシャリングされます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-302">In this case, the variant is still marshaled to an object because the variant is being passed by value.</span></span> <span data-ttu-id="c7ede-303">呼び出しを行う前に、マーシャラーは自動的にバリアントの内容を逆参照し、その内容を新しく作成されるオブジェクトにコピーします。</span><span class="sxs-lookup"><span data-stu-id="c7ede-303">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="c7ede-304">その後、オブジェクトはマネージド関数に渡されます。ただし、呼び出しから制御が返されるときに、このオブジェクトは元のバリアントには反映されません。</span><span class="sxs-lookup"><span data-stu-id="c7ede-304">The object is then passed into the managed function; however, on return from the call, the object is not propagated back into the original variant.</span></span> <span data-ttu-id="c7ede-305">マネージド オブジェクトに対する変更内容は失われます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-305">Changes made to the managed object are lost.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="c7ede-306">バリアントに **VT_BYREF** フラグが設定されていても、値渡しされるバリアントの値を変更する方法はありません。</span><span class="sxs-lookup"><span data-stu-id="c7ede-306">There is no way to change the value of a variant passed by value, even if the variant has the **VT_BYREF** flag set.</span></span>

- <span data-ttu-id="c7ede-307">マネージド コードに参照渡しされるバリアントについても、**VT_BYREF** フラグを設定することで、バリアントに別の参照が含まれることを示すことができます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-307">A variant being passed to managed code by reference can also have the **VT_BYREF** flag set to indicate that the variant contains another reference.</span></span> <span data-ttu-id="c7ede-308">このようにすると、バリアントは参照渡しされるため、**ref** オブジェクトにマーシャリングされます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-308">If it does, the variant is marshaled to a **ref** object because the variant is being passed by reference.</span></span> <span data-ttu-id="c7ede-309">呼び出しを行う前に、マーシャラーは自動的にバリアントの内容を逆参照し、その内容を新しく作成されるオブジェクトにコピーします。</span><span class="sxs-lookup"><span data-stu-id="c7ede-309">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="c7ede-310">呼び出しから制御が返されるときに、オブジェクトの値が元のバリアント内の参照に反映されるのは、そのオブジェクトの型が渡されたオブジェクトの型と同じ場合に限られます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-310">On return from the call, the value of the object is propagated back to the reference within the original variant only if the object is the same type as the object passed in.</span></span> <span data-ttu-id="c7ede-311">つまり、**VT_BYREF** フラグが設定されたバリアントの型が反映によって変更されることはありません。</span><span class="sxs-lookup"><span data-stu-id="c7ede-311">That is, propagation does not change the type of a variant with the **VT_BYREF** flag set.</span></span> <span data-ttu-id="c7ede-312">呼び出しの間にオブジェクトの型が変更された場合、呼び出しから制御が返されるときに <xref:System.InvalidCastException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="c7ede-312">If the type of the object is changed during the call, an <xref:System.InvalidCastException> occurs on return from the call.</span></span>

<span data-ttu-id="c7ede-313">バリアントとオブジェクトに関する反映規則を次の表にまとめます。</span><span class="sxs-lookup"><span data-stu-id="c7ede-313">The following table summarizes the propagation rules for variants and objects.</span></span>

|<span data-ttu-id="c7ede-314">From</span><span class="sxs-lookup"><span data-stu-id="c7ede-314">From</span></span>|<span data-ttu-id="c7ede-315">終了</span><span class="sxs-lookup"><span data-stu-id="c7ede-315">To</span></span>|<span data-ttu-id="c7ede-316">変更内容の反映</span><span class="sxs-lookup"><span data-stu-id="c7ede-316">Changes propagated back</span></span>|
|----------|--------|-----------------------------|
|<span data-ttu-id="c7ede-317">**Variant**  *v*</span><span class="sxs-lookup"><span data-stu-id="c7ede-317">**Variant**  *v*</span></span>|<span data-ttu-id="c7ede-318">**Object**  *o*</span><span class="sxs-lookup"><span data-stu-id="c7ede-318">**Object**  *o*</span></span>|<span data-ttu-id="c7ede-319">Never</span><span class="sxs-lookup"><span data-stu-id="c7ede-319">Never</span></span>|
|<span data-ttu-id="c7ede-320">**Object**  *o*</span><span class="sxs-lookup"><span data-stu-id="c7ede-320">**Object**  *o*</span></span>|<span data-ttu-id="c7ede-321">**Variant**  *v*</span><span class="sxs-lookup"><span data-stu-id="c7ede-321">**Variant**  *v*</span></span>|<span data-ttu-id="c7ede-322">Never</span><span class="sxs-lookup"><span data-stu-id="c7ede-322">Never</span></span>|
|<span data-ttu-id="c7ede-323">**Variant**   ***\****  *pv*</span><span class="sxs-lookup"><span data-stu-id="c7ede-323">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="c7ede-324">**Ref Object**  *o*</span><span class="sxs-lookup"><span data-stu-id="c7ede-324">**Ref Object**  *o*</span></span>|<span data-ttu-id="c7ede-325">Always</span><span class="sxs-lookup"><span data-stu-id="c7ede-325">Always</span></span>|
|<span data-ttu-id="c7ede-326">**Ref object**  *o*</span><span class="sxs-lookup"><span data-stu-id="c7ede-326">**Ref object**  *o*</span></span>|<span data-ttu-id="c7ede-327">**Variant**   ***\****  *pv*</span><span class="sxs-lookup"><span data-stu-id="c7ede-327">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="c7ede-328">Always</span><span class="sxs-lookup"><span data-stu-id="c7ede-328">Always</span></span>|
|<span data-ttu-id="c7ede-329">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_\*)**</span><span class="sxs-lookup"><span data-stu-id="c7ede-329">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_\*)**</span></span>|<span data-ttu-id="c7ede-330">**Object**  *o*</span><span class="sxs-lookup"><span data-stu-id="c7ede-330">**Object**  *o*</span></span>|<span data-ttu-id="c7ede-331">Never</span><span class="sxs-lookup"><span data-stu-id="c7ede-331">Never</span></span>|
|<span data-ttu-id="c7ede-332">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_)**</span><span class="sxs-lookup"><span data-stu-id="c7ede-332">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_)**</span></span>|<span data-ttu-id="c7ede-333">**Ref Object**  *o*</span><span class="sxs-lookup"><span data-stu-id="c7ede-333">**Ref Object**  *o*</span></span>|<span data-ttu-id="c7ede-334">型が変更されていない場合のみ。</span><span class="sxs-lookup"><span data-stu-id="c7ede-334">Only if the type has not changed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="c7ede-335">関連項目</span><span class="sxs-lookup"><span data-stu-id="c7ede-335">See also</span></span>

- [<span data-ttu-id="c7ede-336">既定のマーシャリング動作</span><span class="sxs-lookup"><span data-stu-id="c7ede-336">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="c7ede-337">Blittable 型と非 Blittable 型</span><span class="sxs-lookup"><span data-stu-id="c7ede-337">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="c7ede-338">[方向属性](/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c7ede-338">[Directional Attributes](/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="c7ede-339">コピーと固定</span><span class="sxs-lookup"><span data-stu-id="c7ede-339">Copying and Pinning</span></span>](copying-and-pinning.md)
