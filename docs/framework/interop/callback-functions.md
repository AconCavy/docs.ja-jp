---
title: コールバック関数
ms.date: 03/30/2017
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
ms.openlocfilehash: 8b8bb4dff4f73247282060c0b4fd778ae0169b1f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181515"
---
# <a name="callback-functions"></a><span data-ttu-id="7295d-102">コールバック関数</span><span class="sxs-lookup"><span data-stu-id="7295d-102">Callback Functions</span></span>
<span data-ttu-id="7295d-103">コールバック関数は、アンマネージド DLL 関数がタスクを完了できるように支援するマネージド アプリケーション内のコードです。</span><span class="sxs-lookup"><span data-stu-id="7295d-103">A callback function is code within a managed application that helps an unmanaged DLL function complete a task.</span></span> <span data-ttu-id="7295d-104">コールバック関数の呼び出しは、マネージド アプリケーションから、DLL 関数を介して、マネージド実装へと間接的に渡されます。</span><span class="sxs-lookup"><span data-stu-id="7295d-104">Calls to a callback function pass indirectly from a managed application, through a DLL function, and back to the managed implementation.</span></span> <span data-ttu-id="7295d-105">多数ある DLL 関数の一部はプラットフォーム呼び出しと呼ばれ、正常に実行されるには、マネージド コード内にコールバック関数が必要です。</span><span class="sxs-lookup"><span data-stu-id="7295d-105">Some of the many DLL functions called with platform invoke require a callback function in managed code to run properly.</span></span>  
  
 <span data-ttu-id="7295d-106">ほとんどの DLL 関数は、マネージド コードから呼び出す場合、関数のマネージド定義を作成してから、それを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7295d-106">To call most DLL functions from managed code, you create a managed definition of the function and then call it.</span></span> <span data-ttu-id="7295d-107">このプロセスは簡単です。</span><span class="sxs-lookup"><span data-stu-id="7295d-107">The process is straightforward.</span></span>  
  
 <span data-ttu-id="7295d-108">コールバック関数を必要とする DLL 関数を使用する場合は、追加の手順がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="7295d-108">Using a DLL function that requires a callback function has some additional steps.</span></span> <span data-ttu-id="7295d-109">まず、関数のドキュメントを参照して、その関数にコールバックが必要かどうかを判断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7295d-109">First, you must determine whether the function requires a callback by looking at the documentation for the function.</span></span> <span data-ttu-id="7295d-110">次に、マネージド アプリケーションにコールバック関数を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7295d-110">Next, you have to create the callback function in your managed application.</span></span> <span data-ttu-id="7295d-111">最後に、DLL 関数を呼び出し、引数としてコールバック関数のポインターを渡します。</span><span class="sxs-lookup"><span data-stu-id="7295d-111">Finally, you call the DLL function, passing a pointer to the callback function as an argument.</span></span>

 <span data-ttu-id="7295d-112">次の図は、コールバック関数と実装手順をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="7295d-112">The following illustration summarizes the callback function and implementation steps:</span></span>  
  
 ![プラットフォーム呼び出しのコールバック プロセスを示す図。](./media/callback-functions/platform-invoke-callback-process.gif)  
  
 <span data-ttu-id="7295d-114">コールバック関数は、タスクが繰り返し実行される状況での使用に最適です。</span><span class="sxs-lookup"><span data-stu-id="7295d-114">Callback functions are ideal for use in situations in which a task is performed repeatedly.</span></span> <span data-ttu-id="7295d-115">また、一般的な用途として、Windows API の **EnumFontFamilies**、**EnumPrinters**、**EnumWindows** などの列挙関数があります。</span><span class="sxs-lookup"><span data-stu-id="7295d-115">Another common usage is with enumeration functions, such as **EnumFontFamilies**, **EnumPrinters**, and **EnumWindows** in the Windows API.</span></span> <span data-ttu-id="7295d-116">**EnumWindows** 関数は、各ウィンドウでタスクを実行するコールバック関数を呼び出して、コンピューター上のすべての既存のウィンドウを列挙します。</span><span class="sxs-lookup"><span data-stu-id="7295d-116">The **EnumWindows** function enumerates through all existing windows on your computer, calling the callback function to perform a task on each window.</span></span> <span data-ttu-id="7295d-117">手順と例については、「[方法:コールバック関数を実装する](how-to-implement-callback-functions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7295d-117">For instructions and an example, see [How to: Implement Callback Functions](how-to-implement-callback-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7295d-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="7295d-118">See also</span></span>

- [<span data-ttu-id="7295d-119">方法: コールバック関数を実装する</span><span class="sxs-lookup"><span data-stu-id="7295d-119">How to: Implement Callback Functions</span></span>](how-to-implement-callback-functions.md)
- [<span data-ttu-id="7295d-120">DLL 関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="7295d-120">Calling a DLL Function</span></span>](calling-a-dll-function.md)
