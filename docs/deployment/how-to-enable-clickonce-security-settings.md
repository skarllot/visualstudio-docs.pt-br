---
title: "Como habilitar configura&#231;&#245;es de seguran&#231;a do ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "implantação ClickOnce, configurações de segurança"
  - "segurança [Visual Studio], Aplicativos ClickOnce"
  - "configurações de segurança, implantação ClickOnce"
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como habilitar configura&#231;&#245;es de seguran&#231;a do ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Segurança de acesso ao código para aplicativos de ClickOnce deve ser habilitada para publicar o aplicativo.  Isso é feito automaticamente quando você publica um aplicativo usando o assistente Publicar.  
  
 Em alguns casos, permitindo que a segurança de acesso ao código pode afetar o desempenho quando compilar ou depurar seu aplicativo; Nesses casos, talvez você queira desativar temporariamente as configurações de segurança.  
  
 ClickOnce as configurações de segurança podem ser ativadas ou desativadas no  **Security** página da  **Project Designer**.  
  
### Para ativar as configurações de segurança de ClickOnce  
  
1.  Com um projeto selecionado no  **Solution Explorer**diante do  **projeto**  menu, clique em  **Propriedades**.  
  
2.  Clique na guia **Security**.  
  
3.  Selecione o  **Ativar configurações de segurança de ClickOnce** caixa de seleção.  
  
     Agora você pode personalizar as configurações de segurança para seu aplicativo na página segurança.  
  
    > [!NOTE]
    >  Esta caixa de seleção é selecionada automaticamente sempre que o aplicativo é publicado com o  **Publicar** assistente.  
  
### Para desativar as configurações de segurança de ClickOnce  
  
1.  Com um projeto selecionado no  **Solution Explorer**diante do  **projeto**  menu, clique em  **Propriedades**.  
  
2.  Clique na guia **Security**.  
  
3.  Limpar o  **Ativar configurações de segurança de ClickOnce** caixa de seleção.  
  
     Seu aplicativo será executado com as configurações de segurança confiança total; quaisquer configurações de  **Security** página será ignorada.  
  
    > [!NOTE]
    >  Cada vez que o aplicativo é publicado com o Assistente de publicação, esta caixa de seleção será selecionada; Você deve limpá\-lo novamente após cada publicação bem\-sucedida.  
  
## Consulte também  
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Segurança de acesso do código para aplicativos ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)