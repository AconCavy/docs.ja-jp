---
title: '方法: WindowsPrincipal プロジェクトを作成する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsPrincipal objects, creating
- security [.NET Framework], creating a WindowsPrincipal object
- security [.NET Framework], principals
- principal objects, creating
ms.assetid: 56eb10ca-e61d-4ed2-af7a-555fc4c25a25
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f298a7b036857e783efa128ce45ee8634ce993d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795185"
---
# <a name="how-to-create-a-windowsprincipal-object"></a>方法: WindowsPrincipal プロジェクトを作成する
コードが役割ベースの検証を繰り返し実行する必要があるか、1 回だけ実行する必要があるかによって、<xref:System.Security.Principal.WindowsPrincipal> オブジェクトを作成する方法は 2 つあります。  
  
 コードが役割ベースの検証を繰り返し実行する必要がある場合、次の最初の手順のほうが、生成されるオーバーヘッドが少なくなります。 コードが役割ベースの検証を 1 回だけ実行する必要がある場合、次の 2 番目の手順を使用して <xref:System.Security.Principal.WindowsPrincipal> オブジェクトを作成できます。  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a>繰り返し検証で WindowsPrincipal オブジェクトを作成するには  
  
1. 静的な <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> プロパティによって返される <xref:System.AppDomain> オブジェクトの <xref:System.AppDomain.SetPrincipalPolicy%2A> メソッドを呼び出し、新しいポリシーの内容を示す <xref:System.Security.Principal.PrincipalPolicy> 列挙値があるメソッドに渡します。 サポートされる値は <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>、<xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>、および <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal> です。 次のコードは、このメソッドの呼び出しを示しています。  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2. ポリシーの設定により、静的な <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> プロパティを使用して、現在の Windows ユーザーをカプセル化するプリンシパルを取得します。 プロパティの戻り値の型は <xref:System.Security.Principal.IPrincipal> であるため、結果を <xref:System.Security.Principal.WindowsPrincipal> 型にキャストする必要があります。 次のコードは、新しい <xref:System.Security.Principal.WindowsPrincipal> オブジェクトを、現在のスレッドに関連付けられたプリンシパルの値に初期化します。  
  
    ```csharp  
    WindowsPrincipal myPrincipal =   
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim myPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)   
    ```  
  
3. プリンシパル オブジェクトが作成されると、いくつかのメソッドのいずれかを使用して検証できます。  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a>1 回の検証用に WindowsPrincipal オブジェクトを作成するには  
  
1. 静的な <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> メソッドを呼び出して新しい <xref:System.Security.Principal.WindowsIdentity> オブジェクトを初期化します。このメソッドは、現在の Windows アカウントに対してクエリを実行し、そのアカウントに関する情報を新規作成された ID オブジェクトに配置します。 次のコードは、<xref:System.Security.Principal.WindowsIdentity> オブジェクトを新規作成し、これを現在の認証済みユーザーに初期化します。  
  
    ```csharp  
    WindowsIdentity myIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim myIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2. <xref:System.Security.Principal.WindowsPrincipal> オブジェクトを新規作成し、これに前の手順で作成された <xref:System.Security.Principal.WindowsIdentity> オブジェクトの値を渡します。  
  
    ```csharp  
    WindowsPrincipal myPrincipal = new WindowsPrincipal(myIdentity);  
    ```  
  
    ```vb  
    Dim myPrincipal As New WindowsPrincipal(myIdentity)  
    ```  
  
3. プリンシパル オブジェクトが作成されると、いくつかのメソッドのいずれかを使用して検証できます。  
  
## <a name="see-also"></a>関連項目

- [プリンシパル オブジェクトと ID オブジェクト](../../../docs/standard/security/principal-and-identity-objects.md)
