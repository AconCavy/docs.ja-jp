---
title: メッセージ コントラクトの使用
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message contracts [WCF]
ms.assetid: 1e19c64a-ae84-4c2f-9155-91c54a77c249
ms.openlocfilehash: 1b102b97c62df0bb8b031ded0f9165a11f8a8911
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600271"
---
# <a name="using-message-contracts"></a><span data-ttu-id="ee0bc-102">メッセージ コントラクトの使用</span><span class="sxs-lookup"><span data-stu-id="ee0bc-102">Using Message Contracts</span></span>
<span data-ttu-id="ee0bc-103">通常、Windows Communication Foundation (WCF) アプリケーションを構築する場合、開発者はデータ構造とシリアル化の問題に細心の注意を払って、データが格納されるメッセージの構造を考慮する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-103">Typically when building Windows Communication Foundation (WCF) applications, developers pay close attention to the data structures and serialization issues and do not need to concern themselves with the structure of the messages in which the data is carried.</span></span> <span data-ttu-id="ee0bc-104">このようなアプリケーションでは、パラメーターまたは戻り値用にデータ コントラクトを作成するのは簡単です </span><span class="sxs-lookup"><span data-stu-id="ee0bc-104">For these applications, creating data contracts for the parameters or return values is straightforward.</span></span> <span data-ttu-id="ee0bc-105">(詳細については、「[サービスコントラクトでのデータ転送の指定](specifying-data-transfer-in-service-contracts.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-105">(For more information, see [Specifying Data Transfer in Service Contracts](specifying-data-transfer-in-service-contracts.md).)</span></span>  
  
 <span data-ttu-id="ee0bc-106">ただし、SOAP メッセージの構造を完全に制御することがメッセージの内容の制御と同様に重要となる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-106">However, sometimes complete control over the structure of a SOAP message is just as important as control over its contents.</span></span> <span data-ttu-id="ee0bc-107">これが特に当てはまるのは、相互運用性が重要である場合、具体的にはメッセージまたはメッセージ部分のレベルでセキュリティの問題を制御する場合です。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-107">This is especially true when interoperability is important or to specifically control security issues at the level of the message or message part.</span></span> <span data-ttu-id="ee0bc-108">このような場合は、必要な正確な SOAP メッセージの構造を指定できるようにする*メッセージコントラクト*を作成できます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-108">In these cases, you can create a *message contract* that enables you to specify the structure of the precise SOAP message required.</span></span>  
  
 <span data-ttu-id="ee0bc-109">ここでは、メッセージ コントラクトの各種属性を使用して、ユーザー操作に専用のメッセージ コントラクトを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-109">This topic discusses how to use the various message contract attributes to create a specific message contract for your operation.</span></span>  
  
## <a name="using-message-contracts-in-operations"></a><span data-ttu-id="ee0bc-110">処理におけるメッセージ コントラクトの使用</span><span class="sxs-lookup"><span data-stu-id="ee0bc-110">Using Message Contracts in Operations</span></span>  
 <span data-ttu-id="ee0bc-111">WCF は、*リモートプロシージャコール (RPC) スタイル*または*メッセージングスタイル*でモデル化された操作をサポートします。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-111">WCF supports operations modeled on either the *remote procedure call (RPC) style* or the *messaging style*.</span></span> <span data-ttu-id="ee0bc-112">RPC スタイルの操作では、シリアル化可能な任意の型を使用できます。複数のパラメーター、`ref` パラメーターと `out` パラメーターなど、ローカル呼び出しで使用できる機能を利用できます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-112">In an RPC-style operation, you can use any serializable type, and you have access to the features that are available to local calls, such as multiple parameters and `ref` and `out` parameters.</span></span> <span data-ttu-id="ee0bc-113">このスタイルでは、選択したシリアル化の形式によって基になるメッセージのデータ構造が制御され、WCF ランタイムによって、操作をサポートするメッセージが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-113">In this style, the form of serialization chosen controls the structure of the data in the underlying messages, and the WCF runtime creates the messages to support the operation.</span></span> <span data-ttu-id="ee0bc-114">これにより、SOAP や SOAP メッセージに不慣れな開発者でも、サービス アプリケーションを迅速かつ容易に作成し、使用できます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-114">This enables developers who are not familiar with SOAP and SOAP messages to quickly and easily create and use service applications.</span></span>  
  
 <span data-ttu-id="ee0bc-115">RPC スタイルでモデル化されたサービス操作のコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-115">The following code example shows a service operation modeled on the RPC style.</span></span>  
  
```csharp  
[OperationContract]  
public BankingTransactionResponse PostBankingTransaction(BankingTransaction bt);  
```  
  
 <span data-ttu-id="ee0bc-116">通常は、データ コントラクトだけでメッセージのスキーマを定義することができます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-116">Normally, a data contract is sufficient to define the schema for the messages.</span></span> <span data-ttu-id="ee0bc-117">たとえば、前の例では、`BankingTransaction` と `BankingTransactionResponse` にデータ コントラクトがあれば、ほとんどのアプリケーションで基になる SOAP メッセージの内容を定義できます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-117">For instance, in the preceding example, it is sufficient for most applications if `BankingTransaction` and `BankingTransactionResponse` have data contracts to define the contents of the underlying SOAP messages.</span></span> <span data-ttu-id="ee0bc-118">データコントラクトの詳細については、「[データコントラクトの使用](using-data-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-118">For more information about data contracts, see [Using Data Contracts](using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="ee0bc-119">ただし、場合によっては、SOAP メッセージの構造がネットワーク経由でどのように転送されるかを厳密に制御する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-119">However, occasionally it is necessary to precisely control how the structure of the SOAP message transmitted over the wire.</span></span> <span data-ttu-id="ee0bc-120">最も一般的なシナリオは、カスタム SOAP ヘッダーの挿入です。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-120">The most common scenario for this is inserting custom SOAP headers.</span></span> <span data-ttu-id="ee0bc-121">もう 1 つの一般的なシナリオは、メッセージのヘッダーと本文のセキュリティ プロパティを定義すること、つまり、これらの要素にデジタル署名し、要素を暗号化するかどうかを決定することです。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-121">Another common scenario is to define security properties for the message's headers and body, that is, to decide whether these elements are digitally signed and encrypted.</span></span> <span data-ttu-id="ee0bc-122">最後に、一部のサードパーティの SOAP スタックでは、メッセージが特定の形式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-122">Finally, some third-party SOAP stacks require messages be in a specific format.</span></span> <span data-ttu-id="ee0bc-123">この制御は、メッセージング スタイルの操作によって行うことができます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-123">Messaging-style operations provide this control.</span></span>  
  
 <span data-ttu-id="ee0bc-124">メッセージング スタイルの操作には、最大で 1 つのパラメーターと 1 つの戻り値があります。これらはいずれもメッセージ型です。つまり、パラメーターと戻り値は、指定された SOAP メッセージ構造に直接シリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-124">A messaging-style operation has at most one parameter and one return value where both types are message types; that is, they serialize directly into a specified SOAP message structure.</span></span> <span data-ttu-id="ee0bc-125">これは、<xref:System.ServiceModel.MessageContractAttribute> 型、または <xref:System.ServiceModel.Channels.Message> 型としてマークされた任意の型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-125">This may be any type marked with the <xref:System.ServiceModel.MessageContractAttribute> or the <xref:System.ServiceModel.Channels.Message> type.</span></span> <span data-ttu-id="ee0bc-126">次のコード例は前の RPC スタイルと同様の操作を示していますが、この例ではメッセージング スタイルを使用しています。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-126">The following code example shows an operation similar to the preceding RCP-style, but which uses the messaging style.</span></span>  
  
 <span data-ttu-id="ee0bc-127">たとえば、`BankingTransaction` と `BankingTransactionResponse` がいずれもメッセージ コントラクト型である場合、次の操作のコードは有効です。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-127">For example, if `BankingTransaction` and `BankingTransactionResponse` are both types that are message contracts, then the code in the following operations is valid.</span></span>  
  
```csharp  
[OperationContract]  
BankingTransactionResponse Process(BankingTransaction bt);  
[OperationContract]  
void Store(BankingTransaction bt);  
[OperationContract]  
BankingTransactionResponse GetResponse();  
```  
  
 <span data-ttu-id="ee0bc-128">ただし、次のコードは無効です。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-128">However, the following code is invalid.</span></span>  
  
```csharp  
[OperationContract]  
bool Validate(BankingTransaction bt);  
// Invalid, the return type is not a message contract.  
[OperationContract]  
void Reconcile(BankingTransaction bt1, BankingTransaction bt2);  
// Invalid, there is more than one parameter.  
```  
  
 <span data-ttu-id="ee0bc-129">メッセージ コントラクト型を含み、有効なパターンのいずれにも従わないすべての操作に対して例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-129">An exception is thrown for any operation that involves a message contract type and that does not follow one of the valid patterns.</span></span> <span data-ttu-id="ee0bc-130">もちろん、メッセージ コントラクト型を含まない処理にはこのような制限はありません。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-130">Of course, operations that do not involve message contract types are not subject to these restrictions.</span></span>  
  
 <span data-ttu-id="ee0bc-131">1 つの型にメッセージ コントラクトとデータ コントラクトの両方が含まれる場合は、処理でその型が使用されたときにはメッセージ コントラクトだけが考慮されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-131">If a type has both a message contract and a data contract, only its message contract is considered when the type is used in an operation.</span></span>  
  
## <a name="defining-message-contracts"></a><span data-ttu-id="ee0bc-132">メッセージ コントラクトの定義</span><span class="sxs-lookup"><span data-stu-id="ee0bc-132">Defining Message Contracts</span></span>  
 <span data-ttu-id="ee0bc-133">型のメッセージ コントラクトを定義する (つまり、型と SOAP エンベロープ間のマッピングを定義する) には、<xref:System.ServiceModel.MessageContractAttribute> を型に適用します。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-133">To define a message contract for a type (that is, to define the mapping between the type and a SOAP envelope), apply the <xref:System.ServiceModel.MessageContractAttribute> to the type.</span></span> <span data-ttu-id="ee0bc-134">次に、SOAP ヘッダーにする型のメンバーに <xref:System.ServiceModel.MessageHeaderAttribute> を適用し、メッセージの SOAP 本文の一部にするメンバーに <xref:System.ServiceModel.MessageBodyMemberAttribute> を適用します。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-134">Then apply the <xref:System.ServiceModel.MessageHeaderAttribute> to those members of the type you want to make into SOAP headers, and apply the <xref:System.ServiceModel.MessageBodyMemberAttribute> to those members you want to make into parts of the SOAP body of the message.</span></span>  
  
 <span data-ttu-id="ee0bc-135">メッセージ コントラクトの使用例を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-135">The following code provides an example of using a message contract.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader] public DateTime transactionDate;  
  [MessageBodyMember] private Account sourceAccount;  
  [MessageBodyMember] private Account targetAccount;  
  [MessageBodyMember] public int amount;  
}  
```  
  
 <span data-ttu-id="ee0bc-136">この型を操作パラメーターとして使用すると、次の SOAP エンベロープが生成されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-136">When using this type as an operation parameter, the following SOAP envelope is generated:</span></span>  
  
```xml  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <h:operation xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">Deposit</h:operation>  
    <h:transactionDate xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">2012-02-16T16:10:00</h:transactionDate>  
  </s:Header>  
  <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <BankingTransaction xmlns="http://tempuri.org/">  
      <amount>0</amount>  
      <sourceAccount xsi:nil="true"/>  
      <targetAccount xsi:nil="true"/>  
    </BankingTransaction>  
  </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="ee0bc-137">`operation` と `transactionDate` が SOAP ヘッダーとして表示され、SOAP 本体は `BankingTransaction`、`sourceAccount`、および `targetAccount` を含むラッパー要素 `amount` から成ることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-137">Notice that `operation` and `transactionDate` appear as SOAP headers and the SOAP body consists of a wrapper element `BankingTransaction` containing `sourceAccount`,`targetAccount`, and `amount`.</span></span>  
  
 <span data-ttu-id="ee0bc-138">パブリック、プライベート、保護、または内部のいずれであるかに関係なく、<xref:System.ServiceModel.MessageHeaderAttribute> と <xref:System.ServiceModel.MessageBodyMemberAttribute> は、すべてのフィールド、プロパティ、およびイベントに適用できます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-138">You can apply the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> to all fields, properties, and events, regardless of whether they are public, private, protected, or internal.</span></span>  
  
 <span data-ttu-id="ee0bc-139"><xref:System.ServiceModel.MessageContractAttribute> を使用すると、SOAP メッセージの本文のラッパー要素の名前を制御する WrapperName および WrapperNamespace 属性を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-139">The <xref:System.ServiceModel.MessageContractAttribute> allows you to specify the WrapperName and WrapperNamespace attributes which control the name of the wrapper element in the body of the SOAP message.</span></span> <span data-ttu-id="ee0bc-140">既定では、メッセージ コントラクト型の名前はラッパー用に使用され、メッセージ コントラクトが定義されている名前空間 (`http://tempuri.org/`) は既定の名前空間として使用されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-140">By default the name of the message contract type is used for the wrapper and the namespace in which the message contract is defined `http://tempuri.org/` is used as the default namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee0bc-141"><xref:System.Runtime.Serialization.KnownTypeAttribute> 属性は、メッセージ コントラクトでは無視されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-141"><xref:System.Runtime.Serialization.KnownTypeAttribute> attributes are ignored in message contracts.</span></span> <span data-ttu-id="ee0bc-142"><xref:System.Runtime.Serialization.KnownTypeAttribute> が必要な場合は、対象のメッセージ コントラクトを使用している処理でそれを設定します。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-142">If a <xref:System.Runtime.Serialization.KnownTypeAttribute> is required, place it on the operation that is using the message contract in question.</span></span>  
  
## <a name="controlling-header-and-body-part-names-and-namespaces"></a><span data-ttu-id="ee0bc-143">ヘッダー名、本文名、および名前空間の制御</span><span class="sxs-lookup"><span data-stu-id="ee0bc-143">Controlling Header and Body Part Names and Namespaces</span></span>  
 <span data-ttu-id="ee0bc-144">メッセージ コントラクトの SOAP 表現では、各ヘッダーと本文の各部分が名前と名前空間を持つ XML 要素にマップされます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-144">In the SOAP representation of a message contract, each header and body part maps to an XML element that has a name and a namespace.</span></span>  
  
 <span data-ttu-id="ee0bc-145">既定では、名前空間はメッセージが参加しているサービス コントラクトの名前空間と同じであり、その名前は <xref:System.ServiceModel.MessageHeaderAttribute> 属性または <xref:System.ServiceModel.MessageBodyMemberAttribute> 属性が割り当てられたメンバー名によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-145">By default, the namespace is the same as the namespace of the service contract that the message is participating in, and the name is determined by the member name to which the <xref:System.ServiceModel.MessageHeaderAttribute> or the <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes are applied.</span></span>  
  
 <span data-ttu-id="ee0bc-146">(<xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> 属性と <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> 属性の親クラスの) <xref:System.ServiceModel.MessageHeaderAttribute> および <xref:System.ServiceModel.MessageBodyMemberAttribute> を操作することによって、これらの既定値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-146">You can change these defaults by manipulating the <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (on the parent class of the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes).</span></span>  
  
 <span data-ttu-id="ee0bc-147">次のコード例のクラスについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-147">Consider the class in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader(Namespace="http://schemas.contoso.com/auditing/2005")] public bool IsAudited;  
  [MessageBodyMember(Name="transactionData")] public BankingTransactionData theData;  
}  
```  
  
 <span data-ttu-id="ee0bc-148">この例では、`IsAudited` ヘッダーがコードで指定された名前空間に存在し、`theData` メンバーを表す本文が `transactionData` という名前の XML 要素によって表現されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-148">In this example, the `IsAudited` header is in the namespace specified in the code, and the body part that represents the `theData` member is represented by an XML element with the name `transactionData`.</span></span> <span data-ttu-id="ee0bc-149">次に、このメッセージ コントラクト用に生成された XML を示します。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-149">The following shows the XML generated for this message contract.</span></span>  
  
```xml  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <h:IsAudited xmlns:h="http://schemas.contoso.com/auditing/2005" xmlns="http://schemas.contoso.com/auditing/2005">false</h:IsAudited>  
    <h:operation xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">Deposit</h:operation>  
  </s:Header>  
  <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <AuditedBankingTransaction xmlns="http://tempuri.org/">  
      <transactionData/>  
    </AuditedBankingTransaction>  
  </s:Body>  
</s:Envelope>  
```  
  
## <a name="controlling-whether-the-soap-body-parts-are-wrapped"></a><span data-ttu-id="ee0bc-150">SOAP 本文の各部分のラップの制御</span><span class="sxs-lookup"><span data-stu-id="ee0bc-150">Controlling Whether the SOAP Body Parts Are Wrapped</span></span>  
 <span data-ttu-id="ee0bc-151">SOAP 本文は、既定で、ラップされた要素内にシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-151">By default, the SOAP body parts are serialized inside a wrapped element.</span></span> <span data-ttu-id="ee0bc-152">たとえば、`HelloGreetingMessage` メッセージのメッセージ コントラクトに含まれる <xref:System.ServiceModel.MessageContractAttribute> 型の名前から生成される `HelloGreetingMessage` ラッパー要素を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-152">For example, the following code shows the `HelloGreetingMessage` wrapper element generated from the name of the <xref:System.ServiceModel.MessageContractAttribute> type in the message contract for the `HelloGreetingMessage` message.</span></span>  
  
[!code-csharp[MessageHeaderAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/messageheaderattribute/cs/services.cs#3)]
[!code-vb[MessageHeaderAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/messageheaderattribute/vb/services.vb#3)]  
  
 <span data-ttu-id="ee0bc-153">ラッパー要素を抑制するには、<xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> プロパティを `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-153">To suppress the wrapper element, set the <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> property to `false`.</span></span> <span data-ttu-id="ee0bc-154">ラッパー要素の名前と名前空間を制御するには、<xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> プロパティと <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-154">To control the name and the namespace of the wrapper element, use the <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> and <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee0bc-155">ラップされていないメッセージにメッセージ本文の複数の部分を含めることは、WS-I Basic Profile 1.1 規格に反するため、新しいメッセージ コントラクトを設計する場合はお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-155">Having more than one message body part in messages that are not wrapped is not compliant with WS-I Basic Profile 1.1 and is not recommended when designing new message contracts.</span></span> <span data-ttu-id="ee0bc-156">ただし、特定の相互運用シナリオでは、複数のラップされていないメッセージ本文が必要な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-156">However, it may be necessary to have more than one unwrapped message body part in certain specific interoperability scenarios.</span></span> <span data-ttu-id="ee0bc-157">1 つのメッセージ本文で複数のデータを転送する場合は、既定の (ラップされた) モードを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-157">If you are going to transmit more than one piece of data in a message body, it is recommended to use the default (wrapped) mode.</span></span> <span data-ttu-id="ee0bc-158">ラップされていないメッセージで複数のメッセージ ヘッダーを使用しても、何の問題もありません。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-158">Having more than one message header in unwrapped messages is completely acceptable.</span></span>  
  
## <a name="using-custom-types-inside-message-contracts"></a><span data-ttu-id="ee0bc-159">メッセージ コントラクト内部でのカスタム型の使用</span><span class="sxs-lookup"><span data-stu-id="ee0bc-159">Using Custom Types Inside Message Contracts</span></span>  
 <span data-ttu-id="ee0bc-160">メッセージが使用されるサービス コントラクト用に選択されたシリアル化エンジンを使用して、個々のメッセージ ヘッダーとメッセージ本文がシリアル化されます (XML に変換されます)。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-160">Each individual message header and message body part is serialized (turned into XML) using the chosen serialization engine for the service contract where the message is used.</span></span> <span data-ttu-id="ee0bc-161">既定のシリアル化エンジンである `XmlFormatter` は、データ コントラクトを持つ任意の型を (<xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> を持つことによって) 明示的に処理することも、(プリミティブ型にしたり、<xref:System.SerializableAttribute?displayProperty=nameWithType> を持ったりすることなどによって) 暗黙的に処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-161">The default serialization engine, the `XmlFormatter`, can handle any type that has a data contract, either explicitly (by having the <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) or implicitly (by being a primitive type, having the <xref:System.SerializableAttribute?displayProperty=nameWithType>, and so on).</span></span> <span data-ttu-id="ee0bc-162">詳細については、「[データコントラクトの使用](using-data-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-162">For more information, see [Using Data Contracts](using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="ee0bc-163">前の例では、`Operation` 型と `BankingTransactionData` 型は、データ コントラクトを持つ必要があります。また、`transactionDate` がプリミティブである (したがって、暗黙のデータ コントラクトを持つ) ため、<xref:System.DateTime> はシリアル化可能です。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-163">In the preceding example, the `Operation` and `BankingTransactionData` types must have a data contract, and `transactionDate` is serializable because <xref:System.DateTime> is a primitive (and so has an implicit data contract).</span></span>  
  
 <span data-ttu-id="ee0bc-164">ただし、別のシリアル化エンジンである `XmlSerializer` に切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-164">However, it is possible to switch to a different serialization engine, the `XmlSerializer`.</span></span> <span data-ttu-id="ee0bc-165">このような切り替えを行う場合は、メッセージ ヘッダーと本文の各部分に使用されているすべての型が `XmlSerializer` を使用してシリアル化可能であることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-165">If you make such a switch, you should ensure that all of the types used for message headers and body parts are serializable using the `XmlSerializer`.</span></span>  
  
## <a name="using-arrays-inside-message-contracts"></a><span data-ttu-id="ee0bc-166">メッセージ コントラクト内部での配列の使用</span><span class="sxs-lookup"><span data-stu-id="ee0bc-166">Using Arrays Inside Message Contracts</span></span>  
 <span data-ttu-id="ee0bc-167">メッセージ コントラクトでは、反復要素の配列を 2 とおりの方法で使用できます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-167">You can use arrays of repeating elements in message contracts in two ways.</span></span>  
  
 <span data-ttu-id="ee0bc-168">最初の方法は、配列上で <xref:System.ServiceModel.MessageHeaderAttribute> または <xref:System.ServiceModel.MessageBodyMemberAttribute> を直接使用する方法です。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-168">The first is to use a <xref:System.ServiceModel.MessageHeaderAttribute> or a <xref:System.ServiceModel.MessageBodyMemberAttribute> directly on the array.</span></span> <span data-ttu-id="ee0bc-169">この場合は、配列全体が複数の子要素を含む 1 つの要素 (つまり、1 つのヘッダーまたは 1 つの本文) としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-169">In this case, the entire array is serialized as one element (that is, one header or one body part) with multiple child elements.</span></span> <span data-ttu-id="ee0bc-170">次の例のクラスについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-170">Consider the class in the following example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingDepositLog  
{  
  [MessageHeader] public int numRecords;  
  [MessageHeader] public DepositRecord[] records;  
  [MessageHeader] public int branchID;  
}  
```  
  
 <span data-ttu-id="ee0bc-171">これは、次のような SOAP ヘッダーになります。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-171">This results in SOAP headers is similar to the following.</span></span>  
  
```xml  
<BankingDepositLog>  
<numRecords>3</numRecords>  
<records>  
  <DepositRecord>Record1</DepositRecord>  
  <DepositRecord>Record2</DepositRecord>  
  <DepositRecord>Record3</DepositRecord>  
</records>  
<branchID>20643</branchID>  
</BankingDepositLog>  
```  
  
 <span data-ttu-id="ee0bc-172">もう 1 つの方法は、<xref:System.ServiceModel.MessageHeaderArrayAttribute> を使用する方法です。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-172">An alternative to this is to use the <xref:System.ServiceModel.MessageHeaderArrayAttribute>.</span></span> <span data-ttu-id="ee0bc-173">この場合、各配列要素が個別にシリアル化されるため、次のように配列要素ごとに 1 つのヘッダーが付加されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-173">In this case, each array element is serialized independently and so that each array element has one header, similar to the following.</span></span>  
  
```xml  
<numRecords>3</numRecords>  
<records>Record1</records>  
<records>Record2</records>  
<records>Record3</records>  
<branchID>20643</branchID>  
```  
  
 <span data-ttu-id="ee0bc-174">配列エントリの既定の名前は、<xref:System.ServiceModel.MessageHeaderArrayAttribute> 属性が適用されたメンバーの名前になります。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-174">The default name for array entries is the name of the member to which the <xref:System.ServiceModel.MessageHeaderArrayAttribute> attributes is applied.</span></span>  
  
 <span data-ttu-id="ee0bc-175"><xref:System.ServiceModel.MessageHeaderArrayAttribute> 属性は、<xref:System.ServiceModel.MessageHeaderAttribute> から継承されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-175">The <xref:System.ServiceModel.MessageHeaderArrayAttribute> attribute inherits from the <xref:System.ServiceModel.MessageHeaderAttribute>.</span></span> <span data-ttu-id="ee0bc-176">この属性は、非配列属性と同じ機能セットを持ちます。たとえば、単一のヘッダーに設定するのと同様に、ヘッダーの配列に順序、名前、および名前空間を設定できます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-176">It has the same set of features as the non-array attributes, for example, it is possible to set the order, name, and namespace for an array of headers in the same way you set it for a single header.</span></span> <span data-ttu-id="ee0bc-177">配列で `Order` プロパティを使用すると、その配列全体に適用されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-177">When you use the `Order` property on an array, it applies to the entire array.</span></span>  
  
 <span data-ttu-id="ee0bc-178"><xref:System.ServiceModel.MessageHeaderArrayAttribute> を適用できるのは配列だけであり、コレクションには適用できません。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-178">You can apply the <xref:System.ServiceModel.MessageHeaderArrayAttribute> only to arrays, not collections.</span></span>  
  
## <a name="using-byte-arrays-in-message-contracts"></a><span data-ttu-id="ee0bc-179">メッセージ コントラクトでのバイト配列の使用</span><span class="sxs-lookup"><span data-stu-id="ee0bc-179">Using Byte Arrays in Message Contracts</span></span>  
 <span data-ttu-id="ee0bc-180">バイト配列を非配列属性 (<xref:System.ServiceModel.MessageBodyMemberAttribute> と <xref:System.ServiceModel.MessageHeaderAttribute>) で使用した場合は、配列としてではなく、生成された XML 内で Base64 でエンコードされたデータとして表現される特殊なプリミティブ型として扱われます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-180">Byte arrays, when used with the non-array attributes (<xref:System.ServiceModel.MessageBodyMemberAttribute> and <xref:System.ServiceModel.MessageHeaderAttribute>), are not treated as arrays but as a special primitive type represented as Base64-encoded data in the resulting XML.</span></span>  
  
 <span data-ttu-id="ee0bc-181"><xref:System.ServiceModel.MessageHeaderArrayAttribute> 配列属性でバイト配列を使用した場合、結果は使用しているシリアライザーによって異なります。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-181">When you use byte arrays with the array attribute <xref:System.ServiceModel.MessageHeaderArrayAttribute>, the results depend on the serializer in use.</span></span> <span data-ttu-id="ee0bc-182">既定のシリアライザーでは、配列が個々のバイト エントリとして表されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-182">With the default serializer, the array is represented as an individual entry for each byte.</span></span> <span data-ttu-id="ee0bc-183">ただし、(サービス コントラクトの `XmlSerializer` を使用して) <xref:System.ServiceModel.XmlSerializerFormatAttribute> を選択した場合は、配列属性と非配列属性のどちらを使用しているかに関係なく、バイト配列は Base64 データとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-183">However, when the `XmlSerializer` is selected, (using the <xref:System.ServiceModel.XmlSerializerFormatAttribute> on the service contract), byte arrays are treated as Base64 data regardless of whether the array or non-array attributes are used.</span></span>  
  
## <a name="signing-and-encrypting-parts-of-the-message"></a><span data-ttu-id="ee0bc-184">メッセージの一部の署名と暗号化</span><span class="sxs-lookup"><span data-stu-id="ee0bc-184">Signing and Encrypting Parts of the Message</span></span>  
 <span data-ttu-id="ee0bc-185">メッセージ コントラクトでは、メッセージのヘッダーまたは本文にデジタル署名し、暗号化するかどうかを示すことができます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-185">A message contract can indicate whether the headers and/or body of the message should be digitally signed and encrypted.</span></span>  
  
 <span data-ttu-id="ee0bc-186">この操作は、<xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> 属性と <xref:System.ServiceModel.MessageHeaderAttribute> 属性の <xref:System.ServiceModel.MessageBodyMemberAttribute> プロパティを設定することによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-186">This is done by setting the <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> property on the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="ee0bc-187">このプロパティは、<xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> 型の列挙体であり、<xref:System.Net.Security.ProtectionLevel.None> (暗号化と署名を行わない)、<xref:System.Net.Security.ProtectionLevel.Sign> (デジタル署名だけを行う)、または <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (暗号化とデジタル署名の両方を行う) に設定できます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-187">The property is an enumeration of the <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> type and can be set to <xref:System.Net.Security.ProtectionLevel.None> (no encryption or signature), <xref:System.Net.Security.ProtectionLevel.Sign> (digital signature only), or <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (both encryption and a digital signature).</span></span> <span data-ttu-id="ee0bc-188">既定値は、<xref:System.Net.Security.ProtectionLevel.EncryptAndSign> です。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-188">The default is <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
 <span data-ttu-id="ee0bc-189">これらのセキュリティ機能を使用するには、バインディングと動作を適切に構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-189">For these security features to work, you must properly configure the binding and behaviors.</span></span> <span data-ttu-id="ee0bc-190">適切な構成を行わずにこれらのセキュリティ機能を使用した場合 (資格情報を指定せずにメッセージに署名しようとした場合など)、検証時に例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-190">If you use these security features without the proper configuration (for example, attempting to sign a message without supplying your credentials), an exception is thrown at validation time.</span></span>  
  
 <span data-ttu-id="ee0bc-191">メッセージ ヘッダーの場合、ヘッダーごとに保護レベルが設定されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-191">For message headers, the protection level is determined individually for each header.</span></span>  
  
 <span data-ttu-id="ee0bc-192">メッセージ本文の各部分の場合は、保護レベルを "最小保護レベル" と見なすことができます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-192">For message body parts, the protection level can be thought of as the "minimum protection level."</span></span> <span data-ttu-id="ee0bc-193">本文には、その数に関係なく 1 つの保護レベルしか設定できません。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-193">The body has only one protection level, regardless of the number of body parts.</span></span> <span data-ttu-id="ee0bc-194">本文の保護レベルは、本文の全部分の中の最も高い <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> プロパティの設定によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-194">The protection level of the body is determined by the highest <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> property setting of all the body parts.</span></span> <span data-ttu-id="ee0bc-195">ただし、本文の各部分の保護レベルを必要最小限の保護レベルに設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-195">However, you should set the protection level of each body part to the actual minimum protection level required.</span></span>  
  
 <span data-ttu-id="ee0bc-196">次のコード例のクラスについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-196">Consider the class in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class PatientRecord  
{  
   [MessageHeader(ProtectionLevel=None)] public int recordID;  
   [MessageHeader(ProtectionLevel=Sign)] public string patientName;  
   [MessageHeader(ProtectionLevel=EncryptAndSign)] public string SSN;  
   [MessageBodyMember(ProtectionLevel=None)] public string comments;  
   [MessageBodyMember(ProtectionLevel=Sign)] public string diagnosis;  
   [MessageBodyMember(ProtectionLevel=EncryptAndSign)] public string medicalHistory;  
}  
```  
  
 <span data-ttu-id="ee0bc-197">この例では、`recordID` ヘッダーは保護されず、`patientName` は署名`signed`され、`SSN` は暗号化および署名されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-197">In this example, the `recordID` header is not protected, `patientName` is `signed`, and `SSN` is encrypted and signed.</span></span> <span data-ttu-id="ee0bc-198">本文の comments と diagnosis の各部分では低い保護レベルを指定していても、本文の少なくとも 1 つの部分 (`medicalHistory`) に <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> が適用されているため、メッセージ本文全体が暗号化され、署名されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-198">At least one body part, `medicalHistory`, has <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> applied, and thus the entire message body is encrypted and signed, even though the comments and diagnosis body parts specify lower protection levels.</span></span>  
  
## <a name="soap-action"></a><span data-ttu-id="ee0bc-199">SOAP アクション</span><span class="sxs-lookup"><span data-stu-id="ee0bc-199">SOAP Action</span></span>  
 <span data-ttu-id="ee0bc-200">SOAP 標準と関連する Web サービス標準では、送信されるすべての SOAP メッセージに設定可能な `Action` という名前のプロパティが定義されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-200">SOAP and related Web services standards define a property called `Action` that can be present for every SOAP message sent.</span></span> <span data-ttu-id="ee0bc-201">このプロパティの値は、操作の <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> プロパティと <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> プロパティによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-201">The operation's <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> properties control the value of this property.</span></span>  
  
## <a name="soap-header-attributes"></a><span data-ttu-id="ee0bc-202">SOAP ヘッダーの属性</span><span class="sxs-lookup"><span data-stu-id="ee0bc-202">SOAP Header Attributes</span></span>  
 <span data-ttu-id="ee0bc-203">SOAP 標準では、ヘッダーに設定可能な次の属性が定義されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-203">The SOAP standard defines the following attributes that may exist on a header:</span></span>  
  
- <span data-ttu-id="ee0bc-204">`Actor/Role` (SOAP 1.1 では `Actor`、SOAP 1.2 では `Role`)</span><span class="sxs-lookup"><span data-stu-id="ee0bc-204">`Actor/Role` (`Actor` in SOAP 1.1, `Role` in SOAP 1.2)</span></span>  
  
- `MustUnderstand`  
  
- `Relay`  
  
 <span data-ttu-id="ee0bc-205">`Actor` 属性または `Role` 属性は、指定のヘッダーが対象とするノードの URI (Uniform Resource Identifier) を指定します。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-205">The `Actor` or `Role` attribute specifies the Uniform Resource Identifier (URI) of the node for which a given header is intended.</span></span> <span data-ttu-id="ee0bc-206">`MustUnderstand` 属性は、ヘッダー処理ノードがヘッダーを認識する必要があるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-206">The `MustUnderstand` attribute specifies whether the node processing the header must understand it.</span></span> <span data-ttu-id="ee0bc-207">`Relay` 属性は、ダウンストリーム ノードにヘッダーを中継する必要があるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-207">The `Relay` attribute specifies whether the header is to be relayed to downstream nodes.</span></span> <span data-ttu-id="ee0bc-208">WCF では、 `MustUnderstand` このトピックで後述する「メッセージコントラクトのバージョン管理」セクションで指定されている属性を除き、受信メッセージに対してこれらの属性の処理は実行されません。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-208">WCF does not perform any processing of these attributes on incoming messages, except for the `MustUnderstand` attribute, as specified in the "Message Contract Versioning" section later in this topic.</span></span> <span data-ttu-id="ee0bc-209">ただし、後述するように、必要に応じてこれらの属性を読み書きすることができます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-209">However, it allows you to read and write these attributes as necessary, as in the following description.</span></span>  
  
 <span data-ttu-id="ee0bc-210">既定では、メッセージの送信時にこれらの属性は出力されません。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-210">When sending a message, these attributes are not emitted by default.</span></span> <span data-ttu-id="ee0bc-211">これは、2 とおりの方法で変更できます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-211">You can change this in two ways.</span></span> <span data-ttu-id="ee0bc-212">1 つ目の方法として、次のコード例に示すように、<xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>、<xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>、および <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> の各プロパティを変更することによって、属性を必要な値に静的に設定できます </span><span class="sxs-lookup"><span data-stu-id="ee0bc-212">First, you may statically set the attributes to any desired values by changing the <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, and <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> properties, as shown in the following code example.</span></span> <span data-ttu-id="ee0bc-213">(`Role` プロパティが存在しないことに注意してください。SOAP 1.2 を使用している場合は、<xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> プロパティを設定すると `Role` 属性が出力されます)。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-213">(Note that there is no `Role` property; setting the <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> property emits the `Role` attribute if you are using SOAP 1.2).</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader(Actor="http://auditingservice.contoso.com", MustUnderstand=true)] public bool IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
```  
  
 <span data-ttu-id="ee0bc-214">これらの属性を制御する 2 番目の方法は、コードを通して動的に行う方法です。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-214">The second way to control these attributes is dynamically, through code.</span></span> <span data-ttu-id="ee0bc-215">これを行うには、必要なヘッダーの型を <xref:System.ServiceModel.MessageHeader%601> 型にラップし (この型と非ジェネリック バージョンを混同しないようにしてください)、その型を <xref:System.ServiceModel.MessageHeaderAttribute> と共に使用します。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-215">You can achieve this by wrapping the desired header type in the <xref:System.ServiceModel.MessageHeader%601> type (be sure not to confuse this type with the non-generic version) and by using the type together with the <xref:System.ServiceModel.MessageHeaderAttribute>.</span></span> <span data-ttu-id="ee0bc-216">これで、次のコード例に示すように、<xref:System.ServiceModel.MessageHeader%601> のプロパティを使用して SOAP 属性を設定できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-216">Then, you can use properties on the <xref:System.ServiceModel.MessageHeader%601> to set the SOAP attributes, as shown in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public MessageHeader<bool> IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
// application code:  
BankingTransaction bt = new BankingTransaction();  
bt.IsAudited = new MessageHeader<bool>();  
bt.IsAudited.Content = false; // Set IsAudited header value to "false"  
bt.IsAudited.Actor="http://auditingservice.contoso.com";  
bt.IsAudited.MustUnderstand=true;  
```  
  
 <span data-ttu-id="ee0bc-217">動的制御機構と静的制御機構の両方を使用する場合、静的な設定が既定で使用されますが、次のコードに示すように、後で動的機構を使用して静的な設定をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-217">If you use both the dynamic and the static control mechanisms, the static settings are used as a default but can later be overridden by using the dynamic mechanism, as shown in the following code.</span></span>  
  
```csharp  
[MessageHeader(MustUnderstand=true)] public MessageHeader<Person> documentApprover;  
// later on in the code:  
BankingTransaction bt = new BankingTransaction();  
bt.documentApprover = new MessageHeader<Person>();  
bt.documentApprover.MustUnderstand = false; // override the static default of 'true'  
```  
  
 <span data-ttu-id="ee0bc-218">次のコードに示すように、属性を動的に制御して繰り返すヘッダーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-218">Creating repeated headers with dynamic attribute control is allowed, as shown in the following code.</span></span>  
  
```csharp  
[MessageHeaderArray] public MessageHeader<Person> documentApprovers[];  
```  
  
 <span data-ttu-id="ee0bc-219">受信側で、<xref:System.ServiceModel.MessageHeader%601> クラスがこの型のヘッダーで使用されている場合にのみ、これらの SOAP 属性の読み取りを実行できます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-219">On the receiving side, reading these SOAP attributes can only be done if the <xref:System.ServiceModel.MessageHeader%601> class is used for the header in the type.</span></span> <span data-ttu-id="ee0bc-220">受信メッセージの属性設定を明らかにするために、`Actor` 型のヘッダーの `Relay`、`MustUnderstand`、または <xref:System.ServiceModel.MessageHeader%601> の各プロパティを調べます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-220">Examine the `Actor`, `Relay`, or `MustUnderstand` properties of a header of the <xref:System.ServiceModel.MessageHeader%601> type to discover the attribute settings on the received message.</span></span>  
  
 <span data-ttu-id="ee0bc-221">メッセージを受信して返信するときに、これらの SOAP 属性設定は <xref:System.ServiceModel.MessageHeader%601> 型のヘッダーとして往復するだけです。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-221">When a message is received and then sent back, the SOAP attribute settings only go round-trip for headers of the <xref:System.ServiceModel.MessageHeader%601> type.</span></span>  
  
## <a name="order-of-soap-body-parts"></a><span data-ttu-id="ee0bc-222">SOAP 本文の順序</span><span class="sxs-lookup"><span data-stu-id="ee0bc-222">Order of SOAP Body Parts</span></span>  
 <span data-ttu-id="ee0bc-223">状況によっては、本文の各部分の順序を制御する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-223">In some circumstances, you may need to control the order of the body parts.</span></span> <span data-ttu-id="ee0bc-224">本文要素の既定の順序はアルファベット順ですが、<xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> プロパティで制御できます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-224">The order of the body elements is alphabetical by default, but can be controlled by the <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="ee0bc-225">このプロパティのセマンティクスは、継承シナリオにおける動作を除き、<xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> プロパティのセマンティクスと同じです (メッセージ コントラクトでは、派生型の本文メンバーの前に基本型の本文メンバーが並べ替えられることはありません)。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-225">This property has the same semantics as the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> property, except for the behavior in inheritance scenarios (in message contracts, base type body members are not sorted before the derived type body members).</span></span> <span data-ttu-id="ee0bc-226">詳細については、「[データメンバーの順序](data-member-order.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-226">For more information, see [Data Member Order](data-member-order.md).</span></span>  
  
 <span data-ttu-id="ee0bc-227">次の例では、通常はアルファベット順で最初である `amount` が先頭にきますが、</span><span class="sxs-lookup"><span data-stu-id="ee0bc-227">In the following example, `amount` would normally come first because it is first alphabetically.</span></span> <span data-ttu-id="ee0bc-228"><xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> プロパティによって 3 番目の位置に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-228">However, the <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> property puts it into the third position.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember(Order=1)] public Account sourceAccount;  
  [MessageBodyMember(Order=2)] public Account targetAccount;  
  [MessageBodyMember(Order=3)] public int amount;  
}  
```  
  
## <a name="message-contract-versioning"></a><span data-ttu-id="ee0bc-229">メッセージ コントラクトのバージョン管理</span><span class="sxs-lookup"><span data-stu-id="ee0bc-229">Message Contract Versioning</span></span>  
 <span data-ttu-id="ee0bc-230">場合によっては、メッセージ コントラクトを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-230">Occasionally, you may need to change message contracts.</span></span> <span data-ttu-id="ee0bc-231">たとえば、新しいバージョンのアプリケーションによってメッセージに余分なヘッダーが追加された場合です。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-231">For example, a new version of your application may add an extra header to a message.</span></span> <span data-ttu-id="ee0bc-232">この場合、新しいバージョンから古いバージョンに送信するときは、システムは余分なヘッダーを処理し、逆方向に送信するときは不足しているヘッダーを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-232">Then, when sending from the new version to the old, the system must deal with an extra header, as well as a missing header when going in the other direction.</span></span>  
  
 <span data-ttu-id="ee0bc-233">ヘッダーのバージョン管理には、次のルールが適用されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-233">The following rules apply for versioning headers:</span></span>  
  
- <span data-ttu-id="ee0bc-234">WCF では、不足しているヘッダーにはオブジェクトが存在しません。対応するメンバーは既定値のままになります。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-234">WCF does not object to the missing headers—the corresponding members are left at their default values.</span></span>  
  
- <span data-ttu-id="ee0bc-235">WCF では、予期しない余分なヘッダーも無視されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-235">WCF also ignores unexpected extra headers.</span></span> <span data-ttu-id="ee0bc-236">このルールの 1 つの例外は、入力 SOAP メッセージ内の余分なヘッダーの `MustUnderstand` 属性が `true` に設定されている場合です。この場合、認識する必要のあるヘッダーを処理できないため、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-236">The one exception to this rule is if the extra header has a `MustUnderstand` attribute set to `true` in the incoming SOAP message—in this case, an exception is thrown because a header that must be understood cannot be processed.</span></span>  
  
 <span data-ttu-id="ee0bc-237">メッセージ本文にも同様のバージョン管理ルールがあります。メッセージ本文の不足している部分と追加された部分はいずれも無視されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-237">Message bodies have similar versioning rules—both missing and additional message body parts are ignored.</span></span>  
  
## <a name="inheritance-considerations"></a><span data-ttu-id="ee0bc-238">継承に関する留意点</span><span class="sxs-lookup"><span data-stu-id="ee0bc-238">Inheritance Considerations</span></span>  
 <span data-ttu-id="ee0bc-239">メッセージ コントラクト型は、基本型がメッセージ コントラクトを持っている限り、他の型から継承することができます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-239">A message contract type can inherit from another type, as long as the base type also has a message contract.</span></span>  
  
 <span data-ttu-id="ee0bc-240">他のメッセージ コントラクト型から継承したメッセージ コントラクト型を使用して、メッセージを作成したり、メッセージにアクセスしたりする場合、次のルールが適用されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-240">When creating or accessing a message using a message contract type that inherits from other message contract types, the following rules apply:</span></span>  
  
- <span data-ttu-id="ee0bc-241">継承階層内のすべてのメッセージ ヘッダーが収集され、そのメッセージの完全なヘッダー セットが形成されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-241">All of the message headers in the inheritance hierarchy are collected together to form the full set of headers for the message.</span></span>  
  
- <span data-ttu-id="ee0bc-242">継承階層内のすべてのメッセージ本文が収集され、完全なメッセージ本文が形成されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-242">All of the message body parts in the inheritance hierarchy are collected together to form the full message body.</span></span> <span data-ttu-id="ee0bc-243">本文の各部分は、継承階層内での位置に関係なく、通常の順序ルール (<xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> プロパティ順、続いてアルファベット順) に従って並べられます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-243">The body parts are ordered according to the usual ordering rules (by <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> property and then alphabetical), with no relevance to their place in the inheritance hierarchy.</span></span> <span data-ttu-id="ee0bc-244">メッセージ本文が継承ツリーの複数レベルに存在するメッセージ コントラクト継承の使用は、あまりお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-244">Using message contract inheritance where message body parts occur at multiple levels of the inheritance tree is strongly discouraged.</span></span> <span data-ttu-id="ee0bc-245">基本クラスと派生クラスでヘッダーまたは本文に同じ名前が定義されている場合は、base-most クラスからのメンバーがそのヘッダーまたは本文の値を保存するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-245">If a base class and a derived class define a header or a body part with the same name, the member from the base-most class is used to store the value of that header or body part.</span></span>  
  
 <span data-ttu-id="ee0bc-246">次のコード例のクラスについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-246">Consider the classes in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class PersonRecord  
{  
  [MessageHeader(Name="ID")] public int personID;  
  [MessageBodyMember] public string patientName;  
}  
  
[MessageContract]  
public class PatientRecord : PersonRecord  
{  
  [MessageHeader(Name="ID")] public int patientID;  
  [MessageBodyMember] public string diagnosis;  
}  
```  
  
 <span data-ttu-id="ee0bc-247">`PatientRecord` クラスは、`ID` という名前の 1 つのヘッダーを持つメッセージを記述します。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-247">The `PatientRecord` class describes a message with one header called `ID`.</span></span> <span data-ttu-id="ee0bc-248">このヘッダーは、base-most メンバーが選択されたことによって、`personID` メンバーには対応しますが、`patientID` メンバーには対応しません。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-248">The header corresponds to the `personID` and not the `patientID` member, because the base-most member is chosen.</span></span> <span data-ttu-id="ee0bc-249">そのため、この場合は `patientID` フィールドは使用されません。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-249">Thus, the `patientID` field is useless in this case.</span></span> <span data-ttu-id="ee0bc-250">メッセージ本文には、アルファベット順で、`diagnosis` 要素の次に `patientName` 要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-250">The body of the message contains the `diagnosis` element followed by the `patientName` element, because that is the alphabetical order.</span></span> <span data-ttu-id="ee0bc-251">この例は、基本メッセージ コントラクトと派生メッセージ コントラクトの両方にメッセージ本文が含まれ、あまりお勧めできないパターンを示していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-251">Notice that the example shows a pattern that is strongly discouraged: both the base and the derived message contracts have message body parts.</span></span>  
  
## <a name="wsdl-considerations"></a><span data-ttu-id="ee0bc-252">WSDL に関する留意点</span><span class="sxs-lookup"><span data-stu-id="ee0bc-252">WSDL Considerations</span></span>  
 <span data-ttu-id="ee0bc-253">メッセージ コントラクトを使用するサービスから Web サービス記述言語 (WSDL: Web Services Description Language) コントラクトを生成するときには、メッセージ コントラクトのすべての機能が結果の WSDL に反映されるわけではないことに留意してください。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-253">When generating a Web Services Description Language (WSDL) contract from a service that uses message contracts, it is important to remember that not all message contract features are reflected in the resulting WSDL.</span></span> <span data-ttu-id="ee0bc-254">次の点を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-254">Consider the following points:</span></span>  
  
- <span data-ttu-id="ee0bc-255">WSDL では、ヘッダー配列の概念を表現することができません。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-255">WSDL cannot express the concept of an array of headers.</span></span> <span data-ttu-id="ee0bc-256"><xref:System.ServiceModel.MessageHeaderArrayAttribute> を使用してヘッダー配列を含むメッセージを作成した場合、結果の WSDL は配列ではなく 1 つのヘッダーだけに反映されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-256">When creating messages with an array of headers using the <xref:System.ServiceModel.MessageHeaderArrayAttribute>, the resulting WSDL reflects only one header instead of the array.</span></span>  
  
- <span data-ttu-id="ee0bc-257">結果の WSDL ドキュメントに一部の保護レベル情報が反映されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-257">The resulting WSDL document may not reflect some protection-level information.</span></span>  
  
- <span data-ttu-id="ee0bc-258">WSDL で生成されたメッセージ型が、メッセージ コントラクト型のクラスと同じ名前になります。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-258">The message type generated in the WSDL has the same name as the class name of the message contract type.</span></span>  
  
- <span data-ttu-id="ee0bc-259">複数の処理で同じメッセージ コントラクトを使用すると、WSDL ドキュメント内に複数のメッセージ型が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-259">When using the same message contract in multiple operations, multiple message types are generated in the WSDL document.</span></span> <span data-ttu-id="ee0bc-260">以降も使用できるように、"2"、"3" などの番号を付加することで名前を一意にします。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-260">The names are made unique by adding the numbers "2", "3", and so on, for subsequent uses.</span></span> <span data-ttu-id="ee0bc-261">WSDL をインポートし直すと、名前以外は同一の複数のメッセージ コントラクト型が作成されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-261">When importing back the WSDL, multiple message contract types are created and are identical except for their names.</span></span>  
  
## <a name="soap-encoding-considerations"></a><span data-ttu-id="ee0bc-262">SOAP エンコードに関する留意点</span><span class="sxs-lookup"><span data-stu-id="ee0bc-262">SOAP Encoding Considerations</span></span>  
 <span data-ttu-id="ee0bc-263">WCF では XML の従来の SOAP エンコードスタイルを使用できますが、その使用は推奨されません。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-263">WCF allows you to use the legacy SOAP encoding style of XML, however, its use is not recommended.</span></span> <span data-ttu-id="ee0bc-264">(サービス コントラクトに適用されている `Use` で、`Encoded` プロパティを <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> に設定して) このスタイルを使用する場合、次の追加の考慮事項が適用されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-264">When using this style (by setting the `Use` property to `Encoded` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> applied to the service contract), the following additional considerations apply:</span></span>  
  
- <span data-ttu-id="ee0bc-265">メッセージ ヘッダーはサポートされません。つまり、<xref:System.ServiceModel.MessageHeaderAttribute> 属性と <xref:System.ServiceModel.MessageHeaderArrayAttribute> 配列属性は、SOAP エンコーディングと互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-265">The message headers are not supported; this means that the attribute <xref:System.ServiceModel.MessageHeaderAttribute> and the array attribute <xref:System.ServiceModel.MessageHeaderArrayAttribute> are incompatible with SOAP encoding.</span></span>  
  
- <span data-ttu-id="ee0bc-266">メッセージ コントラクトがラップされていない場合、つまり、<xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> プロパティが `false` に設定されている場合は、メッセージ コントラクトが持つことのできる本文の部分は 1 つに限られます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-266">If the message contract is not wrapped, that is, if the property <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> is set to `false`, the message contract can have only one body part.</span></span>  
  
- <span data-ttu-id="ee0bc-267">要求メッセージ コントラクトのラッパー要素の名前は、操作の名前と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-267">The name of the wrapper element for the request message contract must match the operation name.</span></span> <span data-ttu-id="ee0bc-268">この場合、メッセージ コントラクトの `WrapperName` プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-268">Use the `WrapperName` property of the message contract for this.</span></span>  
  
- <span data-ttu-id="ee0bc-269">応答メッセージ コントラクトのラッパー要素の名前は、操作の名前にサフィックスとして "Response" を付けたものと同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-269">The name of the wrapper element for the response message contract must be the same as the name of the operation suffixed by 'Response'.</span></span> <span data-ttu-id="ee0bc-270">この場合、メッセージ コントラクトの <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-270">Use the <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> property of the message contract for this.</span></span>  
  
- <span data-ttu-id="ee0bc-271">SOAP エンコードはオブジェクト参照を保存します。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-271">SOAP encoding preserves object references.</span></span> <span data-ttu-id="ee0bc-272">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-272">For example, consider the following code.</span></span>  
  
    ```csharp  
    [MessageContract(WrapperName="updateChangeRecord")]  
    public class ChangeRecordRequest  
    {  
      [MessageBodyMember] Person changedBy;  
      [MessageBodyMember] Person changedFrom;  
      [MessageBodyMember] Person changedTo;  
    }  
  
    [MessageContract(WrapperName="updateChangeRecordResponse")]  
    public class ChangeRecordResponse  
    {  
      [MessageBodyMember] Person changedBy;  
      [MessageBodyMember] Person changedFrom;  
      [MessageBodyMember] Person changedTo;  
    }  
  
    // application code:  
    ChangeRecordRequest cr = new ChangeRecordRequest();  
    Person p = new Person("John Doe");  
    cr.changedBy=p;  
    cr.changedFrom=p;  
    cr.changedTo=p;  
    ```  
  
 <span data-ttu-id="ee0bc-273">SOAP エンコーディングを使用してメッセージをシリアル化した後、`changedFrom` と `changedTo` には `p` のコピーは保存されませんが、代わりに、`changedBy` 要素内部のコピーがポイントされます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-273">After serializing the message using SOAP encoding, `changedFrom` and `changedTo` do not contain their own copies of `p`, but instead point to the copy inside the `changedBy` element.</span></span>  
  
## <a name="performance-considerations"></a><span data-ttu-id="ee0bc-274">パフォーマンスに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="ee0bc-274">Performance Considerations</span></span>  
 <span data-ttu-id="ee0bc-275">すべてのメッセージ ヘッダーとメッセージ本文が個別にシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-275">Every message header and message body part is serialized independently of the others.</span></span> <span data-ttu-id="ee0bc-276">したがって、ヘッダーおよび本文ごとに同じ名前空間が繰り返し宣言される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-276">Therefore, the same namespaces can be declared again for each header and body part.</span></span> <span data-ttu-id="ee0bc-277">特に、回線上のメッセージ サイズに関して、パフォーマンスを向上させるには、複数のヘッダーと本文を単一のヘッダーまたは本文に統合します。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-277">To improve performance, especially in terms of the size of the message on the wire, consolidate multiple headers and body parts into a single header or body part.</span></span> <span data-ttu-id="ee0bc-278">たとえば、次のコードの代わりに</span><span class="sxs-lookup"><span data-stu-id="ee0bc-278">For example, instead of the following code:</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public Account sourceAccount;  
  [MessageBodyMember] public Account targetAccount;  
  [MessageBodyMember] public int amount;  
}  
```  
  
 <span data-ttu-id="ee0bc-279">次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-279">Use this code.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public OperationDetails details;  
}  
  
[DataContract]  
public class OperationDetails  
{  
  [DataMember] public Account sourceAccount;  
  [DataMember] public Account targetAccount;  
  [DataMember] public int amount;  
}  
```  
  
### <a name="event-based-asynchronous-and-message-contracts"></a><span data-ttu-id="ee0bc-280">イベント ベースの非同期とメッセージ コントラクト</span><span class="sxs-lookup"><span data-stu-id="ee0bc-280">Event-based Asynchronous and Message Contracts</span></span>  
 <span data-ttu-id="ee0bc-281">イベント ベースの非同期モデルのデザイン ガイドラインには、複数の値を返す場合に、1 つの値を `Result` プロパティとして返し、残りの値を <xref:System.EventArgs> オブジェクトのプロパティとして返すことが記載されています。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-281">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="ee0bc-282">この 1 つの結果として、クライアントがイベント ベースの非同期コマンド オプションを使用してメタデータをインポートし、操作から複数の値が返される場合、既定の <xref:System.EventArgs> オブジェクトは 1 つの値を `Result` プロパティとして返し、残りの値は <xref:System.EventArgs> オブジェクトのプロパティになります。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-282">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="ee0bc-283">メッセージ オブジェクトを `Result` プロパティとして受け取り、返された値をそのオブジェクトのプロパティとして取得する場合は、`/messageContract` コマンド オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-283">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="ee0bc-284">これにより、`Result` オブジェクトの <xref:System.EventArgs> プロパティとして応答メッセージを返すシグネチャが生成されます。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-284">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="ee0bc-285">すべての内部戻り値は、応答メッセージ オブジェクトのプロパティになります。</span><span class="sxs-lookup"><span data-stu-id="ee0bc-285">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee0bc-286">関連項目</span><span class="sxs-lookup"><span data-stu-id="ee0bc-286">See also</span></span>

- [<span data-ttu-id="ee0bc-287">データ コントラクトの使用</span><span class="sxs-lookup"><span data-stu-id="ee0bc-287">Using Data Contracts</span></span>](using-data-contracts.md)
- [<span data-ttu-id="ee0bc-288">サービスの設計と実装</span><span class="sxs-lookup"><span data-stu-id="ee0bc-288">Designing and Implementing Services</span></span>](../designing-and-implementing-services.md)
