---
title: <disableCommitThreadStack> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCommitThreadStack
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCommitThreadStack
helpviewer_keywords:
- <disableCommitThreadStack> element
- disableCommitThreadStack element
ms.assetid: 3559d46a-7640-4c72-9a11-7e980768929e
ms.openlocfilehash: 8aefb8a20d6a95c5b8062d0c03dcb28a3557ca3d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117474"
---
# <a name="disablecommitthreadstack-element"></a><span data-ttu-id="e6c00-102">\<disableCommitThreadStack> 要素</span><span class="sxs-lookup"><span data-stu-id="e6c00-102">\<disableCommitThreadStack> Element</span></span>
<span data-ttu-id="e6c00-103">スレッドの起動時にスレッド スタック全体をコミットするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e6c00-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCommitThreadStack>**  
  
## <a name="syntax"></a><span data-ttu-id="e6c00-104">構文</span><span class="sxs-lookup"><span data-stu-id="e6c00-104">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6c00-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e6c00-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e6c00-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e6c00-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6c00-107">属性</span><span class="sxs-lookup"><span data-stu-id="e6c00-107">Attributes</span></span>  
  
|<span data-ttu-id="e6c00-108">属性</span><span class="sxs-lookup"><span data-stu-id="e6c00-108">Attribute</span></span>|<span data-ttu-id="e6c00-109">説明</span><span class="sxs-lookup"><span data-stu-id="e6c00-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e6c00-110">enabled</span><span class="sxs-lookup"><span data-stu-id="e6c00-110">enabled</span></span>|<span data-ttu-id="e6c00-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="e6c00-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="e6c00-112">スレッド起動時にスレッド スタック全体をコミットすること (既定の動作) を無効にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e6c00-112">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e6c00-113">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="e6c00-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="e6c00-114">値</span><span class="sxs-lookup"><span data-stu-id="e6c00-114">Value</span></span>|<span data-ttu-id="e6c00-115">説明</span><span class="sxs-lookup"><span data-stu-id="e6c00-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e6c00-116">0</span><span class="sxs-lookup"><span data-stu-id="e6c00-116">0</span></span>|<span data-ttu-id="e6c00-117">共通言語ランタイムの既定の動作 (スレッドの起動時にスレッド スタック全体をコミット) を無効にしません。</span><span class="sxs-lookup"><span data-stu-id="e6c00-117">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="e6c00-118">1</span><span class="sxs-lookup"><span data-stu-id="e6c00-118">1</span></span>|<span data-ttu-id="e6c00-119">共通言語ランタイムの既定の動作 (スレッドの起動時にスレッド スタック全体をコミット) を無効にします。</span><span class="sxs-lookup"><span data-stu-id="e6c00-119">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6c00-120">子要素</span><span class="sxs-lookup"><span data-stu-id="e6c00-120">Child Elements</span></span>  
 <span data-ttu-id="e6c00-121">なし。</span><span class="sxs-lookup"><span data-stu-id="e6c00-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e6c00-122">親要素</span><span class="sxs-lookup"><span data-stu-id="e6c00-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e6c00-123">要素</span><span class="sxs-lookup"><span data-stu-id="e6c00-123">Element</span></span>|<span data-ttu-id="e6c00-124">Description</span><span class="sxs-lookup"><span data-stu-id="e6c00-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e6c00-125">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="e6c00-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e6c00-126">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e6c00-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6c00-127">解説</span><span class="sxs-lookup"><span data-stu-id="e6c00-127">Remarks</span></span>  
 <span data-ttu-id="e6c00-128">共通言語ランタイムの既定の動作では、スレッドの起動時にスレッド スタック全体がコミットされます。</span><span class="sxs-lookup"><span data-stu-id="e6c00-128">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="e6c00-129">メモリが限られているサーバーで多数のスレッドが作成する必要があり、それらのスレッドのほとんどがごくわずかのスタック スペースしか使用しない場合は、スレッドの起動時に共通言語ランタイムが直ちにスレッド スタック全体をコミットしなければ、サーバーのパフォーマンスが向上する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e6c00-129">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e6c00-130">アンマネージ ホストは、 `STARTUP_DISABLE_COMMITTHREADSTACK` STARTUP_FLAGS [列挙体の](../../../unmanaged-api/hosting/startup-flags-enumeration.md) 起動フラグを使用することにより、同じ結果を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="e6c00-130">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6c00-131">例</span><span class="sxs-lookup"><span data-stu-id="e6c00-131">Example</span></span>  
 <span data-ttu-id="e6c00-132">次の例は、共通言語ランタイムの既定の動作 (スレッド起動時にスレッド スタック全体をコミット) を無効にする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="e6c00-132">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e6c00-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="e6c00-133">See also</span></span>

- [<span data-ttu-id="e6c00-134">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="e6c00-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e6c00-135">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="e6c00-135">Configuration File Schema</span></span>](../index.md)
