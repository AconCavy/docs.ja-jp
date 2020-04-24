---
title: ドライブ、ディレクトリ、およびファイルの処理
ms.date: 07/20/2015
helpviewer_keywords:
- drives
- drives, processing
- Visual Basic code, file access
- files [Visual Basic], processing
- files [Visual Basic], accessing
- directories [Visual Studio], processing
ms.assetid: f1db14c8-a4fd-4d0b-8323-c7cb29d688c2
ms.openlocfilehash: 790cf5aa2d3fde779fcc24c0c9f1fc9c4c42331b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "74333947"
---
# <a name="processing-drives-directories-and-files-visual-basic"></a><span data-ttu-id="4f962-102">ドライブ、ディレクトリ、およびファイルの処理 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f962-102">Processing Drives, Directories, and Files (Visual Basic)</span></span>

<span data-ttu-id="4f962-103">Visual Basic では、`My.Computer.FileSystem` オブジェクトを使用して、ドライブ、フォルダー、ファイルを処理できます。このオブジェクトは、`FileOpen` 関数や `Write` 関数などの従来のメソッドに比べて、パフォーマンスが優れており、使い方も簡単です (従来のメソッドも引き続き使用できます)。</span><span class="sxs-lookup"><span data-stu-id="4f962-103">You can use Visual Basic to process drives, folders, and files with the `My.Computer.FileSystem` object, which provides better performance and is easier to use than traditional methods such as the `FileOpen` and `Write` functions (although they are still available).</span></span> <span data-ttu-id="4f962-104">以下のセクションでは、これらの方法について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="4f962-104">The following sections discuss these methods in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4f962-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="4f962-105">In This Section</span></span>  

 [<span data-ttu-id="4f962-106">Visual Basic におけるファイル アクセス</span><span class="sxs-lookup"><span data-stu-id="4f962-106">File Access with Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)  
 <span data-ttu-id="4f962-107">`My.Computer.FileSystem` オブジェクトを使ってファイル、ドライブ、フォルダーを処理する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="4f962-107">Discusses how to use the `My.Computer.FileSystem` object to work with files, drives, and folders.</span></span>  
  
 [<span data-ttu-id="4f962-108">.NET Framework のファイル I/O とファイル システムの基礎 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f962-108">Basics of .NET Framework File I/O and the File System (Visual Basic)</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)  
 <span data-ttu-id="4f962-109">ストリーム、分離ストレージ、ファイル イベント、ファイル属性、ファイル アクセスなど、.NET Framework におけるファイル I/O の考え方の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="4f962-109">Provides an overview of file I/O concepts in the .NET Framework, including streams, isolated storage, file events, file attributes, and file access.</span></span>  
  
 [<span data-ttu-id="4f962-110">チュートリアル: .NET Framework のメソッドによるファイル操作</span><span class="sxs-lookup"><span data-stu-id="4f962-110">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)  
 <span data-ttu-id="4f962-111">.NET Framework を使用してファイルやフォルダーを操作する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="4f962-111">Demonstrates how to use the .NET Framework to manipulate files and folders.</span></span>  
  
 [<span data-ttu-id="4f962-112">チュートリアル: Visual Basic によるファイルとディレクトリの操作</span><span class="sxs-lookup"><span data-stu-id="4f962-112">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="4f962-113">`My.Computer.FileSystem` オブジェクトを使用してファイルやフォルダーを操作する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="4f962-113">Demonstrates how to use the `My.Computer.FileSystem` object to manipulate files and folders.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4f962-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f962-114">Related Sections</span></span>  

 [<span data-ttu-id="4f962-115">プログラム構造とコード規則</span><span class="sxs-lookup"><span data-stu-id="4f962-115">Program Structure and Code Conventions</span></span>](../../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 <span data-ttu-id="4f962-116">プログラムの物理構造と外観のガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="4f962-116">Provides guidelines for the physical structure and appearance of programs.</span></span>  
  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <span data-ttu-id="4f962-117">`My.Computer.FileSystem` オブジェクトとそのメンバーのリファレンス ドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="4f962-117">Reference documentation for the `My.Computer.FileSystem` object and its members.</span></span>
