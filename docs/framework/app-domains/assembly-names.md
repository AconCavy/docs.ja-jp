---
title: アセンブリ名
ms.date: 03/30/2017
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36993a13ed085f59fd6002f33e7884bdb1b5db8d
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66832893"
---
# <a name="assembly-names"></a>アセンブリ名
アセンブリの名前は、メタデータに保存され、アセンブリのスコープに重大な影響があり、アプリケーションによって使用されます。 厳密な名前のアセンブリには、アセンブリの名前、カルチャ、公開キー、バージョン番号を含む、完全修飾名があります。 これは、表示名として、また、<xref:System.Reflection.Assembly.FullName%2A> プロパティを使用して取得できる読み込まれたアセンブリに対して、頻繁に参照されます。  
  
 ランタイムはこの情報を使用して、アセンブリを検索し、同じ名前のその他のアセンブリと区別します。 たとえば、`myTypes` と呼ばれる厳密な名前のアセンブリは、次の完全修飾名を持つ場合があります。  
  
```  
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil  
```  
  
> [!NOTE]
>  プロセッサ アーキテクチャは、アセンブリのプロセッサ固有バージョンを許可するために、.NET Framework バージョン 2.0 のアセンブリ ID に追加されます。 ID のプロセッサ アーキテクチャ (たとえば、32 ビットおよび 64 ビットのプロセッサ固有バージョン) のみが異なる、アセンブリのバージョンを作成できます。 プロセッサ アーキテクチャは、厳密な名前には必要ありません。 詳細については、<xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType> を参照してください。  
  
 この例の完全修飾名は、`myTypes` アセンブリには公開キー トークンを持つ厳密な名前があり、英語 (米国) のカルチャの値があり、1.0.1234.0 のバージョン番号があることを示しています。 そのプロセッサ アーキテクチャは "msil" です。つまり、オペレーティング システムやプロセッサに応じて、32 ビット コードまたは 64 ビット コードに Just-In-Time (JIT) でコンパイルされるということです。  
  
 アセンブリの型を要求するコードは、完全修飾のアセンブリ名を使用する必要があります。 これは、完全修飾のバインドと呼ばれます。 アセンブリ名のみを指定する部分的バインドは、.NET Framework のアセンブリを参照している場合は許可されません。  
  
 また、.NET Framework を構成するアセンブリを参照するアセンブリにはすべて、アセンブリの完全修飾名も含める必要があります。 たとえば、バージョン 1.0 の System.Data .NET Framework アセンブリを参照するには、次が含まれます。  
  
```  
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
```  
  
 このバージョンは、.NET Framework バージョン 1.0 に同梱されているすべての .NET Framework アセンブリのバージョン番号に対応しています。 .NET Framework アセンブリでは、カルチャの値は常にニュートラルであり、公開キーは上記の例に示したものと同じです。  
  
 たとえば、トレース リスナーを設定するために、構成ファイルにアセンブリ参照を追加するには、システムの .NET Framework アセンブリの完全修飾名を含めます。  
  
```xml  
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
```  
  
> [!NOTE]
>  アセンブリをバインドするときに、ランタイムは大文字と小文字を区別せずにアセンブリ名を扱いますが、アセンブリ名に使用されている大文字と小文字を保持します。 Windows Software Development Kit (SDK) のいくつかのツールでは、アセンブリ名の大文字小文字を区別して処理します。 最適な結果を得るには、大文字と小文字を区別するものとして、アセンブリ名を管理します。  
  
## <a name="naming-application-components"></a>名前付けアプリケーション コンポーネント  
 アセンブリの ID を特定するときに、ランタイムではファイル名が考慮されません。 アセンブリ名、バージョン、カルチャ、厳密な名前で構成されるアセンブリ ID は、ランタイムに対して明確である必要があります。  
  
 たとえば、myAssembly.dll という名前のアセンブリを参照する myAssembly.exe という名前のアセンブリがある場合は、myAssembly.exe を実行すると、バインドが正しく行われます。 ただし、別のアプリケーションがメソッド <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType> を使用して myAssembly.exe を実行する場合、ランタイムは myAssembly.exe が "myAssembly" へのバインドを要求するときに、"myAssembly" は既に読み込まれていると判断します。 この場合、myAssembly.dll が読み込まれることはありません。 myAssembly.exe には、要求された型が含まれていないため、<xref:System.TypeLoadException> が発生します。  
  
 この問題を避けるには、アプリケーションを構成するアセンブリが、確実に同じアセンブリ名を持たないように、または異なるディレクトリに同じ名前を持つアセンブリを配置しないようにします。  
  
> [!NOTE]
>  グローバル アセンブリ キャッシュに厳密な名前のアセンブリを配置した場合、アセンブリのファイル名は、アセンブリ名と一致する必要があります (.exe または .dll などのファイル名の拡張子を除く)。 たとえば、アセンブリのファイル名が myAssembly.dll である場合は、アセンブリ名は myAssembly である必要があります。 ルート アプリケーション ディレクトリにのみ展開されるプライベート アセンブリは、ファイル名とは異なるアセンブリ名を持つことができます。  
  
## <a name="see-also"></a>関連項目

- [方法: アセンブリの完全修飾名を特定する](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)
- [アセンブリの作成](../../../docs/framework/app-domains/create-assemblies.md)
- [厳密な名前付きアセンブリ](../../../docs/framework/app-domains/strong-named-assemblies.md)
- [グローバル アセンブリ キャッシュ](../../../docs/framework/app-domains/gac.md)
- [ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)
