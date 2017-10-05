---
title: "Criando uma página de opções | Microsoft Docs"
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 10b40fccecfff4d4578b1a1bfe228d037e7516ac
ms.contentlocale: pt-br
ms.lasthandoff: 09/26/2017

---
# <a name="creating-an-options-page"></a>Criando uma página de opções
Este passo a passo cria uma página Ferramentas/opções simples que usa uma grade de propriedade para examinar e definir propriedades.  
  
 Para salvar essas propriedades para e restaurá-los a partir de um arquivo de configurações, siga estas etapas e, em seguida, consulte [criar uma categoria de configurações](../extensibility/creating-a-settings-category.md).  
  
 MPF fornece classes para ajudá-lo a criar páginas de opções de ferramentas, o <xref:Microsoft.VisualStudio.Shell.Package> classe e o <xref:Microsoft.VisualStudio.Shell.DialogPage> classe. Criar um VSPackage para fornecer um contêiner para essas páginas por subclasses de classe de pacote. Cada página de opções de ferramentas para criar, derivado da classe de DialogPage.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instalar o SDK do Visual Studio no Centro de download. Ele está incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS posteriormente. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-tools-options-grid-page"></a>Criando uma página de grade de opções de ferramentas  
 Nesta seção, você deve criar uma grade de propriedades Opções de ferramentas simple. Você usa essa grade para exibir e alterar o valor de uma propriedade.  
  
#### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>Para criar o projeto do VSIX e adicionar um VSPackage  
  
1.  Cada extensão do Visual Studio inicia com um projeto de implantação do VSIX que conterá os ativos de extensão. Criar um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projeto VSIX chamado `MyToolsOptionsExtension`. Você pode encontrar o modelo de projeto do VSIX no **novo projeto** caixa de diálogo em **Visual C# / extensibilidade**.  
  
2.  Adicionar um VSPackage adicionando um modelo de item de pacote do Visual Studio chamado `MyToolsOptionsPackage`. No **Solution Explorer**, com o botão direito no nó do projeto e selecione **Adicionar / Novo Item**. No **caixa de diálogo Adicionar Novo Item**, vá para **itens do Visual C# / extensibilidade** e selecione **pacote do Visual Studio**. No **nome** campo na parte inferior da caixa de diálogo, altere o nome de arquivo para `MyToolsOptionsPackage.cs`. Para obter mais informações sobre como criar um VSPackage, consulte [criando uma extensão com um VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).  
  
#### <a name="to-create-the-tools-options-property-grid"></a>Para criar a grade de propriedades Opções de ferramentas  
  
1.  Abra o arquivo MyToolsOptionsPackage no editor de códigos.  
  
2.  Adicione o seguinte usando a instrução.  
  
    ```csharp  
    using System.ComponentModel;  
    ```  
  
3.  Declarar uma classe OptionPageGrid e derivá-la de <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  }  
    ```  
  
4.  Aplicar um <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> à classe VSPackage para atribuir à classe de uma categoria de opções e o nome de página de opções para o OptionPageGrid. O resultado deve ter esta aparência:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
5.  Adicionar uma `OptionInteger` propriedade para o `OptionPageGrid` classe.  
  
    -   Aplicar um <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> atribuir à propriedade de uma categoria de grade de propriedade.  
  
    -   Aplicar um <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> atribuir à propriedade um nome.  
  
    -   Aplicar um <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> para atribuir a propriedade uma descrição.  
  
    ```csharp  
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
    >  A implementação padrão de <xref:Microsoft.VisualStudio.Shell.DialogPage> oferece suporte às propriedades que têm conversores apropriados ou que são estruturas ou matrizes que podem ser expandidas em propriedades que têm conversores apropriados. Para obter uma lista de conversores, consulte o <xref:System.ComponentModel> namespace.  
  
6.  Compile o projeto e comece a depuração.  
  
7.  Na instância experimental do Visual Studio, no **ferramentas** menu clique **opções**.  
  
     No painel esquerdo, você deve ver **Categoria Meus**. (Categorias de opções são listadas em ordem alfabética, portanto ele deverá aparecer sobre na metade para baixo na lista.) Abra **Categoria Meus** e, em seguida, clique em **minha página da grade**. A grade de opções é exibida no painel direito. A categoria de propriedade é **minhas opções**, e o nome da propriedade é **minha opção de inteiro**. A descrição da propriedade, **minha opção inteiro**, aparece na parte inferior do painel. Altere o valor do seu valor inicial de 256 para outra coisa. Clique em **Okey**e, em seguida, reabra **minha página da grade**. Você pode ver que o novo valor persiste.  
  
     A página de opções também está disponível por meio de início rápido do Visual Studio. Na janela de início rápido no canto superior direito do IDE, digite **Categoria Meus** e você verá **Categoria Meus -> minha página da grade** listados no menu suspenso.  
  
## <a name="creating-a-tools-options-custom-page"></a>Criar um personalizado de opções de ferramentas página  
 Nesta seção, você pode criar uma página de opções de ferramentas com uma interface do usuário personalizada. Use esta página para exibir e alterar o valor de uma propriedade.  
  
1.  Abra o arquivo MyToolsOptionsPackage no editor de códigos.  
  
2.  Adicione o seguinte usando a instrução.  
  
    ```vb  
    using System.Windows.Forms;  
    ```  
  
3.  Adicionar uma `OptionPageCustom` classe antes de `OptionPageGrid` classe. Derive a nova classe de `DialogPage`.  
  
    ```csharp  
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
  
4.  Adicione um atributo GUID. Adicione uma propriedade de OptionString:  
  
    ```csharp  
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
  
5.  Aplicar um segundo <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> à classe VSPackage. Esse atributo atribui a classe de uma categoria de opções e o nome da página de opções.  
  
    ```csharp  
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
  
6.  Adicionar um novo **controle de usuário** chamado MyUserControl ao projeto.  
  
7.  Adicionar um **TextBox** controle para o controle de usuário.  
  
     No **propriedades** janela, na barra de ferramentas, clique no **eventos** botão e, em seguida, clique duas vezes o **deixe** eventos. O novo manipulador de eventos aparece no código MyUserControl.cs.  
  
8.  Adicionar um público `OptionsPage` campo, um `Initialize` método para a classe de controle e a atualização do manipulador de eventos para definir a opção de valor para o conteúdo da caixa de texto:  
  
    ```csharp  
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
  
9. No arquivo de código do pacote, adicione uma substituição para o `OptionPageCustom.Window` propriedade à classe OptionPageCustom para criar, inicializar e retornar uma instância de `MyUserControl`. Agora, a classe deve ser assim:  
  
    ```csharp  
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
  
12. Localizar **minha categoria** e **My Custom página**.  
  
13. Alterar o valor de **OptionString**. Clique em **Okey**e, em seguida, reabra **minha página personalizado**. Você pode ver que o novo valor é persistente.  
  
## <a name="accessing-options"></a>Acessando opções  
 Nesta seção, você pode obter o valor de uma opção do VSPackage que hospeda a página de opções de ferramentas associada. A mesma técnica pode ser usada para obter o valor de qualquer propriedade pública.  
  
1.  No arquivo de código do pacote, adicionar uma propriedade pública chamada **OptionInteger** para o **MyToolsOptionsPackage** classe.  
  
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
  
     Esse código chama <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> para criar ou recuperar um `OptionPageGrid` instância. `OptionPageGrid`chamadas <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> para carregar suas opções, que são propriedades públicas.  
  
2.  Agora, adicione um modelo de item de comando personalizado chamado **MyToolsOptionsCommand** para exibir o valor. No **Adicionar Novo Item** caixa de diálogo, vá para **Visual C# / extensibilidade** e selecione **comando personalizado**. No **nome** campo na parte inferior da janela, altere o nome do arquivo de comando para **MyToolsOptionsCommand.cs**.  
  
3.  No arquivo MyToolsOptionsCommand, substitua o corpo do comando `ShowMessageBox` método com o seguinte:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;  
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));  
    }  
  
    ```  
  
4.  Compile o projeto e comece a depuração.  
  
5.  Na instância experimental, sobre o **ferramentas** menu, clique em **MyToolsOptionsCommand invocar**.  
  
     Uma caixa de mensagem exibe o valor atual de `OptionInteger`.  
  
## <a name="see-also"></a>Consulte também  
 [Opções e páginas de opções](../extensibility/internals/options-and-options-pages.md)
