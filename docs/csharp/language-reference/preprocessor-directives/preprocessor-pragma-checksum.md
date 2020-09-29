---
description: '#pragma checksum - C# リファレンス'
title: '#pragma checksum - C# リファレンス'
ms.date: 07/20/2015
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
ms.openlocfilehash: df665704ac813adbbf6473e81fad0a1c7ff616d0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168570"
---
# <a name="pragma-checksum-c-reference"></a><span data-ttu-id="31aa5-103">#pragma checksum (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="31aa5-103">#pragma checksum (C# Reference)</span></span>

<span data-ttu-id="31aa5-104">ASP.NET ページのデバッグに使用するソース ファイルのチェックサムを生成します。</span><span class="sxs-lookup"><span data-stu-id="31aa5-104">Generates checksums for source files to aid with debugging ASP.NET pages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31aa5-105">構文</span><span class="sxs-lookup"><span data-stu-id="31aa5-105">Syntax</span></span>  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
## <a name="parameters"></a><span data-ttu-id="31aa5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="31aa5-106">Parameters</span></span>  

 `"filename"`  
 <span data-ttu-id="31aa5-107">変更または更新を監視する必要があるファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="31aa5-107">The name of the file that requires monitoring for changes or updates.</span></span>  
  
 `"{guid}"`  
 <span data-ttu-id="31aa5-108">ハッシュ アルゴリズムのグローバル一意識別子 (GUID)。</span><span class="sxs-lookup"><span data-stu-id="31aa5-108">The Globally Unique Identifier (GUID) for the hash algorithm.</span></span>  
  
 `"checksum_bytes"`  
 <span data-ttu-id="31aa5-109">チェックサムのバイト数を表す 16 進数の文字列。</span><span class="sxs-lookup"><span data-stu-id="31aa5-109">The string of hexadecimal digits representing the bytes of the checksum.</span></span> <span data-ttu-id="31aa5-110">偶数の 16 進数である必要があります。</span><span class="sxs-lookup"><span data-stu-id="31aa5-110">Must be an even number of hexadecimal digits.</span></span> <span data-ttu-id="31aa5-111">奇数の数値を指定すると、コンパイル時に警告が出力され、ディレクティブが無視されます。</span><span class="sxs-lookup"><span data-stu-id="31aa5-111">An odd number of digits results in a compile-time warning, and the directive are ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31aa5-112">解説</span><span class="sxs-lookup"><span data-stu-id="31aa5-112">Remarks</span></span>  

 <span data-ttu-id="31aa5-113">Visual Studio デバッガーは、常に正しいソースを検出するために、チェックサムを使用します。</span><span class="sxs-lookup"><span data-stu-id="31aa5-113">The Visual Studio debugger uses a checksum to make sure  that it always finds the right source.</span></span> <span data-ttu-id="31aa5-114">コンパイラはソース ファイルのチェックサムを計算し、プログラム データベース (PDB) ファイルに結果を出力します。</span><span class="sxs-lookup"><span data-stu-id="31aa5-114">The compiler computes the checksum for a source file, and then emits the output to the program database (PDB) file.</span></span> <span data-ttu-id="31aa5-115">デバッガーは、その PDB ファイルを使用して、ソース ファイルについて計算したチェックサムと比較します。</span><span class="sxs-lookup"><span data-stu-id="31aa5-115">The debugger then uses the PDB to compare against the checksum that it computes for the source file.</span></span>  
  
 <span data-ttu-id="31aa5-116">このソリューションは ASP.NET プロジェクトには使用できません。計算されたチェックサムは、.aspx ファイルではなく、生成されたソース ファイルを対象としているためです。</span><span class="sxs-lookup"><span data-stu-id="31aa5-116">This solution does not work for ASP.NET projects, because the computed checksum is for the generated source file, rather than the .aspx file.</span></span> <span data-ttu-id="31aa5-117">この問題に対応するため、`#pragma checksum` によって ASP.NET ページのチェックサムがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="31aa5-117">To address this problem, `#pragma checksum` provides checksum support for ASP.NET pages.</span></span>  
  
 <span data-ttu-id="31aa5-118">Visual C# で ASP.NET プロジェクトを作成すると、生成されるソース ファイルにソースの生成元である .aspx ファイルのチェックサムが含められます。</span><span class="sxs-lookup"><span data-stu-id="31aa5-118">When you create an ASP.NET project in Visual C#, the generated source file contains a checksum for the .aspx file, from which the source is generated.</span></span> <span data-ttu-id="31aa5-119">コンパイラは、この情報を PDB ファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="31aa5-119">The compiler then writes this information into the PDB file.</span></span>  
  
 <span data-ttu-id="31aa5-120">ファイルに `#pragma checksum` ディレクティブが見つからない場合、コンパイラはチェックサムを計算し、PDB ファイルにその値を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="31aa5-120">If the compiler encounters no `#pragma checksum` directive in the file, it computes the checksum and writes the value to the PDB file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31aa5-121">例</span><span class="sxs-lookup"><span data-stu-id="31aa5-121">Example</span></span>  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{406EA660-64CF-4C82-B6F0-42D48172A799}" "ab007f1d23d9" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="31aa5-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="31aa5-122">See also</span></span>

- [<span data-ttu-id="31aa5-123">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="31aa5-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="31aa5-124">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="31aa5-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="31aa5-125">C# プリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="31aa5-125">C# Preprocessor Directives</span></span>](./index.md)
