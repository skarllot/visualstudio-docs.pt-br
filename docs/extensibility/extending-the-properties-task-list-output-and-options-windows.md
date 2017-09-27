---
title: "Estendendo propriedades, lista de tarefas, saída e opções Windows | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
caps.latest.revision: 37
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 5f16658320df87a479d9669fadf269856f80a67a
ms.contentlocale: pt-br
ms.lasthandoff: 09/26/2017

---
# <a name="extending-the-properties-task-list-output-and-options-windows"></a>Estendendo propriedades, lista de tarefas, saída e opções Windows
Você pode acessar qualquer janela de ferramenta no Visual Studio. Este passo a passo mostra como integrar as informações sobre a janela de ferramenta em um novo **opções** página e uma nova configuração no **propriedades** página e também como gravar o **delistadetarefas** e **saída** windows.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instalar o SDK do Visual Studio no Centro de download. Ele está incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS posteriormente. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-an-extension-with-a-tool-window"></a>Criar uma extensão com uma janela de ferramenta  
  
1.  Crie um projeto chamado **TodoList** usando o modelo VSIX e adicionar um modelo de item da janela de ferramenta personalizada denominado **TodoWindow**.  
  
    > [!NOTE]
    >  Para obter mais informações sobre como criar uma extensão com uma janela da ferramenta, consulte [criando uma extensão com uma janela de ferramenta](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="set-up-the-tool-window"></a>Configurar a janela da ferramenta  
 Adicione uma caixa de texto no qual você pode digitar um novo item de tarefas, um botão para adicionar o novo item à lista e uma caixa de listagem para exibir os itens na lista.  
  
1.  No TodoWindow.xaml, exclua os controles de botão, caixa de texto e StackPanel de UserControl.  
  
    > [!NOTE]
    >  Isso não exclui o **button1_Click** manipulador de eventos, que será reutilizada em uma etapa posterior.  
  
2.  Do **todos os controles do WPF** seção o **caixa de ferramentas**, arraste um **tela** controle à grade.  
  
3.  Arraste um **TextBox**, um **botão**e um **ListBox** à tela. Organize os elementos de forma que a caixa de texto e o botão estão no mesmo nível e a caixa de listagem preenche o restante da janela abaixo deles, como na figura abaixo.  
  
     ![Concluída a janela da ferramenta](../extensibility/media/t5-toolwindow.png "T5 ToolWindow")  
  
4.  No painel de XAML, encontre o botão e defina sua propriedade de conteúdo **adicionar**. Reconectar-se o manipulador de eventos do botão para o controle de botão adicionando um `Click="button1_Click"` atributo. O bloco da tela deve ter esta aparência:  
  
    ```xml  
    <Canvas HorizontalAlignment="Left" Width="306">  
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>  
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>  
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>  
    </Canvas>  
    ```  
  
#### <a name="customize-the-constructor"></a>Personalizar o construtor  
  
1.  No arquivo TodoWindowControl.xaml.cs, adicione a seguinte instrução using:  
  
    ```csharp  
    using System;  
    ```  
  
2.  Adicione uma referência pública para o TodoWindow e ter o construtor TodoWindowControl usam um parâmetro TodoWindow. O código deve ter esta aparência:  
  
    ```csharp  
    public TodoWindow parent;  
  
    public TodoWindowControl(TodoWindow window)  
    {  
        InitializeComponent();  
        parent = window;  
    }  
    ```  
  
3.  TodoWindow.cs, altere construtor TodoWindowControl para incluir o parâmetro TodoWindow. O código deve ter esta aparência:  
  
    ```csharp  
    public TodoWindow() : base(null)  
    {  
        this.Caption = "TodoWindow";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
  
         this.Content = new TodoWindowControl(this);  
    }  
    ```  
  
## <a name="create-an-options-page"></a>Criar uma página de opções  
 Você pode fornecer uma página de **opções** caixa de diálogo para que os usuários podem alterar as configurações para a janela da ferramenta. Criar uma página de opções requer uma classe que descreve as opções e uma entrada no arquivo TodoListPackage.cs ou TodoListPackage.vb.  
  
1.  Adicione uma classe denominada `ToolsOptions.cs`. Tornar a classe ToolsOptions herdam <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
    ```csharp  
    class ToolsOptions : DialogPage  
    {  
    }  
    ```  
  
2.  Adicione a seguinte instrução using:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
3.  A página de opções neste passo a passo fornece apenas uma opção chamada DaysAhead. Adicione um campo particular chamado **daysAhead** e uma propriedade chamada **DaysAhead** à classe ToolsOptions:  
  
    ```csharp  
    private double daysAhead;  
  
    public double DaysAhead  
    {  
        get { return daysAhead; }  
        set { daysAhead = value; }  
    }  
    ```  
  
 Agora você deve tornar o projeto atento esta página de opções.  
  
#### <a name="make-the-options-page-available-to-users"></a>Tornar a página de opções disponíveis para usuários  
  
1.  Em TodoWindowPackage.cs, adicione um <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> à classe TodoWindowPackage:  
  
    ```csharp  
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]  
    ```  
  
2.  O primeiro parâmetro para o construtor ProvideOptionPage é o tipo da classe ToolsOptions, que você criou anteriormente. O segundo parâmetro, "ToDo", é o nome da categoria no **opções** caixa de diálogo. O terceiro parâmetro, "Geral", é o nome da subcategoria do **opções** caixa de diálogo em que a página de opções estarão disponível. Os dois parâmetros são IDs de recurso para cadeias de caracteres; a primeira é o nome da categoria e o segundo é o nome da subcategoria. O parâmetro final determina se esta página pode ser acessada por meio de automação.  
  
     Quando um usuário abre sua página de opções, ele deve ser semelhante a imagem a seguir.  
  
     ![Página Opções de](../extensibility/media/t5optionspage.gif "T5OptionsPage")  
  
     Observe a categoria **ToDo** e a subcategoria **geral**.  
  
## <a name="make-data-available-to-the-properties-window"></a>Disponibilizar os dados para a janela de propriedades  
 Você pode disponibilizar informações da lista de tarefas, criando uma classe chamada TodoItem que armazena informações sobre os itens individuais na lista de tarefas.  
  
1.  Adicione uma classe denominada `TodoItem.cs`.  
  
     Quando a janela da ferramenta está disponível para os usuários, os itens na caixa de listagem serão representados por TodoItems. Quando o usuário seleciona um desses itens, na caixa de listagem, o **propriedades** janela exibirá informações sobre o item.  
  
     Para tornar dados disponíveis no **propriedades** janela, você transforma os dados em propriedades públicas que têm dois atributos especiais, `Description` e `Category`. `Description`é o texto que aparece na parte inferior do **propriedades** janela. `Category`determina onde a propriedade deve ser exibida quando o **propriedades** janela é exibida no **categorizado** exibição. Na figura a seguir, o **propriedades** janela está **categorizado** exibição, o **nome** propriedade no **ToDo Fields** categoria é selecionado e a descrição do **nome** propriedade é exibida na parte inferior da janela.  
  
     ![Janela propriedades](../extensibility/media/t5properties.png "T5Properties")  
  
2.  Adicione o seguinte usando instruções o arquivo todoitem. cs.  
  
    ```csharp  
    using System.ComponentModel;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  Adicionar o `public` modificador de acesso para a declaração de classe.  
  
    ```csharp  
    public class TodoItem  
    {  
    }  
    ```  
  
     Adicione as duas propriedades, Name e DueDate. Vamos fazer o UpdateList() e CheckForErrors() mais tarde.  
  
    ```csharp  
    public class TodoItem  
    {  
        private TodoWindowControl parent;  
        private string name;  
        [Description("Name of the ToDo item")]  
        [Category("ToDo Fields")]  
        public string Name  
        {  
            get { return name; }  
            set  
            {  
                name = value;  
                parent.UpdateList(this);  
            }  
        }  
  
        private DateTime dueDate;  
        [Description("Due date of the ToDo item")]  
        [Category("ToDo Fields")]  
        public DateTime DueDate  
        {  
            get { return dueDate; }  
            set  
            {  
                dueDate = value;  
                parent.UpdateList(this);  
                parent.CheckForErrors();  
            }  
        }  
    }  
    ```  
  
4.  Adicione uma referência privada para o controle de usuário. Adicione um construtor que usa o controle de usuário e o nome para este item de tarefas. Para localizar o valor para daysAhead, ele obtém a propriedade da página de opções.  
  
    ```csharp  
    private TodoWindowControl parent;  
  
    public TodoItem(TodoWindowControl control, string itemName)  
    {  
        parent = control;  
        name = itemName;  
        dueDate = DateTime.Now;  
  
        double daysAhead = 0;  
        IVsPackage package = parent.parent.Package as IVsPackage;  
        if (package != null)  
        {  
            object obj;  
            package.GetAutomationObject("ToDo.General", out obj);  
  
            ToolsOptions options = obj as ToolsOptions;  
            if (options != null)  
            {  
                daysAhead = options.DaysAhead;  
            }  
        }  
  
        dueDate = dueDate.AddDays(daysAhead);  
    }  
    ```  
  
5.  Porque instâncias do `TodoItem` classe será armazenada na caixa de listagem e caixa de listagem chamará o `ToString` função, você deve sobrecarregar o `ToString` função. Adicione o seguinte código para todoitem. cs, após o construtor e antes do final da classe.  
  
    ```csharp  
    public override string ToString()  
    {  
        return name + " Due: " + dueDate.ToShortDateString();  
    }  
    ```  
  
6.  Em TodoWindowControl.xaml.cs, adicionar métodos de stub para a classe TodoWindowControl para o `CheckForError` e `UpdateList` métodos. Colocá-los após o ProcessDialogChar e antes do final do arquivo.  
  
    ```csharp  
    public void CheckForErrors()  
    {  
    }  
    public void UpdateList(TodoItem item)  
    {  
    }  
    ```  
  
     O `CheckForError` método chamará um método que tem o mesmo nome no objeto pai, e esse método irá verificar se todos os erros tiverem ocorrido e tratá-los corretamente. O `UpdateList` método atualizará a caixa de listagem no controle pai; o método é chamado quando o `Name` e `DueDate` propriedades nessa alteração de classe. Eles serão implementados mais tarde.  
  
## <a name="integrate-into-the-properties-window"></a>Integrar a janela Propriedades  
 Agora escrever o código que gerencia a caixa de listagem, será ligada para o **propriedades** janela.  
  
 Você deve alterar o botão Clique manipulador para ler a caixa de texto, crie um TodoItem e o adiciona à caixa de listagem.  
  
1.  Substituir o `button1_Click` função com o código que cria um novo TodoItem e o adiciona à caixa de listagem. Ele chama TrackSelection(), que será definido mais tarde.  
  
    ```csharp  
    private void button1_Click(object sender, RoutedEventArgs e)  
    {  
        if (textBox.Text.Length > 0)  
        {  
            var item = new TodoItem(this, textBox.Text);  
            listBox.Items.Add(item);  
            TrackSelection();  
            CheckForErrors();  
        }  
    }  
    ```  
  
2.  No modo Design, selecione o controle de caixa de listagem. No **propriedades** janela clique o **manipuladores de eventos** botão e localizar o evento SelectionChanged. Preencha a caixa de texto com **listBox_SelectionChanged**. Isso adiciona um stub para um manipulador SelectionChanged e o atribui ao evento.  
  
3.  Implemente o método TrackSelection(). Desde que você precisará obter o <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> services, você precisa fazer o <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> acessível pelo TodoWindowControl. Adicione o seguinte método à classe TodoWindow:  
  
    ```  
    internal object GetVsService(Type service)  
    {  
        return GetService(service);  
    }  
    ```  
  
4.  Adicione o seguinte usando instruções TodoWindowControl.xaml.cs:  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  Preencha o manipulador SelectionChanged da seguinte maneira:  
  
    ```  
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)  
    {  
        TrackSelection();  
    }  
    ```  
  
6.  Agora, preencha a função TrackSelection, que fornece integração com o **propriedades** janela. Esta função é chamada quando o usuário adiciona um item à caixa de listagem ou clica em um item na caixa de listagem. Ele adiciona o conteúdo da caixa de listagem a um SelectionContainer e passa o SelectionContainer para o **propriedades** da janela <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> manipulador de eventos. O serviço de TrackSelection controla os objetos selecionados na interface do usuário (UI) e exibe suas propriedades  
  
    ```csharp  
    private SelectionContainer mySelContainer;  
    private System.Collections.ArrayList mySelItems;  
    private IVsWindowFrame frame = null;  
  
    private void TrackSelection()  
    {  
        if (frame == null)  
        {  
            var shell = parent.GetVsService(typeof(SVsUIShell)) as IVsUIShell;  
            if (shell != null)  
            {  
                var guidPropertyBrowser = new  
                Guid(ToolWindowGuids.PropertyBrowser);  
                shell.FindToolWindow((uint)__VSFINDTOOLWIN.FTW_fForceCreate,  
                ref guidPropertyBrowser, out frame);  
            }  
        }  
        if (frame != null)  
            {  
                frame.Show();  
            }  
        if (mySelContainer == null)  
        {  
            mySelContainer = new SelectionContainer();  
        }  
  
        mySelItems = new System.Collections.ArrayList();  
  
        var selected = listBox.SelectedItem as TodoItem;  
        if (selected != null)  
        {  
            mySelItems.Add(selected);  
        }  
  
        mySelContainer.SelectedObjects = mySelItems;  
  
        ITrackSelection track = parent.GetVsService(typeof(STrackSelection))  
                                as ITrackSelection;  
        if (track != null)  
        {  
            track.OnSelectChange(mySelContainer);  
        }  
    }  
    ```  
  
     Agora que você tem uma classe que o **propriedades** pode usar a janela, você pode integrar o **propriedades** janela com a janela da ferramenta. Quando o usuário clica em um item na caixa de listagem na janela da ferramenta, o **propriedades** janela deve ser atualizada adequadamente. Da mesma forma, quando o usuário altera um item de tarefas no **propriedades** janela, o item associado deve ser atualizado.  
  
7.  Agora, adicione o restante do código da função AtualizarLista em TodoWindowControl.xaml.cs. Ele deve descartar e adicionar novamente o TodoItem modificado na caixa de listagem.  
  
    ```csharp  
    public void UpdateList(TodoItem item)  
    {  
        var index = listBox.SelectedIndex;  
        listBox.Items.RemoveAt(index);  
        listBox.Items.Insert(index, item);  
        listBox.SelectedItem = index;  
    }  
    ```  
  
8.  Teste seu código. Compile o projeto e comece a depuração. A instância experimental deve aparecer.  
  
9. Abra o **Ferramentas / opções** páginas. Você deve ver a categoria de tarefas no painel esquerdo. As categorias são listadas em ordem alfabética, então procure em Ts.  
  
10. Na página de opções de tarefas, você deve ver a propriedade DaysAhead definida como **0**. Altere-o para **2**.  
  
11. No modo de exibição / menu outras janelas, abrir **TodoWindow**. Tipo **EndDate** a caixa de texto e clique em **adicionar**.  
  
12. Na caixa de listagem, você deve ver uma data dois dias depois da data atual.  
  
## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Adicione o texto na janela de saída e itens à lista de tarefas  
 Para o **lista de tarefas**, você criar um novo objeto do tipo de tarefa e, em seguida, adicionar esse objeto de tarefa para o **lista de tarefas** chamando o método Add. Para gravar o **saída** janela, chame seu método GetPane para obter um objeto de painel e, em seguida, você chamar o método OutputString do objeto de painel.  
  
1.  Em TodoWindowControl.xaml.cs, no `button1_Click` método, adicione código para obter o **geral** painel do **saída** janela (que é o padrão) e gravar nele. O método deve ter esta aparência:  
  
    ```csharp  
    private void button1_Click(object sender, EventArgs e)  
    {  
        if (textBox.Text.Length > 0)  
        {  
            var item = new TodoItem(this, textBox.Text);  
            listBox.Items.Add(item);  
  
            var outputWindow = parent.GetVsService(  
                typeof(SVsOutputWindow)) as IVsOutputWindow;  
            IVsOutputWindowPane pane;  
            Guid guidGeneralPane = VSConstants.GUID_OutWindowGeneralPane;  
            outputWindow.GetPane(ref guidGeneralPane, out pane);  
            if (pane != null)  
            {  
                 pane.OutputString(string.Format(  
                    "To Do item created: {0}\r\n",  
                 item.ToString()));  
        }  
            TrackSelection();  
            CheckForErrors();  
        }  
    }  
    ```  
  
2.  Para adicionar itens à lista de tarefas, é necessário um para adicionar uma classe aninhada para a classe TodoWindowControl. A classe aninhada deve derivar de <xref:Microsoft.VisualStudio.Shell.TaskProvider>. Adicione o seguinte código ao final da classe TodoWindowControl.  
  
    ```csharp  
    [Guid("72de1eAD-a00c-4f57-bff7-57edb162d0be")]  
    public class TodoWindowTaskProvider : TaskProvider  
    {  
        public TodoWindowTaskProvider(IServiceProvider sp)  
            : base(sp)  
        {  
        }  
    }  
    ```  
  
3.  Em seguida, adicione uma referência privada à TodoTaskProvider e um método CreateProvider() na classe TodoWindowControl. O código deve ter esta aparência:  
  
    ```csharp  
    private TodoWindowTaskProvider taskProvider;  
    private void CreateProvider()  
    {  
        if (taskProvider == null)  
        {  
            taskProvider = new TodoWindowTaskProvider(parent);  
            taskProvider.ProviderName = "To Do";  
        }  
    }  
    ```  
  
4.  Adicione ClearError(), que limpa a lista de tarefas, e ReportError(), que adiciona uma entrada à lista de tarefas, para a classe TodoWindowControl.  
  
    ```csharp  
    private void ClearError()  
    {  
        CreateProvider();  
        taskProvider.Tasks.Clear();  
    }  
    private void ReportError(string p)  
    {  
        CreateProvider();  
        var errorTask = new Task();  
        errorTask.CanDelete = false;  
        errorTask.Category = TaskCategory.Comments;  
        errorTask.Text = p;  
  
        taskProvider.Tasks.Add(errorTask);  
  
        taskProvider.Show();  
  
        var taskList = parent.GetVsService(typeof(SVsTaskList))  
            as IVsTaskList2;  
        if (taskList == null)  
        {  
            return;  
        }  
  
        var guidProvider = typeof(TodoWindowTaskProvider).GUID;  
         taskList.SetActiveProvider(ref guidProvider);  
    }  
    ```  
  
5.  Agora implemente o método CheckForErrors, da seguinte maneira.  
  
    ```csharp  
    public void CheckForErrors()  
    {  
        foreach (TodoItem item in listBox.Items)  
        {  
            if (item.DueDate < DateTime.Now)  
            {  
                ReportError("To Do Item is out of date: "  
                    + item.ToString());  
            }  
        }  
    }  
    ```  
  
## <a name="trying-it-out"></a>Experimentá-lo  
  
1.  Compile o projeto e comece a depuração. A instância experimental aparece.  
  
2.  Abra o TodoWindow (**exibição / outras janelas / TodoWindow**).  
  
3.  Digite algo na caixa de texto e, em seguida, clique em **adicionar**.  
  
     Uma data de vencimento 2 dias depois que hoje é adicionado à caixa de listagem. Nenhum erro é gerado e o **lista de tarefas** (**Exibir / tarefa lista**) não deve ter nenhuma entrada.  
  
4.  Agora, altere a configuração no **Ferramentas / opções / tarefas** página de **2** para **0**.  
  
5.  Digite algo no **TodoWindow** e, em seguida, clique em **adicionar** novamente. Isso dispara um erro e também uma entrada de **lista de tarefas**.  
  
     Como adicionar itens, a data inicial é definida como agora mais de 2 dias.  
  
6.  Sobre o **exibição** menu, clique em **saída** para abrir o **saída** janela.  
  
     Observe que sempre que você adicionar um item, uma mensagem é exibida no **lista de tarefas** painel.  
  
7.  Clique em um dos itens na caixa de listagem.  
  
     O **propriedades** janela exibe as duas propriedades para o item.  
  
8.  Alterar uma das propriedades e, em seguida, pressione ENTER.  
  
     O item é atualizado na caixa de listagem.
