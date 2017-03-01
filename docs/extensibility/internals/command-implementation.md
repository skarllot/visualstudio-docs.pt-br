---
title: "Implementação de comando | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
caps.latest.revision: 24
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
ms.openlocfilehash: bd3c23baffe767083bc541fa9e2e8718834b3ee1
ms.lasthandoff: 02/22/2017

---
# <a name="command-implementation"></a>Implementação de comandos
Para implementar um comando em um VSPackage, você deve executar as seguintes tarefas:  
  
1.  No arquivo. VSCT, configurar um grupo de comando e, em seguida, adicione o comando a ele. Para obter mais informações, consulte [tabela de comando do Visual Studio (. Arquivos VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)'  
  
2.  Registre o comando com o Visual Studio.  
  
3.  Implemente o comando.  
  
 As seções a seguir explicam como registrar e implementar comandos.  
  
## <a name="registering-commands-with-visual-studio"></a>Registro de comandos com o Visual Studio  
 Se o comando deve aparecer em um menu, você deve adicionar <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>seu VSPackage, e usá-la como um valor, o nome do menu ou sua ID de recurso</xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 Além disso, você deve registrar o comando <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>.</xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> Você pode obter esse serviço usando o <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>método se o VSPackage é derivado de <xref:Microsoft.VisualStudio.Shell.Package>.</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>  
  
```  
OleMenuCommandService mcs = GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
if ( null != mcs )  
{  
    // Create the command for the menu item.  
    CommandID menuCommandID = new CommandID(guidCommandGroup, myCommandID);  
    MenuCommand menuItem = new MenuCommand(MenuItemCallback, menuCommandID );  
    mcs.AddCommand( menuItem );  
}  
  
```  
  
## <a name="implementing-commands"></a>Implementação de comandos  
 Há várias maneiras de implementar comandos. Se você quiser que um comando de menu estático, que é um comando sempre tenha a mesma forma e no mesmo menu, o comando create usando <xref:System.ComponentModel.Design.MenuCommand>conforme mostrado nos exemplos na seção anterior.</xref:System.ComponentModel.Design.MenuCommand> Para criar um comando estático, você deve fornecer um manipulador de eventos que é responsável pela execução do comando. Como o comando está sempre visível e habilitado, você não precisa fornecer seu status para o Visual Studio. Se você quiser alterar o status de um comando dependendo de certas condições, você pode criar o comando como uma instância do <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>de classe e, em seu construtor, forneça um manipulador de eventos para executar o comando e um manipulador de consultar o status para notificar o Visual Studio quando muda o status do comando.</xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Você também pode implementar <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>como parte de uma classe de comando ou, você pode implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>se você estiver fornecendo um comando como parte de um projeto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> As duas interfaces e o <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>classe todos têm métodos que notificam o Visual Studio de uma alteração no status de um comando e outros métodos que permitem a execução do comando.</xref:Microsoft.VisualStudio.Shell.OleMenuCommand>  
  
 Quando um comando é adicionado ao serviço de comando, ele se torna um de uma cadeia de comandos. Quando você implementa os métodos de notificação e a execução de status para o comando, tome cuidado para fornecer somente para esse comando específico e passar todos os outros casos para os outros comandos da cadeia. Se você não passar o comando (geralmente retornando <xref:Microsoft.VisualStudio.OLE.Interop.Constants>), o Visual Studio pode parar de funcionar corretamente.</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
## <a name="query-status-methods"></a>Métodos de Status de consulta  
 Se você estiver implementando um o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>método ou o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>método, verificar se o GUID do comando conjunto ao qual pertence o comando e a ID do comando.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Siga estas diretrizes:  
  
-   Se o GUID não for reconhecido, sua implementação de qualquer método deverá retornar <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
-   Se sua implementação de qualquer método reconhece o GUID, mas na verdade não implementou o comando, o método deve retornar <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
-   Se sua implementação de qualquer método reconhece o GUID e o comando, o método deve definir o campo de sinalizadores de comando de cada comando (no `prgCmds` parâmetro) usando os sinalizadores a seguir:  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Se o comando é aceito.</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Se o comando não estará visível.</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Se o comando é ativado e parece ter sido verificado.</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Se o comando é habilitado.</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Se o comando deve ser ocultado se ela aparecer em um menu de atalho.</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Se o comando for um controlador de menu e não está habilitado, mas sua lista do menu suspenso não está vazia e ainda está disponível.</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> (Esse sinalizador é raramente usado.)  
  
-   Se o comando foi definido no arquivo. VSCT com o `TextChanges` sinalizador, defina os seguintes parâmetros:  
  
    -   Definir o `rgwz` elemento o `pCmdText` parâmetro para o novo texto do comando.  
  
    -   Definir o `cwActual` elemento o `pCmdText` parâmetro para o tamanho da cadeia de caracteres de comando.  
  
 Certifique-se de que o contexto atual não é uma função de automação, também, a menos que o comando é projetado especificamente para lidar com funções de automação.  
  
 Para indicar que há suporte para um comando específico, retorne <xref:Microsoft.VisualStudio.VSConstants.S_OK>.</xref:Microsoft.VisualStudio.VSConstants.S_OK> Para outros comandos, retorne <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
 No exemplo a seguir, o método de consulta status primeiro garante que o contexto não é uma função de automação, localiza o GUID correto do conjunto de comandos e a ID de comando. O próprio comando é definido para ser habilitado e suporte. Não há suporte para nenhum outro comando.  
  
```  
public int QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.VSStd2K && cCmds > 0)  
        {  
            // make the Right command visible   
            if ((uint)prgCmds[0].cmdID == (uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                prgCmds[0].cmdf = (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_ENABLED | (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_SUPPORTED;  
                return VSConstants.S_OK;  
            }  
        }  
        return Constants.OLECMDERR_E_NOTSUPPORTED;  
    }  
}  
  
```  
  
## <a name="execution-methods"></a>Métodos de execução  
 Implementação do método execute é semelhante a implementação do método status de consulta. Primeiro, certifique-se de que o contexto não é uma função de automação. Testar o GUID e a ID do comando. Se o GUID ou o comando ID não for reconhecido, retorne <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
 Para lidar com o comando, executá-lo e retornar <xref:Microsoft.VisualStudio.VSConstants.S_OK>se a execução for bem-sucedida.</xref:Microsoft.VisualStudio.VSConstants.S_OK> O comando é responsável pela detecção de erro e notificação; Portanto, retorne um código de erro se a execução falhará. O exemplo a seguir demonstra como o método de execução deve ser implementado.  
  
```  
public int Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.GUID_VSStandardCommandSet97)  
        {  
             if (nCmdID ==(uint) uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                //execute the command  
                return VSConstants.S_OK;  
            }  
        }  
    }  
    return Constants.OLECMDERR_E_NOTSUPPORTED;  
}  
  
```  
  
## <a name="see-also"></a>Consulte também  
 [Como os VSPackages adicionar elementos de Interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
