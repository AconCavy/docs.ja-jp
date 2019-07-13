---
title: <gcServer> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5df7ab070cc0a40f4e2f3d0545c5bc40ccb07f4d
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378036"
---
# <a name="gcserver-element"></a>\<gcServer > 要素
共通言語ランタイムがサーバーのガベージ コレクションを実行するかどうかを指定します。  
  
 \<configuration>  
\<runtime>  
\<gcServer>  
  
## <a name="syntax"></a>構文  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> ランタイムがサーバーのガベージ コレクションを実行するかどうかを指定します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`false`|サーバーのガベージ コレクションを実行しません。 既定値です。|  
|`true`|サーバーのガベージ コレクションを実行します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>Remarks  
 共通言語ランタイム (CLR) は、2 種類のガベージ コレクションをサポートしています。1 つはワークステーション ガベージ コレクションで、すべてのシステムで使用できるものです。もう 1 つはサーバー ガベージ コレクションで、マルチプロセッサ システムで使用できるものです。 `<gcServer>` 要素を使用して、CLR によって実行されるガベージ コレクションの種類を制御します。 <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> プロパティを使用して、サーバー ガベージ コレクションが有効かどうかを決定します。  
  
 シングル プロセッサ コンピューターの場合、既定のワークステーション ガベージ コレクションが催促のオプションです。 2 つのプロセッサを搭載するコンピューターで、ワークステーションかサーバーのいずれかを使用できます。 3 つ以上のプロセッサでは、サーバー ガベージ コレクションが最速のオプションです。  
  
 この要素は、アプリケーション構成ファイルでのみ使用できます。要素がマシン構成ファイルにある場合には無視されます。  
  
> [!NOTE]
>  .NET Framework 4 以前のバージョンでは、サーバー ガベージ コレクションを有効にすると同時実行ガベージ コレクションが使用できません。 以降、.NET Framework 4.5 では、サーバーのガベージ コレクションは、同時実行します。 非同時実行サーバー ガベージ コレクションを使用する設定、`<gcServer>`要素`true`と[ \<gcConcurrent > 要素](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)に`false`します。  
  
## <a name="example"></a>例  
 サーバー ガベージ コレクションを有効にする方法を次の例に示します。  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [同時実行ガベージ コレクションを無効にするには](gcconcurrent-element.md#to-disable-background-garbage-collection)
