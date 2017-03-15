---
title: "O projeto &#39;&lt; projectname &gt;&#39; requer uma refer&#234;ncia &#224; vers&#227;o &#39;&lt; versionnumber1 &gt;&#39; do assembly &#39;&lt; assemblyname &gt;&#39;, mas faz refer&#234;ncia &#224; vers&#227;o &#39;&lt; versionnumber2 &gt;&#39; assembly &#39;&lt; assemblyname &gt;&#39; (aviso Visual Basic) | Microsoft Docs"
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
  - "vbc42203"
  - "bc42203"
helpviewer_keywords: 
  - "BC42203"
ms.assetid: 26a3fa34-ec5d-4817-a947-3959446a924a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O projeto &#39;&lt; projectname &gt;&#39; requer uma refer&#234;ncia &#224; vers&#227;o &#39;&lt; versionnumber1 &gt;&#39; do assembly &#39;&lt; assemblyname &gt;&#39;, mas faz refer&#234;ncia &#224; vers&#227;o &#39;&lt; versionnumber2 &gt;&#39; assembly &#39;&lt; assemblyname &gt;&#39; (aviso Visual Basic)
O projeto '\< projectname \>' requer uma referência à versão '\< versionnumber1 \>' do assembly '\< assemblyname \>', mas faz referência à versão '\< versionnumber2 \>' assembly '\< assemblyname \>'. Referência à versão '\< versionnumber1 \>' emitida.  
  
 Um projeto faz uma referência indireta a um assembly que é definido em outro lugar, mas o projeto também tem uma referência direta a uma versão anterior do assembly.  
  
 Para acomodar acesso a tipos e elementos de programação definidos na versão mais recente, mas não na versão anterior, o compilador usa a referência indireta para a versão mais recente quando Resolvendo acessos.  
  
 Por padrão, essa mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC42203  
  
### Para corrigir este erro  
  
-   Remova a referência direta para a versão anterior do assembly ou alterá\-lo para referir\-se a versão mais recente.  
  
## Consulte também  
 [Assemblies no Common Language Runtime](../Topic/Assemblies%20in%20the%20Common%20Language%20Runtime.md)   
 [NIB: Referenciando Namespaces e componentes](http://msdn.microsoft.com/pt-br/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Gerenciando referências em um projeto](../ide/managing-references-in-a-project.md)   
 [PONTA: Referências](http://msdn.microsoft.com/pt-br/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [PONTA como: Adicionar ou remover referências usando a caixa de diálogo Adicionar referência](http://msdn.microsoft.com/pt-br/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)