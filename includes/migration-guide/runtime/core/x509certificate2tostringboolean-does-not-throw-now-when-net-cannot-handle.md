---
ms.openlocfilehash: 0dfc87201b9b31cd9d936f2c965c7d0ca0140cab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858581"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a><span data-ttu-id="5ff63-101">.NET で証明書を処理できないときに、X509Certificate2.ToString(Boolean) がスローしなくなった</span><span class="sxs-lookup"><span data-stu-id="5ff63-101">X509Certificate2.ToString(Boolean) does not throw now when .NET cannot handle the certificate</span></span>

|   |   |
|---|---|
|<span data-ttu-id="5ff63-102">説明</span><span class="sxs-lookup"><span data-stu-id="5ff63-102">Details</span></span>|<span data-ttu-id="5ff63-103">.NET Framework 4.5.2 およびそれより前のバージョンでは、このメソッドは、verbose パラメーターとして <code>true</code> が渡され、.NET Framework ではサポートされない証明書がインストールされていた場合、スローしました。</span><span class="sxs-lookup"><span data-stu-id="5ff63-103">In .NET Framework 4.5.2 and earlier versions, this method would throw if <code>true</code> was passed for the verbose parameter and there were certificates installed that weren't supported by the .NET Framework.</span></span> <span data-ttu-id="5ff63-104">現在は、メソッドは成功し、証明書のアクセス不能部分を省いた有効な文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="5ff63-104">Now, the method will succeed and return a valid string that omits the inaccessible portions of the certificate.</span></span>|
|<span data-ttu-id="5ff63-105">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="5ff63-105">Suggestion</span></span>|<span data-ttu-id="5ff63-106"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> に依存しているコードは、以前は API がスローしていたような場合には、返される文字列から一部の証明書データ (公開鍵、秘密鍵、拡張子など) が除外されることを予期するように更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ff63-106">Any code depending on <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> should be updated to expect that the returned string may exclude some certificate data (such as public key, private key, and extensions) in some cases in which the API would have previously thrown.</span></span>|
|<span data-ttu-id="5ff63-107">スコープ</span><span class="sxs-lookup"><span data-stu-id="5ff63-107">Scope</span></span>|<span data-ttu-id="5ff63-108">エッジ</span><span class="sxs-lookup"><span data-stu-id="5ff63-108">Edge</span></span>|
|<span data-ttu-id="5ff63-109">バージョン</span><span class="sxs-lookup"><span data-stu-id="5ff63-109">Version</span></span>|<span data-ttu-id="5ff63-110">4.6</span><span class="sxs-lookup"><span data-stu-id="5ff63-110">4.6</span></span>|
|<span data-ttu-id="5ff63-111">[種類]</span><span class="sxs-lookup"><span data-stu-id="5ff63-111">Type</span></span>|<span data-ttu-id="5ff63-112">ランタイム</span><span class="sxs-lookup"><span data-stu-id="5ff63-112">Runtime</span></span>|
|<span data-ttu-id="5ff63-113">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="5ff63-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|
