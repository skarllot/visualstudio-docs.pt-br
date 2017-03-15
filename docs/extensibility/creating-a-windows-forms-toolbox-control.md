---
title: Criando um Windows Forms controle de caixa de ferramentas | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
caps.latest.revision: 19
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 770963e06655c0d4da2946fa7981fd1e4496b7f0
ms.lasthandoff: 02/22/2017

---
# <a name="creating-a-windows-forms-toolbox-control"></a>Criando um controle de caixa de ferramentas do Windows Forms
O modelo de item de controle de caixa de ferramentas do Windows Forms que está incluído no Visual Studio Extensibility Tools (SDK do VS) permite que você crie um controle que é adicionado automaticamente para o **caixa de ferramentas** quando a extensão é instalada. Este tópico mostra como usar o modelo para criar um controle de um contador simples que você pode distribuir para outros usuários.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instale o SDK do Visual Studio no Centro de download. Ele é fornecido como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-windows-forms-toolbox-control"></a>Criando um controle de caixa de ferramentas do Windows Forms  
 O modelo de controle de caixa de ferramentas do Windows Forms cria um controle de usuário indefinido e fornece toda a funcionalidade necessária para adicionar o controle para o **ferramentas**.  
  
#### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Criar uma extensão com um controle de caixa de ferramentas do Windows Forms  
  
1.  Crie um projeto do VSIX chamado `MyWinFormsControl`. Você pode encontrar o modelo de projeto do VSIX no **novo projeto** caixa de diálogo em **Visual c# / extensibilidade**.  
  
2.  Quando o projeto for aberto, adicione uma **controle de caixa de ferramentas do Windows Forms** item modelo nomeado `Counter`. No **Solution Explorer**, com o botão direito no nó do projeto e selecione **Adicionar / Novo Item**. No **Adicionar Novo Item** caixa de diálogo, vá para **Visual c# / extensibilidade** e selecione **controle de caixa de ferramentas do Windows Forms**  
  
3.  Isso adiciona um controle de usuário, uma `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>para colocar o controle no **Toolbox**e um **Microsoft.VisualStudio.ToolboxControl** entrada ativo no manifesto VSIX para implantação.</xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>  
  
### <a name="building-a-user-interface-for-the-control"></a>Criando uma Interface de usuário para o controle  
 O `Counter` controle requer dois controles filhos: um <xref:System.Windows.Forms.Label>para exibir a contagem atual e um <xref:System.Windows.Forms.Button>para redefinir a contagem como 0.</xref:System.Windows.Forms.Button> </xref:System.Windows.Forms.Label> Não há outros controles filho são necessários porque chamadores incrementará o contador programaticamente.  
  
##### <a name="to-build-the-user-interface"></a>Para criar a interface do usuário  
  
1.  Em **Solution Explorer**, clique duas vezes em Counter.cs para abri-lo no designer.  
  
2.  Remover o "Clique aqui!" **Botão** que é incluído por padrão quando você adiciona o modelo de item de controle de caixa de ferramentas do Windows Forms.  
  
3.  Do **Toolbox**, arraste um `Label` controle e, em seguida, um `Button` controle abaixo dela para a superfície de design.  
  
4.  Redimensionar o controle de usuário geral para 150, 50 pixels e redimensionar o botão controle como 50, 20 pixels.  
  
5.  No **propriedades** janela, defina os seguintes valores para os controles na superfície de design.  
  
    |Controle|Propriedade|Valor|  
    |-------------|--------------|-----------|  
    |`Label1`|**Texto**|""|  
    |`Button1`|**Nome**|btnReset|  
    |`Button1`|**Texto**|Redefinir|  
  
### <a name="coding-the-user-control"></a>Codificar o controle de usuário  
 O `Counter` controle irá expor um método para incrementar o contador, de um evento a ser gerado sempre que o contador é incrementado, uma `Reset` botão e três propriedades para armazenar a contagem atual, o texto de exibição e se deseja mostrar ou ocultar o `Reset` botão. O `ProvideToolboxControl` atributo determina onde o **Toolbox** o `Counter` controle será exibido.  
  
##### <a name="to-code-the-user-control"></a>Codificar o controle de usuário  
  
1.  Clique duas vezes no formulário para abrir seu manipulador de eventos de carga na janela de código.  
  
2.  Acima do método de manipulador de eventos na classe de controle, crie um número inteiro para armazenar o valor do contador e uma cadeia de caracteres para armazenar o texto de exibição, conforme mostrado no exemplo a seguir.  
  
    ```c#  
    int currentValue;  
    string displayText;  
    ```  
  
3.  Crie as seguintes declarações de propriedade pública.  
  
    ```c#  
    public int Value {  
        get { return currentValue; }   
    }  
  
    public string Message {  
        get { return displayText; }  
        set { displayText = value; }  
    }  
  
    public bool ShowReset {  
        get { return btnReset.Visible; }  
        set { btnReset.Visible = value; }  
    }  
  
    ```  
  
     Os chamadores podem acessar essas propriedades para obter e definir o texto de exibição do contador para mostrar ou ocultar o `Reset` botão. Os chamadores podem obter o valor atual de somente leitura `Value` propriedade, mas eles não é possível definir o valor diretamente.  
  
4.  Coloque o seguinte código `Load` evento para o controle.  
  
    ```c#  
    private void Counter_Load(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = Message + Value;  
    }  
  
    ```  
  
     Definindo o **rótulo** texto o <xref:System.Windows.Forms.UserControl.Load>evento permite que as propriedades de destino carregar antes que os valores são aplicados.</xref:System.Windows.Forms.UserControl.Load> Definindo o **rótulo** texto no construtor resultaria em vazio **rótulo**.  
  
5.  Crie o seguinte método público para incrementar o contador.  
  
    ```c#  
    public void Increment()  
    {  
        currentValue++;  
        label1.Text = displayText + Value;  
        Incremented(this, EventArgs.Empty);  
    }  
  
    ```  
  
6.  Adicione uma declaração para o `Incremented` evento para a classe de controle.  
  
    ```c#  
    public event EventHandler Incremented;  
    ```  
  
     Os chamadores podem adicionar manipuladores para esse evento para responder a alterações no valor do contador.  
  
7.  Retornar ao modo de design e clique duas vezes o `Reset` botão para gerar o `btnReset_Click` manipulador de eventos e preenchê-lo conforme mostrado no exemplo a seguir.  
  
    ```c#  
    private void btnReset_Click(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = displayText + Value;  
    }  
  
    ```  
  
8.  Imediatamente acima da definição de classe, no `ProvideToolboxControl` declaração do atributo, altere o valor do primeiro parâmetro de `"MyWinFormsControl.Counter"` para `"General"`. Isso define o nome do grupo de itens que hospedará o controle de **ferramentas**.  
  
     A exemplo a seguir mostra o `ProvideToolboxControl` atributo e a definição da classe ajustado.  
  
    ```c#  
    [ProvideToolboxControl("General", false)]  
    public partial class Counter : UserControl  
    ```  
  
### <a name="testing-the-control"></a>Testando o controle  
 Para testar um **Toolbox** controlar, primeiro testá-lo no ambiente de desenvolvimento e teste-o em um aplicativo compilado.  
  
##### <a name="to-test-the-control"></a>Para testar o controle  
  
1.  Pressione F5.  
  
     Isso cria o projeto e abre uma segunda instância Experimental do Visual Studio que tem o controle instalado.  
  
2.  Na instância Experimental do Visual Studio, crie um **Windows Forms Application** projeto.  
  
3.  Em **Solution Explorer**, clique duas vezes em Form1. cs para abri-lo no designer, se ainda não estiver aberto.  
  
4.  No **Toolbox**, o `Counter` controle deve ser exibido no **geral** seção.  
  
5.  Arraste um `Counter` controle ao seu formulário e, em seguida, selecioná-lo. O `Value`, `Message`, e `ShowReset` propriedades serão exibidas no **propriedades** janela, junto com as propriedades que são herdadas de <xref:System.Windows.Forms.UserControl>.</xref:System.Windows.Forms.UserControl>  
  
6.  Defina a propriedade `Message` como `Count:`.  
  
7.  Arraste um <xref:System.Windows.Forms.Button>o controle para o formulário e defina as propriedades name e texto do botão para `Test`.</xref:System.Windows.Forms.Button>  
  
8.  Clique duas vezes no botão para abrir Form1. cs na visualização de código e criar um manipulador de cliques.  
  
9. No manipulador de clique, chame `counter1.Increment()`.  
  
10. Na função de construtor, após a chamada para `InitializeComponent`, digite `counter1``.``Incremented +=` e, em seguida, pressione TAB duas vezes.  
  
     Um manipulador de nível de formulário para o Visual Studio gera o `counter1.Incremented` evento.  
  
11. Realce o `Throw` instrução no manipulador de eventos, digite `mbox`, e pressione a tecla TAB duas vezes para gerar uma caixa de mensagem do trecho de código mbox.  
  
12. Na próxima linha, adicione o seguinte `if` / `else` bloco para definir a visibilidade de `Reset` botão.  
  
    ```c#  
    if (counter1.Value < 5) counter1.ShowReset = false;  
    else counter1.ShowReset = true;  
    ```  
  
13. Pressione F5.  
  
     O formulário é aberto. O `Counter` controle exibe o texto a seguir.  
  
     **Contagem: 0**  
  
14. Clique em **teste**.  
  
     Os incrementos de contador e o Visual Studio exibe uma caixa de mensagem.  
  
15. Feche a caixa de mensagem.  
  
     O **redefinir** desaparecerá.  
  
16. Clique em **teste** até atinge o contador **5** fechar a mensagem de caixas de cada vez.  
  
     O **redefinir** botão é exibida novamente.  
  
17. Clique em **redefinir**.  
  
     O contador é redefinido como **0**.  
  
## <a name="next-steps"></a>Próximas etapas  
 Quando você cria um **Toolbox** controle, o Visual Studio cria um arquivo chamado *ProjectName*. VSIX na pasta \bin\debug\ do seu projeto. Você pode implantar o controle, carregando o arquivo. VSIX em uma rede ou para um site da Web. Quando um usuário abre o arquivo. VSIX, o controle seja instalado e adicionado ao Visual Studio **Toolbox** no computador do usuário. Como alternativa, você pode carregar o arquivo. VSIX para o [Galeria do Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) Web site para que os usuários possam encontrá-lo navegando no **ferramentas / extensão e atualizações** caixa de diálogo.  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo a caixa de ferramentas](../misc/extending-the-toolbox.md)   
 [Criando um controle de caixa de ferramentas do WPF](../extensibility/creating-a-wpf-toolbox-control.md)   
 [Estendendo a outras partes do Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Noções básicas de desenvolvimento de controle do Windows Forms](http://msdn.microsoft.com/Library/6277bb81-90f7-4c5b-9f4b-b02bb42dd316)
