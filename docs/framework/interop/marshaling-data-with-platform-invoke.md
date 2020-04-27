---
title: プラットフォーム呼び出しによるデータのマーシャリング
ms.date: 03/20/2019
dev_langs:
- cpp
helpviewer_keywords:
- platform invoke, marshaling data
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: dc5c76cf-7b12-406f-b79c-d1a023ec245d
ms.openlocfilehash: b8c4e9d835db044912d1cbed92a14dd05e7de658
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400945"
---
# <a name="marshaling-data-with-platform-invoke"></a><span data-ttu-id="64097-102">プラットフォーム呼び出しによるデータのマーシャリング</span><span class="sxs-lookup"><span data-stu-id="64097-102">Marshaling Data with Platform Invoke</span></span>

<span data-ttu-id="64097-103">アンマネージド ライブラリからエクスポートされた関数を呼び出すには、.NET Framework アプリケーションで、マネージド コード内にアンマネージド 関数を表す関数プロトタイプが必要です。</span><span class="sxs-lookup"><span data-stu-id="64097-103">To call functions exported from an unmanaged library, a .NET Framework application requires a function prototype in managed code that represents the unmanaged function.</span></span> <span data-ttu-id="64097-104">プラットフォーム呼び出しがデータを正しくマーシャリングできるようにするプロトタイプを作成するには、次のことを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="64097-104">To create a prototype that enables platform invoke to marshal data correctly, you must do the following:</span></span>

- <span data-ttu-id="64097-105"><xref:System.Runtime.InteropServices.DllImportAttribute> 属性をマネージド コード内の静的関数またはメソッドに適用します。</span><span class="sxs-lookup"><span data-stu-id="64097-105">Apply the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute to the static function or method in managed code.</span></span>

- <span data-ttu-id="64097-106">アンマネージド データ型をマネージド データ型に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="64097-106">Substitute managed data types for unmanaged data types.</span></span>

<span data-ttu-id="64097-107">アンマネージド 関数に付属のドキュメントを使用して、属性とその省略可能なフィールドを適用し、アンマネージド型をマネージド データ型に置き換えることによって、同等のマネージド プロトタイプを作成できます。</span><span class="sxs-lookup"><span data-stu-id="64097-107">You can use the documentation supplied with an unmanaged function to construct an equivalent managed prototype by applying the attribute with its optional fields and substituting managed data types for unmanaged types.</span></span> <span data-ttu-id="64097-108"><xref:System.Runtime.InteropServices.DllImportAttribute> を適用する方法の詳細については、「[アンマネージ DLL 関数の処理](consuming-unmanaged-dll-functions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64097-108">For instructions about how to apply the <xref:System.Runtime.InteropServices.DllImportAttribute>, see [Consuming Unmanaged DLL Functions](consuming-unmanaged-dll-functions.md).</span></span>

<span data-ttu-id="64097-109">このセクションでは、アンマネージド ライブラリによってエクスポートされた関数に引数を渡し、その関数からの戻り値を受け取るための、マネージド関数のプロトタイプを作成する方法を示すサンプルを示します。</span><span class="sxs-lookup"><span data-stu-id="64097-109">This section provides samples that demonstrate how to create managed function prototypes for passing arguments to and receiving return values from functions exported by unmanaged libraries.</span></span> <span data-ttu-id="64097-110">サンプルではまた、いつ <xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性と <xref:System.Runtime.InteropServices.Marshal> クラスを使用して明示的にデータをマーシャリングするかをも示しています。</span><span class="sxs-lookup"><span data-stu-id="64097-110">The samples also demonstrate when to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute and the <xref:System.Runtime.InteropServices.Marshal> class to explicitly marshal data.</span></span>

## <a name="platform-invoke-data-types"></a><span data-ttu-id="64097-111">プラットフォーム呼び出しのデータ型</span><span class="sxs-lookup"><span data-stu-id="64097-111">Platform invoke data types</span></span>

<span data-ttu-id="64097-112">次の表は、Windows API と C スタイルの関数で使用されるデータ型を一覧で示しています。</span><span class="sxs-lookup"><span data-stu-id="64097-112">The following table lists data types used in the Windows APIs and C-style functions.</span></span> <span data-ttu-id="64097-113">多くのアンマネージ ライブラリには、これらのデータ型をパラメーターや戻り値として渡す関数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="64097-113">Many unmanaged libraries contain functions that pass these data types as parameters and return values.</span></span> <span data-ttu-id="64097-114">3 番目の列には、マネージド コードで使用する、対応する .NET Framework の組み込みの値型またはクラスを一覧で示します。</span><span class="sxs-lookup"><span data-stu-id="64097-114">The third column lists the corresponding .NET Framework built-in value type or class that you use in managed code.</span></span> <span data-ttu-id="64097-115">場合によっては、表にリストされた型を、同じサイズの型に置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="64097-115">In some cases, you can substitute a type of the same size for the type listed in the table.</span></span>

|<span data-ttu-id="64097-116">Windows API でのアンマネージ型</span><span class="sxs-lookup"><span data-stu-id="64097-116">Unmanaged type in Windows APIs</span></span>|<span data-ttu-id="64097-117">アンマネージ C 言語型</span><span class="sxs-lookup"><span data-stu-id="64097-117">Unmanaged C language type</span></span>|<span data-ttu-id="64097-118">マネージド型</span><span class="sxs-lookup"><span data-stu-id="64097-118">Managed type</span></span>|<span data-ttu-id="64097-119">説明</span><span class="sxs-lookup"><span data-stu-id="64097-119">Description</span></span>|
|--------------------------------|-------------------------------|------------------------|-----------------|
|`VOID`|`void`|<xref:System.Void?displayProperty=nameWithType>|<span data-ttu-id="64097-120">値を返さない関数に適用されます。</span><span class="sxs-lookup"><span data-stu-id="64097-120">Applied to a function that does not return a value.</span></span>|
|`HANDLE`|`void *`|<span data-ttu-id="64097-121"><xref:System.IntPtr?displayProperty=nameWithType> または <xref:System.UIntPtr?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="64097-121"><xref:System.IntPtr?displayProperty=nameWithType> or <xref:System.UIntPtr?displayProperty=nameWithType></span></span>|<span data-ttu-id="64097-122">32 ビット Windows オペレーティング システム、64 ビット Windows オペレーティング システムで 64 ビットに 32 ビットです。</span><span class="sxs-lookup"><span data-stu-id="64097-122">32 bits on 32-bit Windows operating systems, 64 bits on 64-bit Windows operating systems.</span></span>|
|`BYTE`|`unsigned char`|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="64097-123">8 ビット</span><span class="sxs-lookup"><span data-stu-id="64097-123">8 bits</span></span>|
|`SHORT`|`short`|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="64097-124">16 ビット</span><span class="sxs-lookup"><span data-stu-id="64097-124">16 bits</span></span>|
|`WORD`|`unsigned short`|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="64097-125">16 ビット</span><span class="sxs-lookup"><span data-stu-id="64097-125">16 bits</span></span>|
|`INT`|`int`|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="64097-126">32 ビット</span><span class="sxs-lookup"><span data-stu-id="64097-126">32 bits</span></span>|
|`UINT`|`unsigned int`|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="64097-127">32 ビット</span><span class="sxs-lookup"><span data-stu-id="64097-127">32 bits</span></span>|
|`LONG`|`long`|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="64097-128">32 ビット</span><span class="sxs-lookup"><span data-stu-id="64097-128">32 bits</span></span>|
|`BOOL`|`long`|<span data-ttu-id="64097-129"><xref:System.Boolean?displayProperty=nameWithType> または <xref:System.Int32?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="64097-129"><xref:System.Boolean?displayProperty=nameWithType> or <xref:System.Int32?displayProperty=nameWithType></span></span>|<span data-ttu-id="64097-130">32 ビット</span><span class="sxs-lookup"><span data-stu-id="64097-130">32 bits</span></span>|
|`DWORD`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="64097-131">32 ビット</span><span class="sxs-lookup"><span data-stu-id="64097-131">32 bits</span></span>|
|`ULONG`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="64097-132">32 ビット</span><span class="sxs-lookup"><span data-stu-id="64097-132">32 bits</span></span>|
|`CHAR`|`char`|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="64097-133">ANSI で装飾します。</span><span class="sxs-lookup"><span data-stu-id="64097-133">Decorate with ANSI.</span></span>|
|`WCHAR`|`wchar_t`|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="64097-134">Unicode で装飾します。</span><span class="sxs-lookup"><span data-stu-id="64097-134">Decorate with Unicode.</span></span>|
|`LPSTR`|`char *`|<span data-ttu-id="64097-135"><xref:System.String?displayProperty=nameWithType> または <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="64097-135"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="64097-136">ANSI で装飾します。</span><span class="sxs-lookup"><span data-stu-id="64097-136">Decorate with ANSI.</span></span>|
|`LPCSTR`|`const char *`|<span data-ttu-id="64097-137"><xref:System.String?displayProperty=nameWithType> または <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="64097-137"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="64097-138">ANSI で装飾します。</span><span class="sxs-lookup"><span data-stu-id="64097-138">Decorate with ANSI.</span></span>|
|`LPWSTR`|`wchar_t *`|<span data-ttu-id="64097-139"><xref:System.String?displayProperty=nameWithType> または <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="64097-139"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="64097-140">Unicode で装飾します。</span><span class="sxs-lookup"><span data-stu-id="64097-140">Decorate with Unicode.</span></span>|
|`LPCWSTR`|`const wchar_t *`|<span data-ttu-id="64097-141"><xref:System.String?displayProperty=nameWithType> または <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="64097-141"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="64097-142">Unicode で装飾します。</span><span class="sxs-lookup"><span data-stu-id="64097-142">Decorate with Unicode.</span></span>|
|`FLOAT`|`float`|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="64097-143">32 ビット</span><span class="sxs-lookup"><span data-stu-id="64097-143">32 bits</span></span>|
|`DOUBLE`|`double`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="64097-144">64 ビット</span><span class="sxs-lookup"><span data-stu-id="64097-144">64 bits</span></span>|

<span data-ttu-id="64097-145">Visual Basic、C#、および C++ での対応する型については、「[.NET Framework クラス ライブラリの概要](../../standard/class-library-overview.md#system-namespace)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64097-145">For corresponding types in Visual Basic, C#, and C++, see the [Introduction to the .NET Framework Class Library](../../standard/class-library-overview.md#system-namespace).</span></span>

## <a name="pinvokelibdll"></a><span data-ttu-id="64097-146">PinvokeLib.dll</span><span class="sxs-lookup"><span data-stu-id="64097-146">PinvokeLib.dll</span></span>

<span data-ttu-id="64097-147">次のコードでは、Pinvoke.dll によって提供されるライブラリ関数を定義します。</span><span class="sxs-lookup"><span data-stu-id="64097-147">The following code defines the library functions provided by Pinvoke.dll.</span></span> <span data-ttu-id="64097-148">このセクションで説明される多くのサンプルでは、このライブラリを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="64097-148">Many samples described in this section call this library.</span></span>

### <a name="example"></a><span data-ttu-id="64097-149">例</span><span class="sxs-lookup"><span data-stu-id="64097-149">Example</span></span>

[!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]

[!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
