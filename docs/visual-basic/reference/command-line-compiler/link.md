---
title: -link
ms.date: 03/10/2018
helpviewer_keywords:
- l compiler option [Visual Basic]
- EmbedInteropTypes
- embed interop types [COM Interop]
- -link compiler option [Visual Basic]
- /link compiler option [Visual Basic]
- link compiler option [Visual Basic]
- -l compiler option [Visual Basic]
- /l compiler option [Visual Basic]
ms.assetid: 1885f24a-86f5-486c-a064-9fb7e455ccec
ms.openlocfilehash: ecb7b0448b8ee9c1c1fc1eb9542b693d60a38ffd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335844"
---
# <a name="-link-visual-basic"></a><span data-ttu-id="9a899-102">-link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a899-102">-link (Visual Basic)</span></span>
<span data-ttu-id="9a899-103">指定したアセンブリ内の COM 型情報を、現在のコンパイル対象のプロジェクトで使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="9a899-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a899-104">構文</span><span class="sxs-lookup"><span data-stu-id="9a899-104">Syntax</span></span>  
  
```console  
-link:fileList  
```

<span data-ttu-id="9a899-105">または</span><span class="sxs-lookup"><span data-stu-id="9a899-105">or</span></span>  

```console
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="9a899-106">引数</span><span class="sxs-lookup"><span data-stu-id="9a899-106">Arguments</span></span>  
  
|<span data-ttu-id="9a899-107">用語</span><span class="sxs-lookup"><span data-stu-id="9a899-107">Term</span></span>|<span data-ttu-id="9a899-108">定義</span><span class="sxs-lookup"><span data-stu-id="9a899-108">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="9a899-109">必須。</span><span class="sxs-lookup"><span data-stu-id="9a899-109">Required.</span></span> <span data-ttu-id="9a899-110">アセンブリ ファイル名のコンマ区切りリスト。</span><span class="sxs-lookup"><span data-stu-id="9a899-110">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="9a899-111">ファイル名に空白が含まれている場合は、名前を二重引用符で囲みます。</span><span class="sxs-lookup"><span data-stu-id="9a899-111">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a899-112">コメント</span><span class="sxs-lookup"><span data-stu-id="9a899-112">Remarks</span></span>  
 <span data-ttu-id="9a899-113">`-link` オプションを使用すると、埋め込み型情報を含むアプリケーションを配置できます。</span><span class="sxs-lookup"><span data-stu-id="9a899-113">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="9a899-114">その後、このアプリケーションは、埋め込み型情報を実装する、ランタイム アセンブリ内の型を使用できます。その際、ランタイム アセンブリへの参照は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="9a899-114">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="9a899-115">ランタイム アセンブリのさまざまなバージョンが公開されている場合、埋め込み型情報を含むアプリケーションは、再コンパイルする必要なく、各種バージョンで動作できます。</span><span class="sxs-lookup"><span data-stu-id="9a899-115">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="9a899-116">例については、「[チュートリアル: マネージド アセンブリからの型の埋め込み](../../../standard/assembly/embed-types-visual-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a899-116">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../../standard/assembly/embed-types-visual-studio.md).</span></span>  
  
 <span data-ttu-id="9a899-117">`-link` オプションの使用は、COM 相互運用を使用している場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="9a899-117">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="9a899-118">COM 型を埋め込むことができるため、アプリケーションは、ターゲット コンピューター上にプライマリ相互運用機能アセンブリ (PIA) を必要としなくなります。</span><span class="sxs-lookup"><span data-stu-id="9a899-118">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="9a899-119">`-link` オプションを使用すると、コンパイラによって、COM 型情報は、参照先の相互運用アセンブリから結果としてコンパイルされるコードに埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="9a899-119">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="9a899-120">COM 型は、CLSID (GUID) 値によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="9a899-120">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="9a899-121">その結果、同じ CLSID 値の同じ COM 型がインストールされているターゲット コンピューターでアプリケーションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="9a899-121">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="9a899-122">Microsoft Office を自動化するアプリケーションが良い例です。</span><span class="sxs-lookup"><span data-stu-id="9a899-122">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="9a899-123">Office のようなアプリケーションは、通常、さまざまなバージョン間で同じ CLSID 値を保持するため、.NET Framework 4 以降がターゲット コンピューターにインストールされていて、参照先の COM 型に含まれているメソッド、プロパティ、またはイベントがアプリケーションで使用される限りは、そのアプリケーションで参照先の COM 型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="9a899-123">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="9a899-124">`-link` オプションで埋め込まれるのは、インターフェイス、構造体、デリゲートのみです。</span><span class="sxs-lookup"><span data-stu-id="9a899-124">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="9a899-125">COM クラスの埋め込みはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="9a899-125">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9a899-126">コードで埋め込み COM 型のインスタンスを作成する際は、適切なインターフェイスを使用してインスタンスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a899-126">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="9a899-127">コクラスを使用して埋め込み COM 型のインスタンスを作成しようとすると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="9a899-127">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="9a899-128">Visual Studio で `-link` オプションを設定するには、アセンブリ参照を追加し、`Embed Interop Types` プロパティを **true** に設定します。</span><span class="sxs-lookup"><span data-stu-id="9a899-128">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="9a899-129">`Embed Interop Types` プロパティの既定値は **false** です。</span><span class="sxs-lookup"><span data-stu-id="9a899-129">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="9a899-130">別の COM アセンブリ (アセンブリ B) を参照する COM アセンブリ (アセンブリ A) にリンクする場合、次のいずれかが当てはまるときは、アセンブリ B にもリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a899-130">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
- <span data-ttu-id="9a899-131">アセンブリ A の型がアセンブリ B の型から継承されているか、アセンブリ B のインターフェイスを実装する。</span><span class="sxs-lookup"><span data-stu-id="9a899-131">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="9a899-132">アセンブリ B の戻り値の型またはパラメーターの型を使用するフィールド、プロパティ、イベント、またはメソッドが呼び出される。</span><span class="sxs-lookup"><span data-stu-id="9a899-132">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="9a899-133">アセンブリ参照が1つ以上存在するディレクトリを指定するには、 [-libpath](libpath.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="9a899-133">Use [-libpath](libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="9a899-134">[-Reference](reference.md)コンパイラオプションと同様に、`-link` コンパイラオプションは、頻繁に使用される .NET Framework アセンブリを参照する vbc.exe 応答ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="9a899-134">Like the [-reference](reference.md) compiler option, the `-link` compiler option uses the Vbc.rsp response file, which references frequently used .NET Framework assemblies.</span></span> <span data-ttu-id="9a899-135">コンパイラで Vbc.exe ファイルを使用しない場合は、 [-noconfig](noconfig.md)コンパイラオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="9a899-135">Use the [-noconfig](noconfig.md) compiler option if you do not want the compiler to use the Vbc.rsp file.</span></span>  
  
 <span data-ttu-id="9a899-136">`-link` の省略形は `-l` です。</span><span class="sxs-lookup"><span data-stu-id="9a899-136">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="9a899-137">ジェネリック型と埋め込み型</span><span class="sxs-lookup"><span data-stu-id="9a899-137">Generics and Embedded Types</span></span>  
 <span data-ttu-id="9a899-138">以降のセクションでは、相互運用機能型を埋め込むアプリケーションでジェネリック型を使用する際の制限事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="9a899-138">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="9a899-139">ジェネリック インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a899-139">Generic Interfaces</span></span>  
 <span data-ttu-id="9a899-140">相互運用アセンブリから埋め込まれるジェネリック インターフェイスを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="9a899-140">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="9a899-141">これを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="9a899-141">This is shown in the following example.</span></span>  
  
 [!code-vb[VbLinkCompiler#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#1)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="9a899-142">ジェネリック パラメーターを含む型</span><span class="sxs-lookup"><span data-stu-id="9a899-142">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="9a899-143">型が相互運用アセンブリから埋め込まれているジェネリック パラメーターを含む型は、外部アセンブリからの型である場合に使用できません。</span><span class="sxs-lookup"><span data-stu-id="9a899-143">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="9a899-144">この制限はインターフェイスには当てはまりません。</span><span class="sxs-lookup"><span data-stu-id="9a899-144">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="9a899-145">たとえば、<xref:Microsoft.Office.Interop.Excel.Range> アセンブリで定義されている <xref:Microsoft.Office.Interop.Excel> インターフェイスについて考えます。</span><span class="sxs-lookup"><span data-stu-id="9a899-145">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="9a899-146">ライブラリによって <xref:Microsoft.Office.Interop.Excel> アセンブリから相互運用型が埋め込まれ、型が <xref:Microsoft.Office.Interop.Excel.Range> インターフェイスであるパラメーターを含むジェネリック型を返すメソッドが公開される場合、次のコード例に示すように、そのメソッドはジェネリック インターフェイスを返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a899-146">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-vb[VbLinkCompiler#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#2)]  
[!code-vb[VbLinkCompiler#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#3)]  
[!code-vb[VbLinkCompiler#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#4)]  
  
 <span data-ttu-id="9a899-147">次の例では、クライアント コードで、<xref:System.Collections.IList> ジェネリック インターフェイスを返すメソッドをエラーなしで呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="9a899-147">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-vb[VbLinkCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="9a899-148">例</span><span class="sxs-lookup"><span data-stu-id="9a899-148">Example</span></span>  
 <span data-ttu-id="9a899-149">次のコマンドラインは、`COMData1.dll` と `COMData2.dll` からソースファイル `OfficeApp.vb` と参照アセンブリをコンパイルして `OfficeApp.exe`を生成します。</span><span class="sxs-lookup"><span data-stu-id="9a899-149">The following command line compiles source file `OfficeApp.vb` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```console  
vbc -link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="9a899-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a899-150">See also</span></span>

- [<span data-ttu-id="9a899-151">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="9a899-151">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="9a899-152">チュートリアル: マネージド アセンブリからの型の埋め込み</span><span class="sxs-lookup"><span data-stu-id="9a899-152">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="9a899-153">-reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a899-153">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="9a899-154">-noconfig</span><span class="sxs-lookup"><span data-stu-id="9a899-154">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="9a899-155">-libpath</span><span class="sxs-lookup"><span data-stu-id="9a899-155">-libpath</span></span>](libpath.md)
- [<span data-ttu-id="9a899-156">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="9a899-156">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="9a899-157">COM 相互運用の概要</span><span class="sxs-lookup"><span data-stu-id="9a899-157">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
