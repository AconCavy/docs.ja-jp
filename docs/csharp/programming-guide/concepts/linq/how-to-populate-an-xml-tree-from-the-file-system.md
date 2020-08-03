---
title: ファイル システムから XML ツリーを設定する方法 (C#)
description: C# でファイル システムから XML ツリーを設定する方法について説明します。 この例では、XML を設定し、ツリーに対してクエリを実行して、すべてのファイルの合計サイズを計算します。
ms.date: 07/20/2015
ms.assetid: 2aa2ccac-4a22-47ae-9107-3bb8df232576
ms.openlocfilehash: 676261656be7d306294c9912b75edcb51a31cccc
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104766"
---
# <a name="how-to-populate-an-xml-tree-from-the-file-system-c"></a><span data-ttu-id="a8d3c-104">ファイル システムから XML ツリーを設定する方法 (C#)</span><span class="sxs-lookup"><span data-stu-id="a8d3c-104">How to populate an XML tree from the file system (C#)</span></span>
<span data-ttu-id="a8d3c-105">XML ツリーの一般的で便利な用途の 1 つに、名前と値の階層データ ストアとしての用途があります。</span><span class="sxs-lookup"><span data-stu-id="a8d3c-105">A common and useful application of XML trees is as a hierarchical name/value data store.</span></span> <span data-ttu-id="a8d3c-106">階層データを XML ツリーに設定し、そのツリーをクエリや変換の対象としたり、必要に応じてシリアル化したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="a8d3c-106">You can populate an XML tree with hierarchical data, and then query it, transform it, and if necessary, serialize it.</span></span> <span data-ttu-id="a8d3c-107">この使用シナリオでは、名前空間や空白の扱いなど XML 固有のセマンティクスの多くは重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="a8d3c-107">In this usage scenario, many of the XML specific semantics, such as namespaces and white space behavior, are not important.</span></span> <span data-ttu-id="a8d3c-108">この場合は、XML ツリーをメモリ内の小さなシングル ユーザー階層データベースとして使用します。</span><span class="sxs-lookup"><span data-stu-id="a8d3c-108">Instead, you are using the XML tree as a small, in memory, single user hierarchical database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8d3c-109">例</span><span class="sxs-lookup"><span data-stu-id="a8d3c-109">Example</span></span>  
 <span data-ttu-id="a8d3c-110">次の例では、再帰を使用してローカル ファイル システムから XML ツリーを設定します。</span><span class="sxs-lookup"><span data-stu-id="a8d3c-110">The following example populates an XML tree from the local file system using recursion.</span></span> <span data-ttu-id="a8d3c-111">次に、ツリーに対してクエリを実行して、ツリー内にあるすべてのファイルの合計サイズを計算します。</span><span class="sxs-lookup"><span data-stu-id="a8d3c-111">It then queries the tree, calculating the total of the sizes of all files in the tree.</span></span>  
  
```csharp  
class Program  
{  
    static XElement CreateFileSystemXmlTree(string source)  
    {  
        DirectoryInfo di = new DirectoryInfo(source);  
        return new XElement("Dir",  
            new XAttribute("Name", di.Name),  
            from d in Directory.GetDirectories(source)  
            select CreateFileSystemXmlTree(d),  
            from fi in di.GetFiles()  
            select new XElement("File",  
                new XElement("Name", fi.Name),  
                new XElement("Length", fi.Length)  
            )  
        );  
    }  
  
    static void Main(string[] args)  
    {  
        XElement fileSystemTree = CreateFileSystemXmlTree("C:/Tmp");  
        Console.WriteLine(fileSystemTree);  
        Console.WriteLine("------");  
        long totalFileSize =  
            (from f in fileSystemTree.Descendants("File")  
             select (long)f.Element("Length")).Sum();  
        Console.WriteLine("Total File Size:{0}", totalFileSize);  
    }  
}  
```  
  
 <span data-ttu-id="a8d3c-112">この例では次のような出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a8d3c-112">This example produces output similar to the following:</span></span>  
  
```xml  
<Dir Name="Tmp">  
  <Dir Name="ConsoleApplication1">  
    <Dir Name="bin">  
      <Dir Name="Debug">  
        <File>  
          <Name>ConsoleApplication1.exe</Name>  
          <Length>4608</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.pdb</Name>  
          <Length>11776</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.vshost.exe</Name>  
          <Length>9568</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.vshost.exe.manifest</Name>  
          <Length>473</Length>  
        </File>  
      </Dir>  
    </Dir>  
    <Dir Name="obj">  
      <Dir Name="Debug">  
        <Dir Name="TempPE" />  
        <File>  
          <Name>ConsoleApplication1.csproj.FileListAbsolute.txt</Name>  
          <Length>322</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.exe</Name>  
          <Length>4608</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.pdb</Name>  
          <Length>11776</Length>  
        </File>  
      </Dir>  
    </Dir>  
    <Dir Name="Properties">  
      <File>  
        <Name>AssemblyInfo.cs</Name>  
        <Length>1454</Length>  
      </File>  
    </Dir>  
    <File>  
      <Name>ConsoleApplication1.csproj</Name>  
      <Length>2546</Length>  
    </File>  
    <File>  
      <Name>ConsoleApplication1.sln</Name>  
      <Length>937</Length>  
    </File>  
    <File>  
      <Name>ConsoleApplication1.suo</Name>  
      <Length>10752</Length>  
    </File>  
    <File>  
      <Name>Program.cs</Name>  
      <Length>269</Length>  
    </File>  
  </Dir>  
</Dir>  
------  
Total File Size:59089  
```  
