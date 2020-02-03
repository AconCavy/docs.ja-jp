---
title: データ バインディング
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms]
- Windows Forms, data binding
- data [Windows Forms], architecture
- Windows Forms controls, data binding
ms.assetid: c3826d8e-ea25-4ad4-a669-45bfb19192aa
ms.openlocfilehash: 68871db848ab46b88865e668f27f09972e8debcf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734617"
---
# <a name="windows-forms-data-binding"></a><span data-ttu-id="f1770-102">Windows フォームのデータ バインディング</span><span class="sxs-lookup"><span data-stu-id="f1770-102">Windows Forms Data Binding</span></span>
<span data-ttu-id="f1770-103">Windows フォームでのデータ バインディングは、データ ソースの情報をフォーム上のコントロールで表示したり変更したりする手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="f1770-103">Data binding in Windows Forms gives you the means to display and make changes to information from a data source in controls on the form.</span></span> <span data-ttu-id="f1770-104">従来のデータ ソースに対してだけでなく、データを格納したほとんどすべての構造に対してバインドできます。</span><span class="sxs-lookup"><span data-stu-id="f1770-104">You can bind to both traditional data sources as well as almost any structure that contains data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f1770-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f1770-105">In This Section</span></span>  
 [<span data-ttu-id="f1770-106">データ連結と Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="f1770-106">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)  
 <span data-ttu-id="f1770-107">Windows フォームのデータ バインディングの概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="f1770-107">Provides an overview of data binding in Windows Forms.</span></span>  
  
 [<span data-ttu-id="f1770-108">Windows フォームがサポートするデータ ソース</span><span class="sxs-lookup"><span data-stu-id="f1770-108">Data Sources Supported by Windows Forms</span></span>](data-sources-supported-by-windows-forms.md)  
 <span data-ttu-id="f1770-109">Windows フォームで使用できるデータ ソースについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f1770-109">Describes the data sources that can be used with Windows Forms.</span></span>  
  
 [<span data-ttu-id="f1770-110">データ連結に関連するインターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1770-110">Interfaces Related to Data Binding</span></span>](interfaces-related-to-data-binding.md)  
 <span data-ttu-id="f1770-111">Windows フォームのデータ バインドで使用されるいくつかのインターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f1770-111">Describes several of the interfaces used with Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="f1770-112">方法: Windows フォームでデータ間を移動する</span><span class="sxs-lookup"><span data-stu-id="f1770-112">How to: Navigate Data in Windows Forms</span></span>](how-to-navigate-data-in-windows-forms.md)  
 <span data-ttu-id="f1770-113">データ ソースの項目間を移動する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f1770-113">Shows how to navigate through items in a data source.</span></span>  
  
 [<span data-ttu-id="f1770-114">Windows フォーム データ バインドの変更通知</span><span class="sxs-lookup"><span data-stu-id="f1770-114">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)  
 <span data-ttu-id="f1770-115">Windows フォーム データ バインドの異なる種類の変更通知について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1770-115">Describes different types of change notification for Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="f1770-116">方法: INotifyPropertyChanged インターフェイスを実装する</span><span class="sxs-lookup"><span data-stu-id="f1770-116">How to: Implement the INotifyPropertyChanged Interface</span></span>](how-to-implement-the-inotifypropertychanged-interface.md)  
 <span data-ttu-id="f1770-117"><xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1770-117">Shows how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="f1770-118">インターフェイスは、バインドしたコントロールを通してビジネス オブジェクトのプロパティの変更内容を通信します。</span><span class="sxs-lookup"><span data-stu-id="f1770-118">The interface  communicates to a bound control the property changes on a business object</span></span>  
  
 [<span data-ttu-id="f1770-119">方法: PropertyNameChanged パターンを適用する</span><span class="sxs-lookup"><span data-stu-id="f1770-119">How to: Apply the PropertyNameChanged Pattern</span></span>](how-to-apply-the-propertynamechanged-pattern.md)  
 <span data-ttu-id="f1770-120">*PropertyName*Changed パターンを Windows フォームユーザーコントロールのプロパティに適用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f1770-120">Shows how to apply the *PropertyName*Changed pattern to properties of a Windows Forms user control.</span></span>  
  
 [<span data-ttu-id="f1770-121">方法: ITypedList インターフェイスを実装する</span><span class="sxs-lookup"><span data-stu-id="f1770-121">How to: Implement the ITypedList Interface</span></span>](how-to-implement-the-itypedlist-interface.md)  
 <span data-ttu-id="f1770-122"><xref:System.ComponentModel.ITypedList> インターフェイスを実装して、バインドできるリストのスキーマを検出できるようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1770-122">Shows how to enable discovery of the schema for a bindable list by implementing the <xref:System.ComponentModel.ITypedList> interface.</span></span>  
  
 [<span data-ttu-id="f1770-123">方法: IListSource インターフェイスを実装する</span><span class="sxs-lookup"><span data-stu-id="f1770-123">How to: Implement the IListSource Interface</span></span>](how-to-implement-the-ilistsource-interface.md)  
 <span data-ttu-id="f1770-124"><xref:System.ComponentModel.IListSource> インターフェイスを実装して、<xref:System.Collections.IList> を実装する代わりに別の場所からリストを提供する、バインドできるクラスを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1770-124">Shows how to implement the <xref:System.ComponentModel.IListSource> interface to create a bindable class does not implement <xref:System.Collections.IList>, but provides a list from another location.</span></span>  
  
 [<span data-ttu-id="f1770-125">方法: 複数のコントロールを 1 つのデータ ソースにバインドして同期状態を保つ</span><span class="sxs-lookup"><span data-stu-id="f1770-125">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>](multiple-controls-bound-to-data-source-synchronized.md)  
 <span data-ttu-id="f1770-126"><xref:System.Windows.Forms.BindingSource.BindingComplete> イベントを処理して、データ ソースにバインドされているすべてのコントロールの同期を保つ方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1770-126">Shows how to handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event to ensure all controls bound to a data source remain synchronized.</span></span>  
  
 [<span data-ttu-id="f1770-127">方法: 子テーブルの選択行が現在位置を保持することを保証する</span><span class="sxs-lookup"><span data-stu-id="f1770-127">How to: Ensure the Selected Row in a Child Table Remains at the Correct Position</span></span>](ensure-the-selected-row-in-a-child-table-correct.md)  
 <span data-ttu-id="f1770-128">親テーブルのフィールドが変更された場合に、子テーブルの選択行が変更されないことを保証する方法について説明しています。</span><span class="sxs-lookup"><span data-stu-id="f1770-128">Shows how to ensure the selected row of a child table does not change, when a change is made to a field of the parent table.</span></span>  
  
 <span data-ttu-id="f1770-129">「[データバインディングに関連するインターフェイス](interfaces-related-to-data-binding.md)」、「[方法: Windows フォームでデータを移動](how-to-navigate-data-in-windows-forms.md)する」、および「[方法: Windows フォームに単純バインドコントロールを作成する](how-to-create-a-simple-bound-control-on-a-windows-form.md)」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1770-129">Also see [Interfaces Related to Data Binding](interfaces-related-to-data-binding.md), [How to: Navigate Data in Windows Forms](how-to-navigate-data-in-windows-forms.md), and [How to: Create a Simple-Bound Control on a Windows Form](how-to-create-a-simple-bound-control-on-a-windows-form.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f1770-130">リファレンス</span><span class="sxs-lookup"><span data-stu-id="f1770-130">Reference</span></span>  
 <xref:System.Windows.Forms.Binding?displayProperty=nameWithType>  
 <span data-ttu-id="f1770-131">バインドできるコンポーネントとデータ ソースの間のバインディングを表すクラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f1770-131">Describes the class that represents the binding between a bindable component and a data source.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>  
 <span data-ttu-id="f1770-132">コントロールにバインドするためにデータ ソースをカプセル化するクラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f1770-132">Describes the class that encapsulates a data source for binding to controls.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f1770-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1770-133">Related Sections</span></span>  
 [<span data-ttu-id="f1770-134">BindingSource コンポーネント</span><span class="sxs-lookup"><span data-stu-id="f1770-134">BindingSource Component</span></span>](./controls/bindingsource-component.md)  
 <span data-ttu-id="f1770-135"><xref:System.Windows.Forms.BindingSource> コンポーネントの使用方法の例を示すトピックの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="f1770-135">Contains a list of topics that demonstrate how to use the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="f1770-136">DataGridView コントロール</span><span class="sxs-lookup"><span data-stu-id="f1770-136">DataGridView Control</span></span>](./controls/datagridview-control-windows-forms.md)  
 <span data-ttu-id="f1770-137">バインドできるデータ グリッド コントロールの使用方法の例を示すトピックの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="f1770-137">Provides a list of topics that demonstrate how to use a bindable datagrid control.</span></span>  
  
 <span data-ttu-id="f1770-138">「 [Visual Studio でのデータへのアクセス](/visualstudio/data-tools/accessing-data-in-visual-studio)」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1770-138">Also see [Accessing Data in Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span></span>
