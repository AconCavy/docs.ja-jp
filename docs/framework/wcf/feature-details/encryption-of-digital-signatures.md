---
title: 電子署名の暗号化
ms.date: 03/30/2017
helpviewer_keywords:
- encryption of digital signatures [WCF]
- digital signatures [WCF], encryption
- digital signatures [WCF]
ms.assetid: 0868866d-40b4-4341-8e42-eee3b7f15b69
ms.openlocfilehash: ea53a575802f1e7903a66c2eda466c8937fb02f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61856406"
---
# <a name="encryption-of-digital-signatures"></a>電子署名の暗号化
既定では、メッセージは署名および暗号化され、署名はデジタル暗号化されます。 これは、<xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> または <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> のインスタンスを使用してカスタム バインディングを作成し、いずれかのクラスの `MessageProtectionOrder` プロパティを <xref:System.ServiceModel.Security.MessageProtectionOrder> 列挙値に設定することによって制御できます。 既定値は <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature> です。 このプロセスは、単に署名して暗号化する場合よりも時間が 10 ～ 40 % 長くかかります。 ただし、署名の暗号化を無効にすると、攻撃者がメッセージの内容を予想できるようになる恐れがあります。 その理由は、メッセージ内のすべての署名部分のプレーン テキストのハッシュ コードが署名要素に含まれるからです。 たとえば、メッセージ本体は既定で暗号化されますが、暗号化されていない署名には、メッセージ本体のハッシュ コードが含まれます。 メッセージが短い場合は、攻撃者に内容を推測されてしまうおそれがあります。 署名を暗号化すると、このような危険性が低減または解消されます。  
  
 そのため、署名の暗号化を無効にするのは、セキュリティに影響しない大型のバイナリ ファイルを送信する場合などの、内容の重要性が低く、パフォーマンスの向上が重要な場合に限定してください。  
  
### <a name="to-disable-digital-signing"></a>デジタル署名を無効にするには  
  
1. <xref:System.ServiceModel.Channels.CustomBinding> を作成します。 詳細については、「[方法 :SecurityBindingElement を使用してカスタム バインディングを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)します。  
  
2. <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> または <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> をバインディング コレクションに追加します。  
  
3. <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> プロパティを <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> に設定するか、または <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> プロパティを <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> に設定します。  
  
 カスタム バインディングの作成の詳細については、次を参照してください。[ユーザー定義バインディング](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)します。 特定の認証モード用のカスタム バインディングを作成する方法の詳細については、次を参照してください。[方法。指定した認証モード用の SecurityBindingElement を作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)です。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Security.MessageProtectionOrder>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- [方法: SecurityBindingElement を使用してカスタム バインディングを作成します。](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [ユーザー定義バインディングの作成](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)
- [方法: 指定した認証モード用の SecurityBindingElement を作成します。](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
