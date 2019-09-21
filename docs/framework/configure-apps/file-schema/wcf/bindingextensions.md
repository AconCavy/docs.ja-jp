---
title: <bindingExtensions>
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: 34ba198de33ae4aa1882d13f74bd2d538999a0c9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919788"
---
# <a name="bindingextensions"></a>\<bindingExtensions >
このセクションは、コンピューターまたはアプリケーションの構成ファイルからユーザー定義のバインディングを使用できます。 このコレクションにユーザー定義のバインディングを追加するには、`add` キーワードを使用し、要素の `type` 属性をユーザー定義のバインディングに設定して、`name` 属性をユーザー定義のバインディングの名前に設定します。  
  
 バインディングの拡張により、ユーザーは、エンドポイント構成の一部として使用するユーザー定義のバインディングを作成できます。 プログラムではバインディング拡張は、抽象クラス <xref:System.ServiceModel.Channels.Binding> を実装する型です。  
  
 次の例は、`add` 要素と `name` 属性を使用して、構成ファイルの `bindingElementExtensions` セクションにバインディング拡張を追加します。  
  
```xml  
<system.serviceModel>
  <extensions>
    <bindingExtensions>
      <add name="MyBinding"
           type="Microsoft.ServiceModel.Samples.MyBinding, MyBinding,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </bindingExtensions>
  </extensions>
</system.serviceModel>
```  
  
 構成機能を要素に追加するには、ユーザーは `bindingSection` を記述して登録する必要があります。 詳細については、<xref:System.Configuration> を参照してください。  
  
 要素とその構成の型を定義したら、次の例に示すように拡張をエンドポイントの一部として使用できます。  
  
```xml  
<services>
  <service name="MyService">
    <endpoint address="myAddress"
              binding="MyBinding" />
  </service>
</services>
```  
  
## <a name="see-also"></a>関連項目

- [バインディングの拡張](../../../wcf/extending/extending-bindings.md)
