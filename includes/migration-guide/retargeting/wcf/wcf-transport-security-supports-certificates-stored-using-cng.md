---
ms.openlocfilehash: 5c09bee92f679cd7e7a95cd23d5ce0ca9b57170c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614744"
---
### <a name="wcf-transport-security-supports-certificates-stored-using-cng"></a><span data-ttu-id="9a074-101">WCF トランスポート セキュリティで CNG を使用して格納される証明書をサポート</span><span class="sxs-lookup"><span data-stu-id="9a074-101">WCF transport security supports certificates stored using CNG</span></span>

#### <a name="details"></a><span data-ttu-id="9a074-102">説明</span><span class="sxs-lookup"><span data-stu-id="9a074-102">Details</span></span>

<span data-ttu-id="9a074-103">.NET Framework 4.6.2 を対象とするアプリ以降では、WCF トランスポート セキュリティでは、Windows 暗号化ライブラリ (CNG) を使用して格納される証明書がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="9a074-103">Starting with apps that target the .NET Framework 4.6.2, WCF transport security supports certificates stored using the Windows Cryptography Library (CNG).</span></span> <span data-ttu-id="9a074-104">このサポートは、指数の長さが 32 ビット以下の公開キーを持つ証明書に限定されます。</span><span class="sxs-lookup"><span data-stu-id="9a074-104">This support is limited to certificates with a public key that has an exponent no more than 32 bits in length.</span></span> <span data-ttu-id="9a074-105">アプリケーションが対象 .NET Framework 4.6.2、ときにこの機能は既定でオンです。 .NET Framework の以前のバージョンで X509 を使用しようとすると、証明書を CSG のキー記憶域プロバイダーが例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="9a074-105">When an application targets the .NET Framework 4.6.2, this feature is on by default.In earlier versions of the .NET Framework, the attempt to use X509 certificates with a CSG key storage provider throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="9a074-106">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="9a074-106">Suggestion</span></span>

<span data-ttu-id="9a074-107">.NET Framework 4.6.1 以前を対象とするものの、.NET Framework 4.6.2 で実行されているアプリの場合、app.config または web.config ファイルの `<runtime>` セクションに次の行を追加することで、CNG 証明書のサポートを有効にできます。</span><span class="sxs-lookup"><span data-stu-id="9a074-107">Apps that target the .NET Framework 4.6.1 and earlier but are running on the .NET Framework 4.6.2 can enable support for CNG certificates by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableCngCertificates=false" />
</runtime>
```

<span data-ttu-id="9a074-108">次のコードを使用してプログラムで行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="9a074-108">This can also be done programmatically with the following code:</span></span>

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificate";

AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

<span data-ttu-id="9a074-109">この変更のため、CNG 証明書の失敗で、セキュリティで保護された通信を開始する試行に依存する例外処理コードは、実行されなくなることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9a074-109">Note that, because of this change, any exception handling code that depends on the attempt to initiate secure communication with a CNG certificate to fail will no longer execute.</span></span>

| <span data-ttu-id="9a074-110">名前</span><span class="sxs-lookup"><span data-stu-id="9a074-110">Name</span></span>    | <span data-ttu-id="9a074-111">値</span><span class="sxs-lookup"><span data-stu-id="9a074-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="9a074-112">スコープ</span><span class="sxs-lookup"><span data-stu-id="9a074-112">Scope</span></span>   | <span data-ttu-id="9a074-113">マイナー</span><span class="sxs-lookup"><span data-stu-id="9a074-113">Minor</span></span>       |
| <span data-ttu-id="9a074-114">バージョン</span><span class="sxs-lookup"><span data-stu-id="9a074-114">Version</span></span> | <span data-ttu-id="9a074-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="9a074-115">4.6.2</span></span>       |
| <span data-ttu-id="9a074-116">種類</span><span class="sxs-lookup"><span data-stu-id="9a074-116">Type</span></span>    | <span data-ttu-id="9a074-117">再ターゲット中</span><span class="sxs-lookup"><span data-stu-id="9a074-117">Retargeting</span></span> |
