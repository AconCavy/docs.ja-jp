---
title: Docker ベースのアプリケーションの開発プロセス
description: Docker ベースのアプリケーションの開発のオプションに関する概要を確認します。 マルチ プラットフォームのサポート (Windows、macOS、Linux) のため、Windows 用 Visual Studio、Visual Studio for Mac、または Visual Studio Code のうち好みのものを使います。
ms.date: 09/27/2018
ms.openlocfilehash: 95e940371f4dbef3b3a8f327c13acbbc55ff29ef
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337695"
---
# <a name="development-process-for-docker-based-applications"></a>Docker ベースのアプリケーションの開発プロセス

*Visual Studio と Visual Studio Tools for Docker を使用して IDE に重点を置くか、Docker CLI と Visual Studio Code を使用して CLI/エディターに重点を置くか、好みの方法でコンテナー化された .NET アプリケーションを開発します。*

## <a name="development-environment-for-docker-apps"></a>Docker アプリの開発環境

### <a name="development-tool-choices-ide-or-editor"></a>開発ツールの選択:IDE またはエディター

完全で強力な IDE または軽量でアジャイルなエディターのどちらを選んでも、Microsoft では Docker アプリケーションの開発に使用できるツールが用意されています。

**Visual Studio (Windows 版)。** Visual Studio を使って Docker ベースのアプリケーションを開発する場合は、既に組み込まれている Docker 用ツールに付属する Visual Studio 2017 バージョン 15.7 以降を使うことをお勧めします。 Tools for Docker を使用して、ターゲットの Docker 環境で直接アプリケーションの開発、実行、および検証ができます。 F5 キーを押すと、Docker ホスト内で直接アプリケーション (1 つのコンテナー、または複数のコンテナー) を実行してデバックできます。または、CTRL キーを押しながら F5 キーを押すと、コンテナーを再構築しなくても、アプリケーションを編集して更新できます。 これは、Docker ベース アプリを開発する場合の最も強力な選択肢です。

**Visual Studio for Mac。** これは macOS で動作する IDE であり、Xamarin Studio が進化したものです。2017 年中頃から Docker をサポートしています。 これは、強力な IDE を使用したい macOS コンピューターで作業する開発者にとって好ましい選択肢です。

**Visual Studio Code と Docker CLI**。 任意の開発言語をサポートする軽量なクロスプラット フォーム エディターを選択すると、Microsoft Visual Studio Code (VS Code) と Docker CLI を使用することができます。 これは、macOS、Linux、Windows 向けのクロスプラット フォーム開発アプローチです。 さらに、Visual Studio Code は、Dockerfiles の IntelliSense などの Docker の拡張機能や、エディターから Docker コマンドを実行するショートカット タスクをサポートします。

[Docker Desktop Community Edition (CE)](https://hub.docker.com/search/?type=edition&offering=community) をインストールすることで、1 つの Docker CLI を使用して Windows と Linux の両方のアプリを構築することができます。

### <a name="additional-resources"></a>その他の技術情報

- **Visual Studio**。 公式サイト。 \
  [https://visualstudio.microsoft.com/vs/](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

- **Visual Studio Code**。 公式サイト。 \
  <https://code.visualstudio.com/download>

- **Docker Desktop for Windows Community Edition (CE)**  \
  [https://hub.docker.com/editions/community/docker-ce-desktop-windows](https://hub.docker.com/editions/community/docker-ce-desktop-windows)

- **Docker Desktop for Mac Community Edition (CE)**  \
  [https://hub.docker.com/editions/community/docker-ce-desktop-mac](https://hub.docker.com/editions/community/docker-ce-desktop-mac)

## <a name="net-languages-and-frameworks-for-docker-containers"></a>.NET 言語および Docker コンテナーのフレームワーク

このガイドの前のセクションで触れたように、Docker コンテナー化された NET アプリケーションを開発する際に、.NET Framework、.NET Core、またはオープン ソースの Mono プロジェクトを使用できます。 Linux または Windows コンテナーをターゲットにする場合、使用している .NET Framework に応じて、C\#、F\#、または Visual Basic で開発できます。 .NET 言語の詳細については、ブログ投稿「[The .NET Language Strategy](https://devblogs.microsoft.com/dotnet/the-net-language-strategy/)」 (.NET 言語戦略) を参照してください。

>[!div class="step-by-step"]
>[前へ](../architect-microservice-container-applications/scalable-available-multi-container-microservice-applications.md)
>[次へ](docker-app-development-workflow.md)
