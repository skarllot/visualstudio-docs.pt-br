---
title: "Membro &#39;&lt; nome do membro &gt;&#39; n&#227;o pode ser inicializado em uma express&#227;o de inicializador de objeto porque ele n&#227;o &#233; um campo ou propriedade | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30990"
  - "vbc30990"
helpviewer_keywords: 
  - "BC30990"
ms.assetid: 3be2c135-20f6-49b2-a324-d213cfdf9ee3
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Membro &#39;&lt; nome do membro &gt;&#39; n&#227;o pode ser inicializado em uma express&#227;o de inicializador de objeto porque ele n&#227;o &#233; um campo ou propriedade
Uma lista de inicializadores de objeto não pode incluir membros compartilhados, constantes ou chamadas de método. Os membros na lista de inicializador devem ser campos ou propriedades, e membros de propriedade não podem requerer argumentos.  
  
 **ID do erro:** BC30990  
  
### Para corrigir este erro  
  
-   Remova a lista de inicializadores de objeto, todos os membros compartilhados, constantes, chamadas de métodos ou propriedades que têm parâmetros.  
  
## Consulte também  
 [Inicializadores de objeto: tipos nomeados e anônimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [NÃO está em compilação: Shared Members in Visual Basic](http://msdn.microsoft.com/pt-br/dbc3783f-83a2-4225-995d-c2d6d025663d)   
 [NÃO está em compilação: Propriedades e procedimentos de propriedade](http://msdn.microsoft.com/pt-br/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [NÃO está em compilação: Propriedades do padrão](http://msdn.microsoft.com/pt-br/a70f2a27-8176-4858-935e-f25afdd43ab5)   
 [Membros NotInBuild:Object](http://msdn.microsoft.com/pt-br/dfc2cc12-0e66-44fb-a78e-14f931db2309)   
 [Instrução Const](/dotnet/visual-basic/language-reference/statements/const-statement)