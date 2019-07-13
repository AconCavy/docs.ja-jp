---
title: '方法: Visual Basic でアプリケーション設定を読み取る'
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: e7d909563ca7e991a51c2f921b5248aa587a83d7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58823585"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a>方法: Visual Basic でアプリケーション設定を読み取る
`My.Settings` オブジェクトで設定のプロパティにアクセスすると、ユーザー設定を読み取ることができます。  
  
 `My.Settings` オブジェクトでは、各設定はプロパティとして公開されます。 プロパティ名はその設定の名前と同じで、プロパティの型は設定の型と同じです。 プロパティが読み取り専用かどうかは、設定の**スコープ**でわかります。つまり、**アプリケーション** スコープの設定のプロパティは読み取り専用であるのに対し、**ユーザー** スコープの設定のプロパティは読み取り/書き込みです。 詳細については、「[My.Settings オブジェクト](../../../../visual-basic/language-reference/objects/my-settings-object.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例は、`Nickname` の設定値を表示します。  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 この例を実行するには、アプリケーションで `String` 型の `Nickname` を設定する必要があります。 詳細については、「[アプリケーションの設定の管理 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [My.Settings オブジェクト](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [方法: Visual Basic でユーザー設定を変更する](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [方法: Visual Basic でユーザー設定を永続化する](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [方法: Visual Basic でユーザー設定のためのプロパティ グリッドを作成する](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [アプリケーションの設定の管理 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
