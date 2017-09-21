---
title: Inscrever-se em um evento | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
caps.latest.revision: 35
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
ms.openlocfilehash: 6bd1dd320ad5366ef494a8db958614d837529320
ms.lasthandoff: 02/22/2017

---
# <a name="subscribing-to-an-event"></a>Inscrever-se em um evento
Este passo a passo explica como criar uma janela de ferramenta que responde a eventos em uma tabela de documento (RDT) em execução. Uma janela de ferramentas hospeda um controle de usuário que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> O <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>método conecta-se a interface para os eventos.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instale o SDK do Visual Studio no Centro de download. Ele é fornecido como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="subscribing-to-rdt-events"></a>Assinando eventos RDT  
  
#### <a name="to-create-an-extension-with-a-tool-window"></a>Para criar uma extensão com uma janela de ferramentas  
  
1.  Crie um projeto chamado **RDTExplorer** usando o modelo do VSIX e adicione um modelo de item da janela de ferramenta personalizada denominado **RDTExplorerWindow**.  
  
     Para obter mais informações sobre como criar uma extensão com uma janela da ferramenta, consulte [criando uma extensão com uma janela da ferramenta](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
#### <a name="to-subscribe-to-rdt-events"></a>Para assinar eventos RDT  
  
1.  Abra o arquivo RDTExplorerWindowControl.xaml e excluir o botão denominado `button1`. Adicione um <xref:System.Windows.Forms.ListBox>controlar e aceite o nome padrão.</xref:System.Windows.Forms.ListBox> O elemento de grade deve ter esta aparência:  
  
    ```xml  
    <Grid>  
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">  
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>  
            <ListBox x:Name="listBox" Height="100" />  
        </StackPanel>  
    </Grid>  
    ```  
  
2.  Abra o arquivo RDTExplorerWindow.cs no modo de exibição de código. Adicione as seguintes instruções using ao início do arquivo.  
  
    ```c#  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  Modificar o `RDTExplorerWindow` classe isso que, além de derivar da <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>classe implementa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> </xref:Microsoft.VisualStudio.Shell.ToolWindowPane>  
  
    ```c#  
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents  
    {. . .}  
    ```  
  
4.  Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>  
  
    -   Implemente a interface. Coloque o cursor no nome IVsRunningDocTableEvents. Você deve ver uma lâmpada na margem esquerda. Clique na seta para baixo à direita da lâmpada e selecione **implementar interface**.  
  
5.  Cada método na interface, substitua a linha `throw new NotImplementedException();` com isso:  
  
    ```c#  
    return VSConstants.S_OK;  
    ```  
  
6.  Adicione um campo de cookie para a classe RDTExplorerWindow.  
  
    ```c#  
    private uint rdtCookie;   
    ```  
  
     Isso mantém o cookie é retornado pelo <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>  
  
7.  Substitua método Initialize () do RDTExplorerWindow se registrar para eventos RDT. Você sempre deve obter serviços no método Initialize () do ToolWindowPane, não no construtor.  
  
    ```c#  
    protected override void Initialize()  
    {  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
        this.GetService(typeof(SVsRunningDocumentTable));  
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);  
    }  
    ```  
  
     O <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>serviço é chamado para obter um <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> </xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> O <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>método conecta eventos RDT para um objeto que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>, nesse caso, um objeto RDTExplorer.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> </xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>  
  
8.  Atualização do RDTExplorerWindow Dispose ().  
  
    ```c#  
    protected override void Dispose(bool disposing)  
    {  
        // Release the RDT cookie.  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
            Package.GetGlobalService(typeof(SVsRunningDocumentTable));  
        rdt.UnadviseRunningDocTableEvents(rdtCookie);  
  
        base.Dispose(disposing);  
    }  
    ```  
  
     O <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A>método exclui a conexão entre `RDTExplorer` e notificação de evento RDT.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A>  
  
9. Adicione a seguinte linha ao corpo do <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A>manipulador, antes de `return` instrução.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A>  
  
    ```c#  
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
10. Adicione uma linha semelhante ao corpo do <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A>manipulador e outros eventos que você deseja ver na caixa de listagem.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A>  
  
    ```c#  
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
11. Compile o projeto e iniciar a depuração. A instância experimental do Visual Studio é exibida.  
  
12. Abra o **RDTExplorerWindow** (**exibição / outras janelas / RDTExplorerWindow**).  
  
     O **RDTExplorerWindow** janela é aberta com uma lista de eventos vazio.  
  
13. Abra ou crie uma solução.  
  
     Como `OnBeforeLastDocument` e `OnAfterFirstDocument` os eventos são disparados, notificação de cada evento é exibido no evento lista.
