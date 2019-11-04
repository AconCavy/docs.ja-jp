---
title: '方法 : バインディングの検証の実装'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
ms.openlocfilehash: 245b05d9cfa7ca66dec310bd9a5291def0101d19
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459110"
---
# <a name="how-to-implement-binding-validation"></a><span data-ttu-id="a2312-102">方法 : バインディングの検証の実装</span><span class="sxs-lookup"><span data-stu-id="a2312-102">How to: Implement Binding Validation</span></span>

<span data-ttu-id="a2312-103">この例では、カスタム検証規則に基づいて、<xref:System.Windows.Controls.Validation.ErrorTemplate%2A> とスタイルトリガーを使用して、無効な値が入力されたときにユーザーに通知するための視覚的なフィードバックを提供する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a2312-103">This example shows how to use an <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> and a style trigger to provide visual feedback to inform the user when an invalid value is entered, based on a custom validation rule.</span></span>

## <a name="example"></a><span data-ttu-id="a2312-104">例</span><span class="sxs-lookup"><span data-stu-id="a2312-104">Example</span></span>

<span data-ttu-id="a2312-105">次の例の <xref:System.Windows.Controls.TextBox> のテキストコンテンツは、`ods`という名前のバインディングソースオブジェクトの `Age` プロパティ (int 型) にバインドされています。</span><span class="sxs-lookup"><span data-stu-id="a2312-105">The text content of the <xref:System.Windows.Controls.TextBox> in the following example is bound to the `Age` property (of type int) of a binding source object named `ods`.</span></span> <span data-ttu-id="a2312-106">バインディングは、`AgeRangeRule` という名前の検証規則を使用するよう設定されているため、ユーザーが数字以外の文字、または 21 から 130 の範囲外の値を入力すると、テキスト ボックスの横に赤の感嘆符が表示され、ユーザーがテキスト ボックス上にマウスを置くとエラー メッセージを含んだツール ヒントが示されます。</span><span class="sxs-lookup"><span data-stu-id="a2312-106">The binding is set up to use a validation rule named `AgeRangeRule` so that if the user enters non-numeric characters or a value that is smaller than 21 or greater than 130, a red exclamation mark appears next to the text box and a tool tip with the error message appears when the user moves the mouse over the text box.</span></span>

[!code-xaml[BindValidation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]

<span data-ttu-id="a2312-107">次の例は、<xref:System.Windows.Controls.ValidationRule> から継承し、<xref:System.Windows.Controls.ValidationRule.Validate%2A> メソッドをオーバーライドする `AgeRangeRule`の実装を示しています。</span><span class="sxs-lookup"><span data-stu-id="a2312-107">The following example shows the implementation of `AgeRangeRule`, which inherits from <xref:System.Windows.Controls.ValidationRule> and overrides the <xref:System.Windows.Controls.ValidationRule.Validate%2A> method.</span></span> <span data-ttu-id="a2312-108">`Int32.Parse` メソッドは、無効な文字が含まれていないことを確認するために、値に対して呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a2312-108">The `Int32.Parse` method is called on the value to make sure that it does not contain any invalid characters.</span></span> <span data-ttu-id="a2312-109"><xref:System.Windows.Controls.ValidationRule.Validate%2A> メソッドは、解析中に例外がキャッチされたかどうか、および age 値が下限と上限の範囲外であるかどうかに基づいて、値が有効かどうかを示す <xref:System.Windows.Controls.ValidationResult> を返します。</span><span class="sxs-lookup"><span data-stu-id="a2312-109">The <xref:System.Windows.Controls.ValidationRule.Validate%2A> method returns a <xref:System.Windows.Controls.ValidationResult> that indicates if the value is valid based on whether an exception is caught during the parsing and whether the age value is outside of the lower and upper bounds.</span></span>

[!code-csharp[BindValidation#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]
[!code-vb[BindValidation#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindValidation/VisualBasic/AgeRangeRule.vb#3)]

<span data-ttu-id="a2312-110">次の例は、ユーザーに検証エラーを通知する赤色の感嘆符を作成するカスタム <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` を示しています。</span><span class="sxs-lookup"><span data-stu-id="a2312-110">The following example shows the custom <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` that creates a red exclamation mark to notify the user of a validation error.</span></span> <span data-ttu-id="a2312-111">コントロール テンプレートは、コントロールの外観を再定義するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="a2312-111">Control templates are used to redefine the appearance of a control.</span></span>

[!code-xaml[BindValidation#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]

<span data-ttu-id="a2312-112">次の例に示すように、エラーメッセージを示す <xref:System.Windows.Controls.ToolTip> は `textBoxInError`という名前のスタイルを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="a2312-112">As shown in the following example, the <xref:System.Windows.Controls.ToolTip> that shows the error message is created using the style named `textBoxInError`.</span></span> <span data-ttu-id="a2312-113"><xref:System.Windows.Controls.Validation.HasError%2A> の値が `true`場合、トリガーにより、現在の <xref:System.Windows.Controls.TextBox> のツールヒントが最初の検証エラーに設定されます。</span><span class="sxs-lookup"><span data-stu-id="a2312-113">If the value of <xref:System.Windows.Controls.Validation.HasError%2A> is `true`, the trigger sets the tool tip of the current <xref:System.Windows.Controls.TextBox> to its first validation error.</span></span> <span data-ttu-id="a2312-114"><xref:System.Windows.Data.Binding.RelativeSource%2A> は <xref:System.Windows.Data.RelativeSourceMode.Self>に設定され、現在の要素を参照しています。</span><span class="sxs-lookup"><span data-stu-id="a2312-114">The <xref:System.Windows.Data.Binding.RelativeSource%2A> is set to <xref:System.Windows.Data.RelativeSourceMode.Self>, referring to the current element.</span></span>

[!code-xaml[BindValidation#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]

<span data-ttu-id="a2312-115">完全な例については、「[バインドの検証のサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2312-115">For the complete example, see [Bind Validation sample](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).</span></span>
  
<span data-ttu-id="a2312-116">カスタム <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> を指定しない場合、検証エラーが発生したときにユーザーに視覚的なフィードバックを提供するために、既定のエラーテンプレートが表示されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a2312-116">Note that if you do not provide a custom <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> the default error template appears to provide visual feedback to the user when there is a validation error.</span></span> <span data-ttu-id="a2312-117">詳しくは、「[データ バインドの概要](../../../desktop-wpf/data/data-binding-overview.md)」の「データの検証」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a2312-117">See "Data Validation" in [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md) for more information.</span></span> <span data-ttu-id="a2312-118">さらに [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、バインディング ソース プロパティの更新中にスローされる例外をキャッチするための、組み込みの検証規則を提供します。</span><span class="sxs-lookup"><span data-stu-id="a2312-118">Also, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provides a built-in validation rule that catches exceptions that are thrown during the update of the binding source property.</span></span> <span data-ttu-id="a2312-119">詳細については、「<xref:System.Windows.Controls.ExceptionValidationRule>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2312-119">For more information, see <xref:System.Windows.Controls.ExceptionValidationRule>.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2312-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="a2312-120">See also</span></span>

- [<span data-ttu-id="a2312-121">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="a2312-121">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="a2312-122">方法トピック</span><span class="sxs-lookup"><span data-stu-id="a2312-122">How-to Topics</span></span>](data-binding-how-to-topics.md)
