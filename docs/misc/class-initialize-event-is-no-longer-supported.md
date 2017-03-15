---
title: "N&#227;o h&#225; suporte para o evento &#39;Class_Initialize&#39; | Microsoft Docs"
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
  - "vbc42001"
  - "bc42001"
helpviewer_keywords: 
  - "BC42001"
ms.assetid: 31e7c383-894e-416c-b834-3688cc340ccf
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o h&#225; suporte para o evento &#39;Class_Initialize&#39;
Não há suporte para o evento 'Class\_Initialize'. Use 'Sub New' para inicializar uma classe.  
  
 O `Class_Initialize` eventos de versões anteriores do [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] é substituído por construtores de classe.  
  
 Por padrão, essa mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC42001  
  
### Para corrigir este erro  
  
-   Declare um ou mais `Sub` procedimentos chamados `New` ao inicializar uma classe.`Sub New` é chamado quando uma instância de classe é recém\-criada.  
  
## Consulte também  
 [Class\_Initialize Changes in Visual Basic](http://msdn.microsoft.com/pt-br/2cd023cf-2869-4836-b08d-43822294beeb)   
 [Classes for Visual Basic 6.0 Users](http://msdn.microsoft.com/pt-br/d625222c-cd32-4c8d-b25c-ea71729b88b7)   
 [NÃO está em compilação: Usando construtores e destruidores](http://msdn.microsoft.com/pt-br/548eebe1-86c4-4377-b2f5-447cb8be3d90)