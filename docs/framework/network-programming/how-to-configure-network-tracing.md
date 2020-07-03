---
title: '方法: ネットワークのトレースを構成する'
description: コンピューター構成ファイルまたはアプリケーション構成ファイルでネットワーク トレースを構成する方法について学習します。 アプリケーション構成ファイルが優先されます。
ms.date: 03/30/2017
helpviewer_keywords:
- formatting [.NET Framework], network tracing
- network tracing, configuring
- level attribute
- app.config files, network tracing
- configuration files [.NET Framework], network tracing
- protocol-level trace output
- application configuration files, network tracing
- sockets, trace output
ms.assetid: 5ef9fe4b-8d3d-490e-9259-1d014b2181af
ms.openlocfilehash: b089746e9838c591ed5ccc9ac9aaeedb217de9a9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502562"
---
# <a name="how-to-configure-network-tracing"></a><span data-ttu-id="03dec-104">方法: ネットワークのトレースを構成する</span><span class="sxs-lookup"><span data-stu-id="03dec-104">How to: Configure network tracing</span></span>

<span data-ttu-id="03dec-105">アプリケーションまたはコンピューターの構成ファイルには、ネットワークのトレースの形式と内容を決定する設定が保持されます。</span><span class="sxs-lookup"><span data-stu-id="03dec-105">The application or computer configuration file holds the settings that determine the format and content of network traces.</span></span> <span data-ttu-id="03dec-106">この手順に従う前に、トレースが有効になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="03dec-106">Before performing this procedure, be sure tracing is enabled.</span></span> <span data-ttu-id="03dec-107">詳細については、「[ネットワークのトレースの有効化](enabling-network-tracing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03dec-107">For more information, see [Enable network tracing](enabling-network-tracing.md).</span></span>

<span data-ttu-id="03dec-108">コンピューター構成ファイルの *machine.config* は、 *%windir%\Microsoft.NET\Framework* フォルダーに格納されています。</span><span class="sxs-lookup"><span data-stu-id="03dec-108">The computer configuration file, *machine.config*, is stored in the *%windir%\Microsoft.NET\Framework* folder.</span></span> <span data-ttu-id="03dec-109">*machine.config* は、コンピューターにインストールされている .NET Framework のバージョンごとに、 *%windir%\Microsoft.NET\Framework* フォルダーの下に、次のように別ファイルで用意されています。</span><span class="sxs-lookup"><span data-stu-id="03dec-109">There is a separate *machine.config* file in the folders under *%windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer, for example:</span></span>

- <span data-ttu-id="03dec-110">*C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*</span><span class="sxs-lookup"><span data-stu-id="03dec-110">*C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*</span></span>
- <span data-ttu-id="03dec-111">*C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*</span><span class="sxs-lookup"><span data-stu-id="03dec-111">*C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*</span></span>

<span data-ttu-id="03dec-112">これらの設定は、コンピューター構成ファイルよりも優先されるアプリケーション構成ファイルでも行うことができます。</span><span class="sxs-lookup"><span data-stu-id="03dec-112">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>

## <a name="configure-network-tracing"></a><span data-ttu-id="03dec-113">ネットワークのトレースを構成する</span><span class="sxs-lookup"><span data-stu-id="03dec-113">Configure network tracing</span></span>

<span data-ttu-id="03dec-114">ネットワークのトレースを構成するには、適切な構成ファイルに次の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="03dec-114">To configure network tracing, add the following lines to the appropriate configuration file.</span></span> <span data-ttu-id="03dec-115">これらの設定の値とオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="03dec-115">The values and options for these settings are described in the tables below.</span></span>

```xml
<configuration>
  <system.diagnostics>
    <sources>
      <source name="System.Net" tracemode="includehex" maxdatasize="1024">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.Cache">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.Http">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.Sockets">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.WebSockets">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
   </sources>
    <switches>
      <add name="System.Net" value="Verbose"/>
      <add name="System.Net.Cache" value="Verbose"/>
      <add name="System.Net.Http" value="Verbose"/>
      <add name="System.Net.Sockets" value="Verbose"/>
      <add name="System.Net.WebSockets" value="Verbose"/>
    </switches>
    <sharedListeners>
      <add name="System.Net"
        type="System.Diagnostics.TextWriterTraceListener"
        initializeData="network.log"
        traceOutputOptions="ProcessId, DateTime"
      />
    </sharedListeners>
    <trace autoflush="true"/>
  </system.diagnostics>
</configuration>
```

### <a name="trace-output-from-methods"></a><span data-ttu-id="03dec-116">メソッドからのトレース出力</span><span class="sxs-lookup"><span data-stu-id="03dec-116">Trace output from methods</span></span>

<span data-ttu-id="03dec-117">`<switches>` ブロックに名前を追加すると、トレース出力にその名前に関連する一部のメソッドからの情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="03dec-117">When you add a name to the `<switches>` block, the trace output includes information from some methods related to the name.</span></span> <span data-ttu-id="03dec-118">次の表に出力を示します。</span><span class="sxs-lookup"><span data-stu-id="03dec-118">The following table describes the output:</span></span>

|<span data-ttu-id="03dec-119">名前</span><span class="sxs-lookup"><span data-stu-id="03dec-119">Name</span></span>|<span data-ttu-id="03dec-120">出力元</span><span class="sxs-lookup"><span data-stu-id="03dec-120">Output from</span></span>|
|----------|-----------------|
|`System.Net.Sockets`|<span data-ttu-id="03dec-121"><xref:System.Net.Sockets.Socket>、<xref:System.Net.Sockets.TcpListener>、<xref:System.Net.Sockets.TcpClient>、および <xref:System.Net.Dns> クラスの一部のパブリック メソッド。</span><span class="sxs-lookup"><span data-stu-id="03dec-121">Some public methods of the <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, and <xref:System.Net.Dns> classes.</span></span>|
|`System.Net`|<span data-ttu-id="03dec-122"><xref:System.Net.HttpWebRequest>、<xref:System.Net.HttpWebResponse>、<xref:System.Net.FtpWebRequest>、および <xref:System.Net.FtpWebResponse> クラスの一部のパブリック メソッド、および SSL デバッグ情報 (無効な証明書、不足している発行元一覧、およびクライアント証明書エラー)。</span><span class="sxs-lookup"><span data-stu-id="03dec-122">Some public methods of the <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, and <xref:System.Net.FtpWebResponse> classes, and SSL debug information (invalid certificates, missing issuers list, and client certificate errors).</span></span>|
|`System.Net.HttpListener`|<span data-ttu-id="03dec-123"><xref:System.Net.HttpListener>、<xref:System.Net.HttpListenerRequest>、および <xref:System.Net.HttpListenerResponse> クラスの一部のパブリック メソッド。</span><span class="sxs-lookup"><span data-stu-id="03dec-123">Some public methods of the <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, and <xref:System.Net.HttpListenerResponse> classes.</span></span>|
|`System.Net.Cache`|<span data-ttu-id="03dec-124">`System.Net.Cache` 内の一部のプライベート メソッドと内部メソッド。</span><span class="sxs-lookup"><span data-stu-id="03dec-124">Some private and internal methods in `System.Net.Cache`.</span></span>|
|`System.Net.Http`|<span data-ttu-id="03dec-125"><xref:System.Net.Http.HttpClient>、<xref:System.Net.Http.DelegatingHandler>、<xref:System.Net.Http.HttpClientHandler>、<xref:System.Net.Http.HttpMessageHandler>、<xref:System.Net.Http.MessageProcessingHandler>、および <xref:System.Net.Http.WebRequestHandler> クラスの一部のパブリック メソッド。</span><span class="sxs-lookup"><span data-stu-id="03dec-125">Some public methods of the  <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>,  <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>,  <xref:System.Net.Http.MessageProcessingHandler>, and  <xref:System.Net.Http.WebRequestHandler> classes.</span></span>|
|`System.Net.WebSockets.WebSocket`|<span data-ttu-id="03dec-126"><xref:System.Net.WebSockets.ClientWebSocket> および <xref:System.Net.WebSockets.WebSocket> クラスの一部のパブリック メソッド。</span><span class="sxs-lookup"><span data-stu-id="03dec-126">Some public methods of the <xref:System.Net.WebSockets.ClientWebSocket> and <xref:System.Net.WebSockets.WebSocket> classes.</span></span>|

### <a name="trace-output-attributes"></a><span data-ttu-id="03dec-127">トレースの出力属性</span><span class="sxs-lookup"><span data-stu-id="03dec-127">Trace output attributes</span></span>

<span data-ttu-id="03dec-128">次の表に示した属性で、トレース出力を構成できます。</span><span class="sxs-lookup"><span data-stu-id="03dec-128">The attributes listed in the following table configure trace output:</span></span>

|<span data-ttu-id="03dec-129">属性名</span><span class="sxs-lookup"><span data-stu-id="03dec-129">Attribute name</span></span>|<span data-ttu-id="03dec-130">属性値</span><span class="sxs-lookup"><span data-stu-id="03dec-130">Attribute value</span></span>|
|--------------------|---------------------|
|`value`|<span data-ttu-id="03dec-131">必須の <xref:System.String> 属性です。</span><span class="sxs-lookup"><span data-stu-id="03dec-131">Required <xref:System.String> attribute.</span></span> <span data-ttu-id="03dec-132">出力の詳細度を設定します。</span><span class="sxs-lookup"><span data-stu-id="03dec-132">Sets the verbosity of the output.</span></span> <span data-ttu-id="03dec-133">有効な値は、`Critical`、`Error`、`Verbose`、`Warning`、および `Information` です。</span><span class="sxs-lookup"><span data-stu-id="03dec-133">Legitimate values are `Critical`, `Error`, `Verbose`, `Warning`, and `Information`.</span></span><br /><br /><span data-ttu-id="03dec-134">この属性は、**switches** 要素の **add** 要素に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="03dec-134">This attribute must be set on the **add** element of the **switches** element.</span></span> <span data-ttu-id="03dec-135">この属性を **source** 要素に設定すると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="03dec-135">An exception is thrown if this attribute is set on the **source** element.</span></span><br/><br/><span data-ttu-id="03dec-136">例 : `<add name="System.Net" value="Verbose"/>`</span><span class="sxs-lookup"><span data-stu-id="03dec-136">Example: `<add name="System.Net" value="Verbose"/>`</span></span>|
|`maxdatasize`|<span data-ttu-id="03dec-137">省略可能な <xref:System.Int32> 属性です。</span><span class="sxs-lookup"><span data-stu-id="03dec-137">Optional <xref:System.Int32> attribute.</span></span> <span data-ttu-id="03dec-138">各行トレースに含まれるネットワーク データの最大バイト数を設定します。</span><span class="sxs-lookup"><span data-stu-id="03dec-138">Sets the maximum number of bytes of network data included in each line trace.</span></span> <span data-ttu-id="03dec-139">既定値は 1024 です。</span><span class="sxs-lookup"><span data-stu-id="03dec-139">The default value is 1024.</span></span><br /><br /><span data-ttu-id="03dec-140">この属性は、**source** 要素に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="03dec-140">This attribute must be set on the **source** element.</span></span> <span data-ttu-id="03dec-141">この属性を **switches** 要素の下の要素に設定すると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="03dec-141">An exception is thrown if this attribute is set on an element under the **switches** element.</span></span><br/><br/><span data-ttu-id="03dec-142">例 : `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span><span class="sxs-lookup"><span data-stu-id="03dec-142">Example: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span></span>|
|`tracemode`|<span data-ttu-id="03dec-143">省略可能な <xref:System.String> 属性です。</span><span class="sxs-lookup"><span data-stu-id="03dec-143">Optional <xref:System.String> attribute.</span></span> <span data-ttu-id="03dec-144">プロトコル トレースを 16 進数およびテキストの形式で表示するには、`includehex` に設定します。</span><span class="sxs-lookup"><span data-stu-id="03dec-144">Set to `includehex` to show protocol traces in hexadecimal and text format.</span></span> <span data-ttu-id="03dec-145">テキストのみを表示するには、`protocolonly` に設定します。</span><span class="sxs-lookup"><span data-stu-id="03dec-145">Set to `protocolonly` to show only text.</span></span> <span data-ttu-id="03dec-146">既定値は `includehex` です。</span><span class="sxs-lookup"><span data-stu-id="03dec-146">The default value is `includehex`.</span></span><br /><br /><span data-ttu-id="03dec-147">この属性は、**source** 要素に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="03dec-147">This attribute must be set on the **source** element.</span></span> <span data-ttu-id="03dec-148">この属性を **switches** 要素の下の要素に設定すると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="03dec-148">An exception is thrown if this attribute is set on an element under the **switches** element.</span></span><br/><br/><span data-ttu-id="03dec-149">例 : `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span><span class="sxs-lookup"><span data-stu-id="03dec-149">Example: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span></span>|

## <a name="see-also"></a><span data-ttu-id="03dec-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="03dec-150">See also</span></span>

- [<span data-ttu-id="03dec-151">ネットワークのトレースの解釈</span><span class="sxs-lookup"><span data-stu-id="03dec-151">Interpreting Network Tracing</span></span>](interpreting-network-tracing.md)
- [<span data-ttu-id="03dec-152">.NET Framework のネットワークのトレース</span><span class="sxs-lookup"><span data-stu-id="03dec-152">Network Tracing in the .NET Framework</span></span>](network-tracing.md)
- [<span data-ttu-id="03dec-153">ネットワークのトレースの有効化</span><span class="sxs-lookup"><span data-stu-id="03dec-153">Enabling Network Tracing</span></span>](enabling-network-tracing.md)
- [<span data-ttu-id="03dec-154">アプリケーションのトレースとインストルメント</span><span class="sxs-lookup"><span data-stu-id="03dec-154">Tracing and Instrumenting Applications</span></span>](../debug-trace-profile/tracing-and-instrumenting-applications.md)
