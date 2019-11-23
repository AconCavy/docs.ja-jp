---
title: UI オートメーションを使用して混合テキスト属性の詳細を取得する
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d0e4c005-abd1-42bb-92a4-5faf87097311
ms.openlocfilehash: 9f2cba1f602cedf3a13bd909b4dc2f1a7b4ab972
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443121"
---
# <a name="obtain-mixed-text-attribute-details-using-ui-automation"></a><span data-ttu-id="d7390-102">UI オートメーションを使用して混合テキスト属性の詳細を取得する</span><span class="sxs-lookup"><span data-stu-id="d7390-102">Obtain Mixed Text Attribute Details Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="d7390-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="d7390-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d7390-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](/windows/win32/winauto/entry-uiauto-win32)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7390-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="d7390-105">このトピックでは、 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] を使用して、複数の属性値にまたがるテキスト範囲からテキスト属性の詳細を取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d7390-105">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to obtain text attribute details from a text range that spans multiple attribute values.</span></span> <span data-ttu-id="d7390-106">テキスト範囲は、ドキュメント内のキャレットの現在の位置 (または低次元選択)、テキストの連続した選択、非連続のテキスト選択のコレクション、またはドキュメントのテキスト コンテンツ全体に対応します。</span><span class="sxs-lookup"><span data-stu-id="d7390-106">A text range can correspond to the current location of the caret (or degenerate selection) within a document, a contiguous selection of text, a collection of disjoint text selections, or the entire textual content of a document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7390-107">例</span><span class="sxs-lookup"><span data-stu-id="d7390-107">Example</span></span>  
 <span data-ttu-id="d7390-108">次のコード例は、 <xref:System.Windows.Automation.TextPattern.FontNameAttribute> が <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> オブジェクトを返すテキスト範囲から <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> を取得する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d7390-108">The following code example demonstrates how to obtain the <xref:System.Windows.Automation.TextPattern.FontNameAttribute> from a text range where <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> returns a <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> object.</span></span>  
  
[!code-csharp[FindText#RetrieveMixedAttributes](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#retrievemixedattributes)]
[!code-vb[FindText#RetrieveMixedAttributes](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#retrievemixedattributes)]  
  
 <span data-ttu-id="d7390-109"><xref:System.Windows.Automation.TextPattern> コントロール パターンは <xref:System.Windows.Automation.Text.TextPatternRange> クラスと連携して、基本のテキスト属性、プロパティ、メソッドをサポートします。</span><span class="sxs-lookup"><span data-stu-id="d7390-109">The <xref:System.Windows.Automation.TextPattern> control pattern, in tandem with the <xref:System.Windows.Automation.Text.TextPatternRange> class, supports basic text attributes, properties, and methods.</span></span> <span data-ttu-id="d7390-110"><xref:System.Windows.Automation.TextPattern> または <xref:System.Windows.Automation.Text.TextPatternRange>によってサポートされないコントロール固有の機能の場合、UI オートメーション クライアントが対応するネイティブ オブジェクト モデルにアクセスできるように、 <xref:System.Windows.Automation.AutomationElement> クラスがメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="d7390-110">For control-specific functionality that is not supported by <xref:System.Windows.Automation.TextPattern> or <xref:System.Windows.Automation.Text.TextPatternRange>, the <xref:System.Windows.Automation.AutomationElement> class provides methods for a UI Automation client to access the corresponding native object model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7390-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="d7390-111">See also</span></span>

- [<span data-ttu-id="d7390-112">UI オートメーション TextPattern の概要</span><span class="sxs-lookup"><span data-stu-id="d7390-112">UI Automation TextPattern Overview</span></span>](ui-automation-textpattern-overview.md)
- [<span data-ttu-id="d7390-113">UI オートメーションを使用した、テキスト ボックスへのコンテンツの追加</span><span class="sxs-lookup"><span data-stu-id="d7390-113">Add Content to a Text Box Using UI Automation</span></span>](add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="d7390-114">UI オートメーションを使用した、テキストの検索と強調表示</span><span class="sxs-lookup"><span data-stu-id="d7390-114">Find and Highlight Text Using UI Automation</span></span>](find-and-highlight-text-using-ui-automation.md)
- [<span data-ttu-id="d7390-115">UI Automation コントロール パターンの概要</span><span class="sxs-lookup"><span data-stu-id="d7390-115">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="d7390-116">クライアントの UI オートメーション コントロール パターン</span><span class="sxs-lookup"><span data-stu-id="d7390-116">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="d7390-117">UI オートメーションを使用してテキスト属性を取得する</span><span class="sxs-lookup"><span data-stu-id="d7390-117">Obtain Text Attributes Using UI Automation</span></span>](obtain-text-attributes-using-ui-automation.md)
