---
title: '方法: ObservableCollection を作成およびバインドする'
description: Windows Presentation Foundation で ObservableCollection クラスから派生するコレクションを作成し、それにバインドする方法について説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], ObservableCollection class
- notifications [WPF]
ms.assetid: 6cf7e275-df76-41c6-a611-53b889b8fd5a
ms.openlocfilehash: 36e3d2d84aff0ab96c9b2914da28d4c968c32bac
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617870"
---
# <a name="how-to-create-and-bind-to-an-observablecollection"></a><span data-ttu-id="1caf1-103">方法: ObservableCollection を作成およびバインドする</span><span class="sxs-lookup"><span data-stu-id="1caf1-103">How to: Create and Bind to an ObservableCollection</span></span>
<span data-ttu-id="1caf1-104">この例では、項目が追加または削除されたときに通知するコレクション クラスである <xref:System.Collections.ObjectModel.ObservableCollection%601> クラスから派生したコレクションを作成およびバインドする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1caf1-104">This example shows how to create and bind to a collection that derives from the <xref:System.Collections.ObjectModel.ObservableCollection%601> class, which is a collection class that provides notifications when items get added or removed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1caf1-105">例</span><span class="sxs-lookup"><span data-stu-id="1caf1-105">Example</span></span>  
 <span data-ttu-id="1caf1-106">`NameList` コレクションの実装例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1caf1-106">The following example shows the implementation of a `NameList` collection:</span></span>  
  
```csharp  
public class NameList : ObservableCollection<PersonName>  
{  
    public NameList() : base()  
    {  
        Add(new PersonName("Willa", "Cather"));  
        Add(new PersonName("Isak", "Dinesen"));  
        Add(new PersonName("Victor", "Hugo"));  
        Add(new PersonName("Jules", "Verne"));  
    }  
  }  
  
  public class PersonName  
  {  
      private string firstName;  
      private string lastName;  
  
      public PersonName(string first, string last)  
      {  
          this.firstName = first;  
          this.lastName = last;  
      }  
  
      public string FirstName  
      {  
          get { return firstName; }  
          set { firstName = value; }  
      }  
  
      public string LastName  
      {  
          get { return lastName; }  
          set { lastName = value; }  
      }  
  }  
```  
  
```vb  
Public Class NameList  
    Inherits ObservableCollection(Of PersonName)  
  
    ' Methods  
    Public Sub New()  
        MyBase.Add(New PersonName("Willa", "Cather"))  
        MyBase.Add(New PersonName("Isak", "Dinesen"))  
        MyBase.Add(New PersonName("Victor", "Hugo"))  
        MyBase.Add(New PersonName("Jules", "Verne"))  
    End Sub  
  
End Class  
  
Public Class PersonName  
    ' Methods  
    Public Sub New(ByVal first As String, ByVal last As String)  
        Me._firstName = first  
        Me._lastName = last  
    End Sub  
  
    ' Properties  
    Public Property FirstName() As String  
        Get  
            Return Me._firstName  
        End Get  
        Set(ByVal value As String)  
            Me._firstName = value  
        End Set  
    End Property  
  
    Public Property LastName() As String  
        Get  
            Return Me._lastName  
        End Get  
        Set(ByVal value As String)  
            Me._lastName = value  
        End Set  
    End Property  
  
    ' Fields  
    Private _firstName As String  
    Private _lastName As String  
End Class  
```  
  
 <span data-ttu-id="1caf1-107">このコレクションをバインディングに使用できるようにする方法は、「[XAML でデータをバインディング可能にする](how-to-make-data-available-for-binding-in-xaml.md)」で説明した、他の共通言語ランタイム (CLR) オブジェクトの場合と同様です。</span><span class="sxs-lookup"><span data-stu-id="1caf1-107">You can make the collection available for binding the same way you would with other common language runtime (CLR) objects, as described in [Make Data Available for Binding in XAML](how-to-make-data-available-for-binding-in-xaml.md).</span></span> <span data-ttu-id="1caf1-108">たとえば、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] でコレクションをインスタンス化し、次に示すように、そのコレクションをリソースとして指定します。</span><span class="sxs-lookup"><span data-stu-id="1caf1-108">For example, you can instantiate the collection in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] and specify the collection as a resource, as shown here:</span></span>  
  
```xaml  
<Window  
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
  xmlns:c="clr-namespace:SDKSample"  
  x:Class="SDKSample.Window1"  
  Width="400"  
  Height="280"  
  Title="MultiBinding Sample">  
  
  <Window.Resources>  
    <c:NameList x:Key="NameListData"/>  
  
...  
  
</Window.Resources>  
```  
  
 <span data-ttu-id="1caf1-109">その後、コレクションにバインドできます。</span><span class="sxs-lookup"><span data-stu-id="1caf1-109">You can then bind to the collection:</span></span>  
  
```xaml  
<ListBox Width="200"  
         ItemsSource="{Binding Source={StaticResource NameListData}}"  
         ItemTemplate="{StaticResource NameItemTemplate}"  
         IsSynchronizedWithCurrentItem="True"/>  
```  
  
 <span data-ttu-id="1caf1-110">`NameItemTemplate` の定義は、ここには示していません。</span><span class="sxs-lookup"><span data-stu-id="1caf1-110">The definition of `NameItemTemplate` is not shown here.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1caf1-111">コレクション内のオブジェクトは、「[バインディング ソースの概要](binding-sources-overview.md)」で説明されている要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="1caf1-111">The objects in your collection must satisfy the requirements described in the [Binding Sources Overview](binding-sources-overview.md).</span></span> <span data-ttu-id="1caf1-112">具体的には、<xref:System.Windows.Data.BindingMode.OneWay> または <xref:System.Windows.Data.BindingMode.TwoWay> を使用している場合は (たとえば、ソース プロパティが動的に変更されたときに [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を更新する場合など)、<xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスなどの適切なプロパティ変更通知メカニズムを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1caf1-112">In particular, if you are using <xref:System.Windows.Data.BindingMode.OneWay> or <xref:System.Windows.Data.BindingMode.TwoWay> (for example, you want your [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to update when the source properties change dynamically), you must implement a suitable property changed notification mechanism such as the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span>  
  
 <span data-ttu-id="1caf1-113">詳しくは、「[データ バインディングの概要](../../../desktop-wpf/data/data-binding-overview.md)」の「コレクションへのバインド」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1caf1-113">For more information, see the Binding to Collections section in the [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1caf1-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="1caf1-114">See also</span></span>

- [<span data-ttu-id="1caf1-115">ビュー内のデータの並べ替え</span><span class="sxs-lookup"><span data-stu-id="1caf1-115">Sort Data in a View</span></span>](how-to-sort-data-in-a-view.md)
- [<span data-ttu-id="1caf1-116">ビュー内のデータをフィルター処理する</span><span class="sxs-lookup"><span data-stu-id="1caf1-116">Filter Data in a View</span></span>](how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="1caf1-117">XAML でビューを使用してデータの並べ替えおよびグループ化を行う</span><span class="sxs-lookup"><span data-stu-id="1caf1-117">Sort and Group Data Using a View in XAML</span></span>](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [<span data-ttu-id="1caf1-118">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="1caf1-118">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="1caf1-119">方法トピック</span><span class="sxs-lookup"><span data-stu-id="1caf1-119">How-to Topics</span></span>](data-binding-how-to-topics.md)
