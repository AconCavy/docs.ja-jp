---
title: '方法: 事前計算済みのタスクを作成する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, creating pre-computed
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
ms.openlocfilehash: f5d2a70685fe0401d0219b99ada6936ac04691f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "73123136"
---
# <a name="how-to-create-pre-computed-tasks"></a><span data-ttu-id="595bc-102">方法: 事前計算済みのタスクを作成する</span><span class="sxs-lookup"><span data-stu-id="595bc-102">How to: Create Pre-Computed Tasks</span></span>
<span data-ttu-id="595bc-103">このドキュメントでは、キャッシュに保持されている非同期ダウンロード操作の結果を取得する <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> メソッドの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="595bc-103">This document describes how to use the <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> method to retrieve the results of asynchronous download operations that are held in a cache.</span></span> <span data-ttu-id="595bc-104"><xref:System.Threading.Tasks.Task.FromResult%2A> メソッドは、<xref:System.Threading.Tasks.Task%601> プロパティとして指定された値を保持する、完成した <xref:System.Threading.Tasks.Task%601.Result%2A> オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="595bc-104">The <xref:System.Threading.Tasks.Task.FromResult%2A> method returns a finished <xref:System.Threading.Tasks.Task%601> object that holds the provided value as its <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="595bc-105">このメソッドは <xref:System.Threading.Tasks.Task%601> オブジェクトの結果があらかじめ計算されている <xref:System.Threading.Tasks.Task%601> オブジェクトを返す、非同期操作を実行する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="595bc-105">This method is useful when you perform an asynchronous operation that returns a <xref:System.Threading.Tasks.Task%601> object, and the result of that <xref:System.Threading.Tasks.Task%601> object is already computed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="595bc-106">例</span><span class="sxs-lookup"><span data-stu-id="595bc-106">Example</span></span>  
 <span data-ttu-id="595bc-107">次の例では、Web から文字列をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="595bc-107">The following example downloads strings from the web.</span></span> <span data-ttu-id="595bc-108">これは `DownloadStringAsync` を定義します。</span><span class="sxs-lookup"><span data-stu-id="595bc-108">It defines the `DownloadStringAsync` method.</span></span> <span data-ttu-id="595bc-109">このメソッドでは、Web から非同期的に文字列をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="595bc-109">This method downloads strings from the web asynchronously.</span></span> <span data-ttu-id="595bc-110">また、この例では <xref:System.Collections.Concurrent.ConcurrentDictionary%602> オブジェクトを使用して、前の操作の結果をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="595bc-110">This example also uses a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> object to cache the results of previous operations.</span></span> <span data-ttu-id="595bc-111">入力アドレスがこのキャッシュに保持されている場合、`DownloadStringAsync` では <xref:System.Threading.Tasks.Task.FromResult%2A> メソッドを使用して、そのアドレスでコンテンツを保持する <xref:System.Threading.Tasks.Task%601> オブジェクトを生成します。</span><span class="sxs-lookup"><span data-stu-id="595bc-111">If the input address is held in this cache, `DownloadStringAsync` uses the <xref:System.Threading.Tasks.Task.FromResult%2A> method to produce a <xref:System.Threading.Tasks.Task%601> object that holds the content at that address.</span></span> <span data-ttu-id="595bc-112">それ以外の場合、`DownloadStringAsync` では Web からファイルをダウンロードし、結果をキャッシュに追加します。</span><span class="sxs-lookup"><span data-stu-id="595bc-112">Otherwise, `DownloadStringAsync` downloads the file from the web and adds the result to the cache.</span></span>  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 <span data-ttu-id="595bc-113">この例では、複数の文字列を 2 回ダウンロードするために必要な時間を計算します。</span><span class="sxs-lookup"><span data-stu-id="595bc-113">This example computes the time that is required to download multiple strings two times.</span></span> <span data-ttu-id="595bc-114">結果がキャッシュに保持されているため、ダウンロード操作の 2 番目のセットにかかる時間は最初のセットより短くなります。</span><span class="sxs-lookup"><span data-stu-id="595bc-114">The second set of download operations should take less time than the first set because the results are held in the cache.</span></span> <span data-ttu-id="595bc-115"><xref:System.Threading.Tasks.Task.FromResult%2A> メソッドを使用することで、`DownloadStringAsync` メソッドでこれらの事前計算済みの結果を保持する <xref:System.Threading.Tasks.Task%601> オブジェクトを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="595bc-115">The <xref:System.Threading.Tasks.Task.FromResult%2A> method enables the `DownloadStringAsync` method to create <xref:System.Threading.Tasks.Task%601> objects that hold these pre-computed results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="595bc-116">参照</span><span class="sxs-lookup"><span data-stu-id="595bc-116">See also</span></span>

- [<span data-ttu-id="595bc-117">タスク ベースの非同期プログラミング</span><span class="sxs-lookup"><span data-stu-id="595bc-117">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
