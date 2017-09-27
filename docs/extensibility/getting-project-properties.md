---
title: Obtendo as propriedades do projeto | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project propeties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
caps.latest.revision: 29
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
ms.openlocfilehash: 2384e27a9bb4f0aabf483bbbe0c14911e1380e32
ms.contentlocale: pt-br
ms.lasthandoff: 09/26/2017

---
# <a name="getting-project-properties"></a>Obtendo as propriedades de projeto
Este passo a passo mostra como exibe as propriedades do projeto em uma janela de ferramenta.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instalar o SDK do Visual Studio no Centro de download. Ele está incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS posteriormente. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Para criar um projeto do VSIX e adicionar uma janela de ferramenta  
  
1.  Cada extensão do Visual Studio inicia com um projeto de implantação do VSIX que conterá os ativos de extensão. Criar um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projeto VSIX chamado `ProjectPropertiesExtension`. Você pode encontrar o modelo de projeto do VSIX no **novo projeto** caixa de diálogo em **Visual C# / extensibilidade**.  
  
2.  Adicionar uma janela de ferramenta com a adição de um modelo de item da janela da ferramenta personalizada denominado `ProjectPropertiesToolWindow`. No **Solution Explorer**, com o botão direito no nó do projeto e selecione **Adicionar / Novo Item**. No **caixa de diálogo Adicionar Novo Item**, vá para **itens do Visual C# / extensibilidade** e selecione **janela da ferramenta personalizada**. No **nome** campo na parte inferior da caixa de diálogo, altere o nome de arquivo para `ProjectPropertiesToolWindow.cs`. Para obter mais informações sobre como criar uma janela de ferramenta personalizada, consulte [criando uma extensão com uma janela de ferramenta](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3.  Compile a solução e verifique se que ele foi compilado sem erros.  
  
### <a name="to-display-project-properties-in-a-tool-window"></a>Para exibir as propriedades de projeto em uma janela de ferramenta  
  
1.  No arquivo ProjectPropertiesToolWindowCommand.cs, adicione o seguinte usando instruções.  
  
    ```csharp  
    using EnvDTE;  
    using System.Windows.Controls;  
  
    ```  
  
2.  No ProjectPropertiesToolWindowControl.xaml, remova o botão existente e adicionar um modo de exibição de árvore da caixa de ferramentas. Você também pode remover o manipulador de eventos de clique do arquivo ProjectPropertiesToolWindowControl.xaml.cs.  
  
3.  Em ProjectPropertiesToolWindowCommand.cs, use o método ShowToolWindow() para abrir o projeto e suas propriedades de leitura e adicione as propriedades para o modo de exibição de árvore. O código para ShowToolWindow deve parecer com o seguinte:  
  
    ```csharp  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        ToolWindowPane window = this.package.FindToolWindow(typeof(ProjectPropertiesToolWindow), 0, true);  
        if ((null == window) || (null == window.Frame))  
        {  
            throw new NotSupportedException("Cannot create window.");  
        }  
        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
  
        // Get the tree view and populate it if there is a project open.  
        ProjectPropertiesToolWindowControl control = (ProjectPropertiesToolWindowControl)window.Content;  
        TreeView treeView = control.treeView;  
  
        // Reset the TreeView to 0 items.  
        treeView.Items.Clear();  
  
        DTE dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));  
        Projects projects = dte.Solution.Projects;  
        if (projects.Count == 0)   // no project is open  
        {  
            TreeViewItem item = new TreeViewItem();  
            item.Name = "Projects";  
            item.ItemsSource = new string[]{ "no projects are open." };  
            item.IsExpanded = true;  
            treeView.Items.Add(item);  
            return;  
        }  
  
        Project project = projects.Item(1);  
        TreeViewItem item1 = new TreeViewItem();  
        item1.Header = project.Name + "Properties";  
        treeView.Items.Add(item1);  
  
        foreach (Property property in project.Properties)  
        {  
            TreeViewItem item = new TreeViewItem();  
            item.ItemsSource = new string[] { property.Name };  
            item.IsExpanded = true;  
            treeView.Items.Add(item);  
        }  
    }  
    ```  
  
4.  Compile o projeto e comece a depuração. A instância experimental deve aparecer.  
  
5.  Na instância experimental abra um projeto.  
  
6.  No **exibição / outras janelas** clique **ProjectPropertiesToolWindow**.  
  
     Você deve ver o controle de árvore na janela da ferramenta junto com o nome do primeiro projeto e de todas as propriedades do projeto.
