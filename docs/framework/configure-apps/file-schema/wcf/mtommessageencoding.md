---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: bd38bf812e6d8d9e57d99bf1a5b77ebb776193a5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738845"
---
# \<mtomMessageEncoding>
<span data-ttu-id="67ad5-101">SOAP Message Transmission Optimization Mechanism (MTOM) ベースのメッセージに使用されるエンコーディングおよびメッセージ バージョン管理を指定します。</span><span class="sxs-lookup"><span data-stu-id="67ad5-101">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mtomMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="67ad5-102">構文</span><span class="sxs-lookup"><span data-stu-id="67ad5-102">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67ad5-103">属性および要素</span><span class="sxs-lookup"><span data-stu-id="67ad5-103">Attributes and Elements</span></span>  
 <span data-ttu-id="67ad5-104">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="67ad5-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67ad5-105">属性</span><span class="sxs-lookup"><span data-stu-id="67ad5-105">Attributes</span></span>  
  
|<span data-ttu-id="67ad5-106">属性</span><span class="sxs-lookup"><span data-stu-id="67ad5-106">Attribute</span></span>|<span data-ttu-id="67ad5-107">説明</span><span class="sxs-lookup"><span data-stu-id="67ad5-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="67ad5-108">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="67ad5-108">maxBufferSize</span></span>|<span data-ttu-id="67ad5-109">使用できるバッファーの最大サイズを指定する整数。</span><span class="sxs-lookup"><span data-stu-id="67ad5-109">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="67ad5-110">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="67ad5-110">maxReadPoolSize</span></span>|<span data-ttu-id="67ad5-111">新しいリーダーを割り当てずに同時に読み取り可能なメッセージの数を指定する整数です。</span><span class="sxs-lookup"><span data-stu-id="67ad5-111">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="67ad5-112">プール サイズを大きくすると、システムでは、比較的大きい作業セットで、アクティビティの急増に対する許容度が高まります。</span><span class="sxs-lookup"><span data-stu-id="67ad5-112">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="67ad5-113">既定値は、64 です。</span><span class="sxs-lookup"><span data-stu-id="67ad5-113">The default is 64.</span></span>|  
|<span data-ttu-id="67ad5-114">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="67ad5-114">maxWritePoolSize</span></span>|<span data-ttu-id="67ad5-115">新しいライターを割り当てずに同時に送信可能なメッセージの数を指定する整数です。</span><span class="sxs-lookup"><span data-stu-id="67ad5-115">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="67ad5-116">プール サイズを大きくすると、システムでは、比較的大きい作業セットで、アクティビティの急増に対する許容度が高まります。</span><span class="sxs-lookup"><span data-stu-id="67ad5-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="67ad5-117">既定値は 16 です。</span><span class="sxs-lookup"><span data-stu-id="67ad5-117">The default is 16.</span></span>|  
|<span data-ttu-id="67ad5-118">messageVersion</span><span class="sxs-lookup"><span data-stu-id="67ad5-118">messageVersion</span></span>|<span data-ttu-id="67ad5-119">バインディングを使用して送信されたメッセージの SOAP バージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="67ad5-119">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="67ad5-120">有効な値は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="67ad5-120">Valid values are</span></span><br /><br /> <span data-ttu-id="67ad5-121">- Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="67ad5-121">-   Soap11Addressing1</span></span><br /><span data-ttu-id="67ad5-122">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="67ad5-122">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="67ad5-123">既定値は Soap12Addressing10 です。</span><span class="sxs-lookup"><span data-stu-id="67ad5-123">The default is Soap12Addressing10.</span></span> <span data-ttu-id="67ad5-124">この属性は <xref:System.ServiceModel.Channels.MessageVersion> 型です。</span><span class="sxs-lookup"><span data-stu-id="67ad5-124">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="67ad5-125">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="67ad5-125">writeEncoding</span></span>|<span data-ttu-id="67ad5-126">バインドでメッセージの発行に使用される文字セット エンコーディングを指定します。</span><span class="sxs-lookup"><span data-stu-id="67ad5-126">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="67ad5-127">有効な値は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="67ad5-127">Valid values are</span></span><br /><br /> <span data-ttu-id="67ad5-128">-UnicodeFffeTextEncoding: Unicode BigEndian エンコード</span><span class="sxs-lookup"><span data-stu-id="67ad5-128">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="67ad5-129">-Utf16TextEncoding: Unicode エンコーディング</span><span class="sxs-lookup"><span data-stu-id="67ad5-129">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="67ad5-130">-Utf8TextEncoding: 8 ビットエンコード</span><span class="sxs-lookup"><span data-stu-id="67ad5-130">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="67ad5-131">既定値は Utf8TextEncoding です。</span><span class="sxs-lookup"><span data-stu-id="67ad5-131">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="67ad5-132">この属性は <xref:System.Text.Encoding> 型です。</span><span class="sxs-lookup"><span data-stu-id="67ad5-132">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="67ad5-133">子要素</span><span class="sxs-lookup"><span data-stu-id="67ad5-133">Child Elements</span></span>  
  
|<span data-ttu-id="67ad5-134">要素</span><span class="sxs-lookup"><span data-stu-id="67ad5-134">Element</span></span>|<span data-ttu-id="67ad5-135">Description</span><span class="sxs-lookup"><span data-stu-id="67ad5-135">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="67ad5-136">このバインドを使用して設定されるエンドポイントにより処理可能な、SOAP メッセージの複雑さに対する制約を定義します。</span><span class="sxs-lookup"><span data-stu-id="67ad5-136">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="67ad5-137">この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="67ad5-137">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="67ad5-138">親要素</span><span class="sxs-lookup"><span data-stu-id="67ad5-138">Parent Elements</span></span>  
  
|<span data-ttu-id="67ad5-139">要素</span><span class="sxs-lookup"><span data-stu-id="67ad5-139">Element</span></span>|<span data-ttu-id="67ad5-140">Description</span><span class="sxs-lookup"><span data-stu-id="67ad5-140">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="67ad5-141">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="67ad5-141">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67ad5-142">解説</span><span class="sxs-lookup"><span data-stu-id="67ad5-142">Remarks</span></span>  
 <span data-ttu-id="67ad5-143">エンコーディングは、メッセージをバイト シーケンスに変換するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="67ad5-143">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="67ad5-144">デコードは、その逆のプロセスです。</span><span class="sxs-lookup"><span data-stu-id="67ad5-144">Decoding is the reverse process.</span></span> <span data-ttu-id="67ad5-145">WCF (Windows Communication Foundation) には、SOAP メッセージのエンコードとして、テキスト、バイナリ、および MTOM (Message Transmission Optimization Mechanism) の 3 種類があります。</span><span class="sxs-lookup"><span data-stu-id="67ad5-145">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="67ad5-146">`MtomMessageEncoding` 要素は、MTOM (Message Transmission Optimization Mechanism) エンコーディングを使用するメッセージの文字エンコーディング、メッセージのバージョン管理、およびその他の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="67ad5-146">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="67ad5-147">MTOM は、WCF メッセージでバイナリ データを転送するための効率的なテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="67ad5-147">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="67ad5-148">MTOM エンコーダーは、効率と相互運用性のバランスをとろうとします。</span><span class="sxs-lookup"><span data-stu-id="67ad5-148">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="67ad5-149">MTOM エンコーディングは、ほとんどの XML をテキスト形式で転送しますが、大きいサイズのバイナリ データ ブロックは、base64 でエンコードされた形式に変換せずに、そのまま転送することによって最適化します。</span><span class="sxs-lookup"><span data-stu-id="67ad5-149">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67ad5-150">例</span><span class="sxs-lookup"><span data-stu-id="67ad5-150">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="67ad5-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="67ad5-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="67ad5-152">メッセージ エンコーディング</span><span class="sxs-lookup"><span data-stu-id="67ad5-152">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="67ad5-153">メッセージ エンコーダーを選択する</span><span class="sxs-lookup"><span data-stu-id="67ad5-153">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="67ad5-154">バインド</span><span class="sxs-lookup"><span data-stu-id="67ad5-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="67ad5-155">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="67ad5-155">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="67ad5-156">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="67ad5-156">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
