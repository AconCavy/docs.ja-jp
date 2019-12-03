---
title: アセンブリの場所の指定
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: f13b19dcd0aceac969d9639e6230ad33c6cd8d84
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971546"
---
# <a name="specifying-an-assemblys-location"></a><span data-ttu-id="86082-102">アセンブリの場所の指定</span><span class="sxs-lookup"><span data-stu-id="86082-102">Specifying an Assembly's Location</span></span>
<span data-ttu-id="86082-103">アセンブリの場所を指定するには、次の2つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="86082-103">There are two ways to specify an assembly's location:</span></span>  
  
- <span data-ttu-id="86082-104">[ \<codeBase>](./file-schema/runtime/codebase-element.md) 要素を使用</span><span class="sxs-lookup"><span data-stu-id="86082-104">Using the [\<codeBase>](./file-schema/runtime/codebase-element.md) element.</span></span>  
  
- <span data-ttu-id="86082-105">[\<probing>](./file-schema/runtime/probing-element.md) 要素を使用</span><span class="sxs-lookup"><span data-stu-id="86082-105">Using the [\<probing>](./file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="86082-106">また、 [.NET Framework 構成ツール (mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100))を使用して、アセンブリの場所を指定したり、共通言語ランタイムがアセンブリをプローブする場所を指定したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="86082-106">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="86082-107">\<codeBase> 要素の使用</span><span class="sxs-lookup"><span data-stu-id="86082-107">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="86082-108">**\<コードベース >** 要素は、アセンブリのバージョンをリダイレクトするマシン構成または発行者ポリシーファイルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="86082-108">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="86082-109">使用するアセンブリバージョンをランタイムが決定すると、バージョンを決定するファイルのコードベース設定が適用されます。</span><span class="sxs-lookup"><span data-stu-id="86082-109">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="86082-110">コードベースが指定されていない場合、ランタイムは通常の方法でアセンブリをプローブします。</span><span class="sxs-lookup"><span data-stu-id="86082-110">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="86082-111">詳細については、「[ランタイムがアセンブリを検索する方法](../deployment/how-the-runtime-locates-assemblies.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86082-111">For details, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="86082-112">アセンブリの場所を指定する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="86082-112">The following example shows how to specify an assembly's location.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <codeBase version="2.0.0.0"  
                   href="http://www.litwareinc.com/myAssembly.dll"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="86082-113">**Version**属性は、厳密な名前を持つすべてのアセンブリに必要ですが、厳密な名前ではないアセンブリでは省略する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86082-113">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="86082-114">**\<CodeBase>** 要素が必要です、 **href** 属性。</span><span class="sxs-lookup"><span data-stu-id="86082-114">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="86082-115">コードベースの > 要素で **\<** バージョン範囲を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="86082-115">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="86082-116">厳密な名前が付けられていないアセンブリのコードベースヒントを指定する場合、ヒントはアプリケーションベースディレクトリのアプリケーションベースまたはサブディレクトリをポイントする必要があります。</span><span class="sxs-lookup"><span data-stu-id="86082-116">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="86082-117">\<probing> 要素の使用</span><span class="sxs-lookup"><span data-stu-id="86082-117">Using the \<probing> Element</span></span>  
 <span data-ttu-id="86082-118">実行時に、プローブによってコードベースのないアセンブリが検索されます。</span><span class="sxs-lookup"><span data-stu-id="86082-118">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="86082-119">プローブの詳細については、「[ランタイムがアセンブリを検索する方法](../deployment/how-the-runtime-locates-assemblies.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86082-119">For more information about probing, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="86082-120">アプリケーション構成ファイルの[\<probing>](./file-schema/runtime/probing-element.md)要素を使用して、アセンブリを検索するときにランタイムが検索する必要があるサブディレクトリを指定できます。</span><span class="sxs-lookup"><span data-stu-id="86082-120">You can use the [\<probing>](./file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="86082-121">次の例は、ランタイムが検索するディレクトリを指定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="86082-121">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="86082-122">**PrivatePath**属性には、ランタイムがアセンブリを検索するディレクトリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="86082-122">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="86082-123">アプリケーションが C:\Program Files\MyApp に配置されている場合、ランタイムは C:\Program Files\MyApp\Bin、C:\Program Files\MyApp\Bin2\Subbin、および C:\Program Files\MyApp\Bin3. でコードベースを指定していないアセンブリを検索します。</span><span class="sxs-lookup"><span data-stu-id="86082-123">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="86082-124">**PrivatePath**に指定されたディレクトリは、アプリケーションのベースディレクトリのサブディレクトリである必要があります。</span><span class="sxs-lookup"><span data-stu-id="86082-124">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86082-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="86082-125">See also</span></span>

- [<span data-ttu-id="86082-126">.NET のアセンブリ</span><span class="sxs-lookup"><span data-stu-id="86082-126">Assemblies in .NET</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="86082-127">アセンブリを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="86082-127">Programming with Assemblies</span></span>](../../standard/assembly/program.md)
- [<span data-ttu-id="86082-128">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="86082-128">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="86082-129">構成ファイルを使用したアプリの構成</span><span class="sxs-lookup"><span data-stu-id="86082-129">Configuring Apps by using Configuration Files</span></span>](index.md)
