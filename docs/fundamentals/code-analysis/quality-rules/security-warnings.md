---
title: セキュリティ規則 (コード分析)
description: コード分析のセキュリティ規則について説明します。
ms.date: 10/02/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.securityrules
helpviewer_keywords:
- security [Visual Studio ALM], Enterprise Templates
- security rules
- managed code analysis rules, security rules
- rules, security
author: gewarren
ms.author: gewarren
ms.openlocfilehash: e907905b065d786fc8b3c370fb2d2e2b19e62a2b
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2020
ms.locfileid: "96594085"
---
# <a name="security-rules"></a>セキュリティ規則

セキュリティ規則は、より安全なライブラリとアプリケーションをサポートします。 これらの規則は、プログラムのセキュリティの欠陥を防ぐのに役立ちます。 これらの規則のいずれかを無効にする場合は、コードで理由を明確にマークし、開発プロジェクトの指定されたセキュリティ担当者にも通知する必要があります。

## <a name="in-this-section"></a>このセクションの内容

|ルール|説明|
|----------|-----------------|
|[CA2100:SQL クエリのセキュリティ脆弱性を確認](ca2100.md)|メソッドに渡された文字列引数から構築された文字列を使用して System.Data.IDbCommand.CommandText プロパティが設定されています。 この規則では、文字列引数にユーザー入力が含まれていることが想定されています。 ユーザー入力から構築された SQL コマンド文字列には、SQL 注入攻撃に対する脆弱性があります。|
|[CA2109:表示するイベント ハンドラーを確認します](ca2109.md)|パブリックまたはプロテクトのイベント ハンドラー メソッドが検出されました。 イベント ハンドラー メソッドは、絶対に必要な場合を除き公開しないでください。|
|[CA2119:プライベート インターフェイスを満たすメソッドをシールします](ca2119.md)|継承可能なパブリック型により、internal (Visual Basic では Friend) インターフェイスのオーバーライド可能なメソッド実装が提供されます。 この規則違反を修正するには、アセンブリの外側でメソッドがオーバーライドされないようにします。|
|[CA2153:破損状態例外の処理を回避する](ca2153.md)|[破損状態例外 (CSE)](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions) は、メモリの破損がプロセス内に存在していることを示します。 プロセスをクラッシュさせるのではなくこれらの例外をキャッチすることは、攻撃者が破損したメモリ領域にセキュリティ上の弱点を見出すことができた場合に、セキュリティ上の脆弱性となる可能性があります。|
|[CA2300:安全ではないデシリアライザー BinaryFormatter を使用しないでください](ca2300.md)|安全でないデシリアライザーは、信頼できないデータを逆シリアル化するときに脆弱です。 攻撃者は、悪意のある副作用を持つオブジェクトを挿入するために、シリアル化されたデータを変更し、予期しない型を含めることができます。|
|[CA2301:最初に BinaryFormatter.Binder を設定しないで BinaryFormatter.Deserialize を呼び出さないでください](ca2301.md)|安全でないデシリアライザーは、信頼できないデータを逆シリアル化するときに脆弱です。 攻撃者は、悪意のある副作用を持つオブジェクトを挿入するために、シリアル化されたデータを変更し、予期しない型を含めることができます。|
|[CA2302:BinaryFormatter.Deserialize を呼び出す前に BinaryFormatter.Binder が設定されていることを確認します](ca2302.md)|安全でないデシリアライザーは、信頼できないデータを逆シリアル化するときに脆弱です。 攻撃者は、悪意のある副作用を持つオブジェクトを挿入するために、シリアル化されたデータを変更し、予期しない型を含めることができます。|
|[CA2305:安全ではないデシリアライザー LosFormatter を使用しないでください](ca2305.md)|安全でないデシリアライザーは、信頼できないデータを逆シリアル化するときに脆弱です。 攻撃者は、悪意のある副作用を持つオブジェクトを挿入するために、シリアル化されたデータを変更し、予期しない型を含めることができます。|
|[CA2310:安全ではないデシリアライザー NetDataContractSerializer を使用しないでください](ca2310.md)|安全でないデシリアライザーは、信頼できないデータを逆シリアル化するときに脆弱です。 攻撃者は、悪意のある副作用を持つオブジェクトを挿入するために、シリアル化されたデータを変更し、予期しない型を含めることができます。|
|[CA2311:最初に NetDataContractSerializer.Binder を設定しないで逆シリアル化しないでください](ca2311.md)|安全でないデシリアライザーは、信頼できないデータを逆シリアル化するときに脆弱です。 攻撃者は、悪意のある副作用を持つオブジェクトを挿入するために、シリアル化されたデータを変更し、予期しない型を含めることができます。|
|[CA2312:NetDataContractSerializer.Binder を設定してから逆シリアル化してください](ca2312.md)|安全でないデシリアライザーは、信頼できないデータを逆シリアル化するときに脆弱です。 攻撃者は、悪意のある副作用を持つオブジェクトを挿入するために、シリアル化されたデータを変更し、予期しない型を含めることができます。|
|[CA2315:安全ではないデシリアライザー ObjectStateFormatter を使用しないでください](ca2315.md)|安全でないデシリアライザーは、信頼できないデータを逆シリアル化するときに脆弱です。 攻撃者は、悪意のある副作用を持つオブジェクトを挿入するために、シリアル化されたデータを変更し、予期しない型を含めることができます。|
|[CA2321:SimpleTypeResolver を使って JavaScriptSerializer で逆シリアル化しないでください](ca2321.md)|安全でないデシリアライザーは、信頼できないデータを逆シリアル化するときに脆弱です。 攻撃者は、悪意のある副作用を持つオブジェクトを挿入するために、シリアル化されたデータを変更し、予期しない型を含めることができます。|
|[CA2322:逆シリアル化する前に JavaScriptSerializer が SimpleTypeResolver によって初期化されていないことを確認してください](ca2322.md)|安全でないデシリアライザーは、信頼できないデータを逆シリアル化するときに脆弱です。 攻撃者は、悪意のある副作用を持つオブジェクトを挿入するために、シリアル化されたデータを変更し、予期しない型を含めることができます。|
|[CA2326: None 以外の TypeNameHandling 値は使用しないでください](ca2326.md)|安全でないデシリアライザーは、信頼できないデータを逆シリアル化するときに脆弱です。 攻撃者は、悪意のある副作用を持つオブジェクトを挿入するために、シリアル化されたデータを変更し、予期しない型を含めることができます。|
|[CA2327: 安全でない JsonSerializerSettings を使用しないでください](ca2327.md)|安全でないデシリアライザーは、信頼できないデータを逆シリアル化するときに脆弱です。 攻撃者は、悪意のある副作用を持つオブジェクトを挿入するために、シリアル化されたデータを変更し、予期しない型を含めることができます。|
|[CA2328: JsonSerializerSettings が安全であることを確認してください](ca2328.md)|安全でないデシリアライザーは、信頼できないデータを逆シリアル化するときに脆弱です。 攻撃者は、悪意のある副作用を持つオブジェクトを挿入するために、シリアル化されたデータを変更し、予期しない型を含めることができます。|
|[CA2329: セキュリティで保護されていない構成が JsonSerializer で使用されている場合は、逆シリアル化を行わないでください](ca2329.md)|安全でないデシリアライザーは、信頼できないデータを逆シリアル化するときに脆弱です。 攻撃者は、悪意のある副作用を持つオブジェクトを挿入するために、シリアル化されたデータを変更し、予期しない型を含めることができます。|
|[CA2330: 逆シリアル化の際に、JsonSerializer の構成は確実にセキュリティで保護してください](ca2330.md)|安全でないデシリアライザーは、信頼できないデータを逆シリアル化するときに脆弱です。 攻撃者は、悪意のある副作用を持つオブジェクトを挿入するために、シリアル化されたデータを変更し、予期しない型を含めることができます。|
|[CA2350:DataTable.ReadXml() の入力が信頼されていることを確認してください](ca2350.md)|信頼されていない入力を使用してを逆シリアル化すると <xref:System.Data.DataTable> 、攻撃者は悪意のある入力を行ってサービス拒否攻撃を仕掛けることができます。 不明なリモートコード実行の脆弱性がある可能性があります。|
|[CA2351:DataSet.ReadXml() の入力が信頼されていることを確認してください](ca2351.md)|信頼されていない入力を使用してを逆シリアル化すると <xref:System.Data.DataSet> 、攻撃者は悪意のある入力を行ってサービス拒否攻撃を仕掛けることができます。 不明なリモートコード実行の脆弱性がある可能性があります。|
|[CA2352: 安全でないデータセットまたはシリアル化可能な型の DataTable は、リモートのコード実行攻撃に対して脆弱になる可能性があります](ca2352.md)|でマークされたクラスまたは構造体に、 <xref:System.SerializableAttribute> フィールドまたはプロパティが含まれてい <xref:System.Data.DataSet> ますが、が <xref:System.Data.DataTable> ありません <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> 。|
|[CA2353: Unsafe データセットまたはシリアル化可能な型の DataTable](ca2353.md)|XML シリアル化属性またはデータコントラクト属性でマークされたクラスまたは構造体に、フィールドまたはプロパティが含まれてい <xref:System.Data.DataSet> <xref:System.Data.DataTable> ます。|
|[CA2354:逆シリアル化されたオブジェクト グラフの安全でない DataSet または DataTable は、リモート コード実行攻撃に対して脆弱になる可能性があります](ca2354.md)|シリアル化されたを使用して逆シリアル <xref:System.Runtime.Serialization.IFormatter?displayProperty=nameWithType> 化すると、キャストされた型のオブジェクトグラフにまたはを含めることができ <xref:System.Data.DataSet> <xref:System.Data.DataTable> ます。|
|[CA2355:逆シリアル化されたオブジェクト グラフの安全でない DataSet または DataTable](ca2355.md)|キャストまたは指定された型のオブジェクトグラフがまたはを含むことができる場合、逆シリアル化し <xref:System.Data.DataSet> <xref:System.Data.DataTable> ます。|
|[CA2356: web 逆シリアル化されたオブジェクトグラフ内の安全でないデータセットまたは DataTable](ca2356.md)|またはを持つメソッドには、 <xref:System.Web.Services.WebMethodAttribute?displayProperty=nameWithType> <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> またはを参照できるパラメーターがあり <xref:System.Data.DataSet> <xref:System.Data.DataTable> ます。|
|[CA2361: データセットを含む自動生成されたクラスを確認します。 ReadXml () は信頼されていないデータでは使用されません](ca2361.md)|信頼されていない入力を使用してを逆シリアル化すると <xref:System.Data.DataSet> 、攻撃者は悪意のある入力を行ってサービス拒否攻撃を仕掛けることができます。 不明なリモートコード実行の脆弱性がある可能性があります。|
|[CA2362: 自動生成されたシリアル化可能な型の Unsafe データセットまたは DataTable は、リモートのコード実行攻撃に対して脆弱になる可能性があります](ca2362.md)|で信頼できない入力を逆シリアル <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 化し、逆シリアル化されたオブジェクトグラフにまたはが含まれている場合 <xref:System.Data.DataSet> <xref:System.Data.DataTable> 、攻撃者は悪意のあるペイロードを使用してリモートのコード実行攻撃を行うことができます。|
|[CA3001:SQL インジェクションの脆弱性のコード レビュー](ca3001.md)|信頼されていない入力と SQL コマンドを使用する場合は、SQL インジェクション攻撃に注意してください。 SQL インジェクション攻撃によって、悪意のある SQL コマンドを実行し、アプリケーションのセキュリティと整合性を損なう可能性があります。|
|[CA3002:XSS の脆弱性のコード レビュー](ca3002.md)|Web 要求から信頼されていない入力を処理する場合は、クロスサイトスクリプティング (XSS) 攻撃に注意する必要があります。 XSS 攻撃によって、信頼できない入力が未加工の HTML 出力に挿入され、攻撃者が悪意のあるスクリプトを実行したり、web ページのコンテンツを改ざんしたりする可能性があります。|
|[CA3003:ファイル パス インジェクションの脆弱性のコード レビュー](ca3003.md)|Web 要求から信頼されていない入力を使用する場合は、ファイルへのパスを指定するときにユーザーが制御する入力を使用することに注意してください。|
|[CA3004:情報漏えいの脆弱性のコード レビュー](ca3004.md)|例外情報を公開すると、攻撃者がアプリケーションの内部を調べて、攻撃者が他の脆弱性を悪用するのを支援することができます。|
|[CA3006:プロセス コマンド インジェクションの脆弱性のコード レビュー](ca3006.md)|信頼されていない入力を使用する場合は、コマンドインジェクション攻撃に注意してください。 コマンドインジェクション攻撃は、基になるオペレーティングシステムで悪意のあるコマンドを実行し、サーバーのセキュリティと整合性を損なう可能性があります。|
|[CA3007:オープン リダイレクトの脆弱性のコード レビュー](ca3007.md)|信頼されていない入力を使用する場合は、開いているリダイレクトの脆弱性に注意してください。 攻撃者は、開いているリダイレクトの脆弱性を悪用して、web サイトを使用して正当な URL を表示することができますが、悪意のあるユーザーをフィッシングやその他の悪意のある web ページにリダイレクトする可能性があります。|
|[CA3008:XPath インジェクションの脆弱性のコード レビュー](ca3008.md)|信頼されていない入力を使用する場合は、XPath インジェクション攻撃に注意してください。 信頼されていない入力を使用して XPath クエリを作成すると、攻撃者がクエリを故意に操作して意図しない結果を返すことがあり、場合によってはクエリ対象の XML の内容を開示できます。|
|[CA3009:XML インジェクションの脆弱性のコード レビュー](ca3009.md)|信頼されていない入力を使用する場合は、XML インジェクション攻撃に注意してください。|
|[CA3010:XAML インジェクションの脆弱性のコード レビュー](ca3010.md)|信頼されていない入力を扱う場合は、XAML インジェクション攻撃に注意してください。 XAML は、オブジェクトのインスタンス化と実行を直接表すマークアップ言語です。 つまり、XAML で作成された要素は、システムリソース (ネットワークアクセスやファイルシステム IO など) とやり取りできます。|
|[CA3011:DLL インジェクションの脆弱性のコード レビュー](ca3011.md)|信頼できない入力を使用する場合は、信頼されていないコードを読み込むことに注意してください。 Web アプリケーションが信頼されていないコードを読み込む場合、攻撃者は悪意のある Dll をプロセスに挿入して、悪意のあるコードを実行できる可能性があります。|
|[CA3012:RegEx インジェクションの脆弱性のコード レビュー](ca3012.md)|信頼できない入力を使用する場合は、regex インジェクション攻撃に注意してください。 攻撃者は、regex インジェクションを使用して正規表現を故意に変更したり、regex が意図しない結果に一致するようにしたり、regex が過剰な CPU を消費してサービス拒否攻撃を受ける可能性があります。|
|[CA3061:URL でスキーマを追加しません](ca3061.md)|危険な外部参照が発生する可能性があるため、Add メソッドの unsafe オーバーロードは使用しないでください。|
|[CA3075:安全ではない DTD の処理](ca3075.md)|安全ではない DTDProcessing インスタンスを使用する場合、または外部エンティティ ソースを参照する場合、パーサーは信頼されていない入力を受け入れ、攻撃者に機密情報を漏えいしてしまう可能性があります。|
|[CA3076:安全ではない XSLT スクリプトの実行](ca3076.md)|.NET アプリケーションで XSLT (拡張可能なスタイルシート言語変換) を実行する場合、プロセッサは、攻撃者に機密情報を開示する可能性がある信頼できない URI 参照を解決し、サービス拒否攻撃やクロスサイト攻撃を安全で可能性があります。|
|[CA3077:API のデザイン、XML ドキュメント、および XML テキスト リーダーでの安全ではない処理](ca3077.md)|XMLDocument と XMLTextReader から派生する API をデザインする場合、DtdProcessing にご注意ください。 外部エンティティ ソースを参照または解決したり、XML に安全ではない値を設定したりする場合に、安全ではない DTDProcessing インスタンスを使用すると、情報漏えいにつながる可能性があります。|
|[CA3147:ValidateAntiForgeryToken で動詞ハンドラーをマークします](ca3147.md)|ASP.NET MVC コントローラーを設計するときは、クロスサイトリクエストの偽造攻撃に注意してください。 クロスサイト要求偽造攻撃は、認証されたユーザーから ASP.NET MVC コントローラーに悪意のある要求を送信できます。|
|[CA5350:脆弱な暗号アルゴリズムを使用しないでください](ca5350.md)|現在、さまざまな理由で弱い暗号化アルゴリズムとハッシュ関数が使用されていますが、保護対象のデータの機密性や整合性を保証するためにこれらを使用しないでください。 このルールは、コードで TripleDES、SHA1、または RIPEMD160 アルゴリズムが検出されるとトリガーされます。|
|[CA5351: 破損した暗号アルゴリズムを使用しない](ca5351.md)|破られた暗号アルゴリズムはセキュアであるとは見なされず、それらを使用しないことを強くお勧めします。 このルールは、コードに MD5 ハッシュ アルゴリズムや、DES か RC2 のいずれかの暗号化アルゴリズムが検出されるとトリガーされます。|
|[CA5358:安全ではない暗号モードを使用しないでください](ca5358.md)|安全ではない暗号モードを使用しないでください|
|[CA5359: 証明書の検証を無効にしません](ca5359.md)|証明書は、サーバーの id を認証するのに役立ちます。 クライアントはサーバー証明書を検証して、要求が目的のサーバーに送信されるようにする必要があります。 ServerCertificateValidationCallback が常にを返す場合 `true` 、すべての証明書が検証に合格します。|
|[CA5360: 逆シリアル化で危険なメソッドを呼び出さないでください](ca5360.md)|安全でない逆シリアル化とは、信頼されていないデータを使用してアプリケーションのロジックを不正使用したり、サービス拒否 (DoS) 攻撃を受けたり、逆シリアル化の際に任意のコードを実行したりする場合に発生する脆弱性です。 悪意のあるユーザーが、コントロールの下にある信頼されていないデータを逆シリアル化するときに、これらの逆シリアル化機能を不正使用する可能性があります。 具体的には、逆シリアル化のプロセスで危険なメソッドを呼び出します。 安全に安全でない逆シリアル化攻撃によって、攻撃者は DoS 攻撃、認証バイパス、リモートコード実行などの攻撃を仕掛けることができます。|
|[CA5361: SChannel の強力な暗号の使用を無効にしない](ca5361.md)|`Switch.System.Net.DontEnableSchUseStrongCrypto`をに設定すると `true` 、発信トランスポート層セキュリティ (TLS) 接続で使用される暗号化が弱くなります。 弱い暗号化を使用すると、アプリケーションとサーバーの間の通信の機密性が低下する可能性があるため、攻撃者が機微なデータを簡単に盗聴ことができます。|
|[CA5362: 逆シリアル化されたオブジェクト グラフで可能性のある参照サイクル](ca5362.md)|信頼されていないデータを逆シリアル化する場合、逆シリアル化されたオブジェクトグラフを処理するコードは、無限ループに入ることなく参照サイクルを処理する必要があります。 これには、逆シリアル化のコールバックの一部であるコードと、逆シリアル化の完了後にオブジェクトグラフを処理するコードの両方が含まれます。 そうしないと、攻撃者は参照サイクルを含む悪意のあるデータを使用してサービス拒否攻撃を実行する可能性があります。|
|[CA5363:要求の検証を無効にしません](ca5363.md)|要求の検証は、ASP.NET の機能の1つで、HTTP 要求を調べて、クロスサイトスクリプトを含む注入攻撃につながる可能性がある危険性のあるコンテンツが含まれているかどうかを判断します。|
|[CA5364: 非推奨のセキュリティ プロトコルを使用しないでください](ca5364.md)|トランスポート層セキュリティ (TLS) は、通常、ハイパーテキスト転送プロトコルセキュア (HTTPS) を使用して、コンピューター間の通信をセキュリティで保護します。 Tls の古いプロトコルバージョンは、TLS 1.2 および TLS 1.3 よりも安全性が低く、新しい脆弱性が発生する可能性が高くなります。 リスクを最小限に抑えるために、古いプロトコルバージョンを避けてください。|
|[CA5365: HTTP ヘッダーのチェックを無効にしません](ca5365.md)|HTTP ヘッダーチェックでは、応答ヘッダーに含まれる復帰文字と改行文字 (\r と \n) をエンコードできます。 このエンコーディングは、ヘッダーに含まれる信頼されていないデータをエコーするアプリケーションを悪用する注入攻撃を回避するのに役立ちます。|
|[CA5366: DataSet Read XML に XmlReader を使用します](ca5366.md)|を使用して <xref:System.Data.DataSet> 信頼できないデータを持つ XML を読み取ると、危険な外部参照が読み込まれる可能性があります。これは、 <xref:System.Xml.XmlReader> セキュリティで保護された競合回避モジュールを使用するか、DTD 処理を無効にして制限する必要があり|
|[CA5367: ポインター フィールドを持つ型をシリアル化しません](ca5367.md)|このルールでは、ポインターフィールドまたはプロパティを持つシリアル化可能なクラスがあるかどうかを確認します。 シリアル化できないメンバーは、静的メンバーまたはでマークされたフィールドなどのポインターにすることができ <xref:System.NonSerializedAttribute> ます。|
|[CA5368: ページから派生したクラスに ViewStateUserKey を設定します](ca5368.md)|プロパティを設定する <xref:System.Web.UI.Page.ViewStateUserKey> と、個々のユーザーのビューステート変数に識別子を割り当てて、攻撃者が変数を使用して攻撃を生成できないようにすることで、アプリケーションに対する攻撃を防ぐことができます。 そうしないと、クロスサイト要求の偽造に対する脆弱性が発生します。|
|[CA5369:逆シリアル化に XmlReader を使用します](ca5369.md)|信頼されていない DTD と XML スキーマを処理すると、危険な外部参照を読み込むことができます。これは、セキュリティで保護された競合回避モジュールを使用するか、DTD および XML インラインスキーマ処理を無効にして、XmlReader を使用して制限する|
|[CA5370:読み取りの検証に XmlReader を使用します](ca5370.md)|信頼されていない DTD と XML スキーマを処理すると、危険な外部参照を読み込むことができます。 この危険な読み込みは、セキュリティで保護された競合回避モジュールで XmlReader を使用するか、DTD および XML インラインスキーマ処理を無効にして制限できます。|
|[CA5371:スキーマの読み取りに XmlReader を使用します](ca5371.md)|信頼されていない DTD と XML スキーマを処理すると、危険な外部参照を読み込むことができます。 セキュリティで保護された競合回避モジュールで XmlReader を使用するか、DTD および XML インラインスキーマ処理を使用すると、この制限は無効になります。|
|[CA5372:XPathDocument に XmlReader を使用します](ca5372.md)|信頼されていないデータから XML を処理すると、危険な外部参照が読み込まれる可能性があります。これは、セキュリティで保護された競合回避モジュールを使用するか、DTD 処理を無効にして、XmlReader|
|[CA5373:廃止されたキー派生関数を使用しません](ca5373.md)|このルールは、弱いキー派生メソッドとの呼び出しを検出し <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> `Rfc2898DeriveBytes.CryptDeriveKey` ます。 <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> 弱いアルゴリズム PBKDF1 が使用されていました。|
|[CA5374: XslTransform を使用しません](ca5374.md)|このルール <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> では、がコード内でインスタンス化されているかどうかを確認します。 <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> は互換性のために残されているため、使用しないでください。|
|[CA5375: アカウントの Shared Access Signature を使用しないでください](ca5375.md)|アカウント SAS は、blob コンテナー、テーブル、キュー、およびサービス SAS で許可されていないファイル共有に対する読み取り、書き込み、および削除操作へのアクセスを委任できます。 ただし、コンテナーレベルのポリシーはサポートされておらず、付与されるアクセス許可をより柔軟に制御することはできません。 悪意のあるユーザーがアクセスすると、ストレージアカウントが簡単に侵害されます。|
|[CA5376: SharedAccessProtocol HttpsOnly を使用します](ca5376.md)|SAS は、HTTP でプレーンテキストで転送できない機密データです。|
|[CA5377: コンテナー レベルのアクセス ポリシーを使用します](ca5377.md)|コンテナーレベルのアクセスポリシーは、いつでも変更または失効できます。 これにより、付与されるアクセス許可をより柔軟に制御できるようになります。|
|[CA5378: ServicePointManagerSecurityProtocols を無効にしません](ca5378.md)|`Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols`をに設定すると、 `true` Windows Communication Framework の (WCF) Transport Layer SECURITY (tls) 接続が tls 1.0 を使用するように制限されます。 このバージョンの TLS は非推奨とされます。|
|[CA5379: キー派生関数アルゴリズムが十分に強力であることを確認してください](ca5379.md)|クラスは、 <xref:System.Security.Cryptography.Rfc2898DeriveBytes> 既定でアルゴリズムを使用し <xref:System.Security.Cryptography.HashAlgorithmName.SHA1> ます。 またはそれ以上のコンストラクターの一部のオーバーロードで使用するハッシュアルゴリズムを指定する必要があり <xref:System.Security.Cryptography.HashAlgorithmName.SHA256> ます。 プロパティに <xref:System.Security.Cryptography.Rfc2898DeriveBytes.HashAlgorithm> はアクセサーのみがあり、 `get` 修飾子はありません `overriden` 。|
|[CA5380:ルート ストアに証明書を追加しません](ca5380.md)|このルールは、信頼されたルート証明機関の証明書ストアに証明書を追加するコードを検出します。 既定では、信頼されたルート証明機関の証明書ストアは、Microsoft ルート証明書プログラムの要件を満たしている一連のパブリック Ca で構成されます。|
|[CA5381:証明書がルート ストアに追加されていないことを確認します](ca5381.md)|このルールは、信頼されたルート証明機関の証明書ストアに証明書を追加する可能性のあるコードを検出します。 既定では、信頼されたルート証明機関の証明書ストアは、Microsoft ルート証明書プログラムの要件を満たす公開証明機関 (Ca) のセットを使用して構成されます。|
|[CA5382: ASP.NET Core で安全な Cookie を使用します](ca5382.md)|HTTPS 経由で使用できるアプリケーションでは、セキュリティで保護された cookie を使用する必要があります。これは、cookie がトランスポート層セキュリティ (TLS) を使用してのみ送信されることをブラウザーに示すことを示します。|
|[CA5383: ASP.NET Core で安全な Cookie を使用することを確認します](ca5383.md)|HTTPS 経由で使用できるアプリケーションでは、セキュリティで保護された cookie を使用する必要があります。これは、cookie がトランスポート層セキュリティ (TLS) を使用してのみ送信されることをブラウザーに示すことを示します。|
|[CA5384: デジタル署名アルゴリズム (DSA) を使用しません](ca5384.md)|DSA は、弱い非対称暗号化アルゴリズムです。|
|[CA5385: 十分なキー サイズの Rivest–Shamir–Adleman (RSA) アルゴリズムを使用します](ca5385.md)|RSA キーが2048ビットより小さい場合は、ブルートフォース攻撃に対して脆弱になります。|
|[CA5386: SecurityProtocolType 値のハードコードを避けます](ca5386.md)|トランスポート層セキュリティ (TLS) は、通常、ハイパーテキスト転送プロトコルセキュア (HTTPS) を使用して、コンピューター間の通信をセキュリティで保護します。 Tls 1.2 と TLS 1.3 は最新ではありませんが、プロトコルバージョン TLS 1.0 および TLS 1.1 は非推奨とされます。 今後、TLS 1.2 および TLS 1.3 が非推奨とされる可能性があります。 アプリケーションがセキュリティで保護されていることを確認するには、プロトコルバージョンをハードコーディングし、少なくとも .NET Framework v 4.7.1 をターゲットにするようにします。|
|[CA5387: 反復回数が十分でない弱いキー派生関数は使用しません](ca5387.md)|このルールは、によって暗号化キーが生成されたかどうかを、イテレーション数が10万未満であるかどうかを確認 <xref:System.Security.Cryptography.Rfc2898DeriveBytes> します。 反復回数が多いほど、生成された暗号化キーを推測しようとする辞書攻撃に対する軽減に役立ちます。|
|[CA5388: 弱いキー派生関数を使用する場合は十分な反復回数を確保してください](ca5388.md)|このルールは、によって暗号化キーが生成されたかどうかを、 <xref:System.Security.Cryptography.Rfc2898DeriveBytes> 10万未満の反復回数で確認します。 反復回数が多いほど、生成された暗号化キーを推測しようとする辞書攻撃に対する軽減に役立ちます。|
|[CA5389:アーカイブ項目のパスをターゲット ファイル システム パスに追加しません](ca5389.md)|ファイルパスは相対パスにすることができ、予想されるファイルシステムのターゲットパスの外部でファイルシステムにアクセスする可能性があります。これにより、悪意のある構成の変更や、配置と待機の手法を使用したリモートでのコードの実行が可能になります。|
|[CA5390: 暗号化キーをハードコーディングしません](ca5390.md)|対称アルゴリズムを成功させるには、送信側と受信側だけが秘密キーを認識している必要があります。 キーがハードコーディングされている場合は、簡単に検出できます。 コンパイル済みバイナリでも、悪意のあるユーザーが簡単に抽出できます。 秘密キーが侵害されると、暗号文は直接復号化でき、保護されなくなります。|
|[CA5391: ASP.NET Core MVC コントローラーで偽造防止トークンを使用します](ca5391.md)|偽造防止 `POST` トークンを検証せずに、、、または要求を処理すると、 `PUT` `PATCH` `DELETE` クロスサイト要求偽造攻撃に対して脆弱になる可能性があります。 クロスサイト要求偽造攻撃は、認証されたユーザーから ASP.NET Core MVC コントローラーに悪意のある要求を送信できます。|
|[CA5392: P/Invoke に対して DefaultDllImportSearchPaths 属性を使用します](ca5392.md)|既定では、P/Invoke 関数でプローブを使用して、 <xref:System.Runtime.InteropServices.DllImportAttribute> 読み込むライブラリの現在の作業ディレクトリを含む多数のディレクトリが検出されます。 これは、特定のアプリケーションのセキュリティ上の問題であり、DLL のハイジャックにつながる可能性があります。|
|[CA5393: 安全でない DllImportSearchPath 値を使用しないでください](ca5393.md)|既定の DLL 検索ディレクトリとアセンブリディレクトリに悪意のある DLL が存在する可能性があります。 または、アプリケーションの実行場所によっては、アプリケーションのディレクトリに悪意のある DLL が存在する可能性があります。|
|[CA5394: 安全でないランダム度を使用しません](ca5394.md)|暗号強度の弱い擬似乱数ジェネレーターを使用すると、攻撃者がセキュリティを重視した値が生成されることを予測できます。|
|[CA5395: アクション メソッドの HttpVerb 属性がありません](ca5395.md)|データの作成、編集、削除、またはその他の変更を行うすべてのアクションメソッドは、クロスサイト要求偽造攻撃からの偽造防止属性で保護する必要があります。 GET 操作の実行は、副作用のない安全な操作であり、永続化されたデータを変更することはありません。|
|[CA5396: HttpCookie で HttpOnly を true に設定します](ca5396.md)|多層防御の手段として、セキュリティが重要な HTTP クッキーが HttpOnly としてマークされていることを確認します。 これは、web ブラウザーがスクリプトによる cookie へのアクセスを許可しないことを示します。 挿入された悪意のあるスクリプトは、cookie を盗む一般的な方法です。|
|[CA5397:非推奨の SslProtocols 値を使用しません](ca5397.md)|トランスポート層セキュリティ (TLS) は、通常、ハイパーテキスト転送プロトコルセキュア (HTTPS) を使用して、コンピューター間の通信をセキュリティで保護します。 Tls の古いプロトコルバージョンは、TLS 1.2 および TLS 1.3 よりも安全性が低く、新しい脆弱性が発生する可能性が高くなります。 リスクを最小限に抑えるために、古いプロトコルバージョンを避けてください。|
|[CA5398:ハードコーディングされた SslProtocols 値を回避します](ca5398.md)|トランスポート層セキュリティ (TLS) は、通常、ハイパーテキスト転送プロトコルセキュア (HTTPS) を使用して、コンピューター間の通信をセキュリティで保護します。 Tls 1.2 と TLS 1.3 は最新ではありませんが、プロトコルバージョン TLS 1.0 および TLS 1.1 は非推奨とされます。 今後、TLS 1.2 および TLS 1.3 が非推奨とされる可能性があります。 アプリケーションがセキュリティで保護されていることを確認するには、プロトコルバージョンをハードコーディングしないようにします。|
|[CA5399: HttpClient 証明書失効リストの確認を確実に無効にします](ca5399.md)|失効した証明書は信頼されていません。 攻撃者が悪意のあるデータを渡すか、または HTTPS 通信で機微なデータを盗むために使用される可能性があります。|
|[CA5400: HttpClient 証明書失効リストの確認が無効になっていないことをご確認ください](ca5400.md)|失効した証明書は信頼されていません。 攻撃者が悪意のあるデータを渡すか、または HTTPS 通信で機微なデータを盗むために使用される可能性があります。|
|[CA5401: 既定以外の IV で CreateEncryptor を使用しません](ca5401.md)|対称暗号化では、ディクショナリ攻撃を防ぐために、常に反復不可能な初期化ベクターを使用する必要があります。|
|[CA5402: 既定の IV で CreateEncryptor を使用します](ca5402.md)|対称暗号化では、ディクショナリ攻撃を防ぐために、常に反復不可能な初期化ベクターを使用する必要があります。|
|[CA5403:証明書をハードコーディングしない](ca5403.md)|`data` `rawData` またはコンストラクターのパラメーターまたはパラメーターは <xref:System.Security.Cryptography.X509Certificates.X509Certificate> <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> ハードコーディングされています。|