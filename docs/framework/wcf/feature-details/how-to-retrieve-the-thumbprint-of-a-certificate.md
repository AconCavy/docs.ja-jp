---
title: '方法: 証明書のサムプリントを取得する'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], retrieving thumbprint
ms.assetid: da3101aa-78cd-4c34-9652-d1f24777eeab
ms.openlocfilehash: f59fad86287e89b0a573a6e3ee8420f384b0bc3b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601206"
---
# <a name="how-to-retrieve-the-thumbprint-of-a-certificate"></a><span data-ttu-id="e026c-102">方法: 証明書のサムプリントを取得する</span><span class="sxs-lookup"><span data-stu-id="e026c-102">How to: Retrieve the Thumbprint of a Certificate</span></span>
<span data-ttu-id="e026c-103">認証に x.509 証明書を使用する Windows Communication Foundation (WCF) アプリケーションを作成する場合、多くの場合、証明書で検出されたクレームを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e026c-103">When writing a Windows Communication Foundation (WCF) application that uses an X.509 certificate for authentication, it is often necessary to specify claims found in the certificate.</span></span> <span data-ttu-id="e026c-104">たとえば、 <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> メソッドで <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> 列挙体を使用する場合は、拇印クレームを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e026c-104">For example, you must supply a thumbprint claim when using the <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> enumeration in the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method.</span></span> <span data-ttu-id="e026c-105">クレーム値を検索するには 2 つの手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e026c-105">Finding the claim value requires two steps.</span></span> <span data-ttu-id="e026c-106">まず、証明書用の Microsoft 管理コンソール (MMC) スナップインを開きます</span><span class="sxs-lookup"><span data-stu-id="e026c-106">First, open the Microsoft Management Console (MMC) snap-in for certificates.</span></span> <span data-ttu-id="e026c-107">(「[方法: MMC スナップインを使用して証明書を表示する](how-to-view-certificates-with-the-mmc-snap-in.md)」を参照してください)。次に、ここで説明するように、適切な証明書を検索し、その拇印 (またはその他の要求値) をコピーします。</span><span class="sxs-lookup"><span data-stu-id="e026c-107">(See [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md).) Second, as described here, find an appropriate certificate and copy its thumbprint (or other claim values).</span></span>  
  
 <span data-ttu-id="e026c-108">サービス認証で証明書を使用する場合は、 **[Issued To]** 列 (コンソールの 1 番目の列) の値に注意することが重要です。</span><span class="sxs-lookup"><span data-stu-id="e026c-108">If you are using a certificate for service authentication, it is important to note the value of the **Issued To** column (the first column in the console).</span></span> <span data-ttu-id="e026c-109">トランスポート セキュリティとして SSL (Secure Sockets Layer) を使用する場合、実行される最初のチェックの 1 つで、サービスのベース アドレス URI (Uniform Resource Identifier) が **[Issued To]** の値と比較されます。</span><span class="sxs-lookup"><span data-stu-id="e026c-109">When using Secure Sockets Layer (SSL) as a transport security, one of the first checks done is to compare the base address Uniform Resource Identifier (URI) of a service to the **Issued To** value.</span></span> <span data-ttu-id="e026c-110">値は一致する必要があります。一致しない場合は、認証が停止します。</span><span class="sxs-lookup"><span data-stu-id="e026c-110">The values must match or the authentication process is halted.</span></span>  
  
 <span data-ttu-id="e026c-111">Powershell の新しい-SelfSignedCertificate コマンドレットを使用して、開発中にのみ使用する一時的な証明書を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="e026c-111">You can also use the Powershell New-SelfSignedCertificate cmdlet to create temporary certificates for use only during development.</span></span> <span data-ttu-id="e026c-112">ただし、既定では、このような証明書は証明機関によって発行されず、運用目的では使用できません。</span><span class="sxs-lookup"><span data-stu-id="e026c-112">By default, however, such a certificate is not issued by a certification authority and is unusable for production purposes.</span></span> <span data-ttu-id="e026c-113">詳細については、「[方法: 開発時に使用する一時的な証明書を作成する](how-to-create-temporary-certificates-for-use-during-development.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e026c-113">For more information, see [How to: Create Temporary Certificates for Use During Development](how-to-create-temporary-certificates-for-use-during-development.md).</span></span>  
  
### <a name="to-retrieve-a-certificates-thumbprint"></a><span data-ttu-id="e026c-114">証明書の拇印を取得するには</span><span class="sxs-lookup"><span data-stu-id="e026c-114">To retrieve a certificate's thumbprint</span></span>  
  
1. <span data-ttu-id="e026c-115">証明書用の Microsoft 管理コンソール (MMC) スナップインを開きます</span><span class="sxs-lookup"><span data-stu-id="e026c-115">Open the Microsoft Management Console (MMC) snap-in for certificates.</span></span> <span data-ttu-id="e026c-116">(「 [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="e026c-116">(See [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md).)</span></span>  
  
2. <span data-ttu-id="e026c-117">**[Console Root]** ウィンドウの左ペインで、 **[Certificates (Local Computer)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e026c-117">In the **Console Root** window's left pane, click **Certificates (Local Computer)**.</span></span>  
  
3. <span data-ttu-id="e026c-118">**[Personal]** フォルダーをクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="e026c-118">Click the **Personal** folder to expand it.</span></span>  
  
4. <span data-ttu-id="e026c-119">**[Certificates]** フォルダーをクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="e026c-119">Click the **Certificates** folder to expand it.</span></span>  
  
5. <span data-ttu-id="e026c-120">証明書リストの **[Intended Purposes]** 見出しを確認します。</span><span class="sxs-lookup"><span data-stu-id="e026c-120">In the list of certificates, note the **Intended Purposes** heading.</span></span> <span data-ttu-id="e026c-121">目的として **[Client Authentication]** が表示されている証明書を検索します。</span><span class="sxs-lookup"><span data-stu-id="e026c-121">Find a certificate that lists **Client Authentication** as an intended purpose.</span></span>  
  
6. <span data-ttu-id="e026c-122">証明書をダブルクリックする</span><span class="sxs-lookup"><span data-stu-id="e026c-122">Double-click the certificate.</span></span>  
  
7. <span data-ttu-id="e026c-123">**[Certificate]** ダイアログ ボックスの **[Details]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e026c-123">In the **Certificate** dialog box, click the **Details** tab.</span></span>  
  
8. <span data-ttu-id="e026c-124">フィールド リストをスクロールし、 **[Thumbprint]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e026c-124">Scroll through the list of fields and click **Thumbprint**.</span></span>  
  
9. <span data-ttu-id="e026c-125">ボックスから 16 進文字をコピーします。</span><span class="sxs-lookup"><span data-stu-id="e026c-125">Copy the hexadecimal characters from the box.</span></span> <span data-ttu-id="e026c-126">この拇印を `X509FindType`のコードで使用する場合は、16 進文字の間のスペースを削除します。</span><span class="sxs-lookup"><span data-stu-id="e026c-126">If this thumbprint is used in code for the `X509FindType`, remove the spaces between the hexadecimal numbers.</span></span> <span data-ttu-id="e026c-127">たとえば、拇印 "a9 09 50 2d d8 2a e4 14 33 e6 f8 38 86 b0 0d 42 77 a3 2a 7b" は、コード内で "a909502dd82ae41433e6f83886b00d4277a32a7b" として指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e026c-127">For example, the thumbprint "a9 09 50 2d d8 2a e4 14 33 e6 f8 38 86 b0 0d 42 77 a3 2a 7b" should be specified as "a909502dd82ae41433e6f83886b00d4277a32a7b" in code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e026c-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="e026c-128">See also</span></span>

- <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>
- [<span data-ttu-id="e026c-129">方法: SSL 証明書を使用してポートを構成する</span><span class="sxs-lookup"><span data-stu-id="e026c-129">How to: Configure a Port with an SSL Certificate</span></span>](how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="e026c-130">方法: MMC スナップインを使用して証明書を参照する</span><span class="sxs-lookup"><span data-stu-id="e026c-130">How to: View Certificates with the MMC Snap-in</span></span>](how-to-view-certificates-with-the-mmc-snap-in.md)
- [<span data-ttu-id="e026c-131">方法: 開発中に使用する一時的な証明書を作成する</span><span class="sxs-lookup"><span data-stu-id="e026c-131">How to: Create Temporary Certificates for Use During Development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
