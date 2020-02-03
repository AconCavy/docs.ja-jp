---
title: RealTimeStylus を無効にする
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: 74145c32af7e9ebbc774a0301e205aa1eb1539b3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737941"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a><span data-ttu-id="cabba-102">WPF アプリケーションのリアルタイムなスタイラス入力を無効にする</span><span class="sxs-lookup"><span data-stu-id="cabba-102">Disable the RealTimeStylus for WPF Applications</span></span>

<span data-ttu-id="cabba-103">Windows Presentation Foundation (WPF) には、Windows 7 タッチ入力を処理するためのサポートが組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="cabba-103">Windows Presentation Foundation (WPF) has built in support for processing Windows 7 touch input.</span></span> <span data-ttu-id="cabba-104">サポートは、<xref:System.Windows.UIElement.OnStylusDown%2A>、<xref:System.Windows.UIElement.OnStylusUp%2A>、および <xref:System.Windows.UIElement.OnStylusMove%2A> イベントとしてのタブレットプラットフォームのリアルタイムスタイラス入力を通じて行われます。</span><span class="sxs-lookup"><span data-stu-id="cabba-104">The support comes through the tablet platform’s real-time stylus input as <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, and <xref:System.Windows.UIElement.OnStylusMove%2A> events.</span></span> <span data-ttu-id="cabba-105">Windows 7 では、マルチタッチ入力も Win32 WM_TOUCH ウィンドウメッセージとして提供されます。</span><span class="sxs-lookup"><span data-stu-id="cabba-105">Windows 7 also provides multi-touch input as Win32 WM_TOUCH window messages.</span></span> <span data-ttu-id="cabba-106">これらの2つの Api は、同じ HWND で相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="cabba-106">These two APIs are mutually exclusive on the same HWND.</span></span> <span data-ttu-id="cabba-107">タブレットプラットフォーム (WPF アプリケーションの既定値) を使用してタッチ入力を有効にすると、WM_TOUCH メッセージが無効になります。</span><span class="sxs-lookup"><span data-stu-id="cabba-107">Enabling touch input via the tablet platform (the default for WPF applications) disables WM_TOUCH messages.</span></span> <span data-ttu-id="cabba-108">そのため、WM_TOUCH を使用して WPF ウィンドウからタッチメッセージを受信するには、WPF の組み込みのスタイラスサポートを無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cabba-108">As a result, to use WM_TOUCH to receive touch messages from a WPF window, you must disable the built-in stylus support in WPF.</span></span> <span data-ttu-id="cabba-109">これは、WM_TOUCH を使用するコンポーネントをホストする WPF ウィンドウなどのシナリオに適用されます。</span><span class="sxs-lookup"><span data-stu-id="cabba-109">This is applicable in a scenario such as a WPF window hosting a component that uses WM_TOUCH.</span></span>  
  
 <span data-ttu-id="cabba-110">スタイラス入力をリッスンしている WPF を無効にするには、WPF ウィンドウによって追加されたすべてのタブレットサポートを削除します。</span><span class="sxs-lookup"><span data-stu-id="cabba-110">To disable WPF listening to stylus input, remove any tablet support added by the WPF window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cabba-111">例</span><span class="sxs-lookup"><span data-stu-id="cabba-111">Example</span></span>  
 <span data-ttu-id="cabba-112">次のサンプルコードは、リフレクションを使用して既定のタブレットプラットフォームのサポートを削除する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="cabba-112">The following sample code shows how to remove the default tablet platform support by using reflection.</span></span>  
  
```csharp  
public static void DisableWPFTabletSupport()  
{  
    // Get a collection of the tablet devices for this window.    
    TabletDeviceCollection devices = System.Windows.Input.Tablet.TabletDevices;  
  
    if (devices.Count > 0)  
    {     
        // Get the Type of InputManager.  
        Type inputManagerType = typeof(System.Windows.Input.InputManager);  
  
        // Call the StylusLogic method on the InputManager.Current instance.  
        object stylusLogic = inputManagerType.InvokeMember("StylusLogic",  
                    BindingFlags.GetProperty | BindingFlags.Instance | BindingFlags.NonPublic,  
                    null, InputManager.Current, null);  
  
        if (stylusLogic != null)  
        {  
            //  Get the type of the stylusLogic returned from the call to StylusLogic.  
            Type stylusLogicType = stylusLogic.GetType();  
  
            // Loop until there are no more devices to remove.  
            while (devices.Count > 0)  
            {  
                // Remove the first tablet device in the devices collection.  
                stylusLogicType.InvokeMember("OnTabletRemoved",  
                        BindingFlags.InvokeMethod | BindingFlags.Instance | BindingFlags.NonPublic,  
                        null, stylusLogic, new object[] { (uint)0 });  
            }                  
        }  
  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="cabba-113">参照</span><span class="sxs-lookup"><span data-stu-id="cabba-113">See also</span></span>

- [<span data-ttu-id="cabba-114">スタイラスからの入力のインターセプト</span><span class="sxs-lookup"><span data-stu-id="cabba-114">Intercepting Input from the Stylus</span></span>](intercepting-input-from-the-stylus.md)
