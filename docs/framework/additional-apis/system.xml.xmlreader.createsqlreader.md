---
title: XmlReader (System.xml) メソッド (System.xml)
ms.date: 10/17/2019
topic_type:
- apiref
api_name:
- System.Xml.XmlReader.CreateSqlReader
api_location:
- system.xml.dll
api_type:
- Assembly
ms.openlocfilehash: c65ef7c073175488c11c5e912a44d46fd4319209
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215450"
---
# <a name="xmlreadercreatesqlreader-method"></a><span data-ttu-id="5cfd0-102">XmlReader.CreateSqlReader  メソッド</span><span class="sxs-lookup"><span data-stu-id="5cfd0-102">XmlReader.CreateSqlReader Method</span></span>

<span data-ttu-id="5cfd0-103">解析のために指定されたストリーム、設定、およびコンテキスト情報を使用して、新しい <xref:System.Xml.XmlReader> インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="5cfd0-103">Creates a new <xref:System.Xml.XmlReader> instance using the specified stream, settings, and context information for parsing.</span></span>

```csharp
internal static XmlReader CreateSqlReader(Stream input, 
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a><span data-ttu-id="5cfd0-104">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5cfd0-104">Parameters</span></span>

- <span data-ttu-id="5cfd0-105">`input` <xref:System.IO.Stream></span><span class="sxs-lookup"><span data-stu-id="5cfd0-105">`input` <xref:System.IO.Stream></span></span>  
  <span data-ttu-id="5cfd0-106">XML データを格納しているストリーム。</span><span class="sxs-lookup"><span data-stu-id="5cfd0-106">The stream that contains the XML data.</span></span>

- <span data-ttu-id="5cfd0-107">`settings` <xref:System.Xml.XmlReaderSettings></span><span class="sxs-lookup"><span data-stu-id="5cfd0-107">`settings` <xref:System.Xml.XmlReaderSettings></span></span>  
  <span data-ttu-id="5cfd0-108">新しい <xref:System.Xml.XmlReader> インスタンスの設定。</span><span class="sxs-lookup"><span data-stu-id="5cfd0-108">The settings for the new <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="5cfd0-109">この値には `null` を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5cfd0-109">This value can be `null`.</span></span>

- <span data-ttu-id="5cfd0-110">`inputContext` <xref:System.Xml.XmlParserContext></span><span class="sxs-lookup"><span data-stu-id="5cfd0-110">`inputContext` <xref:System.Xml.XmlParserContext></span></span>  
  <span data-ttu-id="5cfd0-111">XML フラグメントの解析に必要なコンテキスト情報。</span><span class="sxs-lookup"><span data-stu-id="5cfd0-111">The context information required to parse the XML fragment.</span></span> <span data-ttu-id="5cfd0-112">この値には `null` を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5cfd0-112">This value can be `null`.</span></span>

## <a name="returns"></a><span data-ttu-id="5cfd0-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="5cfd0-113">Returns</span></span>

<xref:System.Xml.XmlReader>  
<span data-ttu-id="5cfd0-114">ストリーム内の XML データの読み取りに使用するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5cfd0-114">An object that is used to read the XML data in the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="5cfd0-115">コメント</span><span class="sxs-lookup"><span data-stu-id="5cfd0-115">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="5cfd0-116">`XmlReader.CreateSqlReader` メソッドは内部であり、コードで直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="5cfd0-116">The `XmlReader.CreateSqlReader` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="5cfd0-117">Microsoft では、どのような状況でも、実稼働アプリケーションでこの方法を使用することはサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="5cfd0-117">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="5cfd0-118">要件</span><span class="sxs-lookup"><span data-stu-id="5cfd0-118">Requirements</span></span>

<span data-ttu-id="5cfd0-119">**名前空間:** <xref:System.Xml></span><span class="sxs-lookup"><span data-stu-id="5cfd0-119">**Namespace:** <xref:System.Xml></span></span>

<span data-ttu-id="5cfd0-120">**アセンブリ:** System.xml</span><span class="sxs-lookup"><span data-stu-id="5cfd0-120">**Assembly:** System.Xml.dll</span></span>

<span data-ttu-id="5cfd0-121">**.NET Framework のバージョン:** 2.0 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="5cfd0-121">**.NET Framework versions:** Available since 2.0.</span></span>
