---
title: <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
ms.openlocfilehash: 379552f461a79415e3140a8084901e0c1d6b2c32
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140480"
---
# <a name="ws2007httpbinding"></a><span data-ttu-id="b6f8d-101">\<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="b6f8d-101">\<ws2007HttpBinding></span></span>
<span data-ttu-id="b6f8d-102"><xref:System.ServiceModel.WSHttpBinding.Security%2A>、<xref:System.ServiceModel.ReliableSession>、および <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> の各バインド要素の適切なバージョンをサポートする相互運用可能なバインディングを定義します。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-102">Defines an interoperable binding that provides support for the correct versions of the <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, and <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> binding elements.</span></span>  
  
<span data-ttu-id="b6f8d-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b6f8d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b6f8d-104">&nbsp; &nbsp;[ **\<system >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="b6f8d-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b6f8d-105">&nbsp;&nbsp;&nbsp;&nbsp;\<[**バインド**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="b6f8d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="b6f8d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**ws2007HttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="b6f8d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws2007HttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6f8d-107">構文</span><span class="sxs-lookup"><span data-stu-id="b6f8d-107">Syntax</span></span>  
  
```xml  
<ws2007HttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="Message/None/Transport/TransportWithCredential">
      <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                 proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                 realm="string" />
        <message clientCredentialType ="Certificate/IssuedToken/None/UserName/Windows"
                 negotiateServiceCredential="Boolean"
                 algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
                 establishSecurityContext="Boolean"
                 negotiateServiceCredential="Boolean" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</ws2007HttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6f8d-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b6f8d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b6f8d-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6f8d-110">属性</span><span class="sxs-lookup"><span data-stu-id="b6f8d-110">Attributes</span></span>  
  
|<span data-ttu-id="b6f8d-111">属性</span><span class="sxs-lookup"><span data-stu-id="b6f8d-111">Attribute</span></span>|<span data-ttu-id="b6f8d-112">説明</span><span class="sxs-lookup"><span data-stu-id="b6f8d-112">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="b6f8d-113">クライアントがクッキーを受け入れて、それらを今後の要求に反映させるかどうかを指定する値です。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-113">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="b6f8d-114">既定値は、 `false`です。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="b6f8d-115">クッキーを使用する ASMX (ASP.NET Web サービス) と対話する場合に、このプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-115">You can use this property when you interact with ASP.NET Web services (ASMX) that use cookies.</span></span> <span data-ttu-id="b6f8d-116">これにより、サーバーから返されるクッキーが、このサービスに対するそれ以降のすべてのクライアント要求に自動的にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-116">This ensures that cookies that the server returns are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="b6f8d-117">ローカル アドレスでプロキシ サーバーをバイパスするかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-117">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="b6f8d-118">既定値は、 `false`です。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-118">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="b6f8d-119">クローズ操作が完了するまでの期間を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-119">A <xref:System.TimeSpan> value that specifies the time interval for a close operation to complete.</span></span> <span data-ttu-id="b6f8d-120">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-120">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b6f8d-121">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-121">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="b6f8d-122">URI (Uniform Resource Identifier) の解析に使用する HTTP ホスト名比較モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-122">Specifies the HTTP hostname comparison mode used to parse Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="b6f8d-123">この属性は <xref:System.ServiceModel.HostNameComparisonMode> 型で、URI が一致したときにサービスへのアクセスにホスト名を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-123">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="b6f8d-124">既定値は <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> で、一致しているホスト名を無視します。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-124">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="b6f8d-125">このバインドに使用するバッファー プールの最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-125">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="b6f8d-126">既定値は 524,288 バイト (512 × 1,024) です。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-126">The default is 524,288 bytes (512 × 1,024).</span></span> <span data-ttu-id="b6f8d-127">Windows Communication Foundation (WCF) では、多くの部分でバッファーを使用します。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-127">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="b6f8d-128">使用するたびに毎回バッファーを作成および破棄すると負荷が高くなります。バッファーのガベージ コレクションも同様です。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-128">Creating and destroying buffers each time they are used is expensive, as is garbage collection for buffers.</span></span> <span data-ttu-id="b6f8d-129">バッファー プールを使用すると、バッファーをプールから取得して使用し、作業が終わったらプールに戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool when you are done.</span></span> <span data-ttu-id="b6f8d-130">これで、バッファーの作成と破棄によるオーバーヘッドを回避できます。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-130">This avoids the overhead in creating and destroying buffers.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="b6f8d-131">このバインディングで構成されたチャネルで受信可能な、ヘッダーを含む最大メッセージ サイズ (バイト単位) です。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-131">The maximum message size, in bytes, including headers, which a channel configured with this binding, can receive.</span></span> <span data-ttu-id="b6f8d-132">この制限を超える場合、メッセージの送信者は SOAP エラーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-132">The sender of a message exceeding this limit receives a SOAP fault.</span></span> <span data-ttu-id="b6f8d-133">メッセージは受信者によってドロップされ、トレース ログにこのイベントのエントリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-133">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="b6f8d-134">既定値は 65536 です。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-134">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="b6f8d-135">メッセージのエンコードに使用されるエンコーダーを定義します。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-135">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="b6f8d-136">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-136">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b6f8d-137">-   `Text`: テキストメッセージエンコーダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-137">-   `Text`: Use a text message encoder.</span></span><br /><span data-ttu-id="b6f8d-138">-   `Mtom`: メッセージ伝送組織機構 1.0 (MTOM) エンコーダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-138">-   `Mtom`: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="b6f8d-139">既定値は、 `Text`です。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-139">The default is `Text`.</span></span><br /><br /> <span data-ttu-id="b6f8d-140">この属性は <xref:System.ServiceModel.WSMessageEncoding> 型です。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-140">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="b6f8d-141">バインドの構成名。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-141">The configuration name of the binding.</span></span> <span data-ttu-id="b6f8d-142">この値は、バインディングの ID として使用されるため、一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-142">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="b6f8d-143">.NET Framework 4 以降では、バインドと動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-143">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="b6f8d-144">既定の構成と無名のバインドおよび動作の詳細については、「 [WCF サービスの](../../../wcf/samples/simplified-configuration-for-wcf-services.md)構成と簡略化された構成の[簡略化](../../../wcf/simplified-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-144">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="b6f8d-145">実行中の操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="b6f8d-146">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b6f8d-147">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-147">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="b6f8d-148">HTTP プロキシのアドレスを指定する URI。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-148">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="b6f8d-149">`useSystemWebProxy` が `true` の場合、この設定を `null` にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-149">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="b6f8d-150">既定値は、 `null`です。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-150">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="b6f8d-151">受信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="b6f8d-152">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b6f8d-153">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-153">The default is 00:01:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="b6f8d-154">送信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-154">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="b6f8d-155">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-155">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b6f8d-156">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-156">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="b6f8d-157">バインディングでメッセージの発行に使用する文字セット エンコーディングを指定します。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-157">Specifies the character set encoding to use for emitting messages on the binding.</span></span> <span data-ttu-id="b6f8d-158">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-158">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b6f8d-159">-   `UnicodeFffeTextEncoding`: Unicode ビッグエンディアンエンコーディング。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-159">-   `UnicodeFffeTextEncoding`: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="b6f8d-160">-   `Utf16TextEncoding`:16 ビットエンコード。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-160">-   `Utf16TextEncoding`: 16-bit encoding.</span></span><br /><span data-ttu-id="b6f8d-161">-   `Utf8TextEncoding`: 8 ビットエンコーディング。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-161">-   `Utf8TextEncoding`: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="b6f8d-162">既定値は、 `Utf8TextEncoding`です。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-162">The default is `Utf8TextEncoding`.</span></span><br /><br /> <span data-ttu-id="b6f8d-163">この属性は <xref:System.Text.Encoding> 型です。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-163">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="b6f8d-164">バインドが WS-Transactions のフローをサポートするかどうかを指定する値。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-164">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="b6f8d-165">既定値は、 `false`です。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-165">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="b6f8d-166">システムの自動設定 HTTP プロキシを使用するかどうかを示す値です。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-166">A value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="b6f8d-167">既定値は、 `true`です。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-167">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6f8d-168">子要素</span><span class="sxs-lookup"><span data-stu-id="b6f8d-168">Child Elements</span></span>  
  
|<span data-ttu-id="b6f8d-169">要素</span><span class="sxs-lookup"><span data-stu-id="b6f8d-169">Element</span></span>|<span data-ttu-id="b6f8d-170">説明</span><span class="sxs-lookup"><span data-stu-id="b6f8d-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6f8d-171">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="b6f8d-171">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="b6f8d-172">バインディングのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-172">Defines the security settings for the binding.</span></span> <span data-ttu-id="b6f8d-173">この要素は <xref:System.ServiceModel.Configuration.WSHttpSecurityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-173">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="b6f8d-174">[readerQuotas > の \<](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b6f8d-174">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="b6f8d-175">このバインディングを使用して設定されるエンドポイントで処理できる、SOAP メッセージの複雑さに対する制約を定義します。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-175">Defines the constraints on the complexity of SOAP messages that endpoints configured with this binding can process.</span></span> <span data-ttu-id="b6f8d-176">この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-176">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="b6f8d-177">[\<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="b6f8d-177">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="b6f8d-178">チャネルのエンドポイント間に信頼できるセッションを確立するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-178">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b6f8d-179">親要素</span><span class="sxs-lookup"><span data-stu-id="b6f8d-179">Parent Elements</span></span>  
  
|<span data-ttu-id="b6f8d-180">要素</span><span class="sxs-lookup"><span data-stu-id="b6f8d-180">Element</span></span>|<span data-ttu-id="b6f8d-181">説明</span><span class="sxs-lookup"><span data-stu-id="b6f8d-181">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6f8d-182">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="b6f8d-182">\<bindings></span></span>](bindings.md)|<span data-ttu-id="b6f8d-183">この要素には、標準バインディングおよびカスタム バインドのコレクションが保持されます。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-183">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6f8d-184">Remarks</span><span class="sxs-lookup"><span data-stu-id="b6f8d-184">Remarks</span></span>  
 <span data-ttu-id="b6f8d-185">`WS2007HttpBinding` は、`WSHttpBinding` と同様のシステム標準のバインディングを追加しますが、ReliableSession、Security、および TransactionFlow の各プロトコルの OASIS (Organization for the Advancement of Structured Information Standards) 標準バージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-185">The `WS2007HttpBinding` adds a system-provided binding similar to `WSHttpBinding` but uses the Organization for the Advancement of Structured Information Standards (OASIS) standard versions of the ReliableSession, Security, and TransactionFlow protocols.</span></span> <span data-ttu-id="b6f8d-186">このバインドを使用する場合、オブジェクト モデルも既定の設定も変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b6f8d-186">No changes to the object model or default settings are required when using this binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6f8d-187">例</span><span class="sxs-lookup"><span data-stu-id="b6f8d-187">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007HttpBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://www.contoso.com"
                 textEncoding="utf-16"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="Transport">
            <transport clientCredentialType="Digest"
                       proxyCredentialType="None"
                       realm="someRealm" />
            <message clientCredentialType="Windows"
                     negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     defaultProtectionLevel="None" />
          </security>
        </binding>
      </ws2007HttpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="b6f8d-188">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6f8d-188">See also</span></span>

- <xref:System.ServiceModel.WS2007HttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>
- [<span data-ttu-id="b6f8d-189">バインディング</span><span class="sxs-lookup"><span data-stu-id="b6f8d-189">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b6f8d-190">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="b6f8d-190">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b6f8d-191">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="b6f8d-191">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="b6f8d-192">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="b6f8d-192">\<binding></span></span>](bindings.md)
