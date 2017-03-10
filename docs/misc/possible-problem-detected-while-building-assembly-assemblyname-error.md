---
title: "Poss&#237;vel problema detectado ao criar assembly &#39;&lt; assemblyname &gt;&#39;: &lt; erro &gt; | Microsoft Docs"
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
  - "vbc40010"
  - "bc40010"
helpviewer_keywords: 
  - "BC40010"
ms.assetid: 3a4f4a4a-a5ad-4501-bf4c-0fbf25c50734
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Poss&#237;vel problema detectado ao criar assembly &#39;&lt; assemblyname &gt;&#39;: &lt; erro &gt;
A ferramenta ALink, utilizada [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilador, reporta um erro construindo o assembly. Possíveis causas incluem o seguinte:  
  
-   Um conjunto assinado fazendo referência a um assembly sem sinal. Nesse caso, você deve considerar se o assembly referenciado satisfaz seus critérios de segurança.  
  
-   Criando um aplicativo de 64 bits em uma plataforma de 32 bits. Nesse caso, você deve garantir que versões de 64 bits de todos os assemblies referenciados estão instaladas na plataforma de destino. Para um assembly common language runtime \(CLR\), isso é manipulado automaticamente, embora essa mensagem de erro ainda será gerada.  
  
 Essa mensagem é um aviso. O compilador continua a gerar o assembly. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC40010  
  
### Para corrigir este erro  
  
1.  Examine a mensagem de erro entre aspas e tomar as devidas providências.  
  
2.  Compile o programa novamente para ver se o erro persiste.  
  
3.  Se o erro persistir, reinstale o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilador.  
  
4.  Se o erro persistir após a reinstalação, colete informações sobre as circunstâncias e notifique o Microsoft Product Support Services.  
  
## Consulte também  
 [Acessibilidade e suporte a produtos PAVEOVER](http://msdn.microsoft.com/pt-br/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)   
 [Common Language Runtime Overview](http://msdn.microsoft.com/pt-br/0fd9aeae-af10-435f-86d4-e76619741e4a)