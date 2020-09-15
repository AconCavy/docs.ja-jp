---
ms.openlocfilehash: 0e949cbdeda99dd7b94e919b903a21171a57f527
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614732"
---
### <a name="wcf-binding-with-the-transportwithmessagecredential-security-mode"></a><span data-ttu-id="a9bae-101">TransportWithMessageCredential セキュリティ モードを使用する WCF バインド</span><span class="sxs-lookup"><span data-stu-id="a9bae-101">WCF binding with the TransportWithMessageCredential security mode</span></span>

#### <a name="details"></a><span data-ttu-id="a9bae-102">説明</span><span class="sxs-lookup"><span data-stu-id="a9bae-102">Details</span></span>

<span data-ttu-id="a9bae-103">.NET Framework 4.6.1 より、TransportWithMessageCredential セキュリティ モードを使用する WCF バインドで署名のない非対称セキュリティ キーの &quot;to&quot; ヘッダーを含むメッセージを取得するように設定できるようになりました。既定では、署名のない &quot;to&quot; ヘッダーは .NET Framework 4.6.1 でも引き続き拒否されます。</span><span class="sxs-lookup"><span data-stu-id="a9bae-103">Beginning in the .NET Framework 4.6.1, WCF binding that uses the TransportWithMessageCredential security mode can be set up to receive messages with unsigned &quot;to&quot; headers for asymmetric security keys.By default, unsigned &quot;to&quot; headers will continue to be rejected in .NET Framework 4.6.1.</span></span> <span data-ttu-id="a9bae-104">これは、アプリケーションが Switch.System.ServiceModel.AllowUnsignedToHeader 構成スイッチを使用するこの新しい動作モードをオプトインした場合にのみ許可されます。</span><span class="sxs-lookup"><span data-stu-id="a9bae-104">They will only be accepted if an application opts into this new mode of operation using the Switch.System.ServiceModel.AllowUnsignedToHeader configuration switch.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a9bae-105">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="a9bae-105">Suggestion</span></span>

<span data-ttu-id="a9bae-106">これはオプトイン機能であるため、既存のアプリの動作に影響はないはずです。</span><span class="sxs-lookup"><span data-stu-id="a9bae-106">Because this is an opt-in feature, it should not affect the behavior of existing apps.</span></span><br/><span data-ttu-id="a9bae-107">新しい動作を使用するかどうかを制御するには、次の構成設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="a9bae-107">To control whether the new behavior is used or not, use the following configuration setting:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.ServiceModel.AllowUnsignedToHeader=true" />
</runtime>
```

| <span data-ttu-id="a9bae-108">名前</span><span class="sxs-lookup"><span data-stu-id="a9bae-108">Name</span></span>    | <span data-ttu-id="a9bae-109">[値]</span><span class="sxs-lookup"><span data-stu-id="a9bae-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a9bae-110">スコープ</span><span class="sxs-lookup"><span data-stu-id="a9bae-110">Scope</span></span>   | <span data-ttu-id="a9bae-111">透明</span><span class="sxs-lookup"><span data-stu-id="a9bae-111">Transparent</span></span> |
| <span data-ttu-id="a9bae-112">バージョン</span><span class="sxs-lookup"><span data-stu-id="a9bae-112">Version</span></span> | <span data-ttu-id="a9bae-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="a9bae-113">4.6.1</span></span>       |
| <span data-ttu-id="a9bae-114">種類</span><span class="sxs-lookup"><span data-stu-id="a9bae-114">Type</span></span>    | <span data-ttu-id="a9bae-115">再ターゲット中</span><span class="sxs-lookup"><span data-stu-id="a9bae-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="a9bae-116">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="a9bae-116">Affected APIs</span></span>

- <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpsSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
