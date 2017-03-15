---
title: "Passo a passo: Publicando um modelo de projeto de controle da Web | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modelos de controles da web"
  - "modelos de controle da Web"
ms.assetid: b56490f8-38bd-4220-a17e-5ebb30d3ac78
caps.latest.revision: 22
caps.handback.revision: 22
manager: "douge"
---
# Passo a passo: Publicando um modelo de projeto de controle da Web
Você pode criar um modelo de projeto de controle da web para usar como base para outros projetos de controle da web. Você também pode distribuir o modelo como uma extensão do VSIX.  
  
 Para distribuir uma extensão do VSIX, recomendamos que você adicioná\-lo ao site da Galeria do Visual Studio porque os desenvolvedores podem usar o Gerenciador de extensões para procurar extensões novas e atualizadas não existe. Você também pode distribuir uma extensão, colocando\-o em um servidor diferente ou gravá\-lo em um CD ou outra mídia.  
  
 Este passo a passo, que é uma das duas orientações relacionadas, ensina a criar um modelo de projeto de controle da web e, em seguida, distribuí\-lo. A explicação, [Passo a passo: Publicando uma extensão do Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md), ensina a criar e distribuir um controle da web.  
  
 Este passo a passo contém estas seções:  
  
-   Criando um modelo de projeto de controle da Web em uma extensão do VSIX  
  
-   Publicar o modelo na Galeria do Visual Studio  
  
-   Instalando o modelo da Galeria do Visual Studio  
  
-   Teste o modelo instalado  
  
-   Adicionando um Assistente de ação de depuração ao modelo  
  
## Pré-requisitos  
 Para concluir este passo a passo, você deve entender os controles da web e saber como criar projetos, definir propriedades do projeto e usar a instância experimental do Visual Studio. Visual Studio e o SDK do Visual Studio devem ser instalado no computador. Antes de começar este passo a passo, você deve concluir [Passo a passo: Publicando uma extensão do Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).  
  
## Criando um modelo de projeto de controle da Web em uma extensão do VSIX  
 Para criar um modelo de projeto de controle da web, primeiro crie um projeto de controle da web. Para este passo a passo, comece com o projeto de controle da web ColorTextControl que você criou no [Passo a passo: Publicando uma extensão do Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).  
  
 Antes de publicar um modelo de projeto para a Galeria do Visual Studio, use o **Exportar modelo como VSIX** Assistente para exportar o modelo como uma extensão do VSIX e dê a ele um ícone para ajudar a identificá\-lo no **Extension Manager** e uma imagem para ilustrar o que ele faz.  
  
#### Para preparar um projeto de controle da web para distribuição  
  
1.  No Visual Studio, abra o projeto MyWebControls.  
  
2.  Use **Extension Manager** para baixar o **Exportar Assistente de modelo** do [Galeria do Visual Studio](http://go.microsoft.com/fwlink/?LinkId=194329) site.  
  
     Depois que o assistente é instalado, quando um projeto é aberto, **Exportar modelo como VSIX** aparece no **arquivo** menu.  
  
3.  Sobre o **arquivo** menu, clique em **Exportar modelo como VSIX**.  
  
     ![Arquivo exportar projeto como VSIX](../misc/media/pcwc_exportasvsix.png "PCWC\_ExportAsVsix")  
  
4.  Sobre o **Escolher tipo de modelo** página, selecione **modelo de projeto** e, em seguida, selecione MyWebControls.csproj. Clique em **próximo**.  
  
     ![Escolha um modelo de projeto](../misc/media/pcwc_choosetemplate.png "PCWC\_ChooseTemplate")  
  
5.  Sobre o **Select Template Options** defina **nome do modelo** para `Extensibility Color Text Web Toolbox Control` e **Descrição do modelo** para `Color text web control project that produces a VSIX extension.`  
  
6.  Ao lado de **imagem do ícone** clique em **Procurar**. No **nome de arquivo** digite `*.*`. Localize Color.bmp e clique em **Abrir**.  
  
7.  Ao lado de **imagem de visualização** clique em **Procurar**. No **nome de arquivo** digite `*.*`. Localize ScreenShot.bmp e clique em **Abrir**. Clique em **próximo**.  
  
     ![Selecione as opções de modelo](../misc/media/pcwc_selecttemplateoptions2.png "PCWC\_SelectTemplateOptions2")  
  
8.  Sobre o **Selecionar opções de VSIX** página, altere **nome do produto** para `Extensibility Color Text Web Control Template`.  
  
9. Se desejar, você pode alterar **nome da empresa**, **versão**, **licença**, e **guia de Introdução URL**.  
  
10. Limpar o **importar automaticamente o modelo no Visual Studio** opção. Clique em **Concluir**.  
  
     ![Desmarque a opção automaticamente importar o modelo](../misc/media/pcwc_.png "PCWC\_")  
  
     No Windows Explorer, na... Documents\\Visual studio *\< versão \>*\\My Exported Templates\\ pasta, extensibilidade de cor do texto da Web controle Template.vsix está listada.  
  
## Publicar o modelo na Galeria do Visual Studio  
 O modelo de projeto agora está pronto para ser publicado na Galeria do Visual Studio.  
  
#### Para publicar o modelo de galeria do Visual Studio  
  
1.  Em um navegador da web, abra o [Galeria do Visual Studio](http://go.microsoft.com/fwlink/?LinkId=194329) site.  
  
2.  No canto superior direito, clique em **entrar**.  
  
3.  Use sua conta da Microsoft para entrar. Se você não tiver uma conta da Microsoft, você pode criar um aqui.  
  
4.  Clique em **carregar**.  
  
5.  Em **etapa 1: tipo de extensão**, selecione **modelo de projeto ou Item** e, em seguida, clique em **próximo**.  
  
6.  Em **etapa 2: carregar**, clique em **Procurar**. Na pasta \\My Exported Templates\\, selecione Template.vsix de controle extensibilidade cor do texto da Web. Clique em **próximo**.  
  
7.  Em **etapa 3: informações básicas**, informações do **Exportar modelo Assistente VSIX** é exibida.  
  
8.  Definir **categoria** para `ASP.NET` e **marcas** para `toolbox, web control, templates`.  
  
9. Leia o contrato de contribuição e concordar com ele e, em seguida, na caixa, digite o texto que é exibido.  
  
10. Clique em **criar contribuição**, e, em seguida, clique em **publicar**.  
  
11. Pesquise na Galeria do Visual Studio para o modelo de controle da Web do texto de cor extensibilidade. A listagem para o modelo deve aparecer.  
  
     ![Nova listagem de modelo de controle da web](../misc/media/pcwc_templatelisting.png "PCWC\_TemplateListing")  
  
## Instalando o modelo da Galeria do Visual Studio  
 Agora que o modelo de projeto de controle da web é publicado, instalá\-lo no Visual Studio e testá\-lo lá.  
  
#### Para instalar o modelo de projeto de controle da web no Visual Studio  
  
1.  No Visual Studio, no **ferramentas** menu, clique em **Extension Manager**.  
  
2.  Clique em **Galeria Online**, e em seguida, procure o modelo de controle do extensibilidade cor do texto da Web. A listagem para o modelo deve aparecer.  
  
3.  Clique em **baixar**. Depois que a extensão é baixada, clique em **instalar**.  
  
## Teste o modelo instalado  
 Agora, você pode usar o modelo de projeto de controle de Web de texto de cor de extensibilidade para criar controles personalizados da web. Você não precisa criar cada um manualmente. Esta seção mostra como usar o modelo para criar um controle da web BlueColorTextControl.  
  
#### Para criar um controle da web baseado no modelo  
  
1.  Sobre o **arquivo** aponte para **novo** e, em seguida, clique em **projeto**.  
  
2.  No painel esquerdo, clique em **Modelos Online**, expanda **modelos**, e, em seguida, clique em **ASP.NET**. No painel central, clique em **extensibilidade cor do texto da Web controle modelo**.  
  
     ![Selecione o modelo de web de texto de cor de extensibilidade](../Image/PCWC_NewProjectTemplate.png "PCWC\_NewProjectTemplate")  
  
3.  Definir **nome** para `MoreWebControls`. Clique em **OK**.  
  
4.  Em **Solution Explorer**, renomeie ColorTextControl.cs para BlueColorTextControl.cs.  
  
5.  Clique duas vezes em BlueColorTextControl.cs para abri\-lo no editor.  
  
6.  No `ToolboxData` atributo, substitua as duas ocorrências de `ColorTextControl` com `BlueColorTextControl`.  
  
     Esses valores especificam a abertura e fechamento que são geradas para o controle quando ele é arrastado do **Toolbox** para uma página da web em tempo de design.  Eles devem coincidir com o nome da classe de controle, que também é o nome do controle que aparecerão no **Toolbox**.  
  
     O início do código\-fonte da classe de controle agora deve se parecer com o código a seguir.  
  
    ```  
    namespace MoreWebControls { [DefaultProperty("Text")] [ToolboxData("<{0}:BlueColorTextControl runat=server> </{0}:BlueColorTextControl>")] [ProvideToolboxControl("MoreWebControls", false)] public class BlueColorTextControl : WebControl {  
  
    ```  
  
7.  No `get` método, altere `color:green` para `color:blue`.  
  
    ```  
    get { String s = (String)ViewState["Text"]; return "<span style='color:blue'>" + s + "</span>"; }  
    ```  
  
     Isso envolve o texto em uma marca span que as cores azul.  
  
8.  Compile o projeto MoreWebControls.  
  
## Teste o novo controle da Web  
 Agora, você pode testar se o novo controle da web está disponível na **Toolbox**. No entanto, mesmo que o projeto MoreWebControls estiver aberto, pressionando F5 não iniciar uma instância experimental do Visual Studio para testar o controle. Isso acontece porque o projeto está baseado na extensibilidade cor do texto da Web modelo do controle, que ainda não é possível definir uma ação de depuração. \(A próxima seção mostra como adicionar ao modelo de um assistente que define a ação de depuração.\) Por enquanto, para testar o controle, use as etapas a seguir.  
  
#### Para testar o novo controle da web  
  
1.  Para abrir uma instância experimental do Visual Studio, inicie a instância experimental.  
  
    1.  Em [!INCLUDE[win7](../debugger/includes/win7_md.md)], use o **Iniciar** menu \(**Start\/All programas\/Microsoft Visual Studio \< versão \> ferramentas\/SDK\/iniciar instância Experimental do Microsoft Visual Studio \< versão \>**.  
  
    2.  Em [!INCLUDE[win81](../debugger/includes/win81_md.md)], no **Iniciar** tela, digite **Iniciar instância Experimental do Microsoft Visual Studio \< versão \>**.  
  
2.  Crie um projeto de aplicativo web.  
  
3.  No projeto, abra Default. aspx. Verifique se **fonte** é exibida.  
  
4.  No **Toolbox**, no **MoreWebControls** categoria, **BlueColorTextControl** deve ser exibido.  
  
     ![MoreWebControls BlueColorTextControl](../Image/PCWC_Toolbox2.png "PCWC\_Toolbox2")  
  
5.  Arraste um BlueColorTextControl em algum lugar no `body` marca da página da web.  
  
6.  No `ColorTextControl` marca, adicione um `Text` de atributo e seu valor de fazer `Think Blue!`. A marca resultante deve se parecer com o seguinte.  
  
    ```  
    <cc1:BlueColorTextControl ID="BlueColorTextControl1" Text="Think Blue!" runat="server" />  
  
    ```  
  
7.  Pressione F5 para iniciar o ASP.NET Development Server.  
  
     A exibição do BlueColorTextControl deve ser semelhante a figura a seguir.  
  
     ![BlueColorTextControl processa pensar azul](../misc/media/pcwc_thinkblue.png "PCWC\_ThinkBlue")  
  
8.  Feche o ASP.NET Development Server.  
  
9. Feche a instância experimental do Visual Studio.  
  
## Adicionando um Assistente de ação de depuração ao modelo  
 Conforme observado na seção anterior, se você pressionar F5, quando o projeto MoreWebControls é aberto, uma instância experimental do Visual Studio não está aberta. Esta mensagem é exibida em vez disso: "um projeto com um tipo de saída da biblioteca de classe não pode ser iniciado diretamente". Isso acontece quando o local da instância experimental é desconhecido para um projeto. No entanto, você pode habilitar um modelo para determinar o local da instância experimental em um computador de destino e definir a ação de depuração apropriados. Depois disso, todos os projetos no computador que se baseiam nesse modelo responderá a F5 conforme o esperado.  
  
 Cada modelo de projeto de extensibilidade que está incluído no SDK do Visual Studio contém um assistente que é executado durante a instalação, localiza a instância experimental no computador de destino e define a ação de depuração. Você pode criar seu próprio Assistente para fazer isso e incluí\-lo em cada modelo que você distribuir.  
  
 Para adicionar um Assistente de ação de depuração para o modelo de controle extensibilidade cor do texto da Web, você deve excluir a primeira versão do modelo, o Assistente de adição a ele e, em seguida, recriá\-lo.  
  
#### Para excluir a primeira versão do modelo  
  
1.  No site da Galeria do Visual Studio, no canto superior esquerdo, clique em **Minhas contribuições**. O **extensibilidade cor do texto da Web controle modelo** listagem será exibida.  
  
2.  Para remover permanentemente o modelo de projeto da Galeria do Visual Studio, clique em **Excluir**.  
  
3.  No Visual Studio, no **ferramentas** menu, clique em **Extension Manager**.  
  
4.  Selecione **extensibilidade cor do texto da Web controle modelo**, e, em seguida, clique em **desinstalar**.  
  
5.  Fechar **Extension Manager**.  
  
6.  Feche a solução MoreWebControls.  
  
7.  Feche o Visual Studio.  
  
8.  Exclua a pasta de solução de MoreWebControls.  
  
9. Para concluir o processo de desinstalação, reinicie o Visual Studio.  
  
 O Assistente de ação de depuração deve ter uma implementação pública de `Microsoft.VisualStudio.TemplateWizard.IWizard`, e deve ser assinado com nome forte do assembly.  
  
#### Para criar o Assistente de ação de depuração  
  
1.  No **novo projeto** caixa de diálogo caixa, crie um **Visual C\#**, **Windows**, **biblioteca de classes** do projeto e denomine\- `MyWizard`.  
  
2.  No novo projeto, renomeie class1. cs para MyWizard.cs.  
  
3.  Substitua o conteúdo do MyWizard.cs com o código a seguir.  
  
    ```  
    using System; using System.Collections.Generic; using System.Linq; using System.Text; using Microsoft.VisualStudio.TemplateWizard; using System.Globalization; using EnvDTE; namespace MyWizard { public class MyWizard : IWizard { public void BeforeOpeningFile(ProjectItem projectItem) { } public void ProjectFinishedGenerating(Project project) { foreach (Configuration config in project.ConfigurationManager) { //Set up the debug options to run "devenv /rootsuffix Exp"; config.Properties.Item("StartAction").Value = 1; //Get the full path to devenv.exe through DTE.FullName config.Properties.Item("StartProgram").Value = project.DTE.FullName; config.Properties.Item("StartArguments").Value = "/rootsuffix Exp"; } } public void ProjectItemFinishedGenerating(ProjectItem projectItem) { } public void RunFinished() { } public void RunStarted(object automationObject, Dictionary<string, string> replacementsDictionary, WizardRunKind runKind, object[] customParams) { } public bool ShouldAddProjectItem(string filePath) { return true; } } }  
  
    ```  
  
4.  Adicione as seguintes referências ao projeto. Se houver mais de uma opção, selecione a referência que tem um caminho para [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
5.  Clique com botão direito no projeto MyWizard e, em seguida, clique em **propriedades**. Sobre o **assinatura** guia, selecione o **assinar o assembly** opção.  
  
6.  No **Escolher um arquivo de chave de nome forte** lista, selecione **\< Novo … \>**. O **Create Strong Name Key** caixa de diálogo é exibida.  
  
7.  Definir **nome do arquivo de chave** para `key.snk` e limpe o **proteger meu arquivo de chave com uma senha** opção.  
  
     ![Especificar um arquivo de chave](../misc/media/pcwc_strongname.png "PCWC\_StrongName")  
  
8.  Clique em **OK** adicionar key.snk ao projeto.  
  
9. Compile o projeto MyWizard como uma compilação de versão. O assistente está pronto para uso.  
  
10. Feche a solução MyWizard.  
  
#### Para incorporar o assistente e recriar o modelo  
  
1.  Siga as etapas na seção anterior, criando um modelo de projeto de controle da Web em uma extensão do VSIX, mas fazer essas alterações e adições:  
  
    -   Você não precisará baixar o **Exportar modelo como VSIX** novamente o assistente.  
  
    -   No **Export Template como VSIX** assistente no **Selecionar opções de VSIX** página, o **Assistente** navegue até o arquivo \\bin\\Release\\MyWizard.dll que você criou nas etapas anteriores e selecione.  
  
         ![Especificar o conjunto de Assistente](../misc/media/pcwc_wizardassembly.png "PCWC\_WizardAssembly")  
  
    -   Quando você for solicitado a substituir o arquivo de saída de extensão VSIX existente, clique em **Sim**.  
  
2.  Quando você chegar a seção testar o novo controle da Web, pressione F5. Uma instância experimental do Visual Studio deve ser iniciada.  
  
## Próximas etapas  
 Este passo a passo mostrou como usar o **Exportar modelo como VSIX** Assistente para criar e distribuir um modelo de projeto. Se você precisar de mais controle do modelo de projeto, por exemplo, escolha o ícone que aparece no **novo projeto** caixa de diálogo, você deve explicitamente criar o modelo de projeto e colocá\-la em uma extensão do VSIX. Para obter mais informações, consulte [Criando e de compartilhamento de projetos e modelos de Item](http://go.microsoft.com/fwlink/?LinkId=194551) no site do Blog do Visual Studio.  
  
## Consulte também  
 [Envio de extensões do Visual Studio](../extensibility/shipping-visual-studio-extensions.md)