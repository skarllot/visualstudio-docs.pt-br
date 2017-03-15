---
title: "Prepara&#231;&#227;o de depura&#231;&#227;o: tipos de projeto Visual C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "C++"
helpviewer_keywords: 
  - "depurar compilações, configurações de projeto"
  - "depurando [C++]"
  - "modelos de projeto, depuração"
  - "Projetos Visual C++, depuração"
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Prepara&#231;&#227;o de depura&#231;&#227;o: tipos de projeto Visual C++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta seção descreve como depurar os tipos de projeto básicos criados pelos modelos de projeto do [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)].  
  
 Observe que esses tipos de projeto que criam DLL como suas saídas foram agrupadas em [Depurando projetos de DLL](../debugger/debugging-dll-projects.md) devido aos recursos comuns eles compartilham.  
  
##  <a name="BKMK_In_this_topic"></a> Neste tópico  
 [Configurações de propriedade recomendadas](#BKMK_Recommended_Property_Settings)  
  
 [Projetos Win32](#BKMK_Win32_Projects)  
  
-   [Para depurar um aplicativo Win32 C ou C++](#BKMK_To_debug_a_C_or_C___Win32_application)  
  
-   [Para definir manualmente uma configuração de depuração](#BKMK_To_manually_set_a_Debug_configuration)  
  
 [Aplicativos do Windows Forms (.NET)](#BKMK_Windows_Forms_Applications___NET_)  
  
##  <a name="BKMK_Recommended_Property_Settings"></a> Configurações de propriedade recomendadas  
 Certas propriedades devem ser definidas da mesma maneira para todos os cenários não gerenciados de depuração.  As tabelas a seguir exibem as configurações de propriedade recomendadas.  As configurações não listadas aqui podem variar entre os tipos de projeto não gerenciados diferentes.  Para obter mais informações, consulte [Definições do projeto para uma configuração de depuração do C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md)  
  
### Propriedades de configuração &#124; C\/C\+\+ &#124; Nó de otimização  
  
|Nome da propriedade|Configuração|  
|-------------------------|------------------|  
|**Otimização**|Definido como **Desabilitado \(\/0d\).** O código otimizado é mais difícil de depurar porque as instruções geradas não correspondem diretamente ao código\-fonte.  Se você descobrir que seu programa tem um bug que aparece apenas em código otimizado, poderá ativar essa configuração, mas lembre\-se de que o código mostrado na janela **Desmontagem** é gerado de origem otimizada que pode não corresponder ao que é visto em suas janelas de origem.  Outros recursos, como depuração, podem não se comportar como esperado.|  
  
### Propriedades de configuração &#124; Vinculador &#124; Nó de depuração  
  
|Nome da propriedade|Configuração|  
|-------------------------|------------------|  
|**Gerar informações sobre depuração**|Você sempre deve definir essa opção como **Sim \(\/DEBUG\)** para criar os símbolos e os arquivos de depuração necessários para depurar.  Quando o aplicativo entra em produção, você pode defini\-lo como desativado.|  
  
 [Neste tópico](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Win32_Projects"></a> Projetos Win32  
 Os aplicativos Win32 são programas do Windows tradicionais escritos em C ou C\+\+.  Depurar esse tipo de aplicativo no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] é simples.  
  
 Os aplicativos Win32 incluem aplicativos do MFC e projetos do ATL.  Eles usam APIs do Windows e podem usar MFC ou ATL, mas não usam Common Language Runtime \(CLR\).  Podem, no entanto, chamar código gerenciado que usa o CLR.  
  
 O procedimento a seguir explica como depurar um projeto do Win32 de dentro do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Outro modo de depurar um aplicativo Win32 é iniciar o aplicativo fora do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e anexar a ele.  Para obter mais informações, consulte [Anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
###  <a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> Para depurar um aplicativo Win32 C ou C\+\+  
  
1.  Abra o projeto no Visual Studio.  
  
2.  No menu **Depurar**, escolha **Iniciar**.  
  
3.  Depure usando as técnicas discutidas em [Noções básicas do depurador](../debugger/debugger-basics.md).  
  
###  <a name="BKMK_To_manually_set_a_Debug_configuration"></a> Para definir manualmente uma configuração de depuração  
  
1.  No menu **Exibir**, clique em **Páginas de Propriedades**.  
  
2.  Clique no nó **Propriedades de Configuração** para abri\-la se já não estiver aberto  
  
3.  Selecione **Geral** e defina o valor da linha **Saída** para **Depurar**.  
  
4.  Abra o nó **C\/C\+\+** e selecione **Geral**.  
  
     Na linha **Depurar** você especifica o tipo de informações de depuração a serem geradas pelo compilador.  Os valores que você pode escolher incluem **Banco de dados do programa \(\/Zi\)** ou **Banco de dados do programa para edição & Continuar \(\/ZI\)**.  
  
5.  Selecione **Otimização** e, na linha **Otimização**, selecione **Desabilitado \(\/\) 0d** na lista suspensa.  
  
     O código otimizado é mais difícil de depurar porque as instruções geradas não correspondem diretamente ao código\-fonte.  Se você descobrir que seu programa tem um bug que aparece apenas em código otimizado, poderá ativar essa configuração, mas lembre\-se de que o código mostrado na janela Desmontagem é gerado de origem otimizada que pode não corresponder ao que é visto em suas janelas de origem.  Os recursos como o depuração provavelmente mostram incorretamente pontos de interrupção e ponto de execução.  
  
6.  Abra o nó **Vinculador** e selecione **Depurando**.  Na primeira linha **Gerar**, selecione **Sim \(\/DEBUG\)** na lista suspensa.  Sempre defina isso quando você estiver depurando.  
  
 Para obter mais informações, consulte[Definições do projeto para uma configuração de depuração do C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
 [Neste tópico](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Windows_Forms_Applications___NET_"></a> Aplicativos do Windows Forms \(.NET\)  
 O modelo **Aplicativos do Windows Forms \(.NET\)** cria um aplicativo do Windows Forms do [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)].  Para obter mais informações, consulte [How to: Create a Windows Application Project](http://msdn.microsoft.com/pt-br/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Depurar esse tipo de aplicativo no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] é semelhante a depurar em aplicativos gerenciados do Windows Forms.  
  
 Quando você cria um projeto do Windows Forms com o modelo de projeto, o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cria automaticamente as configurações necessárias para as configurações de depuração e versão.  Se for necessário, você poderá alterar essas configurações na caixa de diálogo **\<nome do projeto\> Páginas de Propriedades**.  Para obter mais informações, consulte [Configurações de depuração e lançamento](../debugger/how-to-set-debug-and-release-configurations.md).  
  
 Para obter mais informações, consulte [Definições do projeto para uma configuração de depuração do C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
 Outro modo de depurar um aplicativo do Windows Forms 2 é iniciar o aplicativo fora do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e anexar a ele.  Para obter mais informações, consulte [Anexar a um programa em execução ou a vários programas](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 [Neste tópico](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
## Consulte também  
 [Noções básicas do depurador](../debugger/debugger-basics.md)   
 [Definições do projeto para uma configuração de depuração do C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Anexando a um programa ou vários programas em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Configurações de depuração e lançamento](../debugger/how-to-set-debug-and-release-configurations.md)   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/pt-br/b2f93fed-c635-4705-8d0e-cf079a264efa)