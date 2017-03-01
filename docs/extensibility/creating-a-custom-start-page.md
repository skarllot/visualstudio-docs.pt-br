---
title: "Criar um personalizado página inicial | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
caps.latest.revision: 18
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
ms.sourcegitcommit: c358bf79945b4f4eef5b19c60cad0bd866c175b3
ms.openlocfilehash: 2902ac3b5cd4fd038bdaf277a8390d5eb9e96b28
ms.lasthandoff: 02/22/2017

---
# <a name="creating-a-custom-start-page"></a>Criando uma página inicial personalizada
Você pode criar uma página de início personalizados, seguindo as etapas neste documento.  
  
## <a name="creating-a-blank-start-page"></a>Criando uma página em branco inicial  
 Primeiro, fazer uma página em branco Iniciar criando um arquivo. XAML que tem uma estrutura de marca que Visual Studio reconheça. Em seguida, adicione a marcação e code-behind para produzir a aparência e a funcionalidade desejada.  
  
#### <a name="to-create-a-blank-start-page"></a>Para criar uma página em branco inicial  
  
1.  Criar um novo projeto do tipo **aplicativo WPF** (**Visual c# / área de trabalho do Windows**.  
  
2.  Adicione uma referência ao `Microsoft.VisualStudio.Shell.14.0`.  
  
3.  Abra o arquivo XAML no editor de XML e altere o nível superior \<janela > elemento para uma \<UserControl > elemento sem remover qualquer uma das declarações de namespace.  
  
4.  Remover o `x:Class` declaração de elemento de nível superior. Isso torna o conteúdo XAML compatível com a janela de ferramenta do Visual Studio que hospeda a página inicial.  
  
5.  Adicione as seguintes declarações de namespace para o nível superior \<UserControl > elemento.  
  
    ```  
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
    ```  
  
     Esses namespaces permite acessar comandos do Visual Studio, controles e configurações de interface do usuário. Para obter mais informações, consulte [adicionando comandos do Visual Studio para uma página de início](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
     O exemplo a seguir mostra a marcação no arquivo. XAML para uma página de início em branco. Qualquer conteúdo personalizado deve entrar interno <xref:System.Windows.Controls.Grid>elemento.</xref:System.Windows.Controls.Grid>  
  
    ```vb  
    <UserControl  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        xmlns:MyNamespace="clr-namespace:ManualStartPage;assembly=ManualStartPage"  
        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
        xmlns:local="clr-namespace:StartPageHost"  
        mc:Ignorable="d"  
         Height="350" Width="525">  
        <Grid>  
        <!--Add content here.-->  
        </Grid>  
    </UserControl>  
    ```  
  
6.  Adicionar controles ao vazia \<UserControl > elemento para preencher a página de início personalizados. Para obter informações sobre como adicionar funcionalidade específica para o Visual Studio, consulte [adicionando comandos do Visual Studio para uma página de início](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Página inicial do teste e aplicando personalizado  
 Não defina a instância primária do Visual Studio para executar a página de início personalizado até que você verificar que ele não falhe Visual Studio. Em vez disso, teste-o na instância experimental.  
  
#### <a name="to-test-a-manually-created-custom-start-page"></a>Para testar uma página de início personalizados criados manualmente  
  
1.  Copie o arquivo XAML e qualquer texto arquivos de suporte ou marcação arquivos, como o **%USERPROFILE%\My Documents\Visual Studio 2015\StartPages\\ ** pasta.  
  
2.  Se sua página inicial fizer referência a quaisquer controles ou tipos em assemblies que não são instalados pelo Visual Studio, copie os assemblies e colá-los em *pasta de instalação do Visual Studio***\Common7\IDE\PrivateAssemblies\\**.  
  
3.  Em um prompt de comando do Visual Studio, digite **devenv /rootsuffix Exp** para abrir uma instância experimental do Visual Studio.  
  
4.  Na instância experimental, vá para o **Ferramentas / opções / ambiente / inicialização** página e selecione seu arquivo XAML do **Personalizar página inicial** lista suspensa.  
  
5.  Sobre o **exibição** menu, clique em **Start Page**.  
  
     Sua página inicial personalizada deve ser exibida. Se você quiser alterar os arquivos, você deve fechar a instância experimental, faça as alterações, copie e cole os arquivos alterados e, em seguida, abra novamente a instância experimental para exibir as alterações.  
  
#### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Para aplicar a personalizar página inicial na instância principal do Visual Studio  
  
-   Depois de testar a página inicial e determinou que ele seja estável, use o **Personalizar página inicial** opção o **opções** caixa de diálogo para selecioná-la como a página inicial na instância principal do Visual Studio  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Adicionando XAML personalizado para a página inicial](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)   
 [Adicionar o controle de usuário para a página inicial](../extensibility/adding-user-control-to-the-start-page.md)   
 [Adicionando comandos do Visual Studio para uma página inicial](../extensibility/adding-visual-studio-commands-to-a-start-page.md)   
 [Passo a passo: Salvando as configurações do usuário em uma página inicial](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)   
 [Implantação de páginas de início personalizado](../extensibility/deploying-custom-start-pages.md)
