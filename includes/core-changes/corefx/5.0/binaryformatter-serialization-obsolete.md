---
ms.openlocfilehash: 7cb146d19486618a4cee9976abe2220ea4b72790
ms.sourcegitcommit: d337df55f83325918cbbd095eb573400bea49064
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2020
ms.locfileid: "88203996"
---
### <a name="binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps"></a>BinaryFormatter シリアル化メソッドが古い形式になり、ASP.NET アプリでは使用不可に

<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>、<xref:System.Runtime.Serialization.Formatter>、および <xref:System.Runtime.Serialization.IFormatter> の `Serialize` メソッドと `Deserialize` メソッドが古い形式になりました。 また、ASP.NET アプリでは、<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> のシリアル化が既定で禁止されます。

#### <a name="change-description"></a>変更の説明

<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> の[セキュリティ脆弱性](../../../../docs/standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities)により、次のメソッドは古い形式になりました。 また、ASP.NET Core 5.0 以降のアプリでは、Web アプリによって <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 機能が再有効化されていない限り、<xref:System.NotSupportedException> がスローされます。

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>

.NET エコシステム内における <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> の使用を段階的に縮小するための取り組みの一環として、これらのメソッドが古い形式としてマークされています。

次のシリアル化メソッドも古い形式になりましたが、動作変更はありません。

- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

#### <a name="version-introduced"></a>導入されたバージョン

5.0 Preview 8

#### <a name="recommended-action"></a>推奨アクション

- コードでの <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> の使用を停止してください。 代わりに、<xref:System.Text.Json.JsonSerializer> または <xref:System.Xml.Serialization.XmlSerializer> の使用を検討してください。 詳しくは、「[BinaryFormatter セキュリティ ガイド](../../../../docs/standard/serialization/binaryformatter-security-guide.md)」をご覧ください。

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> のコンパイル時の警告 (`SYSLIB0011`) を一時的に抑制することができます。 このオプションを選択する前に、リスクについてコードを十分に評価することをお勧めします。 警告を抑制する最も簡単な方法は、個々の呼び出しサイトを `#pragma` ディレクティブで囲むことです。

  ```csharp
  // Now read the purchase order back from disk
  using (var readStream = new FileStream("myfile.bin", FileMode.Open))
  {
      var formatter = new BinaryFormatter();
  #pragma warning disable SYSLIB0011
      return (PurchaseOrder)formatter.Deserialize(readStream);
  #pragma warning restore SYSLIB0011
  }
  ```

  また、プロジェクト ファイルで警告を抑制することもできます。

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "BinaryFormatter is obsolete" warnings for entire project -->
    <NoWarn>$(NoWarn);SYSLIB0011</NoWarn>
  </PropertyGroup>
  ```

  プロジェクト ファイルで警告を抑制すると、プロジェクト内のすべてのコード ファイルに対して警告が抑制されます。 SYSLIB0011 を抑制しても、他の古い API の使用によって発生した警告は抑制されません。

- ASP.NET アプリで引き続き <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> を使用する場合は、プロジェクト ファイルで再有効化することができます。 ただし、そうしないことを強くお勧めします。 詳しくは、「[BinaryFormatter セキュリティ ガイド](../../../../docs/standard/serialization/binaryformatter-security-guide.md)」をご覧ください。

  ```xml
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Warning: Setting the following switch is *NOT* recommended in web apps. -->
    <EnableUnsafeBinaryFormatterSerialization>true</EnableUnsafeBinaryFormatterSerialization>
  </PropertyGroup>
  ```

推奨される操作の詳細については、「[BinaryFormatter の廃止と無効化に関するエラーの解決](https://aka.ms/binaryformatter)」をご覧ください。

#### <a name="category"></a>カテゴリ

- Core .NET ライブラリ
- ASP.NET

#### <a name="affected-apis"></a>影響を受ける API

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize`
- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`
- `M:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)`
- `M:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)`

-->
