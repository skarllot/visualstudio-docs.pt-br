---
title: "Prepara&#231;&#227;o da depura&#231;&#227;o: aplicativos dos Windows Forms | Microsoft Docs"
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
  - "depurando [C#], Aplicativos do Windows"
  - "depurando [J#], Aplicativos do Windows"
  - "depurando [Visual Basic], Aplicativos do Windows"
  - "depurando [Visual Studio], Aplicativos do Windows"
  - "depurando aplicativos Windows"
  - "Aplicativos do Windows, depuração"
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Prepara&#231;&#227;o da depura&#231;&#227;o: aplicativos dos Windows Forms
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O modelo de projeto do Windows Forms \(.NET\) cria um aplicativo do Windows Forms.  Depurar esse tipo de aplicativo no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] é simples.  Para obter mais informações, consulte [Creating a Windows Application Project](http://msdn.microsoft.com/pt-br/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Quando você cria um projeto do Windows Forms com o modelo de projeto, o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cria automaticamente as configurações necessárias para as configurações de depuração e versão.  Se necessário, você pode alterar essas configurações.  Essas configurações podem ser alteradas na caixa de diálogo **\<nome do projeto\> Páginas de Propriedades** \(**Meu Projeto** no Visual Basic\).  
  
 Para obter mais informações, consulte [Configurações de propriedade recomendadas](../debugger/managed-debugging-recommended-property-settings.md).  
  
 A tabela a seguir exibe uma configuração de propriedade recomendada adicional.  
  
### Propriedades de configuração na guia Depurar  
  
|**Nome da propriedade**|**Configuração**|  
|-----------------------------|----------------------|  
|**Iniciar ação**|-   Definido como **Iniciar projeto** na maioria das vezes.  Definir como **Iniciar programa externo** se quiser iniciar outro executável quando iniciar a depuração \(normalmente para depurar DLL\).|  
  
 Você pode depurar aplicativos do Windows Forms de dentro do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou anexando a um aplicativo já em execução.  Para obter mais informações sobre a anexação, consulte [Anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
### Para depurar um aplicativo C\#, F\# ou Windows Forms do Visual Basic  
  
1.  Abra o projeto no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
2.  Crie pontos de interrupção conforme o necessário.  
  
     Como os aplicativos do Windows Forms são controlados por eventos, seus pontos de interrupção entrarão no código do manipulador de eventos ou nos métodos chamados pelo código do manipulador de eventos.  Eventos comuns nos quais colocar pontos de interrupção incluem:  
  
    1.  Os eventos associados a um controle, como Clique, Insira etc.  
  
    2.  Os eventos associados à inicialização e o desligamento do aplicativo, como Carregar, Ativado etc.  
  
    3.  Foco e eventos de validação.  
  
     Para obter mais informações, consulte [Criando manipuladores de eventos no Windows Forms](../Topic/Creating%20Event%20Handlers%20in%20Windows%20Forms.md).  
  
3.  No menu **Depurar**, clique em **Iniciar**.  
  
4.  Depure usando as técnicas discutidas em [Noções básicas do depurador](../debugger/debugger-basics.md).  
  
## Consulte também  
 [Depurando código gerenciado](../debugger/debugging-managed-code.md)   
 [Tipos de projeto C\#, F\# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Como definir configurações de depuração e versão](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Definições do projeto para configurações de depuração do C\#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Definições do projeto para uma configuração de depuração do Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows Forms](../Topic/Windows%20Forms.md)