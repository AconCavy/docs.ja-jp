---
title: '方法: WebRequest を型キャストしてプロトコル固有のプロパティにアクセスする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d9a8eae2-7454-46f9-b43b-c98477c5bcde
ms.openlocfilehash: d38a40aa1e6e3db769aedfc440077721cdfaf06d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180754"
---
# <a name="how-to-typecast-a-webrequest-to-access-protocol-specific-properties"></a><span data-ttu-id="0c37f-102">方法: WebRequest を型キャストしてプロトコル固有のプロパティにアクセスする</span><span class="sxs-lookup"><span data-stu-id="0c37f-102">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>
<span data-ttu-id="0c37f-103">この例では、WebRequest を型キャストしてプロトコル固有のプロパティにアクセスできるようにする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="0c37f-103">This example shows how to typecast a WebRequest so that you can access protocol specific properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c37f-104">例</span><span class="sxs-lookup"><span data-stu-id="0c37f-104">Example</span></span>  
  
```csharp  
HttpWebRequest httpreq =
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
```  
  
```vb  
Dim httpreq As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
```  
  
## <a name="see-also"></a><span data-ttu-id="0c37f-105">参照</span><span class="sxs-lookup"><span data-stu-id="0c37f-105">See also</span></span>

- [<span data-ttu-id="0c37f-106">プラグ可能なプロトコルのプログラミング</span><span class="sxs-lookup"><span data-stu-id="0c37f-106">Programming Pluggable Protocols</span></span>](programming-pluggable-protocols.md)
