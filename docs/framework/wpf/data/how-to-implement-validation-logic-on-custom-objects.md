---
title: '方法: カスタム オブジェクトに検証ロジックを実装する'
ms.date: 08/02/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- checking for validation errors [WPF]
- validation errors [WPF], checking for
- implementing validation logic on custom objects [WPF]
- custom objects [WPF], implementing validation logic on
ms.assetid: 751fda9b-44f9-4d63-b4f2-1df07ac41e0f
ms.openlocfilehash: 8520504757e9e9ec9557b84ca2608b4cb99daf62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931399"
---
# <a name="how-to-implement-validation-logic-on-custom-objects"></a><span data-ttu-id="70811-102">方法: カスタム オブジェクトに検証ロジックを実装する</span><span class="sxs-lookup"><span data-stu-id="70811-102">How to: Implement Validation Logic on Custom Objects</span></span>
<span data-ttu-id="70811-103">この例では、カスタム オブジェクトに検証ロジックを実装し、それにバインドする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="70811-103">This example shows how to implement validation logic on a custom object and then bind to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70811-104">例</span><span class="sxs-lookup"><span data-stu-id="70811-104">Example</span></span>  
 <span data-ttu-id="70811-105">ソース オブジェクトで <xref:System.ComponentModel.IDataErrorInfo> が実装されている場合、ビジネス レイヤーで検証ロジックを提供できます。次に示す例では、<xref:System.ComponentModel.IDataErrorInfo> を実装する `Person` オブジェクトが定義されています、</span><span class="sxs-lookup"><span data-stu-id="70811-105">You can provide validation logic on the business layer if your source object implements <xref:System.ComponentModel.IDataErrorInfo>, as in the following example, which defines a `Person` object that implements <xref:System.ComponentModel.IDataErrorInfo>:</span></span>  
  
 [!code-csharp[BusinessLayerValidation#IDataErrorInfo](~/samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Data.cs#idataerrorinfo)]
 [!code-vb[BusinessLayerValidation#IDataErrorInfo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BusinessLayerValidation/VisualBasic/Data.vb#idataerrorinfo)]  
  
 <span data-ttu-id="70811-106">次の例では、テキスト ボックスのテキスト プロパティが、`Person.Age` プロパティにバインドされています。このプロパティは、`x:Key` `data` が指定されているリソースによって、バインドに使用できるようになっています。</span><span class="sxs-lookup"><span data-stu-id="70811-106">In the following example, the text property of the text box binds to the `Person.Age` property, which has been made available for binding through a resource declaration that is given the `x:Key` `data`.</span></span> <span data-ttu-id="70811-107"><xref:System.Windows.Controls.DataErrorValidationRule> では、<xref:System.ComponentModel.IDataErrorInfo> の実装によって発生する検証エラーがチェックされます。</span><span class="sxs-lookup"><span data-stu-id="70811-107">The <xref:System.Windows.Controls.DataErrorValidationRule> checks for the validation errors raised by the <xref:System.ComponentModel.IDataErrorInfo> implementation.</span></span>  
  
 [!code-xaml[BusinessLayerValidation#BoundTextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Window1.xaml?highlight=8,11-19,25-42)]  
  
 <span data-ttu-id="70811-108">または、<xref:System.Windows.Controls.DataErrorValidationRule> を使用する代わりに、<xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> プロパティを `true` に設定してもかまいません。</span><span class="sxs-lookup"><span data-stu-id="70811-108">Alternatively, instead of using the <xref:System.Windows.Controls.DataErrorValidationRule>, you can set the <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> property to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70811-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="70811-109">See also</span></span>

- <xref:System.Windows.Controls.ExceptionValidationRule>
- [<span data-ttu-id="70811-110">バインディングの検証の実装</span><span class="sxs-lookup"><span data-stu-id="70811-110">Implement Binding Validation</span></span>](how-to-implement-binding-validation.md)
- [<span data-ttu-id="70811-111">方法トピック</span><span class="sxs-lookup"><span data-stu-id="70811-111">How-to Topics</span></span>](data-binding-how-to-topics.md)
