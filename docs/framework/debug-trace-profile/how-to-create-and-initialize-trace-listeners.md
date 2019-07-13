---
title: '方法: トレース リスナーを作成し初期化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- initializing trace listeners
- trace listeners, creating
- trace listeners, initializing
- tracing [.NET Framework], trace listeners
- logs, trace listeners
ms.assetid: 21726de1-61ee-4fdc-9dd0-3be49324d066
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ea5db2ba1060479f55bbd7f67266d36085a2535f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754376"
---
# <a name="how-to-create-and-initialize-trace-listeners"></a>方法: トレース リスナーを作成し初期化する

<xref:System.Diagnostics.Debug?displayProperty=nameWithType> クラスと <xref:System.Diagnostics.Trace?displayProperty=nameWithType> クラスは、メッセージの受け取りと処理を実行する、リスナーと呼ばれるオブジェクトにメッセージを送ります。 トレースまたはデバッグを有効にすると、こうしたリスナーの 1 つである <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType> が自動的に作成および初期化されます。 <xref:System.Diagnostics.Trace> または <xref:System.Diagnostics.Debug> の出力を別のソースに送るには、別のトレース リスナーを作成して初期化する必要があります。

作成するリスナーには、アプリケーションのニーズが反映されている必要があります。 たとえば、すべてのトレース出力のテキスト レコードが必要である場合は、有効になったときにすべての出力を新しいテキスト ファイルに書き込む <xref:System.Diagnostics.TextWriterTraceListener> リスナーを作成します。 一方、アプリケーションの実行時にのみ出力を表示する場合は、すべての出力をコンソール ウィンドウに送る <xref:System.Diagnostics.ConsoleTraceListener> リスナーを作成します。 <xref:System.Diagnostics.EventLogTraceListener> は、トレース出力をイベント ログに転送することができます。 詳細については、「[トレース リスナー](../../../docs/framework/debug-trace-profile/trace-listeners.md)」を参照してください。

トレース リスナーは、[アプリケーション構成ファイル](../../../docs/framework/configure-apps/index.md)またはコードで作成できます。 アプリケーション構成ファイルではコードを変更せずにトレース リスナーを追加、変更、または削除できるので、アプリケーション構成ファイルを使用することをお勧めします。

### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a>構成ファイルを使用してトレース リスナーを作成して使用するには

1. アプリケーション構成ファイルでトレース リスナーを宣言します。 作成しているリスナーで他のオブジェクトが必要な場合は、必要なオブジェクトも宣言します。 テキスト ファイル `TextWriterOutput.log` への書き込みを実行する `myListener` というリスナーの作成方法を次の例に示します。

    ```xml
    <configuration>
      <system.diagnostics>
        <trace autoflush="false" indentsize="4">
          <listeners>
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="TextWriterOutput.log" />
            <remove name="Default" />
          </listeners>
        </trace>
      </system.diagnostics>
    </configuration>
    ```

2. コードで <xref:System.Diagnostics.Trace> クラスを使用して、メッセージをトレース リスナーに書き込みます。

    ```vb
    Trace.TraceInformation("Test message.")
    ' You must close or flush the trace to empty the output buffer.
    Trace.Flush()
    ```

    ```csharp
    Trace.TraceInformation("Test message.");
    // You must close or flush the trace to empty the output buffer.
    Trace.Flush();
    ```

### <a name="to-create-and-use-a-trace-listener-in-code"></a>コードでトレース リスナーを作成して使用するには

- トレース リスナーを <xref:System.Diagnostics.Trace.Listeners%2A> コレクションに追加し、トレース情報をリスナーに送ります。

    ```vb
    Trace.Listeners.Add(New TextWriterTraceListener("TextWriterOutput.log", "myListener"))
    Trace.TraceInformation("Test message.")
    ' You must close or flush the trace to empty the output buffer.
    Trace.Flush()
    ```

    ```csharp
    Trace.Listeners.Add(new TextWriterTraceListener("TextWriterOutput.log", "myListener"));
    Trace.TraceInformation("Test message.");
    // You must close or flush the trace to empty the output buffer.
    Trace.Flush();
    ```

    \- または -

- リスナーがトレース出力を受け取らないようにするには、リスナーを <xref:System.Diagnostics.Trace.Listeners%2A> コレクションに追加しないようにします。 リスナー自体の出力メソッドを呼び出すことにより、<xref:System.Diagnostics.Trace.Listeners%2A> コレクションから独立したリスナーを通じて出力を生成できます。 <xref:System.Diagnostics.Trace.Listeners%2A> コレクションに属さないリスナーに行を書き込む方法を次の例に示します。

    ```vb
    Dim myListener As New TextWriterTraceListener("TextWriterOutput.log", "myListener")
    myListener.WriteLine("Test message.")
    ' You must close or flush the trace listener to empty the output buffer.
    myListener.Flush()
    ```

    ```csharp
    TextWriterTraceListener myListener = new TextWriterTraceListener("TextWriterOutput.log", "myListener");
    myListener.WriteLine("Test message.");
    // You must close or flush the trace listener to empty the output buffer.
    myListener.Flush();
    ```

## <a name="see-also"></a>関連項目

- [トレース リスナー](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [トレース スイッチ](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [方法: アプリケーション コードにトレース ステートメントを追加します。](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [アプリケーションのトレースとインストルメント](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
