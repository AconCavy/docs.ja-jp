---
title: "WIF セッション管理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98bce126-18a9-401b-b20d-67ee462a5f8a
caps.latest.revision: 7
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d71b83231140dcc18e6d2351091fbfd4985e90a2
ms.contentlocale: ja-jp
ms.lasthandoff: 08/21/2017

---
# <a name="wif-session-management"></a>WIF セッション管理
証明書利用者によりホストされている保護リソースにクライアントが初めてアクセスしようとするとき、クライアントは最初に、証明書利用者が信頼しているセキュリティ トークン サービス (STS) に身元を証明する必要があります。 認証後、STS はセキュリティ トークンをクライアントに発行します。 クライアントは証明書利用者にこのトークンを提示します。証明書利用者は保護リソースへのアクセスをクライアントに許可します。 ただし、要求のたびにクライアントが STS に再認証するということは望ましくありません。コンピューターやドメインが証明書利用者のものと同じではないことがあるためです。 代わりに、Windows Identity Foundation (WIF) はクライアントと証明書利用者にセッションを確立させ、そのセッションで、最初の要求後のすべての要求に関して、クライアントはセッション セキュリティ トークンを利用して証明書利用者に身元を証明します。 証明書利用者は Cookie 内に保存されるこのセッション セキュリティ トークンを利用し、クライアントの <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=fullName> を再構築できます。  
  
 STS は、クライアントが提供する必要のある認証を定義します。 ただし、STS に身元を証明するための資格情報がクライアントに複数与えられていることがあります。 たとえば、Windows Live のトークン、ユーザー名とパスワード、証明書、スマートキーが与えられていることがあります。 その場合、STS はクライアントにいくつかの ID を与えます。それぞれの ID が、クライアントが提示する資格情報の 1 つに対応します。 証明書利用者は、クライアントに与えるアクセス レベルを決定するとき、そのような ID の 1 つまたは複数を利用できます。  
  
 <xref:System.IdentityModel.Tokens.SessionSecurityToken?displayProperty=fullName> は、<xref:System.Security.Claims.ClaimsPrincipal.Identities%2A> にクライアントのすべての ID を含む、クライアントの <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=fullName> の再構築に使用されます。 コレクションの各 <xref:System.Security.Claims.ClaimsIdentity?displayProperty=fullName> には、その ID に関連付けられているブートストラップ トークンが含まれます。  
  
 新しいセッション トークンが元のセッション トークンのセッション ID で発行されている場合、<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler?displayProperty=fullName> は、トークン キャッシュのセッション トークンを更新しません。 セッション トークンは常に一意のセッション ID でインスタンス化する必要があります。  
  
> [!NOTE]
>  Session.SecurityTokenHandler.ReadToken は、無効な入力を受け取ると、<xref:System.Xml.XmlException> 例外をスローします。たとえば、セッション トークンが含まれる Cookie が壊れている場合です。 この例外をキャッチし、アプリケーション固有の動作を提供することが推奨されます。  
  
 保護されている Web ページに、保護ドメインにも存在するたくさんのリソースが含まれる場合 (小さなグラフィックスなど)、各リソースをダウンロードするには、クライアントは証明書利用者に対して身元を再証明する必要があります。 セッション認証トークンを利用することで、要求のたびに STS に認証する必要がなくなります。ただし、Cookie がたくさん送信されることは変わりません。 重要なデータとリソースを保護ドメインに保存し、重要ではない項目を保護のないドメインに保存し、メインの Web ページにリンクさせる方法が Web ページの構築方法として推奨されます。 また、Cookie パスは、保護ドメインだけを参照するように設定します。  
  
 参照モードで操作する際、**global.asax.cs** ファイルに <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SessionSecurityTokenCreated> イベントのハンドラーを指定し、<xref:System.IdentityModel.Services.SessionSecurityTokenCreatedEventArgs.SessionToken%2A> プロパティで渡されるトークンで **IsReferenceMode** プロパティを設定することを Microsoft は推奨しています。 以上の更新により、セッション トークンは要求のたびに参照モードで動作し、セッション認証モジュールで設定した <xref:System.IdentityModel.Services.SessionAuthenticationModule.IsReferenceMode%2A> プロパティより優先されます。  
  
## <a name="extensibility"></a>機能拡張  
 セッション管理メカニズムを拡張できます。 その理由の 1 つは、パフォーマンスを改善できることにあります。 たとえば、メモリ内の状態と Cookie の内容を比較し、セッション セキュリティ トークンを変換したり、最適化したりするカスタム Cookie ハンドラーを作成できます。 その場合、<xref:System.IdentityModel.Services.SessionAuthenticationModule?displayProperty=fullName> の <xref:System.IdentityModel.Services.SessionAuthenticationModule.CookieHandler%2A?displayProperty=fullName> プロパティを構成し、<xref:System.IdentityModel.Services.CookieHandler?displayProperty=fullName> から誘導されたカスタム Cookie ハンドラーを使用できます。 <xref:System.IdentityModel.Services.ChunkedCookieHandler?displayProperty=fullName> が既定の Cookie ハンドラーです。Cookie はハイパーテキスト転送プロトコル (HTTP) の許容サイズを超えるためです。代わりにカスタム Cookie ハンドラーを使用する場合、チャンクを実装してください。  
  
 詳細については、[ClaimsAwareWebFarm](http://go.microsoft.com/fwlink/?LinkID=248408) (http://go.microsoft.com/fwlink/?LinkID=248408) サンプルをご覧ください。 このサンプルでは、(tokenreplycache ではなく) ファーム対応セッション キャッシュを確認できます。大きな Cookie を交換せず、参照でセッションを利用できます。このサンプルではまた、ファームで Cookie を保護する簡単な方法を確認できます。 このセッション キャッシュは WCF ベースです。 セッション セキュリティに関しては、このサンプルでは、MachineKey に基づく、Cookie 変換の WIF 4.5 の新機能を確認できます。これは、web.config に適切なスニペットを貼り付けるだけで有効にできます。サンプル自体は "ファーム化" されていませんが、アプリをファーム対応にするために必要なことを示します。
