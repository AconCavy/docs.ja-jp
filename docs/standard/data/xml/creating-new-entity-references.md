---
title: 新しいエンティティ参照の作成
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
ms.openlocfilehash: 8c81aae89bbe5979dffdc47a369349bd2b3f2df7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710987"
---
# <a name="creating-new-entity-references"></a><span data-ttu-id="f95cf-102">新しいエンティティ参照の作成</span><span class="sxs-lookup"><span data-stu-id="f95cf-102">Creating New Entity References</span></span>
<span data-ttu-id="f95cf-103">**CreateEntityReference** メソッドによって新しい **XmlEntityReference** ノードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="f95cf-103">The **CreateEntityReference** method creates a new **XmlEntityReference** node.</span></span> <span data-ttu-id="f95cf-104">XML ドキュメント オブジェクト モデル (DOM) は、参照されているエンティティ名が既に宣言されているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="f95cf-104">The XML Document Object Model (DOM) looks to see if the entity name being referenced has already been declared.</span></span> <span data-ttu-id="f95cf-105">宣言されている場合は、エンティティ宣言ノードから **XmlEntityReference** ノードの子ノードがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="f95cf-105">If it has, the child nodes of **XmlEntityReference** node are copied from the entity declaration node.</span></span> <span data-ttu-id="f95cf-106">一致するエンティティ宣言がない場合、エンティティ参照ノードには、唯一の子として空のテキスト ノードが追加されます。</span><span class="sxs-lookup"><span data-stu-id="f95cf-106">If there is no entity declaration that matches, an empty text node is attached as the only child of the entity reference node.</span></span> <span data-ttu-id="f95cf-107">**XmlEntityReference** ノードの子ノードは別のノードのコピーなので、これらの子ノードは読み取り専用になり、変更はできません。</span><span class="sxs-lookup"><span data-stu-id="f95cf-107">Because the child nodes of the **XmlEntityReference** node are copies of other nodes, these child nodes are read-only and cannot be modified.</span></span>  
  
 <span data-ttu-id="f95cf-108">ノードがコピーされるとき、そのエンティティ参照が存在する位置のスコープに、名前空間が適用されていることがあります。</span><span class="sxs-lookup"><span data-stu-id="f95cf-108">When the nodes are copied, there may be a namespace in scope at the point of the entity reference.</span></span> <span data-ttu-id="f95cf-109">生成される要素ノードまたは属性ノードの構成は、この名前空間の影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="f95cf-109">This namespace affects the configuration of any element or attribute nodes generated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f95cf-110">DOM は、ドキュメントに **EntityReference** ノードが挿入されたときだけ **EntityReference** に子ノードを追加します。</span><span class="sxs-lookup"><span data-stu-id="f95cf-110">The DOM adds child nodes to the **EntityReference** only when you insert the **EntityReference** node to the document.</span></span> <span data-ttu-id="f95cf-111">新しく作成された **EntityReference** ノードには、子ノードはありません。</span><span class="sxs-lookup"><span data-stu-id="f95cf-111">Newly created **EntityReference** nodes have no child nodes.</span></span>  
  
 <span data-ttu-id="f95cf-112">**XmlDataDocument** は **XmlDocument** の派生クラスですが、**XmlDataDocument** はエンティティ参照の作成をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="f95cf-112">Even though the **XmlDataDocument** is a derived class of the **XmlDocument**, the **XmlDataDocument** does not support the creation of entity references.</span></span> <span data-ttu-id="f95cf-113">**EntityReference** の子が読み取り専用であるためです。</span><span class="sxs-lookup"><span data-stu-id="f95cf-113">This is because **EntityReference** children are read-only.</span></span> <span data-ttu-id="f95cf-114">**EntityReference** ノードの子の範囲は、複数の領域にまたがることができます。</span><span class="sxs-lookup"><span data-stu-id="f95cf-114">The children of an **EntityReference** node can span more than one region.</span></span> <span data-ttu-id="f95cf-115">この場合は、**EntityReference** の一部を含む領域と関連付けられている行の部分が読み取り専用になります。</span><span class="sxs-lookup"><span data-stu-id="f95cf-115">In this case, part of a row associated with the region that contains a part of an **EntityReference** will be read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f95cf-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f95cf-116">See also</span></span>

- [<span data-ttu-id="f95cf-117">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="f95cf-117">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
