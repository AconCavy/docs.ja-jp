---
title: プラットフォーム呼び出しの例
description: User32.dll で MessageBox 関数を定義して呼び出す方法を示すプラットフォーム呼び出しの例について説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [.NET Framework], platform invoke
- unmanaged functions
- COM interop, platform invoke
- platform invoke, examples
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 15926806-f0b7-487e-93a6-4e9367ec689f
ms.openlocfilehash: 97b0720b8954bc24a4058e6a03c32d32bd9e3180
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620808"
---
# <a name="platform-invoke-examples"></a><span data-ttu-id="a93a4-103">プラットフォーム呼び出しの例</span><span class="sxs-lookup"><span data-stu-id="a93a4-103">Platform Invoke Examples</span></span>
<span data-ttu-id="a93a4-104">User32.dll で **MessageBox** 関数を定義し、引数として単純な文字列を渡して呼び出す例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a93a4-104">The following examples demonstrate how to define and call the **MessageBox** function in User32.dll, passing a simple string as an argument.</span></span> <span data-ttu-id="a93a4-105">この例では、<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> フィールドは **Auto** に設定されているため、ターゲット プラットフォームで文字の幅と文字列のマーシャリングを決定できます。</span><span class="sxs-lookup"><span data-stu-id="a93a4-105">In the examples, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field is set to **Auto** to let the target platform determine the character width and string marshaling.</span></span>  
  
 [!code-cpp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cpp/Example.cpp#1)]
 [!code-csharp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cs/Example1.cs#1)]
 [!code-vb[Conceptual.Interop.PInvoke#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Interop.PInvoke/vb/Example1.vb#1)]  
  
 <span data-ttu-id="a93a4-106">その他の例については、「[Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md)」(プラットフォーム呼び出しによるデータのマーシャリング) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a93a4-106">For additional examples, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a93a4-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="a93a4-107">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="a93a4-108">マネージド コードでのプロトタイプの作成</span><span class="sxs-lookup"><span data-stu-id="a93a4-108">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="a93a4-109">文字セットの指定</span><span class="sxs-lookup"><span data-stu-id="a93a4-109">Specifying a Character Set</span></span>](specifying-a-character-set.md)
