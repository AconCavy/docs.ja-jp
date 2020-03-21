---
title: '方法 : カスタム WSDL をインポートする'
ms.date: 03/30/2017
ms.assetid: ddc3718d-ce60-44f6-92af-a5c67477dd99
ms.openlocfilehash: 614842f2d77d967e0a6d4841e5e5e4fcc8805580
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185548"
---
# <a name="how-to-import-custom-wsdl"></a><span data-ttu-id="75895-102">方法 : カスタム WSDL をインポートする</span><span class="sxs-lookup"><span data-stu-id="75895-102">How to: Import Custom WSDL</span></span>
<span data-ttu-id="75895-103">このトピックでは、カスタム WSDL をインポートする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="75895-103">This topic describes how to import custom WSDL.</span></span> <span data-ttu-id="75895-104">カスタム WSDL を処理するには、<xref:System.ServiceModel.Description.IWsdlImportExtension> インターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="75895-104">To handle the custom WSDL, you must implement the <xref:System.ServiceModel.Description.IWsdlImportExtension> interface.</span></span>  
  
### <a name="to-import-custom-wsdl"></a><span data-ttu-id="75895-105">カスタム WSDL をインポートするには</span><span class="sxs-lookup"><span data-stu-id="75895-105">To import custom WSDL</span></span>  
  
1. <span data-ttu-id="75895-106"><xref:System.ServiceModel.Description.IWsdlImportExtension>を実装します。</span><span class="sxs-lookup"><span data-stu-id="75895-106">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension>.</span></span> <span data-ttu-id="75895-107"><xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> メソッドを実装してメタデータをインポートする前に変更します。</span><span class="sxs-lookup"><span data-stu-id="75895-107">Implement the <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> method to modify the metadata before it is imported.</span></span> <span data-ttu-id="75895-108"><xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> メソッドと <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> メソッドを実装してメタデータからインポートされたコントラクトとエンドポイントを変更します。</span><span class="sxs-lookup"><span data-stu-id="75895-108">Implement the <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> and <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> methods to modify contracts and endpoints imported from the metadata.</span></span> <span data-ttu-id="75895-109">インポートしたコントラクトまたはエンドポイントにアクセスするには、対応するコンテキスト オブジェクト (<xref:System.ServiceModel.Description.WsdlContractConversionContext> または <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>) を使用します。</span><span class="sxs-lookup"><span data-stu-id="75895-109">To access the imported contract or endpoint, use the corresponding context object (<xref:System.ServiceModel.Description.WsdlContractConversionContext> or <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>):</span></span>  
  
    ```csharp
    public class WsdlDocumentationImporter : IWsdlImportExtension
    {
        public void ImportContract(WsdlImporter importer, WsdlContractConversionContext context)
        {
            // Contract documentation
            if (context.WsdlPortType.Documentation != null)
            {
                context.Contract.Behaviors.Add(new WsdlDocumentationImporter(context.WsdlPortType.Documentation));
            }
            // Operation documentation
            foreach (Operation operation in context.WsdlPortType.Operations)
            {
                if (operation.Documentation != null)
                {
                    OperationDescription operationDescription = context.Contract.Operations.Find(operation.Name);
                    if (operationDescription != null)
                    {
                        operationDescription.Behaviors.Add(new WsdlDocumentationImporter(operation.Documentation));
                    }
                }
            }
        }

        public void BeforeImport(ServiceDescriptionCollection wsdlDocuments, XmlSchemaSet xmlSchemas, ICollection<XmlElement> policy)
        {
            Console.WriteLine("BeforeImport called.");
        }

        public void ImportEndpoint(WsdlImporter importer, WsdlEndpointConversionContext context)
        {
            Console.WriteLine("ImportEndpoint called.");
        }
    }
    ```
  
2. <span data-ttu-id="75895-110">カスタム WSDL インポーターを使用するようクライアント アプリケーションを構成します。</span><span class="sxs-lookup"><span data-stu-id="75895-110">Configure the client application to use the custom WSDL importer.</span></span> <span data-ttu-id="75895-111">Svcutil.exe を使用する場合は、Svcutil.exe の構成ファイル (Svcutil.exe.config) にこの構成を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="75895-111">Note that if you are using Svcutil.exe, you should add this configuration to the configuration file for Svcutil.exe (Svcutil.exe.config):</span></span>  
  
    ```xml  
    <system.serviceModel>  
          <client>  
            <endpoint
              address="http://localhost:8000/Fibonacci"
              binding="wsHttpBinding"  
              contract="IFibonacci"  
            />  
            <metadata>  
              <wsdlImporters>  
                <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
              </wsdlImporters>  
            </metadata>  
          </client>  
        </system.serviceModel>  
    ```  
  
3. <span data-ttu-id="75895-112">新しい <xref:System.ServiceModel.Description.WsdlImporter> インスタンス (インポートする WSDL ドキュメントが含まれる <xref:System.ServiceModel.Description.MetadataSet> インスタンスを渡す) を作成し、<xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="75895-112">Create a new <xref:System.ServiceModel.Description.WsdlImporter> instance (passing in the <xref:System.ServiceModel.Description.MetadataSet> instance that contains the WSDL documents that you want to import), and call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:</span></span>  
  
    ```csharp
    WsdlImporter importer = new WsdlImporter(metaDocs);
    System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="75895-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="75895-113">See also</span></span>

- [<span data-ttu-id="75895-114">メタデータ</span><span class="sxs-lookup"><span data-stu-id="75895-114">Metadata</span></span>](../feature-details/metadata.md)
- [<span data-ttu-id="75895-115">メタデータのエクスポートとインポート</span><span class="sxs-lookup"><span data-stu-id="75895-115">Exporting and Importing Metadata</span></span>](../feature-details/exporting-and-importing-metadata.md)
- [<span data-ttu-id="75895-116">カスタム WSDL パブリケーション</span><span class="sxs-lookup"><span data-stu-id="75895-116">Custom WSDL Publication</span></span>](../samples/custom-wsdl-publication.md)
