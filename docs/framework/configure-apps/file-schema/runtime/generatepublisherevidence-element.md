---
title: <generatePublisherEvidence> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: 506e7873fab8e41fce121587c22d85600a8b1760
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158774"
---
# <a name="generatepublisherevidence-element"></a>\<generatePublisherEvidence> 要素

ランタイムが <xref:System.Security.Policy.Publisher> コードアクセスセキュリティ (CAS) の証拠を作成するかどうかを指定します。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<generatePublisherEvidence
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> ランタイムが証拠を作成するかどうかを指定し <xref:System.Security.Policy.Publisher> ます。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|[説明]|  
|-----------|-----------------|  
|`false`|は <xref:System.Security.Policy.Publisher> 証拠を作成しません。|  
|`true`|<xref:System.Security.Policy.Publisher>証拠を作成します。 これは既定値です。|  
  
### <a name="child-elements"></a>子要素  

 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## <a name="remarks"></a>解説  
  
> [!NOTE]
> .NET Framework 4 以降では、この要素はアセンブリの読み込み時間に影響しません。 詳細については、「セキュリティの [変更](/previous-versions/dotnet/framework/security/security-changes)」の「セキュリティポリシーの簡略化」を参照してください。  
  
 共通言語ランタイム (CLR) は、読み込み時に Authenticode 署名を検証して、アセンブリの証拠を作成しようとし <xref:System.Security.Policy.Publisher> ます。 ただし、既定では、ほとんどのアプリケーションは証拠を必要としません <xref:System.Security.Policy.Publisher> 。 標準の CAS ポリシーは、に依存 <xref:System.Security.Policy.PublisherMembershipCondition> しません。 カスタム CAS ポリシーを使用しているコンピューターでアプリケーションを実行する場合や、部分信頼環境での要求を満たす場合を除き、発行元の署名の検証に関連する不要な起動コストを回避する必要があり <xref:System.Security.Permissions.PublisherIdentityPermission> ます。 (Id 権限の要求は、完全に信頼された環境では常に成功します)。  
  
> [!NOTE]
> サービスでは、要素を使用して起動時のパフォーマンスを向上させることをお勧めし `<generatePublisherEvidence>` ます。  また、この要素を使用すると、タイムアウトを発生させたり、サービスの開始をキャンセルしたりする可能性がある遅延を回避することもできます。  
  
## <a name="configuration-file"></a>構成ファイル  

 この要素は、アプリケーション構成ファイルでのみ使用できます。  
  
## <a name="example"></a>例  

 次の例は、要素を使用して、 `<generatePublisherEvidence>` アプリケーションの CAS 発行者ポリシーのチェックを無効にする方法を示しています。  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
