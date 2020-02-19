---
title: WCF 構成スキーマ
ms.date: 03/30/2017
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
ms.openlocfilehash: 866b0639f4391e1898bbe36e458df87e3c24bfff
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2020
ms.locfileid: "77448660"
---
# <a name="wcf-configuration-schema"></a><span data-ttu-id="5e4b4-102">WCF 構成スキーマ</span><span class="sxs-lookup"><span data-stu-id="5e4b4-102">WCF Configuration Schema</span></span>
<span data-ttu-id="5e4b4-103">Windows Communication Foundation (WCF) 構成要素を使用すると、WCF サービスとクライアントアプリケーションを構成できます。</span><span class="sxs-lookup"><span data-stu-id="5e4b4-103">Windows Communication Foundation (WCF) configuration elements enable you to configure WCF service and client applications.</span></span> <span data-ttu-id="5e4b4-104">[ 構成エディター ツール (SvcConfigEditor.exe)](../../../wcf/configuration-editor-tool-svcconfigeditor-exe.md) を使用して、クライアントとサービスの構成ファイルを作成および変更できます。</span><span class="sxs-lookup"><span data-stu-id="5e4b4-104">You can use the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../wcf/configuration-editor-tool-svcconfigeditor-exe.md) to create and modify configuration files for clients and services.</span></span> <span data-ttu-id="5e4b4-105">構成ファイルは XML として書式設定されているので、テキスト エディターを使用して手動で編集する場合は、XML について理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e4b4-105">Since the configuration files are formatted as XML, you must be familiar with XML if you want to manually edit them using a text editor.</span></span> <span data-ttu-id="5e4b4-106">理解しないで編集すると、XML 要素タグや属性が見つからないなどの問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5e4b4-106">Otherwise, you may run into issues such as an unfound XML element tag or attribute.</span></span> <span data-ttu-id="5e4b4-107">問題の原因は、XML 要素タグと属性が大文字と小文字を区別することによります。</span><span class="sxs-lookup"><span data-stu-id="5e4b4-107">This is because XML element tags and attributes are case-sensitive.</span></span>  
  
 <span data-ttu-id="5e4b4-108">WCF 構成システムは、<xref:System.Configuration> 名前空間に基づいています。</span><span class="sxs-lookup"><span data-stu-id="5e4b4-108">The WCF configuration system is based on the <xref:System.Configuration> namespace.</span></span> <span data-ttu-id="5e4b4-109">したがって、<xref:System.Configuration> 名前空間によって提供される、構成ロック、暗号化、マージなどのすべての標準機能を使用して、アプリケーションとその構成のセキュリティを強化できます。</span><span class="sxs-lookup"><span data-stu-id="5e4b4-109">Therefore, you can use all the standard features provided by the <xref:System.Configuration> namespace, such as configuration locking, encryption and merging to increase the security of your application and its configuration.</span></span> <span data-ttu-id="5e4b4-110">これらの概念の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5e4b4-110">For more information on these concepts, see the following topics.</span></span>  
  
 <span data-ttu-id="5e4b4-111">[保護された構成を使用した構成情報の暗号化](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5e4b4-111">[Encrypting Configuration Information](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100))</span></span>  
  
 <span data-ttu-id="5e4b4-112">[構成設定のロック](https://docs.microsoft.com/previous-versions/aspnet/55th21y4(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5e4b4-112">[Locking Configuration Settings](https://docs.microsoft.com/previous-versions/aspnet/55th21y4(v=vs.100))</span></span>  
  
 <span data-ttu-id="5e4b4-113">このセクションでは、各構成項目のすべての可能な値についてと各構成項目が他の WCF 構成要素とやり取りする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5e4b4-113">This section describes all possible values of each configuration item, and how it interacts with other WCF configuration elements.</span></span> <span data-ttu-id="5e4b4-114">次のマップは、WCF 構成スキーマを示しています。</span><span class="sxs-lookup"><span data-stu-id="5e4b4-114">The following map illustrates the WCF configuration schema:</span></span>  
  
 ![WCF 構成スキーマを示す図。](./media/index/windows-communication-foundation-configuration-schema.gif)  
  
> [!CAUTION]
> <span data-ttu-id="5e4b4-116">アプリケーション構成ファイル (app.config) の WCF 構成セクションは、適切な Access Control リスト (ACL) を使用して保護し、潜在的なセキュリティ上の脅威を防ぐ必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e4b4-116">You should protect WCF configuration sections in your application configuration files (app.config) with appropriate Access Control Lists (ACL) to prevent any potential security threats.</span></span>  <span data-ttu-id="5e4b4-117">たとえば、適切なユーザーだけが、アプリケーション バインドのセキュリティ設定、またはサービスの構成ファイルのサービス モデル セクションにアクセスまたは変更できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e4b4-117">For example, you should make sure that only the appropriate people can access or modify the security settings on application bindings, or the service model section of the configuration file for a service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5e4b4-118">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="5e4b4-118">In This Section</span></span>  
 [<span data-ttu-id="5e4b4-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5e4b4-119">\<system.serviceModel></span></span>](system-servicemodel.md)  
 <span data-ttu-id="5e4b4-120">`ServiceModel` 要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="5e4b4-120">Describes the `ServiceModel` element.</span></span>  
  
 [<span data-ttu-id="5e4b4-121">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="5e4b4-121">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)  
 <span data-ttu-id="5e4b4-122">SMSvcHost.exe ツールを構成します。</span><span class="sxs-lookup"><span data-stu-id="5e4b4-122">Configures the SMSvcHost.exe tool.</span></span>  
  
 [<span data-ttu-id="5e4b4-123">\<system.runtime.serialization ></span><span class="sxs-lookup"><span data-stu-id="5e4b4-123">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)  
 <span data-ttu-id="5e4b4-124"><xref:System.Runtime.Serialization.DataContractSerializer> などのシリアライザーの使用時にオプションを設定するための最上位の要素。</span><span class="sxs-lookup"><span data-stu-id="5e4b4-124">The top-level element for setting options when using serializers such as the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5e4b4-125">関連セクション</span><span class="sxs-lookup"><span data-stu-id="5e4b4-125">Related Sections</span></span>  
 [<span data-ttu-id="5e4b4-126">Windows Communication Foundation アプリケーションの構成</span><span class="sxs-lookup"><span data-stu-id="5e4b4-126">Configuring Windows Communication Foundation Applications</span></span>](../../../wcf/configuring-services.md)  
 <span data-ttu-id="5e4b4-127">WCF サービスとクライアントを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5e4b4-127">Describes how to configure WCF services and clients.</span></span>
