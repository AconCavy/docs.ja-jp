---
title: AssemblyAttributesGoHereS
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereS
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereS
helpviewer_keywords:
- AssemblyAttributesGoHereS type
- Alink API, AssemblyAttributesGoHereS type
ms.assetid: 4e817f35-a2bc-4403-9e6f-f731e6b9fe23
topic_type:
- apiref
ms.openlocfilehash: 128268bab77c8be5dc809eaa6d2548fc34f13cbd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446613"
---
# <a name="assemblyattributesgoheres"></a><span data-ttu-id="733c9-102">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="733c9-102">AssemblyAttributesGoHereS</span></span>

<span data-ttu-id="733c9-103">ALink でプレースホルダーとして使用し、カスタム属性に関する情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="733c9-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>

## <a name="syntax"></a><span data-ttu-id="733c9-104">構文</span><span class="sxs-lookup"><span data-stu-id="733c9-104">Syntax</span></span>

```csharp
internal sealed class AssemblyAttributesGoHereS
```

## <a name="remarks"></a><span data-ttu-id="733c9-105">コメント</span><span class="sxs-lookup"><span data-stu-id="733c9-105">Remarks</span></span>

<span data-ttu-id="733c9-106">この型への参照は、ソースにアセンブリのカスタム属性が含まれている netmodule 内部に埋め込まれていることがあります。</span><span class="sxs-lookup"><span data-stu-id="733c9-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="733c9-107">これらの型への参照が含まれる 1 つまたは複数の  netmodule からアセンブリ マニフェストを作成すると、ALink はこれらの参照にアタッチされた情報を使用して、実際のカスタム属性を生成します。</span><span class="sxs-lookup"><span data-stu-id="733c9-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="733c9-108">このため、この型がインスタンス化されることはなく、その型への参照はビルド処理の一部としてのみ使用され、最終的なアセンブリでは使用されません。</span><span class="sxs-lookup"><span data-stu-id="733c9-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>

<span data-ttu-id="733c9-109">この型への参照は、セキュリティに関連せず複数の用途を持たないカスタム属性を示します。</span><span class="sxs-lookup"><span data-stu-id="733c9-109">References to this type indicate custom attributes that are security related and are not multiple-use.</span></span>

<span data-ttu-id="733c9-110">これらの型は、.NET Framework 内で "internal" とマークされ、<xref:System.Runtime.CompilerServices> 名前空間に配置されます。</span><span class="sxs-lookup"><span data-stu-id="733c9-110">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span></span>

## <a name="requirements"></a><span data-ttu-id="733c9-111">要件</span><span class="sxs-lookup"><span data-stu-id="733c9-111">Requirements</span></span>

<span data-ttu-id="733c9-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="733c9-112">mscorlib.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="733c9-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="733c9-113">See also</span></span>

- [<span data-ttu-id="733c9-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="733c9-114">AssemblyAttributesGoHere</span></span>](assemblyattributesgohere.md)
- [<span data-ttu-id="733c9-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="733c9-115">AssemblyAttributesGoHereM</span></span>](assemblyattributesgoherem.md)
- [<span data-ttu-id="733c9-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="733c9-116">AssemblyAttributesGoHereSM</span></span>](assemblyattributesgoheresm.md)
