---
title: クライアント側プロバイダー アセンブリの登録
description: クライアント側 UI オートメーションプロバイダーを含む DLL を登録する方法を示す例を確認します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- registering client-side provider assemblies
- client-side provider assemblies, registering
- UI Automation, registering provider assemblies
- provider assemblies, registering
ms.assetid: a03af4d9-2771-43cc-b07b-d468dca23190
ms.openlocfilehash: 034a109bb69c08883c0943b7b6ef69a397a8e7e1
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168134"
---
# <a name="register-a-client-side-provider-assembly"></a><span data-ttu-id="36ed8-103">クライアント側プロバイダー アセンブリの登録</span><span class="sxs-lookup"><span data-stu-id="36ed8-103">Register a Client-Side Provider Assembly</span></span>
> [!NOTE]
> <span data-ttu-id="36ed8-104">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="36ed8-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="36ed8-105">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="36ed8-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="36ed8-106">このトピックでは、クライアント側 UI オートメーション プロバイダーを格納する DLL を登録する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="36ed8-106">This topic shows how to register a DLL that contains client-side UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36ed8-107">例</span><span class="sxs-lookup"><span data-stu-id="36ed8-107">Example</span></span>  
 <span data-ttu-id="36ed8-108">次の例では、コンソール ウィンドウのプロバイダーを格納するアセンブリを登録する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="36ed8-108">The following example shows how to register an assembly that contains a provider for a console window.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSClientProgram.cs#102)]
 [!code-vb[UIAClientSideProvider_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csclientprogram.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="36ed8-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="36ed8-109">See also</span></span>

- [<span data-ttu-id="36ed8-110">クライアント側 UI オートメーション プロバイダーの作成</span><span class="sxs-lookup"><span data-stu-id="36ed8-110">Create a Client-Side UI Automation Provider</span></span>](create-a-client-side-ui-automation-provider.md)
