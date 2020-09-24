---
title: 書き込みを行うと MaximumSize 値を超えてしまうため、ログ ファイルに書き込めません
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_FileExceedsMaximumSize
ms.assetid: 61747a9c-e460-424b-a365-73cdba9dd428
ms.openlocfilehash: 95a7b9036e7c1494cd44c250b0580bab5144417b
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059458"
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-cause-it-to-exceed-maximumsize-value"></a><span data-ttu-id="85d28-102">書き込みを行うと MaximumSize 値を超えてしまうため、ログ ファイルに書き込めません</span><span class="sxs-lookup"><span data-stu-id="85d28-102">Unable to write to log file because writing to it would cause it to exceed MaximumSize value</span></span>

<span data-ttu-id="85d28-103">次の理由により、 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> クラスは、ログ ファイルに書き込むことができませんでした。</span><span class="sxs-lookup"><span data-stu-id="85d28-103">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not write to the log file because:</span></span>  
  
- <span data-ttu-id="85d28-104">ログ ファイルのサイズ (バイト単位) が <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> プロパティの値より大きい</span><span class="sxs-lookup"><span data-stu-id="85d28-104">The log file size (in bytes) is greater than the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> property</span></span>  
  
     <span data-ttu-id="85d28-105">- および -</span><span class="sxs-lookup"><span data-stu-id="85d28-105">—and—</span></span>  
  
- <span data-ttu-id="85d28-106"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> プロパティの値が <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>でした。</span><span class="sxs-lookup"><span data-stu-id="85d28-106">The value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property was <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="85d28-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="85d28-107">To correct this error</span></span>  
  
1. <span data-ttu-id="85d28-108">既存のログをアーカイブし、それらをコンピューターから削除して、 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> オブジェクトが新しいログを作成できるようにします。</span><span class="sxs-lookup"><span data-stu-id="85d28-108">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
2. <span data-ttu-id="85d28-109"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> プロパティの値を変更して、より大きなログを作成できるようにします。</span><span class="sxs-lookup"><span data-stu-id="85d28-109">Change the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> property to allow for larger logs.</span></span>  
  
3. <span data-ttu-id="85d28-110"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> プロパティを <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> に設定し、ログが大きすぎる場合は、警告のないメッセージを破棄します。</span><span class="sxs-lookup"><span data-stu-id="85d28-110">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property to <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> to discard messages without warning if the log is too large.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85d28-111">こちらもご覧ください</span><span class="sxs-lookup"><span data-stu-id="85d28-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- [<span data-ttu-id="85d28-112">.Log</span><span class="sxs-lookup"><span data-stu-id="85d28-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- <span data-ttu-id="85d28-113">[[DirectoryPath]](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)</span><span class="sxs-lookup"><span data-stu-id="85d28-113">[My.Application.Info.DirectoryPath](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)</span></span>
