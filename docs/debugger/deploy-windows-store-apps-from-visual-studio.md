---
title: "Implantar aplicativos da Windows Store pelo Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: ef3a0f36-bfc9-4ca0-aa61-18261f619bff
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Implantar aplicativos da Windows Store pelo Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Applies to Windows only](../debugger/media/windows_only_content.png "windows\_only\_content")  
  
 A funcionalidade de implantação do Visual Studio compila e registra aplicativos na Windows Store que são criados com o Visual Studio em um dispositivo de destino. Exatamente como o aplicativo é registrado depende de o dispositivo de destino ser local ou remoto:  
  
-   Quando o destino é o computador local com o Visual Studio, ele registra o aplicativo de sua pasta de compilação.  
  
-   Quando o destino é um dispositivo remoto, o Visual Studio copia os arquivos necessários ao computador remoto e registra o aplicativo nesse dispositivo.  
  
 A implantação é automática quando você depurar seu aplicativo do Visual Studio usando o **Iniciar depuração** opção \(teclado: F5\) ou o **Start Without Debugging** opção \(teclado: CTRL \+ F5\). Você também pode implantar seu aplicativo manualmente. A implantação manual é útil nos seguintes cenários:  
  
-   Teste ad\-hoc em um computador local ou remoto.  
  
-   Implantação de um aplicativo que iniciará outro aplicativo que você quer depurar.  
  
-   Implantação de um aplicativo que será depurado quando é iniciado por outro aplicativo ou método.  
  
##  <a name="BKMK_In_this_topic"></a> Neste tópico  
 Neste tópico, você pode aprender:  
  
 [Como implantar um aplicativo da Windows Store](#BKMK_How_to_deploy_a_Windows_Store_app)  
  
 [Como especificar um dispositivo remoto](#BKMK_How_to_specify_a_remote_device)  
  
 [Opções de implantação](#BKMK_Deployment_options)  
  
##  <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> Como implantar um aplicativo da Windows Store  
 Implantar manualmente um aplicativo é simples:  
  
1.  Se você está implantando para um dispositivo remoto, especifique o nome ou o endereço IP do dispositivo na página de propriedade do projeto de inicialização do aplicativo. \(As etapas para fazer isso são listadas a seguir neste tópico.\)  
  
2.  Na barra de ferramentas do depurador do Visual Studio, escolha o destino da implantação da lista suspensa ao lado do botão **Iniciar Depuração**.  
  
     ![Executado na máquina Local](~/docs/debugger/media/vsrun_f5_local.png "VSRUN\_F5\_Local")  
  
3.  No menu **Compilar**, escolha **Implantar**  
  
##  <a name="BKMK_How_to_specify_a_remote_device"></a> Como especificar um dispositivo remoto  
 **Pré\-requisitos**  
  
 Para implantar um aplicativo em um dispositivo remoto:  
  
-   Uma licença de desenvolvedor deve estar instalada no dispositivo remoto.  
  
-   As Ferramentas Remotas do Visual Studio devem estar instaladas no dispositivo remoto e o Monitor de Depuração Remota deve estar em execução.  
  
     A implantação usa o canal de rede do depurador remoto para enviar os arquivos do aplicativo ao dispositivo remoto.  
  
#### Para especificar um dispositivo remoto  
  
1.  Na página de propriedade de depuração do projeto de inicialização, especifique o nome ou o endereço IP de um destino de implantação remoto.  
  
2.  Para abrir a página de propriedade de depuração, escolha o projeto no Gerenciador de Soluções e **Propriedades** no menu de atalho.  
  
3.  Em seguida, escolha o nó **Depurar** na janela de páginas de propriedade.  
  
4.  Você pode digitar o nome ou o endereço IP do dispositivo remoto ou escolhê\-lo na caixa de diálogo **Selecionar Conexão de Depurador Remoto**.  
  
     ![Marque a caixa de diálogo conexão de depurador remoto](~/docs/debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN\_SelectRemoteDebuggerDlg")  
  
     A caixa de diálogo **Selecionar Conexão de Depurador Remoto** exibe os dispositivos na sub\-rede local e qualquer dispositivo que está diretamente conectado ao computador com o Visual Studio por um cabo Ethernet.  
  
 **Como especificar o dispositivo remoto na página de projetos em JavaScript ou Visual C\+\+**  
  
 ![Propriedades do projeto C&#43;&#43; para depuração remota](~/docs/debugger/media/vsrun_cpp_projprop_remote.png "VSRUN\_CPP\_ProjProp\_Remote")  
  
1.  Escolha **Depurador Remoto** na lista **Depurador a iniciar**.  
  
2.  Digite o nome da rede do dispositivo remoto na caixa **Nome do Computador**. Ou então, você pode escolher a seta para baixo na caixa para selecionar o dispositivo da caixa de diálogo Selecionar Conexão de Depurador Remoto.  
  
 **Como especificar o dispositivo remoto na página de projetos em Visual C\# e Visual Basic**  
  
 ![Gerenciado de propriedades do projeto para depuração remota](~/docs/debugger/media/vsrun_managed_projprop_remote.png "VSRUN\_Managed\_ProjProp\_Remote")  
  
1.  Escolha **Computador Remoto** na lista **Dispositivo de Destino**.  
  
2.  Digite o nome de rede do dispositivo remoto na caixa **Computador Remoto** ou clique em **Localizar** para escolher o dispositivo na caixa de diálogo **Selecionar Conexão de Depurador Remoto**.  
  
##  <a name="BKMK_Deployment_options"></a> Opções de implantação  
 Você pode definir as opções de implantação a seguir na página de propriedade de depuração do projeto de inicialização.  
  
 **Permitir Loopback de Rede**  
 Por motivos de segurança, um aplicativo [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] instalado de maneira padrão não pode efetuar chamadas de rede para o dispositivo em que está instalado. Por padrão, a implantação do Visual Studio cria uma isenção dessa regra para o aplicativo implantado. Essa isenção permite que você teste procedimentos de comunicação em um único computador. Antes de enviar seu aplicativo para [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)], você deve testá\-lo sem a isenção.  
  
 Para remover a isenção de loopback de rede do aplicativo:  
  
-   Na página de propriedade de depuração C\# e VB, desmarque a caixa de seleção **Permitir Loopback de Rede**.  
  
-   Na página de propriedade de JavaScript e depuração, defina o valor de **Permitir Loopback de Rede** para **Não**.  
  
 **Não iniciar, mas depurar meu código quando ele iniciar \(C\# e VB\)\/Iniciar Aplicativo \(JavaScript e C\+\+\)**  
 Para configurar a implantação para iniciar automaticamente uma sessão de depuração quando o aplicativo é iniciado:  
  
-   Na página de propriedade de depuração C\# e VB, marque a caixa de seleção **Não iniciar, mas sim depurar meu código quando iniciar**.  
  
-   Na página de propriedade de JavaScript e depuração, defina o valor de **Iniciar Aplicativo** para **Sim**.  
  
## Consulte também  
 [Executar aplicativos pelo Visual Studio](../debugger/run-store-apps-from-visual-studio.md)