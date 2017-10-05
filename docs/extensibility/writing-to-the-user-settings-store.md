---
title: "Gravar no repositório de configurações do usuário | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
caps.latest.revision: 3
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
ms.openlocfilehash: 8be43438312773b2e02915f963b1c68fff61e889
ms.contentlocale: pt-br
ms.lasthandoff: 09/26/2017

---
# <a name="writing-to-the-user-settings-store"></a>Gravar no repositório de configurações do usuário
Configurações de usuário são graváveis como os de **Ferramentas / opções** caixa de diálogo, janelas Propriedades e outras caixas de diálogo determinados. Extensões do Visual Studio podem usá-los para armazenar pequenas quantidades de dados. Este passo a passo mostra como adicionar o bloco de notas para o Visual Studio como uma ferramenta externa, leitura e gravação para o repositório de configurações do usuário.  
  
### <a name="backing-up-your-user-settings"></a>Fazendo backup das configurações de usuário do  
  
1.  Você deve ser capaz de redefinir as configurações de ferramentas externas para que você possa depurar e repita o procedimento. Para fazer isso, você deve salvar as configurações originais para que você possa restaurá-las conforme necessário.  
  
2.  Abra o Regedit.exe.  
  
3.  Navegue até HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External ferramentas\\.  
  
    > [!NOTE]
    >  Certifique-se de que você está vendo a chave que contém \14.0Exp\ e não \14.0\\. Quando você executa a instância experimental do Visual Studio, as configurações do usuário são no hive do Registro "14.0Exp".  
  
4.  Com o botão direito na subchave \External Tools\ e, em seguida, clique em **exportar**. Verifique se **ramificação selecionada** está selecionado.  
  
5.  Salve o arquivo externo Tools.reg resultante.  
  
6.  Posteriormente, quando você deseja redefinir as configurações de ferramentas externas, selecione a chave de registro HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External Tools\ e clique em **excluir** no menu de contexto.  
  
7.  Quando o **Confirmar exclusão da chave** caixa de diálogo for exibida, clique em **Sim**.  
  
8.  O arquivo Tools.reg externa que você salvou anteriormente, clique **abrir com**e, em seguida, clique em **Editor do registro**.  
  
## <a name="writing-to-the-user-settings-store"></a>Gravar no repositório de configurações do usuário  
  
1.  Crie um projeto do VSIX denominado UserSettingsStoreExtension e, em seguida, adicionar um comando personalizado chamado UserSettingsStoreCommand. Para obter mais informações sobre como criar um comando personalizado, consulte [criando uma extensão com um comando de Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  Em UserSettingsStoreCommand.cs, adicione o seguinte usando instruções:  
  
    ```csharp  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    ```  
  
3.  Em MenuItemCallback, exclua o corpo do método e obter o usuário do repositório de configurações, da seguinte maneira:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
    }  
    ```  
  
4.  Agora, descubra se o bloco de notas já está definido como uma ferramenta externa. Você precisa percorrer todas as ferramentas externas para determinar se a configuração ToolCmd é "Notepad", da seguinte maneira:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
  
        // Find out whether Notepad is already an External Tool.  
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");  
        bool hasNotepad = false;  
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;  
        for (int i = 0; i < toolCount; i++)  
        {  
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)  
            {  
                hasNotepad = true;  
                break;  
            }  
        }  
    }  
  
    ```  
  
5.  Se o bloco de notas não foi definido como uma ferramenta externa, defina-o da seguinte maneira:  
  
    ```vb  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
  
        // Find out whether Notepad is already installed.  
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");  
        bool hasNotepad = false;  
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;  
        for (int i = 0; i < toolCount; i++)  
        {  
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)  
            {  
                hasNotepad = true;  
                break;  
            }  
        }  
  
        string message = (hasNotepad) ? "Notepad already installed" : "Installing Notepad";  
         if (!hasNotepad)  
        {  
            userSettingsStore.SetString("External Tools", "ToolTitle" + toolCount, "&Notepad");  
            userSettingsStore.SetString("External Tools", "ToolCmd" + toolCount, "C:\\Windows\\notepad.exe");  
            userSettingsStore.SetString("External Tools", "ToolArg" + toolCount, "");  
            userSettingsStore.SetString("External Tools", "ToolDir" + toolCount, "$(ProjectDir)");  
            userSettingsStore.SetString("External Tools", "ToolSourceKey" + toolCount, "");  
            userSettingsStore.SetUInt32("External Tools", "ToolOpt" + toolCount, 0x00000011);  
  
            userSettingsStore.SetInt32("External Tools", "ToolNumKeys", toolCount + 1);  
        }  
    }  
    ```  
  
6.  Teste o código. Lembre-se de que ele adiciona o bloco de notas como uma ferramenta externa, portanto você deve reverter o registro antes de executá-lo uma segunda vez.  
  
7.  Compile o código e iniciar a depuração.  
  
8.  Sobre o **ferramentas** menu, clique em **UserSettingsStoreCommand invocar**. Isso adicionará o bloco de notas para o **ferramentas** menu.  
  
9. Agora você deve ver o bloco de notas no menu Ferramentas / opções de menu e clicando em **o bloco de notas** deve abrir uma instância do bloco de notas.
