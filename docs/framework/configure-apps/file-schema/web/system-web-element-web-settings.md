---
title: <system.web> 要素 (Web 設定)
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
ms.openlocfilehash: b9a43c5f5141e364ab9aac1cfdff577a8fb8a161
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486676"
---
# <a name="systemweb-element-web-settings"></a>\<system.web > 要素 (Web 設定)
ASP.NET ホスト レイヤーがプロセス全体の動作を管理する方法についてを説明します。  
  
 \<configuration>  
\<system.web > 要素 (Web 設定)  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<applicationPool>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|Aspnet.config ファイルには、IIS アプリケーション プールの構成設定を指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルでは、ルート要素を指定します。|  
  
## <a name="remarks"></a>Remarks  
 `system.web`要素とその子`applicationPool`要素は、.NET Framework 3.5 SP1 の時点で、.NET Framework に追加されました。 統合モードで IIS 7.0 またはそれ以降のバージョンを実行するときにこの要素の組み合わせでは、ASP.NET はスレッドを管理する方法と、ASP.NET が IIS アプリケーション プールでホストされている場合に要求をキューにする方法を構成することができます。 クラシックまたは ISAPI のモードで IIS 7.0 またはそれ以降のバージョンを実行する場合は、これらの設定は無視されます。  
  
## <a name="example"></a>例  
 次の例では、ASP.NET が IIS アプリケーション プールでホストされている場合は、aspnet.config ファイルに ASP.NET プロセス全体の動作を構成する方法を示します。 この例では統合で IIS が実行されているモードと、アプリケーションが、.NET Framework 3.5 SP1 またはそれ以降のバージョンを使用しています。 この動作は、.NET Framework、.NET Framework 3.5 SP1 より前のバージョンでは発生しません。 値の例では、既定値です。  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool   
        maxConcurrentRequestsPerCPU="5000"   
        maxConcurrentThreadsPerCPU="0"   
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a>要素情報  
  
|||  
|-|-|  
|名前空間||  
|スキーマ名||  
|検証ファイル||  
|空にすることができます。||  
  
## <a name="see-also"></a>関連項目

- [\<applicationPool> 要素 (Web 設定)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)
