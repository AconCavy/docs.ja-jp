---
title: -unsafe (C# コンパイラ オプション)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 146299fda103567b111c66400c17edf36addd843
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "65877988"
---
# <a name="-unsafe-c-compiler-options"></a><span data-ttu-id="86571-102">-unsafe (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="86571-102">-unsafe (C# Compiler Options)</span></span>

<span data-ttu-id="86571-103">**-unsafe** コンパイラ オプションは、[unsafe](../keywords/unsafe.md) キーワードを使用するコードをコンパイルできるようにします。</span><span class="sxs-lookup"><span data-stu-id="86571-103">The **-unsafe** compiler option allows code that uses the [unsafe](../keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86571-104">構文</span><span class="sxs-lookup"><span data-stu-id="86571-104">Syntax</span></span>  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="86571-105">解説</span><span class="sxs-lookup"><span data-stu-id="86571-105">Remarks</span></span>

<span data-ttu-id="86571-106">アンセーフ コードの詳細については、「[アンセーフ コードとポインター](../../programming-guide/unsafe-code-pointers/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86571-106">For more information about unsafe code, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="86571-107">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="86571-107">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="86571-108">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="86571-108">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="86571-109">**[ビルド]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="86571-109">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="86571-110">**[アンセーフ コードの許可]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="86571-110">Select the **Allow Unsafe Code** check box.</span></span>  
  
### <a name="to-add-this-option-in-a-csproj-file"></a><span data-ttu-id="86571-111">このオプションを csproj ファイルに追加するには</span><span class="sxs-lookup"><span data-stu-id="86571-111">To add this option in a csproj file</span></span>

<span data-ttu-id="86571-112">プロジェクトの .csproj ファイルを開き、次の要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="86571-112">Open the .csproj file for a project, and add the following elements:</span></span>

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 <span data-ttu-id="86571-113">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86571-113">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86571-114">例</span><span class="sxs-lookup"><span data-stu-id="86571-114">Example</span></span>

<span data-ttu-id="86571-115">unsafe モードで `in.cs` をコンパイルする場合は、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="86571-115">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="86571-116">参照</span><span class="sxs-lookup"><span data-stu-id="86571-116">See also</span></span>

- [<span data-ttu-id="86571-117">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="86571-117">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="86571-118">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="86571-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
