---
title: "Estendendo a janela de saída | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
caps.latest.revision: 13
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
ms.openlocfilehash: d5c830046aa89f9a7eeba765846b2b7484221aa7
ms.lasthandoff: 02/22/2017

---
# <a name="extending-the-output-window"></a>Estendendo a janela de saída
O **saída** janela é um conjunto de painéis de texto de leitura/gravação. O Visual Studio tem esses painéis internos: **criar**, em quais projetos de comunicar mensagens sobre compilações, e **geral**, em que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se comunica mensagens sobre o IDE. Projetos obtém uma referência para o **criar** automaticamente por meio do painel o <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>métodos de interface e o Visual Studio oferece acesso direto ao **geral** painel por meio o <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane>service.</xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> </xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> Além de painéis internos, você pode criar e gerenciar seus próprios painéis personalizados.  
  
 Você pode controlar o **saída** janela diretamente por meio de <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane>interfaces.</xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> </xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> O <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>interface, que é oferecido pelo <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow>de serviço, define métodos para criar, recuperar e destruindo **saída** painéis de janela.</xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> </xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> O <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>interface define métodos para mostrando painéis, ocultando painéis e manipular seu texto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> Uma maneira alternativa de controlar o **saída** janela é por meio de <xref:EnvDTE.OutputWindow>e <xref:EnvDTE.OutputWindowPane>objetos no modelo de objeto de automação do Visual Studio.</xref:EnvDTE.OutputWindowPane> </xref:EnvDTE.OutputWindow> Esses objetos encapsulam quase toda a funcionalidade da <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane>interfaces.</xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> </xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> Além disso, o <xref:EnvDTE.OutputWindow>e <xref:EnvDTE.OutputWindowPane>objetos adicionam algumas funcionalidades de alto nível para facilitar a enumerar o **saída** painéis de janela e recuperar texto a partir de painéis.</xref:EnvDTE.OutputWindowPane> </xref:EnvDTE.OutputWindow>  
  
## <a name="creating-an-extension-that-uses-the-output-pane"></a>Criando uma extensão que usa o painel de saída  
 Você pode fazer uma extensão que emprega diversos aspectos do painel de saída.  
  
1.  Crie um projeto do VSIX chamado `TestOutput` com um comando de menu chamado **TestOutput**. Para obter mais informações, consulte [criando uma extensão com um comando de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Adicione as seguintes referências:  
  
    1.  EnvDTE  
  
    2.  EnvDTE80  
  
3.  No TestOutput.cs, adicione a seguinte instrução using:  
  
    ```f#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  TestOutput.cs, exclua o método ShowMessageBox. Adicione o seguinte stub do método:  
  
    ```c#  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
5.  No construtor TestOutput, altere o manipulador de comandos para OutputCommandHandler. Aqui está a parte que adiciona os comandos:  
  
    ```c#  
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    if (commandService != null)  
    {  
        CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
        EventHandler eventHandler = OutputCommandHandler;  
        MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
        commandService.AddCommand(menuItem);  
    }  
    ```  
  
6.  As seções a seguir têm métodos diferentes que mostram diferentes maneiras de lidar com o painel de saída. Você pode chamar esses métodos ao corpo do método OutputCommandHandler(). Por exemplo, o código a seguir adiciona o método CreatePane() fornecido na próxima seção.  
  
    ```c#  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
        CreatePane(new Guid(), "Created Pane", true, false);  
    }  
    ```  
  
## <a name="creating-an-output-window-with-ivsoutputwindow"></a>Criando uma janela de saída com IVsOutputWindow  
 Este exemplo mostra como criar um novo **saída** painel da janela usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>  
  
```c#  
void CreatePane(Guid paneGuid, string title,   
    bool visible, bool clearWithSolution)  
{  
    IVsOutputWindow output =   
        (IVsOutputWindow)GetService(typeof(SVsOutputWindow));  
    IVsOutputWindowPane pane;  
  
    // Create a new pane.  
    output.CreatePane(  
        ref paneGuid,   
        title,   
        Convert.ToInt32(visible),   
        Convert.ToInt32(clearWithSolution));  
  
    // Retrieve the new pane.  
    output.GetPane(ref paneGuid, out pane);  
  
     pane.OutputString("This is the Created Pane \n");  
}  
```  
  
 Se você adicionar esse método para a extensão fornecida na seção anterior, quando você clica o **invocar TestOutput** comando você deve ver o **saída** janela com um cabeçalho que diz **Mostrar saída de: CreatedPane** e as palavras **isso é o painel criado** no painel em si.  
  
## <a name="creating-an-output-window-with-outputwindow"></a>Criando uma janela de saída com OutputWindow  
 Este exemplo mostra como criar um **saída** painel da janela usando o <xref:EnvDTE.OutputWindow>objeto.</xref:EnvDTE.OutputWindow>  
  
```c#  
void CreatePane(string title)  
{  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
  
    try  
    {  
        // If the pane exists already, write to it.  
        panes.Item(title);  
    }  
    catch (ArgumentException)  
    {  
        // Create a new pane and write to it.  
        return panes.Add(title);  
    }  
}  
```  
  
 Embora o <xref:EnvDTE.OutputWindowPanes>coleção permite que você recupere um **saída** painel seu título, títulos do painel não há garantia de exclusividade.</xref:EnvDTE.OutputWindowPanes> Quando você tiver dúvidas a exclusividade de um título, use o <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A>método para recuperar o painel correto pelo seu GUID.</xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A>  
  
 Se você adicionar esse método para a extensão fornecida na seção anterior, quando você clica o **invocar TestOutput** comando você deve ver a janela de saída com um cabeçalho que diz **Mostrar saída de: DTEPane** e as palavras **adicionado DTE painel** no painel em si.  
  
## <a name="deleting-an-output-window"></a>Excluindo uma janela de saída  
 Este exemplo mostra como excluir um **saída** painel da janela.  
  
```c#  
void DeletePane(Guid paneGuid)  
{  
    IVsOutputWindow output =  
    (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow));  
  
    IVsOutputWindowPane pane;  
    output.GetPane(ref paneGuid, out pane);  
  
    if (pane == null)  
    {  
        CreatePane(paneGuid, "New Pane\n", true, true);  
    }  
     else  
    {  
        output.DeletePane(ref paneGuid);  
    }  
}  
```  
  
 Se você adicionar esse método para a extensão fornecida na seção anterior, quando você clica o **invocar TestOutput** comando você deve ver a janela de saída com um cabeçalho que diz **Mostrar saída de: novo painel** e as palavras **adicionado painel criado** no painel em si. Se você clicar no **TestOutput invocar** comando novamente, o painel é excluído.  
  
## <a name="getting-the-general-pane-of-the-output-window"></a>Obtendo o painel geral da janela de saída  
 Este exemplo mostra como obter interna **geral** painel do **saída** janela.  
  
```c#  
void GetGeneralPane()  
{  
    return (IVsOutputWindowPane)GetService(  
        typeof(SVsGeneralOutputWindowPane));  
}  
```  
  
 Se você adicionar esse método para a extensão fornecida na seção anterior, quando você clica o **invocar TestOutput** comando, você verá que o **saída** janela mostra as palavras **painel geral encontrado** no painel.  
  
## <a name="getting-the-build-pane-of-the-output-window"></a>Obtendo o painel compilação da janela de saída  
 Este exemplo mostra como localizar o painel compilação e gravar nele. Uma vez que o painel de compilação não é ativado por padrão, ele será ativado-lo também.  
  
```c#  
void OutputTaskItemStringExExample(string buildMessage)  
{  
    EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE));  
  
    EnvDTE.OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
    foreach (EnvDTE.OutputWindowPane pane in panes)  
        {  
            if (pane.Name.Contains("Build"))  
            {  
                pane.OutputString(buildMessage + "\n");  
                pane.Activate();  
                return;  
             }  
        }  
}  
```
