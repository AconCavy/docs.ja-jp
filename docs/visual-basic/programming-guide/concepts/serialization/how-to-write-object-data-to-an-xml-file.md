---
title: '方法: XML ファイルにオブジェクト データを書き込む'
ms.date: 07/20/2015
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
ms.openlocfilehash: af62d10b29e76701668fd3d595b967bd1754a22c
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077229"
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a><span data-ttu-id="97e2f-102">方法: XML ファイルにオブジェクト データを書き込む (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97e2f-102">How to: Write Object Data to an XML File (Visual Basic)</span></span>

<span data-ttu-id="97e2f-103"><xref:System.Xml.Serialization.XmlSerializer> クラスを使用して、クラスから XML ファイルにオブジェクトを書き込む例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="97e2f-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97e2f-104">例</span><span class="sxs-lookup"><span data-stu-id="97e2f-104">Example</span></span>  
  
```vb  
Public Module XMLWrite  
  
    Sub Main()  
        WriteXML()  
    End Sub  
  
    Public Class Book  
        Public Title As String  
    End Class  
  
    Public Sub WriteXML()  
        Dim overview As New Book  
        overview.Title = "Serialization Overview"  
        Dim writer As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
        Dim file As New System.IO.StreamWriter(  
            "c:\temp\SerializationOverview.xml")  
        writer.Serialize(file, overview)  
        file.Close()  
    End Sub  
End Module  
```  
  
## <a name="compile-the-code"></a><span data-ttu-id="97e2f-105">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="97e2f-105">Compile the code</span></span>  

 <span data-ttu-id="97e2f-106">クラスには、パラメーターのないパブリック コンストラクターが必要です。</span><span class="sxs-lookup"><span data-stu-id="97e2f-106">The class must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="97e2f-107">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="97e2f-107">Robust Programming</span></span>  

 <span data-ttu-id="97e2f-108">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="97e2f-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="97e2f-109">シリアル化されるクラスにパブリックなパラメーターなしのコンストラクターがない場合</span><span class="sxs-lookup"><span data-stu-id="97e2f-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="97e2f-110">ファイルが存在するものの、読み取り専用の場合 (<xref:System.IO.IOException>)</span><span class="sxs-lookup"><span data-stu-id="97e2f-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="97e2f-111">パスが長すぎる (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="97e2f-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="97e2f-112">ディスクの空き領域がない場合 (<xref:System.IO.IOException>)</span><span class="sxs-lookup"><span data-stu-id="97e2f-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="97e2f-113">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="97e2f-113">.NET Framework Security</span></span>  

 <span data-ttu-id="97e2f-114">次のコード例では、ファイルが存在しない場合は新規にファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="97e2f-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="97e2f-115">アプリケーションでファイルを作成する必要がある場合、そのアプリケーションにはフォルダーに対する `Create` アクセスが必要です。</span><span class="sxs-lookup"><span data-stu-id="97e2f-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="97e2f-116">ファイルが既に存在する場合、アプリケーションに必要なのは、より低い権限である `Write` アクセスだけです。</span><span class="sxs-lookup"><span data-stu-id="97e2f-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="97e2f-117">フォルダーに対して `Read` アクセスを許可するのではなく、可能な限りアプリケーションの配置時にファイルを作成しておき、1 つのファイルに対してのみ `Create` アクセスを許可する方が安全です。</span><span class="sxs-lookup"><span data-stu-id="97e2f-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97e2f-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="97e2f-118">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="97e2f-119">方法: XML ファイルからオブジェクト データを読み込む (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97e2f-119">How to: Read Object Data from an XML File (Visual Basic)</span></span>](how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="97e2f-120">シリアル化 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97e2f-120">Serialization (Visual Basic)</span></span>](index.md)
