---
title: '方法: サービスのインスタンス化を制御する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e0b12b34-8004-443a-a46d-83a5c00f2601
ms.openlocfilehash: 8a73dd90d268c61e0df974861753119e205a870f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599075"
---
# <a name="how-to-control-service-instancing"></a><span data-ttu-id="d808f-102">方法: サービスのインスタンス化を制御する</span><span class="sxs-lookup"><span data-stu-id="d808f-102">How to: Control Service Instancing</span></span>
<span data-ttu-id="d808f-103">サービスのインスタンス モードを設定することにより、<xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (およびそのユーザー定義のサービス オブジェクト) をいつ生成するかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="d808f-103">Setting the instance mode of a service enables you to specify when a <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (and its associated user-defined service object) is created.</span></span> <span data-ttu-id="d808f-104">設定できるモードについては、<xref:System.ServiceModel.InstanceContextMode> 列挙体を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d808f-104">See the <xref:System.ServiceModel.InstanceContextMode> enumeration for the possible modes.</span></span> <span data-ttu-id="d808f-105">動作の詳細については、「動作を使用した[ランタイムの構成と拡張](../extending/configuring-and-extending-the-runtime-with-behaviors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d808f-105">For more information about behaviors, see [Configuring and Extending the Runtime with Behaviors](../extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span> <span data-ttu-id="d808f-106">実際の例については、「[動作](../samples/behaviors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d808f-106">For working examples, see [Behaviors](../samples/behaviors.md).</span></span>  
  
### <a name="to-control-the-service-instance-lifetime-using-code"></a><span data-ttu-id="d808f-107">サービス インスタンスの有効期間をコードで制御するには</span><span class="sxs-lookup"><span data-stu-id="d808f-107">To control the service instance lifetime using code</span></span>  
  
1. <span data-ttu-id="d808f-108">サービス クラスに <xref:System.ServiceModel.ServiceBehaviorAttribute> 属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="d808f-108">Apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> to the service class.</span></span>  
  
2. <span data-ttu-id="d808f-109"><xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> プロパティを <xref:System.ServiceModel.InstanceContextMode.PerCall>、<xref:System.ServiceModel.InstanceContextMode.PerSession>、<xref:System.ServiceModel.InstanceContextMode.Single> のいずれかの値に設定します。</span><span class="sxs-lookup"><span data-stu-id="d808f-109">Set the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property to one of the following values: <xref:System.ServiceModel.InstanceContextMode.PerCall>, <xref:System.ServiceModel.InstanceContextMode.PerSession>, or <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span>  
  
     [!code-csharp[C_ControlServiceInstancing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#1)]
     [!code-vb[C_ControlServiceInstancing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="d808f-110">例</span><span class="sxs-lookup"><span data-stu-id="d808f-110">Example</span></span>  
 <span data-ttu-id="d808f-111"><xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 属性の <xref:System.ServiceModel.ServiceBehaviorAttribute> プロパティを <xref:System.ServiceModel.InstanceContextMode.PerCall> に設定するコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="d808f-111">The following code example sets the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property of the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to <xref:System.ServiceModel.InstanceContextMode.PerCall>.</span></span>  
  
 [!code-csharp[c_ControlServiceInstancing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#2)]
 [!code-vb[c_ControlServiceInstancing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d808f-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="d808f-112">See also</span></span>

- <xref:System.ServiceModel.ServiceBehaviorAttribute>
- <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>
- <xref:System.ServiceModel.InstanceContextMode>
- [<span data-ttu-id="d808f-113">サービス : 動作サンプル</span><span class="sxs-lookup"><span data-stu-id="d808f-113">Service: Behaviors Samples</span></span>](../samples/behaviors.md)
