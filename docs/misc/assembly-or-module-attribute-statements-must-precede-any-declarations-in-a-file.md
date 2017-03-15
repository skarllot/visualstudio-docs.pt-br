---
title: "Declara&#231;&#245;es de atributo de m&#243;dulo ou assembly devem preceder qualquer declara&#231;&#227;o em um arquivo | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30637"
  - "bc30637"
helpviewer_keywords: 
  - "BC30637"
ms.assetid: 80242581-fa8a-4903-9395-6f7ad1610231
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Declara&#231;&#245;es de atributo de m&#243;dulo ou assembly devem preceder qualquer declara&#231;&#227;o em um arquivo
Atributos globais devem ser declarados na parte superior de um arquivo de origem após `Option` e `Imports` instruções, mas antes de quaisquer outras instruções.  
  
 **ID do erro:** BC30637  
  
### Para corrigir este erro  
  
1.  Coloque atributos globais, tais como `<Module:>` e `<Assembly:>` na parte superior do seu arquivo de origem.  
  
## Consulte também  
 [NÃO está em compilação: Atributos no Visual Basic](http://msdn.microsoft.com/pt-br/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [NÃO está em compilação: Atributos globais no Visual Basic](http://msdn.microsoft.com/pt-br/253a32d8-1531-4504-b687-088554ab71d2)