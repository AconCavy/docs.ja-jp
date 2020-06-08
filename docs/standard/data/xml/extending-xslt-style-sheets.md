---
title: XSLT スタイル シートの拡張
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: df4ba2bf-a99e-4d22-bbf3-04fc67669dbc
ms.openlocfilehash: 2ac4aeb598563ac85a20ef1e2c0b63ccc682bfba
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287754"
---
# <a name="extending-xslt-style-sheets"></a><span data-ttu-id="a1414-102">XSLT スタイル シートの拡張</span><span class="sxs-lookup"><span data-stu-id="a1414-102">Extending XSLT Style Sheets</span></span>
<span data-ttu-id="a1414-103">このセクションでは、XSLT の機能を拡張するさまざまな方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a1414-103">This section describes the different methods of extending the XSLT functionality.</span></span> <span data-ttu-id="a1414-104">拡張オブジェクトまたはパラメーターは、<xref:System.Xml.Xsl.XsltArgumentList> クラスを使用して追加できます。</span><span class="sxs-lookup"><span data-stu-id="a1414-104">You can add extension objects or parameters using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="a1414-105">その後、スタイル シートから拡張オブジェクトまたはパラメーターを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="a1414-105">The extension objects or parameters can then be called from the style sheet.</span></span> <span data-ttu-id="a1414-106">また、`msxsl:script` 要素を使用すると、スタイル シートにスクリプト ブロックを埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="a1414-106">In addition, you can also embed script blocks into the style sheet by using the `msxsl:script` element.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a1414-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a1414-107">In This Section</span></span>  
 [<span data-ttu-id="a1414-108">XSLT 拡張オブジェクト</span><span class="sxs-lookup"><span data-stu-id="a1414-108">XSLT Extension Objects</span></span>](xslt-extension-objects.md)  
 <span data-ttu-id="a1414-109"><xref:System.Xml.Xsl.XsltArgumentList> クラスを使用して XSLT 拡張オブジェクトを処理する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a1414-109">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT extension objects.</span></span>  
  
 [<span data-ttu-id="a1414-110">XSLT パラメーター</span><span class="sxs-lookup"><span data-stu-id="a1414-110">XSLT Parameters</span></span>](xslt-parameters.md)  
 <span data-ttu-id="a1414-111"><xref:System.Xml.Xsl.XsltArgumentList> クラスを使用して XSLT パラメーターを処理する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a1414-111">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT parameters.</span></span>  
  
 [<span data-ttu-id="a1414-112">msxsl:script を使用したスクリプト ブロック</span><span class="sxs-lookup"><span data-stu-id="a1414-112">Script Blocks Using msxsl:script</span></span>](script-blocks-using-msxsl-script.md)  
 <span data-ttu-id="a1414-113">`msxsl:script` 要素の使い方を説明します。</span><span class="sxs-lookup"><span data-stu-id="a1414-113">Discusses using the `msxsl:script` element.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a1414-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1414-114">Related Sections</span></span>  
 [<span data-ttu-id="a1414-115">XSLT 変換</span><span class="sxs-lookup"><span data-stu-id="a1414-115">XSLT Transformations</span></span>](xslt-transformations.md)
