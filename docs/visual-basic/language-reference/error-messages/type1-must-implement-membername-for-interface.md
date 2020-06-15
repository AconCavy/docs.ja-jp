---
title: <type1>'<typename>' は、インターフェイス '<interfacename>' に対して '<membername>' を実装しなければなりません。
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 4ffe18e11c388a8c69ef0592bde1b78f5b219680
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386855"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a><span data-ttu-id="22117-102">\<type1>'\<typename>' は、インターフェイス '\<interfacename>' に対して '\<membername>' を実装しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="22117-102">\<type1>'\<typename>' must implement '\<membername>' for interface '\<interfacename>'</span></span>
<span data-ttu-id="22117-103">'\<typename>' は、インターフェイス '\<interfacename>' に対して '\<membername>' を実装しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="22117-103">'\<typename>' must implement '\<membername>' for interface '\<interfacename>'.</span></span> <span data-ttu-id="22117-104">プロパティの実装には、一致する 'ReadOnly'/'WriteOnly' 指定子が必要です。</span><span class="sxs-lookup"><span data-stu-id="22117-104">Implementing property must have matching 'ReadOnly'/'WriteOnly' specifiers.</span></span>  
  
 <span data-ttu-id="22117-105">クラスまたは構造体では、インターフェイスを実装することが要求されますが、インターフェイスによって定義されるプロシージャ、プロパティ、またはイベントは実装しません。</span><span class="sxs-lookup"><span data-stu-id="22117-105">A class or structure claims to implement an interface but does not implement a procedure, property, or event defined by the interface.</span></span> <span data-ttu-id="22117-106">インターフェイスのすべてのメンバーを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="22117-106">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="22117-107">**エラー ID:** BC30154</span><span class="sxs-lookup"><span data-stu-id="22117-107">**Error ID:** BC30154</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="22117-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="22117-108">To correct this error</span></span>  
  
1. <span data-ttu-id="22117-109">インターフェイスで定義されているものと同じ名前およびシグネチャのメンバーを宣言します。</span><span class="sxs-lookup"><span data-stu-id="22117-109">Declare a member with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="22117-110">少なくとも `End Function`、`End Sub`、または `End Property` ステートメントを含めてください。</span><span class="sxs-lookup"><span data-stu-id="22117-110">Be sure to include at least the `End Function`, `End Sub`, or `End Property` statement.</span></span>  
  
2. <span data-ttu-id="22117-111">`Function`、`Sub`、`Property`、または `Event` ステートメントの末尾に `Implements` 句を追加します。</span><span class="sxs-lookup"><span data-stu-id="22117-111">Add an `Implements` clause to the end of the `Function`, `Sub`, `Property`, or `Event` statement.</span></span> <span data-ttu-id="22117-112">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="22117-112">For example:</span></span>  
  
    ```vb  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3. <span data-ttu-id="22117-113">プロパティを実装するときは、インターフェイス定義と同じ方法で `ReadOnly` または `WriteOnly` が使用されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="22117-113">When implementing a property, make sure that `ReadOnly` or `WriteOnly` is used in the same way as in the interface definition.</span></span>  
  
4. <span data-ttu-id="22117-114">プロパティを実装する場合は、必要に応じて `Get` および `Set` プロシージャを宣言します。</span><span class="sxs-lookup"><span data-stu-id="22117-114">When implementing a property, declare `Get` and `Set` procedures, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22117-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="22117-115">See also</span></span>

- [<span data-ttu-id="22117-116">Implements ステートメント</span><span class="sxs-lookup"><span data-stu-id="22117-116">Implements Statement</span></span>](../statements/implements-statement.md)
- [<span data-ttu-id="22117-117">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="22117-117">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
