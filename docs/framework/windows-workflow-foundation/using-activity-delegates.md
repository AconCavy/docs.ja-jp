---
title: アクティビティ デリゲートの使用
ms.date: 03/30/2017
ms.assetid: e33cf876-8979-440b-9b23-4a12d1139960
ms.openlocfilehash: 63f550549456404b237067c98afdb18a8758dd7a
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989093"
---
# <a name="using-activity-delegates"></a>アクティビティ デリゲートの使用
アクティビティ デリゲートを使用すると、アクティビティの作成者は、特定の署名を持つコールバックを公開できます。アクティビティのユーザーは、この署名用のアクティビティベースのハンドラーを提供できます。 2 種類のアクティビティ デリゲートを使用できます。<xref:System.Activities.ActivityAction%601> は、戻り値を持たないアクティビティ デリゲートを定義する場合に使用され、<xref:System.Activities.ActivityFunc%601> は戻り値を持つアクティビティ デリゲートを定義する場合に使用されます。

アクティビティ デリゲートは、子アクティビティが特定の署名を持つように制限する必要がある場合に便利です。 たとえば、<xref:System.Activities.Statements.While> アクティビティは制約のないあらゆる型のアクティビティを含めることができますが、<xref:System.Activities.Statements.ForEach%601> アクティビティの本体は <xref:System.Activities.ActivityAction%601> であるため、最終的には <xref:System.Activities.Statements.ForEach%601> によって実行されるその子アクティビティは、<xref:System.Activities.InArgument%601> が列挙するコレクションのメンバーと同じ型である <xref:System.Activities.Statements.ForEach%601> を持つ必要があります。

## <a name="using-activityaction"></a>ActivityAction の使用

いくつかの [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] アクティビティ (<xref:System.Activities.Statements.Catch> アクティビティや <xref:System.Activities.Statements.ForEach%601> アクティビティなど) では、アクティビティ アクションが使用されます。 それぞれの場合において、アクティビティ アクションは、これらのアクティビティのいずれかを使用してワークフローを作成するときに、ワークフローの作成者が目的の動作を提供するアクティビティを指定する場所を表します。 次の例では、<xref:System.Activities.Statements.ForEach%601> アクティビティを使用してコンソール ウィンドウにテキストを表示します。 <xref:System.Activities.Statements.ForEach%601> の本体は、<xref:System.Activities.ActivityAction%601> の型 (文字列) に一致する <xref:System.Activities.Statements.ForEach%601> を使用して指定します。 <xref:System.Activities.Statements.WriteLine> で指定された <xref:System.Activities.ActivityDelegate.Handler%2A> アクティビティには、<xref:System.Activities.Statements.WriteLine.Text%2A> アクティビティによって反復処理されるコレクションの文字列値にバインドされる <xref:System.Activities.Statements.ForEach%601> 引数があります。

[!code-csharp[CFX_ActivityExample#6](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#6)]

actionArgument は、コレクション内の各項目を WriteLine にフローするために使用されます。 このワークフローが呼び出されると、次の出力がコンソールに表示されます。

```console
HelloWorld.
```

このトピックの例では、オブジェクトの初期化の構文を使用します。 オブジェクトの初期化の構文は、コードでワークフロー定義を作成する場合に便利な方法です。これは、ワークフローのアクティビティの階層ビューが提供され、アクティビティ間の関係が示されるためです。 プログラムからワークフローを作成する場合に、オブジェクトの初期化の構文を使用しなければならないという要件はありません。 次の例は、機能的には前のサンプルと同じです。

[!code-csharp[CFX_ActivityExample#7](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#7)]

オブジェクト初期化子の詳細について[は、「」を参照してください。コンストラクターを呼び出さずにオブジェクトC#を初期化する](https://go.microsoft.com/fwlink/?LinkId=161015) ( [プログラミングガイド) と方法:オブジェクト初期化子](https://go.microsoft.com/fwlink/?LinkId=161016)を使用してオブジェクトを宣言します。

次の例では、ワークフローで <xref:System.Activities.Statements.TryCatch> アクティビティを使用します。 ワークフローによって <xref:System.ApplicationException> がスローされ、<xref:System.Activities.Statements.Catch%601> アクティビティによってこの例外が処理されます。 アクティビティのアクティビティアクション<xref:System.Activities.Statements.Catch%601>のハンドラー <xref:System.Activities.Statements.WriteLine>はアクティビティで<xref:System.Activities.DelegateInArgument%601>あり、例外の詳細はを使用し`ex`てそれにフローされます。

[!code-csharp[CFX_WorkflowApplicationExample#33](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#33)]

<xref:System.Activities.ActivityAction%601> を定義するカスタム アクティビティを作成する場合は、<xref:System.Activities.Statements.InvokeAction%601> を使用して <xref:System.Activities.ActivityAction%601> の呼び出しをモデル化します。 次の例では、カスタムの `WriteLineWithNotification` アクティビティを定義します。 このアクティビティは、<xref:System.Activities.Statements.Sequence> アクティビティが含まれ、その後に 1 つの文字列引数を取る <xref:System.Activities.Statements.WriteLine> を呼び出す <xref:System.Activities.Statements.InvokeAction%601> が続く <xref:System.Activities.ActivityAction%601> で構成されます。

[!code-csharp[CFX_ActivityExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#1)]

`WriteLineWithNotification` アクティビティを使用してワークフローを作成する場合、ワークフローの作成者は、アクティビティ アクションの <xref:System.Activities.ActivityDelegate.Handler%2A> で必要なカスタム ロジックを指定します。 次の例では、`WriteLineWithNotification` アクティビティを使用してワークフローを作成し、<xref:System.Activities.Statements.WriteLine> として <xref:System.Activities.ActivityDelegate.Handler%2A> アクティビティを使用します。

[!code-csharp[CFX_ActivityExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#2)]

1 つ以上の引数を渡すために <xref:System.Activities.Statements.InvokeAction%601> および <xref:System.Activities.ActivityAction%601> のジェネリック バージョンが複数用意されています。

## <a name="using-activityfunc"></a>ActivityFunc の使用

<xref:System.Activities.ActivityAction%601> はアクティビティから結果値が返されない場合に役立ち、<xref:System.Activities.ActivityFunc%601> は結果値が返される場合に使用されます。 <xref:System.Activities.ActivityFunc%601> を定義するカスタム アクティビティを作成する場合は、<xref:System.Activities.Expressions.InvokeFunc%601> を使用して <xref:System.Activities.ActivityFunc%601> の呼び出しをモデル化します。 次の例では、 `WriteFillerText` アクティビティを定義します。 充てんテキストを提供するために、整数の引数を取って文字列の結果を持つ <xref:System.Activities.Expressions.InvokeFunc%601> を指定します。 充てんテキストが取得されると、<xref:System.Activities.Statements.WriteLine> アクティビティを使用してコンソールに表示されます。

[!code-csharp[CFX_ActivityExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#3)]

テキストを提供するには、`int` の引数を 1 つ取って文字列の結果を持つアクティビティを使用する必要があります。 次の例では、これらの要件を満たす `TextGenerator` アクティビティを示します。

[!code-csharp[CFX_ActivityExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#4)]

`TextGenerator` アクティビティと `WriteFillerText` アクティビティを一緒に使用するには、<xref:System.Activities.ActivityDelegate.Handler%2A> として指定します。

[!code-csharp[CFX_ActivityExample#5](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#5)]
