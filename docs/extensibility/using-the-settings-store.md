---
title: "Usando o armazenamento de configurações | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
caps.latest.revision: 28
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
ms.openlocfilehash: 0654db108c3f0bec3965a702c8f2100ee78407c4
ms.lasthandoff: 02/22/2017

---
# <a name="using-the-settings-store"></a>Usando o armazenamento de configurações
Há dois tipos de repositórios de configurações:  
  
-   Definições de configuração, que são as configurações do Visual Studio e o VSPackage somente leitura. Visual Studio mescla as configurações de todos os arquivos pkgdef conhecidos esse repositório.  
  
-   Configurações de usuário, que são graváveis configurações, como aqueles que são exibidos em páginas de **opções** caixa de diálogo, páginas de propriedade e determinadas outras caixas de diálogo. Extensões do Visual Studio podem usá-los para o armazenamento local de pequenas quantidades de dados.  
  
 Este passo a passo mostra como ler dados do armazenamento de configuração de configuração. Consulte [gravar no armazenamento de configurações do usuário](../extensibility/writing-to-the-user-settings-store.md) para obter uma explicação de como gravar no armazenamento de configurações do usuário.  
  
## <a name="creating-the-example-project"></a>Criando o projeto de exemplo  
 Esta seção mostra como criar um projeto de extensão simples com um comando de menu para demonstração.  
  
1.  Cada extensão do Visual Studio inicia com um projeto de implantação do VSIX que conterá os ativos de extensão. Criar um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projeto VSIX chamado `SettingsStoreExtension`. Você pode encontrar o modelo de projeto do VSIX no **novo projeto** caixa de diálogo em **Visual c# / extensibilidade**.  
  
2.  Agora, adicione um modelo de item de comando personalizada chamado **SettingsStoreCommand**. No **Adicionar Novo Item** caixa de diálogo, vá para **Visual c# / extensibilidade** e selecione **comando personalizado**. No **nome** campo na parte inferior da janela, altere o nome do arquivo de comando para **SettingsStoreCommand.cs**. Para obter mais informações sobre como criar um comando personalizado, consulte [criando uma extensão com um comando de Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
## <a name="using-the-configuration-settings-store"></a>Usando o armazenamento de configurações de configuração  
 Esta seção mostra como detectar e exibir as definições de configuração.  
  
1.  No arquivo SettingsStorageCommand.cs, adicione as seguintes instruções using:  
  
    ```  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
2.  Em `MenuItemCallback`, remova o corpo do método e adicionar essas linhas obtém o armazenamento de configurações de configuração:  
  
    ```  
    SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
    SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
    ```  
  
     O <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager>é uma classe auxiliar gerenciada sobre o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager>service.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> </xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager>  
  
3.  Agora, descubra se as ferramentas do Windows Phone serão instaladas. O código deve ter esta aparência:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools");  
        string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled;  
        MessageBox.Show(message);  
    }  
    ```  
  
4.  Teste o código. Compile o projeto e iniciar a depuração.  
  
5.  Na instância experimental, sobre o **ferramentas** menu, clique em **SettingsStoreCommand invocar**.  
  
     Você deve ver uma caixa de texto **ferramentas de desenvolvedor do Microsoft Windows Phone:** seguido por **True** ou **False**.  
  
 O Visual Studio manterá o repositório de configurações no registro do sistema.  
  
#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Usar um editor de registro para verificar as definições de configuração  
  
1.  Abra Regedit.exe.  
  
2.  Navegue até HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\.  
  
    > [!NOTE]
    >  Certifique-se de que você está vendo a chave que contém \14.0Exp_Config\ e não \14.0_Config\\. Quando você executa a instância experimental do Visual Studio, as configurações estão na seção do Registro "14.0Exp_Config".  
  
3.  Expanda o nó \Installed Products\. Se a mensagem nas etapas anteriores é **instalado de ferramentas de desenvolvedor do Microsoft Windows Phone: True**, então \Installed Products\ deve conter um nó de ferramentas de desenvolvedor do Microsoft Windows Phone. Se a mensagem for **instalado de ferramentas de desenvolvedor do Microsoft Windows Phone: False**, então, \Installed Products\ não deve conter um nó de ferramentas de desenvolvedor do Microsoft Windows Phone.
