---
title: '方法: (WCF) 証明書を取得します。'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: 1a2731c535bd403046ca3bc01364d0933f127a7f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64643671"
---
# <a name="how-to-obtain-a-certificate-wcf"></a>方法: (WCF) 証明書を取得します。
Windows Communication Foundation (WCF) のいずれかを使用するには、その機能を使用して、X.509 証明書の最初に証明書を取得します。  
  
### <a name="to-obtain-an-x509-certificate"></a>X.509 証明書を取得するには  
  
1. 次のいずれかを選択します。  
  
    - VeriSign, Inc. などの証明機関から証明書を購入します。  
  
    - 独自の証明書サービスを設定し、証明機関に証明書への署名を依頼します。 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]、Windows 2000 Server、Windows 2000 Server Datacenter、および Windows 2000 Datacenter Server にはすべて、公開キー基盤 (PKI) をサポートする証明書サービスが用意されています。 Windows Server 2008 で使用して、 [Active Directory Certificate Services](https://go.microsoft.com/fwlink/?LinkID=153483)証明機関を管理します。  
  
    - 独自の証明書サービスを設定し、証明書には署名しません。  
  
    > [!NOTE]
    >  どの方法を使用する場合でも、X.509 証明書を含む SOAP 要求の受信者は、その X.509 証明書を信頼する必要があります。 つまり、証明書チェーン内の X.509 証明書または発行者は、信頼されたユーザーの証明書ストア内に存在し、また X.509 証明書は信頼されない証明書ストア内には存在しないということを意味します。  
  
## <a name="see-also"></a>関連項目

- [証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [方法: 開発中に使用するための一時的な証明書を作成します。](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
