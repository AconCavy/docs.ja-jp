---
title: '方法 : イベントベースの非同期パターンのクライアントを実装する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 21a858c1-3c99-4904-86ee-0d17b49804fa
ms.openlocfilehash: 50aa36d2caf774638ad20323813f0de3703aab2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "69950719"
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a><span data-ttu-id="e38e5-102">方法 : イベントベースの非同期パターンのクライアントを実装する</span><span class="sxs-lookup"><span data-stu-id="e38e5-102">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="e38e5-103">次のコード例では、[イベント ベースの非同期パターンの概要](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)ページに記載されている方法でコンポーネントを使用しています。</span><span class="sxs-lookup"><span data-stu-id="e38e5-103">The following code example demonstrates how to use a component that adheres to the [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span> <span data-ttu-id="e38e5-104">この例のフォームでは、「[方法 : イベントベースの非同期パターンをサポートするコンポーネントを実装する](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)」に説明がある `PrimeNumberCalculator` コンポーネントが使用されています。</span><span class="sxs-lookup"><span data-stu-id="e38e5-104">The form for this example uses the `PrimeNumberCalculator` component described in [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>  
  
 <span data-ttu-id="e38e5-105">この例を使用するプロジェクトを実行すると、"Prime Number Calculator" とグリッドと共に、 **[Start New Task]\(新しいタスクの開始\)** と **[キャンセル]** という 2 つのボタンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e38e5-105">When you run a project that uses this example, you will see a "Prime Number Calculator" form with a grid and two buttons: **Start New Task** and **Cancel**.</span></span> <span data-ttu-id="e38e5-106">**[Start New Task]\(新しいタスクの開始\)** ボタンは数回連続でクリックできます。クリックのたびに、非同期操作は計算を開始し、無作為に生成されたテスト用の数字が素数かどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="e38e5-106">You can click the **Start New Task** button several times in succession, and for each click, an asynchronous operation will begin a computation to determine if a randomly generated test number is prime.</span></span> <span data-ttu-id="e38e5-107">フォームには進捗と増分が定期的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="e38e5-107">The form will periodically display progress and incremental results.</span></span> <span data-ttu-id="e38e5-108">各操作には一意のタスク ID が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="e38e5-108">Each operation is assigned a unique task ID.</span></span> <span data-ttu-id="e38e5-109">計算結果は **[結果]** 列に表示されます。テスト用の数字が素数ではない場合、**Composite** というラベルが付き、その最初の除数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e38e5-109">The result of the computation is displayed in the **Result** column; if the test number is not prime, it is labeled as **Composite,** and its first divisor is displayed.</span></span>  
  
 <span data-ttu-id="e38e5-110">保留中の操作は **[キャンセル]** ボタンでキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="e38e5-110">Any pending operation can be canceled with the **Cancel** button.</span></span> <span data-ttu-id="e38e5-111">複数選択が可能です。</span><span class="sxs-lookup"><span data-stu-id="e38e5-111">Multiple selections can be made.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e38e5-112">ほとんどの数値は素数になりません。</span><span class="sxs-lookup"><span data-stu-id="e38e5-112">Most numbers will not be prime.</span></span> <span data-ttu-id="e38e5-113">操作を数回完了しても素数が出てこない場合、さらに多くのタスクを開始してください。いずれは素数が見つかります。</span><span class="sxs-lookup"><span data-stu-id="e38e5-113">If you have not found a prime number after several completed operations, simply start more tasks, and eventually you will find some prime numbers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e38e5-114">例</span><span class="sxs-lookup"><span data-stu-id="e38e5-114">Example</span></span>  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="e38e5-115">参照</span><span class="sxs-lookup"><span data-stu-id="e38e5-115">See also</span></span>

- <xref:System.ComponentModel.AsyncOperation>
- <xref:System.ComponentModel.AsyncOperationManager>
- <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
