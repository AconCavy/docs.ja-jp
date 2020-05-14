---
title: DLL 読み込み時のエラーです。
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: 36452cc6ff03042939cd4066aef76129b5bb8f0a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329552"
---
# <a name="error-in-loading-dll-visual-basic"></a><span data-ttu-id="4e3d0-102">DLL 読み込み時のエラーです。(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e3d0-102">Error in loading DLL (Visual Basic)</span></span>
<span data-ttu-id="4e3d0-103">ダイナミックリンク ライブラリ (DLL) は、`Declare` ステートメントの `Lib` 句で指定されたライブラリです。</span><span class="sxs-lookup"><span data-stu-id="4e3d0-103">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span></span> <span data-ttu-id="4e3d0-104">このエラーには、次の原因が考えられます。</span><span class="sxs-lookup"><span data-stu-id="4e3d0-104">Possible causes for this error include:</span></span>  
  
- <span data-ttu-id="4e3d0-105">ファイルが DLL 実行可能ファイルではありません。</span><span class="sxs-lookup"><span data-stu-id="4e3d0-105">The file is not DLL executable.</span></span>  
  
- <span data-ttu-id="4e3d0-106">ファイルが Microsoft Windows DLL ではありません。</span><span class="sxs-lookup"><span data-stu-id="4e3d0-106">The file is not a Microsoft Windows DLL.</span></span>  
  
- <span data-ttu-id="4e3d0-107">DLL が存在しない別の DLL を参照しています。</span><span class="sxs-lookup"><span data-stu-id="4e3d0-107">The DLL references another DLL that is not present.</span></span>  
  
- <span data-ttu-id="4e3d0-108">DLL または参照先の DLL が、パスで指定されたディレクトリにありません。</span><span class="sxs-lookup"><span data-stu-id="4e3d0-108">The DLL or referenced DLL is not in a directory specified in the path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4e3d0-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="4e3d0-109">To correct this error</span></span>  
  
- <span data-ttu-id="4e3d0-110">ファイルがソーステキスト ファイルであり、そのため DLL 実行可能ファイルでない場合は、コンパイルして DLL 実行可能形式にリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4e3d0-110">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span></span>  
  
- <span data-ttu-id="4e3d0-111">ファイルが Microsoft Windows DLL でない場合は、Microsoft Windows と同等のものを取得します。</span><span class="sxs-lookup"><span data-stu-id="4e3d0-111">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span></span>  
  
- <span data-ttu-id="4e3d0-112">DLL が存在しない別の DLL を参照している場合は、参照先の DLL を取得して、使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="4e3d0-112">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span></span>  
  
- <span data-ttu-id="4e3d0-113">DLL または参照先の DLL がパスによって指定されたディレクトリにない場合は、DLL を参照先のディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="4e3d0-113">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e3d0-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="4e3d0-114">See also</span></span>

- [<span data-ttu-id="4e3d0-115">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="4e3d0-115">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
