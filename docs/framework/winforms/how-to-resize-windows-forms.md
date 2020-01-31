---
title: フォームのサイズ変更
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- resizing Windows Forms
- Windows Forms, resizing
ms.assetid: 5d9dd47e-e68c-48c9-a0a3-a9ff34ba009d
ms.openlocfilehash: 8d4ce46ada505f952fc3090d10c5d893338d19f2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739303"
---
# <a name="how-to-resize-windows-forms"></a><span data-ttu-id="c4a57-102">方法 : Windows フォームのサイズを変更する</span><span class="sxs-lookup"><span data-stu-id="c4a57-102">How to: Resize Windows Forms</span></span>

<span data-ttu-id="c4a57-103">Windows フォームのサイズは、いくつかの方法で指定できます。</span><span class="sxs-lookup"><span data-stu-id="c4a57-103">You can specify the size of your Windows Form in several ways.</span></span> <span data-ttu-id="c4a57-104"><xref:System.Windows.Forms.Form.Size%2A> プロパティに新しい値を設定したり、<xref:System.Windows.Forms.Control.Height%2A> プロパティまたは <xref:System.Windows.Forms.Control.Width%2A> プロパティを個別に調整したりすることで、フォームの高さと幅の両方をプログラムで変更できます。</span><span class="sxs-lookup"><span data-stu-id="c4a57-104">You can change both the height and the width of the form programmatically by setting a new value for the <xref:System.Windows.Forms.Form.Size%2A> property, or adjust the <xref:System.Windows.Forms.Control.Height%2A> or <xref:System.Windows.Forms.Control.Width%2A> properties individually.</span></span> <span data-ttu-id="c4a57-105">Visual Studio を使用している場合は、Windows フォームデザイナーを使用してサイズを変更できます。</span><span class="sxs-lookup"><span data-stu-id="c4a57-105">If you're using Visual Studio, you can change the size using the Windows Forms Designer.</span></span> <span data-ttu-id="c4a57-106">「[方法: デザイナーを使用して Windows フォームのサイズを変更する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4a57-106">Also see [How to: Resize Windows Forms Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).</span></span>

## <a name="resize-a-form-programmatically"></a><span data-ttu-id="c4a57-107">プログラムによるフォームのサイズ変更</span><span class="sxs-lookup"><span data-stu-id="c4a57-107">Resize a form programmatically</span></span>

<span data-ttu-id="c4a57-108">フォームの <xref:System.Windows.Forms.Form.Size%2A> プロパティを設定して、実行時にフォームのサイズを定義します。</span><span class="sxs-lookup"><span data-stu-id="c4a57-108">Define the size of a form at run time by setting the <xref:System.Windows.Forms.Form.Size%2A> property of the form.</span></span>

<span data-ttu-id="c4a57-109">次のコード例では、フォームのサイズを 100 × 100 ピクセルに設定します。</span><span class="sxs-lookup"><span data-stu-id="c4a57-109">The following code example shows the form size set to 100 × 100 pixels.</span></span>

```vb
Form1.Size = New System.Drawing.Size(100, 100)
```

```csharp
Form1.Size = new System.Drawing.Size(100, 100);
```

```cpp
Form1->Size = System::Drawing::Size(100, 100);
```

## <a name="change-form-width-and-height-programmatically"></a><span data-ttu-id="c4a57-110">フォームの幅と高さをプログラムによって変更する</span><span class="sxs-lookup"><span data-stu-id="c4a57-110">Change form width and height programmatically</span></span>

<span data-ttu-id="c4a57-111"><xref:System.Windows.Forms.Form.Size%2A> を定義した後で、<xref:System.Windows.Forms.Control.Width%2A> プロパティまたは <xref:System.Windows.Forms.Control.Height%2A> プロパティを使用して、フォームの高さと幅のいずれかを変更します。</span><span class="sxs-lookup"><span data-stu-id="c4a57-111">After the <xref:System.Windows.Forms.Form.Size%2A> is defined, change either the form height or width by using the <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>

<span data-ttu-id="c4a57-112">次のコード例は、フォームの幅を、フォームの左端から 300 ピクセルに設定し、高さは一定のままにする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c4a57-112">The following code example shows the width of the form set to 300 pixels from the left edge of the form, whereas the height stays constant.</span></span>

```vb
Form1.Width = 300
```

```csharp
Form1.Width = 300;
```

```cpp
Form1->Width = 300;
```

<span data-ttu-id="c4a57-113">-または-</span><span class="sxs-lookup"><span data-stu-id="c4a57-113">-or-</span></span>

<span data-ttu-id="c4a57-114"><xref:System.Windows.Forms.Form.Size%2A> プロパティを設定して、<xref:System.Drawing.Size.Width%2A> または <xref:System.Drawing.Size.Height%2A> を変更します。</span><span class="sxs-lookup"><span data-stu-id="c4a57-114">Change <xref:System.Drawing.Size.Width%2A> or <xref:System.Drawing.Size.Height%2A> by setting the <xref:System.Windows.Forms.Form.Size%2A> property.</span></span>

<span data-ttu-id="c4a57-115">ただし、次のコード例が示すように、この方法は、<xref:System.Windows.Forms.Control.Width%2A> プロパティまたは <xref:System.Windows.Forms.Control.Height%2A> プロパティをただ設定する方法よりも煩雑になります。</span><span class="sxs-lookup"><span data-stu-id="c4a57-115">However, as the following code example shows, this approach is more cumbersome than just setting <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>

```vb
Form1.Size = New Size(300, Form1.Size.Height)
```

```csharp
Form1.Size = new Size(300, Form1.Size.Height);
```

```cpp
Form1->Size = System::Drawing::Size(300, Form1->Size.Height);
```

## <a name="change-form-size-by-increments-programmatically"></a><span data-ttu-id="c4a57-116">プログラムによってフォームのサイズをインクリメントして変更する</span><span class="sxs-lookup"><span data-stu-id="c4a57-116">Change form size by increments programmatically</span></span>

<span data-ttu-id="c4a57-117">フォームのサイズを増分するには、<xref:System.Drawing.Size.Width%2A> プロパティと <xref:System.Drawing.Size.Height%2A> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="c4a57-117">To increment the size of the form, set the <xref:System.Drawing.Size.Width%2A> and <xref:System.Drawing.Size.Height%2A> properties.</span></span>

<span data-ttu-id="c4a57-118">次のコード例は、フォームの幅を、現在の設定より 200 ピクセル広くする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c4a57-118">The following code example shows the width of the form set to 200 pixels wider than the current setting.</span></span>

```vb
Form1.Width += 200
```

```csharp
Form1.Width += 200;
```

```cpp
Form1->Width += 200;
```

> [!CAUTION]
> <span data-ttu-id="c4a57-119"><xref:System.Windows.Forms.Form.Size%2A> プロパティを新しい <xref:System.Drawing.Size> 構造に設定することにより高さと幅の両方のディメンションを同時に設定するというのでない限り、フォームのディメンションを変更するには、常に <xref:System.Drawing.Size.Height%2A> プロパティまたは <xref:System.Drawing.Size.Width%2A> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="c4a57-119">Always use the <xref:System.Drawing.Size.Height%2A> or <xref:System.Drawing.Size.Width%2A> property to change a dimension of a form, unless you are setting both height and width dimensions at the same time by setting the <xref:System.Windows.Forms.Form.Size%2A> property to a new <xref:System.Drawing.Size> structure.</span></span> <span data-ttu-id="c4a57-120"><xref:System.Windows.Forms.Form.Size%2A> プロパティは、値型である <xref:System.Drawing.Size> 構造を返します。</span><span class="sxs-lookup"><span data-stu-id="c4a57-120">The <xref:System.Windows.Forms.Form.Size%2A> property returns a <xref:System.Drawing.Size> structure, which is a value type.</span></span> <span data-ttu-id="c4a57-121">値型のプロパティに新しい値を割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="c4a57-121">You cannot assign a new value to the property of a value type.</span></span> <span data-ttu-id="c4a57-122">このため、次のコード例はコンパイルされません。</span><span class="sxs-lookup"><span data-stu-id="c4a57-122">Therefore, the following code example will not compile.</span></span>

```vb
' NOTE: CODE WILL NOT COMPILE
Dim f As New Form()
f.Size.Width += 100
```

```csharp
// NOTE: CODE WILL NOT COMPILE
Form f = new Form();
f.Size.Width += 100;
```

```cpp
// NOTE: CODE WILL NOT COMPILE
Form^ f = gcnew Form();
f->Size->X += 100;
```

## <a name="see-also"></a><span data-ttu-id="c4a57-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4a57-123">See also</span></span>

- [<span data-ttu-id="c4a57-124">Windows フォームについて</span><span class="sxs-lookup"><span data-stu-id="c4a57-124">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
- [<span data-ttu-id="c4a57-125">Windows フォーム アプリケーションの拡張</span><span class="sxs-lookup"><span data-stu-id="c4a57-125">Enhancing Windows Forms Applications</span></span>](./advanced/index.md)
