---
title: DLL 内の関数の識別
ms.date: 03/30/2017
helpviewer_keywords:
- platform invoke, identifying functions
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- identifying DLL functions
- DLL functions
ms.assetid: 3e3f6780-6d90-4413-bad7-ba641220364d
ms.openlocfilehash: 1a94bb2020b07ba8405d901f46ec4a0687e79700
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121973"
---
# <a name="identifying-functions-in-dlls"></a><span data-ttu-id="86ccc-102">DLL 内の関数の識別</span><span class="sxs-lookup"><span data-stu-id="86ccc-102">Identifying Functions in DLLs</span></span>
<span data-ttu-id="86ccc-103">DLL 関数の ID は、次の要素で構成されます。</span><span class="sxs-lookup"><span data-stu-id="86ccc-103">The identity of a DLL function consists of the following elements:</span></span>  
  
- <span data-ttu-id="86ccc-104">関数の名前または序数</span><span class="sxs-lookup"><span data-stu-id="86ccc-104">Function name or ordinal</span></span>  
  
- <span data-ttu-id="86ccc-105">実装が含まれている DLL ファイルの名前</span><span class="sxs-lookup"><span data-stu-id="86ccc-105">Name of the DLL file in which the implementation can be found</span></span>  
  
 <span data-ttu-id="86ccc-106">たとえば、User32.dll で **MessageBox** 関数を指定すると、関数 (**MessageBox**) とその場所 (User32.dll、User32、または user32) が識別されます。</span><span class="sxs-lookup"><span data-stu-id="86ccc-106">For example, specifying the **MessageBox** function in the User32.dll identifies the function (**MessageBox**) and its location (User32.dll, User32, or user32).</span></span> <span data-ttu-id="86ccc-107">Microsoft Windows のアプリケーション プログラミング インターフェイス (Windows API) は、文字と文字列を処理する各関数の 2 つのバージョンを含めることができます。これは、1 バイト文字 ANSI バージョンと 2 バイト文字 Unicode バージョンです。</span><span class="sxs-lookup"><span data-stu-id="86ccc-107">The Microsoft Windows application programming interface (Windows API) can contain two versions of each function that handles characters and strings: a 1-byte character ANSI version and a 2-byte character Unicode version.</span></span> <span data-ttu-id="86ccc-108">指定されていない場合、<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> フィールドによって表される文字セットは、既定で ANSI になります。</span><span class="sxs-lookup"><span data-stu-id="86ccc-108">When unspecified, the character set, represented by the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field, defaults to ANSI.</span></span> <span data-ttu-id="86ccc-109">一部の関数は、2 つのより多くのバージョンを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="86ccc-109">Some functions can have more than two versions.</span></span>  
  
 <span data-ttu-id="86ccc-110">**MessageBoxA** は、**MessageBox** 関数の ANSI のエントリ ポイントであり、**MessageBoxW** は Unicode バージョンです。</span><span class="sxs-lookup"><span data-stu-id="86ccc-110">**MessageBoxA** is the ANSI entry point for the **MessageBox** function; **MessageBoxW** is the Unicode version.</span></span> <span data-ttu-id="86ccc-111">さまざまなコマンド ライン ツールを実行して、User32.dll などの特定の DLL の関数名の一覧を表示することができます。</span><span class="sxs-lookup"><span data-stu-id="86ccc-111">You can list function names for a specific DLL, such as user32.dll, by running a variety of command-line tools.</span></span> <span data-ttu-id="86ccc-112">たとえば、`dumpbin /exports user32.dll` または `link /dump /exports user32.dll` を使用して関数名を取得できます。</span><span class="sxs-lookup"><span data-stu-id="86ccc-112">For example, you can use `dumpbin /exports user32.dll` or `link /dump /exports user32.dll` to obtain function names.</span></span>  
  
 <span data-ttu-id="86ccc-113">DLL で新しい名前を元のエントリ ポイントにマップする限り、コード内でアンマネージ関数の名前を自由に変更することができます。</span><span class="sxs-lookup"><span data-stu-id="86ccc-113">You can rename an unmanaged function to whatever you like within your code as long as you map the new name to the original entry point in the DLL.</span></span> <span data-ttu-id="86ccc-114">マネージド ソース コードでアンマネージド DLL 関数の名前を変更する方法の詳細については、「[Specifying an Entry Point](specifying-an-entry-point.md)」(エントリ ポイントの指定) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86ccc-114">For instructions on renaming an unmanaged DLL function in managed source code, see the [Specifying an Entry Point](specifying-an-entry-point.md).</span></span>  
  
 <span data-ttu-id="86ccc-115">プラットフォーム呼び出しにより、Windows API とその他の DLL で関数を呼び出すことによって、オペレーティング システムの重要な部分を制御できます。</span><span class="sxs-lookup"><span data-stu-id="86ccc-115">Platform invoke enables you to control a significant portion of the operating system by calling functions in the Windows API and other DLLs.</span></span> <span data-ttu-id="86ccc-116">Windows API に加えて、その他の多数の API と DLL を、プラットフォーム呼び出しによって使用できます。</span><span class="sxs-lookup"><span data-stu-id="86ccc-116">In addition to the Windows API, there are numerous other APIs and DLLs available to you through platform invoke.</span></span>  
  
 <span data-ttu-id="86ccc-117">次の表では、Windows API のいくつかの一般的に使用される DLL について説明します。</span><span class="sxs-lookup"><span data-stu-id="86ccc-117">The following table describes several commonly used DLLs in the Windows API.</span></span>  
  
|<span data-ttu-id="86ccc-118">[DLL]</span><span class="sxs-lookup"><span data-stu-id="86ccc-118">DLL</span></span>|<span data-ttu-id="86ccc-119">コンテンツの説明</span><span class="sxs-lookup"><span data-stu-id="86ccc-119">Description of Contents</span></span>|  
|---------|-----------------------------|  
|<span data-ttu-id="86ccc-120">GDI32.dll</span><span class="sxs-lookup"><span data-stu-id="86ccc-120">GDI32.dll</span></span>|<span data-ttu-id="86ccc-121">描画とフォントの管理などのデバイスの出力のグラフィックス デバイス インターフェイス (GDI) 関数。</span><span class="sxs-lookup"><span data-stu-id="86ccc-121">Graphics Device Interface (GDI) functions for device output, such as those for drawing and font management.</span></span>|  
|<span data-ttu-id="86ccc-122">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="86ccc-122">Kernel32.dll</span></span>|<span data-ttu-id="86ccc-123">メモリ管理とリソースの処理のための低レベルのオペレーティング システム関数。</span><span class="sxs-lookup"><span data-stu-id="86ccc-123">Low-level operating system functions for memory management and resource handling.</span></span>|  
|<span data-ttu-id="86ccc-124">User32.dll</span><span class="sxs-lookup"><span data-stu-id="86ccc-124">User32.dll</span></span>|<span data-ttu-id="86ccc-125">メッセージの処理、タイマー、メニュー、通信用の Windows 管理関数。</span><span class="sxs-lookup"><span data-stu-id="86ccc-125">Windows management functions for message handling, timers, menus, and communications.</span></span>|  
  
 <span data-ttu-id="86ccc-126">Windows API の詳細については、プラットフォーム SDK を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86ccc-126">For complete documentation on the Windows API, see the Platform SDK.</span></span> <span data-ttu-id="86ccc-127">プラットフォーム呼び出しで使用する .NET ベースの宣言を作成する方法を示す例については、「[プラットフォーム呼び出しによるデータのマーシャリング](marshaling-data-with-platform-invoke.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86ccc-127">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86ccc-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="86ccc-128">See also</span></span>

- [<span data-ttu-id="86ccc-129">アンマネージ DLL 関数の処理</span><span class="sxs-lookup"><span data-stu-id="86ccc-129">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="86ccc-130">エントリ ポイントの指定</span><span class="sxs-lookup"><span data-stu-id="86ccc-130">Specifying an Entry Point</span></span>](specifying-an-entry-point.md)
- [<span data-ttu-id="86ccc-131">DLL 関数を保持するクラスの作成</span><span class="sxs-lookup"><span data-stu-id="86ccc-131">Creating a Class to Hold DLL Functions</span></span>](creating-a-class-to-hold-dll-functions.md)
- [<span data-ttu-id="86ccc-132">マネージド コードでのプロトタイプの作成</span><span class="sxs-lookup"><span data-stu-id="86ccc-132">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="86ccc-133">DLL 関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="86ccc-133">Calling a DLL Function</span></span>](calling-a-dll-function.md)
