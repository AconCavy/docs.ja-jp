---
title: '方法: アセンブリを他のアプリケーションと共有する'
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: b4c183c3fc0b04121be8bbc2db4027887cbc3132
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644292"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a><span data-ttu-id="06985-102">方法: アセンブリを他のアプリケーションと共有する</span><span class="sxs-lookup"><span data-stu-id="06985-102">How to: Share an assembly with other applications</span></span>
<span data-ttu-id="06985-103">アセンブリはプライベートまたは共有にすることができます。既定では、ほとんどの単純なプログラムは、他のアプリケーションによって使われることを意図されていないので、プライベート アセンブリで構成されます。</span><span class="sxs-lookup"><span data-stu-id="06985-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  

<span data-ttu-id="06985-104">他のアプリケーションとアセンブリを共有するには、[グローバル アセンブリ キャッシュ (GAC)](gac.md) にアセンブリを置く必要があります。</span><span class="sxs-lookup"><span data-stu-id="06985-104">In order to share an assembly with other applications, it must be placed in the [global assembly cache (GAC)](gac.md).</span></span>  
  
<span data-ttu-id="06985-105">アセンブリを共有するには:</span><span class="sxs-lookup"><span data-stu-id="06985-105">To share an assembly:</span></span>
  
1. <span data-ttu-id="06985-106">アセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="06985-106">Create your assembly.</span></span> <span data-ttu-id="06985-107">詳しくは、「[アセンブリを作成する](../../standard/assembly/create.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="06985-107">For more information, see [Create assemblies](../../standard/assembly/create.md).</span></span>  
  
2. <span data-ttu-id="06985-108">アセンブリに厳密な名前を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="06985-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="06985-109">詳細については、[厳密な名前でアセンブリに署名する](../../standard/assembly/sign-strong-name.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06985-109">For more information, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>  
  
3. <span data-ttu-id="06985-110">アセンブリにバージョン情報を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="06985-110">Assign version information to your assembly.</span></span> <span data-ttu-id="06985-111">詳細については、「[アセンブリのバージョン管理](../../standard/assembly/versioning.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06985-111">For more information, see [Assembly versioning](../../standard/assembly/versioning.md).</span></span>  
  
4. <span data-ttu-id="06985-112">グローバル アセンブリ キャッシュにアセンブリを追加します。</span><span class="sxs-lookup"><span data-stu-id="06985-112">Add your assembly to the global assembly cache.</span></span> <span data-ttu-id="06985-113">詳細については、[アセンブリをグローバル アセンブリ キャッシュにインストールする](install-assembly-into-gac.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06985-113">For more information, see [How to: Install an assembly into the global assembly cache](install-assembly-into-gac.md).</span></span>  
  
5. <span data-ttu-id="06985-114">他のアプリケーションからアセンブリに含まれる型にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="06985-114">Access the types contained in the assembly from other applications.</span></span> <span data-ttu-id="06985-115">詳細については、[厳密な名前のアセンブリを参照する](../../standard/assembly/reference-strong-named.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06985-115">For more information, see [How to: Reference a strong-named assembly](../../standard/assembly/reference-strong-named.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06985-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="06985-116">See also</span></span>

- [<span data-ttu-id="06985-117">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="06985-117">C# programming guide</span></span>](../../../api/index.md)
- [<span data-ttu-id="06985-118">プログラミングの概念 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06985-118">Programming concepts (Visual Basic)</span></span>](../../../api/index.md)
- [<span data-ttu-id="06985-119">アセンブリを使用したプログラム</span><span class="sxs-lookup"><span data-stu-id="06985-119">Program with assemblies</span></span>](../../standard/assembly/index.md)
