---
title: ファイル システムから XML ツリーを設定する方法 (C#)
ms.date: 07/20/2015
ms.assetid: 2aa2ccac-4a22-47ae-9107-3bb8df232576
ms.openlocfilehash: beb44be1a787fa09b091aa48022dbb5b10c4632b
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345782"
---
# <a name="how-to-populate-an-xml-tree-from-the-file-system-c"></a><span data-ttu-id="44c78-102">ファイル システムから XML ツリーを設定する方法 (C#)</span><span class="sxs-lookup"><span data-stu-id="44c78-102">How to populate an XML tree from the file system (C#)</span></span>
<span data-ttu-id="44c78-103">XML ツリーの一般的で便利な用途の 1 つに、名前と値の階層データ ストアとしての用途があります。</span><span class="sxs-lookup"><span data-stu-id="44c78-103">A common and useful application of XML trees is as a hierarchical name/value data store.</span></span> <span data-ttu-id="44c78-104">階層データを XML ツリーに設定し、そのツリーをクエリや変換の対象としたり、必要に応じてシリアル化したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="44c78-104">You can populate an XML tree with hierarchical data, and then query it, transform it, and if necessary, serialize it.</span></span> <span data-ttu-id="44c78-105">この使用シナリオでは、名前空間や空白の扱いなど XML 固有のセマンティクスの多くは重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="44c78-105">In this usage scenario, many of the XML specific semantics, such as namespaces and white space behavior, are not important.</span></span> <span data-ttu-id="44c78-106">この場合は、XML ツリーをメモリ内の小さなシングル ユーザー階層データベースとして使用します。</span><span class="sxs-lookup"><span data-stu-id="44c78-106">Instead, you are using the XML tree as a small, in memory, single user hierarchical database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44c78-107">例</span><span class="sxs-lookup"><span data-stu-id="44c78-107">Example</span></span>  
 <span data-ttu-id="44c78-108">次の例では、再帰を使用してローカル ファイル システムから XML ツリーを設定します。</span><span class="sxs-lookup"><span data-stu-id="44c78-108">The following example populates an XML tree from the local file system using recursion.</span></span> <span data-ttu-id="44c78-109">次に、ツリーに対してクエリを実行して、ツリー内にあるすべてのファイルの合計サイズを計算します。</span><span class="sxs-lookup"><span data-stu-id="44c78-109">It then queries the tree, calculating the total of the sizes of all files in the tree.</span></span>  
  
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
  
 <span data-ttu-id="44c78-110">この例では次のような出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="44c78-110">This example produces output similar to the following:</span></span>  
  
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
