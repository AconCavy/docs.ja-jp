---
title: UI オートメーションを使用した、チェック ボックスのトグル状態の取得
description: Microsoft UI オートメーションを使用して、コントロール (チェックボックスなど) のトグル状態を取得する方法を示すコード例を参照してください。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, getting toggle states of check boxes
- check boxes, getting toggle states of
- getting, toggle states of check boxes
ms.assetid: 84fc31a3-175f-4e93-90a0-dd29d89b77ce
ms.openlocfilehash: 2ec0cc996461b13d0ddc3453188eeb3287a56be7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276439"
---
# <a name="get-the-toggle-state-of-a-check-box-using-ui-automation"></a>UI オートメーションを使用した、チェック ボックスのトグル状態の取得

> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。  
  
 このトピックでは、を使用し [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] て、コントロールのトグル状態を取得する方法について説明します。  
  
## <a name="example"></a>例  

 この例では、 <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> クラスのメソッドを使用し <xref:System.Windows.Automation.AutomationElement> て、 <xref:System.Windows.Automation.TogglePattern> コントロールからオブジェクトを取得し、そのプロパティを返し <xref:System.Windows.Automation.ToggleState> ます。  
  
 [!code-csharp[NavigatingWithTreeWalker#1200](../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigatingWithTreeWalker/CSharp/ClientClass.cs#1200)]
 [!code-vb[NavigatingWithTreeWalker#1200](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigatingWithTreeWalker/visualbasic/clientclass.vb#1200)]
