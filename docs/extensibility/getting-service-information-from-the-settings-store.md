---
title: "Obtendo informações do serviço de armazenamento de configurações | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
caps.latest.revision: 4
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
ms.openlocfilehash: 4c55481058fea4bf5407e803d19ad2b9ad2fffee
ms.lasthandoff: 02/22/2017

---
# <a name="getting-service-information-from-the-settings-store"></a>Obtendo informações do serviço de armazenamento de configurações
Você pode usar o armazenamento de configurações para localizar todos os serviços disponíveis ou para determinar se um determinado serviço está instalado. Você deve saber o tipo da classe de serviço.  
  
### <a name="to-list-the-available-services"></a>Para listar os serviços disponíveis  
  
1.  Criar um projeto do VSIX denominado FindServicesExtension e, em seguida, adicione um comando personalizado denominado FindServicesCommand. Para obter mais informações sobre como criar um comando personalizado, consulte [criando uma extensão com um comando de Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  FindServicesCommand.cs, adicione as seguintes instruções using:  
  
    ```vb  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
3.  Obtenha o armazenamento de definições de configuração, em seguida, localize a subcoleção denominada serviços. Esta coleção inclui todos os serviços disponíveis. No método MenuItemCommand, remova o código existente e substitua-o pelo seguinte:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        string message = "Available services:\n";  
        IEnumerable<string> collection = configurationSettingsStore.GetSubCollectionNames("Services");  
        int n = 0;  
        foreach (string service in collection)  
        {  
            message += configurationSettingsStore.GetString("Services\\" + service, "Name", "Unknown") + "\n";  
        }  
  
        MessageBox.Show(message);  
    }  
    ```  
  
4.  Compile o projeto e iniciar a depuração. A instância experimental aparece.  
  
5.  Na instância experimental, sobre o **ferramentas** menu, clique em **FindServicesCommand invocar**.  
  
     Você deve ver uma caixa de mensagem listando todos os serviços.  
  
     Para verificar essas configurações, você pode usar o editor do registro.  
  
## <a name="finding-a-specific-service"></a>Localizando um serviço específico  
 Você também pode usar o <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A>método para determinar se um determinado serviço está instalado.</xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> Você deve saber o tipo da classe de serviço.  
  
1.  Na MenuItemCallback de projeto que você criou no procedimento anterior, pesquise o armazenamento de definições de configuração para o `Services` coleção que possui a subcoleção chamada pelo GUID do serviço. Nesse caso, irá procurar o serviço de Ajuda.  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        string helpServiceGUID = typeof(SVsHelpService).GUID.ToString("B").ToUpper();  
        bool hasHelpService = configurationSettingsStore.CollectionExists("Services\\" + helpServiceGUID);  
        string message = "Help Service Available: " + hasHelpService;  
  
        MessageBox.Show(message);  
    }  
    ```  
  
2.  Compile o projeto e iniciar a depuração.  
  
3.  Na instância experimental, sobre o **ferramentas** menu, clique em **FindServicesCommand invocar**.  
  
     Você verá uma mensagem com o texto **ajuda disponível do serviço:** seguido por **True** ou **False**. Para verificar essa configuração, você pode usar um editor de registro, conforme mostrado nas etapas anteriores.
