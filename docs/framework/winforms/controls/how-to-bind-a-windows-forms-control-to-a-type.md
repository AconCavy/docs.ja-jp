---
title: コントロールを型にバインドする
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 94faeebb-d2bc-45d6-86d7-96a42661b43d
ms.openlocfilehash: 0bc1f92ee8922990bd0e461655168f5618ba39a6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744992"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type"></a><span data-ttu-id="7e258-102">方法 : Windows フォーム コントロールを型にバインドする</span><span class="sxs-lookup"><span data-stu-id="7e258-102">How to: Bind a Windows Forms Control to a Type</span></span>
<span data-ttu-id="7e258-103">データをやり取りするコントロールを作成する際、オブジェクトではなく型にコントロールをバインドすることが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="7e258-103">When you are building controls that interact with data, you will sometimes find it necessary to bind a control to a type, rather than an object.</span></span> <span data-ttu-id="7e258-104">このような状況は、特にデータを使用できないデザイン時に発生しますが、データ バインド コントロールは、型のパブリック インターフェイスから情報を表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e258-104">This situation arises especially at design time, when data may not be available, but your data-bound controls still need to display information from a type's public interface.</span></span> <span data-ttu-id="7e258-105">たとえば、<xref:System.Windows.Forms.DataGridView> コントロールを Web サービスによって公開されているオブジェクトにバインドし、デザイン時に <xref:System.Windows.Forms.DataGridView> コントロールで列にカスタム型のメンバー名のラベルを付けたいときがあります。</span><span class="sxs-lookup"><span data-stu-id="7e258-105">For example, you may bind a <xref:System.Windows.Forms.DataGridView> control to an object exposed by a Web service and want the <xref:System.Windows.Forms.DataGridView> control to label its columns at design time with the member names of a custom type.</span></span>  
  
 <span data-ttu-id="7e258-106"><xref:System.Windows.Forms.BindingSource> コンポーネントを使用して、コントロールを型に簡単にバインドできます。</span><span class="sxs-lookup"><span data-stu-id="7e258-106">You can easily bind a control to a type with the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e258-107">使用例</span><span class="sxs-lookup"><span data-stu-id="7e258-107">Example</span></span>  
 <span data-ttu-id="7e258-108">次のサンプル コードは、<xref:System.Windows.Forms.BindingSource> コンポーネントを使用して、<xref:System.Windows.Forms.DataGridView> コントロールをカスタム型にバインドする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7e258-108">The following code example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a custom type by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="7e258-109">例を実行すると、コントロールにデータを設定する前に、<xref:System.Windows.Forms.DataGridView> に `Customer` オブジェクトのプロパティを反映するラベルが付いた列があることに気付きます。</span><span class="sxs-lookup"><span data-stu-id="7e258-109">When you run the example, you'll notice the <xref:System.Windows.Forms.DataGridView> has labeled columns that reflect the properties of a `Customer` object, before the control is populated with data.</span></span> <span data-ttu-id="7e258-110">この例には、データを <xref:System.Windows.Forms.DataGridView> コントロールに追加する [顧客の追加] ボタンがあります。</span><span class="sxs-lookup"><span data-stu-id="7e258-110">The example has an Add Customer button to add data to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="7e258-111">ボタンをクリックすると、新しい `Customer` オブジェクトが <xref:System.Windows.Forms.BindingSource> に追加されます。</span><span class="sxs-lookup"><span data-stu-id="7e258-111">When you click the button, a new `Customer` object is added to the <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="7e258-112">実際のシナリオでは、Web サービスまたはその他のデータ ソースへの呼び出しにより、データを取得する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7e258-112">In a real-world scenario, the data might be obtained by a call to a Web service or other data source.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7e258-113">コードのコンパイル方法</span><span class="sxs-lookup"><span data-stu-id="7e258-113">Compiling the Code</span></span>  
 <span data-ttu-id="7e258-114">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7e258-114">This example requires:</span></span>  
  
- <span data-ttu-id="7e258-115">System アセンブリおよび System.Windows.Forms アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="7e258-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e258-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="7e258-116">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="7e258-117">BindingSource コンポーネント</span><span class="sxs-lookup"><span data-stu-id="7e258-117">BindingSource Component</span></span>](bindingsource-component.md)
