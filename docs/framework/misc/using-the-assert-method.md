---
title: Assert メソッドの使用
description: Assert メソッドを使用して、コード (および下流の呼び出し元のコード) でコードがアクセス許可を持っていても、その呼び出し元にはアクセスできないようにする方法について説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- granting permissions, overriding security checks
- code access security, overriding security checks
- overriding security checks
- security [.NET Framework], overriding security checks
- security [.NET Framework], assertions
- asserted permissions
- Assert method
- caller security checks
- permissions [.NET Framework], overriding security checks
- permissions [.NET Framework], assertions
ms.assetid: 1e40f4d3-fb7d-4f19-b334-b6076d469ea9
ms.openlocfilehash: 096e0375a94c92a835cccb4d1b3297783b4120e9
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309808"
---
# <a name="using-the-assert-method"></a><span data-ttu-id="95256-103">Assert メソッドの使用</span><span class="sxs-lookup"><span data-stu-id="95256-103">Using the Assert Method</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="95256-104"><xref:System.Security.CodeAccessPermission.Assert%2A> は、コードのアクセス許可のクラスおよび <xref:System.Security.PermissionSet>クラスで呼び出すことができるメソッドです。</span><span class="sxs-lookup"><span data-stu-id="95256-104"><xref:System.Security.CodeAccessPermission.Assert%2A> is a method that can be called on code access permission classes and on the <xref:System.Security.PermissionSet> class.</span></span> <span data-ttu-id="95256-105">**Assert**を使用すると、コード (および下流の呼び出し元) が、コードが実行するアクセス許可を持っているものの、その呼び出し元が実行するアクセス許可を持っていないアクションを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="95256-105">You can use **Assert** to enable your code (and downstream callers) to perform actions that your code has permission to do but its callers might not have permission to do.</span></span> <span data-ttu-id="95256-106">セキュリティ アサーションは、セキュリティ チェック時にランタイムが実行する正常なプロセスを変更します。</span><span class="sxs-lookup"><span data-stu-id="95256-106">A security assertion changes the normal process that the runtime performs during a security check.</span></span> <span data-ttu-id="95256-107">アクセス許可をアサートすると、アサートされたアクセス許可のためにコードの呼び出し元をチェックしないようセキュリティ システムに指示します。</span><span class="sxs-lookup"><span data-stu-id="95256-107">When you assert a permission, it tells the security system not to check the callers of your code for the asserted permission.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="95256-108">アサーションはセキュリティ ホールを開き、セキュリティの制限事項を適用するランタイムのメカニズムを弱体化させる可能性があるため、慎重に使用してください。</span><span class="sxs-lookup"><span data-stu-id="95256-108">Use assertions carefully because they can open security holes and undermine the runtime's mechanism for enforcing security restrictions.</span></span>  
  
 <span data-ttu-id="95256-109">アサーションは、ライブラリがアンマネージ コードを呼び出す状況、またはライブラリの使用目的と明らかに関係のないアクセス許可を必要とする呼び出しを行う状況に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="95256-109">Assertions are useful in situations in which a library calls into unmanaged code or makes a call that requires a permission that is not obviously related to the library's intended use.</span></span> <span data-ttu-id="95256-110">たとえば、アンマネージコードを呼び出すすべてのマネージコードは、 **UnmanagedCode**フラグが指定された**SecurityPermission**を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="95256-110">For example, all managed code that calls into unmanaged code must have **SecurityPermission** with the **UnmanagedCode** flag specified.</span></span> <span data-ttu-id="95256-111">ローカルのイントラネットからダウンロードするコードなど、ローカル コンピューターから発生していないコードには、既定でこのアクセス許可は付与されません。</span><span class="sxs-lookup"><span data-stu-id="95256-111">Code that does not originate from the local computer, such as code that is downloaded from the local intranet, will not be granted this permission by default.</span></span> <span data-ttu-id="95256-112">そのため、ローカルのイントラネットからダウンロードするコードがアンマネージ コードを使用するライブラリを呼び出せるようにするには、ライブラリによってアサートされたアクセス許可がコードに指定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="95256-112">Therefore, in order for code that is downloaded from the local intranet to be able to call a library that uses unmanaged code, it must have the permission asserted by the library.</span></span> <span data-ttu-id="95256-113">さらに、ライブラリによっては呼び出し元からは見えない呼び出し、および特別なアクセス許可を必要とする呼び出しを行う場合があります。</span><span class="sxs-lookup"><span data-stu-id="95256-113">Additionally, some libraries might make calls that are unseen to callers and require special permissions.</span></span>  
  
 <span data-ttu-id="95256-114">また、コードが呼び出し元から完全に非表示にされる方法でリソースにアクセスする状況において、アサーションを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="95256-114">You can also use assertions in situations in which your code accesses a resource in a way that is completely hidden from callers.</span></span> <span data-ttu-id="95256-115">たとえば、ライブラリがデータベースから情報を取得しますが、プロセス内でコンピューターのレジストリからも情報を読み取ると仮定してください。</span><span class="sxs-lookup"><span data-stu-id="95256-115">For example, suppose your library acquires information from a database, but in the process also reads information from the computer registry.</span></span> <span data-ttu-id="95256-116">ライブラリを使用している開発者は、ソースにアクセスできないため、コードを使用するためにコードが**RegistryPermission**を必要としていることを知る方法がありません。</span><span class="sxs-lookup"><span data-stu-id="95256-116">Because developers using your library do not have access to your source, they have no way of knowing that their code requires **RegistryPermission** in order to use your code.</span></span> <span data-ttu-id="95256-117">この場合、コードの呼び出し元がレジストリへのアクセス許可を持つことを求めるのは妥当でないか不必要と判断した場合は、レジストリを読み取るアクセス許可をアサートすることができます。</span><span class="sxs-lookup"><span data-stu-id="95256-117">In this case, if you decide that it is not reasonable or necessary to require that callers of your code have permission to access the registry, you can assert permission for reading the registry.</span></span> <span data-ttu-id="95256-118">このような状況では、 **RegistryPermission**のない呼び出し元がライブラリを使用できるように、ライブラリがアクセス許可をアサートするのが適切です。</span><span class="sxs-lookup"><span data-stu-id="95256-118">In this situation, it is appropriate for the library to assert the permission so that callers without **RegistryPermission** can use the library.</span></span>  
  
 <span data-ttu-id="95256-119">アサーションがスタック ウォークに影響を与えるのは、アサートされたアクセス許可および下流の呼び出し元によって要求されるアクセス許可が同じ型である場合、かつ要求されたアクセス許可がアサートされているアクセス許可のサブセットである場合のみです。</span><span class="sxs-lookup"><span data-stu-id="95256-119">The assertion affects the stack walk only if the asserted permission and a permission demanded by a downstream caller are of the same type and if the demanded permission is a subset of the asserted permission.</span></span> <span data-ttu-id="95256-120">たとえば、C:\ をアサートして C ドライブ上のすべての**ファイルを読み取る**場合、 **fileiopermission**が C:\Temp 内のファイルを読み取るために下流の要求が行われると、アサーションはスタックウォークに影響を与える可能性があります。ただし、 **FileIOPermission**から C ドライブに書き込む必要がある場合、アサーションは無効になります。</span><span class="sxs-lookup"><span data-stu-id="95256-120">For example, if you assert **FileIOPermission** to read all files on the C drive, and a downstream demand is made for **FileIOPermission** to read files in C:\Temp, the assertion could affect the stack walk; however, if the demand was for **FileIOPermission** to write to the C drive, the assertion would have no effect.</span></span>  
  
 <span data-ttu-id="95256-121">アサーションを実行する場合、コードにアサートしているアクセス許可と、アサーションを実行する権利を表す <xref:System.Security.Permissions.SecurityPermission> の両方が付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="95256-121">To perform assertions, your code must be granted both the permission you are asserting and the <xref:System.Security.Permissions.SecurityPermission> that represents the right to make assertions.</span></span> <span data-ttu-id="95256-122">コードに付与されていないアクセス許可をアサートすることができますが、アサーションがセキュリティ チェックを成功させようとする前にセキュリティ チェックが失敗するため、アサーションが無意味になってしまいます。</span><span class="sxs-lookup"><span data-stu-id="95256-122">Although you could assert a permission that your code has not been granted, the assertion would be pointless because the security check would fail before the assertion could cause it to succeed.</span></span>  
  
 <span data-ttu-id="95256-123">次の図は、 **Assert**を使用した場合の動作を示しています。</span><span class="sxs-lookup"><span data-stu-id="95256-123">The following illustration shows what happens when you use **Assert**.</span></span> <span data-ttu-id="95256-124">次のステートメントについて、アセンブリ A、B、C、E、および F が true であり、P1 と P1A という 2 つのアクセス許可があると仮定してください。</span><span class="sxs-lookup"><span data-stu-id="95256-124">Assume that the following statements are true about assemblies A, B, C, E, and F, and two permissions, P1 and P1A:</span></span>  
  
- <span data-ttu-id="95256-125">P1A は C ドライブ上の .txt ファイルを読み取る権限を表します。</span><span class="sxs-lookup"><span data-stu-id="95256-125">P1A represents the right to read .txt files on the C drive.</span></span>  
  
- <span data-ttu-id="95256-126">P1 は C ドライブ上のすべてのファイルを読み取る権限を表します。</span><span class="sxs-lookup"><span data-stu-id="95256-126">P1 represents the right to read all files on the C drive.</span></span>  
  
- <span data-ttu-id="95256-127">P1A と P1 はどちらも**FileIOPermission**型であり、P1A は p1 のサブセットです。</span><span class="sxs-lookup"><span data-stu-id="95256-127">P1A and P1 are both **FileIOPermission** types, and P1A is a subset of P1.</span></span>  
  
- <span data-ttu-id="95256-128">アセンブリ E と F には P1A のアクセス許可が付与されています。</span><span class="sxs-lookup"><span data-stu-id="95256-128">Assemblies E and F have been granted P1A permission.</span></span>  
  
- <span data-ttu-id="95256-129">アセンブリ C には P1 のアクセス許可が付与されています。</span><span class="sxs-lookup"><span data-stu-id="95256-129">Assembly C has been granted P1 permission.</span></span>  
  
- <span data-ttu-id="95256-130">アセンブリ A と B には P1 と P1A のアクセス許可のいずれも付与されていません。</span><span class="sxs-lookup"><span data-stu-id="95256-130">Assemblies A and B have been granted neither P1 nor P1A permissions.</span></span>  
  
- <span data-ttu-id="95256-131">メソッド A はアセンブリ A 内にあり、メソッド B はアセンブリ B 内にあり、以下同様です。</span><span class="sxs-lookup"><span data-stu-id="95256-131">Method A is contained in assembly A, method B is contained in assembly B, and so on.</span></span>  
  
 ![Assert メソッドアセンブリを示す図。](./media/using-the-assert-method/assert-method-assemblies.gif)
  
 <span data-ttu-id="95256-133">このシナリオでは、メソッド A が B を呼び出し、B は c を呼び出し、C は E を呼び出し、E は F を呼び出します。メソッド C は、c ドライブ (アクセス許可 P1) 上のファイルを読み取るためのアクセス許可をアサートし、メソッド E は C ドライブ (アクセス許可 P1A) で .txt ファイルを読み取るアクセス許可を要求します。</span><span class="sxs-lookup"><span data-stu-id="95256-133">In this scenario, method A calls B, B calls C, C calls E, and E calls F. Method C asserts permission to read files on the C drive (permission P1), and method E demands permission to read .txt files on the C drive (permission P1A).</span></span> <span data-ttu-id="95256-134">実行時に F の要求が発生した場合、F で始まるすべての呼び出し元のアクセス許可を確認するためにスタックウォークが実行されます。 P1A のアクセス許可が付与されているため、スタックウォークは C のアクセス許可を調べ、C のアサーションを検出します。</span><span class="sxs-lookup"><span data-stu-id="95256-134">When the demand in F is encountered at run time, a stack walk is performed to check the permissions of all callers of F, starting with E. E has been granted P1A permission, so the stack walk proceeds to examine the permissions of C, where C's assertion is discovered.</span></span> <span data-ttu-id="95256-135">要求されたアクセス許可 (P1A) は、アサートされたアクセス許可 (P1) のサブセットであるため、スタック ウォークが停止し、セキュリティ チェックは自動的に成功します。</span><span class="sxs-lookup"><span data-stu-id="95256-135">Because the demanded permission (P1A) is a subset of the asserted permission (P1), the stack walk stops and the security check automatically succeeds.</span></span> <span data-ttu-id="95256-136">アセンブリ A と B に P1A のアクセス許可が付与されていないことは関係ありません。</span><span class="sxs-lookup"><span data-stu-id="95256-136">It does not matter that assemblies A and B have not been granted permission P1A.</span></span> <span data-ttu-id="95256-137">P1 をアサートすることで、メソッド C は、呼び出し元がそのリソースへのアクセス許可を付与されていない場合でも呼び出し元が、P1 で保護されているリソースにアクセスできることを保証します。</span><span class="sxs-lookup"><span data-stu-id="95256-137">By asserting P1, method C ensures that its callers can access the resource protected by P1, even if the callers have not been granted permission to access that resource.</span></span>  
  
 <span data-ttu-id="95256-138">クラス ライブラリをデザインし、クラスが保護されたリソースにアクセスする場合は、ほとんどの場合、呼び出し元のクラスが適切なアクセス許可を持つことを求めるセキュリティの要求を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="95256-138">If you design a class library and a class accesses a protected resource, you should, in most cases, make a security demand requiring that the callers of the class have the appropriate permission.</span></span> <span data-ttu-id="95256-139">その後、ほとんどの呼び出し元にアクセス許可がないことがわかっている操作を実行し、呼び出し元がコードを呼び出すことを許可する必要がある場合は、コードが実行している操作を表すアクセス許可オブジェクトで**assert**メソッドを呼び出すことにより、アクセス許可をアサートできます。</span><span class="sxs-lookup"><span data-stu-id="95256-139">If the class then performs an operation for which you know most of its callers will not have permission, and if you are willing to take the responsibility for letting these callers call your code, you can assert the permission by calling the **Assert** method on a permission object that represents the operation the code is performing.</span></span> <span data-ttu-id="95256-140">この方法で**Assert**を使用すると、通常は、コードを呼び出すことができなかった呼び出し元を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="95256-140">Using **Assert** in this way lets callers that normally could not do so call your code.</span></span> <span data-ttu-id="95256-141">そのため、アクセス許可をアサートする場合、自分のコンポーネントが誤使用されるのを防ぐために、必ず事前に適切なセキュリティ チェックを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95256-141">Therefore, if you assert a permission, you should be sure to perform appropriate security checks beforehand to prevent your component from being misused.</span></span>  
  
 <span data-ttu-id="95256-142">たとえば、信頼性の高いライブラリのクラスにファイルを削除するメソッドがあると仮定します。</span><span class="sxs-lookup"><span data-stu-id="95256-142">For example, suppose your highly trusted library class has a method that deletes files.</span></span> <span data-ttu-id="95256-143">メソッドは、アンマネージ Win32 関数を呼び出してファイルにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="95256-143">It accesses the file by calling an unmanaged Win32 function.</span></span> <span data-ttu-id="95256-144">呼び出し元は、削除するファイルの名前を渡して、コードの**Delete**メソッドを呼び出し、C:\Test.txt します。</span><span class="sxs-lookup"><span data-stu-id="95256-144">A caller invokes your code's **Delete** method, passing in the name of the file to be deleted, C:\Test.txt.</span></span> <span data-ttu-id="95256-145">**Delete**メソッド内で、コードは <xref:System.Security.Permissions.FileIOPermission> C:\Test.txt への書き込みアクセスを表すオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="95256-145">Within the **Delete** method, your code creates a <xref:System.Security.Permissions.FileIOPermission> object representing write access to C:\Test.txt.</span></span> <span data-ttu-id="95256-146">(ファイルを削除するには書き込みアクセスが必要です)。コードは、 **FileIOPermission**オブジェクトの**Demand**メソッドを呼び出すことによって、強制セキュリティチェックを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="95256-146">(Write access is required to delete a file.) Your code then invokes an imperative security check by calling the **FileIOPermission** object's **Demand** method.</span></span> <span data-ttu-id="95256-147">コール スタックのいずれかの呼び出し元にこのアクセス許可がない場合は、<xref:System.Security.SecurityException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="95256-147">If one of the callers in the call stack does not have this permission, a <xref:System.Security.SecurityException> is thrown.</span></span> <span data-ttu-id="95256-148">例外がスローされない場合、すべての呼び出し元に C:\Test.txt へのアクセス権があることがわかります。</span><span class="sxs-lookup"><span data-stu-id="95256-148">If no exception is thrown, you know that all callers have the right to access C:\Test.txt.</span></span> <span data-ttu-id="95256-149">ほとんどの呼び出し元にはアンマネージコードへのアクセス許可がないと考えられるので、コードは <xref:System.Security.Permissions.SecurityPermission> アンマネージコードを呼び出す権限を表すオブジェクトを作成し、オブジェクトの**Assert**メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="95256-149">Because you believe that most of your callers will not have permission to access unmanaged code, your code then creates a <xref:System.Security.Permissions.SecurityPermission> object that represents the right to call unmanaged code and calls the object's **Assert** method.</span></span> <span data-ttu-id="95256-150">最後に、コードは C:\Text.txt を削除するアンマネージ Win32 関数を呼び出し、呼び出し元にコントロールを返します。</span><span class="sxs-lookup"><span data-stu-id="95256-150">Finally, it calls the unmanaged Win32 function to delete C:\Text.txt and returns control to the caller.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="95256-151">そこで、アサートするためのアクセス許可によって保護されているリソースにアクセスするために自分のコードが他のコードによって使用される状況では、自分のコードでアサーションが使用されていないことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95256-151">You must be sure that your code does not use assertions in situations where your code can be used by other code to access a resource that is protected by the permission you are asserting.</span></span> <span data-ttu-id="95256-152">たとえば、呼び出し元によってパラメーターとして指定された名前を持つファイルに書き込むコードでは、ファイルへの書き込みのための**FileIOPermission**をアサートしません。これは、コードがサードパーティによって悪用されるためです。</span><span class="sxs-lookup"><span data-stu-id="95256-152">For example, in code that writes to a file whose name is specified by the caller as a parameter, you would not assert the **FileIOPermission** for writing to files because your code would be open to misuse by a third party.</span></span>  
  
 <span data-ttu-id="95256-153">命令型セキュリティ構文を使用する場合、同じメソッド内の複数のアクセス許可で**Assert**メソッドを呼び出すと、セキュリティ例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="95256-153">When you use the imperative security syntax, calling the **Assert** method on multiple permissions in the same method causes a security exception to be thrown.</span></span> <span data-ttu-id="95256-154">代わりに、 **PermissionSet**オブジェクトを作成し、呼び出す個々のアクセス許可を渡してから、 **PermissionSet**オブジェクトの**Assert**メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="95256-154">Instead, you should create a **PermissionSet** object, pass it the individual permissions you want to invoke, and then call the **Assert** method on the **PermissionSet** object.</span></span> <span data-ttu-id="95256-155">宣言セキュリティ構文を使用すると、 **Assert**メソッドを複数回呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="95256-155">You can call the **Assert** method more than once when you use the declarative security syntax.</span></span>  
  
 <span data-ttu-id="95256-156">次の例は、 **Assert**メソッドを使用してセキュリティチェックをオーバーライドする宣言型の構文を示しています。</span><span class="sxs-lookup"><span data-stu-id="95256-156">The following example shows declarative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="95256-157">**FileIOPermissionAttribute**構文は、 <xref:System.Security.Permissions.SecurityAction> 列挙と、アクセス許可が付与されるファイルまたはディレクトリの場所の2つの値を取ります。</span><span class="sxs-lookup"><span data-stu-id="95256-157">Notice that the **FileIOPermissionAttribute** syntax takes two values: a <xref:System.Security.Permissions.SecurityAction> enumeration and the location of the file or directory to which permission is to be granted.</span></span> <span data-ttu-id="95256-158">呼び出し元に**Assert** `C:\Log.txt` ファイルへのアクセス許可があるかどうかがチェックされない場合でも、Assert を呼び出すと、へのアクセスの要求が成功します。</span><span class="sxs-lookup"><span data-stu-id="95256-158">The call to **Assert** causes demands for access to `C:\Log.txt` to succeed, even though callers are not checked for permission to access the file.</span></span>  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
  
      End Sub  
  
     <FileIOPermission(SecurityAction.Assert, All := "C:\Log.txt")> Public Sub
      MakeLog()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now) '  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {
      }
      [FileIOPermission(SecurityAction.Assert, All = @"C:\Log.txt")]  
      public void MakeLog()  
      {
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}
```  
  
 <span data-ttu-id="95256-159">次のコードフラグメントは、 **Assert**メソッドを使用してセキュリティチェックをオーバーライドするための命令型の構文を示しています。</span><span class="sxs-lookup"><span data-stu-id="95256-159">The following code fragments show imperative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="95256-160">この例では、 **FileIOPermission**オブジェクトのインスタンスが宣言されています。</span><span class="sxs-lookup"><span data-stu-id="95256-160">In this example, an instance of the **FileIOPermission** object is declared.</span></span> <span data-ttu-id="95256-161">コンストラクターには、許可されているアクセスの種類を定義するための FileIOPermissionAccess が渡され、その後にファイルの場所を説明する文字列が続きます **。**</span><span class="sxs-lookup"><span data-stu-id="95256-161">Its constructor is passed **FileIOPermissionAccess.AllAccess** to define the type of access allowed, followed by a string describing the file's location.</span></span> <span data-ttu-id="95256-162">**FileIOPermission**オブジェクトが定義されたら、その**Assert**メソッドを呼び出して、セキュリティチェックをオーバーライドするだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="95256-162">Once the **FileIOPermission** object is defined, you only need to call its **Assert** method to override the security check.</span></span>  
  
```vb  
Option Explicit  
Option Strict  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
      End Sub 'New  
  
      Public Sub MakeLog()  
         Dim FilePermission As New FileIOPermission(FileIOPermissionAccess.AllAccess, "C:\Log.txt")  
         FilePermission.Assert()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now)  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {
      }
      public void MakeLog()  
      {  
         FileIOPermission FilePermission = new FileIOPermission(FileIOPermissionAccess.AllAccess,@"C:\Log.txt");
         FilePermission.Assert();  
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="95256-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="95256-163">See also</span></span>

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.SecurityPermission>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.Permissions.SecurityAction>
- [<span data-ttu-id="95256-164">属性</span><span class="sxs-lookup"><span data-stu-id="95256-164">Attributes</span></span>](../../standard/attributes/index.md)
- [<span data-ttu-id="95256-165">コード アクセス セキュリティ</span><span class="sxs-lookup"><span data-stu-id="95256-165">Code Access Security</span></span>](code-access-security.md)
