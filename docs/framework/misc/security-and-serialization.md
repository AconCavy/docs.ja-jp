---
title: セキュリティとシリアル化
description: 「セキュリティとシリアル化」を参照してください。 オブジェクトインスタンスデータを表示または変更するには、SecurityPermission を SerializationFormatter フラグを指定して使用します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, serialization
- serialization, security
- secure coding, serialization
- security [.NET Framework], serialization
ms.assetid: b921bc94-bd3a-4c91-9ede-2c8d4f78ea9a
ms.openlocfilehash: 393e334e8165f55812681848070929bdfb03a2a5
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855687"
---
# <a name="security-and-serialization"></a><span data-ttu-id="66d94-104">セキュリティとシリアル化</span><span class="sxs-lookup"><span data-stu-id="66d94-104">Security and serialization</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="66d94-105">シリアル化によって、他の方法ではアクセスできないオブジェクト インスタンス データを他のコードから参照または変更できるようになるため、シリアル化を実行するコードには、特殊なアクセス許可として、 <xref:System.Security.Permissions.SecurityPermission> フラグが指定された <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> が必要です。</span><span class="sxs-lookup"><span data-stu-id="66d94-105">Because serialization can allow other code to see or modify object instance data that would otherwise be inaccessible, a special permission is required of code performing serialization: <xref:System.Security.Permissions.SecurityPermission> with the <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="66d94-106">既定のポリシーでは、インターネットからダウンロードしたコードまたはイントラネット コードにはこのアクセス許可は与えられず、ローカル コンピューター上のコードにだけ付与されます。</span><span class="sxs-lookup"><span data-stu-id="66d94-106">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span>  
  
 <span data-ttu-id="66d94-107">通常、オブジェクト インスタンスのすべてのフィールドはシリアル化されます。つまり、データは、インスタンスのシリアル化されたデータで表されます。</span><span class="sxs-lookup"><span data-stu-id="66d94-107">Normally, all fields of an object instance are serialized, meaning that data is represented in the serialized data for the instance.</span></span> <span data-ttu-id="66d94-108">形式を解釈できるコードでは、メンバーのアクセシビリティとは関係なく、データ値を判断できます。</span><span class="sxs-lookup"><span data-stu-id="66d94-108">It is possible for code that can interpret the format to determine what the data values are, independent of the accessibility of the member.</span></span> <span data-ttu-id="66d94-109">同様に、逆シリアル化でもアクセシビリティ規則に関係なく、シリアル化された表現からデータを抽出し、オブジェクトの状態を直接設定します。</span><span class="sxs-lookup"><span data-stu-id="66d94-109">Similarly, deserialization extracts data from the serialized representation and sets object state directly, again irrespective of accessibility rules.</span></span>  
  
 <span data-ttu-id="66d94-110">機密データを含む可能性のあるオブジェクトは、可能であれば、シリアル化できないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="66d94-110">Any object that could contain security-sensitive data should be made nonserializable, if possible.</span></span> <span data-ttu-id="66d94-111">そのようなオブジェクトをシリアル化しなければならない場合、機密データを保持する特定のフィールドは、シリアル化できないように維持してください。</span><span class="sxs-lookup"><span data-stu-id="66d94-111">If it must be serializable, try to make specific fields that hold sensitive data nonserializable.</span></span> <span data-ttu-id="66d94-112">これらのフィールドをシリアル化にできない場合、機密データは、シリアル化のアクセス許可を持つすべてのコードに公開されます。</span><span class="sxs-lookup"><span data-stu-id="66d94-112">If those fields cannot be made nonserializable, the sensitive data will be exposed to any code that has permission to serialize.</span></span> <span data-ttu-id="66d94-113">悪意のあるコードがこのアクセス許可を取得できないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="66d94-113">Make sure that no malicious code can get this permission.</span></span>  
  
 <span data-ttu-id="66d94-114"><xref:System.Runtime.Serialization.ISerializable> インターフェイスは、シリアル化インフラストラクチャでのみ使用するためのものです。</span><span class="sxs-lookup"><span data-stu-id="66d94-114">The <xref:System.Runtime.Serialization.ISerializable> interface is intended for use only by the serialization infrastructure.</span></span> <span data-ttu-id="66d94-115">ただし、保護されていない場合、機密情報をリリースする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="66d94-115">However, if unprotected, it can potentially release sensitive information.</span></span> <span data-ttu-id="66d94-116">**ISerializable**を実装してカスタムのシリアル化を提供する場合は、必ず次の予防措置を取ってください。</span><span class="sxs-lookup"><span data-stu-id="66d94-116">If you provide custom serialization by implementing **ISerializable**, make sure you take the following precautions:</span></span>  
  
- <span data-ttu-id="66d94-117"><xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> SerializationFormatter **アクセス許可を指定した** SecurityPermission **を要求するか、メソッドの出力で機密情報がリリースされないことを確実にして、** メソッドを明示的に保護します。</span><span class="sxs-lookup"><span data-stu-id="66d94-117">The <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method should be explicitly secured either by demanding the **SecurityPermission** with **SerializationFormatter** permission specified or by making sure that no sensitive information is released with the method output.</span></span> <span data-ttu-id="66d94-118">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="66d94-118">For example:</span></span>  
  
    ```vb  
    Public Overrides<SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)>  _  
    Sub GetObjectData(info As SerializationInfo, context As StreamingContext)  
    End Sub  
    ```  
  
    ```csharp  
    [SecurityPermissionAttribute(SecurityAction.Demand,SerializationFormatter
    =true)]  
    public override void GetObjectData(SerializationInfo info,
    StreamingContext context)  
    {  
    }  
    ```  
  
- <span data-ttu-id="66d94-119">シリアル化に使用する特殊なコンストラクターでも徹底的な入力検証を行い、悪質なコードによる悪用を防ぐために、コンストラクターを保護するか、またはプライベートにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="66d94-119">The special constructor used for serialization should also perform thorough input validation and should be either protected or private to help protect against misuse by malicious code.</span></span> <span data-ttu-id="66d94-120">また、クラスを明示的に作成したり、ある種のファクトリで間接的に作成したりするなど、他の方法でこのようなクラスのインスタンスを取得する場合にも、同じセキュリティ チェックとアクセス許可を適用してください。</span><span class="sxs-lookup"><span data-stu-id="66d94-120">It should enforce the same security checks and permissions required to obtain an instance of such a class by any other means, such as explicitly creating the class or indirectly creating it through some kind of factory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66d94-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="66d94-121">See also</span></span>

- [<span data-ttu-id="66d94-122">安全なコーディングのガイドライン</span><span class="sxs-lookup"><span data-stu-id="66d94-122">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
