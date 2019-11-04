---
title: 正規表現におけるスレッド セーフ
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework regular expressions, threads
- regular expressions, threads
- searching with regular expressions, threads
- parsing text with regular expressions, threads
- pattern-matching with regular expressions, threads
ms.assetid: 7c4a167b-5236-4cde-a2ca-58646230730f
ms.openlocfilehash: db25028e10872cfca08d28518c795414d06c5d49
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124800"
---
# <a name="thread-safety-in-regular-expressions"></a><span data-ttu-id="1abd1-102">正規表現におけるスレッド セーフ</span><span class="sxs-lookup"><span data-stu-id="1abd1-102">Thread Safety in Regular Expressions</span></span>
<span data-ttu-id="1abd1-103"><xref:System.Text.RegularExpressions.Regex> クラス自体はスレッド セーフであり、変更できません (読み取り専用)。</span><span class="sxs-lookup"><span data-stu-id="1abd1-103">The <xref:System.Text.RegularExpressions.Regex> class itself is thread safe and immutable (read-only).</span></span> <span data-ttu-id="1abd1-104">つまり、**Regex** オブジェクトは任意のスレッドで作成できます。また、スレッド間で共有できます。一致するメソッドは任意のスレッドから呼び出すことができますが、グローバルな状態を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="1abd1-104">That is, **Regex** objects can be created on any thread and shared between threads; matching methods can be called from any thread and never alter any global state.</span></span>  
  
 <span data-ttu-id="1abd1-105">ただし、**Regex** から返された結果オブジェクト (**Match** と **MatchCollection**) は、単一のスレッドで使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1abd1-105">However, result objects (**Match** and **MatchCollection**) returned by **Regex** should be used on a single thread.</span></span> <span data-ttu-id="1abd1-106">これらのオブジェクトの多くは、論理的に変更できませんが、実装によってパフォーマンスを改善するために一部の結果の演算を遅延させることができます。結果として、呼び出し側はオブジェクトに対するアクセスをシリアル化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1abd1-106">Although many of these objects are logically immutable, their implementations could delay computation of some results to improve performance, and as a result, callers must serialize access to them.</span></span>  
  
 <span data-ttu-id="1abd1-107">複数のスレッドで **Regex** オブジェクトを共有する必要がある場合、同期されたメソッドを呼び出すことで、それらのオブジェクトはスレッドセーフ インスタンスに変換できます。</span><span class="sxs-lookup"><span data-stu-id="1abd1-107">If there is a need to share **Regex** result objects on multiple threads, these objects can be converted to thread-safe instances by calling their synchronized methods.</span></span> <span data-ttu-id="1abd1-108">列挙子の例外はありますが、すべての正規表現クラスはスレッド セーフです。または、同期されたメソッドでスレッドセーフ オブジェクトに変換することができます。</span><span class="sxs-lookup"><span data-stu-id="1abd1-108">With the exception of enumerators, all regular expression classes are thread safe or can be converted into thread-safe objects by a synchronized method.</span></span>  
  
 <span data-ttu-id="1abd1-109">列挙子は唯一の例外です。</span><span class="sxs-lookup"><span data-stu-id="1abd1-109">Enumerators are the only exception.</span></span> <span data-ttu-id="1abd1-110">アプリケーションはコレクション列挙子に対する呼び出しをシリアル化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1abd1-110">An application must serialize calls to collection enumerators.</span></span> <span data-ttu-id="1abd1-111">複数のスレッドでコレクションを同時に列挙できる場合、列挙子によってスキャンされるコレクションのルート オブジェクト上の列挙子メソッドを同期する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1abd1-111">The rule is that if a collection can be enumerated on more than one thread simultaneously, you should synchronize enumerator methods on the root object of the collection traversed by the enumerator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1abd1-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="1abd1-112">See also</span></span>

- [<span data-ttu-id="1abd1-113">.NET の正規表現</span><span class="sxs-lookup"><span data-stu-id="1abd1-113">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
