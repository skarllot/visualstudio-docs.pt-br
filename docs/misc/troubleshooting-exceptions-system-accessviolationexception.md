---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.AccessViolationException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Exceção System.AccessViolationException"
  - "Classe AccessViolationException"
ms.assetid: 7f09315d-8aad-4ab1-8b5e-21a8c97f6c14
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.AccessViolationException
Um <xref:System.AccessViolationException> é lançada quando há uma tentativa de ler ou gravar em memória protegida.  
  
## Dicas associadas  
 Certifique\-se de que a memória que você está tentando acessar foi alocada.  
 Gerenciamento automático de memória é um dos serviços que o common language runtime fornece. Você poderá ir para código gerenciado para tirar proveito desse serviço. Para obter mais informações, consulte [Gerenciamento automático de memória](../Topic/Automatic%20Memory%20Management.md).  
  
 Certifique\-se de que a memória que você está tentando acessar não foi corrompida.  
 Se vários de operações de gravação ocorreram por ponteiros incorretos, a memória pode estar corrompida.  
  
### Comentários  
 Uma violação de acesso ocorre em código não gerenciado ou não seguro quando ele tenta ler ou gravar em memória que não foi alocada, ou para o qual ele não tem acesso. Nem todas as leituras ou gravações por ponteiros incorretos resultam em violações de acesso, portanto uma violação de acesso geralmente indica que várias leituras ou gravações ocorreram através de ponteiros incorretos, e que a memória pode estar corrompida.  
  
 No código gerenciado, todas as referências são válidas ou nulas. Qualquer operação que tenta referenciar uma referência nula no código verificável gera <xref:System.NullReferenceException>.  
  
 Uma violação de acesso ocorre em código gerenciado não seguro pode ser expressa como uma <xref:System.NullReferenceException> ou <xref:System.AccessViolationException>, dependendo da plataforma.  
  
 Violações de acesso em código não gerenciado que vão para código gerenciado sempre são encapsuladas em um <xref:System.AccessViolationException>.  
  
## Consulte também  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Gerenciamento de memória: exemplos](../Topic/Memory%20Management:%20Examples.md)   
 [Gerenciamento automático de memória](../Topic/Automatic%20Memory%20Management.md)