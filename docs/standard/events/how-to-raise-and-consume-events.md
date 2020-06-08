---
title: '方法 : イベントを発生させる/処理する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], raising
- raising events
- events [.NET Framework], samples
ms.assetid: 42afade7-3a02-4f2e-868b-95845f302f8f
ms.openlocfilehash: 4d0b24b8a6f1b914745d819b90b973752e32447c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279959"
---
# <a name="how-to-raise-and-consume-events"></a><span data-ttu-id="db2c6-102">方法 : イベントを発生させる/処理する</span><span class="sxs-lookup"><span data-stu-id="db2c6-102">How to: Raise and Consume Events</span></span>
<span data-ttu-id="db2c6-103">このトピックの例では、イベントを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="db2c6-103">The examples in this topic show how to work with events.</span></span> <span data-ttu-id="db2c6-104">ここでは、<xref:System.EventHandler> デリゲートと <xref:System.EventHandler%601> デリゲート、およびカスタム デリゲートの例を使用して、データを持つイベントと持たないイベントを示します。</span><span class="sxs-lookup"><span data-stu-id="db2c6-104">They include examples of the <xref:System.EventHandler> delegate, the <xref:System.EventHandler%601> delegate, and a custom delegate, to illustrate events with and without data.</span></span>  
  
 <span data-ttu-id="db2c6-105">この例では、「[イベント](index.md)」で説明されている概念を使用します。</span><span class="sxs-lookup"><span data-stu-id="db2c6-105">The examples use concepts described in the [Events](index.md) article.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db2c6-106">例</span><span class="sxs-lookup"><span data-stu-id="db2c6-106">Example</span></span>  
 <span data-ttu-id="db2c6-107">最初の例は、データを持たないイベントを発生させて処理する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="db2c6-107">The first example shows how to raise and consume an event that doesn't have data.</span></span> <span data-ttu-id="db2c6-108">この例には、`Counter` という名前のイベントを持つ、`ThresholdReached` という名前のクラスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="db2c6-108">It contains a class named `Counter` that has an event named `ThresholdReached`.</span></span> <span data-ttu-id="db2c6-109">このイベントは、カウンター値がしきい値と等しいか、またはそれを超えた場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="db2c6-109">This event is raised when a counter value equals or exceeds a threshold value.</span></span> <span data-ttu-id="db2c6-110">イベントのデータが指定されていないため、<xref:System.EventHandler> デリゲートはイベントに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="db2c6-110">The <xref:System.EventHandler> delegate is associated with the event, because no event data is provided.</span></span>  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="db2c6-111">例</span><span class="sxs-lookup"><span data-stu-id="db2c6-111">Example</span></span>  
 <span data-ttu-id="db2c6-112">次の例は、データを持つイベントを発生させて処理する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="db2c6-112">The next example shows how to raise and consume an event that provides data.</span></span> <span data-ttu-id="db2c6-113"><xref:System.EventHandler%601> デリゲートはイベントに関連付けられ、カスタム イベント データ オブジェクトのインスタンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="db2c6-113">The <xref:System.EventHandler%601> delegate is associated with the event, and an instance of a custom event data object is provided.</span></span>  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="db2c6-114">例</span><span class="sxs-lookup"><span data-stu-id="db2c6-114">Example</span></span>  
 <span data-ttu-id="db2c6-115">次の例は、イベントのデリゲートを宣言する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="db2c6-115">The next example shows how to declare a delegate for an event.</span></span> <span data-ttu-id="db2c6-116">デリゲートの名前は `ThresholdReachedEventHandler` です。</span><span class="sxs-lookup"><span data-stu-id="db2c6-116">The delegate is named `ThresholdReachedEventHandler`.</span></span> <span data-ttu-id="db2c6-117">これはあくまでも一例です。</span><span class="sxs-lookup"><span data-stu-id="db2c6-117">This is just an illustration.</span></span> <span data-ttu-id="db2c6-118">通常は、<xref:System.EventHandler> デリゲートまたは <xref:System.EventHandler%601> デリゲートを使用できるため、イベントのデリゲートを宣言する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="db2c6-118">Typically, you do not have to declare a delegate for an event, because you can use either the <xref:System.EventHandler> or the <xref:System.EventHandler%601> delegate.</span></span> <span data-ttu-id="db2c6-119">ジェネリックを使用できないレガシ コードでクラスを使用できるようにするなど、ごくまれに、デリゲートの宣言が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="db2c6-119">You should declare a delegate only in rare scenarios, such as making your class available to legacy code that cannot use generics.</span></span>  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="db2c6-120">参照</span><span class="sxs-lookup"><span data-stu-id="db2c6-120">See also</span></span>

- [<span data-ttu-id="db2c6-121">イベント</span><span class="sxs-lookup"><span data-stu-id="db2c6-121">Events</span></span>](index.md)
