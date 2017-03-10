---
title: "Editar e Continuar (Visual Basic) | Microsoft Docs"
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
helpviewer_keywords: 
  - "Editar e Continuar 64 bits"
  - "depurando [Visual Basic], Editar e continuar"
  - "Editar e Continuar [Visual Basic]"
  - "Editar e continuar, 64 bits"
  - "Visual Basic, Editar e continuar"
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
caps.latest.revision: 40
caps.handback.revision: 40
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Editar e Continuar (Visual Basic)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Editar e Continuar são um recurso para depuração do [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] que permite alterar seu código durante a execução em modo de interrupção.  Depois que as edições do código tiverem sido aplicadas, você poderá retomar a execução de código com as novas edições no lugar e visualizar o efeito.  
  
 Você pode usar o recurso Editar e Continuar sempre que entrar no modo de Interrupção.  No modo de Interrupção, o ponteiro de instrução, uma seta amarela na janela de origem, aponta para a linha que será executada em seguida e será localizado em uma instrução executável dentro de um método ou corpo de propriedade.  Você pode fazer praticamente qualquer tipo de alteração nas instruções executáveis no modo de Interrupção, e a alteração será inserida no projeto subjacente.  Quando estiver no modo de Interrupção, porém, não será permitido em geral modificar instruções de declaração, como métodos públicos, campos públicos ou declarações da classe.  
  
 Quando você faz uma edição não autorizada, a alteração será marcada com um sublinhado ondulado roxo e uma tarefa será exibida na Lista de Tarefas.  Você deve desfazer uma edição não autorizada se quiser continuar usando Editar e Continuar.  Certas edições não autorizadas podem ser permitidas se forem feitas fora de Editar e Continuar.  Se você quiser reter os resultados de uma edição não autorizada, deverá parar de depurar e reiniciar o aplicativo.  
  
 Editar e Continuar tem suporte para projetos de 64 bits voltados para o .NET Framework 4.5.1.  
  
 Editar e Continuar não tem suporte quando você começa a depuração usando **Anexar ao Processo**.  Editar e Continuar não tem suporte para código otimizado, código gerenciado misto e código nativo, ou projetos do Compact Framework \(dispositivo inteligente\).  
  
 Os tópicos desta seção fornecem detalhes adicionais sobre como usar esse recurso e que tipos de alterações não são permitidas.  
  
## Nesta seção  
 [Como aplicar edições no modo de interrupção com editar e continuar](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 Explica como aplicar edições do código no modo de Interrupção.  
  
 [Edições não suportadas em Editar e Continuar do Visual Basic](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)  
 Descreve quais tipos de edições não podem ser executadas em Editar e Continuar do [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].  
  
## Seções relacionadas  
 [Editar e continuar](../debugger/edit-and-continue.md)  
 Fornece uma lista de tópicos em Editar e Continuar.