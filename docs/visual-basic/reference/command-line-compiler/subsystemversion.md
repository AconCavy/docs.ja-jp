---
title: -subsystemversion
ms.date: 03/13/2018
helpviewer_keywords:
- /subsystemversion compiler option [Visual Basic]
- -subsystemversion compiler option [Visual Basic]
- subsystemversion compiler option [Visual Basic]
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
ms.openlocfilehash: e8607f8254783b5486b02ccc4c7e4081da506fae
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802151"
---
# <a name="-subsystemversion-visual-basic"></a><span data-ttu-id="85b48-102">-subsystemversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85b48-102">-subsystemversion (Visual Basic)</span></span>

<span data-ttu-id="85b48-103">生成された実行可能ファイルが動作できるサブシステムの最小バージョンを指定します。これにより、実行可能ファイルが動作できる Windows のバージョンが決まります。</span><span class="sxs-lookup"><span data-stu-id="85b48-103">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="85b48-104">通常、このオプションを指定することで、実行可能ファイルが、Windows の以前のバージョンでは使用できない特定のセキュリティ機能を利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="85b48-104">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="85b48-105">サブシステム自体を指定するには、[-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) のコンパイラ オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="85b48-105">To specify the subsystem itself, use the [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) compiler option.</span></span>

## <a name="syntax"></a><span data-ttu-id="85b48-106">構文</span><span class="sxs-lookup"><span data-stu-id="85b48-106">Syntax</span></span>

```vb
-subsystemversion:major.minor
```

## <a name="parameters"></a><span data-ttu-id="85b48-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="85b48-107">Parameters</span></span>

`major.minor`

<span data-ttu-id="85b48-108">サブシステムに必要な最小バージョン。メジャー バージョンおよびマイナー バージョンのドット表記で表されます。</span><span class="sxs-lookup"><span data-stu-id="85b48-108">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="85b48-109">たとえば、このオプションの値を 6.01 に設定すると、Windows 7 より古いオペレーティング システムではアプリケーションを実行できないように指定できます (このトピックの以下の表を参照)。</span><span class="sxs-lookup"><span data-stu-id="85b48-109">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="85b48-110">`major` と `minor` の値を整数で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="85b48-110">You must specify the values for `major` and `minor` as integers.</span></span>

<span data-ttu-id="85b48-111">`minor` バージョンでは、前に配置されるゼロによってバージョンが変更されることはありませんが、後ろにゼロが付くとバージョンが変わります。</span><span class="sxs-lookup"><span data-stu-id="85b48-111">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="85b48-112">たとえば、6.1 と 6.01 は同じバージョンを示しますが、6.10 は異なるバージョンを示します。</span><span class="sxs-lookup"><span data-stu-id="85b48-112">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="85b48-113">混乱を避けるため、マイナー バージョンには 2 桁の数値を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="85b48-113">We recommend expressing the minor version as two digits to avoid confusion.</span></span>

## <a name="remarks"></a><span data-ttu-id="85b48-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="85b48-114">Remarks</span></span>

<span data-ttu-id="85b48-115">次の表は、Windows の一般的なサブシステムのバージョンを示しています。</span><span class="sxs-lookup"><span data-stu-id="85b48-115">The following table lists common subsystem versions of Windows.</span></span>

|<span data-ttu-id="85b48-116">Windows のバージョン</span><span class="sxs-lookup"><span data-stu-id="85b48-116">Windows version</span></span>|<span data-ttu-id="85b48-117">サブシステムのバージョン</span><span class="sxs-lookup"><span data-stu-id="85b48-117">Subsystem version</span></span>|
|---------------------|-----------------------|
|<span data-ttu-id="85b48-118">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="85b48-118">Windows 2000</span></span>|<span data-ttu-id="85b48-119">5.00</span><span class="sxs-lookup"><span data-stu-id="85b48-119">5.00</span></span>|
|<span data-ttu-id="85b48-120">Windows XP</span><span class="sxs-lookup"><span data-stu-id="85b48-120">Windows XP</span></span>|<span data-ttu-id="85b48-121">5.01</span><span class="sxs-lookup"><span data-stu-id="85b48-121">5.01</span></span>|
|<span data-ttu-id="85b48-122">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="85b48-122">Windows Server 2003</span></span>|<span data-ttu-id="85b48-123">5.02</span><span class="sxs-lookup"><span data-stu-id="85b48-123">5.02</span></span>|
|<span data-ttu-id="85b48-124">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="85b48-124">Windows Vista</span></span>|<span data-ttu-id="85b48-125">6.00</span><span class="sxs-lookup"><span data-stu-id="85b48-125">6.00</span></span>|
|<span data-ttu-id="85b48-126">Windows 7</span><span class="sxs-lookup"><span data-stu-id="85b48-126">Windows 7</span></span>|<span data-ttu-id="85b48-127">6.01</span><span class="sxs-lookup"><span data-stu-id="85b48-127">6.01</span></span>|
|<span data-ttu-id="85b48-128">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="85b48-128">Windows Server 2008</span></span>|<span data-ttu-id="85b48-129">6.01</span><span class="sxs-lookup"><span data-stu-id="85b48-129">6.01</span></span>|
|<span data-ttu-id="85b48-130">Windows 8</span><span class="sxs-lookup"><span data-stu-id="85b48-130">Windows 8</span></span>|<span data-ttu-id="85b48-131">6.02</span><span class="sxs-lookup"><span data-stu-id="85b48-131">6.02</span></span>|

## <a name="default-values"></a><span data-ttu-id="85b48-132">既定の値</span><span class="sxs-lookup"><span data-stu-id="85b48-132">Default values</span></span>

<span data-ttu-id="85b48-133">**-subsystemversion** コンパイラ オプションの既定値は条件によって異なります。その条件を次に示します。</span><span class="sxs-lookup"><span data-stu-id="85b48-133">The default value of the **-subsystemversion** compiler option depends on the conditions in the following list:</span></span>

- <span data-ttu-id="85b48-134">次のコンパイラ オプションのいずれかが設定されている場合、既定値は 6.02 です。</span><span class="sxs-lookup"><span data-stu-id="85b48-134">The default value is 6.02 if any compiler option in the following list is set:</span></span>

  - [<span data-ttu-id="85b48-135">/target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="85b48-135">-target:appcontainerexe</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)

  - [<span data-ttu-id="85b48-136">/target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="85b48-136">-target:winmdobj</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)

  - [<span data-ttu-id="85b48-137">-platform:arm</span><span class="sxs-lookup"><span data-stu-id="85b48-137">-platform:arm</span></span>](../../../visual-basic/reference/command-line-compiler/platform.md)

- <span data-ttu-id="85b48-138">MSBuild を使用しており、.NET Framework 4.5 が対象で、さらにこの一覧で前に指定したコンパイラ オプションを設定していない場合、既定値は 6.00 です。</span><span class="sxs-lookup"><span data-stu-id="85b48-138">The default value is 6.00 if you're using MSBuild, you're targeting .NET Framework 4.5, and you haven't set any of the compiler options that were specified earlier in this list.</span></span>

- <span data-ttu-id="85b48-139">上記の条件がどれも当てはまらない場合、既定値は 4.00 です。</span><span class="sxs-lookup"><span data-stu-id="85b48-139">The default value is 4.00 if none of the previous conditions is true.</span></span>

## <a name="setting-this-option"></a><span data-ttu-id="85b48-140">このオプションを設定する</span><span class="sxs-lookup"><span data-stu-id="85b48-140">Setting this option</span></span>

<span data-ttu-id="85b48-141">Visual Studio で **-subsystemversion**コンパイラオプションを設定するには、.vbproj ファイルを開き、MSBuild XML で `SubsystemVersion` プロパティの値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="85b48-141">To set the **-subsystemversion** compiler option in Visual Studio, you must open the .vbproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="85b48-142">Visual Studio IDE でこのオプションを設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="85b48-142">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="85b48-143">詳細については、このトピックの「既定値」または「[MSBuild プロジェクトの共通プロパティ](/visualstudio/msbuild/common-msbuild-project-properties)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85b48-143">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="see-also"></a><span data-ttu-id="85b48-144">参照</span><span class="sxs-lookup"><span data-stu-id="85b48-144">See also</span></span>

- [<span data-ttu-id="85b48-145">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="85b48-145">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)

- [<span data-ttu-id="85b48-146">MSBuild プロパティ</span><span class="sxs-lookup"><span data-stu-id="85b48-146">MSBuild Properties</span></span>](/visualstudio/msbuild/msbuild-properties)
