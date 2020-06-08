---
title: 文字列の .NET Framework データ型への変換
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 65455ef3-9120-412c-819b-d0f59f88ac09
ms.openlocfilehash: fda5441c58d14b91a9eca16fff9149c8795f95b9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289227"
---
# <a name="converting-strings-to-net-framework-data-types"></a><span data-ttu-id="28d78-102">文字列の .NET Framework データ型への変換</span><span class="sxs-lookup"><span data-stu-id="28d78-102">Converting Strings to .NET Framework Data Types</span></span>
<span data-ttu-id="28d78-103">文字列を .NET Framework データ型に変換するには、アプリケーションの要件に適合する **XmlConvert** メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="28d78-103">If you want to convert a string to a .NET Framework data type, use the **XmlConvert** method that fits the application requirements.</span></span> <span data-ttu-id="28d78-104">**XmlConvert** クラスで利用可能なすべての変換メソッドの一覧については、「<xref:System.Xml.XmlConvert>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28d78-104">For a list of all conversion methods available in the **XmlConvert** class, see <xref:System.Xml.XmlConvert>.</span></span>  
  
 <span data-ttu-id="28d78-105">**ToString** メソッドから返される文字列は、渡したデータを文字列に変換したものです。</span><span class="sxs-lookup"><span data-stu-id="28d78-105">The string returned from the **ToString** method is a string version of the data that is passed in.</span></span> <span data-ttu-id="28d78-106">変換に **XmlConvert** クラスを使用する .NET Framework 型の中には、**System.Convert** クラスのメソッドを使用しないものがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="28d78-106">Additionally, there are several .NET Framework types that convert using the **XmlConvert** class yet they do not use the methods in the **System.Convert** class.</span></span> <span data-ttu-id="28d78-107">**XmlConvert** クラスは XML Schema (XSD) のデータ型に準拠しており、**XmlConvert** によって変換できるデータ型は決まっています。</span><span class="sxs-lookup"><span data-stu-id="28d78-107">The **XmlConvert** class follows the XML Schema (XSD) data type specification and has a data type that the **XmlConvert** can map to.</span></span>  
  
 <span data-ttu-id="28d78-108">次の表は、.NET Framework データ型の一覧と、XML スキーマ (XSD) のデータ型マップを使用した場合に返される文字列を示しています。</span><span class="sxs-lookup"><span data-stu-id="28d78-108">The following table lists .NET Framework data types and the string types that are returned using XML Schema (XSD) data type mapping.</span></span> <span data-ttu-id="28d78-109">これらの .NET Framework 型は、**System.Convert** で処理することはできません。</span><span class="sxs-lookup"><span data-stu-id="28d78-109">These .NET Framework types cannot be processed using **System.Convert**.</span></span>  
  
|<span data-ttu-id="28d78-110">.NET Framework 型</span><span class="sxs-lookup"><span data-stu-id="28d78-110">.NET Framework type</span></span>|<span data-ttu-id="28d78-111">返される文字列</span><span class="sxs-lookup"><span data-stu-id="28d78-111">String returned</span></span>|  
|-------------------------|---------------------|  
|<span data-ttu-id="28d78-112">ブール型</span><span class="sxs-lookup"><span data-stu-id="28d78-112">Boolean</span></span>|<span data-ttu-id="28d78-113">"true"、"false"</span><span class="sxs-lookup"><span data-stu-id="28d78-113">"true", "false"</span></span>|  
|<span data-ttu-id="28d78-114">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="28d78-114">Single.PositiveInfinity</span></span>|<span data-ttu-id="28d78-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="28d78-115">"INF"</span></span>|  
|<span data-ttu-id="28d78-116">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="28d78-116">Single.NegativeInfinity</span></span>|<span data-ttu-id="28d78-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="28d78-117">"-INF"</span></span>|  
|<span data-ttu-id="28d78-118">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="28d78-118">Double.PositiveInfinity</span></span>|<span data-ttu-id="28d78-119">"INF"</span><span class="sxs-lookup"><span data-stu-id="28d78-119">"INF"</span></span>|  
|<span data-ttu-id="28d78-120">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="28d78-120">Double.NegativeInfinity</span></span>|<span data-ttu-id="28d78-121">"-INF"</span><span class="sxs-lookup"><span data-stu-id="28d78-121">"-INF"</span></span>|  
|<span data-ttu-id="28d78-122">DateTime</span><span class="sxs-lookup"><span data-stu-id="28d78-122">DateTime</span></span>|<span data-ttu-id="28d78-123">形式は、yyyy-MM-ddTHH:mm:sszzzzzz およびそのサブセットです。</span><span class="sxs-lookup"><span data-stu-id="28d78-123">Format is "yyyy-MM-ddTHH:mm:sszzzzzz" and its subsets.</span></span>|  
|<span data-ttu-id="28d78-124">Timespan</span><span class="sxs-lookup"><span data-stu-id="28d78-124">Timespan</span></span>|<span data-ttu-id="28d78-125">PnYnMnTnHnMnS の形式。つまり、`P2Y10M15DT10H30M20S` は 2 年 10 か月 15 日 10 時間 30 分 20 秒の期間です。</span><span class="sxs-lookup"><span data-stu-id="28d78-125">Format is PnYnMnTnHnMnS that is, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10 hours, 30 minutes, and 20 seconds.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="28d78-126">表中の .NET Framework 型を **ToString** メソッドを使用して文字列に変換したときに返される文字列は基本型ではなく、XML スキーマ (XSD) 文字列型です。</span><span class="sxs-lookup"><span data-stu-id="28d78-126">If converting any of the .NET Framework types listed in the table to a string using the **ToString** method, the returned string is not the base type, but the XML Schema (XSD) string type.</span></span>  
  
 <span data-ttu-id="28d78-127">**DateTime** 値型と **Timespan** 値型の違いは、**DateTime** が瞬間を表すのに対して、**TimeSpan** が時間間隔を表すことです。</span><span class="sxs-lookup"><span data-stu-id="28d78-127">The **DateTime** and **Timespan** value type differs in that a **DateTime** represents an instant in time, whereas a **TimeSpan** represents a time interval.</span></span> <span data-ttu-id="28d78-128">**DateTime** および **Timespan** の形式は、XML スキーマ (XSD) のデータ型仕様で指定されています。</span><span class="sxs-lookup"><span data-stu-id="28d78-128">The **DateTime** and **Timespan** formats are specified in the XML Schema (XSD) data types specification.</span></span> <span data-ttu-id="28d78-129">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="28d78-129">For example:</span></span>  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim [date] As New DateTime(2001, 8, 4)  
writer.WriteElementString("Date", XmlConvert.ToString([date]))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
DateTime date = new DateTime (2001, 08, 04);  
writer.WriteElementString("Date", XmlConvert.ToString(date));  
```  
  
 <span data-ttu-id="28d78-130">**出力**</span><span class="sxs-lookup"><span data-stu-id="28d78-130">**Output**</span></span>  
  
 <span data-ttu-id="28d78-131">`<Date>2001-08-04T00:00:00</Date>`。</span><span class="sxs-lookup"><span data-stu-id="28d78-131">`<Date>2001-08-04T00:00:00</Date>`.</span></span>  
  
 <span data-ttu-id="28d78-132">整数を文字列に変換するコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="28d78-132">The following code converts an integer to a string:</span></span>  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim value As Int32 = 200  
writer.WriteElementString("Number", XmlConvert.ToString(value))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
Int32 value = 200;  
writer.WriteElementString("Number", XmlConvert.ToString(value));  
```  
  
 <span data-ttu-id="28d78-133">**出力**</span><span class="sxs-lookup"><span data-stu-id="28d78-133">**Output**</span></span>  
  
 `<Number>200</Number>`  
  
 <span data-ttu-id="28d78-134">ただし、文字列を **Boolean**、**Single**、または **Double** に変換する場合、返される .NET Framework 型は、**System.Convert** クラスを使用したときに返される型とは異なります。</span><span class="sxs-lookup"><span data-stu-id="28d78-134">However, if you are converting a string to **Boolean**, **Single**, or **Double**, the .NET Framework type that is returned is not the same as the type returned when using the **System.Convert** class.</span></span>  
  
## <a name="string-to-boolean"></a><span data-ttu-id="28d78-135">String から Boolean</span><span class="sxs-lookup"><span data-stu-id="28d78-135">String to Boolean</span></span>  
 <span data-ttu-id="28d78-136">**ToBoolean** メソッドを使用して文字列を **Boolean** に変換するときの入力文字列と生成される型の対応を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="28d78-136">The following table shows what type is generated for the given input strings, when converting a string to **Boolean** using the **ToBoolean** method.</span></span>  
  
|<span data-ttu-id="28d78-137">有効な文字列入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="28d78-137">Valid string input parameter</span></span>|<span data-ttu-id="28d78-138">出力される .NET Framework 型</span><span class="sxs-lookup"><span data-stu-id="28d78-138">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="28d78-139">"true"</span><span class="sxs-lookup"><span data-stu-id="28d78-139">"true"</span></span>|<span data-ttu-id="28d78-140">Boolean.True</span><span class="sxs-lookup"><span data-stu-id="28d78-140">Boolean.True</span></span>|  
|<span data-ttu-id="28d78-141">"1"</span><span class="sxs-lookup"><span data-stu-id="28d78-141">"1"</span></span>|<span data-ttu-id="28d78-142">Boolean.True</span><span class="sxs-lookup"><span data-stu-id="28d78-142">Boolean.True</span></span>|  
|<span data-ttu-id="28d78-143">"false"</span><span class="sxs-lookup"><span data-stu-id="28d78-143">"false"</span></span>|<span data-ttu-id="28d78-144">Boolean.False</span><span class="sxs-lookup"><span data-stu-id="28d78-144">Boolean.False</span></span>|  
|<span data-ttu-id="28d78-145">"0"</span><span class="sxs-lookup"><span data-stu-id="28d78-145">"0"</span></span>|<span data-ttu-id="28d78-146">Boolean.False</span><span class="sxs-lookup"><span data-stu-id="28d78-146">Boolean.False</span></span>|  
  
 <span data-ttu-id="28d78-147">たとえば、次のような XML があるとします。</span><span class="sxs-lookup"><span data-stu-id="28d78-147">For example, given the following XML:</span></span>  
  
 <span data-ttu-id="28d78-148">**入力**</span><span class="sxs-lookup"><span data-stu-id="28d78-148">**Input**</span></span>  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>
```  
  
 <span data-ttu-id="28d78-149">いずれも次のコードによって解釈することができ、**bvalue** は **System.Boolean.True** になります。</span><span class="sxs-lookup"><span data-stu-id="28d78-149">Both can be understood by the following code, and **bvalue** is **System.Boolean.True**:</span></span>  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a><span data-ttu-id="28d78-150">String から Single</span><span class="sxs-lookup"><span data-stu-id="28d78-150">String to Single</span></span>  
 <span data-ttu-id="28d78-151">**ToSingle** メソッドを使用して文字列を **Single** に変換するときの入力文字列と生成される型の対応を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="28d78-151">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToSingle** method.</span></span>  
  
|<span data-ttu-id="28d78-152">有効な文字列入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="28d78-152">Valid string input parameter</span></span>|<span data-ttu-id="28d78-153">出力される .NET Framework 型</span><span class="sxs-lookup"><span data-stu-id="28d78-153">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="28d78-154">"INF"</span><span class="sxs-lookup"><span data-stu-id="28d78-154">"INF"</span></span>|<span data-ttu-id="28d78-155">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="28d78-155">Single.PositiveInfinity</span></span>|  
|<span data-ttu-id="28d78-156">"-INF"</span><span class="sxs-lookup"><span data-stu-id="28d78-156">"-INF"</span></span>|<span data-ttu-id="28d78-157">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="28d78-157">Single.NegativeInfinity</span></span>|  
  
## <a name="string-to-double"></a><span data-ttu-id="28d78-158">String から Double</span><span class="sxs-lookup"><span data-stu-id="28d78-158">String to Double</span></span>  
 <span data-ttu-id="28d78-159">**ToDouble** メソッドを使用して文字列を **Single** に変換するときの入力文字列と生成される型の対応を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="28d78-159">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToDouble** method.</span></span>  
  
|<span data-ttu-id="28d78-160">有効な文字列入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="28d78-160">Valid string input parameter</span></span>|<span data-ttu-id="28d78-161">出力される .NET Framework 型</span><span class="sxs-lookup"><span data-stu-id="28d78-161">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="28d78-162">"INF"</span><span class="sxs-lookup"><span data-stu-id="28d78-162">"INF"</span></span>|<span data-ttu-id="28d78-163">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="28d78-163">Double.PositiveInfinity</span></span>|  
|<span data-ttu-id="28d78-164">"-INF"</span><span class="sxs-lookup"><span data-stu-id="28d78-164">"-INF"</span></span>|<span data-ttu-id="28d78-165">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="28d78-165">Double.NegativeInfinity</span></span>|  
  
 <span data-ttu-id="28d78-166">次のコードは、`<Infinity>INF</Infinity>` を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="28d78-166">The following code writes `<Infinity>INF</Infinity>`:</span></span>  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## <a name="see-also"></a><span data-ttu-id="28d78-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="28d78-167">See also</span></span>

- [<span data-ttu-id="28d78-168">XML データ型の変換</span><span class="sxs-lookup"><span data-stu-id="28d78-168">Conversion of XML Data Types</span></span>](conversion-of-xml-data-types.md)
- [<span data-ttu-id="28d78-169">.NET Framework 型の文字列への変換</span><span class="sxs-lookup"><span data-stu-id="28d78-169">Converting .NET Framework Types to Strings</span></span>](converting-dotnet-types-to-strings.md)
