---
title: ローカライズされた例外メッセージを使用するユーザー定義の例外を作成する方法
description: ローカライズされた例外メッセージを使用するユーザー定義の例外を作成する方法について説明します。
author: Youssef1313
dev_langs:
- csharp
- vb
ms.date: 09/13/2019
ms.openlocfilehash: fa0bbfdbfc9408302eec2edd4e4ee4503d2612c7
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243350"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a><span data-ttu-id="33a64-103">ローカライズされた例外メッセージを使用するユーザー定義の例外を作成する方法</span><span class="sxs-lookup"><span data-stu-id="33a64-103">How to create user-defined exceptions with localized exception messages</span></span>

<span data-ttu-id="33a64-104">この記事では、サテライト アセンブリを使用してローカライズされた例外メッセージ使用する、基底の <xref:System.Exception> クラスから継承されるユーザー定義の例外を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="33a64-104">In this article, you will learn how to create user-defined exceptions that are inherited from the base <xref:System.Exception> class with localized exception messages using satellite assemblies.</span></span>

## <a name="create-custom-exceptions"></a><span data-ttu-id="33a64-105">カスタムの例外を作成する</span><span class="sxs-lookup"><span data-stu-id="33a64-105">Create custom exceptions</span></span>

<span data-ttu-id="33a64-106">.NET には、使用できるさまざまな例外があります。</span><span class="sxs-lookup"><span data-stu-id="33a64-106">.NET contains many different exceptions that you can use.</span></span> <span data-ttu-id="33a64-107">ただし、いずれもニーズに合わない場合は、独自のカスタムの例外を作成できます。</span><span class="sxs-lookup"><span data-stu-id="33a64-107">However, in some cases when none of them meets your needs, you can create your own custom exceptions.</span></span>

<span data-ttu-id="33a64-108">たとえば、`StudentName` プロパティを含む `StudentNotFoundException` を作成するとします。</span><span class="sxs-lookup"><span data-stu-id="33a64-108">Let's assume you want to create a `StudentNotFoundException` that contains a `StudentName` property.</span></span>
<span data-ttu-id="33a64-109">カスタムの例外を作成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="33a64-109">To create a custom exception, follow these steps:</span></span>

1. <span data-ttu-id="33a64-110"><xref:System.Exception> から継承されるシリアル化可能なクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="33a64-110">Create a serializable class that inherits from <xref:System.Exception>.</span></span> <span data-ttu-id="33a64-111">クラス名の末尾は "Exception" にするようにします。</span><span class="sxs-lookup"><span data-stu-id="33a64-111">The class name should end in "Exception":</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception { }
    ```

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception
    End Class
    ```

1. <span data-ttu-id="33a64-112">既定のコンストラクターを追加します。</span><span class="sxs-lookup"><span data-stu-id="33a64-112">Add the default constructors:</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception
    {
        public StudentNotFoundException() { }

        public StudentNotFoundException(string message)
            : base(message) { }

        public StudentNotFoundException(string message, Exception inner)
            : base(message, inner) { }
    }
    ```

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception

        Public Sub New()
        End Sub

        Public Sub New(message As String)
            MyBase.New(message)
        End Sub

        Public Sub New(message As String, inner As Exception)
            MyBase.New(message, inner)
        End Sub
    End Class
    ```

1. <span data-ttu-id="33a64-113">追加のプロパティとコンストラクターを定義します。</span><span class="sxs-lookup"><span data-stu-id="33a64-113">Define any additional properties and constructors:</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception
    {
        public string StudentName { get; }

        public StudentNotFoundException() { }

        public StudentNotFoundException(string message)
            : base(message) { }

        public StudentNotFoundException(string message, Exception inner)
            : base(message, inner) { }

        public StudentNotFoundException(string message, string studentName)
            : this(message)
        {
            StudentName = studentName;
        }
    }
    ```

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception

        Public ReadOnly Property StudentName As String

        Public Sub New()
        End Sub

        Public Sub New(message As String)
            MyBase.New(message)
        End Sub

        Public Sub New(message As String, inner As Exception)
            MyBase.New(message, inner)
        End Sub

        Public Sub New(message As String, studentName As String)
            Me.New(message)
            StudentName = studentName
        End Sub
    End Class
    ```

## <a name="create-localized-exception-messages"></a><span data-ttu-id="33a64-114">ローカライズされた例外メッセージを作成する</span><span class="sxs-lookup"><span data-stu-id="33a64-114">Create localized exception messages</span></span>

<span data-ttu-id="33a64-115">カスタムの例外を作成すると、次のようなコードを使用して任意の場所に例外をスローすることができます。</span><span class="sxs-lookup"><span data-stu-id="33a64-115">You have created a custom exception, and you can throw it anywhere with code like the following:</span></span>

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

```vb
Throw New StudentNotFoundException("The student cannot be found.", "John")
```

<span data-ttu-id="33a64-116">前の行の問題は、`"The student cannot be found."` が定数文字列であることです。</span><span class="sxs-lookup"><span data-stu-id="33a64-116">The problem with the previous line is that `"The student cannot be found."` is just a constant string.</span></span> <span data-ttu-id="33a64-117">ローカライズされるアプリケーションでは、ユーザーのカルチャに応じて異なるメッセージを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="33a64-117">In a localized application, you want to have different messages depending on user culture.</span></span>
<span data-ttu-id="33a64-118">[サテライト アセンブリ](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)はこの処理に適しています。</span><span class="sxs-lookup"><span data-stu-id="33a64-118">[Satellite Assemblies](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) are a good way to do that.</span></span> <span data-ttu-id="33a64-119">サテライト アセンブリは、特定の言語のリソースを含む .dll です。</span><span class="sxs-lookup"><span data-stu-id="33a64-119">A satellite assembly is a .dll that contains resources for a specific language.</span></span> <span data-ttu-id="33a64-120">実行時に特定のリソースを要求すると、ユーザーのカルチャに応じて CLR によってそのリソースが検索されます。</span><span class="sxs-lookup"><span data-stu-id="33a64-120">When you ask for a specific resources at run time, the CLR finds that resource depending on user culture.</span></span> <span data-ttu-id="33a64-121">そのカルチャのサテライト アセンブリが見つからない場合は、既定のカルチャのリソースが使用されます。</span><span class="sxs-lookup"><span data-stu-id="33a64-121">If no satellite assembly is found for that culture, the resources of the default culture are used.</span></span>

<span data-ttu-id="33a64-122">ローカライズされた例外メッセージを作成するには:</span><span class="sxs-lookup"><span data-stu-id="33a64-122">To create the localized exception messages:</span></span>

1. <span data-ttu-id="33a64-123">リソース ファイルを保持するために、*Resources* という名前の新しいフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="33a64-123">Create a new folder named *Resources* to hold the resource files.</span></span>
1. <span data-ttu-id="33a64-124">そこに新しいリソース ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="33a64-124">Add a new resource file to it.</span></span> <span data-ttu-id="33a64-125">Visual Studio でこれを行うには、**ソリューション エクスプローラー**でフォルダーを右クリックし、 **[追加]**  >  **[新しい項目]**  >  **[リソース ファイル]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="33a64-125">To do that in Visual Studio, right-click the folder in **Solution Explorer**, and select **Add** > **New Item** > **Resources File**.</span></span> <span data-ttu-id="33a64-126">ファイルに *ExceptionMessages.resx* という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="33a64-126">Name the file *ExceptionMessages.resx*.</span></span> <span data-ttu-id="33a64-127">これは既定のリソース ファイルです。</span><span class="sxs-lookup"><span data-stu-id="33a64-127">This is the default resources file.</span></span>
1. <span data-ttu-id="33a64-128">次の図に示すように、例外メッセージの名前と値のペアを追加します。</span><span class="sxs-lookup"><span data-stu-id="33a64-128">Add a name/value pair for your exception message, like the following image shows:</span></span>

   ![既定のカルチャにリソースを追加する](media/add-resources-to-default-culture.jpg)

1. <span data-ttu-id="33a64-130">フランス語用の新しいリソース ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="33a64-130">Add a new resource file for French.</span></span> <span data-ttu-id="33a64-131">*ExceptionMessages.fr-FR.resx* という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="33a64-131">Name it *ExceptionMessages.fr-FR.resx*.</span></span>
1. <span data-ttu-id="33a64-132">例外メッセージの名前と値のペアを再び追加します。今回はフランス語の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="33a64-132">Add a name/value pair for the exception message again, but with a French value:</span></span>

   ![fr-FR カルチャにリソースを追加する](media/add-resources-to-fr-culture.jpg)

1. <span data-ttu-id="33a64-134">プロジェクトをビルドすると、ビルド出力フォルダーには、サテライト アセンブリである *.dll* ファイルを含む *fr-FR* フォルダーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="33a64-134">After you build the project, the build output folder should contain the *fr-FR* folder with a *.dll* file, which is the satellite assembly.</span></span>
1. <span data-ttu-id="33a64-135">次のようなコードを使用して例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="33a64-135">You throw the exception with code like the following:</span></span>

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QUALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

    ```vb
    Dim resourceManager As New ResourceManager("FULLY_QUALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly())
    Throw New StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John")
    ```

    > [!NOTE]
    > <span data-ttu-id="33a64-136">プロジェクト名が `TestProject` で、リソース ファイル *ExceptionMessages.resx* がプロジェクトの *Resources* フォルダー内にある場合、リソース ファイルの完全修飾名は `TestProject.Resources.ExceptionMessages` です。</span><span class="sxs-lookup"><span data-stu-id="33a64-136">If the project name is `TestProject` and the resource file *ExceptionMessages.resx* resides in the *Resources* folder of the project, the fully qualified name of the resource file is `TestProject.Resources.ExceptionMessages`.</span></span>

## <a name="see-also"></a><span data-ttu-id="33a64-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="33a64-137">See also</span></span>

- [<span data-ttu-id="33a64-138">ユーザー定義の例外を作成する方法</span><span class="sxs-lookup"><span data-stu-id="33a64-138">How to create user-defined exceptions</span></span>](how-to-create-user-defined-exceptions.md)
- [<span data-ttu-id="33a64-139">デスクトップ アプリケーションに対するサテライト アセンブリの作成</span><span class="sxs-lookup"><span data-stu-id="33a64-139">Creating Satellite Assemblies for Desktop Apps</span></span>](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [<span data-ttu-id="33a64-140">base (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="33a64-140">base (C# Reference)</span></span>](../../csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="33a64-141">this (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="33a64-141">this (C# Reference)</span></span>](../../csharp/language-reference/keywords/this.md)
