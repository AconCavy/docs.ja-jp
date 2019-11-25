---
title: '方法: XML ファイルからオブジェクト データを読み込む'
ms.date: 07/20/2015
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
ms.openlocfilehash: c997af4729a24a6b5bd5b22d0153860cff3282d7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346436"
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a><span data-ttu-id="0bdbb-102">How to: Read Object Data from an XML File (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0bdbb-102">How to: Read Object Data from an XML File (Visual Basic)</span></span>
<span data-ttu-id="0bdbb-103">次の例では、<xref:System.Xml.Serialization.XmlSerializer> クラスを使用して、XML ファイルに以前に書き込まれたオブジェクト データを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="0bdbb-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bdbb-104">例</span><span class="sxs-lookup"><span data-stu-id="0bdbb-104">Example</span></span>  
  
```vb  
Public Class Book  
    Public Title As String  
End Class  
  
Public Sub ReadXML()  
    Dim reader As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
    Dim file As New System.IO.StreamReader(  
        "c:\temp\SerializationOverview.xml")  
    Dim overview As Book  
    overview = CType(reader.Deserialize(file), Book)  
    Console.WriteLine(overview.Title)  
End Sub  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0bdbb-105">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="0bdbb-105">Compiling the Code</span></span>  
 <span data-ttu-id="0bdbb-106">ファイル名 "c:\temp\SerializationOverview.xml" を、シリアル化されたデータを含むファイルの名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="0bdbb-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="0bdbb-107">For more information about serializing data, see [How to: Write Object Data to an XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="0bdbb-107">For more information about serializing data, see [How to: Write Object Data to an XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="0bdbb-108">クラスには、パラメーターのないパブリック コンストラクターが必要です。</span><span class="sxs-lookup"><span data-stu-id="0bdbb-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="0bdbb-109">パブリック プロパティとパブリック フィールドだけが逆シリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="0bdbb-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="0bdbb-110">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="0bdbb-110">Robust Programming</span></span>  
 <span data-ttu-id="0bdbb-111">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0bdbb-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="0bdbb-112">シリアル化されるクラスにパブリックなパラメーターなしのコンストラクターがない場合</span><span class="sxs-lookup"><span data-stu-id="0bdbb-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="0bdbb-113">ファイル内のデータが、逆シリアル化されるクラスのデータを表していない場合。</span><span class="sxs-lookup"><span data-stu-id="0bdbb-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
- <span data-ttu-id="0bdbb-114">ファイルが存在しない (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="0bdbb-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="0bdbb-115">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="0bdbb-115">.NET Framework Security</span></span>  
 <span data-ttu-id="0bdbb-116">入力を常に検証し、信頼できないソースから決してデータを逆シリアル化しないでください。</span><span class="sxs-lookup"><span data-stu-id="0bdbb-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="0bdbb-117">再作成されたオブジェクトは、そのオブジェクトを逆シリアル化したコードと同じアクセス許可を持つローカル コンピューターで実行されます。</span><span class="sxs-lookup"><span data-stu-id="0bdbb-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="0bdbb-118">アプリケーションでデータを使用する前に、入力をすべて検証してください。</span><span class="sxs-lookup"><span data-stu-id="0bdbb-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bdbb-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="0bdbb-119">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="0bdbb-120">方法: XML ファイルにオブジェクト データを書き込む (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0bdbb-120">How to: Write Object Data to an XML File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="0bdbb-121">シリアル化 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0bdbb-121">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
- [<span data-ttu-id="0bdbb-122">Visual Basic のプログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="0bdbb-122">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
