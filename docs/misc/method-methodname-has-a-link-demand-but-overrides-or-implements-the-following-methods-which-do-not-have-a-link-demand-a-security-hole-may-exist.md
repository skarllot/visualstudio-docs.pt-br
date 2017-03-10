---
title: "O m&#233;todo &#39;&lt; methodname &gt;&#39; tem uma demanda de link, mas substitui ou implementa os m&#233;todos a seguir que n&#227;o possuem uma demanda de link. Pode haver uma falha de seguran&#231;a: | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc42200"
  - "vbc42200"
helpviewer_keywords: 
  - "BC42200"
ms.assetid: c79d672e-638c-4d87-9b93-edf12ce84a52
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O m&#233;todo &#39;&lt; methodname &gt;&#39; tem uma demanda de link, mas substitui ou implementa os m&#233;todos a seguir que n&#227;o possuem uma demanda de link. Pode haver uma falha de seguran&#231;a:
Uma ação de demanda de link de segurança foi adicionada ao método. No entanto, o método substitui ou implementa os métodos que não têm as demandas de link. Portanto, os métodos substituídos ou implementados podem ser chamados com permissões insuficientes, que podem causar um problema de segurança.  
  
 Por padrão, essa mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC42200  
  
### Para corrigir este erro  
  
-   Adicione as demandas de link para os métodos implementados e\/ou substituídos.  
  
## Consulte também  
 [Demandas de link](../Topic/Link%20Demands.md)   
 [Demanda vs. LinkDemand](http://msdn.microsoft.com/pt-br/1ab877f2-70f4-4e0d-8116-943999dfe8f5)   
 [Otimizações de segurança](http://msdn.microsoft.com/pt-br/cf255069-d85d-4de3-914a-e4625215a7c0)