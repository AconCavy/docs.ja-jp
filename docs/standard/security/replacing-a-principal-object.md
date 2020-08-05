---
title: プリンシパル オブジェクトの置き換え
ms.date: 07/15/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- principal objects, replacing
- security [.NET], replacing principal objects
- security [.NET], principals
ms.assetid: c323687e-b196-487b-beba-f38f9b3f961b
ms.openlocfilehash: fced91aef991bc228e65128d5e8d69e6a46588e5
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557100"
---
# <a name="replacing-a-principal-object"></a><span data-ttu-id="e0ba4-102">プリンシパル オブジェクトの置き換え</span><span class="sxs-lookup"><span data-stu-id="e0ba4-102">Replacing a Principal Object</span></span>

<span data-ttu-id="e0ba4-103">認証サービスを提供するアプリケーションでは、特定のスレッドの **プリンシパル** オブジェクト (<xref:System.Security.Principal.IPrincipal>) を置換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0ba4-103">Applications that provide authentication services must be able to replace the **Principal** object (<xref:System.Security.Principal.IPrincipal>) for a given thread.</span></span> <span data-ttu-id="e0ba4-104">さらに、虚偽の ID やロールを要求することにより、悪意をもってアタッチされた不適切な **プリンシパル** がアプリケーションのセキュリティに問題を生じさせるため、セキュリティ システムを活用して **プリンシパル** オブジェクトを置き換える機能を保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0ba4-104">Furthermore, the security system must help protect the ability to replace **Principal** objects because a maliciously attached, incorrect **Principal** compromises the security of your application by claiming an untrue identity or role.</span></span> <span data-ttu-id="e0ba4-105">そのため、 **プリンシパル** オブジェクトを置き換える機能を必要とするアプリケーションに、プリンシパルを制御するための <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> オブジェクトを付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0ba4-105">Therefore, applications that require the ability to replace **Principal** objects must be granted the <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> object for principal control.</span></span> <span data-ttu-id="e0ba4-106">(ロール ベースのセキュリティ チェックを実行する、または **プリンシパル** オブジェクトを作成するために、このアクセス許可は必要がないことに注意してください。)</span><span class="sxs-lookup"><span data-stu-id="e0ba4-106">(Note that this permission is not required for performing role-based security checks or for creating **Principal** objects.)</span></span>  
  
<span data-ttu-id="e0ba4-107">次のタスクを実行することによって、現在の **プリンシパル** オブジェクトを置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="e0ba4-107">The current **Principal** object can be replaced by performing the following tasks:</span></span>  
  
1. <span data-ttu-id="e0ba4-108">置き換える **プリンシパル** オブジェクトと関連付けられている **ID** オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="e0ba4-108">Create the replacement **Principal** object and associated **Identity** object.</span></span>  
  
2. <span data-ttu-id="e0ba4-109">新しい **プリンシパル** オブジェクトを呼び出しコンテキストにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="e0ba4-109">Attach the new **Principal** object to the call context.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0ba4-110">例</span><span class="sxs-lookup"><span data-stu-id="e0ba4-110">Example</span></span>

<span data-ttu-id="e0ba4-111">次の例では、汎用プリンシパル オブジェクトを作成し、それを使用してスレッドのプリンシパルを設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e0ba4-111">The following example shows how to create a generic principal object and use it to set the principal of a thread.</span></span>  
  
[!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
[!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e0ba4-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="e0ba4-112">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>
- [<span data-ttu-id="e0ba4-113">プリンシパル オブジェクトと ID オブジェクト</span><span class="sxs-lookup"><span data-stu-id="e0ba4-113">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
- [<span data-ttu-id="e0ba4-114">ASP.NET Core のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="e0ba4-114">ASP.NET Core Security</span></span>](/aspnet/core/security/)
