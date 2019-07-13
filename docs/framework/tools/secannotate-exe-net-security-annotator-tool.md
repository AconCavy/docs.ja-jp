---
title: SecAnnotate.exe (.NET セキュリティ アノテーター ツール)
ms.date: 03/30/2017
helpviewer_keywords:
- SecAnnotate.exe
- Security Annotator tool
ms.assetid: 8104d208-7813-4a1d-8a75-58f9a7bcb8c9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: caedc586a9d33ecbdc4a8c7202abcfdaafabd98c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469275"
---
# <a name="secannotateexe-net-security-annotator-tool"></a>SecAnnotate.exe (.NET セキュリティ アノテーター ツール)
.NET セキュリティ アノテーター ツール (SecAnnotate.exe) は、1 つ以上のアセンブリの `SecurityCritical` 部分と `SecuritySafeCritical` 部分を識別するコマンド ライン アプリケーションです。  
  
 Visual Studio 拡張機能である[セキュリティ アノテーター](https://go.microsoft.com/fwlink/?LinkId=198007)は、SecAnnotate.exe のグラフィカル ユーザー インターフェイスであり、Visual Studio から実行できます。  
  
 このツールは、Visual Studio と共に自動的にインストールされます。 このツールを実行するには、Visual Studio 用開発者コマンド プロンプト (または Windows 7 の Visual Studio コマンド プロンプト) を使用します。 詳細については、「[Visual Studio 用開発者コマンド プロンプト](../../../docs/framework/tools/developer-command-prompt-for-vs.md)」を参照してください。  
  
 コマンド プロンプトで次のコマンドを入力します。*parameters* は、次のセクションで説明するパラメーターで、*assemblies* は、空白で区切られた 1 つ以上のアセンブリ名で構成されます。  
  
## <a name="syntax"></a>構文  
  
```  
SecAnnotate.exe [parameters] [assemblies]  
```  
  
## <a name="parameters"></a>パラメーター  
  
|オプション|説明|  
|------------|-----------------|  
|`/a`<br /><br /> または<br /><br /> `/showstatistics`|分析対象のアセンブリにおける透過性の使用に関する統計情報を表示します。|  
|`/d:` *directory*<br /><br /> または<br /><br /> `/referencedir:` *directory*|注釈の処理時に依存アセンブリを検索するディレクトリを指定します。|  
|`/i`<br /><br /> または<br /><br /> `/includesignatures`|署名に関する拡張情報を注釈レポート ファイルに含めます。|  
|`/n`<br /><br /> または<br /><br /> `/nogac`|グローバル アセンブリ キャッシュ内の参照アセンブリを検索しないようにします。|  
|`/o:` *output.xml*<br /><br /> または<br /><br /> `/out:` *output.xml*|出力注釈ファイルを指定します。|  
|`/p:` *maxpasses*<br /><br /> または<br /><br /> `/maximumpasses:` *maxpasses*|新しい注釈の生成を停止するまでにアセンブリで実行する注釈パスの最大数を指定します。|  
|`/q`<br /><br /> または<br /><br /> `/quiet`|クワイエット モードを指定します。このモードでは、ステータス メッセージは出力されず、エラー情報だけが出力されます。|  
|`/r:` *assembly*<br /><br /> または<br /><br /> `/referenceassembly:` *assembly*|注釈の処理時、依存アセンブリを解決するときに、指定したアセンブリを含めます。 参照アセンブリは参照パスにあるアセンブリよりも優先されます。|  
|`/s:` *rulename*<br /><br /> または<br /><br /> `/suppressrule:` *rulename*|入力アセンブリについて、指定した透過性規則を実行しないようにします。|  
|`/t`<br /><br /> または<br /><br /> `/forcetransparent`|強制的に、透過性注釈がないすべてのアセンブリを完全に透過的として扱います。|  
|`/t`:*assembly*<br /><br /> または<br /><br /> `/forcetransparent`:*assembly*|現在のアセンブリ レベルの注釈に関係なく、指定されたアセンブリを強制的に透過的にします。|  
|||  
|`/v`<br /><br /> または<br /><br /> `/verify`|アセンブリの注釈が正しいことだけを検証します。アセンブリで検証されない場合に、必要な注釈をすべて見つけるために複数のパスを実行しようとはしません。|  
|`/x`<br /><br /> または<br /><br /> `/verbose`|注釈の処理時に詳細を出力することを指定します。|  
|`/y:` *directory*<br /><br /> または<br /><br /> `/symbolpath:` *directory*|注釈の処理時、シンボル ファイルを検索するときに、指定したディレクトリを含めます。|  
  
## <a name="remarks"></a>解説  
 パラメーターとアセンブリは、コマンド ラインでアット マーク (@) をプレフィックスとして付けて指定する応答ファイルで指定することもできます。 応答ファイルの各行には、1 つのパラメーターまたはアセンブリの名前を指定する必要があります。  
  
 .NET セキュリティ アノテーターについて詳しくは、.NET セキュリティ ブログの「[Using SecAnnotate to Analyze Your Assemblies for Transparency Violations](https://go.microsoft.com/fwlink/?LinkId=187648)」(SecAnnotate を使用したアセンブリでの透過性違反の分析) をご覧ください。  
  
## <a name="examples"></a>使用例
