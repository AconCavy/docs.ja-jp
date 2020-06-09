---
title: '方法: SSL 証明書を使用してポートを構成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: 30b24c4ff06cc7249d3ddb6d95549a574e313f52
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579619"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a><span data-ttu-id="2bb76-102">方法: SSL 証明書を使用してポートを構成する</span><span class="sxs-lookup"><span data-stu-id="2bb76-102">How to: Configure a Port with an SSL Certificate</span></span>

<span data-ttu-id="2bb76-103">トランスポートセキュリティを使用するクラスを使用して自己ホスト型 Windows Communication Foundation (WCF) サービスを作成する場合は、 <xref:System.ServiceModel.WSHttpBinding> x.509 証明書を使用してポートを構成する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="2bb76-103">When creating a self-hosted Windows Communication Foundation (WCF) service with the <xref:System.ServiceModel.WSHttpBinding> class that uses transport security, you must also configure a port with an X.509 certificate.</span></span> <span data-ttu-id="2bb76-104">自己ホスト型サービスを作成するのでなければ、インターネット インフォメーション サービス (IIS) でサービスをホストできます。</span><span class="sxs-lookup"><span data-stu-id="2bb76-104">If you are not creating a self-hosted service, you can host your service on Internet Information Services (IIS).</span></span> <span data-ttu-id="2bb76-105">詳細については、「 [HTTP トランスポートセキュリティ](http-transport-security.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2bb76-105">For more information, see [HTTP Transport Security](http-transport-security.md).</span></span>  
  
 <span data-ttu-id="2bb76-106">ポートを構成する場合に使用するツールは、コンピューターで実行されているオペレーティング システムによって異なります。</span><span class="sxs-lookup"><span data-stu-id="2bb76-106">To configure a port, the tool you use depends on the operating system that is running on your machine.</span></span>  
  
 <span data-ttu-id="2bb76-107">Windows Server 2003 を実行している場合は、Httpcfg.exe ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="2bb76-107">If you are running Windows Server 2003, use the HttpCfg.exe tool.</span></span> <span data-ttu-id="2bb76-108">Windows Server 2003 では、このツールはインストールされています。</span><span class="sxs-lookup"><span data-stu-id="2bb76-108">On Windows Server 2003, this tool is installed.</span></span> <span data-ttu-id="2bb76-109">詳細については、「 [httpcfg.exe の概要](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2bb76-109">For more information, see [Httpcfg Overview](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)).</span></span> <span data-ttu-id="2bb76-110">[Windows サポートツールのドキュメント](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10))では、httpcfg.exe ツールの構文について説明しています。</span><span class="sxs-lookup"><span data-stu-id="2bb76-110">The [Windows Support Tools documentation](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) explains the syntax for the Httpcfg.exe tool.</span></span>  
  
 <span data-ttu-id="2bb76-111">Windows Vista を実行している場合は、既にインストールされている Netsh.exe ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="2bb76-111">If you are running Windows Vista, use the Netsh.exe tool that is already installed.</span></span>
  
> [!NOTE]
> <span data-ttu-id="2bb76-112">コンピューターに保存されている証明書を変更するには、管理者特権が必要です。</span><span class="sxs-lookup"><span data-stu-id="2bb76-112">Modifying certificates stored on the computer requires administrative privileges.</span></span>  
  
## <a name="determine-how-ports-are-configured"></a><span data-ttu-id="2bb76-113">ポートの構成方法を決定する</span><span class="sxs-lookup"><span data-stu-id="2bb76-113">Determine how ports are configured</span></span>  
  
1. <span data-ttu-id="2bb76-114">Windows Server 2003 または Windows XP では、Httpcfg.exe ツールを使用して、次の例に示すように、**クエリ**と**ssl**スイッチを使用して現在のポート構成を表示します。</span><span class="sxs-lookup"><span data-stu-id="2bb76-114">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool to view the current port configuration, using the **query** and **ssl** switches, as shown in the following example.</span></span>  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. <span data-ttu-id="2bb76-115">Windows Vista では、次の例に示すように、Netsh.exe ツールを使用して現在のポート構成を表示します。</span><span class="sxs-lookup"><span data-stu-id="2bb76-115">In Windows Vista, use the Netsh.exe tool to view the current port configuration, as shown in the following example.</span></span>  
  
    ```console  
    netsh http show sslcert  
    ```  
  
## <a name="get-a-certificates-thumbprint"></a><span data-ttu-id="2bb76-116">証明書の拇印を取得する</span><span class="sxs-lookup"><span data-stu-id="2bb76-116">Get a certificate's thumbprint</span></span>  
  
1. <span data-ttu-id="2bb76-117">証明書 MMC スナップインを使用して、クライアント認証を目的として含む X.509 証明書を検索します。</span><span class="sxs-lookup"><span data-stu-id="2bb76-117">Use the Certificates MMC snap-in to find an X.509 certificate that has an intended purpose of client authentication.</span></span> <span data-ttu-id="2bb76-118">詳細については、「 [方法: MMC スナップインを使用して証明書を参照する](how-to-view-certificates-with-the-mmc-snap-in.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2bb76-118">For more information, see [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2. <span data-ttu-id="2bb76-119">証明書の拇印にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="2bb76-119">Access the certificate's thumbprint.</span></span> <span data-ttu-id="2bb76-120">詳細については、「[方法: 証明書のサムプリントを取得する](how-to-retrieve-the-thumbprint-of-a-certificate.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2bb76-120">For more information, see [How to: Retrieve the Thumbprint of a Certificate](how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
3. <span data-ttu-id="2bb76-121">証明書のサムプリントを、メモ帳などのテキスト エディターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="2bb76-121">Copy the thumbprint of the certificate into a text editor, such as Notepad.</span></span>  
  
4. <span data-ttu-id="2bb76-122">16 進文字の間にある空白をすべて削除します。</span><span class="sxs-lookup"><span data-stu-id="2bb76-122">Remove all spaces between the hexadecimal characters.</span></span> <span data-ttu-id="2bb76-123">たとえばエディターの "すべて置換" 機能を使用して、空白を空文字列に置き換えるとよいでしょう。</span><span class="sxs-lookup"><span data-stu-id="2bb76-123">One way to accomplish this is to use the text editor's find-and-replace feature and replace each space with a null character.</span></span>  
  
## <a name="bind-an-ssl-certificate-to-a-port-number"></a><span data-ttu-id="2bb76-124">SSL 証明書をポート番号にバインドする</span><span class="sxs-lookup"><span data-stu-id="2bb76-124">Bind an SSL certificate to a port number</span></span>  
  
1. <span data-ttu-id="2bb76-125">Windows Server 2003 または Windows XP では、Secure Sockets Layer (SSL) ストアの "設定" モードで Httpcfg.exe ツールを使用して、証明書をポート番号にバインドします。</span><span class="sxs-lookup"><span data-stu-id="2bb76-125">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool in "set" mode on the Secure Sockets Layer (SSL) store to bind the certificate to a port number.</span></span> <span data-ttu-id="2bb76-126">このツールは、次のように、拇印を使用して証明書を識別します。</span><span class="sxs-lookup"><span data-stu-id="2bb76-126">The tool uses the thumbprint to identify the certificate, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - <span data-ttu-id="2bb76-127">**-I**スイッチの構文はです。は、 `IP` `port` コンピューターのポート8012に証明書を設定するようにツールに指示します。</span><span class="sxs-lookup"><span data-stu-id="2bb76-127">The **-i** switch has the syntax of `IP`:`port` and instructs the tool to set the certificate to port 8012 of the computer.</span></span> <span data-ttu-id="2bb76-128">"0.0.0.0" の部分は、必要に応じて、コンピューターの実際の IP アドレスに置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="2bb76-128">Optionally, the four zeroes that precede the number can also be replaced by the actual IP address of the computer.</span></span>  
  
    - <span data-ttu-id="2bb76-129">**-H**スイッチは、証明書の拇印を指定します。</span><span class="sxs-lookup"><span data-stu-id="2bb76-129">The **-h** switch specifies the thumbprint of the certificate.</span></span>  
  
2. <span data-ttu-id="2bb76-130">Windows Vista では、次の例に示すように、Netsh.exe ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="2bb76-130">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}
    ```  
  
    - <span data-ttu-id="2bb76-131">**Certhash**パラメーターは、証明書の拇印を指定します。</span><span class="sxs-lookup"><span data-stu-id="2bb76-131">The **certhash** parameter specifies the thumbprint of the certificate.</span></span>  
  
    - <span data-ttu-id="2bb76-132">**Ipport**パラメーターは、IP アドレスとポートを指定し、httpcfg.exe ツールの **-i**スイッチと同様に機能します。</span><span class="sxs-lookup"><span data-stu-id="2bb76-132">The **ipport** parameter specifies the IP address and port, and functions just like the **-i** switch of the Httpcfg.exe tool described.</span></span>  
  
    - <span data-ttu-id="2bb76-133">**Appid**パラメーターは、所有しているアプリケーションを識別するために使用できる GUID です。</span><span class="sxs-lookup"><span data-stu-id="2bb76-133">The **appid** parameter is a GUID that can be used to identify the owning application.</span></span>  
  
## <a name="bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a><span data-ttu-id="2bb76-134">SSL 証明書をポート番号にバインドし、クライアント証明書をサポートする</span><span class="sxs-lookup"><span data-stu-id="2bb76-134">Bind an SSL certificate to a port number and support client certificates</span></span>  
  
1. <span data-ttu-id="2bb76-135">Windows Server 2003 または Windows XP で、トランスポート層で x.509 証明書を使用して認証を行うクライアントをサポートするには、前の手順に従いますが、次の例に示すように、Httpcfg.exe に追加のコマンドラインパラメーターを渡します。</span><span class="sxs-lookup"><span data-stu-id="2bb76-135">In Windows Server 2003 or Windows XP, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure but pass an additional command-line parameter to HttpCfg.exe, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     <span data-ttu-id="2bb76-136">**-F**スイッチには、の構文があり `n` ます。 n は 1 ~ 7 の数値です。</span><span class="sxs-lookup"><span data-stu-id="2bb76-136">The **-f** switch has the syntax of `n` where n is a number between 1 and 7.</span></span> <span data-ttu-id="2bb76-137">前の例のように 2 を指定すると、クライアントはトランスポート層で認証することになります。</span><span class="sxs-lookup"><span data-stu-id="2bb76-137">A value of 2, as shown in the preceding example, enables client certificates at the transport layer.</span></span> <span data-ttu-id="2bb76-138">値として 3 を指定すると、クライアント証明書が有効になり、それらの証明書が Windows アカウントに対応付けられます。</span><span class="sxs-lookup"><span data-stu-id="2bb76-138">A value of 3 enables client certificates and maps those certificates to a Windows account.</span></span> <span data-ttu-id="2bb76-139">他の値については、HttpCfg.exe のヘルプ機能を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2bb76-139">See HttpCfg.exe Help for the behavior of other values.</span></span>  
  
2. <span data-ttu-id="2bb76-140">Windows Vista で、トランスポート層で x.509 証明書を使用して認証を行うクライアントをサポートするには、次の例に示すように、上記の手順に従いますが、追加のパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="2bb76-140">In Windows Vista, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure, but with an additional parameter, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
## <a name="delete-an-ssl-certificate-from-a-port-number"></a><span data-ttu-id="2bb76-141">ポート番号から SSL 証明書を削除する</span><span class="sxs-lookup"><span data-stu-id="2bb76-141">Delete an SSL certificate from a port number</span></span>  
  
1. <span data-ttu-id="2bb76-142">HttpCfg.exe または Netsh.exe ツールを使用して、コンピューター上のすべてのバインディングのポートと拇印を確認します。</span><span class="sxs-lookup"><span data-stu-id="2bb76-142">Use the HttpCfg.exe or Netsh.exe tool to see the ports and thumbprints of all bindings on the computer.</span></span> <span data-ttu-id="2bb76-143">情報をディスクに出力するには、次の例に示すように、リダイレクト文字 ">" を使用します。</span><span class="sxs-lookup"><span data-stu-id="2bb76-143">To print the information to disk, use the redirection character ">", as shown in the following example.</span></span>  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. <span data-ttu-id="2bb76-144">Windows Server 2003 または Windows XP では、Httpcfg.exe ツールと**delete**および**ssl**キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="2bb76-144">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool with the **delete** and **ssl** keywords.</span></span> <span data-ttu-id="2bb76-145">**-I**スイッチを使用して、 `IP` : `port` number を指定し、 **-h**スイッチを使用してサムプリントを指定します。</span><span class="sxs-lookup"><span data-stu-id="2bb76-145">Use the **-i** switch to specify the `IP`:`port` number, and the **-h** switch to specify the thumbprint.</span></span>  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. <span data-ttu-id="2bb76-146">Windows Vista では、次の例に示すように、Netsh.exe ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="2bb76-146">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a><span data-ttu-id="2bb76-147">例</span><span class="sxs-lookup"><span data-stu-id="2bb76-147">Example</span></span>  

 <span data-ttu-id="2bb76-148">次のコードは、トランスポート セキュリティを設定した <xref:System.ServiceModel.WSHttpBinding> クラスを使用して、自己ホスト型サービスを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2bb76-148">The following code shows how to create a self-hosted service using the <xref:System.ServiceModel.WSHttpBinding> class set to transport security.</span></span> <span data-ttu-id="2bb76-149">アプリケーションを作成する際、アドレス中にポート番号を指定してください。</span><span class="sxs-lookup"><span data-stu-id="2bb76-149">When creating an application, specify the port number in the address.</span></span>  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="2bb76-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="2bb76-150">See also</span></span>

- [<span data-ttu-id="2bb76-151">HTTP トランスポート セキュリティ</span><span class="sxs-lookup"><span data-stu-id="2bb76-151">HTTP Transport Security</span></span>](http-transport-security.md)
