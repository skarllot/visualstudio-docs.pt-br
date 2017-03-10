---
title: "Como editar um valor de registro | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.register.edit"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "valores de registro"
  - "Janela Registros, editando valores de registro"
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como editar um valor de registro
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A janela Registros estará disponível apenas se a depuração do nível de endereços estiver habilitada na caixa de diálogo **Opções**, nó **Depuração**.  
  
### Para alterar o valor de um registro  
  
1.  Na janela **Registros**, use a tecla TAB ou o mouse para mover o ponto de inserção para o valor que você deseja alterar.  Quando você começa a digitar, o cursor deve estar localizado na frente do valor que você deseja substituir.  
  
2.  Digite o novo valor.  
  
    > [!CAUTION]
    >  Alterar valores do registro \(principalmente nos registros de EIP e EBP\) pode afetar a execução do programa.  
  
    > [!CAUTION]
    >  Editar valores de ponto flutuante pode resultar em imprecisões secundárias devido à conversão decimal\-binária de componentes fracionários.  Mesmo uma edição aparentemente inócua pode resultar em alterações em alguns bits menos significativos no registro de um ponto flutuante.  
  
## Consulte também  
 [Como usar a janela Registros](../debugger/how-to-use-the-registers-window.md)