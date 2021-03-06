---
title: F# を使用した Azure File Storage の概要
description: Azure File Storage を使用してクラウドにファイル データを格納し、Azure 仮想マシン (VM) から、または Windows を実行しているオンプレミスのアプリケーションからクラウド ファイル共有をマウントします。
author: sylvanc
ms.date: 09/20/2016
ms.custom: devx-track-fsharp
ms.openlocfilehash: dd19b156e73774f4eca63afd3f4c10a4a7b8d46c
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100127"
---
# <a name="get-started-with-azure-file-storage-using-f"></a>F を使用して Azure File storage を使ってみる\#

Azure File Storage は、標準の [サーバー メッセージ ブロック (SMB) プロトコル](/windows/win32/fileio/microsoft-smb-protocol-and-cifs-protocol-overview)を使用してクラウドでファイル共有を提供するサービスです。 SMB 2.1 と SMB 3.0 の両方がサポートされます。 Azure File Storage を使用すると、コストがかかる書き換えを行わずに、ファイル共有に依存しているレガシ アプリケーションをすばやく Azure に移行することができます。 Azure 仮想マシンまたはクラウド サービスで実行されているアプリケーション、またはオンプレミスのクライアントから実行されているアプリケーションは、デスクトップ アプリケーションが一般的な SMB 共有をマウントするのと同じように、クラウドにファイル共有をマウントできます。 このため、任意の数のアプリケーション コンポーネントが、File Storage 共有をマウントして同時にアクセスできます。

ファイルストレージの概念の概要については、「 [.net ガイド](/azure/storage/storage-dotnet-how-to-use-files)」を参照してください。

## <a name="prerequisites"></a>必須コンポーネント

このガイドを使用するには、最初に [Azure ストレージアカウントを作成](/azure/storage/storage-create-storage-account)する必要があります。
また、このアカウントのストレージアクセスキーも必要になります。

## <a name="create-an-f-script-and-start-f-interactive"></a>F # スクリプトを作成して F# インタラクティブを開始する

この記事のサンプルは、F # アプリケーションと F # スクリプトのどちらでも使用できます。 F # スクリプトを作成するには、 `.fsx` `files.fsx` f # 開発環境で、などの拡張子を持つファイルを作成します。

次に、[パケット](https://fsprojects.github.io/Paket/)や[NuGet](https://www.nuget.org/)などの[パッケージマネージャー](package-management.md)を使用して、 `WindowsAzure.Storage` ディレクティブを使用してスクリプトにパッケージと参照をインストールし `WindowsAzure.Storage.dll` `#r` ます。

### <a name="add-namespace-declarations"></a>名前空間宣言の追加

次の `open` ステートメントを `files.fsx` ファイルの先頭に追加します。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>接続文字列を取得する

このチュートリアルでは、Azure Storage 接続文字列が必要です。 接続文字列の詳細については、「 [ストレージ接続文字列の構成](/azure/storage/storage-configure-connection-string)」を参照してください。

このチュートリアルでは、次のように、スクリプトに接続文字列を入力します。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

ただし、実際のプロジェクトではこの方法は **お勧めできません** 。 ストレージ アカウント キーは、ストレージ アカウントの root パスワードに似ています。 ストレージ アカウント キーは常に慎重に保護してください。 このキーを他のユーザーに配布したり、ハードコーディングしたり、他のユーザーがアクセスできるプレーン テキスト ファイルに保存したりしないでください。 侵害された可能性があると思われる場合は、Azure portal を使用してキーを再生成することができます。

実際のアプリケーションでは、ストレージ接続文字列を維持する最善の方法は構成ファイルにあります。 構成ファイルから接続文字列を取得するには、次の手順を実行します。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

Azure Configuration Manager の使用はオプションです。 .NET Framework の型などの API を使用することもでき `ConfigurationManager` ます。

### <a name="parse-the-connection-string"></a>接続文字列を解析する

接続文字列を解析するには、次のように指定します。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

これにより、が返され `CloudStorageAccount` ます。

### <a name="create-the-file-service-client"></a>ファイルサービスクライアントを作成する

`CloudFileClient`型を使用すると、ファイルストレージに格納されているファイルをプログラムで使用できます。 サービス クライアントを作成する方法の 1 つを次に示します。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

これで、からデータを読み取り、ファイルストレージにデータを書き込むコードを記述する準備ができました。

## <a name="create-a-file-share"></a>ファイル共有を作成する

この例では、ファイル共有がまだ存在しない場合に作成する方法を示します。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a>ルートディレクトリとサブディレクトリを作成する

ここでは、ルートディレクトリを取得し、ルートのサブディレクトリを取得します。 まだ存在しない場合は、両方を作成します。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a>テキストをファイルとしてアップロードする

この例では、テキストをファイルとしてアップロードする方法を示します。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a>ファイルのローカルコピーにファイルをダウンロードする

ここでは、作成したばかりのファイルをダウンロードし、ローカルファイルに内容を追加します。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a>ファイル共有の最大サイズの設定

次の例では、共有の現在の使用状況を確認する方法と、共有のクォータを設定する方法を示します。 `FetchAttributes` 共有のを設定し、ローカルの `Properties` 変更を `SetProperties` Azure File storage に反映するには、を呼び出す必要があります。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a>ファイルまたはファイル共有の Shared Access Signature の生成

ファイル共有または個々のファイルの Shared Access Signature (SAS) を生成することができます。 また、ファイル共有に共有アクセス ポリシーを作成して、Shared Access Signature を管理することもできます。 共有アクセス ポリシーを作成することをお勧めします。これにより、侵害されそうな場合に SAS を取り消すことができます。

ここでは、共有に対して共有アクセスポリシーを作成し、そのポリシーを使用して、共有内のファイルの SAS に対する制約を指定します。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

Shared Access Signature の作成と使用の詳細については、「[Shared Access Signature (SAS) の使用](/azure/storage/storage-dotnet-shared-access-signature-part-1)」と、[Blob Storage での SAS の作成と使用](/azure/storage/storage-dotnet-shared-access-signature-part-2)に関するページを参照してください。

### <a name="copy-files"></a>ファイルのコピー

ファイルを別のファイルまたは blob にコピーしたり、blob をファイルにコピーしたりできます。 Blob をファイルにコピーする場合、またはファイルを blob にコピーする場合は、同じストレージアカウント内でコピーする場合でも、共有アクセス署名 (SAS) を使用してソースオブジェクトを認証する *必要があり* ます。

### <a name="copy-a-file-to-another-file"></a>別のファイルへのファイルのコピー

ここでは、同じ共有内の別のファイルにファイルをコピーします。 このコピー操作では同じストレージ アカウント内のファイルがコピーされるため、共有キー認証を使用してコピーを実行できます。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a>BLOB へのファイルのコピー

ここでは、ファイルを作成し、同じストレージアカウント内の blob にコピーします。 コピー操作中にソースファイルへのアクセスを認証するためにサービスが使用するソースファイルの SAS を作成します。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

同じ方法で、ファイルに BLOB をコピーできます。 ソース オブジェクトが BLOB である場合、SAS を作成して、コピー操作中にその BLOB へのアクセスを認証します。

## <a name="troubleshooting-file-storage-using-metrics"></a>メトリックを使用した File Storage のトラブルシューティング

Azure Storage Analytics は、ファイルストレージのメトリックをサポートしています。 メトリック データを使用すると、要求のトレースや問題の診断ができます。

[Azure portal](https://portal.azure.com)から File storage のメトリックを有効にすることも、次のように F # からメトリックを有効にすることもできます。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a>次の手順

Azure File storage の詳細については、次のリンクを参照してください。

### <a name="conceptual-articles-and-videos"></a>概念に関する記事とビデオ

- [Azure File Storage: Windows および Linux 用の円滑なクラウド SMB ファイル システム](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [Linux で Azure File Storage を使用する方法](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a>File Storage 用のツールのサポート

- [Azure Storage での Azure PowerShell の使用](/azure/storage/storage-powershell-guide-full)
- [Microsoft Azure Storage で AzCopy を使用する方法](/azure/storage/storage-use-azcopy)
- [Azure CLI を使用して BLOB を作成、ダウンロード、一覧表示する](/azure/storage/blobs/storage-quickstart-blobs-cli#create-and-manage-file-shares)

### <a name="reference"></a>リファレンス

- [.NET 用ストレージ クライアント ライブラリ リファレンス](/dotnet/api/overview/azure/storage)
- [File サービスの REST API リファレンス](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a>ブログ記事

- [Azure File Storage の一般提供開始](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [Inside Azure File Storage (Azure File Storage の内部)](https://azure.microsoft.com/blog/inside-azure-file-storage/)
- [Microsoft Azure File サービスの概要](/archive/blogs/windowsazurestorage/introducing-microsoft-azure-file-service)
- [Microsoft Azure Files への接続の維持](/archive/blogs/windowsazurestorage/persisting-connections-to-microsoft-azure-files)
