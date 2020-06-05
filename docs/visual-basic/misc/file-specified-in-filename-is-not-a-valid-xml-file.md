---
title: FileName で指定されたファイルは、正しい XML ファイルではありません
ms.date: 07/20/2015
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
ms.openlocfilehash: a84042490935e3e7e5a6de2a802d9effd5b4d3d4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84358349"
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a><span data-ttu-id="b1ee6-102">FileName で指定されたファイルは、正しい XML ファイルではありません</span><span class="sxs-lookup"><span data-stu-id="b1ee6-102">File specified in FileName is not a valid XML file</span></span>

<span data-ttu-id="b1ee6-103">指定したファイル名は、正しい XML ファイルではありません。</span><span class="sxs-lookup"><span data-stu-id="b1ee6-103">The file name that you supplied is not a valid XML file.</span></span> <span data-ttu-id="b1ee6-104">XML ドキュメントの許可されている構造体とコンテンツを指定する場合、ドキュメント型定義 (DTD)、Microsoft XML-Data Reduced (XDR) スキーマ、または XML スキーマ定義言語 (XSD) スキーマを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b1ee6-104">To specify the allowed structure and content of an XML document, you can use a Document Type Definition (DTD), a Microsoft XML-Data Reduced (XDR) schema, or an XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="b1ee6-105">.NET Framework で XML 文法を指定する場合は、XSD スキーマを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b1ee6-105">XSD schemas are the preferred way to specify XML grammars in the .NET Framework.</span></span>

> [!NOTE]
> <span data-ttu-id="b1ee6-106">Visual Studio の以前のバージョンにある **XML デザイナー** とは、型指定されたデータセットおよび XML スキーマのデザイナーのことです。</span><span class="sxs-lookup"><span data-stu-id="b1ee6-106">In some earlier versions of Visual Studio, the **XML Designer** is the designer for typed datasets and XML schema.</span></span> <span data-ttu-id="b1ee6-107">**XML デザイナー** は、XML スキーマ ファイルの作成と編集に今も使用できます。</span><span class="sxs-lookup"><span data-stu-id="b1ee6-107">The **XML Designer** can still be used to create and edit XML schema files.</span></span> <span data-ttu-id="b1ee6-108">ただし、Visual Studio 2012 では、型指定されたデータセットを作成および編集するためのデザイナーが**データセットデザイナー**です。</span><span class="sxs-lookup"><span data-stu-id="b1ee6-108">However, in Visual Studio 2012, the designer for creating and editing typed datasets is the **Dataset Designer**.</span></span> <span data-ttu-id="b1ee6-109">詳細については、「型指定された[データセットの作成と編集](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1ee6-109">For more information, see [Creating and Editing Typed Datasets](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120)).</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="b1ee6-110">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="b1ee6-110">To correct this error</span></span>

- <span data-ttu-id="b1ee6-111">正しいファイル名を指定していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b1ee6-111">Check that you are supplying the correct file name.</span></span>

- <span data-ttu-id="b1ee6-112">確認する必要のある XML ファイルを **XML デザイナー**に読み込んで、指定したファイルに正しい XML が含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b1ee6-112">Check that the specified file contains valid XML by loading the XML file that you want to check into the **XML Designer**.</span></span> <span data-ttu-id="b1ee6-113">**[XML]** メニューで、 **[XML の整合性チェック]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1ee6-113">From the **XML** menu, click **Validate XML**.</span></span> <span data-ttu-id="b1ee6-114">エラーは **[タスク一覧]** に表示されます。</span><span class="sxs-lookup"><span data-stu-id="b1ee6-114">Errors are displayed in the **Task List**.</span></span>

- <span data-ttu-id="b1ee6-115">XML ファイルに関連付けられた XML スキーマがある場合は、定義された構造体にその要素が出現し、個々の要素のコンテンツがスキーマで指定された宣言されたデータ型に準拠していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b1ee6-115">If the XML file has an associated XML Schema, check that the elements appear in the defined structure and that the content of the individual elements conforms to the declared data types specified in the schema.</span></span>

## <a name="see-also"></a><span data-ttu-id="b1ee6-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="b1ee6-116">See also</span></span>

- <xref:System.Xml>
- [<span data-ttu-id="b1ee6-117">方法: ファイル パスを解析する</span><span class="sxs-lookup"><span data-stu-id="b1ee6-117">How to: Parse File Paths</span></span>](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
