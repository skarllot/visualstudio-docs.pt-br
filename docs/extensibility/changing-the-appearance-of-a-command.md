---
title: "Alterando a aparência de um comando | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
caps.latest.revision: 23
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
ms.openlocfilehash: 549d7bc0c2ea0fae75ce487926287f2f2b6152b6
ms.lasthandoff: 02/22/2017

---
# <a name="changing-the-appearance-of-a-command"></a>Alterando a aparência de um comando
Você pode fornecer comentários para o usuário, alterando a aparência de um comando. Por exemplo, convém um comando a uma aparência diferente quando ele não está disponível. Você pode ativar ou desativar a comandos, ocultar ou mostrá-los, ou marque ou desmarque-los no menu.  
  
 Para alterar a aparência de um comando, execute uma destas ações:  
  
-   Especifica os sinalizadores adequados na definição de comando no arquivo de tabela de comando.  
  
-   Use o <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>service.</xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>  
  
-   Implementar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>da interface e modificar os objetos de comando puro.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>  
  
 As etapas a seguir mostram como localizar e atualizar a aparência de um comando usando o Framework de pacote gerenciado (MPF).  
  
### <a name="to-change-the-appearance-of-a-menu-command"></a>Para alterar a aparência de um comando de menu  
  
1.  Siga as instruções em [alterar o texto de um comando de Menu](../extensibility/changing-the-text-of-a-menu-command.md) para criar um item de menu chamado `New Text`.  
  
2.  No arquivo ChangeMenuText.cs, adicione a seguinte instrução using:  
  
    ```c#  
    using System.Security.Permissions;  
    ```  
  
3.  No arquivo ChangeMenuTextPackageGuids.cs, adicione a seguinte linha:  
  
    ```c#  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4.  No arquivo ChangeMenuText.cs, substitua o código no método ShowMessageBox com o seguinte:  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5.  Obter o comando que você deseja atualizar a partir de <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>de objeto e, em seguida, defina as propriedades apropriadas no objeto command.</xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> Por exemplo, o método a seguir faz o comando especificado de um comando de VSPackage conjunto disponível ou não. O código a seguir faz com que o item de menu chamado `New Text` indisponível após ele ser clicado.  
  
    ```c#  
    public bool ChangeMyCommand(int cmdID, bool enableCmd)  
    {  
        bool cmdUpdated = false;  
        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService))  
            as OleMenuCommandService;  
        var newCmdID = new CommandID(new Guid(ChangeMenuTextPackageGuids.guidChangeMenuTextPackageCmdSet), cmdID);  
        MenuCommand mc = mcs.FindCommand(newCmdID);  
        if (mc != null)  
        {  
            mc.Enabled = enableCmd;  
            cmdUpdated = true;  
        }  
        return cmdUpdated;    }  
    }  
    ```  
  
6.  Compile o projeto e iniciar a depuração. A instância experimental do Visual Studio deve aparecer.  
  
7.  Sobre o **ferramentas** menu, clique no **invocar ChangeMenuText** comando. Neste ponto é o nome do comando **ChangeMenuText invocar**, portanto, o manipulador de comandos não chama ChangeMyCommand().  
  
8.  Sobre o **ferramentas** menu, você verá agora **novo texto**. Clique em **novo texto**. O comando agora deveriam ser esmaecido.  
  
## <a name="see-also"></a>Consulte também  
 [Barras de ferramentas, Menus e comandos](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Como os VSPackages adicionar elementos de Interface do usuário](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Estendendo Menus e comandos](../extensibility/extending-menus-and-commands.md)   
 [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
