---
title: '方法: 添付プロパティを登録する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF], registering
- registering attached properties [WPF]
ms.assetid: eb47bd94-0451-4f8d-8fb6-95f7812ac05b
ms.openlocfilehash: 4c678a64b62b8f4db24cf39ffbafac52e56c9982
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768681"
---
# <a name="how-to-register-an-attached-property"></a><span data-ttu-id="759e2-102">方法: 添付プロパティを登録する</span><span class="sxs-lookup"><span data-stu-id="759e2-102">How to: Register an Attached Property</span></span>
<span data-ttu-id="759e2-103">この例では、添付プロパティを登録する方法、および [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] とコードの両方でプロパティを使用できるようにパブリック アクセサーを提供する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="759e2-103">This example shows how to register an attached property and provide public accessors so that you can use the property in both [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] and code.</span></span> <span data-ttu-id="759e2-104">添付プロパティは、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] で定義されている構文の概念です。</span><span class="sxs-lookup"><span data-stu-id="759e2-104">Attached properties are a syntax concept defined by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="759e2-105">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の型のほとんどの添付プロパティは、依存関係プロパティとしても実装されます。</span><span class="sxs-lookup"><span data-stu-id="759e2-105">Most attached properties for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] types are also implemented as dependency properties.</span></span> <span data-ttu-id="759e2-106">あらゆる <xref:System.Windows.DependencyObject> 型で依存関係プロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="759e2-106">You can use dependency properties on any <xref:System.Windows.DependencyObject> types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="759e2-107">例</span><span class="sxs-lookup"><span data-stu-id="759e2-107">Example</span></span>  
 <span data-ttu-id="759e2-108">次の例では、<xref:System.Windows.DependencyProperty.RegisterAttached%2A> メソッドを使用して添付プロパティを依存関係プロパティとして登録する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="759e2-108">The following example shows how to register an attached property as a dependency property, by using the <xref:System.Windows.DependencyProperty.RegisterAttached%2A> method.</span></span> <span data-ttu-id="759e2-109">プロバイダー クラスは、プロパティの既定のメタデータを提供するオプションを持っています。この既定値は、別のクラスに対してプロパティが使用されるときに適用されます (そのクラスがメタデータをオーバーライドしない場合)。</span><span class="sxs-lookup"><span data-stu-id="759e2-109">The provider class has the option of providing default metadata for the property that is applicable when the property is used on another class, unless that class overrides the metadata.</span></span> <span data-ttu-id="759e2-110">この例では、`IsBubbleSource` プロパティの既定値は `false` に設定されています。</span><span class="sxs-lookup"><span data-stu-id="759e2-110">In this example, the default value of the `IsBubbleSource` property is set to `false`.</span></span>  
  
 <span data-ttu-id="759e2-111">添付プロパティ (依存関係プロパティとして登録されていなくても) のプロバイダー クラスは、`Set` *[AttachedPropertyName]* および `Get` *[AttachedPropertyName]* の名前付け規則に従う静的な get および set アクセサーを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="759e2-111">The provider class for an attached property (even if it is not registered as a dependency property) must provide static get and set accessors that follow the naming convention `Set`*[AttachedPropertyName]* and `Get`*[AttachedPropertyName]*.</span></span> <span data-ttu-id="759e2-112">これらのアクセサーは、機能している [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] リーダーがプロパティを [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の属性として認識し、適切な型を解決できるために必要です。</span><span class="sxs-lookup"><span data-stu-id="759e2-112">These accessors are required so that the acting [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader can recognize the property as an attribute in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] and resolve the appropriate types.</span></span>  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
## <a name="see-also"></a><span data-ttu-id="759e2-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="759e2-113">See also</span></span>

- <xref:System.Windows.DependencyProperty>
- [<span data-ttu-id="759e2-114">依存関係プロパティの概要</span><span class="sxs-lookup"><span data-stu-id="759e2-114">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="759e2-115">カスタム依存関係プロパティ</span><span class="sxs-lookup"><span data-stu-id="759e2-115">Custom Dependency Properties</span></span>](custom-dependency-properties.md)
- [<span data-ttu-id="759e2-116">方法トピック</span><span class="sxs-lookup"><span data-stu-id="759e2-116">How-to Topics</span></span>](properties-how-to-topics.md)
