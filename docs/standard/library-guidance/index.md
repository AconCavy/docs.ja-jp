---
title: オープン ソース .NET ライブラリのガイダンス
description: 高品質の .NET ライブラリを作成するための開発者向けのベスト プラクティスとしての推奨事項。
author: jamesnk
ms.author: mairaw
ms.date: 10/17/2018
ms.openlocfilehash: eff6c822757af6fb85622e88714accd40c32bcf5
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928957"
---
# <a name="open-source-library-guidance"></a>オープン ソース ライブラリのガイダンス

このガイドでは、高品質の .NET ライブラリを作成するための開発者向け推奨事項を説明します。 このドキュメントでは、.NET ライブラリを構築するときの、"*方法*" ではなく、"*内容*" と "*理由*" について説明します。

高品質のオープン ソースの .NET ライブラリの特徴:

> [!div class="checklist"]
>
> * **包括的である** - 多くのプラットフォーム、プログラミング言語、アプリケーションをサポートするように、適切な .NET ライブラリで対応しています。
> * **安定している** - 適切な .NET ライブラリが .NET エコシステム内で共存しており、多くのライブラリを使用してビルドされたアプリケーション内で実行されます。
> * **進化するように設計されている** - .NET ライブラリは、既存のユーザーをサポートしながら、時間の経過と共に改善され進化します。
> * **デバッグできる** - .NET ライブラリでは、最新のツールを使用してユーザー向けの優れたデバッグ エクスペリエンスが作成されます。
> * **信頼されている** - .NET ライブラリは、セキュリティのベスト プラクティスを使用して NuGet に発行することにより、開発者から信頼されています。

> [!div class="nextstepaction"]
> [開始するには](./get-started.md)

## <a name="types-of-recommendations"></a>推奨事項の種類

各記事で 4 種類のレコメンデーションが提示されます:**実施**、**検討**、**回避**、**実施しない**です。 推奨事項の種類によって、その推奨設定にどの程度厳密に従う必要があるかが示されます。

**実施**の推奨事項にはほとんど常に従う必要があります。 次に例を示します。

NuGet パッケージを使用してご利用のライブラリの配布を **✔️ 実施**してください。

その一方で、**検討**推奨事項は、一般に実施する必要がありますが、ルールには正当な例外があり、ガイダンスに従っていないことを気する必要はありません。

ご利用の NuGet パッケージのバージョンに [SemVer 2.0.0](https://semver.org/) を使用することを **✔️ 検討**してください。

**回避**の推奨事項は一般には良いアイデアではありませんが、規則に違反することが効果的である場合があります。

正確なバージョンを要求する NuGet パッケージは **❌ 回避**してください。

最後に、**実施しない**の推奨事項は、ほとんどの場合でやってはいけないことを示しています。

ご利用のライブラリに関して厳密な名前が指定されたバージョンおよび厳密でない名前が指定されたバージョンの発行は **❌ 実施しない**でください。 たとえば、`Contoso.Api` と`Contoso.Api.StrongNamed` です。

>[!div class="step-by-step"]
>[次へ](get-started.md)