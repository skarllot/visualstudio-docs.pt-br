---
title: "Como habilitar e desabilitar Editar e Continuar | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "Opção de vinculador /INCREMENTAL"
  - "Comando Aplicar Alterações de Código"
  - "Modo de interrupção, aplicando alterações de código"
  - "alterações de código, aplicando no modo de interrupção"
  - "Editar e continuar, aplicando alterações de código"
  - "Editar e continuar, desabilitando"
  - "Editar e continuar, ativando"
  - "Comando Ir"
  - "opção de vinculador INCREMENTAL"
  - "Comando Etapa"
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como habilitar e desabilitar Editar e Continuar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode desabilitar ou habilitar editar e continuar no **opções** caixa de diálogo em tempo de design. Você não pode alterar essa configuração enquanto você está depurando.  
  
 Editar e continuar funciona somente em compilações de depuração. Para C\+\+ nativo, editar e continuar requer o uso de \/incremental. opção.  
  
## Procedimentos  
  
#### Para habilitar\/desabilitar editar e continuar  
  
1.  Abrir página de opções de depuração \(**Ferramentas \/ opções \/ depuração**\).  
  
2.  Role para baixo até **Editar e continuar** categoria.  
  
3.  Para habilitar, selecione o **Habilitar Editar e continuar** caixa de seleção. Para desabilitar, desmarque a caixa de seleção.  
  
    > [!NOTE]
    >  Se IntelliTrace estiver habilitado e coletar eventos do IntelliTrace e informações de chamada, editar e continuar está desabilitado. Para obter mais informações, consulte [Configurar IntelliTrace](http://msdn.microsoft.com/pt-br/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
4.  Clique em **OK**.  
  
 Para obter mais informações sobre essas opções, consulte [Caixa de diálogo Geral, Depuração, Opções](../debugger/general-debugging-options-dialog-box.md).  
  
## Consulte também  
 [Editar e continuar](../debugger/edit-and-continue.md)