---
title: '方法: アクセス制御リスト エントリを追加または削除する (.NET Framework のみ)'
ms.date: 01/14/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ACEs [.NET Framework]
- ACLs [.NET Framework]
- access control entries [.NET Framework]
- I/O [.NET Framework], access control list entries
- access control lists [.NET Framework]
ms.assetid: 53758b39-bd9b-4640-bb04-cad5ed8d0abf
ms.openlocfilehash: 49cbb27c1b9d7ae0b05077c7f4fe01a2dfe87ccb
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820801"
---
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a>方法: アクセス制御リスト エントリを追加または削除する (.NET Framework のみ)

ファイルまたはディレクトリでアクセス制御リスト (ACL) エントリを追加したり、削除したりするには、<xref:System.Security.AccessControl.FileSecurity> または <xref:System.Security.AccessControl.DirectorySecurity> オブジェクトをファイルまたはディレクトリから取得します。 オブジェクトを変更し、ファイルまたはディレクトリに戻します。  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a>ACL エントリをファイルに追加するか、ファイルから削除する  
  
1. <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> メソッドを呼び出して、ファイルの現在の ACL エントリを含む <xref:System.Security.AccessControl.FileSecurity> オブジェクトを取得します。  
  
2. 手順 1. から返された <xref:System.Security.AccessControl.FileSecurity> オブジェクトで ACL エントリの追加または削除を行います。  
  
3. 変更を適用するには、<xref:System.Security.AccessControl.FileSecurity> オブジェクトを <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> メソッドに渡します。  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a>ACL エントリをディレクトリに追加するか、ディレクトリから削除する  
  
1. <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> メソッドを呼び出して、ディレクトリの現在の ACL エントリを含む <xref:System.Security.AccessControl.DirectorySecurity> オブジェクトを取得します。  
  
2. 手順 1. から返された <xref:System.Security.AccessControl.DirectorySecurity> オブジェクトで ACL エントリの追加または削除を行います。  
  
3. 変更を適用するには、<xref:System.Security.AccessControl.DirectorySecurity> オブジェクトを <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> メソッドに渡します。  
  
## <a name="example"></a>例  
 この例を実行するには、有効なユーザーまたはグループ アカウントを使用する必要があります。 この例は <xref:System.IO.File> オブジェクトを使用します。 <xref:System.IO.FileInfo>、<xref:System.IO.Directory>、<xref:System.IO.DirectoryInfo> クラスに対して同じ手順を使用します。

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
