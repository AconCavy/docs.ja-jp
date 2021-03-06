---
title: 使用規則 (コード分析)
description: コード分析の使用規則について説明します。
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.usagerules
helpviewer_keywords:
- rules, usage
- managed code analysis rules, usage rules
- usage rules
author: gewarren
ms.author: gewarren
ms.openlocfilehash: c8b14d2f92502d5a82e41a322e599745bdcf8b85
ms.sourcegitcommit: a6bd4cad438fe479cbd112eae10f2cd449f06e40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/08/2020
ms.locfileid: "96593527"
---
# <a name="usage-rules"></a>使い方の規則

使用規則は、.NET の適切な使用をサポートします。

## <a name="in-this-section"></a>このセクションの内容

|ルール|説明|
|----------|-----------------|
|[CA1801:使用されていないパラメーターの確認](ca1801.md)|メソッドのシグネチャに、メソッドの本体で使用されていないパラメーターがあります。|
|[CA1816:GC.SuppressFinalize を正しく呼び出します](ca1816.md)|Dispose の実装であるメソッドがを呼び出さないか、 `GC.SuppressFinalize` または呼び出しの実装ではないメソッドである `Dispose` か、 `GC.SuppressFinalize` またはメソッドが `GC.SuppressFinalize` を呼び出し、(Visual Basic) 以外の値を渡してい `this` `Me` ます。|
|[CA2200:スタック詳細を保持するために再度スローします](ca2200.md)|例外が再スローされ、その例外が throw ステートメントで明示的に指定されています。 throw ステートメントで例外を指定して例外が再スローされると、例外をスローした元のメソッドと現在のメソッドの間で呼び出されたメソッドの一覧は失われます。|
|[CA2201:予約された例外の種類を発生させません](ca2201.md)|これにより、元のエラーの検出とデバッグが困難になります。|
|[CA2207:値型のスタティック フィールドのインラインを初期化します](ca2207.md)|値型で明示的な静的コンストラクターを宣言しています。 この規則違反を修正するには、静的データが宣言されたとき、および静的コンストラクターを削除するときに、静的データをすべて初期化します。|
|[CA2208:引数の例外を正しくインスタンス化します](ca2208.md)|ArgumentException またはそのクラスから派生した例外の種類の既定 (パラメーターなし) のコンストラクターに対して呼び出しが行われたか、ArgumentException またはそのクラスから派生した例外の種類のパラメーター付きのコンストラクターに不適切な文字列型の引数が渡されました。|
|[CA2211:非定数フィールドは表示されません](ca2211.md)|定数または読み取り専用ではない静的フィールドは、スレッドセーフではありません。 このようなフィールドへのアクセスは慎重に制御する必要があり、クラスオブジェクトへのアクセスを同期するための高度なプログラミング手法が必要です。|
|[CA2213:破棄可能なフィールドは破棄されなければなりません](ca2213.md)|を実装する型は、 <xref:System.IDisposable?displayProperty=fullName> も実装する型のフィールドを宣言 `IDisposable` します。 `Dispose`フィールドのメソッドが、 `Dispose` 宣言する型のメソッドによって呼び出されていません。|
|[CA2214:コンストラクターのオーバーライド可能なメソッドを呼び出しません](ca2214.md)|コンストラクターが仮想メソッドを呼び出すと、そのメソッドを呼び出すインスタンスのコンストラクターが実行されていない可能性があります。|
|[CA2215:Dispose メソッドが基底クラスの Dispose を呼び出す必要があります](ca2215.md)|型が破棄可能な型から継承する場合は、 `Dispose` 独自のメソッドから基本型のメソッドを呼び出す必要があり `Dispose` ます。|
|[CA2216:破棄可能な型はファイナライザーを宣言しなければなりません](ca2216.md)|を実装し、 <xref:System.IDisposable?displayProperty=fullName> アンマネージリソースの使用を提案するフィールドを持つ型は、「」で説明されているように、ファイナライザーを実装しません `Object.Finalize` 。|
|[CA2217:列挙型を FlagsAttribute に設定しません](ca2217.md)|外部から参照できる列挙体はでマークされ、 `FlagsAttribute` 1 つ以上の値があります。この値は、列挙体で2つまたはその他の定義済みの値の組み合わせにはなりません。|
|[CA2218:オーバーライドする Equals で GetHashCode をオーバーライドします](ca2218.md)|パブリック型はを <xref:System.Object.Equals%2A?displayProperty=fullName> オーバーライドしますが、をオーバーライドしません <xref:System.Object.GetHashCode%2A?displayProperty=fullName> 。|
|[CA2219:exception 句に例外を発生させないでください](ca2219.md)|finally 句または fault 句で例外が発生すると、アクティブな例外が新しい例外によって隠されます。 filter 句で例外が発生すると、ランタイムがその例外を暗黙的にキャッチします。 これにより、元のエラーの検出とデバッグが困難になります。|
|[CA2224:オーバーロードする演算子 equals で Equals をオーバーライドします](ca2224.md)|パブリック型で等値演算子が実装されていますが、オーバーライドされていません <xref:System.Object.Equals%2A?displayProperty=fullName> 。|
|[CA2225:演算子オーバーロードには名前付けされた代替が存在します](ca2225.md)|演算子のオーバーロードが検出され、予想される名前の代替メソッドが検出されませんでした。 名前付き代替メンバーは、演算子と同じ機能へのアクセスを提供し、オーバーロードされた演算子をサポートしない言語でプログラミングする開発者向けに用意されています。|
|[CA2226:演算子は対称型オーバーロードを含まなければなりません](ca2226.md)|型は等値演算子または非等値演算子を実装し、逆の演算子は実装しません。|
|[CA2227:Collection プロパティは読み取り専用でなければなりません](ca2227.md)|書き込み可能なコレクション プロパティにより、ユーザーはコレクションを異なるコレクションで置換できます。 読み取り専用プロパティは、コレクションを置換できないようにしますが、個別のメンバーが設定されることは回避できません。|
|[CA2229:シリアル化コンストラクターを実装します](ca2229.md)|この規則違反を修正するには、シリアル化コンストラクターを実装します。 シールされたクラスの場合、コンストラクターをプライベートにするか、プロテクトにします。|
|[CA2231:ValueType.Equals のオーバーライドで、演算子 equals をオーバーロードします](ca2231.md)|値型はをオーバーライドし `Object.Equals` ますが、等値演算子を実装しません。|
|[CA2234:文字列の代わりに System.Uri オブジェクトを渡します](ca2234.md)|"uri"、"URI"、"urn"、"URN"、"url"、または "URL" という名前を持つ文字列パラメーターが指定されているメソッドに対して、呼び出しが行われました。  メソッドの宣言する型に、パラメーターを持つ対応するメソッドオーバーロードが含まれてい <xref:System.Uri?displayProperty=fullName> ます。|
|[CA2235:すべてのシリアル化不可能なフィールドを設定します](ca2235.md)|シリアル化できない型のインスタンス フィールドが、シリアル化できる型で宣言されています。|
|[CA2237:ISerializable 型を SerializableAttribute に設定します](ca2237.md)|共通言語ランタイムによってシリアル化可能として認識されるようにするには、型がインターフェイスの実装によってカスタムのシリアル化ルーチンを使用する場合でも、型は SerializableAttribute 属性でマークする必要があり `ISerializable` ます。|
|[CA2241:書式設定メソッドに正しい引数を提供](ca2241.md)|に渡された書式引数に、 <xref:System.String.Format%2A?displayProperty=nameWithType> 各オブジェクト引数に対応する書式項目が含まれていません。または、その逆も同様です。|
|[CA2242:NaN に対して正しくテストします](ca2242.md)|この式は、またはに対して値をテストし `Single.Nan` `Double.Nan` ます。 `Single.IsNan(Single)`値をテストするには、またはを使用し `Double.IsNan(Double)` ます。|
|[CA2243:属性文字列リテラルは、正しく解析する必要があります](ca2243.md)|属性の文字列リテラルパラメーターは、URL、GUID、またはバージョンに対して正しく解析されません。|
|[CA2244: インデックス付き要素の初期化を重複させません](ca2244.md)|オブジェクト初期化子に、同じ定数インデックスを持つ複数のインデックス付き要素初期化子があります。 最後の初期化子以外はすべて冗長です。|
|[CA2245: プロパティをそれ自体に割り当てません](ca2245.md)|プロパティが誤ってそれ自体に割り当てられました。|
|[CA2246: 同じステートメントにシンボルとそのメンバーを割り当てません](ca2246.md)|同じステートメントで、シンボルとそのメンバー (フィールドまたはプロパティ) を割り当てることは推奨されていません。 メンバーアクセスが、割り当ての前にシンボルの古い値を使用するのか、またはこのステートメントの代入の新しい値を使用するのかは明確ではありません。|
|[CA2247:TaskCompletionSource コンストラクターに渡された引数は、TaskContinuationOptions 列挙型ではなく、TaskCreationOptions 列挙型にする必要があります](ca2246.md)|Taskて Source には、タスクに格納されているオブジェクトの状態を取得する、基になるタスクとコンストラクターを制御する Task/Options を受け取るコンストラクターがあります。  Task/options ではなく Task続行 Ationoptions を渡した場合、オプションが状態として扱われます。|
|[CA2248: 正しい ' enum ' 引数を ' Enum. HasFlag ' に指定してください](ca2248.md)|メソッド呼び出しの引数として渡された列挙型 `HasFlag` が、呼び出し元の列挙型と異なります。|
|[CA2249:String.IndexOf の代わりに String.Contains を使用することを検討します](ca2249.md)|結果を `string.IndexOf` 使用して部分文字列が存在するかどうかを確認するための呼び出しは、で置き換えることができ `string.Contains` ます。|
