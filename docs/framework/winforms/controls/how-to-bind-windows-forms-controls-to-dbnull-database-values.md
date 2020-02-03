---
title: コントロールを DBNull データベース値にバインドする
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
ms.openlocfilehash: 175d7f5aee2540916480e2c55a485af1f9d16653
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746668"
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a><span data-ttu-id="7e52b-102">方法 : Windows フォーム コントロールを DBNull データベース値にバインドする</span><span class="sxs-lookup"><span data-stu-id="7e52b-102">How to: Bind Windows Forms Controls to DBNull Database Values</span></span>
<span data-ttu-id="7e52b-103">データ ソースに Windows フォーム コントロールをバインドして、データ ソースが <xref:System.DBNull> 値を返す場合、イベントの処理、書式設定、または解析なしで、適切な値に置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="7e52b-103">When you bind Windows Forms controls to a data source and the data source returns a <xref:System.DBNull> value, you can substitute an appropriate value without handling, formatting, or parsing events.</span></span> <span data-ttu-id="7e52b-104"><xref:System.Windows.Forms.Binding.NullValue%2A> プロパティは、データ ソースの値を書式設定または解析する際、<xref:System.DBNull> を指定されたオブジェクトに変換します。</span><span class="sxs-lookup"><span data-stu-id="7e52b-104">The <xref:System.Windows.Forms.Binding.NullValue%2A> property will convert <xref:System.DBNull> to a specified object when formatting or parsing the data source values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e52b-105">例</span><span class="sxs-lookup"><span data-stu-id="7e52b-105">Example</span></span>  
 <span data-ttu-id="7e52b-106">次の例では、2 つの異なる状況で <xref:System.DBNull> の値をバインドする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="7e52b-106">The following example demonstrates how to bind a <xref:System.DBNull> value in two different situations.</span></span> <span data-ttu-id="7e52b-107">1 つ目は、文字列のプロパティに対して <xref:System.Windows.Forms.Binding.NullValue%2A> を設定する方法を示し、2 つ目は、イメージのプロパティに対して <xref:System.Windows.Forms.Binding.NullValue%2A> を設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7e52b-107">The first demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for a string property; the second demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for an image property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 <span data-ttu-id="7e52b-108">バインドされたプロパティの種類と <xref:System.Windows.Forms.Binding.NullValue%2A> プロパティは同じにする必要があります。そうでないとエラーが発生し、<xref:System.Windows.Forms.Binding.NullValue%2A> の値はそれ以上処理されません。</span><span class="sxs-lookup"><span data-stu-id="7e52b-108">The types of the bound property and the <xref:System.Windows.Forms.Binding.NullValue%2A> property must be the same or an error will result, and no further <xref:System.Windows.Forms.Binding.NullValue%2A> values will be processed.</span></span> <span data-ttu-id="7e52b-109">このような場合は、例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="7e52b-109">In this situation, an exception will not be thrown.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7e52b-110">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="7e52b-110">Compiling the Code</span></span>  
 <span data-ttu-id="7e52b-111">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7e52b-111">This example requires:</span></span>  
  
- <span data-ttu-id="7e52b-112">System、System.Data、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="7e52b-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e52b-113">参照</span><span class="sxs-lookup"><span data-stu-id="7e52b-113">See also</span></span>

- [<span data-ttu-id="7e52b-114">BindingSource コンポーネント</span><span class="sxs-lookup"><span data-stu-id="7e52b-114">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="7e52b-115">方法: データ バインドで発生するエラーと例外を処理する</span><span class="sxs-lookup"><span data-stu-id="7e52b-115">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
- [<span data-ttu-id="7e52b-116">方法: Windows フォーム コントロールを型にバインドする</span><span class="sxs-lookup"><span data-stu-id="7e52b-116">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
