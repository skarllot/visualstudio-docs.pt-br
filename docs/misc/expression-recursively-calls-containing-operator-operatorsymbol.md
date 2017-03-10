---
title: "A express&#227;o chama recursivamente o operador recipiente &#39;&lt; operatorsymbol &gt;&#39; | Microsoft Docs"
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
  - "BC42004"
  - "vbc42004"
helpviewer_keywords: 
  - "BC42004"
ms.assetid: a874c44a-3aec-447d-90f7-5659f1b2f5f6
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A express&#227;o chama recursivamente o operador recipiente &#39;&lt; operatorsymbol &gt;&#39;
Uma expressão em um procedimento de operador usa o operador que está sendo definido. Isso resulta em um procedimento de operador chamando a mesmo devido a tipos de dados que estão sendo usados.  
  
 O procedimento de operador que você está definindo chama a mesmo se ele usa o mesmo operador com qualquer um dos seguintes:  
  
-   Os mesmos operandos para o qual você está definindo o operador;  
  
-   Operandos dos mesmos tipos de dados para o qual você está definindo o operador; ou  
  
-   Operandos de tipos de dados que ampliam para os tipos de dados para o qual você está definindo o operador.  
  
 Um *chamada recursiva* é quando um procedimento chama a mesmo. Chamadas recursivas podem resultar em um *loop infinito*, no qual controle passa pelo mesmo conjunto de instruções repetidamente até que seu aplicativo seja encerrado externamente. Se seu código não incluir um ou mais testes que podem ser usados para terminar a recursão, risco de um loop infinito.  
  
 Por padrão, essa mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC42004  
  
### Para corrigir este erro  
  
-   Se sua lógica requer que o procedimento de operador chame a mesmo, esteja certo de que testar pelo menos uma condição que certamente ocorrerá em algum ponto e usar este teste para finalizar as chamadas recursivas.  
  
-   Se sua lógica não exigir que o procedimento de operador chame a mesmo, remova todas as chamadas recursivas ou substituí\-los por instruções que não chamam seu próprio procedimento.  
  
## Consulte também  
 [Procedimentos do operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Como definir um operador de conversão](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)