---
title: クライアント側 UI オートメーション プロバイダーの作成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, creating client-side provider
- client-side UI Automation provider, creating
ms.assetid: d91edaf2-be28-41ec-a508-af421cb43c3d
ms.openlocfilehash: 79accd23392ff9e1e8157348f7a1042ee2b3cc47
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433656"
---
# <a name="create-a-client-side-ui-automation-provider"></a><span data-ttu-id="cc043-102">クライアント側 UI オートメーション プロバイダーの作成</span><span class="sxs-lookup"><span data-stu-id="cc043-102">Create a Client-Side UI Automation Provider</span></span>
> [!NOTE]
> <span data-ttu-id="cc043-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="cc043-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="cc043-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](/windows/win32/winauto/entry-uiauto-win32)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc043-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="cc043-105">このトピックのコード例では、クライアント側 UI オートメーション プロバイダーを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="cc043-105">This topic contains example code that shows how to implement a client-side UI Automation provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc043-106">例</span><span class="sxs-lookup"><span data-stu-id="cc043-106">Example</span></span>  
 <span data-ttu-id="cc043-107">The following example code can be built into a dynamic-link library (DLL) that implements a very simple client-side provider for a console window.</span><span class="sxs-lookup"><span data-stu-id="cc043-107">The following example code can be built into a dynamic-link library (DLL) that implements a very simple client-side provider for a console window.</span></span> <span data-ttu-id="cc043-108">このコードは、有用な機能は備えていませんが、UI オートメーション クライアント アプリケーションによって登録できるプロバイダー アセンブリを設定する際の基本的な手順を示すために用意されています。</span><span class="sxs-lookup"><span data-stu-id="cc043-108">The code does not have any useful functionality, but is intended to demonstrate the basic steps in setting up a provider assembly that can be registered by a UI Automation client application.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSProviderProgram.cs#101)]
 [!code-vb[UIAClientSideProvider_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csproviderprogram.vb#101)]  
  
## <a name="see-also"></a><span data-ttu-id="cc043-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc043-109">See also</span></span>

- [<span data-ttu-id="cc043-110">UI オートメーション プロバイダーの概要</span><span class="sxs-lookup"><span data-stu-id="cc043-110">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="cc043-111">クライアント側プロバイダー アセンブリの登録</span><span class="sxs-lookup"><span data-stu-id="cc043-111">Register a Client-Side Provider Assembly</span></span>](register-a-client-side-provider-assembly.md)
