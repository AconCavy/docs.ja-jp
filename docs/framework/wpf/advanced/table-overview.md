---
title: テーブルの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flow content elements [WPF], Table
- documents [WPF], tables
- tables [WPF]
ms.assetid: 5e1105f4-8fc4-473a-ba55-88c8e71386e6
ms.openlocfilehash: fa7106207c69f19b647ba80ab7e724e9aad174c1
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005079"
---
# <a name="table-overview"></a><span data-ttu-id="6aca2-102">テーブルの概要</span><span class="sxs-lookup"><span data-stu-id="6aca2-102">Table Overview</span></span>
<span data-ttu-id="6aca2-103"><xref:System.Windows.Documents.Table> は、フロードキュメントコンテンツのグリッドベースの表現をサポートするブロックレベルの要素です。</span><span class="sxs-lookup"><span data-stu-id="6aca2-103"><xref:System.Windows.Documents.Table> is a block level element that supports grid-based presentation of Flow document content.</span></span> <span data-ttu-id="6aca2-104">この要素は、その柔軟性により非常に便利ですが、正しく理解して使用するのが難しいとも言えます。</span><span class="sxs-lookup"><span data-stu-id="6aca2-104">The flexibility of this element makes it very useful, but also makes it more complicated to understand and use correctly.</span></span>  
  
 <span data-ttu-id="6aca2-105">このトピックの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6aca2-105">This topic contains the following sections.</span></span>  
  
- [<span data-ttu-id="6aca2-106">テーブルの基本</span><span class="sxs-lookup"><span data-stu-id="6aca2-106">Table Basics</span></span>](#table_basics)  
  
- [<span data-ttu-id="6aca2-107">テーブルとグリッドの相違点</span><span class="sxs-lookup"><span data-stu-id="6aca2-107">How is Table Different then Grid?</span></span>](#table_vs_Grid)  
  
- [<span data-ttu-id="6aca2-108">テーブルの基本構造</span><span class="sxs-lookup"><span data-stu-id="6aca2-108">Basic Table Structure</span></span>](#basic_table_structure)  
  
- [<span data-ttu-id="6aca2-109">テーブルの内容</span><span class="sxs-lookup"><span data-stu-id="6aca2-109">Table Containment</span></span>](#table_containment)  
  
- [<span data-ttu-id="6aca2-110">行グループ</span><span class="sxs-lookup"><span data-stu-id="6aca2-110">Row Groupings</span></span>](#row_groupings)  
  
- [<span data-ttu-id="6aca2-111">背景のレンダリングの優先順位</span><span class="sxs-lookup"><span data-stu-id="6aca2-111">Background Rendering Precedence</span></span>](#rendering_precedence)  
  
- [<span data-ttu-id="6aca2-112">複数の行または列にまたがるセル</span><span class="sxs-lookup"><span data-stu-id="6aca2-112">Spanning Rows or Columns</span></span>](#spanning_rows_or_columns)  
  
- [<span data-ttu-id="6aca2-113">テーブルとコードのバインディング</span><span class="sxs-lookup"><span data-stu-id="6aca2-113">Building a Table With Code</span></span>](#building_a_table_with_code)  
  
- <span data-ttu-id="6aca2-114">関連トピック</span><span class="sxs-lookup"><span data-stu-id="6aca2-114">[Related Topics]</span></span> 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a><span data-ttu-id="6aca2-115">テーブルの基礎</span><span class="sxs-lookup"><span data-stu-id="6aca2-115">Table Basics</span></span>  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a><span data-ttu-id="6aca2-116">テーブルとグリッドの相違点</span><span class="sxs-lookup"><span data-stu-id="6aca2-116">How is Table Different then Grid?</span></span>  
 <span data-ttu-id="6aca2-117"><xref:System.Windows.Documents.Table> と <xref:System.Windows.Controls.Grid> はいくつかの一般的な機能を共有しますが、それぞれが異なるシナリオに最適です。</span><span class="sxs-lookup"><span data-stu-id="6aca2-117"><xref:System.Windows.Documents.Table> and <xref:System.Windows.Controls.Grid> share some common functionality, but each is best suited for different scenarios.</span></span> <span data-ttu-id="6aca2-118"><xref:System.Windows.Documents.Table> は、フローコンテンツ内で使用するように設計されています (フローコンテンツの詳細については、「[フロードキュメントの概要](flow-document-overview.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="6aca2-118">A <xref:System.Windows.Documents.Table> is designed for use within flow content (see [Flow Document Overview](flow-document-overview.md) for more information on flow content).</span></span> <span data-ttu-id="6aca2-119">グリッドは、フォーム内で最適に使用される (基本的に任意の場所以外のフロー コンテンツ)。</span><span class="sxs-lookup"><span data-stu-id="6aca2-119">Grids are best used inside of forms (basically anywhere outside of flow content).</span></span> <span data-ttu-id="6aca2-120"><xref:System.Windows.Documents.FlowDocument>内では、<xref:System.Windows.Documents.Table> は改ページ位置、列の折り返し、コンテンツの選択などのフローコンテンツの動作をサポートしていますが、<xref:System.Windows.Controls.Grid> ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="6aca2-120">Within a <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> supports flow content behaviors like pagination, column reflow, and content selection while a <xref:System.Windows.Controls.Grid> does not.</span></span> <span data-ttu-id="6aca2-121">一方、<xref:System.Windows.Controls.Grid> は <xref:System.Windows.Documents.FlowDocument> の外部で最もよく使用されます。たとえば、行インデックスと列インデックスに基づいて要素が追加される <xref:System.Windows.Controls.Grid> などですが、<xref:System.Windows.Documents.Table> はできません。</span><span class="sxs-lookup"><span data-stu-id="6aca2-121">A <xref:System.Windows.Controls.Grid> on the other hand is best used outside of a <xref:System.Windows.Documents.FlowDocument> for many reasons including <xref:System.Windows.Controls.Grid> adds elements based on a row and column index, <xref:System.Windows.Documents.Table> does not.</span></span> <span data-ttu-id="6aca2-122"><xref:System.Windows.Controls.Grid> 要素を使用すると、1つの "セル" 内に複数の要素を持つことができるように、子コンテンツをレイヤー化できます。</span><span class="sxs-lookup"><span data-stu-id="6aca2-122">The <xref:System.Windows.Controls.Grid> element allows layering of child content, allowing more than one element to exist within a single "cell."</span></span> <span data-ttu-id="6aca2-123"><xref:System.Windows.Documents.Table> は、レイヤーをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="6aca2-123"><xref:System.Windows.Documents.Table> does not support layering.</span></span> <span data-ttu-id="6aca2-124"><xref:System.Windows.Controls.Grid> の子要素は、"セル" の境界の領域を基準として絶対に配置できます。</span><span class="sxs-lookup"><span data-stu-id="6aca2-124">Child elements of a <xref:System.Windows.Controls.Grid> can be absolutely positioned relative to the area of their "cell" boundaries.</span></span> <span data-ttu-id="6aca2-125"><xref:System.Windows.Documents.Table> では、この機能はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="6aca2-125"><xref:System.Windows.Documents.Table> does not support this feature.</span></span> <span data-ttu-id="6aca2-126">最後に、<xref:System.Windows.Controls.Grid> に必要な <xref:System.Windows.Documents.Table> リソースが少なくなるため、パフォーマンスを向上させるために <xref:System.Windows.Controls.Grid> の使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="6aca2-126">Finally, a <xref:System.Windows.Controls.Grid> requires less resources then a <xref:System.Windows.Documents.Table> so consider using a <xref:System.Windows.Controls.Grid> to improve performance.</span></span>  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a><span data-ttu-id="6aca2-127">テーブルの基本構造</span><span class="sxs-lookup"><span data-stu-id="6aca2-127">Basic Table Structure</span></span>  
 <span data-ttu-id="6aca2-128"><xref:System.Windows.Documents.Table> には、列 (<xref:System.Windows.Documents.TableColumn> の要素で表される) と行 (<xref:System.Windows.Documents.TableRow> 要素で表される) で構成されるグリッドベースのプレゼンテーションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="6aca2-128"><xref:System.Windows.Documents.Table> provides a grid-based presentation consisting of columns (represented by <xref:System.Windows.Documents.TableColumn> elements) and rows (represented by <xref:System.Windows.Documents.TableRow> elements).</span></span> <span data-ttu-id="6aca2-129"><xref:System.Windows.Documents.TableColumn> 要素はコンテンツをホストしません。列および列の特性を定義するだけです。</span><span class="sxs-lookup"><span data-stu-id="6aca2-129"><xref:System.Windows.Documents.TableColumn> elements do not host content; they simply define columns and characteristics of columns.</span></span> <span data-ttu-id="6aca2-130"><xref:System.Windows.Documents.TableRow> の要素は、テーブルの行のグループ化を定義する <xref:System.Windows.Documents.TableRowGroup> 要素でホストされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="6aca2-130"><xref:System.Windows.Documents.TableRow> elements must be hosted in a <xref:System.Windows.Documents.TableRowGroup> element, which defines a grouping of rows for the table.</span></span> <span data-ttu-id="6aca2-131">テーブルによって表示される実際のコンテンツを含む <xref:System.Windows.Documents.TableCell> 要素は、<xref:System.Windows.Documents.TableRow> の要素でホストされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="6aca2-131"><xref:System.Windows.Documents.TableCell> elements, which contain the actual content to be presented by the table, must be hosted in a <xref:System.Windows.Documents.TableRow> element.</span></span> <span data-ttu-id="6aca2-132"><xref:System.Windows.Documents.TableCell> には、<xref:System.Windows.Documents.Block>から派生した要素のみを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="6aca2-132"><xref:System.Windows.Documents.TableCell> may only contain elements that derive from <xref:System.Windows.Documents.Block>.</span></span>  <span data-ttu-id="6aca2-133"><xref:System.Windows.Documents.TableCell> の有効な子要素にはが含まれます。</span><span class="sxs-lookup"><span data-stu-id="6aca2-133">Valid child elements for a <xref:System.Windows.Documents.TableCell> include.</span></span>  
  
- <xref:System.Windows.Documents.BlockUIContainer>  
  
- <xref:System.Windows.Documents.List>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
> <span data-ttu-id="6aca2-134"><xref:System.Windows.Documents.TableCell> 要素は、テキストコンテンツを直接ホストすることはできません。</span><span class="sxs-lookup"><span data-stu-id="6aca2-134"><xref:System.Windows.Documents.TableCell> elements may not directly host text content.</span></span> <span data-ttu-id="6aca2-135"><xref:System.Windows.Documents.TableCell>のようなフローコンテンツ要素の含有規則の詳細については、「[フロードキュメントの概要](flow-document-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6aca2-135">For more information about the containment rules for flow content elements like <xref:System.Windows.Documents.TableCell>, see [Flow Document Overview](flow-document-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6aca2-136"><xref:System.Windows.Documents.Table> は <xref:System.Windows.Controls.Grid> 要素に似ていますが、より多くの機能を備えているため、リソースのオーバーヘッドが大きくなります。</span><span class="sxs-lookup"><span data-stu-id="6aca2-136"><xref:System.Windows.Documents.Table> is similar to the <xref:System.Windows.Controls.Grid> element but has more capabilities and, therefore, requires greater resource overhead.</span></span>  
  
 <span data-ttu-id="6aca2-137">次の例では、XAML を使用して単純な 2 x 3 テーブルを定義します。</span><span class="sxs-lookup"><span data-stu-id="6aca2-137">The following example defines a simple 2 x 3 table with XAML.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 <span data-ttu-id="6aca2-138">この例の表示結果を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="6aca2-138">The following figure shows how this example renders.</span></span>  
  
 ![基本的なテーブルのレンダリング方法を示すスクリーンショット。](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a><span data-ttu-id="6aca2-140">テーブルの内容</span><span class="sxs-lookup"><span data-stu-id="6aca2-140">Table Containment</span></span>  
 <span data-ttu-id="6aca2-141"><xref:System.Windows.Documents.Table> は <xref:System.Windows.Documents.Block> 要素から派生し、<xref:System.Windows.Documents.Block> レベルの要素の一般的な規則に従います。</span><span class="sxs-lookup"><span data-stu-id="6aca2-141"><xref:System.Windows.Documents.Table> derives from the <xref:System.Windows.Documents.Block> element, and adheres to the common rules for <xref:System.Windows.Documents.Block> level elements.</span></span>  <span data-ttu-id="6aca2-142"><xref:System.Windows.Documents.Table> 要素は、次のいずれかの要素に含めることができます。</span><span class="sxs-lookup"><span data-stu-id="6aca2-142">A <xref:System.Windows.Documents.Table> element may be contained by any of the following elements:</span></span>  
  
- <xref:System.Windows.Documents.FlowDocument>  
  
- <xref:System.Windows.Documents.TableCell>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a><span data-ttu-id="6aca2-143">行グループ</span><span class="sxs-lookup"><span data-stu-id="6aca2-143">Row Groupings</span></span>  
 <span data-ttu-id="6aca2-144"><xref:System.Windows.Documents.TableRowGroup> 要素は、テーブル内の任意の行を任意にグループ化する方法を提供します。テーブル内のすべての行は、行グループに属している必要があります。</span><span class="sxs-lookup"><span data-stu-id="6aca2-144">The <xref:System.Windows.Documents.TableRowGroup> element provides a way to arbitrarily group rows within a table; every row in a table must belong to a row grouping.</span></span>  <span data-ttu-id="6aca2-145">多くの場合、行グループ内の行は共通の目的を共有しており、1 つのグループとしてスタイルを設定できます。</span><span class="sxs-lookup"><span data-stu-id="6aca2-145">Rows within a row group often share a common intent, and may be styled as a group.</span></span>  <span data-ttu-id="6aca2-146">一般に、行のグループ化は、テーブルに格納された主要コンテンツから、特別な目的を持つ行 (タイトル行、ヘッダー行、フッター行など) を分離するために使用します。</span><span class="sxs-lookup"><span data-stu-id="6aca2-146">A common use for row groupings is to separate special-purpose rows, such as a title, header, and footer rows, from the primary content contained by the table.</span></span>  
  
 <span data-ttu-id="6aca2-147">次の例では、XAML を使用して、スタイルが設定されたヘッダー行とフッター行を含むテーブルを定義します。</span><span class="sxs-lookup"><span data-stu-id="6aca2-147">The following example uses XAML to define a table with styled header and footer rows.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 <span data-ttu-id="6aca2-148">この例の表示結果を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="6aca2-148">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="6aca2-149">![スクリーンショット: テーブル行グループ](./media/table-rowgroups.png "Table_RowGroups")</span><span class="sxs-lookup"><span data-stu-id="6aca2-149">![Screenshot: Table row groups](./media/table-rowgroups.png "Table_RowGroups")</span></span>  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a><span data-ttu-id="6aca2-150">背景のレンダリングの優先順位</span><span class="sxs-lookup"><span data-stu-id="6aca2-150">Background Rendering Precedence</span></span>  
 <span data-ttu-id="6aca2-151">テーブル要素は、次の順序でレンダリングされます (優先順位の低い項目から高い項目の z オーダー)。</span><span class="sxs-lookup"><span data-stu-id="6aca2-151">Table elements render in the following order (z-order from lowest to highest).</span></span> <span data-ttu-id="6aca2-152">この順序は変更できません。</span><span class="sxs-lookup"><span data-stu-id="6aca2-152">This order cannot be changed.</span></span> <span data-ttu-id="6aca2-153">たとえば、これらの要素には、確立された順序をオーバーライドするための "Z オーダー" プロパティは用意されていません。</span><span class="sxs-lookup"><span data-stu-id="6aca2-153">For example, there is no "Z-order" property for these elements that you can use to override this established order.</span></span>  
  
1. <xref:System.Windows.Documents.Table>  
  
2. <xref:System.Windows.Documents.TableColumn>  
  
3. <xref:System.Windows.Documents.TableRowGroup>  
  
4. <xref:System.Windows.Documents.TableRow>  
  
5. <xref:System.Windows.Documents.TableCell>  
  
 <span data-ttu-id="6aca2-154">テーブル内のこれらの各要素に対して背景色を定義する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6aca2-154">Consider the following example, which defines background colors for each of these elements within a table.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 <span data-ttu-id="6aca2-155">次の図は、この例の表示結果 (背景色のみ表示) を示したものです。</span><span class="sxs-lookup"><span data-stu-id="6aca2-155">The following figure shows how this example renders (showing background colors only).</span></span>  
  
 <span data-ttu-id="6aca2-156">![スクリーンショット: テーブル z オーダー](./media/table-zorder.png "Table_ZOrder")</span><span class="sxs-lookup"><span data-stu-id="6aca2-156">![Screenshot: Table z&#45;order](./media/table-zorder.png "Table_ZOrder")</span></span>  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a><span data-ttu-id="6aca2-157">複数の行または列にまたがるセル</span><span class="sxs-lookup"><span data-stu-id="6aca2-157">Spanning Rows or Columns</span></span>  
 <span data-ttu-id="6aca2-158">テーブルセルは、<xref:System.Windows.Documents.TableCell.RowSpan%2A> または <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> 属性をそれぞれ使用して、複数の行または列にまたがるように構成できます。</span><span class="sxs-lookup"><span data-stu-id="6aca2-158">Table cells may be configured to span multiple rows or columns by using the <xref:System.Windows.Documents.TableCell.RowSpan%2A> or <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> attributes, respectively.</span></span>  
  
 <span data-ttu-id="6aca2-159">3 つの列にまたがるセルの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6aca2-159">Consider the following example, in which a cell spans three columns.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 <span data-ttu-id="6aca2-160">この例の表示結果を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="6aca2-160">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="6aca2-161">![スクリーンショット: 3 つの列すべてにまたがるセル](./media/table-columnspan.png "Table_ColumnSpan")</span><span class="sxs-lookup"><span data-stu-id="6aca2-161">![Screenshot: Cell spanning all three columns](./media/table-columnspan.png "Table_ColumnSpan")</span></span>  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a><span data-ttu-id="6aca2-162">テーブルとコードのバインディング</span><span class="sxs-lookup"><span data-stu-id="6aca2-162">Building a Table With Code</span></span>  
 <span data-ttu-id="6aca2-163">次の例では、プログラムを使用して <xref:System.Windows.Documents.Table> を作成し、コンテンツを設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6aca2-163">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="6aca2-164">テーブルの内容は、5つの行 (<xref:System.Windows.Documents.Table.RowGroups%2A> オブジェクトに含まれる <xref:System.Windows.Documents.TableRow> オブジェクトによって表されます) と6つの列 (<xref:System.Windows.Documents.TableColumn> オブジェクトで表される) に分配されます。</span><span class="sxs-lookup"><span data-stu-id="6aca2-164">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="6aca2-165">行はさまざまな表示目的で利用されます。たとえば、テーブル全体にタイトルを付けるタイトル行、テーブル内のデータの列を表すヘッダー行、まとめ情報が入るフッター行があります。</span><span class="sxs-lookup"><span data-stu-id="6aca2-165">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="6aca2-166">"タイトル" 行、"ヘッダー" 行、"フッター" 行という概念はテーブルに固有のものではありません。特性が異なる行にすぎません。</span><span class="sxs-lookup"><span data-stu-id="6aca2-166">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="6aca2-167">テーブルのセルには実際のコンテンツが含まれます。これは、テキスト、画像、またはその他の [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 要素で構成できます。</span><span class="sxs-lookup"><span data-stu-id="6aca2-167">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
 <span data-ttu-id="6aca2-168">まず、<xref:System.Windows.Documents.Table>をホストする <xref:System.Windows.Documents.FlowDocument> が作成され、新しい <xref:System.Windows.Documents.Table> が作成され、<xref:System.Windows.Documents.FlowDocument>の内容に追加されます。</span><span class="sxs-lookup"><span data-stu-id="6aca2-168">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 <span data-ttu-id="6aca2-169">次に、いくつかの書式設定を適用して、6つの <xref:System.Windows.Documents.TableColumn> オブジェクトが作成され、テーブルの <xref:System.Windows.Documents.Table.Columns%2A> コレクションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="6aca2-169">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6aca2-170">テーブルの <xref:System.Windows.Documents.Table.Columns%2A> コレクションでは、0から始まる標準のインデックス作成が使用されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6aca2-170">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 <span data-ttu-id="6aca2-171">次に、タイトル行が作成され、テーブルに追加されます。いくつかの書式設定が適用されます。</span><span class="sxs-lookup"><span data-stu-id="6aca2-171">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="6aca2-172">タイトル行には、テーブルの 6 つの列にまたがる 1 つのセルが格納されます。</span><span class="sxs-lookup"><span data-stu-id="6aca2-172">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 <span data-ttu-id="6aca2-173">次に、ヘッダー行が作成され、テーブルに追加されます。ヘッダー行のセルが作成され、内容が入力されます。</span><span class="sxs-lookup"><span data-stu-id="6aca2-173">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 <span data-ttu-id="6aca2-174">次に、データの行が作成され、テーブルに追加されます。この行のセルが作成され、内容が入力されます。</span><span class="sxs-lookup"><span data-stu-id="6aca2-174">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="6aca2-175">この行の作成はヘッダー行の作成に似ていますが、適用する書式が少し異なります。</span><span class="sxs-lookup"><span data-stu-id="6aca2-175">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 <span data-ttu-id="6aca2-176">最後に、フッター行が作成され、追加され、書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="6aca2-176">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="6aca2-177">タイトル行と同様に、フッター行にはテーブルの 6 つの列にまたがる 1 つのセルが格納されます。</span><span class="sxs-lookup"><span data-stu-id="6aca2-177">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="6aca2-178">参照</span><span class="sxs-lookup"><span data-stu-id="6aca2-178">See also</span></span>

- [<span data-ttu-id="6aca2-179">フロー ドキュメントの概要</span><span class="sxs-lookup"><span data-stu-id="6aca2-179">Flow Document Overview</span></span>](flow-document-overview.md)
- [<span data-ttu-id="6aca2-180">XAML を使用してテーブルを定義する</span><span class="sxs-lookup"><span data-stu-id="6aca2-180">Define a Table with XAML</span></span>](how-to-define-a-table-with-xaml.md)
- [<span data-ttu-id="6aca2-181">WPF のドキュメント</span><span class="sxs-lookup"><span data-stu-id="6aca2-181">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="6aca2-182">フロー コンテンツ要素を使用する</span><span class="sxs-lookup"><span data-stu-id="6aca2-182">Use Flow Content Elements</span></span>](how-to-use-flow-content-elements.md)
