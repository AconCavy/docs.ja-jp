---
title: サウンドの再生
ms.date: 07/20/2015
helpviewer_keywords:
- system sounds, playing
- system sounds
- playing sounds, Visual Basic
- sound loops
- My.Computer.Audio object, tasks
- sounds, playing
- sounds, background
- playing sounds
ms.assetid: f0d9e4ab-57c7-47b6-86d3-99ff07078040
ms.openlocfilehash: 416fedd011ff35d2b32d1b64932e3908a73ed14e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345522"
---
# <a name="playing-sounds-visual-basic"></a><span data-ttu-id="b0648-102">サウンドの再生 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0648-102">Playing Sounds (Visual Basic)</span></span>

<span data-ttu-id="b0648-103">`My.Computer.Audio` オブジェクトには、サウンドを再生するためのメソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="b0648-103">The `My.Computer.Audio` object provides methods for playing sounds.</span></span>  
  
## <a name="playing-sounds"></a><span data-ttu-id="b0648-104">サウンドの再生</span><span class="sxs-lookup"><span data-stu-id="b0648-104">Playing Sounds</span></span>  

 <span data-ttu-id="b0648-105">バックグラウンド再生により、アプリケーションでサウンドを再生しながら他のコードを実行できます。</span><span class="sxs-lookup"><span data-stu-id="b0648-105">Background playing lets the application execute other code while the sound plays.</span></span> <span data-ttu-id="b0648-106">`My.Computer.Audio.Play` メソッドを使用すると、アプリケーションでバックグラウンド サウンドを一度に 1 つだけ再生できます。アプリケーションで新しいバックグラウンド サウンドが再生されると、その前のバックグラウンド サウンドの再生は停止します。</span><span class="sxs-lookup"><span data-stu-id="b0648-106">The `My.Computer.Audio.Play` method allows the application to play only one background sound at a time; when the application plays a new background sound, it stops playing the previous background sound.</span></span> <span data-ttu-id="b0648-107">また、サウンドを再生してから、その再生が完了するまで待機することもできます。</span><span class="sxs-lookup"><span data-stu-id="b0648-107">You can also play a sound and wait for it to complete.</span></span>  
  
 <span data-ttu-id="b0648-108">次の例では、`My.Computer.Audio.Play` メソッドによってサウンドが再生されます。</span><span class="sxs-lookup"><span data-stu-id="b0648-108">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="b0648-109">`AudioPlayMode.WaitToComplete` が指定されている場合、`My.Computer.Audio.Play` はサウンドの再生が完了するまで待機し、その後呼び出し元のコードが処理を再開します。</span><span class="sxs-lookup"><span data-stu-id="b0648-109">When `AudioPlayMode.WaitToComplete` is specified, `My.Computer.Audio.Play` waits until the sound completes before calling code continues.</span></span> <span data-ttu-id="b0648-110">この例を使用する場合は、必ず自分のコンピューター上の .wav サウンド ファイルを示すファイル名を指定してください。</span><span class="sxs-lookup"><span data-stu-id="b0648-110">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer</span></span>  
  
 [!code-vb[VbVbalrMyComputer#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#15)]  
  
 <span data-ttu-id="b0648-111">次の例では、`My.Computer.Audio.Play` メソッドによってサウンドが再生されます。</span><span class="sxs-lookup"><span data-stu-id="b0648-111">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="b0648-112">この例を使用する場合は、アプリケーション リソースに Waterfall という名前の .wav サウンド ファイルが含まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b0648-112">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#16)]  
  
## <a name="playing-looping-sounds"></a><span data-ttu-id="b0648-113">ループ サウンドの再生</span><span class="sxs-lookup"><span data-stu-id="b0648-113">Playing Looping Sounds</span></span>  

 <span data-ttu-id="b0648-114">次の例では、`My.Computer.Audio.Play` が指定されている場合に、指定されているサウンドが `PlayMode.BackgroundLoop` メソッドによってバックグラウンドで再生されます。</span><span class="sxs-lookup"><span data-stu-id="b0648-114">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="b0648-115">この例を使用する場合は、必ず自分のコンピューター上の .wav サウンド ファイルを示すファイル名を指定してください。</span><span class="sxs-lookup"><span data-stu-id="b0648-115">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#11)]  
  
 <span data-ttu-id="b0648-116">次の例では、`My.Computer.Audio.Play` が指定されている場合に、指定されているサウンドが `PlayMode.BackgroundLoop` メソッドによってバックグラウンドで再生されます。</span><span class="sxs-lookup"><span data-stu-id="b0648-116">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="b0648-117">この例を使用する場合は、アプリケーション リソースに Waterfall という名前の .wav サウンド ファイルが含まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b0648-117">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#12)]  
  
 <span data-ttu-id="b0648-118">上記のコード例は、IntelliSense コード スニペットとしても利用できます。</span><span class="sxs-lookup"><span data-stu-id="b0648-118">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="b0648-119">コード スニペット ピッカーでこのスニペットにアクセスするには、 **[Windows フォーム アプリケーション]、[サウンド]** の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="b0648-119">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="b0648-120">詳細については、「 [Code Snippets](/visualstudio/ide/code-snippets)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0648-120">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="b0648-121">一般に、アプリケーションでループ サウンドを再生する場合は、最終的にそのサウンドを停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0648-121">In general, when an application plays a looping sound, it should eventually stop the sound.</span></span>  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a><span data-ttu-id="b0648-122">バックグラウンドで再生しているサウンドの停止</span><span class="sxs-lookup"><span data-stu-id="b0648-122">Stopping the Playing of Sounds in the Background</span></span>  

 <span data-ttu-id="b0648-123">`My.Computer.Audio.Stop` メソッドを使用し、アプリケーションで現在再生中のバックグラウンド サウンドまたはループ サウンドを停止します。</span><span class="sxs-lookup"><span data-stu-id="b0648-123">Use the `My.Computer.Audio.Stop` method to stop the application's currently playing background or looping sound.</span></span>  
  
 <span data-ttu-id="b0648-124">一般に、アプリケーションでループ サウンドを再生する場合は、どこかの時点でそのサウンドを停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0648-124">In general, when an application plays a looping sound, it should stop the sound at some point.</span></span>  
  
 <span data-ttu-id="b0648-125">次の例では、バックグラウンドで再生中のサウンドを停止します。</span><span class="sxs-lookup"><span data-stu-id="b0648-125">The following example stops a sound that is playing in the background.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#18)]  
  
 <span data-ttu-id="b0648-126">上記のコード例は、IntelliSense コード スニペットとしても利用できます。</span><span class="sxs-lookup"><span data-stu-id="b0648-126">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="b0648-127">コード スニペット ピッカーでこのスニペットにアクセスするには、 **[Windows フォーム アプリケーション]、[サウンド]** の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="b0648-127">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="b0648-128">詳細については、「 [Code Snippets](/visualstudio/ide/code-snippets)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0648-128">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="playing-system-sounds"></a><span data-ttu-id="b0648-129">システム サウンドの再生</span><span class="sxs-lookup"><span data-stu-id="b0648-129">Playing System Sounds</span></span>  

 <span data-ttu-id="b0648-130">`My.Computer.Audio.PlaySystemSound` メソッドを使用して、指定したシステム サウンドを再生します。</span><span class="sxs-lookup"><span data-stu-id="b0648-130">Use the `My.Computer.Audio.PlaySystemSound` method to play the specified system sound.</span></span>  
  
 <span data-ttu-id="b0648-131">`My.Computer.Audio.PlaySystemSound` メソッドは、<xref:System.Media.SystemSound> クラスのいずれかの共有メンバーをパラメーターとして受け取ります。</span><span class="sxs-lookup"><span data-stu-id="b0648-131">The `My.Computer.Audio.PlaySystemSound` method takes as a parameter one of the shared members from the <xref:System.Media.SystemSound> class.</span></span> <span data-ttu-id="b0648-132">システム サウンド <xref:System.Media.SystemSounds.Asterisk%2A> は、一般にエラーを表します。</span><span class="sxs-lookup"><span data-stu-id="b0648-132">The system sound <xref:System.Media.SystemSounds.Asterisk%2A> generally denotes errors.</span></span>  
  
 <span data-ttu-id="b0648-133">次の例では、`My.Computer.Audio.PlaySystemSound` メソッドを使用してシステム サウンドを再生しています。</span><span class="sxs-lookup"><span data-stu-id="b0648-133">The following example uses the `My.Computer.Audio.PlaySystemSound` method to play a system sound.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="b0648-134">参照</span><span class="sxs-lookup"><span data-stu-id="b0648-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>
- <xref:Microsoft.VisualBasic.AudioPlayMode>
