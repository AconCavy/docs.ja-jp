---
title: <interfacename>.<membername>' は、基本クラス '<baseclassname>' によって既に実装されています。 <type> の再実装と見なされます。
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 4056c61bf6556f54276817c1c105ba7a17b6fd5a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873945"
---
# <a name="interfacenamemembername-is-already-implemented-by-the-base-class-baseclassname-re-implementation-of-type-assumed"></a><span data-ttu-id="97fe7-103">\<interfacename>.\<membername>' は、基本クラス '\<baseclassname>' によって既に実装されています。</span><span class="sxs-lookup"><span data-stu-id="97fe7-103">'\<interfacename>.\<membername>' is already implemented by the base class '\<baseclassname>'.</span></span> <span data-ttu-id="97fe7-104">\<type> の再実装と見なされます。</span><span class="sxs-lookup"><span data-stu-id="97fe7-104">Re-implementation of \<type> assumed</span></span>

<span data-ttu-id="97fe7-105">派生クラスのプロパティ、プロシージャ、またはイベントで `Implements` 句を使用し、基底クラスに既に実装されている派生インターフェイス メンバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="97fe7-105">A property, procedure, or event in a derived class uses an `Implements` clause specifying an interface member that is already implemented in the base class.</span></span>  
  
 <span data-ttu-id="97fe7-106">派生クラスでは、その基底クラスによって実装されているインターフェイス メンバーを再実装できます。</span><span class="sxs-lookup"><span data-stu-id="97fe7-106">A derived class can reimplement an interface member that is implemented by its base class.</span></span> <span data-ttu-id="97fe7-107">このことは、基底クラスの実装をオーバーライドすることとは異なります。</span><span class="sxs-lookup"><span data-stu-id="97fe7-107">This is not the same as overriding the base class implementation.</span></span> <span data-ttu-id="97fe7-108">詳細については、「 [Implements](../statements/implements-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="97fe7-108">For more information, see [Implements](../statements/implements-clause.md).</span></span>  
  
 <span data-ttu-id="97fe7-109">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="97fe7-109">By default, this message is a warning.</span></span> <span data-ttu-id="97fe7-110">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="97fe7-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="97fe7-111">**エラー ID:** BC42015</span><span class="sxs-lookup"><span data-stu-id="97fe7-111">**Error ID:** BC42015</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="97fe7-112">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="97fe7-112">To correct this error</span></span>  
  
- <span data-ttu-id="97fe7-113">インターフェイス メンバーを再実装する場合は、操作を行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="97fe7-113">If you intend to reimplement the interface member, you do not need to take any action.</span></span> <span data-ttu-id="97fe7-114">派生クラスのコードでは、`MyBase` キーワードを使用して基底クラスの実装にアクセスしない限り、再実装されたメンバーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="97fe7-114">Code in your derived class accesses the reimplemented member unless you use the `MyBase` keyword to access the base class implementation.</span></span>  
  
- <span data-ttu-id="97fe7-115">インターフェイス メンバーを再実装しない場合は、プロパティ、プロシージャ、またはイベント宣言から、 `Implements` 句を削除します。</span><span class="sxs-lookup"><span data-stu-id="97fe7-115">If you do not intend to reimplement the interface member, remove the `Implements` clause from the property, procedure, or event declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97fe7-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="97fe7-116">See also</span></span>

- [<span data-ttu-id="97fe7-117">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="97fe7-117">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
