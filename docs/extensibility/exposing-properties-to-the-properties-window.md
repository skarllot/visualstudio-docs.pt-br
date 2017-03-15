---
title: Expondo propriedades na janela Propriedades | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
caps.latest.revision: 36
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 2c31b8c677eddb54f25e52d32bb5961ea8bef7f6
ms.lasthandoff: 02/22/2017

---
# <a name="exposing-properties-to-the-properties-window"></a>Expondo propriedades na janela Propriedades
Este passo a passo expõe as propriedades públicas de um objeto para o **propriedades** janela. As alterações feitas a essas propriedades são refletidas no **propriedades** janela.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instale o SDK do Visual Studio no Centro de download. Ele é fornecido como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="exposing-properties-to-the-properties-window"></a>Expondo propriedades na janela Propriedades  
 Nesta seção, você cria uma janela de ferramenta personalizada e exibir as propriedades públicas do objeto no painel janela associada a **propriedades** janela.  
  
#### <a name="to-expose-properties-to-the-properties-window"></a>Expor propriedades na janela Propriedades  
  
1.  Cada extensão do Visual Studio inicia com um projeto de implantação do VSIX que conterá os ativos de extensão. Criar um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projeto VSIX chamado `MyObjectPropertiesExtension`. Você pode encontrar o modelo de projeto do VSIX no **novo projeto** caixa de diálogo em **Visual c# / extensibilidade**.  
  
2.  Adicionar uma janela da ferramenta, adicionando um modelo de item da janela da ferramenta personalizada denominado `MyToolWindow`. No **Solution Explorer**, com o botão direito no nó do projeto e selecione **Adicionar / Novo Item**. No **caixa de diálogo Add New Item**, vá para **itens do Visual c# / extensibilidade** e selecione **janela da ferramenta personalizada**. No **nome** campo na parte inferior da caixa de diálogo, altere o nome de arquivo para `MyToolWindow.cs`. Para obter mais informações sobre como criar uma janela de ferramentas personalizada, consulte [criando uma extensão com uma janela da ferramenta](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3.  Abra MyToolWindow.cs e adicione a seguinte instrução using:  
  
    ```  
    using System.Collections;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
4.  Agora, adicione os campos a seguir para o `MyToolWindow` classe.  
  
    ```c#  
    private ITrackSelection trackSel;  
    private SelectionContainer selContainer;  
  
    ```  
  
5.  Adicione o seguinte código à classe MyToolWindow.  
  
    ```c#  
    private ITrackSelection TrackSelection  
    {  
        get  
        {  
            if (trackSel == null)  
                trackSel =  
                   GetService(typeof(STrackSelection)) as ITrackSelection;  
            return trackSel;  
        }  
    }  
  
    public void UpdateSelection()  
    {  
        ITrackSelection track = TrackSelection;  
        if (track != null)  
            track.OnSelectChange((ISelectionContainer)selContainer);  
    }  
  
    public void SelectList(ArrayList list)  
    {  
        selContainer = new SelectionContainer(true, false);  
        selContainer.SelectableObjects = list;  
        selContainer.SelectedObjects = list;  
        UpdateSelection();  
    }  
  
    public override void OnToolWindowCreated()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
     O `TrackSelection` propriedade usa `GetService` para obter um `STrackSelection` service, que fornece um <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>interface.</xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> O `OnToolWindowCreated` manipulador de eventos e `SelectList` método juntas criam uma lista de objetos selecionados que contém somente o ferramenta janela Painel próprio objeto. O `UpdateSelection` método informa o **propriedades** janela para exibir as propriedades públicas do painel de janela de ferramenta.  
  
6.  Compile o projeto e iniciar a depuração. A instância experimental do Visual Studio deve aparecer.  
  
7.  Se o **propriedades** janela não estiver visível, abra-a pressionando F4.  
  
8.  Abra o **MyToolWindow** janela. Você pode encontrar na **exibição / Other Windows**.  
  
     A janela é aberta e as propriedades públicas do painel da janela aparecem no **propriedades** janela.  
  
9. Alterar o **legenda** propriedade no **propriedades** janela **propriedades do meu objeto**.  
  
     A legenda da janela MyToolWindow é alterada de acordo.  
  
## <a name="exposing-tool-window-properties"></a>Expondo propriedades da janela de ferramenta  
 Nesta seção, você adiciona uma janela de ferramenta e expor suas propriedades. As alterações feitas em propriedades serão refletidas no **propriedades** janela.  
  
#### <a name="to-expose-tool-window-properties"></a>Para expor propriedades da janela de ferramenta  
  
1.  Abra MyToolWindow.cs e adicione a propriedade booleana pública IsChecked à classe MyToolWindow.  
  
    ```c#  
    [Category("My Properties")]  
    [Description("MyToolWindowControl properties")]  
    public bool IsChecked  
    {  
        get {  
            if (base.Content == null)  return false;  
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;   
        }  
        set {  
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;  
        }  
    }  
    ```  
  
     Esta propriedade obtém seu estado da caixa de seleção WPF, que você criará mais tarde.  
  
2.  Abra MyToolWindowControl.xaml.cs e substitua o construtor MyToolWindowControl com o código a seguir.  
  
    ```vb  
    private MyToolWindow pane;  
    public MyToolWindowControl(MyToolWindow pane)  
    {  
        InitializeComponent();  
        this.pane = pane;  
        checkBox.IsChecked = false;  
    }  
    ```  
  
     Isso fornece `MyToolWindowControl` acesso a `MyToolWindow` painel.  
  
3.  No MyToolWindow.cs, altere o `MyToolWindow` construtor da seguinte maneira:  
  
    ```c#  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4.  Altere para o modo de exibição de design de MyToolWindowControl.  
  
5.  O botão excluir e adicionar uma caixa de seleção de **caixa de ferramentas** para o canto superior esquerdo.  
  
6.  Adicione os eventos marcada e desmarcada. Selecione a caixa de seleção no modo design. No **propriedades** janela, clique no botão de manipuladores de evento (na parte superior direita do **propriedades** janela). Localizar **check** e digite **checkbox_Checked** na caixa de texto, localize **desmarcado** e digite **checkbox_Unchecked** na caixa de texto.  
  
7.  Adicione os manipuladores de eventos de caixa de seleção:  
  
    ```c#  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = true;  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.UpdateSelection();  
    }  
    ```  
  
8.  Compile o projeto e iniciar a depuração.  
  
9. Na instância experimental, abra o **MyToolWindow** janela.  
  
     Procurar por propriedades da janela no **propriedades** janela. O **IsChecked** propriedade aparece na parte inferior da janela, sob o **propriedades do meu** categoria.  
  
10. Marque a caixa de seleção **MyToolWindow** janela. **IsChecked** no **propriedades** janela muda para **True**. Desmarque a caixa de seleção no **MyToolWindow** janela. **IsChecked** no **propriedades** janela muda para **False**. Altere o valor de **IsChecked** no **propriedades** janela. Caixa de seleção de **MyToolWindow** alterações de janela para coincidir com o novo valor.  
  
    > [!NOTE]
    >  Se você deve descartar um objeto que é exibido no **propriedades** janela, chamada `OnSelectChange` com um `null` contêiner de seleção primeiro. Depois de descartar a propriedade ou o objeto, você pode alterar para um contêiner de seleção que foi atualizada <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A>e <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A>lista.</xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> </xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A>  
  
## <a name="changing-selection-lists"></a>Alterando listas de seleção  
 Nesta seção, você adiciona uma lista de seleção para uma classe de propriedade básicas e usa a interface de janela de ferramenta para escolher qual lista de seleção para exibir.  
  
#### <a name="to-change-selection-lists"></a>Para alterar a seleção de lista  
  
1.  Abra MyToolWindow.cs e adicione uma classe pública denominada `Simple`.  
  
    ```c#  
    public class Simple  
    {  
        private string someText = "";  
  
        [Category("My Properties")]  
        [Description("Simple Properties")]  
        [DisplayName("My Text")]  
        public string SomeText  
        {  
            get { return someText; }  
            set { someText = value; }  
        }  
  
        [Category("My Properties")]  
        [Description("Read-only property")]  
        public bool ReadOnly  
        {  
            get { return false; }  
        }  
    }  
    ```  
  
2.  Adicionar uma propriedade SimpleObject para a classe MyToolWindow, além de dois métodos para alternar o **propriedades** seleção janela entre o painel da janela e o `Simple` objeto.  
  
    ```c#  
    private Simple simpleObject = null;  
    public Simple SimpleObject  
    {  
        get  
        {  
            if (simpleObject == null) simpleObject = new Simple();  
            return simpleObject;  
        }  
    }  
  
    public void SelectSimpleList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(SimpleObject);  
        SelectList(listObjects);  
    }  
  
    public void SelectThisList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
3.  No MyToolWindowControl.cs, substitua os manipuladores de caixa de seleção com estas linhas de código:  
  
    ```c#  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
     {  
        pane.IsChecked = true;  
        pane.SelectSimpleList();  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.SelectThisList();  
        pane.UpdateSelection();  
    }  
    ```  
  
4.  Compile o projeto e iniciar a depuração.  
  
5.  Na instância experimental, abra o **MyToolWindow** janela.  
  
6.  Marque a caixa de seleção no **MyToolWindow** janela. O **propriedades** janela exibe o `Simple` propriedades do objeto **SomeText** e **ReadOnly**. Desmarque a caixa de seleção. As propriedades públicas da janela aparecem no **propriedades** janela.  
  
    > [!NOTE]
    >  O nome de exibição **SomeText** é **texto Meus**.  
  
## <a name="best-practice"></a>Prática recomendada  
 Neste passo a passo, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>é implementado de forma que a coleção de objeto selecionável e a coleção de objetos selecionados são a mesma coleção.</xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> Apenas o objeto selecionado aparece na lista do navegador de propriedade. Para uma implementação de ISelectionContainer mais completa, consulte os exemplos de Reference.ToolWindow.  
  
 Janelas de ferramentas do Visual Studio persistem entre sessões do Visual Studio. Para obter mais informações sobre como manter o estado da janela de ferramenta, consulte <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo propriedades e a janela de propriedades](../extensibility/extending-properties-and-the-property-window.md)
