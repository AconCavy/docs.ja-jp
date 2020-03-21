---
title: エラーの定義と指定
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling faults [WCF], specifying
- handling faults [WCF], defining
ms.assetid: c00c84f1-962d-46a7-b07f-ebc4f80fbfc1
ms.openlocfilehash: 10fc045cab995cca8d78e470d74ec9341e167308
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176696"
---
# <a name="defining-and-specifying-faults"></a><span data-ttu-id="19d99-102">エラーの定義と指定</span><span class="sxs-lookup"><span data-stu-id="19d99-102">Defining and Specifying Faults</span></span>
<span data-ttu-id="19d99-103">SOAP エラーを使用する目的は、エラー状態情報をサービスからクライアントに伝達し、双方向のシナリオでは、相互利用が可能な手段でクライアントからサービスにも伝達することです。</span><span class="sxs-lookup"><span data-stu-id="19d99-103">SOAP faults convey error condition information from a service to a client and, in the duplex case, from a client to a service in an interoperable way.</span></span> <span data-ttu-id="19d99-104">ここでは、カスタムのエラー コンテンツをいつどのように定義し、そのエラーを返す操作をどのように指定するかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="19d99-104">This topic discusses when and how to define custom fault content and specify which operations can return them.</span></span> <span data-ttu-id="19d99-105">サービスまたは双方向クライアントがそれらの障害を送信する方法、およびクライアントまたはサービス アプリケーションがこれらの障害を処理する方法の詳細については、「エラーの[送受信](sending-and-receiving-faults.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19d99-105">For more information about how a service, or duplex client, can send those faults and how a client or service application handles these faults, see [Sending and Receiving Faults](sending-and-receiving-faults.md).</span></span> <span data-ttu-id="19d99-106">Wcf (Windows 通信基盤) アプリケーションでのエラー処理の概要については、「[コントラクトとサービスでのエラーの指定と処理](specifying-and-handling-faults-in-contracts-and-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19d99-106">For an overview of error handling in Windows Communication Foundation (WCF) applications, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="19d99-107">概要</span><span class="sxs-lookup"><span data-stu-id="19d99-107">Overview</span></span>  
 <span data-ttu-id="19d99-108">宣言された SOAP エラーは、カスタム SOAP エラーの種類を指定する <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> を含む操作で発生します。</span><span class="sxs-lookup"><span data-stu-id="19d99-108">Declared SOAP faults are those in which an operation has a <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> that specifies a custom SOAP fault type.</span></span> <span data-ttu-id="19d99-109">宣言されていない SOAP エラーとは、操作のコントラクトに指定されていないエラーです。</span><span class="sxs-lookup"><span data-stu-id="19d99-109">Undeclared SOAP faults are those that are not specified in the contract for an operation.</span></span> <span data-ttu-id="19d99-110">ここでは、各種のエラー状態を特定したうえで、サービスに関するエラー コントラクトを作成する方法について説明します。クライアントは、カスタムの SOAP エラーから通知を受けたときに、これらを使用することでエラーを適切に処理できます。</span><span class="sxs-lookup"><span data-stu-id="19d99-110">This topic helps you identify those error conditions and create a fault contract for your service that clients can use to properly handle those error conditions when notified by custom SOAP faults.</span></span> <span data-ttu-id="19d99-111">基本的なタスクは、次の順序で行います。</span><span class="sxs-lookup"><span data-stu-id="19d99-111">The basic tasks are, in order:</span></span>  
  
1. <span data-ttu-id="19d99-112">サービスのクライアントに通知する必要があるエラー状態を定義します。</span><span class="sxs-lookup"><span data-stu-id="19d99-112">Define the error conditions that a client of your service should know about.</span></span>  
  
2. <span data-ttu-id="19d99-113">そのエラー状態に対して SOAP エラーのカスタム コンテンツを定義します。</span><span class="sxs-lookup"><span data-stu-id="19d99-113">Define the custom content of the SOAP faults for those error conditions.</span></span>  
  
3. <span data-ttu-id="19d99-114">操作でスローされた特定の SOAP エラーがクライアントに公開されるように、WSDL でその操作にマークします。</span><span class="sxs-lookup"><span data-stu-id="19d99-114">Mark your operations so that the specific SOAP faults that they throw are exposed to clients in WSDL.</span></span>  
  
### <a name="defining-error-conditions-that-clients-should-know-about"></a><span data-ttu-id="19d99-115">クライアントに通知する必要があるエラー状態の定義</span><span class="sxs-lookup"><span data-stu-id="19d99-115">Defining Error Conditions That Clients Should Know About</span></span>  
 <span data-ttu-id="19d99-116">SOAP エラーは、特定の操作に関するフォールト情報を伝達するためにパブリックに記述されたメッセージです。</span><span class="sxs-lookup"><span data-stu-id="19d99-116">SOAP faults are publicly described messages that carry fault information for a particular operation.</span></span> <span data-ttu-id="19d99-117">これらのメッセージは、WSDL で他の操作メッセージと共に記述されているので、クライアントは、操作を呼び出した時点でこのようなエラー処理を予測できます。</span><span class="sxs-lookup"><span data-stu-id="19d99-117">Because they are described along with other operation messages in WSDL, clients know and, therefore, expect to handle such faults when invoking an operation.</span></span> <span data-ttu-id="19d99-118">しかし、WCF サービスはマネージ コードで記述されているため、マネージ コードのどのエラー条件をエラーに変換してクライアントに返すかを決定すると、サービスのエラー条件とバグを正式なエラーから分離する機会が得られます。クライアントとの会話。</span><span class="sxs-lookup"><span data-stu-id="19d99-118">But because WCF services are written in managed code, deciding which error conditions in managed code are to be converted into faults and returned to the client provides you the opportunity to separate error conditions and bugs in your service from the formal error conversation you have with a client.</span></span>  
  
 <span data-ttu-id="19d99-119">たとえば、次のコード例には、2 つの整数を受け取り、別の整数を返す操作があります。</span><span class="sxs-lookup"><span data-stu-id="19d99-119">For example, the following code example shows an operation that takes two integers and returns another integer.</span></span> <span data-ttu-id="19d99-120">ここではいくつかの例外がスローされる可能性があります。そのため、エラー コントラクトを設計するときに、クライアントにとって重要なエラー状態を判別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="19d99-120">Several exceptions can be thrown here, so when designing the fault contract, you must determine which error conditions are important for your client.</span></span> <span data-ttu-id="19d99-121">この場合、サービスでは <xref:System.DivideByZeroException?displayProperty=nameWithType> 例外を検出する必要があります。</span><span class="sxs-lookup"><span data-stu-id="19d99-121">In this case, the service should detect the <xref:System.DivideByZeroException?displayProperty=nameWithType> exception.</span></span>  
  
```csharp  
[ServiceContract]  
public class CalculatorService  
{  
    [OperationContract]
    int Divide(int a, int b)  
    {  
      if (b==0) throw new Exception("Division by zero!");  
      return a/b;  
    }  
}  
```  
  
```vb
<ServiceContract> _
Public Class CalculatorService
    <OperationContract> _
    Public Function Divide(a As Integer, b As Integer) As Integer
        If b = 0 Then Throw New DivideByZeroException("Division by zero!")
        Return a / b
    End Function
End Class
```
  
 <span data-ttu-id="19d99-122">この例で操作から返せるエラーには、ゼロによる除算に特化したカスタム SOAP エラー、ゼロ除算に特化した情報が算術演算に特化したエラーに含まれているもの、複数の異なるエラー状態に対する複数のエラーなどがあります。SOAP エラーを返さないことも選択できます。</span><span class="sxs-lookup"><span data-stu-id="19d99-122">In the preceding example the operation can either return a custom SOAP fault that is specific to dividing by zero, a custom fault that is specific to math operations but that contains information specific to dividing by zero, multiple faults for several different error situations, or no SOAP fault at all.</span></span>  
  
### <a name="define-the-content-of-error-conditions"></a><span data-ttu-id="19d99-123">エラー状態のコンテンツの定義</span><span class="sxs-lookup"><span data-stu-id="19d99-123">Define the Content of Error Conditions</span></span>  
 <span data-ttu-id="19d99-124">意義のあるカスタム SOAP エラーを返すエラー状態を特定したら、次の手順では、そのエラーのコンテンツを定義し、コンテンツ構造をシリアル化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="19d99-124">Once an error condition has been identified as one that can usefully return a custom SOAP fault, the next step is to define the contents of that fault and ensure that the content structure can be serialized.</span></span> <span data-ttu-id="19d99-125">前のセクションのコード例では、`Divide` 演算に特化したエラーを示していました。しかし、`Calculator` サービスに他の演算がある場合、1 つのカスタム SOAP エラーで、`Divide` を含むすべての電卓エラー状態をクライアントに通知することも可能です。</span><span class="sxs-lookup"><span data-stu-id="19d99-125">The code example in the preceding section shows an error specific to a `Divide` operation, but if there are other operations on the `Calculator` service, then a single custom SOAP fault can inform the client of all calculator error conditions, `Divide` included.</span></span> <span data-ttu-id="19d99-126">次のコード例では、`MathFault` を含むすべての算術演算で生成されたエラーを報告するためのカスタム SOAP エラー `Divide` を作成しています。</span><span class="sxs-lookup"><span data-stu-id="19d99-126">The following code example shows the creation of a custom SOAP fault, `MathFault`, which can report errors made using all math operations, including `Divide`.</span></span> <span data-ttu-id="19d99-127">このクラスでは、操作 (`Operation` プロパティ) と問題を説明する値 (`ProblemType` プロパティ) を指定できますが、カスタム SOAP エラーでクライアントに転送するには、クラスとこれらのプロパティがシリアル化可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="19d99-127">While the class can specify an operation (the `Operation` property) and a value that describes the problem (the `ProblemType` property), the class and these properties must be serializable to be transferred to the client in a custom SOAP fault.</span></span> <span data-ttu-id="19d99-128">このため、<xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> 属性と <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> 属性を使用して、型とそのプロパティをシリアル化可能にし、できる限り相互運用可能にします。</span><span class="sxs-lookup"><span data-stu-id="19d99-128">Therefore, the <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> and <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> attributes are used to make the type and its properties serializable and as interoperable as possible.</span></span>  
  
 [!code-csharp[Faults#2](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#2)]
 [!code-vb[Faults#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#2)]  
  
 <span data-ttu-id="19d99-129">データをシリアル化可能にする方法の詳細については、「サービス[コントラクトでのデータ転送の指定](./feature-details/specifying-data-transfer-in-service-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19d99-129">For more information about how to ensure your data is serializable, see [Specifying Data Transfer in Service Contracts](./feature-details/specifying-data-transfer-in-service-contracts.md).</span></span> <span data-ttu-id="19d99-130">提供するシリアル化サポートの一覧については、「[データ コントラクト シリアライザーでサポートされる型](./feature-details/types-supported-by-the-data-contract-serializer.md)」を参照してください。 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="19d99-130">For a list of the serialization support that <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> provides, see [Types Supported by the Data Contract Serializer](./feature-details/types-supported-by-the-data-contract-serializer.md).</span></span>  
  
### <a name="mark-operations-to-establish-the-fault-contract"></a><span data-ttu-id="19d99-131">エラー コントラクトを確立するための操作のマーク</span><span class="sxs-lookup"><span data-stu-id="19d99-131">Mark Operations to Establish the Fault Contract</span></span>  
 <span data-ttu-id="19d99-132">カスタム SOAP エラーの一部として返されるシリアル化可能なデータ構造を定義したら、最後に、その型の SOAP エラーをスローできることを操作コントラクトにマークします。</span><span class="sxs-lookup"><span data-stu-id="19d99-132">Once a serializable data structure that is returned as part of a custom SOAP fault is defined, the last step is to mark your operation contract as throwing a SOAP fault of that type.</span></span> <span data-ttu-id="19d99-133">これには、<xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> 属性を使用して、作成したカスタム データ型の型を渡します。</span><span class="sxs-lookup"><span data-stu-id="19d99-133">To do this, use the <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> attribute and pass the type of the custom data type that you have constructed.</span></span> <span data-ttu-id="19d99-134"><xref:System.ServiceModel.FaultContractAttribute> 属性を使用して、`Divide` 操作で `MathFault` 型の SOAP エラーを返すように指定する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="19d99-134">The following code example shows how to use the <xref:System.ServiceModel.FaultContractAttribute> attribute to specify that the `Divide` operation can return a SOAP fault of type `MathFault`.</span></span> <span data-ttu-id="19d99-135">他の算術に関する操作でも、`MathFault` を返せるように指定できます。</span><span class="sxs-lookup"><span data-stu-id="19d99-135">Other math-based operations can now also specify that they can return a `MathFault`.</span></span>  
  
 [!code-csharp[Faults#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#1)]
 [!code-vb[Faults#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#1)]  
  
 <span data-ttu-id="19d99-136">操作に複数の <xref:System.ServiceModel.FaultContractAttribute> 属性をマークすることによって、その操作で複数のカスタム エラーを返すことを指定できます。</span><span class="sxs-lookup"><span data-stu-id="19d99-136">An operation can specify that it returns more than one custom fault by marking that operation with more than one <xref:System.ServiceModel.FaultContractAttribute> attribute.</span></span>  
  
 <span data-ttu-id="19d99-137">次の手順では、操作の実装で障害コントラクトを実装する方法について、トピック「[送信および受信障害](sending-and-receiving-faults.md)」で説明します。</span><span class="sxs-lookup"><span data-stu-id="19d99-137">The next step, to implement the fault contract in your operation implementation, is described in the topic [Sending and Receiving Faults](sending-and-receiving-faults.md).</span></span>  
  
#### <a name="soap-wsdl-and-interoperability-considerations"></a><span data-ttu-id="19d99-138">SOAP、WSDL、相互運用性に関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="19d99-138">SOAP, WSDL, and Interoperability Considerations</span></span>  
 <span data-ttu-id="19d99-139">特に他のプラットフォームと相互運用するときなど、状況によっては、SOAP メッセージでエラーを表す方法または WSDL メタデータでエラーを記述する方法を制御することが重要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="19d99-139">In some circumstances, especially when interoperating with other platforms, it may be important to control the way a fault appears in a SOAP message or the way it is described in the WSDL metadata.</span></span>  
  
 <span data-ttu-id="19d99-140"><xref:System.ServiceModel.FaultContractAttribute> 属性の <xref:System.ServiceModel.FaultContractAttribute.Name%2A> プロパティを使用すると、エラーに対してメタデータで生成される WSDL エラー要素名を制御できます。</span><span class="sxs-lookup"><span data-stu-id="19d99-140">The <xref:System.ServiceModel.FaultContractAttribute> attribute has a <xref:System.ServiceModel.FaultContractAttribute.Name%2A> property that allows control of the WSDL fault element name that is generated in the metadata for that fault.</span></span>  
  
 <span data-ttu-id="19d99-141">SOAP 標準に従って、エラーには、`Action`、`Code`、および `Reason` を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="19d99-141">According to the SOAP standard, a fault can have an `Action`, a `Code`, and a `Reason`.</span></span> <span data-ttu-id="19d99-142">`Action` は、<xref:System.ServiceModel.FaultContractAttribute.Action%2A> プロパティによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="19d99-142">The `Action` is controlled by the <xref:System.ServiceModel.FaultContractAttribute.Action%2A> property.</span></span> <span data-ttu-id="19d99-143"><xref:System.ServiceModel.FaultException.Code%2A> プロパティと <xref:System.ServiceModel.FaultException.Reason%2A> プロパティは、ジェネリック <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> の親クラスである <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> クラスのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="19d99-143">The <xref:System.ServiceModel.FaultException.Code%2A> property and <xref:System.ServiceModel.FaultException.Reason%2A> property are both properties of the <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> class, which is the parent class of the generic <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="19d99-144">`Code` プロパティには、<xref:System.ServiceModel.FaultCode.SubCode%2A> メンバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="19d99-144">The `Code` property includes a <xref:System.ServiceModel.FaultCode.SubCode%2A> member.</span></span>  
  
 <span data-ttu-id="19d99-145">エラーを生成する非サービスを利用する場合には、特定の制限事項があります。</span><span class="sxs-lookup"><span data-stu-id="19d99-145">When accessing non-services that generate faults, certain limitations exist.</span></span> <span data-ttu-id="19d99-146">WCF は、スキーマが記述し、データ コントラクトと互換性がある詳細な型のエラーのみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="19d99-146">WCF supports only faults with detail types that the schema describes and that are compatible with data contracts.</span></span> <span data-ttu-id="19d99-147">たとえば、前述のように、WCF は詳細の種類で XML 属性を使用するエラー、または詳細セクションで複数の最上位要素を持つフォールトをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="19d99-147">For example, as mentioned above, WCF does not support faults that use XML attributes in their detail types, or faults with more than one top-level element in the detail section.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19d99-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="19d99-148">See also</span></span>

- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="19d99-149">コントラクトおよびサービスのエラーの指定と処理</span><span class="sxs-lookup"><span data-stu-id="19d99-149">Specifying and Handling Faults in Contracts and Services</span></span>](specifying-and-handling-faults-in-contracts-and-services.md)
- [<span data-ttu-id="19d99-150">エラーの送受信</span><span class="sxs-lookup"><span data-stu-id="19d99-150">Sending and Receiving Faults</span></span>](sending-and-receiving-faults.md)
- [<span data-ttu-id="19d99-151">方法: サービス コントラクトでのエラーを宣言する</span><span class="sxs-lookup"><span data-stu-id="19d99-151">How to: Declare Faults in Service Contracts</span></span>](how-to-declare-faults-in-service-contracts.md)
- [<span data-ttu-id="19d99-152">保護レベルの理解</span><span class="sxs-lookup"><span data-stu-id="19d99-152">Understanding Protection Level</span></span>](understanding-protection-level.md)
- [<span data-ttu-id="19d99-153">方法: ProtectionLevel プロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="19d99-153">How to: Set the ProtectionLevel Property</span></span>](how-to-set-the-protectionlevel-property.md)
- [<span data-ttu-id="19d99-154">Specifying Data Transfer in Service Contracts</span><span class="sxs-lookup"><span data-stu-id="19d99-154">Specifying Data Transfer in Service Contracts</span></span>](./feature-details/specifying-data-transfer-in-service-contracts.md)
