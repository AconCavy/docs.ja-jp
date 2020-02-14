---
title: トレース リスナー
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Listener object types
- listeners
- Trace class, listeners
- trace listeners, about trace listeners
- Listeners collection
- trace listeners
- tracing [.NET Framework], trace listeners
- logs, trace listeners
ms.assetid: 444b0d33-67ea-4c36-9e94-79c50f839025
ms.openlocfilehash: a51c046a296fbb62d21c7784cf7c1e78b700f3e9
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216144"
---
# <a name="trace-listeners"></a><span data-ttu-id="fdbc2-102">トレース リスナー</span><span class="sxs-lookup"><span data-stu-id="fdbc2-102">Trace Listeners</span></span>
<span data-ttu-id="fdbc2-103">**Trace**、**Debug**、および <xref:System.Diagnostics.TraceSource> を使用するときには、送信されたメッセージを収集して記録するための機構が必要です。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-103">When using **Trace**, **Debug** and <xref:System.Diagnostics.TraceSource>, you must have a mechanism for collecting and recording the messages that are sent.</span></span> <span data-ttu-id="fdbc2-104">トレース メッセージは*リスナー*によって受け取られます。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-104">Trace messages are received by *listeners*.</span></span> <span data-ttu-id="fdbc2-105">リスナーの目的は、トレース メッセージを収集し、保存し、ルーティングすることです。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-105">The purpose of a listener is to collect, store, and route tracing messages.</span></span> <span data-ttu-id="fdbc2-106">リスナーは、ログ、ウィンドウ、テキスト ファイルなどの適切なターゲットにトレース出力を送ります。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-106">Listeners direct the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="fdbc2-107">リスナーは、**Debug**、**Trace**、および <xref:System.Diagnostics.TraceSource> の各クラスで使用できます。それらのクラスからも出力を各種のリスナー オブジェクトに送ることができます。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-107">Listeners are available to the **Debug**, **Trace**, and <xref:System.Diagnostics.TraceSource> classes, each of which can send its output to a variety of listener objects.</span></span> <span data-ttu-id="fdbc2-108">一般的に使用される定義済みのリスナーは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-108">The following are the commonly used predefined listeners:</span></span>  
  
- <span data-ttu-id="fdbc2-109"><xref:System.Diagnostics.TextWriterTraceListener> は、<xref:System.IO.TextWriter> クラスのインスタンスまたは <xref:System.IO.Stream> クラスの任意の対象に出力をリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-109">A <xref:System.Diagnostics.TextWriterTraceListener> redirects output to an instance of the <xref:System.IO.TextWriter> class or to anything that is a <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="fdbc2-110">また、コンソールまたはファイルに書き込むこともできます (これらは <xref:System.IO.Stream> クラスなので)。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-110">It can also write to the console or to a file, because these are <xref:System.IO.Stream> classes.</span></span>  
  
- <span data-ttu-id="fdbc2-111"><xref:System.Diagnostics.EventLogTraceListener> は、出力をイベント ログにリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-111">An <xref:System.Diagnostics.EventLogTraceListener> redirects output to an event log.</span></span>  
  
- <span data-ttu-id="fdbc2-112"><xref:System.Diagnostics.DefaultTraceListener> は、**Write** メッセージと **WriteLine** メッセージを **OutputDebugString** と **Debugger.Log** メソッドに出力します。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-112">A <xref:System.Diagnostics.DefaultTraceListener> emits **Write** and **WriteLine** messages to the **OutputDebugString** and to the **Debugger.Log** method.</span></span> <span data-ttu-id="fdbc2-113">Visual Studio では、これによってデバッグ メッセージが [出力] ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-113">In Visual Studio, this causes the debugging messages to appear in the Output window.</span></span> <span data-ttu-id="fdbc2-114">**Fail** メッセージと、失敗した **Assert** メッセージも **OutputDebugString** Windows API と **Debugger.Log** メソッドに出力され、これらはメッセージ ボックスとしても表示されます。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-114">**Fail** and failed **Assert** messages also emit to the **OutputDebugString** Windows API and the **Debugger.Log** method, and also cause a message box to be displayed.</span></span> <span data-ttu-id="fdbc2-115">**DefaultTraceListener** はすべての **コレクションに自動的に取り込まれる唯一のリスナーであるため、この動作は**Debug**メッセージと**Trace`Listeners` メッセージの既定の動作になります。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-115">This behavior is the default behavior for **Debug** and **Trace** messages, because **DefaultTraceListener** is automatically included in every `Listeners` collection and is the only listener automatically included.</span></span>  
  
- <span data-ttu-id="fdbc2-116"><xref:System.Diagnostics.ConsoleTraceListener> は、トレース出力またはデバッグ出力を、標準出力と標準エラー出力ストリームのいずれかに転送します。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-116">A <xref:System.Diagnostics.ConsoleTraceListener> directs tracing or debugging output to either the standard output or the standard error stream.</span></span>  
  
- <span data-ttu-id="fdbc2-117"><xref:System.Diagnostics.DelimitedListTraceListener> は、トレース出力またはデバッグ出力を、テキスト ライター (ストリーム ライターなど) またはストリーム (ファイル ストリームなど) に送ります。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-117">A <xref:System.Diagnostics.DelimitedListTraceListener> directs tracing or debugging output to a text writer, such as a stream writer, or to a stream, such as a file stream.</span></span> <span data-ttu-id="fdbc2-118">トレース出力は、<xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> プロパティによって指定された区切り記号を使用する区切りテキスト形式になっています。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-118">The trace output is in a delimited text format that uses the delimiter specified by the <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> property.</span></span>  
  
- <span data-ttu-id="fdbc2-119"><xref:System.Diagnostics.XmlWriterTraceListener> は、トレース出力またはデバッグ出力を、XML でエンコードされたデータとして <xref:System.IO.TextWriter> または <xref:System.IO.Stream> (<xref:System.IO.FileStream> など) に送ります。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-119">An <xref:System.Diagnostics.XmlWriterTraceListener> directs tracing or debugging output as XML-encoded data to a <xref:System.IO.TextWriter> or to a <xref:System.IO.Stream>, such as a <xref:System.IO.FileStream>.</span></span>  
  
 <span data-ttu-id="fdbc2-120"><xref:System.Diagnostics.DefaultTraceListener> 以外のリスナーが **Debug** 出力、**Trace** 出力、および <xref:System.Diagnostics.TraceSource> 出力を受け取るようにする場合は、目的のリスナーを `Listeners` コレクションに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-120">If you want any listener besides the <xref:System.Diagnostics.DefaultTraceListener> to receive **Debug**, **Trace** and <xref:System.Diagnostics.TraceSource> output, you must add it to the `Listeners` collection.</span></span> <span data-ttu-id="fdbc2-121">詳細については、「[方法 : トレース リスナーを作成し初期化する](how-to-create-and-initialize-trace-listeners.md)」と「[方法 : TraceSource とフィルターをトレース リスナーと共に使用する](how-to-use-tracesource-and-filters-with-trace-listeners.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-121">For more information, see [How to: Create and Initialize Trace Listeners](how-to-create-and-initialize-trace-listeners.md) and [How to: Use TraceSource and Filters with Trace Listeners](how-to-use-tracesource-and-filters-with-trace-listeners.md).</span></span> <span data-ttu-id="fdbc2-122">**Listeners** コレクションのすべてのリスナーは、トレース出力のメソッドから同じメッセージを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-122">Any listener in the **Listeners** collection gets the same messages from the trace output methods.</span></span> <span data-ttu-id="fdbc2-123">たとえば、**TextWriterTraceListener** と **EventLogTraceListener** という 2 つのリスナーを設定したとします。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-123">For example, suppose you set up two listeners: a **TextWriterTraceListener** and an **EventLogTraceListener**.</span></span> <span data-ttu-id="fdbc2-124">各リスナーは同一のメッセージを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-124">Each listener receives the same message.</span></span> <span data-ttu-id="fdbc2-125">この場合、**TextWriterTraceListener** はストリームに出力を送り、**EventLogTraceListener** はイベント ログに出力を送るなどの動作が可能です。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-125">The **TextWriterTraceListener** would direct its output to a stream, and the **EventLogTraceListener** would direct its output to an event log.</span></span>  
  
 <span data-ttu-id="fdbc2-126">出力を **Listeners** コレクションに送る方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-126">The following example shows how to send output to the **Listeners** collection.</span></span>  
  
```vb  
' Use this example when debugging.  
Debug.WriteLine("Error in Widget 42")  
' Use this example when tracing.  
Trace.WriteLine("Error in Widget 42")  
```  
  
```csharp  
// Use this example when debugging.  
System.Diagnostics.Debug.WriteLine("Error in Widget 42");  
// Use this example when tracing.  
System.Diagnostics.Trace.WriteLine("Error in Widget 42");  
```  
  
 <span data-ttu-id="fdbc2-127">デバッグとトレースは、同じ **Listeners** コレクションを共有しています。したがって、リスナー オブジェクトをアプリケーションの **Debug.Listeners** コレクションに追加した場合、そのリスナー オブジェクトは **Trace.Listeners** コレクションにも追加されます。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-127">Debug and trace share the same **Listeners** collection, so if you add a listener object to a **Debug.Listeners** collection in your application, it gets added to the **Trace.Listeners** collection as well.</span></span>  
  
 <span data-ttu-id="fdbc2-128">トレース情報をコンソールに送る場合のリスナーの使用方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-128">The following example shows how to use a listener to send tracing information to a console:</span></span>  
  
```vb  
Trace.Listeners.Clear()  
Trace.Listeners.Add(New TextWriterTraceListener(Console.Out))  
```  
  
```csharp  
System.Diagnostics.Trace.Listeners.Clear();  
System.Diagnostics.Trace.Listeners.Add(  
   new System.Diagnostics.TextWriterTraceListener(Console.Out));  
```  
  
## <a name="developer-defined-listeners"></a><span data-ttu-id="fdbc2-129">開発者が定義するリスナー</span><span class="sxs-lookup"><span data-stu-id="fdbc2-129">Developer-Defined Listeners</span></span>  
 <span data-ttu-id="fdbc2-130">**TraceListener** 基底クラスから継承することにより、独自のリスナーを定義し、カスタマイズされたメソッドで既存のメソッドをオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-130">You can define your own listeners by inheriting from the **TraceListener** base class and overriding its methods with your customized methods.</span></span> <span data-ttu-id="fdbc2-131">開発者が定義するリスナーの作成については、「.NET Framework リファレンス」の「<xref:System.Diagnostics.TraceListener>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-131">For more information on creating developer-defined listeners, see <xref:System.Diagnostics.TraceListener> in the .NET Framework reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdbc2-132">参照</span><span class="sxs-lookup"><span data-stu-id="fdbc2-132">See also</span></span>

- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="fdbc2-133">アプリケーションのトレースとインストルメント</span><span class="sxs-lookup"><span data-stu-id="fdbc2-133">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="fdbc2-134">トレース スイッチ</span><span class="sxs-lookup"><span data-stu-id="fdbc2-134">Trace Switches</span></span>](trace-switches.md)
