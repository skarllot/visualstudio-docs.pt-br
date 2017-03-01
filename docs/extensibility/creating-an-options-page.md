---
title: "Criando uma página de opções | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
caps.latest.revision: 62
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
ms.openlocfilehash: e08a04277663b4be23efdadd6845dd66da6a154d
ms.lasthandoff: 02/22/2017

---
# <a name="creating-an-options-page"></a>Criando uma página de opções
Este passo a passo cria uma página Ferramentas/opções simples que usa uma grade de propriedade para examinar e definir propriedades.  
  
 Para salvar essas propriedades para e restaurá-los a partir de um arquivo de configurações, siga estas etapas e, em seguida, consulte [criar uma categoria de configurações](../extensibility/creating-a-settings-category.md).  
  
 MPF fornece classes para ajudá-lo a criar páginas de opções de ferramentas, a <xref:Microsoft.VisualStudio.Shell.Package>classe e a <xref:Microsoft.VisualStudio.Shell.DialogPage>classe.</xref:Microsoft.VisualStudio.Shell.DialogPage> </xref:Microsoft.VisualStudio.Shell.Package> Crie um VSPackage para fornecer um contêiner para essas páginas através de subclasses da classe de pacote. Você pode criar cada página de opções de ferramentas, derivando da classe DialogPage.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instale o SDK do Visual Studio no Centro de download. Ele é fornecido como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-tools-options-grid-page"></a>Criando uma página de grade de opções de ferramentas  
 Nesta seção, você deve criar uma grade de propriedade de opções de ferramentas simple. Você usa essa grade para exibir e alterar o valor de uma propriedade.  
  
#### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>Para criar o projeto do VSIX e adicione um VSPackage  
  
1.  Cada extensão do Visual Studio inicia com um projeto de implantação do VSIX que conterá os ativos de extensão. Criar um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projeto VSIX chamado `MyToolsOptionsExtension`. Você pode encontrar o modelo de projeto do VSIX no **novo projeto** caixa de diálogo em **Visual c# / extensibilidade**.  
  
2.  Adicionar um VSPackage adicionando um modelo de item de pacote do Visual Studio chamado `MyToolsOptionsPackage`. No **Solution Explorer**, com o botão direito no nó do projeto e selecione **Adicionar / Novo Item**. No **caixa de diálogo Add New Item**, vá para **itens do Visual c# / extensibilidade** e selecione **Visual Studio Package**. No **nome** campo na parte inferior da caixa de diálogo, altere o nome de arquivo para `MyToolsOptionsPackage.cs`. Para obter mais informações sobre como criar um VSPackage, consulte [criando uma extensão com um VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).  
  
#### <a name="to-create-the-tools-options-property-grid"></a>Para criar a grade de propriedades de opções de ferramentas  
  
1.  Abra o arquivo MyToolsOptionsPackage no editor de códigos.  
  
2.  Adicione a seguinte instrução using.  
  
    ```c#  
    using System.ComponentModel;  
    ```  
  
3.  Declare uma classe OptionPageGrid e derive-o de <xref:Microsoft.VisualStudio.Shell.DialogPage>.</xref:Microsoft.VisualStudio.Shell.DialogPage>  
  
    ```c#  
    public class OptionPageGrid : DialogPage  
    {  }  
    ```  
  
4.  Aplicar um <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>à classe VSPackage para atribuir à classe de uma categoria de opções e o nome de página de opções para o OptionPageGrid.</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> O resultado deve ter esta aparência:  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
5.  Adicionar uma `OptionInteger` propriedade para o `OptionPageGrid` classe.  
  
    -   Aplicar um <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName>atribuir à propriedade uma categoria de grade de propriedade.</xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName>  
  
    -   Aplicar um <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName>atribuir à propriedade um nome.</xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName>  
  
    -   Aplicar um <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName>atribuir à propriedade uma descrição.</xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName>  
  
    ```c#  
    public class OptionPageGrid : DialogPage  
    {  
        private int optionInt = 256;  
  
        [Category("My Category")]  
        [DisplayName("My Integer Option")]  
        [Description("My integer option")]  
        public int OptionInteger  
        {  
            get { return optionInt; }  
            set { optionInt = value; }  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  A implementação padrão de <xref:Microsoft.VisualStudio.Shell.DialogPage>dá suporte às propriedades que têm conversores apropriados ou que são estruturas ou matrizes que podem ser expandidos para propriedades que tenham conversores apropriados.</xref:Microsoft.VisualStudio.Shell.DialogPage> Para obter uma lista dos conversores, consulte a <xref:System.ComponentModel>namespace.</xref:System.ComponentModel>  
  
6.  Compile o projeto e iniciar a depuração.  
  
7.  Na instância experimental do Visual Studio, no **ferramentas** menu clique **opções**.  
  
     No painel à esquerda, você deve ver **My Category**. (Categorias de opções são listadas em ordem alfabética, portanto ele deverá aparecer sobre metade para baixo na lista.) Abra **My Category** e, em seguida, clique em **minha página de grade**. A grade de opções é exibida no painel à direita. A categoria de propriedade é **minhas opções**, e o nome da propriedade é **minha opção inteiro**. A descrição da propriedade, **minha opção inteiro**, aparece na parte inferior do painel. Altere o valor do seu valor inicial de 256 para algo mais. Clique em **Okey**e, em seguida, reabra **minha página de grade**. Você pode ver que o novo valor persiste.  
  
     A página de opções também está disponível por meio de início rápido do Visual Studio. Na janela de início rápido no canto superior direito do IDE, digite **My Category** e você verá **My Category – > minha página de grade** listados na lista suspensa.  
  
## <a name="creating-a-tools-options-custom-page"></a>Criar um personalizado de opções de ferramentas página  
 Nesta seção, você criará uma página de opções de ferramentas com uma interface do usuário personalizada. Use esta página para exibir e alterar o valor de uma propriedade.  
  
1.  Abra o arquivo MyToolsOptionsPackage no editor de códigos.  
  
2.  Adicione a seguinte instrução using.  
  
    ```vb  
    using System.Windows.Forms;  
    ```  
  
3.  Adicionar uma `OptionPageCustom` classe antes de `OptionPageGrid` classe. Derive a classe nova de `DialogPage`.  
  
    ```c#  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
    }  
    ```  
  
4.  Adicione um atributo GUID. Adicione uma propriedade OptionString:  
  
    ```c#  
    [Guid("00000000-0000-0000-0000-000000000000")]  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
    }  
    ```  
  
5.  Aplicar um segundo <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>à classe VSPackage.</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Esse atributo atribui a classe de uma categoria de opções e o nome da página de opções.  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    [ProvideOptionPage(typeof(OptionPageCustom),  
        "My Category", "My Custom Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
6.  Adicione um novo **controle de usuário** chamado MyUserControl ao projeto.  
  
7.  Adicionar uma **TextBox** controle para o controle de usuário.  
  
     No **propriedades** na barra de ferramentas, clique o **eventos** botão e, em seguida, clique duas vezes o **deixe** eventos. O novo manipulador de eventos é exibida no código MyUserControl.cs.  
  
8.  Adicionar um público `OptionsPage` campo, um `Initialize` método à classe de controle e o conteúdo da caixa de texto valor do manipulador de eventos para definir a opção de atualização:  
  
    ```c#  
    public partial class MyUserControl : UserControl  
    {  
        public MyUserControl()  
        {  
            InitializeComponent();  
        }  
  
        internal OptionPageCustom optionsPage;  
  
        public void Initialize()  
        {  
            textBox1.Text = optionsPage.OptionString;  
        }  
  
        private void textBox1_Leave(object sender, EventArgs e)  
        {  
            optionsPage.OptionString = textBox1.Text;  
        }  
    }  
    ```  
  
     O `optionsPage` campo contém uma referência ao pai `OptionPageCustom` instância. O `Initialize` método exibe `OptionString` no **caixa de texto**. O manipulador de eventos grava o valor atual do **TextBox** para o `OptionString` ao focalizar deixa o **caixa de texto**.  
  
9. No arquivo de pacote de código, adicione uma substituição para o `OptionPageCustom.Window` propriedade à classe OptionPageCustom para criar, inicializar e retornar uma instância de `MyUserControl`. A classe deve ficar assim:  
  
    ```c#  
    [Guid("00000000-0000-0000-0000-000000000000")]  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
  
        protected override IWin32Window Window  
        {  
            get  
            {  
                MyUserControl page = new MyUserControl();  
                page.optionsPage = this;  
                page.Initialize();  
                return page;  
            }  
        }  
    }  
    ```  
  
10. Compile e execute o projeto.  
  
11. Na instância experimental, clique em **Ferramentas / opções**.  
  
12. Localizar **minha categoria** e **meu personalizado página**.  
  
13. Altere o valor de **OptionString**. Clique em **Okey**e, em seguida, reabra **minha página personalizada**. Você pode ver que o novo valor tem persistente.  
  
## <a name="accessing-options"></a>Acessando opções  
 Nesta seção, você pode obter o valor de uma opção de VSPackage que hospeda a página de opções de ferramentas associada. A mesma técnica pode ser usada para obter o valor de qualquer propriedade pública.  
  
1.  No arquivo de código do pacote, adicionar uma propriedade pública denominada **OptionInteger** para o **MyToolsOptionsPackage** classe.  
  
    ```  
    public int OptionInteger  
    {  
        get  
        {  
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));  
            return page.OptionInteger;  
        }  
    }  
  
    ```  
  
     Esse código chama <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A>para criar ou recuperar um `OptionPageGrid` instância.</xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> `OptionPageGrid`chamadas <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A>para carregar suas opções, que são propriedades públicas.</xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A>  
  
2.  Agora, adicione um modelo de item de comando personalizada chamado **MyToolsOptionsCommand** para exibir o valor. No **Adicionar Novo Item** caixa de diálogo, vá para **Visual c# / extensibilidade** e selecione **comando personalizado**. No **nome** campo na parte inferior da janela, altere o nome do arquivo de comando para **MyToolsOptionsCommand.cs**.  
  
3.  No arquivo MyToolsOptionsCommand, substitua o corpo do comando `ShowMessageBox` método com o seguinte:  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;  
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));  
    }  
  
    ```  
  
4.  Compile o projeto e iniciar a depuração.  
  
5.  Na instância experimental, sobre o **ferramentas** menu, clique em **MyToolsOptionsCommand invocar**.  
  
     Uma caixa de mensagem exibe o valor atual de `OptionInteger`.  
  
## <a name="see-also"></a>Consulte também  
 [Opções e páginas de opções](../extensibility/internals/options-and-options-pages.md)
