---
title: "Prepara&#231;&#227;o de depura&#231;&#227;o: aplicativos Web ASP.NET | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "depurando [Visual Studio], aplicativos da Web"
  - "depurando aplicativos Web ASP.NET"
ms.assetid: bcfb1080-98d1-42f9-96af-186fb14f232a
caps.latest.revision: 35
caps.handback.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Prepara&#231;&#227;o de depura&#231;&#227;o: aplicativos Web ASP.NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O modelo de site do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]cria um aplicativo de Web Form.  Quando você cria um site usando esse modelo, o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cria as configurações padrão para depuração.  Na caixa de diálogo **Propriedades do Projeto**, você pode especificar se deseja que a página da Web seja uma página de inicialização.  Quando você inicia a depuração de um site do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]com essas configurações padrão, o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] inicia o Internet Explorer e anexa o depurador ao processo de trabalho do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] \(aspnet\_wp.exe ou w3wp.exe\).  Para obter mais informações, consulte [Requisitos do sistema](../debugger/aspnet-debugging-system-requirements.md).  
  
### Para criar um aplicativo de Web Forms  
  
1.  No menu **Arquivo**, escolha **Novo Site**.  
  
2.  Na caixa de diálogo **Novo Site**, selecione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]**Site**.  
  
3.  Clique em **OK**.  
  
### Para depurar seu Web form  
  
1.  Defina um ou mais pontos de interrupção em suas funções e manipuladores de eventos.  
  
     Para obter mais informações, consulte [Breakpoints and Tracepoints](http://msdn.microsoft.com/pt-br/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2.  Quando um ponto de interrupção é atingido, insira o código na função.  Observe a execução do código até isolar o problema.  
  
     Para obter mais informações, consulte [Stepping](http://msdn.microsoft.com/pt-br/8791dac9-64d1-4bb9-b59e-8d59af1833f9) e [Depurando aplicativos Web e script](../debugger/debugging-web-applications-and-script.md).  
  
## Alterar Configurações padrão  
 Se você quiser alterar a depuração padrão e liberar as configurações criadas pelo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], poderá fazer isso.  Para obter mais informações, consulte [Como definir configurações de depuração e versão](../debugger/how-to-set-debug-and-release-configurations.md).  
  
#### Para alterar a configuração de depuração padrão  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito no site e selecione **Páginas de Propriedades** para abrir a caixa de diálogo **Páginas de Propriedades**.  
  
2.  Clique em **Opções de Inicialização**.  
  
3.  Defina **Iniciar Ação** para a página da Web que deve ser exibida primeiro.  
  
4.  Em **Depuradores**, verifique se **Depuração de ASP.NET** está selecionado.  
  
     Para obter mais informações, consulte [Configurações das páginas de propriedade para projetos Web](../debugger/property-pages-settings-for-web-projects.md).  
  
## Consulte também  
 [Configurações de depuração e preparação](../debugger/debugger-settings-and-preparation.md)   
 [Noções básicas do depurador](../debugger/debugger-basics.md)   
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Depurando código gerenciado](../debugger/debugging-managed-code.md)