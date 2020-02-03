---
title: TabControl の外観を変更する
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- icons [Windows Forms], displaying on tabs
- TabControl control [Windows Forms], changing page appearance
- tabs [Windows Forms], controlling appearance
- buttons [Windows Forms], displaying tabs as
ms.assetid: 7c6cc443-ed62-4d26-b94d-b8913b44f773
ms.openlocfilehash: 056070177e6bbaba0c93c7b94f5adfd7887be6a8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746615"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a><span data-ttu-id="58fe8-102">方法 : Windows フォーム TabControl の表示形式を変更する</span><span class="sxs-lookup"><span data-stu-id="58fe8-102">How to: Change the Appearance of the Windows Forms TabControl</span></span>
<span data-ttu-id="58fe8-103">Windows フォームのタブの外観を変更するには、<xref:System.Windows.Forms.TabControl> のプロパティと、コントロールの各タブを構成する <xref:System.Windows.Forms.TabPage> オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="58fe8-103">You can change the appearance of tabs in Windows Forms by using properties of the <xref:System.Windows.Forms.TabControl> and the <xref:System.Windows.Forms.TabPage> objects that make up the individual tabs on the control.</span></span> <span data-ttu-id="58fe8-104">これらのプロパティを設定することにより、タブに画像を表示し、水平方向ではなく垂直方向にタブを表示し、タブの複数行を表示し、プログラムによってタブを有効または無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="58fe8-104">By setting these properties, you can display images on tabs, display tabs vertically instead of horizontally, display multiple rows of tabs, and enable or disable tabs programmatically.</span></span>  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a><span data-ttu-id="58fe8-105">タブのラベル部分にアイコンを表示するには</span><span class="sxs-lookup"><span data-stu-id="58fe8-105">To display an icon on the label part of a tab</span></span>  
  
1. <span data-ttu-id="58fe8-106">フォームに <xref:System.Windows.Forms.ImageList> コントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="58fe8-106">Add an <xref:System.Windows.Forms.ImageList> control to the form.</span></span>  
  
2. <span data-ttu-id="58fe8-107">イメージリストにイメージを追加します。</span><span class="sxs-lookup"><span data-stu-id="58fe8-107">Add images to the image list.</span></span>  
  
     <span data-ttu-id="58fe8-108">イメージリストの詳細については、「 [Imagelist コンポーネント](imagelist-component-windows-forms.md)」および「[方法: Windows フォーム imagelist コンポーネントを使用してイメージを追加または削除する](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58fe8-108">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
3. <span data-ttu-id="58fe8-109"><xref:System.Windows.Forms.TabControl> の <xref:System.Windows.Forms.TabControl.ImageList%2A> プロパティを <xref:System.Windows.Forms.ImageList> コントロールに設定します。</span><span class="sxs-lookup"><span data-stu-id="58fe8-109">Set the <xref:System.Windows.Forms.TabControl.ImageList%2A> property of the <xref:System.Windows.Forms.TabControl> to the <xref:System.Windows.Forms.ImageList> control.</span></span>  
  
4. <span data-ttu-id="58fe8-110"><xref:System.Windows.Forms.TabPage> の [<xref:System.Windows.Forms.TabPage.ImageIndex%2A>] プロパティを、一覧内の適切なイメージのインデックスに設定します。</span><span class="sxs-lookup"><span data-stu-id="58fe8-110">Set the <xref:System.Windows.Forms.TabPage.ImageIndex%2A> property of the <xref:System.Windows.Forms.TabPage> to the index of an appropriate image in the list.</span></span>  
  
### <a name="to-create-multiple-rows-of-tabs"></a><span data-ttu-id="58fe8-111">複数行のタブを作成するには</span><span class="sxs-lookup"><span data-stu-id="58fe8-111">To create multiple rows of tabs</span></span>  
  
1. <span data-ttu-id="58fe8-112">必要なタブページの数を追加します。</span><span class="sxs-lookup"><span data-stu-id="58fe8-112">Add the number of tab pages you want.</span></span>  
  
2. <span data-ttu-id="58fe8-113"><xref:System.Windows.Forms.TabControl> の <xref:System.Windows.Forms.TabControl.Multiline%2A> プロパティを `true`に設定します。</span><span class="sxs-lookup"><span data-stu-id="58fe8-113">Set the <xref:System.Windows.Forms.TabControl.Multiline%2A> property of the <xref:System.Windows.Forms.TabControl> to `true`.</span></span>  
  
3. <span data-ttu-id="58fe8-114">タブが複数の行にまだ表示されていない場合は、<xref:System.Windows.Forms.TabControl> の [<xref:System.Windows.Forms.Control.Width%2A>] プロパティを、すべてのタブよりも狭くするように設定します。</span><span class="sxs-lookup"><span data-stu-id="58fe8-114">If the tabs do not already appear in multiple rows, set the <xref:System.Windows.Forms.Control.Width%2A> property of the <xref:System.Windows.Forms.TabControl> to be narrower than all the tabs.</span></span>  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a><span data-ttu-id="58fe8-115">コントロールの横にタブを配置するには</span><span class="sxs-lookup"><span data-stu-id="58fe8-115">To arrange tabs on the side of the control</span></span>  
  
- <span data-ttu-id="58fe8-116"><xref:System.Windows.Forms.TabControl> の <xref:System.Windows.Forms.TabControl.Alignment%2A> プロパティを <xref:System.Windows.Forms.TabAlignment.Left> または <xref:System.Windows.Forms.TabAlignment.Right>に設定します。</span><span class="sxs-lookup"><span data-stu-id="58fe8-116">Set the <xref:System.Windows.Forms.TabControl.Alignment%2A> property of the <xref:System.Windows.Forms.TabControl> to <xref:System.Windows.Forms.TabAlignment.Left> or <xref:System.Windows.Forms.TabAlignment.Right>.</span></span>  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a><span data-ttu-id="58fe8-117">タブのすべてのコントロールをプログラムで有効または無効にするには</span><span class="sxs-lookup"><span data-stu-id="58fe8-117">To programmatically enable or disable all controls on a tab</span></span>  
  
1. <span data-ttu-id="58fe8-118"><xref:System.Windows.Forms.TabPage> の <xref:System.Windows.Forms.TabPage.Enabled%2A> プロパティを `true` または `false`に設定します。</span><span class="sxs-lookup"><span data-stu-id="58fe8-118">Set the <xref:System.Windows.Forms.TabPage.Enabled%2A> property of the <xref:System.Windows.Forms.TabPage> to `true` or `false`.</span></span>  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a><span data-ttu-id="58fe8-119">タブをボタンとして表示するには</span><span class="sxs-lookup"><span data-stu-id="58fe8-119">To display tabs as buttons</span></span>  
  
- <span data-ttu-id="58fe8-120"><xref:System.Windows.Forms.TabControl> の <xref:System.Windows.Forms.TabControl.Appearance%2A> プロパティを <xref:System.Windows.Forms.TabAppearance.Buttons> または <xref:System.Windows.Forms.TabAppearance.FlatButtons>に設定します。</span><span class="sxs-lookup"><span data-stu-id="58fe8-120">Set the <xref:System.Windows.Forms.TabControl.Appearance%2A> property of the <xref:System.Windows.Forms.TabControl> to <xref:System.Windows.Forms.TabAppearance.Buttons> or <xref:System.Windows.Forms.TabAppearance.FlatButtons>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58fe8-121">参照</span><span class="sxs-lookup"><span data-stu-id="58fe8-121">See also</span></span>

- [<span data-ttu-id="58fe8-122">TabControl コントロール</span><span class="sxs-lookup"><span data-stu-id="58fe8-122">TabControl Control</span></span>](tabcontrol-control-windows-forms.md)
- [<span data-ttu-id="58fe8-123">TabControl コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="58fe8-123">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="58fe8-124">方法: タブ ページにコントロールを追加する</span><span class="sxs-lookup"><span data-stu-id="58fe8-124">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="58fe8-125">方法: タブ ページを無効化する</span><span class="sxs-lookup"><span data-stu-id="58fe8-125">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)
- [<span data-ttu-id="58fe8-126">方法: Windows フォーム TabControl のタブを追加および削除する</span><span class="sxs-lookup"><span data-stu-id="58fe8-126">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
