---
title: "Poss&#237;vel problema detectado ao compilar o assembly: &lt; erro &gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40009"
  - "bc40009"
helpviewer_keywords: 
  - "BC40009"
ms.assetid: 4bc5108a-a96e-43be-8bba-a47441a25f3e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Poss&#237;vel problema detectado ao compilar o assembly: &lt; erro &gt;
A ferramenta ALink, utilizada [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilador, reporta um erro construindo o assembly. Uma possível causa é um assembly assinado fazendo referência a um assembly sem sinal.  
  
 Essa mensagem é um aviso. O compilador continua a gerar o assembly. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC40009  
  
### Para corrigir este erro  
  
1.  Examine a mensagem de erro entre aspas e tomar as devidas providências.  
  
2.  Compile o programa novamente para ver se o erro persiste.  
  
3.  Se o erro persistir, reinstale o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilador.  
  
4.  Se o erro persistir após a reinstalação, colete informações sobre as circunstâncias e notifique o Microsoft Product Support Services.  
  
## Consulte também  
 [Acessibilidade e suporte a produtos PAVEOVER](http://msdn.microsoft.com/pt-br/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)