---
title: イベント ログに無効な名前が指定されました
ms.date: 07/20/2015
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
ms.openlocfilehash: 70b1de2a3776a9c68260cc431b65e754d7247a0c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84412924"
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a><span data-ttu-id="4db15-102">イベント ログに無効な名前が指定されました</span><span class="sxs-lookup"><span data-stu-id="4db15-102">An invalid name was specified for the event log</span></span>
<span data-ttu-id="4db15-103">イベント ログに無効な名前が指定されました。</span><span class="sxs-lookup"><span data-stu-id="4db15-103">An invalid name was specified for the event log.</span></span> <span data-ttu-id="4db15-104">通常これは、名前に含まれる無効な文字、空のファイル名、または長すぎるファイル名の結果です。</span><span class="sxs-lookup"><span data-stu-id="4db15-104">Usually this is a result of invalid characters in the name, a blank file name, or a file name that is too long.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4db15-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="4db15-105">To correct this error</span></span>  
  
- <span data-ttu-id="4db15-106">指定した名前が 8 文字を超える場合、他のイベント ログの名前と競合しないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="4db15-106">If the specified name is more than eight characters, make sure there is no conflict with the names of other event logs.</span></span> <span data-ttu-id="4db15-107">名前が一意であるかどうかを判断するときには、最初の 8 文字のみが評価されます。</span><span class="sxs-lookup"><span data-stu-id="4db15-107">Only the first eight characters are evaluated when determining if the name is unique.</span></span>  
  
- <span data-ttu-id="4db15-108">パスを指定する場合は、正しく解析されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4db15-108">If supplying a path, make sure it is parsed correctly.</span></span>  
  
- <span data-ttu-id="4db15-109">名前に無効な文字がないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="4db15-109">Check that there are no invalid characters in the name.</span></span> <span data-ttu-id="4db15-110">ファイル名に使用できない文字には `<`、 `>`、 `:`、 `"`、 `/`、 `\`、および `|`があります。</span><span class="sxs-lookup"><span data-stu-id="4db15-110">Characters that cannot be used in a file name include `<`, `>`, `:`, `"`, `/`, `\`, and `|`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4db15-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="4db15-111">See also</span></span>

- [<span data-ttu-id="4db15-112">方法: ファイル パスを解析する</span><span class="sxs-lookup"><span data-stu-id="4db15-112">How to: Parse File Paths</span></span>](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
- [<span data-ttu-id="4db15-113">方法: ファイルの名前を変更する</span><span class="sxs-lookup"><span data-stu-id="4db15-113">How to: Rename a File</span></span>](../developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
