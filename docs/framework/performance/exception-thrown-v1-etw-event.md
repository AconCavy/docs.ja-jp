---
title: Exception Thrown_V1 ETW イベント
description: ExceptionThrown_V1 ETW イベントに関する詳細情報を表示します。 スローされた例外に対して、フィールド名、データ型、説明などのイベントデータが与えられます。
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
ms.openlocfilehash: f4ae277b5dfb09d2676755fec2208b63906ead84
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554672"
---
# <a name="exception-thrown_v1-etw-event"></a><span data-ttu-id="8ecea-104">Exception Thrown_V1 ETW イベント</span><span class="sxs-lookup"><span data-stu-id="8ecea-104">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="8ecea-105">このイベントは、スローされる例外に関する情報をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="8ecea-105">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="8ecea-106">イベントが発生するキーワードとイベントのレベルを次の表に示します </span><span class="sxs-lookup"><span data-stu-id="8ecea-106">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="8ecea-107">(詳細については、「 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="8ecea-107">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="8ecea-108">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="8ecea-108">Keyword for raising the event</span></span>|<span data-ttu-id="8ecea-109">レベル</span><span class="sxs-lookup"><span data-stu-id="8ecea-109">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="8ecea-110">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="8ecea-110">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="8ecea-111">警告 (2)</span><span class="sxs-lookup"><span data-stu-id="8ecea-111">Warning (2)</span></span>|  
  
 <span data-ttu-id="8ecea-112">次の表にイベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="8ecea-112">The following table shows event information.</span></span>  
  
|<span data-ttu-id="8ecea-113">Event</span><span class="sxs-lookup"><span data-stu-id="8ecea-113">Event</span></span>|<span data-ttu-id="8ecea-114">イベント ID</span><span class="sxs-lookup"><span data-stu-id="8ecea-114">Event ID</span></span>|<span data-ttu-id="8ecea-115">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="8ecea-115">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="8ecea-116">80</span><span class="sxs-lookup"><span data-stu-id="8ecea-116">80</span></span>|<span data-ttu-id="8ecea-117">マネージド例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="8ecea-117">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="8ecea-118">次の表にイベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="8ecea-118">The following table shows event data.</span></span>  
  
|<span data-ttu-id="8ecea-119">フィールド名</span><span class="sxs-lookup"><span data-stu-id="8ecea-119">Field name</span></span>|<span data-ttu-id="8ecea-120">データ型</span><span class="sxs-lookup"><span data-stu-id="8ecea-120">Data type</span></span>|<span data-ttu-id="8ecea-121">説明</span><span class="sxs-lookup"><span data-stu-id="8ecea-121">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="8ecea-122">例外の種類</span><span class="sxs-lookup"><span data-stu-id="8ecea-122">Exception Type</span></span>|<span data-ttu-id="8ecea-123">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="8ecea-123">win:UnicodeString</span></span>|<span data-ttu-id="8ecea-124">例外の種類 (`System.NullReferenceException` など)。</span><span class="sxs-lookup"><span data-stu-id="8ecea-124">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="8ecea-125">例外メッセージ</span><span class="sxs-lookup"><span data-stu-id="8ecea-125">Exception Message</span></span>|<span data-ttu-id="8ecea-126">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="8ecea-126">win:UnicodeString</span></span>|<span data-ttu-id="8ecea-127">実際の例外メッセージ。</span><span class="sxs-lookup"><span data-stu-id="8ecea-127">Actual exception message.</span></span>|  
|<span data-ttu-id="8ecea-128">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="8ecea-128">EIPCodeThrow</span></span>|<span data-ttu-id="8ecea-129">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="8ecea-129">win:Pointer</span></span>|<span data-ttu-id="8ecea-130">例外が発生した命令ポインター。</span><span class="sxs-lookup"><span data-stu-id="8ecea-130">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="8ecea-131">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="8ecea-131">ExceptionHR</span></span>|<span data-ttu-id="8ecea-132">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="8ecea-132">win:UInt32</span></span>|<span data-ttu-id="8ecea-133">例外 [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a)。</span><span class="sxs-lookup"><span data-stu-id="8ecea-133">Exception [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span></span>|  
|<span data-ttu-id="8ecea-134">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="8ecea-134">ExceptionFlags</span></span>|<span data-ttu-id="8ecea-135">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="8ecea-135">win:UInt16</span></span>|<span data-ttu-id="8ecea-136">0x01: HasInnerException (Visual Basic のドキュメントで「[CLR ETW イベント](clr-etw-events.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="8ecea-136">0x01: HasInnerException (see [CLR ETW Events](clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="8ecea-137">0x02: IsNestedException。</span><span class="sxs-lookup"><span data-stu-id="8ecea-137">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="8ecea-138">0x04: IsRethrownException。</span><span class="sxs-lookup"><span data-stu-id="8ecea-138">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="8ecea-139">0x08: IsCorruptedStateException (プロセスの状態が破損していることを示します。「 [破損状態の例外の処理](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="8ecea-139">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span></span><br /><br /> <span data-ttu-id="8ecea-140">0x10: IsCLSCompliant (<xref:System.Exception> から派生した例外は CLS 準拠で、それ以外は CLS 非準拠)。</span><span class="sxs-lookup"><span data-stu-id="8ecea-140">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="8ecea-141">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="8ecea-141">ClrInstanceID</span></span>|<span data-ttu-id="8ecea-142">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="8ecea-142">win:UInt16</span></span>|<span data-ttu-id="8ecea-143">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="8ecea-143">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8ecea-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ecea-144">See also</span></span>

- [<span data-ttu-id="8ecea-145">CLR ETW イベント</span><span class="sxs-lookup"><span data-stu-id="8ecea-145">CLR ETW Events</span></span>](clr-etw-events.md)
