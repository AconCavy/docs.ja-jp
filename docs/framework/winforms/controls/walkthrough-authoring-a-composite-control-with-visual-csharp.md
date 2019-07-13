---
title: 'チュートリアル: Visual C# による複合コントロールの作成'
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
ms.openlocfilehash: 67fecb95ea373e88e5428251151cc30bfeb580a6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61759948"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-c"></a>チュートリアル: Visual C# による複合コントロールの作成\#
複合コントロールは、カスタム グラフィカル インターフェイスを作成し、再利用するための手段を提供します。 複合コントロールは、基本的には視覚的に表示されるコンポーネントです。 そのため、複合コントロールは、1 つ以上の Windows フォーム コントロール、コンポーネント、または機能を拡張できるコード ブロックで構成されます。コード ブロックでは、ユーザー入力の検証、表示プロパティの変更、作成者が必要とする他のタスクの実行などによって機能を拡張します。 複合コントロールは、他のコントロールと同様に Windows フォームに配置できます。 このチュートリアルの前半では、`ctlClock` という単純な複合コントロールを作成します。 チュートリアルの後半では、継承によって `ctlClock` の機能を拡張します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 新しいプロジェクトを作成するときは、ルート名前空間、アセンブリ名、プロジェクト名を設定し、既定のコンポーネントが適切な名前空間に含まれるようにするために、プロジェクトの名前を指定します。  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>ctlClockLib コントロール ライブラリと ctlClock コントロールを作成するには  
  
1. **[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** をクリックして **[新しいプロジェクト]** ダイアログ ボックスを開きます。  
  
2. Visual c# プロジェクトのリストから選択、 **Windows フォーム コントロール ライブラリ**プロジェクト テンプレートで、「`ctlClockLib`で、**名前**ボックスと順にクリックします **[ok]**。  
  
     プロジェクト名 `ctlClockLib` は、既定でルート名前空間にも割り当てられます。 ルート名前空間は、アセンブリ内のコンポーネント名の修飾に使用されます。 たとえば、`ctlClock` という名前のコンポーネントが 2 つのアセンブリに含まれている場合、`ctlClockLib.ctlClock.` を使用して目的の `ctlClock` コンポーネントを指定できます。  
  
3. ソリューション エクスプローラーで、**[UserControl1.cs]** を右クリックし、**[名前の変更]** をクリックします。 ファイル名を `ctlClock.cs` に変更します。 コード要素 "UserControl1" へのすべての参照の名前を変更するかどうかをたずねられたら、**[はい]** をクリックします。  
  
    > [!NOTE]
    >  既定では、複合コントロールを継承から、<xref:System.Windows.Forms.UserControl>システムによって提供されるクラス。 <xref:System.Windows.Forms.UserControl>クラスは、すべての複合コントロールに必要な機能を提供し、標準的なメソッドとプロパティを実装します。  
  
4. **[ファイル]** メニューの **[すべて保存]** をクリックして、プロジェクトを保存します。  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a>複合コントロールへの Windows コントロールとコンポーネントの追加  
 ビジュアル インターフェイスは、複合コントロールに不可欠な部分です。 このビジュアル インターフェイスは、デザイナー画面に 1 つ以上の Windows コントロールを追加することによって実装されます。 次の例では、複合コントロールに Windows コントロールを組み込み、機能を実装するコードを記述します。  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>複合コントロールに Label と Timer を追加するには  
  
1. ソリューション エクスプローラーで、**[ctlClock.cs]** を右クリックし、**[デザイナーの表示]** をクリックします。  
  
2. **ツールボックス**の **[コモン コントロール]** ノードを展開し、**[Label]** をダブルクリックします。  
  
     A<xref:System.Windows.Forms.Label>という名前のコントロール`label1`デザイナー画面上にコントロールに追加されます。  
  
3. デザイナーで **[label1]** をクリックします。 [プロパティ] ウィンドウで、次のプロパティを設定します。  
  
    |プロパティ|変更後の値|  
    |--------------|---------------|  
    |**Name**|`lblDisplay`|  
    |**Text**|`(blank space)`|  
    |**TextAlign**|`MiddleCenter`|  
    |**Font.Size**|`14`|  
  
4. **ツールボックス**の **[コンポーネント]** ノードを展開し、**[Timer]** をダブルクリックします。  
  
     <xref:System.Windows.Forms.Timer>コンポーネントは、実行時にビジュアル表現を持ちません。 そのため、コントロールと共にデザイナー画面に表示されるのではなく、**コンポーネント デザイナー** (デザイナー画面の下部にあるトレイ) に表示されます。  
  
5. **Component Designer**、 をクリックして**timer1**、し、設定、<xref:System.Windows.Forms.Timer.Interval%2A>プロパティを`1000`と<xref:System.Windows.Forms.Timer.Enabled%2A>プロパティを`true`します。  
  
     <xref:System.Windows.Forms.Timer.Interval%2A>プロパティは、頻度を制御、<xref:System.Windows.Forms.Timer>コンポーネントのタイマー刻み。 `timer1` が時を刻むたびに、`timer1_Tick` イベントのコードが実行されます。 このプロパティは、タイマーの刻み間隔をミリ秒単位で表します。  
  
6. **コンポーネント デザイナー**で **[timer1]** をダブルクリックして、`ctlClock` の `timer1_Tick` イベントに移動します。  
  
7. コードを次のコード サンプルのように変更します。 アクセス修飾子を `private` から `protected` に必ず変更してください。  
  
    ```csharp  
    protected void timer1_Tick(object sender, System.EventArgs e)  
    {  
        // Causes the label to display the current time.  
        lblDisplay.Text = DateTime.Now.ToLongTimeString();   
    }  
    ```  
  
     このコードにより、現在の時刻が `lblDisplay` に表示されます。 `timer1` の間隔が `1000` に設定されているため、このイベントは 1000 ミリ秒ごとに発生します。したがって、現在の時刻が 1 秒ごとに更新されます。  
  
8. `virtual` キーワードを使用して、メソッドをオーバーライド可能に変更します。 詳細については、後述の「複合コントロールの継承」を参照してください。  
  
    ```csharp  
    protected virtual void timer1_Tick(object sender, System.EventArgs e)  
    ```  
  
9. **[ファイル]** メニューの **[すべて保存]** をクリックして、プロジェクトを保存します。  
  
## <a name="adding-properties-to-the-composite-control"></a>複合コントロールへのプロパティの追加  
 時計コントロールにカプセル化されました、<xref:System.Windows.Forms.Label>コントロールと<xref:System.Windows.Forms.Timer>コンポーネントは、それぞれに固有のプロパティの独自のセット。 時計コントロールを今後使用するユーザーは、これらのコントロールの個々のプロパティにアクセスすることはできませんが、適切なコード ブロックを記述することで、カスタム プロパティを作成して公開できます。 次の手順では、ユーザーが背景とテキストの色を変更できるようにするプロパティをコントロールに追加します。  
  
#### <a name="to-add-a-property-to-your-composite-control"></a>複合コントロールにプロパティを追加するには  
  
1. ソリューション エクスプローラーで、**[ctlClock.cs]** を右クリックし、**[コードの表示]** をクリックします。  
  
     コントロールの**コード エディター**が開きます。  
  
2. `public partial class ctlClock` ステートメントを探します。 左中かっこ (`{)` の下に次のコードを入力します。  
  
    ```csharp  
    private Color colFColor;  
    private Color colBColor;  
    ```  
  
     これらのステートメントにより、作成するプロパティの値の格納に使用するプライベート変数が作成されます。  
  
3. 手順 2. の変数の宣言の下に次のコードを入力します。  
  
    ```csharp  
    // Declares the name and type of the property.  
    public Color ClockBackColor  
    {  
        // Retrieves the value of the private variable colBColor.  
        get  
        {  
            return colBColor;  
        }  
        // Stores the selected value in the private variable colBColor, and   
        // updates the background color of the label control lblDisplay.  
        set  
        {  
            colBColor = value;  
            lblDisplay.BackColor = colBColor;     
        }  
    }  
    // Provides a similar set of instructions for the foreground color.  
    public Color ClockForeColor  
    {  
        get  
        {  
            return colFColor;  
        }  
        set  
        {  
            colFColor = value;  
            lblDisplay.ForeColor = colFColor;  
        }  
    }  
    ```  
  
     上記のコードは、このコントロールを今後使用するユーザーが、`ClockForeColor` と `ClockBackColor` の 2 つのカスタム プロパティを使用できるようにします。 `get` ステートメントと `set` ステートメントは、プロパティ値を格納および取得できるようにし、そのプロパティに適した機能を実装するコードを提供します。  
  
4. **[ファイル]** メニューの **[すべて保存]** をクリックして、プロジェクトを保存します。  
  
## <a name="testing-the-control"></a>コントロールのテスト  
 コントロールはスタンドアロン アプリケーションではないため、コンテナー内でホストする必要があります。 **UserControl Test Container** でコントロールの実行時の動作をテストし、プロパティを実行します。 詳細については、「[方法 :UserControl の実行時の動作をテスト](how-to-test-the-run-time-behavior-of-a-usercontrol.md)します。  
  
#### <a name="to-test-your-control"></a>コントロールをテストするには  
  
1. F5 キーを押してプロジェクトをビルドし、**UserControl Test Container** でコントロールを実行します。  
  
2. テスト コンテナーのプロパティ グリッドで、`ClockBackColor` プロパティを探し、このプロパティを選択してカラー パレットを表示します。  
  
3. 任意の色をクリックして選択します。  
  
     コントロールの背景色が選択した色に変更されます。  
  
4. 同様のイベント シーケンスを使用して、`ClockForeColor` プロパティが予想どおりに機能していることを確認します。  
  
     このセクションとこれまでのセクションでは、コンポーネントと Windows コントロールをコードと組み合わせてパッケージ化し、複合コントロールの形でカスタム機能を提供する方法を説明しました。 また、複合コントロールのプロパティを公開し、完了後にコントロールをテストする方法も説明しました。 次のセクションでは、`ctlClock` をベースとして使用して、継承された複合コントロールを作成する方法を説明します。  
  
## <a name="inheriting-from-a-composite-control"></a>複合コントロールの継承  
 これまでのセクションでは、Windows コントロール、コンポーネント、コードを組み合わせて、再利用可能な複合コントロールを作成する方法を説明しました。 作成した複合コントロールをベースとして使用して、他のコントロールを作成できます。 基本クラスからクラスを派生するプロセスは "*継承*" と呼ばれます。 このセクションでは、`ctlAlarmClock` という複合コントロールを作成します。 このコントロールは、親コントロールである `ctlClock` から派生します。 ここでは、親のメソッドをオーバーライドし、新しいメソッドとプロパティを追加して、`ctlClock` の機能を拡張する方法を説明します。  
  
 継承されたコントロールを作成するには、まず、親から派生します。 これにより、親コントロールのプロパティ、メソッド、グラフィカル特性をすべて備えた新しいコントロールが作成されます。このコントロールをベースとして使用して、新しい機能や変更された機能を追加できます。  
  
#### <a name="to-create-the-inherited-control"></a>継承されたコントロールを作成するには  
  
1. ソリューション エクスプローラーで、**[ctlClockLib]** を右クリックし、**[追加]** をポイントして、**[ユーザー コントロール]** をクリックします。  
  
     **[新しい項目の追加]** ダイアログ ボックスが開きます。  
  
2. **[継承されたユーザー コントロール]** テンプレートを選択します。  
  
3. **[名前]** ボックスに「`ctlAlarmClock.cs`」と入力し、**[追加]** をクリックします。  
  
     **[継承ピッカー]** ダイアログ ボックスが表示されます。  
  
4. **[コンポーネント名]** の **[ctlClock]** をダブルクリックします。  
  
5. ソリューション エクスプローラーで、現在のプロジェクトを参照します。  
  
    > [!NOTE]
    >  現在のプロジェクトに、**ctlAlarmClock.cs** というファイルが追加されています。  
  
### <a name="adding-the-alarm-properties"></a>アラームのプロパティの追加  
 複合コントロールにプロパティを追加する場合と同様に、継承されたコントロールにプロパティを追加します。 ここでは、プロパティ宣言の構文を使用して、コントロールに 2 つのプロパティを追加します。`AlarmTime` プロパティは、アラームを鳴らす日時の値を格納し、`AlarmSet` プロパティは、アラームが設定されているかどうかを示します。  
  
##### <a name="to-add-properties-to-your-composite-control"></a>複合コントロールにプロパティを追加するには  
  
1. ソリューション エクスプローラーで、**[ctlAlarmClock]** を右クリックし、**[コードの表示]** をクリックします。  
  
2. `public class` ステートメントを探します。 コントロールは `ctlClockLib.ctlClock` から継承されています。 左中かっこ (`{)` ステートメントの下に次のコードを入力します。  
  
    ```csharp  
    private DateTime dteAlarmTime;  
    private bool blnAlarmSet;  
    // These properties will be declared as public to allow future   
    // developers to access them.  
    public DateTime AlarmTime  
    {  
        get  
        {  
            return dteAlarmTime;  
        }  
        set  
        {  
            dteAlarmTime = value;  
        }  
    }  
    public bool AlarmSet  
    {  
        get  
        {  
            return blnAlarmSet;  
        }  
        set  
        {  
            blnAlarmSet = value;  
        }  
    }  
    ```  
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a>コントロールのグラフィカル インターフェイスへの追加  
 継承されたコントロールには、継承元のコントロールと同じビジュアル インターフェイスがあります。 継承されたコントロールは親コントロールと同じ内在コントロールを持ちますが、内在コントロールのプロパティは、明確に公開されていない限り使用できません。 複合コントロールに追加する場合と同様に、継承された複合コントロールのグラフィカル インターフェイスに追加できます。 引き続き、アラーム時計のビジュアル インターフェイスに、アラームが鳴っているときに点滅するラベル コントロールを追加します。  
  
##### <a name="to-add-the-label-control"></a>ラベル コントロールを追加するには  
  
1. ソリューション エクスプローラーで、**[ctlAlarmClock]** を右クリックし、**[デザイナーの表示]** をクリックします。  
  
     メイン ウィンドウに、`ctlAlarmClock` のデザイナーが表示されます。  
  
2. コントロールの表示部分をクリックし、[プロパティ] ウィンドウを表示します。  
  
    > [!NOTE]
    >  すべてのプロパティが表示されていますが、淡色表示になっています。 これは、これらのプロパティが `lblDisplay` に対してネイティブであり、[プロパティ] ウィンドウで変更したりアクセスしたりすることはできないことを示しています。 既定では、複合コントロールに含まれているコントロールは `private` であり、どのような方法でもプロパティにはアクセスできません。  
  
    > [!NOTE]
    >  複合コントロールを今後使用するユーザーが、その内部のコントロールにアクセスできるようにする場合は、内部のコントロールを `public` または `protected` として宣言します。 これにより、適切なコードを使用して、複合コントロールに含まれているコントロールのプロパティの設定や変更が可能になります。  
  
3. 追加、<xref:System.Windows.Forms.Label>複合コントロールにコントロール。  
  
4. ドラッグして、マウスを使用して、<xref:System.Windows.Forms.Label>表示ボックスのすぐ下にあるコントロール。 [プロパティ] ウィンドウで、次のプロパティを設定します。  
  
    |プロパティ|設定|  
    |--------------|-------------|  
    |**Name**|`lblAlarm`|  
    |**Text**|**Alarm!**|  
    |**TextAlign**|`MiddleCenter`|  
    |**Visible**|`false`|  
  
### <a name="adding-the-alarm-functionality"></a>アラーム機能の追加  
 前の手順では、複合コントロールでアラーム機能を有効にするためのプロパティとコントロールを追加しました。 この手順では、現在の時刻をアラームの時刻と比較して、2 つの時刻が同じである場合にアラームを点滅させるコードを追加します。 `ctlClock` の `timer1_Tick` メソッドをオーバーライドし、コードを追加することで、`ctlClock` の固有の機能をすべて保持しながら、`ctlAlarmClock` の機能を拡張します。  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a>ctlClock の timer1_Tick メソッドをオーバーライドするには  
  
1. **コード エディター**で、`private bool blnAlarmSet;` ステートメントを探します。 このステートメントのすぐ下に、次のステートメントを追加します。  
  
    ```csharp  
    private bool blnColorTicker;  
    ```  
  
2. **コード エディター**で、クラスの末尾にある右中かっこ (`})` を探します。 中かっこの直前に次のコードを追加します。  
  
    ```csharp  
    protected override void timer1_Tick(object sender, System.EventArgs e)  
    {  
        // Calls the Timer1_Tick method of ctlClock.  
        base.timer1_Tick(sender, e);  
        // Checks to see if the alarm is set.  
        if (AlarmSet == false)  
            return;  
        else  
            // If the date, hour, and minute of the alarm time are the same as  
            // the current time, flash an alarm.   
        {  
            if (AlarmTime.Date == DateTime.Now.Date && AlarmTime.Hour ==   
                DateTime.Now.Hour && AlarmTime.Minute == DateTime.Now.Minute)  
            {  
                // Sets lblAlarmVisible to true, and changes the background color based on  
                // the value of blnColorTicker. The background color of the label   
                // will flash once per tick of the clock.  
                lblAlarm.Visible = true;  
                if (blnColorTicker == false)   
                {  
                    lblAlarm.BackColor = Color.Red;  
                    blnColorTicker = true;  
                }  
                else  
                {  
                    lblAlarm.BackColor = Color.Blue;  
                    blnColorTicker = false;  
                }  
            }  
            else  
            {  
                // Once the alarm has sounded for a minute, the label is made   
                // invisible again.  
                lblAlarm.Visible = false;  
            }  
        }  
    }  
    ```  
  
     このコードを追加すると、いくつかのタスクが実行されます。 `override` ステートメントは、基本コントロールから継承されたメソッドの代わりに、このメソッドを使用するようコントロールに指示します。 このメソッドが呼び出されると、メソッドは `base.timer1_Tick` ステートメントを呼び出して、オーバーライドしたメソッドを呼び出します。これにより、元のコントロールに組み込まれたすべての機能がこのコントロールに継承されます。 その後、メソッドは追加のコードを実行してアラーム機能を組み込みます。 アラームが発生すると、点滅するラベル コントロールが表示されます。  
  
     これで、アラーム時計コントロールはほぼ完成です。 あとはアラームを止める方法を実装するだけです。 これを行うには、`lblAlarm_Click` メソッドにコードを追加します。  
  
##### <a name="to-implement-the-shutoff-method"></a>停止メソッドを実装するには  
  
1. ソリューション エクスプローラーで、**[ctlAlarmClock.cs]** を右クリックし、**[デザイナーの表示]** をクリックします。  
  
     デザイナーが開きます。  
  
2. コントロールにボタンを追加します。 ボタンのプロパティを次のように設定します。  
  
    |プロパティ|[値]|  
    |--------------|-----------|  
    |**Name**|`btnAlarmOff`|  
    |**Text**|**Disable Alarm**|  
  
3. デザイナーで **[btnAlarmOff]** をダブルクリックします。  
  
     **コード エディター**が開き、`private void btnAlarmOff_Click` 行が表示されます。  
  
4. このメソッドを次のコードのように変更します。  
  
    ```csharp  
    private void btnAlarmOff_Click(object sender, System.EventArgs e)  
    {  
        // Turns off the alarm.  
        AlarmSet = false;  
        // Hides the flashing label.  
        lblAlarm.Visible = false;  
    }  
    ```  
  
5. **[ファイル]** メニューの **[すべて保存]** をクリックして、プロジェクトを保存します。  
  
### <a name="using-the-inherited-control-on-a-form"></a>フォームでの継承されたコントロールの使用  
 継承されたコントロールは基本クラスのコントロールをテストするのと同じ方法でテストできます`ctlClock`:F5 キーを押してプロジェクトをビルドし、**UserControl Test Container** でコントロールを実行します。 詳細については、「[方法 :UserControl の実行時の動作をテスト](how-to-test-the-run-time-behavior-of-a-usercontrol.md)します。  
  
 コントロールを使用するには、フォーム上でコントロールをホストする必要があります。 標準の複合コントロールと同様に、継承された複合コントロールをスタンドアロンにすることはできないので、フォームまたは他のコンテナー内でホストする必要があります。 `ctlAlarmClock` は機能が拡張されているため、テストするには追加のコードが必要となります。 次の手順では、`ctlAlarmClock` の機能をテストするための簡単なプログラムを作成します。 `ctlAlarmClock` の `AlarmTime` プロパティを設定して表示するコードを記述し、固有の機能をテストします。  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a>コントロールをビルドしてテスト フォームに追加するには  
  
1. ソリューション エクスプローラーで、**[ctlClockLib]** を右クリックし、**[ビルド]** をクリックします。  
  
2. 新しい **Windows アプリケーション** プロジェクトをソリューションに追加し、`Test` という名前を付けます。  
  
3. ソリューション エクスプローラーで、テスト プロジェクトの **[参照設定]** ノードを右クリックします。 **[参照の追加]** をクリックして、**[参照の追加]** ダイアログ ボックスを表示します。 **[プロジェクト]** というラベルのタブをクリックします。 **[プロジェクト名]** に `ctlClockLib` プロジェクトが表示されます。 プロジェクトをダブルクリックして、テスト プロジェクトへの参照を追加します。  
  
4. ソリューション エクスプローラーで、**[Test]** を右クリックし、**[ビルド]** をクリックします。  
  
5. **ツールボックス**で、**[ctlClockLib コンポーネント]** ノードを展開します。  
  
6. **[ctlAlarmClock]** をダブルクリックして、`ctlAlarmClock` のコピーをフォームに追加します。  
  
7. **ツールボックス**をダブルクリック**DateTimePicker**を追加する、<xref:System.Windows.Forms.DateTimePicker>をフォームに制御し、追加、<xref:System.Windows.Forms.Label>コントロールをダブルクリックして**ラベル**.  
  
8. マウスを使用して、各コントロールをフォーム上の使いやすい場所に配置します。  
  
9. これらのコントロールのプロパティを次のように設定します。  
  
    |コントロール|プロパティ|[値]|  
    |-------------|--------------|-----------|  
    |`label1`|**Text**|`(blank space)`|  
    ||**Name**|`lblTest`|  
    |`dateTimePicker1`|**Name**|`dtpTest`|  
    ||**Format**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
10. デザイナーで **[dtpTest]** をダブルクリックします。  
  
     **コード エディター**が開き、`private void dtpTest_ValueChanged` が表示されます。  
  
11. コードを次のように変更します。  
  
    ```csharp  
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)  
    {  
        ctlAlarmClock1.AlarmTime = dtpTest.Value;  
        ctlAlarmClock1.AlarmSet = true;  
        lblTest.Text = "Alarm Time is " +  
            ctlAlarmClock1.AlarmTime.ToShortTimeString();  
    }  
    ```  
  
12. ソリューション エクスプローラーで、**[Test]** を右クリックし、**[スタートアップ プロジェクトに設定]** をクリックします。  
  
13. **[デバッグ]** メニューの **[デバッグの開始]** をクリックします。  
  
     テスト プログラムが起動します。 現在の時刻が更新されることに注意してください、`ctlAlarmClock`制御、およびその開始時刻を示します、<xref:System.Windows.Forms.DateTimePicker>コントロール。  
  
14. をクリックして、<xref:System.Windows.Forms.DateTimePicker>の分が表示されます。  
  
15. キーボードを使用して、`ctlAlarmClock` に表示されている現在の時刻の 1 分後の値を設定します。  
  
     アラーム設定の時刻が `lblTest` に表示されます。 表示時刻がアラーム設定時刻になるまで待ちます。 表示時刻がアラーム設定時刻になると、`lblAlarm` が点滅します。  
  
16. `btnAlarmOff` をクリックしてアラームを止めます。 これでアラームをリセットできます。  
  
     このチュートリアルでは、多数の重要な概念を取り上げました。 コントロールとコンポーネントを複合コントロール コンテナーに組み込んで複合コントロールを作成する方法を説明しました。 また、コントロールにプロパティを追加する方法と、カスタム機能を実装するコードを記述する方法も説明しました。 最後のセクションでは、継承によって特定の複合コントロールの機能を拡張する方法と、ホスト メソッドをオーバーライドすることでメソッドの機能を変更する方法を説明しました。  
  
## <a name="see-also"></a>関連項目

- [さまざまなカスタム コントロール](varieties-of-custom-controls.md)
- [方法: 内のコントロールを表示、ツールボックス項目 ダイアログ ボックスの選択](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [チュートリアル: ビジュアルを含む Windows フォーム コントロールからの継承C#](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
