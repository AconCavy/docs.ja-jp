---
title: Docker について
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | Docker について
ms.date: 08/31/2018
ms.openlocfilehash: 215d756c631440c99a3a8ad8128ec61fef3bc26d
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740100"
---
# <a name="what-is-docker"></a>Docker について

[Docker](https://www.docker.com/) は、クラウドまたはオンプレミスで実行できる移植可能な自己完結型のコンテナーとしてアプリの展開を自動化する[オープン ソース プロジェクト](https://github.com/docker/docker)です。 Docker は、クラウド、Linux、および Windows ベンダー (Microsoft を含む) と協力し、このテクノロジを促進し、進化させている[企業](https://www.docker.com/)でもあります。

![Docker コンテナーを実行できる場所を示す図。](./media/docker-defined/docker-containers-run-anywhere.png)

**図 2-2** Docker は、ハイブリッド クラウドのすべてのレイヤーでコンテナーを展開します。

Docker コンテナーは、オンプレミスのカスタマー データセンター内、外部サービス プロバイダー内、Azure 上のクラウド内など、どこでも実行できます。 Docker イメージ コンテナーは、Linux と Windows 上でネイティブに実行できます。 ただし、Windows イメージは Windows ホスト上でのみ実行でき、Linux イメージは (現在のところ Hyper-V Linux VM を使用して) Linux ホストと Windows ホスト上で実行できます (ここで言うホストとは、サーバーまたは VM です)。

開発者は、Windows、Linux、または macOS 上の開発環境を使用できます。 開発用コンピューターで、アプリとその依存関係を含む、Docker イメージが展開されている Docker ホストを実行します。 Linux または Mac 上で開発する場合は、Linux ベースの Docker ホストを使用し、Linux コンテナー専用のイメージを作成できます (Mac 上で開発する場合は、macOS からコードを編集したり Docker CLI を実行したりすることができますが、この記事の執筆時点では、コンテナーは macOS 上で直接動作しません)。Windows 上で開発する場合は、Linux または Windows コンテナーのいずれかのイメージを作成できます。

開発環境でコンテナーをホストし、開発ツールを追加するために、Docker は Windows 用または macOS 用の [Docker Community Edition (CE)](https://www.docker.com/community-edition) をリリースしています。 これらの製品で、コンテナーをホストするために必要な VM (Docker ホスト) がインストールされます。 Docker は [Docker Enterprise Edition (EE) ](https://www.docker.com/enterprise-edition) もリリースしています。エンタープライズ開発向けに設計されており、大規模なビジネスクリティカル アプリケーションをビルドし、リリースし、運用環境で実行する IT チームに使用されています。

[Windows コンテナー](/virtualization/windowscontainers/about/)を実行するには、次の 2 つの種類のランタイムがあります。

- Windows Server コンテナーは、プロセスと名前空間の分離テクノロジを使用してアプリケーションの分離を提供します。 Windows Server コンテナーは、コンテナー ホストおよびホストで実行されているすべてのコンテナーとカーネルを共有します。

- HYPER-V コンテナーは、各コンテナーを高度に最適化された仮想マシンで実行することで、Windows Server コンテナーによって提供される分離を拡張します。 この構成では、コンテナー ホストのカーネルは Hyper-V コンテナーと共有されないため、分離性に優れています。

これらのコンテナーのイメージは、同じ方法で作成され、同じように機能します。 違いは、Hyper-V コンテナーを実行しているイメージからコンテナーを作成する方法に、追加のパラメーターが必要な点です。 詳細については、「[Hyper-V コンテナー](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container)」を参照してください。

## <a name="comparing-docker-containers-with-virtual-machines"></a>Docker コンテナーと仮想マシンの比較

図 2-3 は、VM と Docker コンテナーの比較を示しています。

| 仮想マシン | Docker コンテナー |
| -----------------| ------------------|
|![従来の VM のハードウェア/ソフトウェア スタックを示す図。](./media/docker-defined/virtual-machine-hardware-software.png)|![Docker コンテナーのハードウェア/ソフトウェア スタックを示す図。](./media/docker-defined/docker-container-hardware-software.png)|
|仮想マシンには、アプリケーション、必要なライブラリまたはバイナリ、および完全なゲスト オペレーティング システムが含まれます。 完全な仮想化では、コンテナー詰めより多くのリソースが必要です。 | コンテナーには、アプリケーションとそのすべての依存関係が含まれます。 ただし、OS カーネルは他のコンテナーと共有され、ホスト オペレーティング システム上のユーザー空間内で分離されたプロセスとして実行されます (コンテナーごとに特別な仮想マシン内で実行される Hyper-V コンテナーは例外です)。 |

**図 2-3** 従来の仮想マシンと Docker コンテナーの比較

VM の場合、ホスト サーバーに 3 つの基本レイヤーがあります。下からインフラストラクチャ、ホスト オペレーティング システム、ハイパーバイザーです。また、それらすべての上位には、各 VM の OS とすべての必要なライブラリがあります。 Docker の場合、ホスト サーバーにはインフラストラクチャと OS のみがあり、その上位には、コンテナー エンジンがあります。これで、コンテナーの分離が維持され、さらにベースの OS サービスが共有されます。

コンテナーに必要なリソースははるかに少ないため (たとえば、完全な OS は必要ありません)、導入が簡単で、すぐに開始することができます。 そのため、密度を高めることができます。つまり、同じハードウェア ユニットでより多くのサービスを実行できるため、コストを削減できます。

同じカーネル上で実行することの副作用として、VM よりも分離度が低くなります。

イメージの主な目的は、異なる展開間で同じ環境 (依存関係) にすることです。 自分のコンピューターでデバッグし、同じ環境が保証されている別のコンピューターに展開できます。

コンテナー イメージは、アプリやサービスをパッケージ化し、信頼性が高く、再現可能な方法で展開する方法です。 Docker はテクノロジであるだけでなく、哲学やプロセスとも言うことができます。

Docker を使用すると、「自分のマシンでは動作するのに運用環境で動作しないのはなぜだ」と言う開発者の言葉を聞くことはありません。 単に「Docker で動作する」と言うことができます。これは、パッケージ化された Docker アプリケーションは、サポートされている任意の Docker 環境で動作し、すべての展開ターゲット (開発、QA、ステージング、運用など) 上で意図したとおりに動作するためです。

## <a name="a-simple-analogy"></a>簡単な例え

おそらく、簡単な例えで Docker の中核となる概念を理解できます。

少しの間、1950 年代を振り返ってみましょう。 ワード プロセッサはなく、(ほぼ) あらゆる場所でコピー機が使用されていました。

たとえば、必要に応じて多数の手紙を迅速に発行し、顧客に郵送する業務を担当しているとします。実際の紙と封筒を使用して、各顧客の住所に物理的に送付する業務です (当時、電子メールはありませんでした)。

あるとき、手紙は、多数の段落の単なる組み合わせであることに気づきます。手紙の目的に従って、必要に応じて段落は選択され、配置されます。そこで、大幅な昇級を期待して、短時間で手紙を発行できるシステムを考案することにしました。

システムは単純です。

1. まず 1 枚に 1 つの段落が記載された透明なシートのデッキを用意します。

2. 手紙のセットを発行するには、必要な段落が記載されたシートを選択し、見た目がよく、読みやすいように積み重ねて配置します。

3. 最後に、そのセットをコピー機に置き、開始ボタンを押して必要な数の手紙を作成します。

簡単に言うと、これが Docker の中核となるアイデアです。

Docker の各レイヤーは、プログラムのインストールなどのコマンドを実行した後に、結果としてファイルシステムに加えられる変更のセットです。

そのため、レイヤーがコピーされた後にファイルシステムを "見る" と、プログラムのインストール時にレイヤーに追加されたすべてのファイルが表示されます。

イメージは、オペレーティング システムが既にインストールされている "コンピューター" にインストールすることができる、補助的な読み取り専用ハード ディスクと考えることができます。

同様に、コンテナーは、イメージ ハード ディスクがインストールされている "コンピューター" と考えることができます。 コンテナーは、コンピューターと同様に、電源をオンまたはオフにすることができます。

>[!div class="step-by-step"]
>[前へ](index.md)
>[次へ](docker-terminology.md)