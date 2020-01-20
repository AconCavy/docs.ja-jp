---
title: .NET Framework ガイドラインに準拠したイベントを発行する方法 - C# プログラミング ガイド
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 0ae240d0c078b5eaa690f128c037ee2471325872
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705341"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a><span data-ttu-id="50ff0-102">.NET Framework ガイドラインに準拠したイベントを発行する方法 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="50ff0-102">How to publish events that conform to .NET Framework Guidelines (C# Programming Guide)</span></span>
<span data-ttu-id="50ff0-103">ここでは、.NET Framework の標準のパターンに従うイベントをクラスおよび構造体に追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="50ff0-103">The following procedure demonstrates how to add events that follow the standard .NET Framework pattern to your classes and structs.</span></span> <span data-ttu-id="50ff0-104">.NET Framework クラス ライブラリ内のすべてのイベントは、次のように定義されている <xref:System.EventHandler> デリゲートに基づいています。</span><span class="sxs-lookup"><span data-stu-id="50ff0-104">All events in the .NET Framework class library are based on the <xref:System.EventHandler> delegate, which is defined as follows:</span></span>  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
> <span data-ttu-id="50ff0-105">.NET Framework 2.0 には、このデリゲートのジェネリック バージョンである <xref:System.EventHandler%601> が導入されています。</span><span class="sxs-lookup"><span data-stu-id="50ff0-105">The .NET Framework 2.0 introduces a generic version of this delegate, <xref:System.EventHandler%601>.</span></span> <span data-ttu-id="50ff0-106">次の例は、両方のバージョンの使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="50ff0-106">The following examples show how to use both versions.</span></span>  
  
 <span data-ttu-id="50ff0-107">ユーザー定義のクラス内のイベントは、値を返すデリゲートを含む、あらゆる有効なデリゲートに基づいて発行できますが、一般的には、次の例のように <xref:System.EventHandler> を使用して、.NET Framework のパターンに基づいて発行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="50ff0-107">Although events in classes that you define can be based on any valid delegate type, even delegates that return a value, it is generally recommended that you base your events on the .NET Framework pattern by using <xref:System.EventHandler>, as shown in the following example.</span></span>  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a><span data-ttu-id="50ff0-108">EventHandler パターンに基づいてイベントを発行するには</span><span class="sxs-lookup"><span data-stu-id="50ff0-108">To publish events based on the EventHandler pattern</span></span>  
  
1. <span data-ttu-id="50ff0-109">(イベントと共にカスタム データを送信する必要がない場合は、この手順を省略して手順 3a. に進んでください。)パブリッシャー クラスとサブスクライバー クラスの両方から参照できるスコープで、カスタム データのクラスを宣言します。</span><span class="sxs-lookup"><span data-stu-id="50ff0-109">(Skip this step and go to Step 3a if you do not have to send custom data with your event.) Declare the class for your custom data at a scope that is visible to both your publisher and subscriber classes.</span></span> <span data-ttu-id="50ff0-110">次に、カスタム イベント データを保持する必須メンバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="50ff0-110">Then add the required members to hold your custom event data.</span></span> <span data-ttu-id="50ff0-111">この例では、単純な文字列が 1 つ返されます。</span><span class="sxs-lookup"><span data-stu-id="50ff0-111">In this example, a simple string is returned.</span></span>  
  
    ```csharp  
    public class CustomEventArgs : EventArgs  
    {  
        public CustomEventArgs(string s)  
        {  
            msg = s;  
        }  
        private string msg;  
        public string Message  
        {  
            get { return msg; }  
        }   
    }  
    ```  
  
2. <span data-ttu-id="50ff0-112">(ジェネリック バージョンの <xref:System.EventHandler%601> を使用する場合、この手順は省略します。)パブリッシャー クラスでデリゲートを宣言します。</span><span class="sxs-lookup"><span data-stu-id="50ff0-112">(Skip this step if you are using the generic version of <xref:System.EventHandler%601> .) Declare a delegate in your publishing class.</span></span> <span data-ttu-id="50ff0-113">*EventHandler* で終わる名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="50ff0-113">Give it a name that ends with *EventHandler*.</span></span> <span data-ttu-id="50ff0-114">2 番目のパラメーターで、カスタムの EventArgs 型を指定します。</span><span class="sxs-lookup"><span data-stu-id="50ff0-114">The second parameter specifies your custom EventArgs type.</span></span>  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3. <span data-ttu-id="50ff0-115">次のいずれかの手順を使用して、パブリッシャー クラスでイベントを宣言します。</span><span class="sxs-lookup"><span data-stu-id="50ff0-115">Declare the event in your publishing class by using one of the following steps.</span></span>  
  
    1. <span data-ttu-id="50ff0-116">カスタムの EventArgs クラスがない場合、Event 型は非ジェネリック バージョンの EventHandler デリゲートになります。</span><span class="sxs-lookup"><span data-stu-id="50ff0-116">If you have no custom EventArgs class, your Event type will be the non-generic EventHandler delegate.</span></span> <span data-ttu-id="50ff0-117">このデリゲートは、C# プロジェクトを作成したときに含まれている <xref:System> 名前空間で既に宣言されているため、ここで宣言する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="50ff0-117">You do not have to declare the delegate because it is already declared in the <xref:System> namespace that is included when you create your C# project.</span></span> <span data-ttu-id="50ff0-118">パブリッシャー クラスに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="50ff0-118">Add the following code to your publisher class.</span></span>  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2. <span data-ttu-id="50ff0-119">非ジェネリック バージョンの <xref:System.EventHandler> を使用し、<xref:System.EventArgs> から派生したカスタム クラスがある場合は、パブリッシャー クラス内でイベントを宣言し、手順 2 のデリゲートを型として使用します。</span><span class="sxs-lookup"><span data-stu-id="50ff0-119">If you are using the non-generic version of <xref:System.EventHandler> and you have a custom class derived from <xref:System.EventArgs>, declare your event inside your publishing class and use your delegate from step 2 as the type.</span></span>  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3. <span data-ttu-id="50ff0-120">ジェネリック バージョンを使用する場合、カスタム デリゲートは不要です。</span><span class="sxs-lookup"><span data-stu-id="50ff0-120">If you are using the generic version, you do not need a custom delegate.</span></span> <span data-ttu-id="50ff0-121">代わりに、パブリッシャー クラスでイベントの種類として `EventHandler<CustomEventArgs>` を指定します。山かっこの部分は、実際のクラス名で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="50ff0-121">Instead, in your publishing class, you specify your event type as `EventHandler<CustomEventArgs>`, substituting the name of your own class between the angle brackets.</span></span>  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a><span data-ttu-id="50ff0-122">例</span><span class="sxs-lookup"><span data-stu-id="50ff0-122">Example</span></span>  
 <span data-ttu-id="50ff0-123">次の例は、前の手順を具体的に示しています。ここでは、カスタムの EventArgs クラスを使用し、イベントの種類として <xref:System.EventHandler%601> を使用しています。</span><span class="sxs-lookup"><span data-stu-id="50ff0-123">The following example demonstrates the previous steps by using a custom EventArgs class and <xref:System.EventHandler%601> as the event type.</span></span>  
  
 [!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]  
  
## <a name="see-also"></a><span data-ttu-id="50ff0-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="50ff0-124">See also</span></span>

- <xref:System.Delegate>
- [<span data-ttu-id="50ff0-125">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="50ff0-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="50ff0-126">イベント</span><span class="sxs-lookup"><span data-stu-id="50ff0-126">Events</span></span>](./index.md)
- [<span data-ttu-id="50ff0-127">デリゲート</span><span class="sxs-lookup"><span data-stu-id="50ff0-127">Delegates</span></span>](../delegates/index.md)
