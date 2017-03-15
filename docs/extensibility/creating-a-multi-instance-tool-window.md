---
title: "Criando uma janela da ferramenta várias instâncias | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
caps.latest.revision: 12
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
ms.openlocfilehash: 12ecde3d4bc9803638798db908192effb3c1ba99
ms.lasthandoff: 02/22/2017

---
# <a name="creating-a-multi-instance-tool-window"></a>Criando uma janela de ferramentas de várias instâncias
Você pode programar uma janela da ferramenta para que várias instâncias dele podem ser abertas simultaneamente. Por padrão, janelas de ferramenta podem ter apenas uma instância abertos.  
  
 Quando você usa uma janela de ferramentas de várias instâncias, você pode mostrar várias fontes relacionadas de informações ao mesmo tempo. Por exemplo, você pode colocar uma multilinhas <xref:System.Windows.Forms.TextBox>controle em uma janela de ferramenta várias instâncias para que vários trechos de código estão disponíveis simultaneamente durante uma sessão de programação.</xref:System.Windows.Forms.TextBox> Também, por exemplo, você pode colocar um <xref:System.Windows.Forms.DataGrid>controle e uma lista suspensa caixa em uma janela de ferramenta várias instâncias para que várias fontes de dados em tempo real podem ser rastreadas simultaneamente.</xref:System.Windows.Forms.DataGrid>  
  
## <a name="creating-a-basic-single-instance-tool-window"></a>Criando uma janela da ferramenta Basic (instância única)  
  
1.  Crie um projeto chamado **MultiInstanceToolWindow** usando o modelo do VSIX e adicione um modelo de item da janela de ferramenta personalizada denominado **MIToolWindow**.  
  
    > [!NOTE]
    >  Para obter mais informações sobre como criar uma extensão com uma janela da ferramenta, consulte [criando uma extensão com uma janela da ferramenta](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="making-a-tool-window-multi-instance"></a>Fazendo uma instância múltipla de janela de ferramenta  
  
1.  Abra o **MIToolWindowPackage.cs** de arquivo e localize o `ProvideToolWindow` atributo. e o `MultiInstances=true` parâmetro, conforme mostrado no exemplo a seguir.  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
        [ProvideMenuResource("Menus.ctmenu", 1)]  
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]  
        [Guid(MIToolWindowPackageGuids.PackageGuidString)]  
        public sealed class MIToolWindowPackage : Package  
    {. . .}  
    ```  
  
2.  No arquivo MIToolWindowCommand.cs, localize o método ShowToolWindos(). Nesse método, chamar o <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>método e defina seu `create` sinalizador como `false` para que ele irá iterar instâncias existentes de janela de ferramenta até uma disponível `id` for encontrado.</xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>  
  
3.  Para criar uma instância da ferramenta, chame o <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>método e defina seu `id` para um valor disponível e seu `create` sinalizador como `true`.</xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>  
  
     Por padrão, o valor da `id` parâmetro o <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>método é `0`.</xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> Isso faz com que uma janela da ferramenta de instância única. Para mais de uma instância seja hospedado, cada instância deve ter seu próprio exclusivo `id`.  
  
4.  Chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>objeto que é retornado pelo <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A>propriedade da instância de janela de ferramenta.</xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> </xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>  
  
5.  Por padrão, o `ShowToolWindow` método criado pelo modelo de item da janela de ferramenta cria uma janela da ferramenta de instância única. O exemplo a seguir mostra como modificar o `ShowToolWindow` método para criar várias instâncias.  
  
    ```c#  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        for (int i = 0; i < 10; i++)  
        {  
            ToolWindowPane window = this.package.FindToolWindow(typeof(MIToolWindow), i, false);  
            if (window == null)  
            {  
                // Create the window with the first free ID.   
                window = (ToolWindowPane)this.package.FindToolWindow(typeof(MIToolWindow), i, true);  
                if ((null == window) || (null == window.Frame))  
                {  
                    throw new NotSupportedException("Cannot create tool window");  
                }  
  
            IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
            break;  
            }  
        }  
    }  
    ```
