---
title: コールバック メソッドとしてのデリゲートのマーシャ リング
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, Callback sample
- marshaling, Callback sample
ms.assetid: 6ddd7866-9804-4571-84de-83f5cc017a5a
ms.openlocfilehash: c71c89e5797745144a2baed2d4846e3d9f9f26be
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73114013"
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a><span data-ttu-id="e2e0b-102">コールバック メソッドとしてのデリゲートのマーシャ リング</span><span class="sxs-lookup"><span data-stu-id="e2e0b-102">Marshaling a Delegate as a Callback Method</span></span>
<span data-ttu-id="e2e0b-103">このサンプルでは、関数ポインターを要求するアンマネージ関数にデリゲートを渡す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e2e0b-103">This sample demonstrates how to pass delegates to an unmanaged function expecting function pointers.</span></span> <span data-ttu-id="e2e0b-104">デリゲートは、メソッドへの参照を保持できるクラスであり、タイプ セーフな関数ポインターまたはコールバック関数と同等のものです。</span><span class="sxs-lookup"><span data-stu-id="e2e0b-104">A delegate is a class that can hold a reference to a method and is equivalent to a type-safe function pointer or a callback function.</span></span>

> [!NOTE]
> <span data-ttu-id="e2e0b-105">呼び出しの中でデリゲートを使うと、共通言語ランタイムがデリゲートをその呼び出しの期間中ガベージ コレクションから保護します。</span><span class="sxs-lookup"><span data-stu-id="e2e0b-105">When you use a delegate inside a call, the common language runtime protects the delegate from being garbage collected for the duration of that call.</span></span> <span data-ttu-id="e2e0b-106">ただし、アンマネージ関数が呼び出し完了後に使うためにデリゲートを保存する場合は、アンマネージ関数がデリゲートを終了するまで手動でガベージ コレクションを防ぐ必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2e0b-106">However, if the unmanaged function stores the delegate to use after the call completes, you must manually prevent garbage collection until the unmanaged function finishes with the delegate.</span></span> <span data-ttu-id="e2e0b-107">詳細については、「[HandleRef Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100))」(HandleRef のサンプル) および「[GCHandle Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100))」(GCHandle のサンプル) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e2e0b-107">For more information, see the [HandleRef Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100)) and [GCHandle Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100)).</span></span>

<span data-ttu-id="e2e0b-108">Callback のサンプルで使用するアンマネージ関数とその元の関数宣言を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e2e0b-108">The Callback sample uses the following unmanaged functions, shown with their original function declaration:</span></span>

- <span data-ttu-id="e2e0b-109">PinvokeLib.dll からエクスポートされる `TestCallBack`。</span><span class="sxs-lookup"><span data-stu-id="e2e0b-109">`TestCallBack` exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestCallBack(FPTR pf, int value);
    ```

- <span data-ttu-id="e2e0b-110">PinvokeLib.dll からエクスポートされる `TestCallBack2`。</span><span class="sxs-lookup"><span data-stu-id="e2e0b-110">`TestCallBack2` exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestCallBack2(FPTR2 pf2, char* value);
    ```

<span data-ttu-id="e2e0b-111">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) はカスタム アンマネージ ライブラリであり、上で示した関数の実装を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="e2e0b-111">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed functions.</span></span>

<span data-ttu-id="e2e0b-112">このサンプルでは、`NativeMethods` クラスには、`TestCallBack` メソッドと `TestCallBack2` メソッドのマネージド プロトタイプが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e2e0b-112">In this sample, the `NativeMethods` class contains managed prototypes for the `TestCallBack` and `TestCallBack2` methods.</span></span> <span data-ttu-id="e2e0b-113">どちらのメソッドも、コールバック関数にパラメーターとしてデリゲートを渡します。</span><span class="sxs-lookup"><span data-stu-id="e2e0b-113">Both methods pass a delegate to a callback function as a parameter.</span></span> <span data-ttu-id="e2e0b-114">デリゲートのシグネチャは、それが参照しているメソッドのシグネチャと一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2e0b-114">The signature of the delegate must match the signature of the method it references.</span></span> <span data-ttu-id="e2e0b-115">たとえば、`FPtr` および `FPtr2` デリゲートのシグネチャは、`DoSomething` および `DoSomething2` メソッドと同じです。</span><span class="sxs-lookup"><span data-stu-id="e2e0b-115">For example, the `FPtr` and `FPtr2` delegates have signatures that are identical to the `DoSomething` and `DoSomething2` methods.</span></span>

## <a name="declaring-prototypes"></a><span data-ttu-id="e2e0b-116">プロトタイプの宣言</span><span class="sxs-lookup"><span data-stu-id="e2e0b-116">Declaring Prototypes</span></span>
[!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
[!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
[!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]

## <a name="calling-functions"></a><span data-ttu-id="e2e0b-117">関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="e2e0b-117">Calling Functions</span></span>
[!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
[!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
[!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]

## <a name="see-also"></a><span data-ttu-id="e2e0b-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="e2e0b-118">See also</span></span>

- <span data-ttu-id="e2e0b-119">[各種のマーシャリングのサンプル](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e2e0b-119">[Miscellaneous Marshaling Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))</span></span>
- [<span data-ttu-id="e2e0b-120">プラットフォーム呼び出しのデータ型</span><span class="sxs-lookup"><span data-stu-id="e2e0b-120">Platform Invoke Data Types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="e2e0b-121">マネージド コードでのプロトタイプの作成</span><span class="sxs-lookup"><span data-stu-id="e2e0b-121">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
