---
title: -win32manifest (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
ms.openlocfilehash: 6eb9d50a3ecd80acb0349f1ba315d9cf8ccc6dc2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937235"
---
# <a name="-win32manifest-visual-basic"></a>-win32manifest (Visual Basic)
プロジェクトのポータブル実行可能 (PE) ファイルに埋め込まれる、ユーザー定義の Win32 アプリケーション マニフェスト ファイルを識別します。  
  
## <a name="syntax"></a>構文  
  
```  
-win32manifest: fileName  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`fileName`|カスタムマニフェストファイルのパス。|  
  
## <a name="remarks"></a>Remarks  
 既定では、Visual Basic コンパイラは、asInvoker の要求実行レベルを指定するアプリケーションマニフェストを埋め込みます。 実行可能ファイルがビルドされたフォルダー (通常は、Visual Studio を使用する場合は bin\Debug または bin\Release フォルダー) にマニフェストが作成されます。 HighestAvailable または requireAdministrator の要求実行レベルを指定するなど、カスタムマニフェストを指定する場合は、このオプションを使用してファイルの名前を指定します。  
  
> [!NOTE]
> このオプションと[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)オプションは同時に指定できません。 同じコマンドラインで両方のオプションを使用しようとすると、ビルドエラーが発生します。  
  
 アプリケーション マニフェストを持たないアプリケーションは、要求実行レベルを指定した場合、Windows Vista のユーザー アカウント制御機能によって、ファイルまたはレジストリの仮想化の対象となります。 仮想化について詳しくは、「[Windows Vista の ClickOnce 配置](/visualstudio/deployment/clickonce-deployment-on-windows-vista)」を参照してください。  
  
 次のいずれかの条件に該当する場合、アプリケーションは仮想化の対象になります。  
  
1. オプションを使用`-nowin32manifest`して、後のビルド手順でマニフェストを提供したり、 `-win32resource`オプションを使用して Windows リソース (.res) ファイルの一部として指定したりすることはできません。  
  
2. 要求実行レベルが指定されていないカスタム マニフェストを提供している。  
  
 Visual Studio は、既定の .manifest ファイルを作成し、それを実行可能ファイルと一緒にデバッグ ディレクトリとリリース ディレクトリに保存します。 既定のアプリケーションマニフェストファイルを表示または編集するには、プロジェクトデザイナーの **[アプリケーション]** タブで **[UAC 設定の表示]** をクリックします。 詳細については、「[[アプリケーション] ページ (プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)」を参照してください。  
  
 アプリケーションマニフェストは、カスタムのビルド後の手順として提供することも、 `-nowin32manifest`オプションを使用して Win32 リソースファイルの一部として指定することもできます。 アプリケーションを Windows Vista でファイルまたはレジストリの仮想化の対象にする場合は、これと同じオプションを使用します。 これにより、コンパイラは既定のマニフェストを作成し、PE ファイルに埋め込むことができなくなります。  
  
## <a name="example"></a>例  
 次の例は、Visual Basic コンパイラによって PE に挿入される既定のマニフェストを示しています。  
  
> [!NOTE]
> コンパイラは、標準のアプリケーション名 MyApplication をマニフェスト XML に挿入します。 これは、アプリケーションを Windows Server 2003 Service Pack 3 で実行できるようにするための回避策です。  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <assemblyIdentity version="1.0.0.0" name="MyApplication.app"/>  
  <trustInfo xmlns="urn:schemas-microsoft-com:asm.v2">  
    <security>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <requestedExecutionLevel level="asInvoker"/>  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
</assembly>  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-nowin32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
