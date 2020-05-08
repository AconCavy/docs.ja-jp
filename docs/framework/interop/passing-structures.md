---
title: 構造体の受け渡し
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform invoke, calling unmanaged functions
ms.assetid: 9b92ac73-32b7-4e1b-862e-6d8d950cf169
ms.openlocfilehash: 11e329fa8f0c059b6c2f1c8ccb1d6bd0d0f0030a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181339"
---
# <a name="passing-structures"></a><span data-ttu-id="ab0a9-102">構造体の受け渡し</span><span class="sxs-lookup"><span data-stu-id="ab0a9-102">Passing Structures</span></span>
<span data-ttu-id="ab0a9-103">多くのアンマネージド 関数では、構造体のメンバー (Visual Basic ではユーザー定義型) またはマネージド コードで定義されたクラスのメンバーがパラメーターとして渡されることを期待しています。</span><span class="sxs-lookup"><span data-stu-id="ab0a9-103">Many unmanaged functions expect you to pass, as a parameter to the function, members of structures (user-defined types in Visual Basic) or members of classes that are defined in managed code.</span></span> <span data-ttu-id="ab0a9-104">プラットフォーム呼び出しを使って構造体またはクラスをアンマネージ コードに渡す場合は、元のレイアウトやアラインメントを保持するための追加情報を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab0a9-104">When passing structures or classes to unmanaged code using platform invoke, you must provide additional information to preserve the original layout and alignment.</span></span> <span data-ttu-id="ab0a9-105">このトピックでは、フォーマットされた型を定義するために使用する <xref:System.Runtime.InteropServices.StructLayoutAttribute> 属性について説明します。</span><span class="sxs-lookup"><span data-stu-id="ab0a9-105">This topic introduces the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute, which you use to define formatted types.</span></span> <span data-ttu-id="ab0a9-106">マネージ構造体やマネージド クラスの場合は、**LayoutKind** 列挙型によって提供される想定されたレイアウト動作から選択できます。</span><span class="sxs-lookup"><span data-stu-id="ab0a9-106">For managed structures and classes, you can select from several predictable layout behaviors supplied by the **LayoutKind** enumeration.</span></span>  
  
 <span data-ttu-id="ab0a9-107">ここで説明する概念の中心は、構造体の型とクラスの型の相違点です。</span><span class="sxs-lookup"><span data-stu-id="ab0a9-107">Central to the concepts presented in this topic is an important difference between structure and class types.</span></span> <span data-ttu-id="ab0a9-108">構造体は値型であり、クラスは参照型です。クラスは常に最低 1 つのレベルのメモリの間接参照 (値へのポインター) を提供します。</span><span class="sxs-lookup"><span data-stu-id="ab0a9-108">Structures are value types and classes are reference types — classes always provide at least one level of memory indirection (a pointer to a value).</span></span> <span data-ttu-id="ab0a9-109">アンマネージ関数は、次の表の第 1 列のシグネチャに示されているように、間接参照を必要とすることが多いため、この違いは重要です。</span><span class="sxs-lookup"><span data-stu-id="ab0a9-109">This difference is important because unmanaged functions often demand indirection, as shown by the signatures in the first column of the following table.</span></span> <span data-ttu-id="ab0a9-110">他の列のマネージ構造体およびマネージド クラスの宣言は、宣言でどの程度間接参照のレベルを調整できるかを示しています。宣言は、Visual Basic と Visual C# の両方で指定されています。</span><span class="sxs-lookup"><span data-stu-id="ab0a9-110">The managed structure and class declarations in the remaining columns show the degree to which you can adjust the level of indirection in your declaration.Declarations are provided for both Visual Basic and Visual C#.</span></span>  
  
|<span data-ttu-id="ab0a9-111">アンマネージ シグネチャ</span><span class="sxs-lookup"><span data-stu-id="ab0a9-111">Unmanaged signature</span></span>|<span data-ttu-id="ab0a9-112">マネージド宣言</span><span class="sxs-lookup"><span data-stu-id="ab0a9-112">Managed declaration:</span></span> <br /><span data-ttu-id="ab0a9-113">間接参照なし</span><span class="sxs-lookup"><span data-stu-id="ab0a9-113">no indirection</span></span><br />`Structure MyType`<br />`struct MyType;`|<span data-ttu-id="ab0a9-114">マネージド宣言</span><span class="sxs-lookup"><span data-stu-id="ab0a9-114">Managed declaration:</span></span> <br /><span data-ttu-id="ab0a9-115">1 レベルの間接参照</span><span class="sxs-lookup"><span data-stu-id="ab0a9-115">one level of indirection</span></span><br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> <span data-ttu-id="ab0a9-116">0 レベルの間接参照を必要とします。</span><span class="sxs-lookup"><span data-stu-id="ab0a9-116">Demands zero levels of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="ab0a9-117">0 レベルの間接参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="ab0a9-117">Adds zero levels of indirection.</span></span>|<span data-ttu-id="ab0a9-118">既に 1 レベルの間接参照が存在するため調整できません。</span><span class="sxs-lookup"><span data-stu-id="ab0a9-118">Not possible because there is already one level of indirection.</span></span>|  
|`DoWork(MyType* x);`<br /><br /> <span data-ttu-id="ab0a9-119">1 レベルの間接参照を必要とします。</span><span class="sxs-lookup"><span data-stu-id="ab0a9-119">Demands one level of indirection.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="ab0a9-120">1 レベルの間接参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="ab0a9-120">Adds one level of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="ab0a9-121">0 レベルの間接参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="ab0a9-121">Adds zero levels of indirection.</span></span>|  
|`DoWork(MyType** x);`<br /><br /> <span data-ttu-id="ab0a9-122">2 レベルの間接参照を必要とします。</span><span class="sxs-lookup"><span data-stu-id="ab0a9-122">Demands two levels of indirection.</span></span>|<span data-ttu-id="ab0a9-123">**ByRef** **ByRef** または `ref` `ref` を使用できないため調整できません。</span><span class="sxs-lookup"><span data-stu-id="ab0a9-123">Not possible because **ByRef** **ByRef** or `ref` `ref` cannot be used.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="ab0a9-124">1 レベルの間接参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="ab0a9-124">Adds one level of indirection.</span></span>|  
  
 <span data-ttu-id="ab0a9-125">この表は、プラットフォーム呼び出しの宣言について次のようなガイドラインを示しています。</span><span class="sxs-lookup"><span data-stu-id="ab0a9-125">The table describes the following guidelines for platform invoke declarations:</span></span>  
  
- <span data-ttu-id="ab0a9-126">アンマネージ関数が間接参照を必要としない場合は、値渡しによる構造体を使用します。</span><span class="sxs-lookup"><span data-stu-id="ab0a9-126">Use a structure passed by value when the unmanaged function demands no indirection.</span></span>  
  
- <span data-ttu-id="ab0a9-127">アンマネージ関数が 1 レベルの間接参照を必要とする場合は、参照渡しによる構造体または値渡しによるクラスのいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="ab0a9-127">Use either a structure passed by reference or a class passed by value when the unmanaged function demands one level of indirection.</span></span>  
  
- <span data-ttu-id="ab0a9-128">アンマネージ関数が 2 レベルの間接参照を必要とする場合は、参照渡しによるクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="ab0a9-128">Use a class passed by reference when the unmanaged function demands two levels of indirection.</span></span>  
  
## <a name="declaring-and-passing-structures"></a><span data-ttu-id="ab0a9-129">構造体の宣言と受け渡し</span><span class="sxs-lookup"><span data-stu-id="ab0a9-129">Declaring and Passing Structures</span></span>  
 <span data-ttu-id="ab0a9-130">マネージド コードで `Point` 型および `Rect` 型を定義し、これらの型を User32.dll ファイル内の **PtInRect** 関数にパラメーターとして渡す方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ab0a9-130">The following example shows how to define the `Point` and `Rect` structures in managed code, and pass the types as parameter to the **PtInRect** function in the User32.dll file.</span></span> <span data-ttu-id="ab0a9-131">**PtInRect** は、次に示すアンマネージ シグネチャを持っています。</span><span class="sxs-lookup"><span data-stu-id="ab0a9-131">**PtInRect** has the following unmanaged signature:</span></span>  
  
```cpp
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="ab0a9-132">この関数は RECT 型へのポインターを期待しているため、Rect 構造体は参照渡しする必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ab0a9-132">Notice that you must pass the Rect structure by reference, since the function expects a pointer to a RECT type.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
  
<StructLayout(LayoutKind.Sequential)> Public Structure Point  
    Public x As Integer  
    Public y As Integer  
End Structure  
  
Public Structure <StructLayout(LayoutKind.Explicit)> Rect  
    <FieldOffset(0)> Public left As Integer  
    <FieldOffset(4)> Public top As Integer  
    <FieldOffset(8)> Public right As Integer  
    <FieldOffset(12)> Public bottom As Integer  
End Structure  
  
Friend Class NativeMethods
    Friend Declare Auto Function PtInRect Lib "user32.dll" (
        ByRef r As Rect, p As Point) As Boolean  
End Class  
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
  
internal static class NativeMethods
{  
    [DllImport("User32.dll")]  
    internal static extern bool PtInRect(ref Rect r, Point p);  
}  
```  
  
## <a name="declaring-and-passing-classes"></a><span data-ttu-id="ab0a9-133">クラスの宣言と受け渡し</span><span class="sxs-lookup"><span data-stu-id="ab0a9-133">Declaring and Passing Classes</span></span>  
 <span data-ttu-id="ab0a9-134">クラスが固定したメンバー レイアウトを持っている場合に限り、クラスのメンバーをアンマネージ DLL 関数に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="ab0a9-134">You can pass members of a class to an unmanaged DLL function, as long as the class has a fixed member layout.</span></span> <span data-ttu-id="ab0a9-135">定義の順序で固定されている `MySystemTime` クラスのメンバーを User32.dll ファイル内の **GetSystemTime** に渡す方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ab0a9-135">The following example demonstrates how to pass members of the `MySystemTime` class, which are defined in sequential order, to the **GetSystemTime** in the User32.dll file.</span></span> <span data-ttu-id="ab0a9-136">**GetSystemTime** は、次に示すアンマネージ シグネチャを持っています。</span><span class="sxs-lookup"><span data-stu-id="ab0a9-136">**GetSystemTime** has the following unmanaged signature:</span></span>  
  
```cpp
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="ab0a9-137">値型とは異なり、クラスは常に 1 レベルの間接参照を使用します。</span><span class="sxs-lookup"><span data-stu-id="ab0a9-137">Unlike value types, classes always have at least one level of indirection.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
  
<StructLayout(LayoutKind.Sequential)> Public Class MySystemTime  
    Public wYear As Short  
    Public wMonth As Short  
    Public wDayOfWeek As Short
    Public wDay As Short  
    Public wHour As Short  
    Public wMinute As Short  
    Public wSecond As Short  
    Public wMiliseconds As Short  
End Class  
  
Friend Class NativeMethods  
    Friend Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (
        sysTime As MySystemTime)  
    Friend Declare Auto Function MessageBox Lib "User32.dll" (
        hWnd As IntPtr, lpText As String, lpCaption As String, uType As UInteger) As Integer  
End Class  
  
Public Class TestPlatformInvoke
    Public Shared Sub Main()  
        Dim sysTime As New MySystemTime()  
        NativeMethods.GetSystemTime(sysTime)  
  
        Dim dt As String  
        dt = "System time is:" & ControlChars.CrLf & _  
              "Year: " & sysTime.wYear & _  
              ControlChars.CrLf & "Month: " & sysTime.wMonth & _  
              ControlChars.CrLf & "DayOfWeek: " & sysTime.wDayOfWeek & _  
              ControlChars.CrLf & "Day: " & sysTime.wDay  
        NativeMethods.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0)
    End Sub  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public class MySystemTime {  
    public ushort wYear;
    public ushort wMonth;  
    public ushort wDayOfWeek;
    public ushort wDay;
    public ushort wHour;
    public ushort wMinute;
    public ushort wSecond;
    public ushort wMilliseconds;
}  
internal static class NativeMethods
{  
    [DllImport("Kernel32.dll")]  
    internal static extern void GetSystemTime(MySystemTime st);  
  
    [DllImport("user32.dll", CharSet = CharSet.Auto)]  
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);  
}  
  
public class TestPlatformInvoke  
{  
    public static void Main()  
    {  
        MySystemTime sysTime = new MySystemTime();  
        NativeMethods.GetSystemTime(sysTime);  
  
        string dt;  
        dt = "System time is: \n" +  
              "Year: " + sysTime.wYear + "\n" +  
              "Month: " + sysTime.wMonth + "\n" +  
              "DayOfWeek: " + sysTime.wDayOfWeek + "\n" +  
              "Day: " + sysTime.wDay;  
        NativeMethods.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="ab0a9-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab0a9-138">See also</span></span>

- [<span data-ttu-id="ab0a9-139">DLL 関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="ab0a9-139">Calling a DLL Function</span></span>](calling-a-dll-function.md)
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
