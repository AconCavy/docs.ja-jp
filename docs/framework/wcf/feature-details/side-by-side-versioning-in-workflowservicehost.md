---
title: WorkflowServiceHost による side-by-side でのバージョン管理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 60887eed-df40-4412-b812-41e1dd329d15
ms.openlocfilehash: bc662e51c96a06737e1bd6fd78d5f70f3922d080
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184474"
---
# <a name="side-by-side-versioning-in-workflowservicehost"></a><span data-ttu-id="76699-102">WorkflowServiceHost による side-by-side でのバージョン管理</span><span class="sxs-lookup"><span data-stu-id="76699-102">Side by Side Versioning in WorkflowServiceHost</span></span>
<span data-ttu-id="76699-103">.NET Framework 4.5 で導入されたサイド バイ サイド バージョン管理では<xref:System.ServiceModel.Activities.WorkflowServiceHost>、1 つのエンドポイントで複数のバージョンのワークフロー サービスをホストする機能が提供されます。</span><span class="sxs-lookup"><span data-stu-id="76699-103">The <xref:System.ServiceModel.Activities.WorkflowServiceHost> side-by-side versioning introduced in .NET Framework 4.5 provides the capability to host multiple versions of a workflow service on a single endpoint.</span></span> <span data-ttu-id="76699-104">提供される side-by-side 機能により、既存の定義を使用してインスタンスを実行しているときに、新しいワークフロー定義を使用してワークフロー サービスの新しいインスタンスが作成されるように、ワークフロー サービスを構成できます。</span><span class="sxs-lookup"><span data-stu-id="76699-104">The side-by-side functionality provided allows a workflow service to be configured so that new instances of the workflow service are created using the new workflow definition, while running instances complete using the existing definition.</span></span> <span data-ttu-id="76699-105">このトピックでは、<xref:System.ServiceModel.Activities.WorkflowServiceHost> を使用したワークフロー サービスの side-by-side での実行の概要を提供します。</span><span class="sxs-lookup"><span data-stu-id="76699-105">This topic provides an overview of workflow service side-by-side execution using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76699-106">サンプルをダウンロードして、ワークフロー サービスのサイド バイ サイド バージョン管理のビデオ チュートリアルを見る方法については[、「Web ホスト Xamlx ワークフロー サービスとのサイド バイ サイド バージョニング](https://go.microsoft.com/fwlink/?LinkId=393746)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76699-106">To download a sample and watch a video walkthrough of workflow service side-by-side versioning, see [Side by Side Versioning with a Web-Hosted Xamlx Workflow Service](https://go.microsoft.com/fwlink/?LinkId=393746).</span></span>  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a><span data-ttu-id="76699-107">ワークフロー サービスでの複数のバージョンのホスティング</span><span class="sxs-lookup"><span data-stu-id="76699-107">Hosting Multiple Versions in a Workflow Service</span></span>  
 <span data-ttu-id="76699-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost> には、ワークフローの複数のバージョンを side-by-side 実行するように構成できる <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> と <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> の 2 つのプロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="76699-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost> contains two properties that can be configured to allow multiple versions of a workflow to execute side-by-side: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="76699-109"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> には、ワークフロー サービスのサポートされているバージョンが含まれます。<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> は、各ワークフロー サービスを一意に識別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="76699-109"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> contains the supported versions of the workflow service, and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is used to uniquely identify each workflow service.</span></span> <span data-ttu-id="76699-110">これは、<xref:System.Activities.WorkflowIdentity> をワークフロー サービスと関連付けることによって行われます。</span><span class="sxs-lookup"><span data-stu-id="76699-110">This is done by associating a <xref:System.Activities.WorkflowIdentity> with the workflow service.</span></span> <span data-ttu-id="76699-111"><xref:System.Activities.WorkflowIdentity> には 3 種類の識別情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="76699-111">A <xref:System.Activities.WorkflowIdentity> contains three identifying pieces of information.</span></span> <span data-ttu-id="76699-112"><xref:System.Activities.WorkflowIdentity.Name%2A> と <xref:System.Activities.WorkflowIdentity.Version%2A> は必須で、名前と <xref:System.Version> を表します。また、<xref:System.Activities.WorkflowIdentity.Package%2A> は省略可能で、アセンブリ名やその他の必要な情報などの情報を格納する追加文字列の指定に使用できます。</span><span class="sxs-lookup"><span data-stu-id="76699-112"><xref:System.Activities.WorkflowIdentity.Name%2A> and <xref:System.Activities.WorkflowIdentity.Version%2A> contain a name and a <xref:System.Version> and are required, and <xref:System.Activities.WorkflowIdentity.Package%2A> is optional and can be used to specify an additional string containing information such as assembly name or other desired information.</span></span> <span data-ttu-id="76699-113"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> コレクションに含まれる各ワークフロー サービスは、一意の <xref:System.Activities.WorkflowIdentity> を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="76699-113">Each workflow service contained in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection must have a unique <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="76699-114"><xref:System.Activities.WorkflowIdentity> は、その 3 つのプロパティのいずれかが他の <xref:System.Activities.WorkflowIdentity> と異なる場合に一意です。</span><span class="sxs-lookup"><span data-stu-id="76699-114">A <xref:System.Activities.WorkflowIdentity> is unique if any of its three properties are different from another <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="76699-115">は`null`<xref:System.Activities.WorkflowIdentity>に指定できる値<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>ですが、以前のバージョンの ワークフロー サービスは`null`<xref:System.Activities.WorkflowIdentity>1 つだけを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="76699-115">A `null` <xref:System.Activities.WorkflowIdentity> is an allowable value for <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but only one previous version of a workflow service may have a `null` <xref:System.Activities.WorkflowIdentity>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="76699-116"><xref:System.Activities.WorkflowIdentity> には、個人を特定できる情報 (PII) を含めないでください。</span><span class="sxs-lookup"><span data-stu-id="76699-116">A <xref:System.Activities.WorkflowIdentity> should not contain any personally identifiable information (PII).</span></span> <span data-ttu-id="76699-117"><xref:System.Activities.WorkflowIdentity> は、<xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>)、<xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>)、および <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>) の 3 つの部分で構成されます。</span><span class="sxs-lookup"><span data-stu-id="76699-117"><xref:System.Activities.WorkflowIdentity> is composed of three parts: a <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), a <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>), and a <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>).</span></span> <span data-ttu-id="76699-118">インスタンスの作成に使用される <xref:System.Activities.WorkflowIdentity> に関する情報は、ランタイムによるアクティビティ ライフ サイクルのさまざまなポイントで構成されているすべての追跡サービスに出力されます。</span><span class="sxs-lookup"><span data-stu-id="76699-118">Information about the <xref:System.Activities.WorkflowIdentity> used to create an instance is emitted to any configured tracking services at several different points of the activity life-cycle by the runtime.</span></span> <span data-ttu-id="76699-119">WF の追跡には PII (機密ユーザー データ) を非表示にするメカニズムがありません。</span><span class="sxs-lookup"><span data-stu-id="76699-119">WF Tracking does not have any mechanism to hide PII (sensitive user data).</span></span> <span data-ttu-id="76699-120">そのため、<xref:System.Activities.WorkflowIdentity> インスタンスには PII データを含めないでください。PII データは、ランタイムによって追跡レコードに出力され、追跡レコードを表示するためのアクセス権を持つユーザーに表示できます。</span><span class="sxs-lookup"><span data-stu-id="76699-120">Therefore, a <xref:System.Activities.WorkflowIdentity> instance should not contain any PII data as it will be emitted by the runtime in tracking records and may be visible to anyone with access to view the tracking records.</span></span>  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a><span data-ttu-id="76699-121">ワークフロー サービスでの複数のバージョンのホスティングに関する規則</span><span class="sxs-lookup"><span data-stu-id="76699-121">Rules for Hosting Multiple Versions of a Workflow Service</span></span>  
 <span data-ttu-id="76699-122">ユーザーが追加のバージョンを <xref:System.ServiceModel.Activities.WorkflowServiceHost> に追加する場合、エンドポイントと説明の同じセットを使用してワークフロー サービスをホストするために満たす必要があるいくつかの条件があります。</span><span class="sxs-lookup"><span data-stu-id="76699-122">When a user adds an additional version to the <xref:System.ServiceModel.Activities.WorkflowServiceHost>, there are several conditions that must be met in order for a workflow service to be hosted with the same set of endpoints and description.</span></span> <span data-ttu-id="76699-123">追加のバージョンのいずれかがこれらの条件を満たすことができない場合、<xref:System.ServiceModel.Activities.WorkflowServiceHost> は `Open` が呼び出されたときに例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="76699-123">If any of the additional versions fail to meet these conditions, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> throws an exception when `Open` is called.</span></span> <span data-ttu-id="76699-124">追加のバージョンとしてホストに提供される各ワークフロー定義は、次の要件を満たす必要があります (プライマリ バージョンは、ホストのコンストラクターに提供されるワークフロー サービス定義です)。</span><span class="sxs-lookup"><span data-stu-id="76699-124">Each workflow definition provided to the host as an additional version must meet the following requirements (where the primary version is the workflow service definition that is provided to the host constructor).</span></span> <span data-ttu-id="76699-125">追加のワークフローのバージョンは、次の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="76699-125">The additional workflow version must:</span></span>  
  
- <span data-ttu-id="76699-126">ワークフロー サービスのプライマリ バージョンと同じ <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="76699-126">Have the same the <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> as the primary version of the workflow service.</span></span>  
  
- <span data-ttu-id="76699-127">プライマリ バージョンにない <xref:System.ServiceModel.Activities.Receive> に <xref:System.ServiceModel.Activities.SendReply> アクティビティまたは <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> アクティビティがあってはならず、これらは操作コントラクトに一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="76699-127">Must not have any <xref:System.ServiceModel.Activities.Receive> or <xref:System.ServiceModel.Activities.SendReply> activities in its <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> that are not in the primary version, and they must match the operation contract.</span></span>  
  
- <span data-ttu-id="76699-128">一意の <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="76699-128">Have a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="76699-129">`null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> を持つことができるワークフロー定義は 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="76699-129">One and only one workflow definition may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
 <span data-ttu-id="76699-130">一部の変更は可能です。</span><span class="sxs-lookup"><span data-stu-id="76699-130">Some changes are permitted.</span></span> <span data-ttu-id="76699-131">次の項目は、バージョン間で異なることができます。</span><span class="sxs-lookup"><span data-stu-id="76699-131">The following items may be different between the versions:</span></span>  
  
- <span data-ttu-id="76699-132"><xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> は、プライマリ バージョンと異なる名前およびパッケージを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="76699-132">The <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> may have a different Name and Package than the primary version.</span></span>  
  
- <span data-ttu-id="76699-133"><xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> 値は、プライマリ バージョンと異なることができます。</span><span class="sxs-lookup"><span data-stu-id="76699-133">The <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> value may be different than the primary version.</span></span>  
  
- <span data-ttu-id="76699-134"><xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> 値は、プライマリ バージョンと異なることができます。</span><span class="sxs-lookup"><span data-stu-id="76699-134">The <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> may be different than the primary version.</span></span>  
  
- <span data-ttu-id="76699-135"><xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> 値は、プライマリ バージョンと異なることができます。</span><span class="sxs-lookup"><span data-stu-id="76699-135">The <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> may be different than the primary version.</span></span>  
  
### <a name="configuring-the-definitionidentity"></a><span data-ttu-id="76699-136">DefinitionIdentity の構成</span><span class="sxs-lookup"><span data-stu-id="76699-136">Configuring the DefinitionIdentity</span></span>  
 <span data-ttu-id="76699-137">ワークフロー デザイナーを使用してワークフロー サービスを作成すると<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>、 は **[プロパティ]** ウィンドウを使用して設定されます。</span><span class="sxs-lookup"><span data-stu-id="76699-137">When a workflow service is created using the workflow designer, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is set using the **Properties** window.</span></span> <span data-ttu-id="76699-138">デザイナーでサービスのルート アクティビティの外側をクリックしてワークフロー サービスを選択し、[**表示**] メニューの **[プロパティ] ウィンドウ**を選択します。</span><span class="sxs-lookup"><span data-stu-id="76699-138">Click outside of the service’s root activity in the designer to select the workflow service, and choose **Properties Window** from the **View** menu.</span></span> <span data-ttu-id="76699-139">DefinitionIdentity プロパティの横に表示されるドロップダウン リストから **[WorkflowIdentity]** を選択し、目的<xref:System.Activities.WorkflowIdentity>のプロパティを展開して指定します。 **DefinitionIdentity**</span><span class="sxs-lookup"><span data-stu-id="76699-139">Select **WorkflowIdentity** from the drop-down list that appears beside the **DefinitionIdentity** property, and then expand and specify the desired <xref:System.Activities.WorkflowIdentity> properties.</span></span> <span data-ttu-id="76699-140">次の例では、 <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> <xref:System.Activities.WorkflowIdentity.Name%2A>`MortgageWorkflow`と の を<xref:System.Activities.WorkflowIdentity.Version%2A>使用`1.0.0.0`して構成します。</span><span class="sxs-lookup"><span data-stu-id="76699-140">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `1.0.0.0`.</span></span> <span data-ttu-id="76699-141"><xref:System.Activities.WorkflowIdentity.Package%2A> は省略可能です。この例では、`null` です。</span><span class="sxs-lookup"><span data-stu-id="76699-141"><xref:System.Activities.WorkflowIdentity.Package%2A> is optional and in this example is `null`.</span></span>  
  
 ![プロパティを示すスクリーンショット。](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-property.bmp)  
  
 <span data-ttu-id="76699-143">ワークフロー サービスが自己ホスト型の場合、<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> はワークフロー サービスを構築するときに構成されます。</span><span class="sxs-lookup"><span data-stu-id="76699-143">When a workflow service is self-hosted, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured when the workflow service is constructed.</span></span> <span data-ttu-id="76699-144">次の例では、<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>は、 の と を使用して、前の<xref:System.Activities.WorkflowIdentity.Name%2A>`MortgageWorkflow`例と<xref:System.Activities.WorkflowIdentity.Name%2A>同`1.0.0.0`じ値で構成されています。</span><span class="sxs-lookup"><span data-stu-id="76699-144">In the following example, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the same values as the previous example, with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Name%2A> of `1.0.0.0`.</span></span>  
  
```csharp  
WorkflowService service = new WorkflowService  
{  
    Name = "MortgageWorkflowService",  
    Body = new MortgageWorkflow(),  
    DefinitionIdentity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow",  
        Version = new Version(1, 0, 0, 0)  
    }  
};  
```  
  
```vb  
Dim service As New WorkflowService  
With service  
    .Name = "MortgageWorkflowService"  
    .Body = New MortgageWorkflow  
    .DefinitionIdentity = New WorkflowIdentity With _  
    { _  
        .Name = "MortgageWorkflow", _  
        .Version = New Version(1, 0, 0, 0) _  
    }  
End With  
```  
  
 <span data-ttu-id="76699-145">A<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>は必須ではありませんが、1 つのバージョンのワークフロー サービスに**null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>を設定する場合があります。</span><span class="sxs-lookup"><span data-stu-id="76699-145">A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is not required, although only one version of the workflow service may have a **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76699-146">これは、最初に <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> を構成せずにサービスを配置し、後で更新されたバージョンを作成する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="76699-146">This is useful if the service was deployed initially without a <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> configured, and then an updated version is created.</span></span>  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a><span data-ttu-id="76699-147">Web ホスト ワークフロー サービスへの新しいバージョンの追加</span><span class="sxs-lookup"><span data-stu-id="76699-147">Adding a New Version to a Web-hosted Workflow Service</span></span>  
 <span data-ttu-id="76699-148">Web ホスト サービスで新しいバージョンのワークフロー サービスを構成する最初の手順では、`App_Code` フォルダーにサービス ファイルと同じ名前を持つ新しいフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="76699-148">The first step in configuring a new version of a workflow service in a web-hosted service is to create a new folder in the `App_Code` folder that has the same name as the service file.</span></span> <span data-ttu-id="76699-149">たとえば、サービスの `xamlx` ファイルの名前が `MortgageWorkflow.xamlx` である場合は、フォルダーに `MortgageWorkflow` という名前を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="76699-149">If the service’s `xamlx` file is named `MortgageWorkflow.xamlx`, then the folder must be named `MortgageWorkflow`.</span></span> <span data-ttu-id="76699-150">元のサービスの `xamlx` ファイルをこのフォルダーにコピーした後、新しい名前 (たとえば、`MortgageWorkflowV1.xamlx`) に変更します。</span><span class="sxs-lookup"><span data-stu-id="76699-150">Place a copy of the original service’s `xamlx` file into this folder and rename it to a new name, such as `MortgageWorkflowV1.xamlx`.</span></span> <span data-ttu-id="76699-151">プライマリ サービスに必要な変更を加え、その <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> を更新し、サービスを展開します。</span><span class="sxs-lookup"><span data-stu-id="76699-151">Make the desired changes to the primary service, update its <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, and then deploy the service.</span></span> <span data-ttu-id="76699-152">次の例の <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> は、<xref:System.Activities.WorkflowIdentity.Name%2A> という値の `MortgageWorkflow` と <xref:System.Activities.WorkflowIdentity.Version%2A> という値の `2.0.0.0` で更新されています。</span><span class="sxs-lookup"><span data-stu-id="76699-152">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> has been updated with a <xref:System.Activities.WorkflowIdentity.Name%2A> of `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `2.0.0.0`.</span></span>  
  
 ![ワークフロー ID の定義 ID を示すスクリーンショット。](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-workflowidentity.bmp)  
  
 <span data-ttu-id="76699-154">サービスが再起動されたとき、以前のバージョンは指定された `App_Code` サブフォルダーにないため、<xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> コレクションに自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="76699-154">When the service restarts, the previous version will automatically be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection because it is located in the designated `App_Code` subfolder.</span></span> <span data-ttu-id="76699-155">ワークフロー サービスのプライマリ バージョンに以前のバージョンがある`null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>場合は、追加されません。</span><span class="sxs-lookup"><span data-stu-id="76699-155">Note that if the primary version of the workflow service has a `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> the previous versions will not be added.</span></span> <span data-ttu-id="76699-156">`null` の <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> を持つことができるのは 1 つのバージョンのみです。しかし、複数のバージョンがある場合、プライマリ バージョンは `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> を持つバージョンであることはできません。そうでないと、以前のバージョンが <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> コレクションに追加されません。</span><span class="sxs-lookup"><span data-stu-id="76699-156">One version may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but if there are multiple versions the primary version must not be the one with the `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> or else the previous versions will not be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span>  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a><span data-ttu-id="76699-157">自己ホスト型ワークフロー サービスへの新しいバージョンの追加</span><span class="sxs-lookup"><span data-stu-id="76699-157">Adding a New Version to a Self-hosted Workflow Service</span></span>  
 <span data-ttu-id="76699-158">自己ホスト型ワークフロー サービスに新しいバージョンを追加する場合、ワークフロー サービスのプライマリ バージョンを使用して <xref:System.ServiceModel.Activities.WorkflowServiceHost> が構成されます。以前のバージョンは明示的に <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> コレクションに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="76699-158">When adding a new version to a self-hosted workflow service, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with the primary version of the workflow service, and previous versions must be explicitly added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="76699-159">次の例では、<xref:System.ServiceModel.Activities.WorkflowServiceHost> ワークフロー定義を使用するプライマリ ワークフロー サービスを使用して `MortgageWorkflowV2` が構成されています。さらに、`MortgageWorkflowV1` ワークフロー定義を使用して構成されたワークフロー サービスが <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> コレクションに追加されています。</span><span class="sxs-lookup"><span data-stu-id="76699-159">In the following example, a <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with a primary workflow service that uses a `MortgageWorkflowV2` workflow definition, and a workflow service configured with a `MortgageWorkflowV1` workflow definition is added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="76699-160">各ワークフロー サービスは、ワークフロー定義のバージョンを反映する一意の <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> で構成されます。</span><span class="sxs-lookup"><span data-stu-id="76699-160">Each workflow service is configured with a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> that reflects the version of the workflow definition.</span></span>  
  
```csharp  
// Create the primary version of the workflow service.  
WorkflowService serviceV2 = new WorkflowService  
{  
    Name = "MortgageWorkflowService",  
    Body = new MortgageWorkflowV2(),  
    DefinitionIdentity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow",  
        Version = new Version(2, 0, 0, 0)  
    }  
};  
  
// Configure the WorkflowServiceHost with the current version  
// of the workflow service. This code requires Administrator  
// privileges to function correctly. If running from Visual  
// Studio, Visual Studio must be run with Administrator privileges.  
WorkflowServiceHost host = new WorkflowServiceHost(serviceV2,
    new Uri("http://localhost:8080/MortgageWorkflowService"));  
  
// Create the previous version of the workflow service.  
WorkflowService serviceV1 = new WorkflowService  
{  
    Name = "MortgageWorkflowService",  
    Body = new MortgageWorkflowV1(),  
    DefinitionIdentity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow",  
        Version = new Version(1, 0, 0, 0)  
    }  
};  
  
// Add the previous version of the service to the SupportedVersions collection.  
host.SupportedVersions.Add(serviceV1);  
```  
  
```vb  
'Create the primary version of the workflow service  
Dim serviceV2 As New WorkflowService  
With serviceV2  
    .Name = "MortgageWorkflowService"  
    .Body = New MortgageWorkflowV2  
    .DefinitionIdentity = New WorkflowIdentity With _  
    { _  
        .Name = "MortgageWorkflow", _  
        .Version = New Version(2, 0, 0, 0) _  
    }  
End With  
  
'Configure the WorkflowServiceHost with the current version  
'of the workflow service. This code requires Administrator  
'privileges to function correctly. If running from Visual  
'Studio, Visual Studio must be run with Administrator privileges.  
  
Dim host As New WorkflowServiceHost(serviceV2, _  
    New Uri("http://localhost:8080/MortgageWorkflowService"))  
  
'Create the previous version of the workflow service.  
Dim serviceV1 As New WorkflowService  
With serviceV1  
    .Name = "MortgageWorkflowService"  
    .Body = New MortgageWorkflowV1  
    .DefinitionIdentity = New WorkflowIdentity With _  
    { _  
        .Name = "MortgageWorkflow", _  
        .Version = New Version(1, 0, 0, 0) _  
    }  
End With  
  
'Add the previous version of the service to the SupportedVersions collection.  
host.SupportedVersions.Add(serviceV1)  
```
