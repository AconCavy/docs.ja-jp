---
title: DockerFile で Windows PowerShell コマンドを使用して Windows コンテナー (Docker 標準ベース) を設定する
description: Windows コンテナーで Docker を操作する場合の PowerShell の使用方法について説明します
ms.date: 08/06/2020
ms.openlocfilehash: be30fd4092f51acd4972c05b3c3ccc936aebd884
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539789"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a>DockerFile で Windows PowerShell コマンドを使用して Windows コンテナー (Docker 標準ベース) を設定する

[Windows コンテナー](/virtualization/windowscontainers/about/index)によって、既存の Windows アプリケーションを Docker イメージに変換して、その他の Docker エコシステムと同じツールでそれらをデプロイできます。

Windows コンテナーを使用するには、次の例に示すように、DockerFile で PowerShell コマンドを記述するだけです。

```dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

この例では、Windows PowerShell を使用して、Windows Server Core 基本イメージと IIS をインストールしています。

同様に、Windows PowerShell コマンドを使用して、次に示すように、従来の ASP.NET 4.x および .NET 4.6、またはその他の任意の Windows ソフトウェアなどの追加コンポーネントを設定することもできます。

```dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
>[前へ](visual-studio-tools-for-docker.md)
>[次へ](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
