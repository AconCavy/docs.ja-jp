---
title: .NET Framework における文字列の操作
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- strings [.NET Framework], manipulating
- manipulating strings
ms.assetid: d4568ff3-9f83-4549-acd8-47aec2194ac0
ms.openlocfilehash: 5188c4f1099aad486e921dfba0c6c4216613ba4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "73135228"
---
# <a name="manipulating-strings-in-net"></a><span data-ttu-id="bee3f-102">.NET における文字列の操作</span><span class="sxs-lookup"><span data-stu-id="bee3f-102">Manipulating Strings in .NET</span></span>
<span data-ttu-id="bee3f-103">.NET では、文字列を効率的に作成、比較、変更できるだけでなく、検索、削除、およびテキスト パターンを置換するために、大量のテキストとデータをすばやく解析できる広範囲のルーチンのセットを提供しています。</span><span class="sxs-lookup"><span data-stu-id="bee3f-103">.NET provides an extensive set of routines that enable you to efficiently create, compare, and modify strings as well as rapidly parse large amounts of text and data to search for, remove, and replace text patterns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bee3f-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="bee3f-104">In This Section</span></span>  
 [<span data-ttu-id="bee3f-105">文字列を使用するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="bee3f-105">Best Practices for Using Strings</span></span>](../../../docs/standard/base-types/best-practices-strings.md)  
 <span data-ttu-id="bee3f-106">.NET での文字列の並べ替え、比較、および大文字小文字の区別の方法を調査し、文字列処理方法を選択する場合の推奨事項を示します。</span><span class="sxs-lookup"><span data-stu-id="bee3f-106">Examines string-sorting, comparison, and casing methods in .NET, and provides recommendations for selecting a string-handling method .</span></span>  
  
 [<span data-ttu-id="bee3f-107">.NET の正規表現</span><span class="sxs-lookup"><span data-stu-id="bee3f-107">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)  
 <span data-ttu-id="bee3f-108">言語要素、正規表現の動作、例などの .NET の正規表現の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="bee3f-108">Provides detailed information about .NET regular expressions, including language elements, regular expression behavior, and examples.</span></span>  
  
 [<span data-ttu-id="bee3f-109">基本的な文字列操作</span><span class="sxs-lookup"><span data-stu-id="bee3f-109">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)  
 <span data-ttu-id="bee3f-110">バイト配列からの新しい文字列の作成、文字列値の比較、既存の文字列の変更など、<xref:System.String?displayProperty=nameWithType> および <xref:System.Text.StringBuilder?displayProperty=nameWithType> クラスによって提供される文字列の操作について説明します。</span><span class="sxs-lookup"><span data-stu-id="bee3f-110">Describes string operations provided by the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes, including creating new strings from arrays of bytes, comparing string values, and modifying existing strings.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bee3f-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="bee3f-111">Related Sections</span></span>  
 [<span data-ttu-id="bee3f-112">.NET での型変換</span><span class="sxs-lookup"><span data-stu-id="bee3f-112">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="bee3f-113">.NET を使用して型を変換するための手法とルールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="bee3f-113">Explains the techniques and rules used to convert types using .NET.</span></span>  
  
 [<span data-ttu-id="bee3f-114">型の書式設定</span><span class="sxs-lookup"><span data-stu-id="bee3f-114">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="bee3f-115">基本クラス ライブラリを使用して書式設定を実装する方法、数値型を書式設定する方法、文字列型を書式設定する方法、特定のカルチャに対して書式設定する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="bee3f-115">Provides how to use the base class library to implement formatting, how to format numeric types, how to format string types, and how to format for a specific culture.</span></span>  
  
 [<span data-ttu-id="bee3f-116">文字列の解析</span><span class="sxs-lookup"><span data-stu-id="bee3f-116">Parsing Strings</span></span>](../../../docs/standard/base-types/parsing-strings.md)  
 <span data-ttu-id="bee3f-117">オブジェクトの文字列表現によって指定された値にオブジェクトを初期化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bee3f-117">Describes how to initialize objects to the values described by string representations of those objects.</span></span> <span data-ttu-id="bee3f-118">解析は書式設定の逆の操作です。</span><span class="sxs-lookup"><span data-stu-id="bee3f-118">Parsing is the inverse operation of formatting.</span></span>
