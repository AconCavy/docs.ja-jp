---
title: Assert メソッドの使用
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
ms.openlocfilehash: 92e49af78d42f360d5798a72d4e7b981295947e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181104"
---
# <a name="using-the-assert-method"></a><span data-ttu-id="b2cbd-102">Assert メソッドの使用</span><span class="sxs-lookup"><span data-stu-id="b2cbd-102">Using the Assert Method</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="b2cbd-103"><xref:System.Security.CodeAccessPermission.Assert%2A> は、コードのアクセス許可のクラスおよび <xref:System.Security.PermissionSet>クラスで呼び出すことができるメソッドです。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-103"><xref:System.Security.CodeAccessPermission.Assert%2A> is a method that can be called on code access permission classes and on the <xref:System.Security.PermissionSet> class.</span></span> <span data-ttu-id="b2cbd-104">**Assert**を使用すると、コード (および下位の呼び出し元) が、コードに対するアクセス許可を持ち、その呼び出し元に実行するアクセス許可がない可能性があるアクションを実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-104">You can use **Assert** to enable your code (and downstream callers) to perform actions that your code has permission to do but its callers might not have permission to do.</span></span> <span data-ttu-id="b2cbd-105">セキュリティ アサーションは、セキュリティ チェック時にランタイムが実行する正常なプロセスを変更します。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-105">A security assertion changes the normal process that the runtime performs during a security check.</span></span> <span data-ttu-id="b2cbd-106">アクセス許可をアサートすると、アサートされたアクセス許可のためにコードの呼び出し元をチェックしないようセキュリティ システムに指示します。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-106">When you assert a permission, it tells the security system not to check the callers of your code for the asserted permission.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="b2cbd-107">アサーションはセキュリティ ホールを開き、セキュリティの制限事項を適用するランタイムのメカニズムを弱体化させる可能性があるため、慎重に使用してください。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-107">Use assertions carefully because they can open security holes and undermine the runtime's mechanism for enforcing security restrictions.</span></span>  
  
 <span data-ttu-id="b2cbd-108">アサーションは、ライブラリがアンマネージ コードを呼び出す状況、またはライブラリの使用目的と明らかに関係のないアクセス許可を必要とする呼び出しを行う状況に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-108">Assertions are useful in situations in which a library calls into unmanaged code or makes a call that requires a permission that is not obviously related to the library's intended use.</span></span> <span data-ttu-id="b2cbd-109">たとえば、アンマネージ コードを呼び出すすべてのマネージ コードには **、UnmanagedCode**フラグが指定された**SecurityPermission**が必要です。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-109">For example, all managed code that calls into unmanaged code must have **SecurityPermission** with the **UnmanagedCode** flag specified.</span></span> <span data-ttu-id="b2cbd-110">ローカルのイントラネットからダウンロードするコードなど、ローカル コンピューターから発生していないコードには、既定でこのアクセス許可は付与されません。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-110">Code that does not originate from the local computer, such as code that is downloaded from the local intranet, will not be granted this permission by default.</span></span> <span data-ttu-id="b2cbd-111">そのため、ローカルのイントラネットからダウンロードするコードがアンマネージ コードを使用するライブラリを呼び出せるようにするには、ライブラリによってアサートされたアクセス許可がコードに指定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-111">Therefore, in order for code that is downloaded from the local intranet to be able to call a library that uses unmanaged code, it must have the permission asserted by the library.</span></span> <span data-ttu-id="b2cbd-112">さらに、ライブラリによっては呼び出し元からは見えない呼び出し、および特別なアクセス許可を必要とする呼び出しを行う場合があります。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-112">Additionally, some libraries might make calls that are unseen to callers and require special permissions.</span></span>  
  
 <span data-ttu-id="b2cbd-113">また、コードが呼び出し元から完全に非表示にされる方法でリソースにアクセスする状況において、アサーションを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-113">You can also use assertions in situations in which your code accesses a resource in a way that is completely hidden from callers.</span></span> <span data-ttu-id="b2cbd-114">たとえば、ライブラリがデータベースから情報を取得しますが、プロセス内でコンピューターのレジストリからも情報を読み取ると仮定してください。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-114">For example, suppose your library acquires information from a database, but in the process also reads information from the computer registry.</span></span> <span data-ttu-id="b2cbd-115">ライブラリを使用している開発者はソースにアクセスできないため、コードを使用するためにコードに**RegistryPermission**が必要であることを知る方法はありません。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-115">Because developers using your library do not have access to your source, they have no way of knowing that their code requires **RegistryPermission** in order to use your code.</span></span> <span data-ttu-id="b2cbd-116">この場合、コードの呼び出し元がレジストリへのアクセス許可を持つことを求めるのは妥当でないか不必要と判断した場合は、レジストリを読み取るアクセス許可をアサートすることができます。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-116">In this case, if you decide that it is not reasonable or necessary to require that callers of your code have permission to access the registry, you can assert permission for reading the registry.</span></span> <span data-ttu-id="b2cbd-117">このような場合は、**ライブラリ**がアクセス許可をアサートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-117">In this situation, it is appropriate for the library to assert the permission so that callers without **RegistryPermission** can use the library.</span></span>  
  
 <span data-ttu-id="b2cbd-118">アサーションがスタック ウォークに影響を与えるのは、アサートされたアクセス許可および下流の呼び出し元によって要求されるアクセス許可が同じ型である場合、かつ要求されたアクセス許可がアサートされているアクセス許可のサブセットである場合のみです。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-118">The assertion affects the stack walk only if the asserted permission and a permission demanded by a downstream caller are of the same type and if the demanded permission is a subset of the asserted permission.</span></span> <span data-ttu-id="b2cbd-119">たとえば、C ドライブ上のすべてのファイルを読み取るために**FileIOPermission**をアサートし、C:\Temp で**FileIOPermission**がファイルを読み取るように下流の要求が行われると、アサーションがスタック ウォークに影響を与える可能性があります。ただし **、FileIOPermission**が C ドライブに書き込む必要がある場合、アサーションは効果がありません。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-119">For example, if you assert **FileIOPermission** to read all files on the C drive, and a downstream demand is made for **FileIOPermission** to read files in C:\Temp, the assertion could affect the stack walk; however, if the demand was for **FileIOPermission** to write to the C drive, the assertion would have no effect.</span></span>  
  
 <span data-ttu-id="b2cbd-120">アサーションを実行する場合、コードにアサートしているアクセス許可と、アサーションを実行する権利を表す <xref:System.Security.Permissions.SecurityPermission> の両方が付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-120">To perform assertions, your code must be granted both the permission you are asserting and the <xref:System.Security.Permissions.SecurityPermission> that represents the right to make assertions.</span></span> <span data-ttu-id="b2cbd-121">コードに付与されていないアクセス許可をアサートすることができますが、アサーションがセキュリティ チェックを成功させようとする前にセキュリティ チェックが失敗するため、アサーションが無意味になってしまいます。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-121">Although you could assert a permission that your code has not been granted, the assertion would be pointless because the security check would fail before the assertion could cause it to succeed.</span></span>  
  
 <span data-ttu-id="b2cbd-122">次の図は、 **Assert**を使用した場合の動作を示しています。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-122">The following illustration shows what happens when you use **Assert**.</span></span> <span data-ttu-id="b2cbd-123">次のステートメントについて、アセンブリ A、B、C、E、および F が true であり、P1 と P1A という 2 つのアクセス許可があると仮定してください。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-123">Assume that the following statements are true about assemblies A, B, C, E, and F, and two permissions, P1 and P1A:</span></span>  
  
- <span data-ttu-id="b2cbd-124">P1A は C ドライブ上の .txt ファイルを読み取る権限を表します。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-124">P1A represents the right to read .txt files on the C drive.</span></span>  
  
- <span data-ttu-id="b2cbd-125">P1 は C ドライブ上のすべてのファイルを読み取る権限を表します。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-125">P1 represents the right to read all files on the C drive.</span></span>  
  
- <span data-ttu-id="b2cbd-126">P1A と P1 は両方とも**FileIOPermission**型であり、P1A は P1 のサブセットです。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-126">P1A and P1 are both **FileIOPermission** types, and P1A is a subset of P1.</span></span>  
  
- <span data-ttu-id="b2cbd-127">アセンブリ E と F には P1A のアクセス許可が付与されています。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-127">Assemblies E and F have been granted P1A permission.</span></span>  
  
- <span data-ttu-id="b2cbd-128">アセンブリ C には P1 のアクセス許可が付与されています。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-128">Assembly C has been granted P1 permission.</span></span>  
  
- <span data-ttu-id="b2cbd-129">アセンブリ A と B には P1 と P1A のアクセス許可のいずれも付与されていません。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-129">Assemblies A and B have been granted neither P1 nor P1A permissions.</span></span>  
  
- <span data-ttu-id="b2cbd-130">メソッド A はアセンブリ A 内にあり、メソッド B はアセンブリ B 内にあり、以下同様です。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-130">Method A is contained in assembly A, method B is contained in assembly B, and so on.</span></span>  
  
 ![Assert メソッドアセンブリを示す図。](./media/using-the-assert-method/assert-method-assemblies.gif)
  
 <span data-ttu-id="b2cbd-132">このシナリオでは、メソッド A が B を呼び出し、B が呼び出す C、C 呼び出し E、および E 呼び出し F. C のファイルを読み取るアクセス許可をアサートする (アクセス許可 P1) C ドライブ上のファイルを読み取るアクセス許可をメソッド E (アクセス許可 P1A) します。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-132">In this scenario, method A calls B, B calls C, C calls E, and E calls F. Method C asserts permission to read files on the C drive (permission P1), and method E demands permission to read .txt files on the C drive (permission P1A).</span></span> <span data-ttu-id="b2cbd-133">実行時に F の要求が発生すると、F のすべての呼び出し元のアクセス許可をチェックするスタック ウォークが実行され、E. E から始めて P1A アクセス許可が付与されているので、スタック ウォークは C のアサーションが検出された C のアクセス許可を調べます。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-133">When the demand in F is encountered at run time, a stack walk is performed to check the permissions of all callers of F, starting with E. E has been granted P1A permission, so the stack walk proceeds to examine the permissions of C, where C's assertion is discovered.</span></span> <span data-ttu-id="b2cbd-134">要求されたアクセス許可 (P1A) は、アサートされたアクセス許可 (P1) のサブセットであるため、スタック ウォークが停止し、セキュリティ チェックは自動的に成功します。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-134">Because the demanded permission (P1A) is a subset of the asserted permission (P1), the stack walk stops and the security check automatically succeeds.</span></span> <span data-ttu-id="b2cbd-135">アセンブリ A と B に P1A のアクセス許可が付与されていないことは関係ありません。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-135">It does not matter that assemblies A and B have not been granted permission P1A.</span></span> <span data-ttu-id="b2cbd-136">P1 をアサートすることで、メソッド C は、呼び出し元がそのリソースへのアクセス許可を付与されていない場合でも呼び出し元が、P1 で保護されているリソースにアクセスできることを保証します。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-136">By asserting P1, method C ensures that its callers can access the resource protected by P1, even if the callers have not been granted permission to access that resource.</span></span>  
  
 <span data-ttu-id="b2cbd-137">クラス ライブラリをデザインし、クラスが保護されたリソースにアクセスする場合は、ほとんどの場合、呼び出し元のクラスが適切なアクセス許可を持つことを求めるセキュリティの要求を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-137">If you design a class library and a class accesses a protected resource, you should, in most cases, make a security demand requiring that the callers of the class have the appropriate permission.</span></span> <span data-ttu-id="b2cbd-138">その後、ほとんどの呼び出し元にアクセス許可がないことがわかっている操作をクラスが実行し、これらの呼び出し元にコードを呼び出す責任を負う場合は、コードが実行している操作を表すアクセス許可オブジェクトに対して**Assert**メソッドを呼び出して、アクセス許可をアサートできます。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-138">If the class then performs an operation for which you know most of its callers will not have permission, and if you are willing to take the responsibility for letting these callers call your code, you can assert the permission by calling the **Assert** method on a permission object that represents the operation the code is performing.</span></span> <span data-ttu-id="b2cbd-139">この方法で**Assert**を使用すると、通常は呼び出し元がコードを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-139">Using **Assert** in this way lets callers that normally could not do so call your code.</span></span> <span data-ttu-id="b2cbd-140">そのため、アクセス許可をアサートする場合、自分のコンポーネントが誤使用されるのを防ぐために、必ず事前に適切なセキュリティ チェックを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-140">Therefore, if you assert a permission, you should be sure to perform appropriate security checks beforehand to prevent your component from being misused.</span></span>  
  
 <span data-ttu-id="b2cbd-141">たとえば、信頼性の高いライブラリのクラスにファイルを削除するメソッドがあると仮定します。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-141">For example, suppose your highly trusted library class has a method that deletes files.</span></span> <span data-ttu-id="b2cbd-142">メソッドは、アンマネージ Win32 関数を呼び出してファイルにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-142">It accesses the file by calling an unmanaged Win32 function.</span></span> <span data-ttu-id="b2cbd-143">呼び出し元がコードの**Delete**メソッドを呼び出し、削除するファイルの名前 C:\Test.txt を渡します。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-143">A caller invokes your code's **Delete** method, passing in the name of the file to be deleted, C:\Test.txt.</span></span> <span data-ttu-id="b2cbd-144">**Delete**メソッド内で、コードは<xref:System.Security.Permissions.FileIOPermission>C:\Test.txt への書き込みアクセスを表すオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-144">Within the **Delete** method, your code creates a <xref:System.Security.Permissions.FileIOPermission> object representing write access to C:\Test.txt.</span></span> <span data-ttu-id="b2cbd-145">(ファイルを削除するには、書き込みアクセス権が必要です。次に、**コードは、FileIOPermission**オブジェクトの**Demand**メソッドを呼び出すことによって、強制セキュリティ チェックを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-145">(Write access is required to delete a file.) Your code then invokes an imperative security check by calling the **FileIOPermission** object's **Demand** method.</span></span> <span data-ttu-id="b2cbd-146">コール スタックのいずれかの呼び出し元にこのアクセス許可がない場合は、<xref:System.Security.SecurityException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-146">If one of the callers in the call stack does not have this permission, a <xref:System.Security.SecurityException> is thrown.</span></span> <span data-ttu-id="b2cbd-147">例外がスローされない場合、すべての呼び出し元に C:\Test.txt へのアクセス権があることがわかります。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-147">If no exception is thrown, you know that all callers have the right to access C:\Test.txt.</span></span> <span data-ttu-id="b2cbd-148">呼び出し元の多くはアンマネージ コードにアクセスするアクセス許可を持たないと考えているため<xref:System.Security.Permissions.SecurityPermission>、アンマネージ コードを呼び出す権限を表すオブジェクトを作成し、そのオブジェクトの**Assert**メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-148">Because you believe that most of your callers will not have permission to access unmanaged code, your code then creates a <xref:System.Security.Permissions.SecurityPermission> object that represents the right to call unmanaged code and calls the object's **Assert** method.</span></span> <span data-ttu-id="b2cbd-149">最後に、コードは C:\Text.txt を削除するアンマネージ Win32 関数を呼び出し、呼び出し元にコントロールを返します。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-149">Finally, it calls the unmanaged Win32 function to delete C:\Text.txt and returns control to the caller.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="b2cbd-150">そこで、アサートするためのアクセス許可によって保護されているリソースにアクセスするために自分のコードが他のコードによって使用される状況では、自分のコードでアサーションが使用されていないことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-150">You must be sure that your code does not use assertions in situations where your code can be used by other code to access a resource that is protected by the permission you are asserting.</span></span> <span data-ttu-id="b2cbd-151">たとえば、呼び出し元によってパラメータとして指定された名前を持つファイルに書き込むコードでは、コードが第三者によって悪用されそうであるため **、FileIOPermission**をアサートしてファイルに書き込む必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-151">For example, in code that writes to a file whose name is specified by the caller as a parameter, you would not assert the **FileIOPermission** for writing to files because your code would be open to misuse by a third party.</span></span>  
  
 <span data-ttu-id="b2cbd-152">強制セキュリティ構文を使用する場合、同じメソッド内の複数のアクセス許可に対して**Assert**メソッドを呼び出すと、セキュリティ例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-152">When you use the imperative security syntax, calling the **Assert** method on multiple permissions in the same method causes a security exception to be thrown.</span></span> <span data-ttu-id="b2cbd-153">代わりに **、PermissionSet**オブジェクトを作成し、呼び出す個々のアクセス許可を渡し **、PermissionSet**オブジェクトの**Assert**メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-153">Instead, you should create a **PermissionSet** object, pass it the individual permissions you want to invoke, and then call the **Assert** method on the **PermissionSet** object.</span></span> <span data-ttu-id="b2cbd-154">宣言セキュリティ構文を使用する場合は **、Assert**メソッドを複数回呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-154">You can call the **Assert** method more than once when you use the declarative security syntax.</span></span>  
  
 <span data-ttu-id="b2cbd-155">**Assert**メソッドを使用してセキュリティ チェックをオーバーライドするための宣言構文を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-155">The following example shows declarative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="b2cbd-156">**FileIOPermissionAttribute**構文には、<xref:System.Security.Permissions.SecurityAction>列挙型と、アクセス許可を与えるファイルまたはディレクトリの場所の 2 つの値が使用されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-156">Notice that the **FileIOPermissionAttribute** syntax takes two values: a <xref:System.Security.Permissions.SecurityAction> enumeration and the location of the file or directory to which permission is to be granted.</span></span> <span data-ttu-id="b2cbd-157">**Assert**への呼び出しは、`C:\Log.txt`呼び出し元がファイルへのアクセス許可をチェックされていない場合でも、アクセスの要求が成功します。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-157">The call to **Assert** causes demands for access to `C:\Log.txt` to succeed, even though callers are not checked for permission to access the file.</span></span>  
  
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
  
 <span data-ttu-id="b2cbd-158">次のコードは **、Assert**メソッドを使用してセキュリティ チェックをオーバーライドするための命令構文を示しています。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-158">The following code fragments show imperative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="b2cbd-159">この例では、**オブジェクト**のインスタンスが宣言されています。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-159">In this example, an instance of the **FileIOPermission** object is declared.</span></span> <span data-ttu-id="b2cbd-160">そのコンストラクターに渡される**FileIOPermissionAccess.AllAccess**アクセスの種類を定義し、その後にファイルの場所を説明する文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-160">Its constructor is passed **FileIOPermissionAccess.AllAccess** to define the type of access allowed, followed by a string describing the file's location.</span></span> <span data-ttu-id="b2cbd-161">**FileIOPermission**オブジェクトを定義した後は、Assert**メソッドを**呼び出してセキュリティ チェックをオーバーライドするだけです。</span><span class="sxs-lookup"><span data-stu-id="b2cbd-161">Once the **FileIOPermission** object is defined, you only need to call its **Assert** method to override the security check.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b2cbd-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2cbd-162">See also</span></span>

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.SecurityPermission>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.Permissions.SecurityAction>
- [<span data-ttu-id="b2cbd-163">属性</span><span class="sxs-lookup"><span data-stu-id="b2cbd-163">Attributes</span></span>](../../standard/attributes/index.md)
- [<span data-ttu-id="b2cbd-164">コード アクセス セキュリティ</span><span class="sxs-lookup"><span data-stu-id="b2cbd-164">Code Access Security</span></span>](code-access-security.md)
