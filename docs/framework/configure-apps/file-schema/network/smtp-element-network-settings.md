---
title: <smtp> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
ms.openlocfilehash: 625c3cb82a8659c742b540724e5cf31be65a705e
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089094"
---
# <a name="smtp-element-network-settings"></a><span data-ttu-id="7b557-102">\<smtp > 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="7b557-102">\<smtp> Element (Network Settings)</span></span>
<span data-ttu-id="7b557-103">電子メールの送信に使用する配信形式、配信方法、差出人アドレスを構成します。</span><span class="sxs-lookup"><span data-stu-id="7b557-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
<span data-ttu-id="7b557-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7b557-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7b557-105">&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="7b557-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="7b557-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<mailSettings >** ](mailsettings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="7b557-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span></span>\
<span data-ttu-id="7b557-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**smtp**\<</span><span class="sxs-lookup"><span data-stu-id="7b557-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<smtp>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="7b557-108">構文</span><span class="sxs-lookup"><span data-stu-id="7b557-108">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b557-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="7b557-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7b557-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b557-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b557-111">属性</span><span class="sxs-lookup"><span data-stu-id="7b557-111">Attributes</span></span>  
  
|<span data-ttu-id="7b557-112">属性</span><span class="sxs-lookup"><span data-stu-id="7b557-112">Attribute</span></span>|<span data-ttu-id="7b557-113">説明</span><span class="sxs-lookup"><span data-stu-id="7b557-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="7b557-114">送信電子メールの配信形式を指定します。</span><span class="sxs-lookup"><span data-stu-id="7b557-114">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="7b557-115">指定できる値は SevenBit および International です。</span><span class="sxs-lookup"><span data-stu-id="7b557-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="7b557-116">電子メールの配信方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="7b557-116">Specifies the delivery method for emails.</span></span> <span data-ttu-id="7b557-117">使用可能な値は、Network、ピックアップディレクトリ Fromiis、および指定された指定された Updirectory です。</span><span class="sxs-lookup"><span data-stu-id="7b557-117">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="7b557-118">送信メールの差出人アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="7b557-118">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7b557-119">子要素</span><span class="sxs-lookup"><span data-stu-id="7b557-119">Child Elements</span></span>  
  
|<span data-ttu-id="7b557-120">属性</span><span class="sxs-lookup"><span data-stu-id="7b557-120">Attribute</span></span>|<span data-ttu-id="7b557-121">説明</span><span class="sxs-lookup"><span data-stu-id="7b557-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="7b557-122">SMTP (Simple Mail Transport Protocol) サーバー用のローカル ディレクトリを設定します。</span><span class="sxs-lookup"><span data-stu-id="7b557-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="7b557-123">外部 SMTP サーバー用のネットワーク オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="7b557-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7b557-124">親要素</span><span class="sxs-lookup"><span data-stu-id="7b557-124">Parent Elements</span></span>  
  
|<span data-ttu-id="7b557-125">**要素**</span><span class="sxs-lookup"><span data-stu-id="7b557-125">**Element**</span></span>|<span data-ttu-id="7b557-126">**説明**</span><span class="sxs-lookup"><span data-stu-id="7b557-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="7b557-127">\<mailSettings> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="7b557-127">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="7b557-128">電子メールの送信オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="7b557-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7b557-129">例</span><span class="sxs-lookup"><span data-stu-id="7b557-129">Example</span></span>  
 <span data-ttu-id="7b557-130">次の例では、既定のネットワーク資格情報を使用して電子メールを送信するための適切な SMTP パラメーターを指定しています。</span><span class="sxs-lookup"><span data-stu-id="7b557-130">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network" deliveryFormat="SevenBit"  from="ben@contoso.com">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7b557-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b557-131">See also</span></span>

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="7b557-132">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="7b557-132">Network Settings Schema</span></span>](index.md)
