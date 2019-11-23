---
title: 構成セクションのスキーマ
ms.date: 05/02/2017
helpviewer_keywords:
- configuration settings [.NET Framework], custom
- schema configuration settings
- configuration sections [.NET Framework]
- custom elements
- configuration schema [.NET Framework], custom settings in configuration files
- elements [.NET Framework], custom settings in configuration files
ms.assetid: 6e4cc793-c526-4007-b4e9-37d56295f2cb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a17d30af9d7abc3eea6b87d5e8768ac49a7c05ab
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118927"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="5bab5-102">構成セクションのスキーマ</span><span class="sxs-lookup"><span data-stu-id="5bab5-102">Configuration sections schema</span></span>

<span data-ttu-id="5bab5-103">構成セクションスキーマには、構成ファイルのカスタム設定を定義する要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5bab5-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="5bab5-104">構成ファイルとスキーマに関する一般的な情報については、 [.NET Framework の構成ファイルスキーマ](index.md)に関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5bab5-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](index.md).</span></span>

<span data-ttu-id="5bab5-105">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="5bab5-105">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="5bab5-106">[ **\<configSections >** ](configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="5bab5-106">[**\<configSections>**](configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="5bab5-107">[ **\<clear>** ](clear-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="5bab5-107">[**\<clear>**](clear-element-for-configsections.md) </span></span>  
<span data-ttu-id="5bab5-108">[ **\<remove>** ](remove-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="5bab5-108">[**\<remove>**](remove-element-for-configsections.md) </span></span>  
<span data-ttu-id="5bab5-109">[ **\<section>** ](section-element.md) </span><span class="sxs-lookup"><span data-stu-id="5bab5-109">[**\<section>**](section-element.md) </span></span>  
[<span data-ttu-id="5bab5-110"> **\<sectionGroup >** </span><span class="sxs-lookup"><span data-stu-id="5bab5-110">**\<sectionGroup>**</span></span>](sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="5bab5-111">説明</span><span class="sxs-lookup"><span data-stu-id="5bab5-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="5bab5-112"> **\<configSections >** の **\<clear>** </span><span class="sxs-lookup"><span data-stu-id="5bab5-112">**\<clear>** for **\<configSections>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="5bab5-113">以前に定義したセクションとセクショングループをすべて消去します。</span><span class="sxs-lookup"><span data-stu-id="5bab5-113">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="5bab5-114"> **\<clear>** </span><span class="sxs-lookup"><span data-stu-id="5bab5-114">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="5bab5-115">以前に定義したセクションとセクショングループをすべて消去します。</span><span class="sxs-lookup"><span data-stu-id="5bab5-115">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="5bab5-116"> **\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="5bab5-116">**\<configSections>**</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="5bab5-117">構成セクションと名前空間の宣言が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5bab5-117">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="5bab5-118"> **\<remove>** の **\<configSections>** </span><span class="sxs-lookup"><span data-stu-id="5bab5-118">**\<remove>** for **\<configSections>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="5bab5-119">定義済みのセクション、またはセクション グループを削除します。</span><span class="sxs-lookup"><span data-stu-id="5bab5-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="5bab5-120"> **\<section>** の **\<configSections >** と **\<sectionGroup >** </span><span class="sxs-lookup"><span data-stu-id="5bab5-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](section-element.md) | <span data-ttu-id="5bab5-121">構成セクションの宣言が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5bab5-121">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="5bab5-122"> **\<configSections**の **\<sectionGroup >** ></span><span class="sxs-lookup"><span data-stu-id="5bab5-122">**\<sectionGroup>** for **\<configSections>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="5bab5-123">構成セクションの名前空間を定義します。</span><span class="sxs-lookup"><span data-stu-id="5bab5-123">Defines a namespace for configuration sections.</span></span> |
