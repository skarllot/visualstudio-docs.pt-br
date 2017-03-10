---
title: "Como depurar um servi&#231;o WCF auto-hospedado | Microsoft Docs"
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
helpviewer_keywords: 
  - "depuração, WCF"
  - "WCF, depuração"
  - "WCF, serviço auto-hospedado"
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como depurar um servi&#231;o WCF auto-hospedado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Um *serviço auto\-hospedado* é um serviço WCF que não é executado dentro do IIS, do Host de Serviço WCF ou do Servidor de Desenvolvimento do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  A maneira mais fácil de depurar um WCF auto\-hospedado é configurar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para iniciar o cliente e o servidor quando você escolher **Iniciar Depuração** no menu **Depurar**.  
  
 Se o serviço WCF está sendo auto\-hospedado internamente ou é um processo que não pode ser iniciado dessa maneira, como serviço do NT, você não pode usar este método.  Em vez disso, execute um destes procedimentos:  
  
-   Anexe manualmente o depurador ao processo de hospedagem.  Para obter mais informações, consulte [Anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
     — ou —  
  
-   Inicie a depuração do cliente e inspecione uma chamada para o serviço.  Isso requer que você habilite a depuração no arquivo app.config.  Para obter mais informações, consulte [Limitações da depuração WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### Para iniciar o cliente e o host do Visual Studio  
  
1.  Crie uma solução do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que contém os projetos de cliente e de servidor.  
  
2.  Configure a solução para iniciar os processos do cliente e do servidor quando você escolhe **Iniciar** no menu **Depurar**.  
  
    1.  No **Gerenciador de Soluções**, clique com o botão direito do mouse no nome da solução.  
  
    2.  Clique em **Definir Projetos de Inicialização**.  
  
    3.  Na caixa de diálogo **Propriedades da Solução \<nome\>**, selecione **Vários Projetos de Inicialização**.  
  
    4.  Na grade **Vários Projetos de Inicialização**, na linha que corresponde ao projeto do servidor, clique em **Ação** e escolha **Iniciar**.  
  
    5.  Na linha que corresponde ao projeto de cliente, clique em **Ação** e escolha **Iniciar**.  
  
    6.  Clique em **OK**.  
  
## Consulte também  
 [Depurando serviços WCF](../debugger/debugging-wcf-services.md)   
 [Limitações da depuração WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Como intervir em serviços WCF](../debugger/how-to-step-into-wcf-services.md)