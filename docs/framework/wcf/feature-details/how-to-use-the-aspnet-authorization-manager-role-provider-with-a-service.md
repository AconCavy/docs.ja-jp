---
title: '方法 : ASP.NET の承認マネージャー ロール プロバイダーとサービスを使用する'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 20955578ce4d344c2057036c0944557edf737389
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212222"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a><span data-ttu-id="b51cd-102">方法 : ASP.NET の承認マネージャー ロール プロバイダーとサービスを使用する</span><span class="sxs-lookup"><span data-stu-id="b51cd-102">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>
<span data-ttu-id="b51cd-103">ASP.NET が Web サービスをホストする場合、承認マネージャーをアプリケーションに統合して、サービスに承認を提供できます。</span><span class="sxs-lookup"><span data-stu-id="b51cd-103">When ASP.NET hosts a Web service, you can integrate Authorization Manager into the application to provide authorization to the service.</span></span> <span data-ttu-id="b51cd-104">承認マネージャーを使用して、アプリケーション開発者は個々の操作を定義できます。また、個々の操作をグループ化してタスクを形成できます。</span><span class="sxs-lookup"><span data-stu-id="b51cd-104">Authorization Manager enables an application developer to define individual operations, which can be grouped together to form tasks.</span></span> <span data-ttu-id="b51cd-105">次に管理者は、ロールを承認して特定のタスクまたは個々の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="b51cd-105">An administrator can then authorize roles to perform specific tasks or individual operations.</span></span> <span data-ttu-id="b51cd-106">承認マネージャーでは、ロール、タスク、操作、ユーザーを管理する管理ツールとして Microsoft 管理コンソール (MMC) スナップインが提供されます。</span><span class="sxs-lookup"><span data-stu-id="b51cd-106">Authorization Manager provides an administration tool as a Microsoft Management Console (MMC) snap-in to manage roles, tasks, operations, and users.</span></span> <span data-ttu-id="b51cd-107">管理者は、承認マネージャーのポリシー ストアを XML ファイル、Active Directory、または Active Directory アプリケーション モード (ADAM) ストアに構成します。</span><span class="sxs-lookup"><span data-stu-id="b51cd-107">Administrators configure an Authorization Manager policy store in an XML file, Active Directory, or in an Active Directory Application Mode (ADAM) store.</span></span>  
  
 <span data-ttu-id="b51cd-108">承認マネージャーは、Web サービスをホストする ASP.NET アプリケーションの承認マネージャー ASP.NET ロールプロバイダーを構成することによって、アプリケーションに統合されます。</span><span class="sxs-lookup"><span data-stu-id="b51cd-108">Authorization Manager is Integrated into the application by configuring the Authorization Manager ASP.NET role provider for the ASP.NET application that is hosting the Web service.</span></span> <span data-ttu-id="b51cd-109">他の ASP.NET ロールプロバイダーと同様に、Authorization Manager ASP.NET ロールプロバイダーは <`providers`> 要素を使用して構成されます。</span><span class="sxs-lookup"><span data-stu-id="b51cd-109">Like other ASP.NET role providers, the Authorization Manager ASP.NET role provider is configured using the <`providers`> element.</span></span>  
  
 <span data-ttu-id="b51cd-110">承認マネージャーをアプリケーションに統合する Web サービスの構成ファイルの一部を示すコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b51cd-110">The following code example is a portion of a configuration file for a Web service that is integrating Authorization Manager into the application.</span></span>  
  
```xml  
<system.web>  
    <roleManager enabled="true" defaultProvider="AzManRoleProvider">  
      <providers>  
        <add name="AzManRoleProvider"  
             type="System.Web.Security.AuthorizationStoreRoleProvider, System.Web, Version=2.0.0.0, Culture=neutral, publicKeyToken=b03f5f7f11d50a3a"  
             connectionStringName="AzManPolicyStoreConnectionString"   
             applicationName="SecureService"/>  
      </providers>  
    </roleManager>  
</system.web>  
```  
  
 <span data-ttu-id="b51cd-111">ASP.NET ロールプロバイダーと WCF アプリケーションの統合の詳細については、「[方法: ASP.NET Role プロバイダーをサービスで使用](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b51cd-111">For more information about integrating an ASP.NET role provider with a WCF application, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span> <span data-ttu-id="b51cd-112">ASP.NET で承認マネージャーを使用する方法の詳細については、「[方法: 承認マネージャー (AzMan) と ASP.NET 2.0 を使用](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10))する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b51cd-112">For more information about using Authorization Manager with ASP.NET, see [How to: Use Authorization Manager (AzMan) with ASP.NET 2.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b51cd-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="b51cd-113">See also</span></span>

- [<span data-ttu-id="b51cd-114">方法 : ASP.NET のロール プロバイダーとサービスを使用する</span><span class="sxs-lookup"><span data-stu-id="b51cd-114">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
