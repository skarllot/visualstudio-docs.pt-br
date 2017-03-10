---
title: "Erro no n&#237;vel de projeto importar &#39;&lt; qualifiedelementname &gt;&#39; em &#39;&lt; qualifiedcontainername &gt;&#39;: &lt; errormessage &gt; | Microsoft Docs"
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
  - "BC30797"
  - "vbc30797"
helpviewer_keywords: 
  - "BC30797"
ms.assetid: 529f354f-f255-4adc-ab21-bd1796e58d69
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Erro no n&#237;vel de projeto importar &#39;&lt; qualifiedelementname &gt;&#39; em &#39;&lt; qualifiedcontainername &gt;&#39;: &lt; errormessage &gt;
Uma instrução acessa um elemento de programação que é definido em outro assembly, mas não há nenhuma referência de projeto ao assembly.  
  
 Por exemplo, seu código pode estar acessando uma enumeração chamada `desiredEnumeration` usando a cadeia de caracteres de qualificação `otherNamespace.otherClass.desiredEnumeration`. Se o compilador não pode localizar `otherNamespace.otherClass` entre suas referências do projeto, ele gerará esse erro.  
  
 **ID do erro:** BC30797  
  
### Para corrigir este erro  
  
1.  Verifique se que todos os elementos na cadeia de caracteres de qualificação do elemento de programação está escrito corretamente.  
  
2.  Verifique se que seu projeto possui uma referência ao assembly que define o elemento de programação desejado.  
  
3.  Consulte a mensagem de erro e tomar as devidas providências.  
  
## Consulte também  
 [NOTINBUILD: Resolvendo uma referência quando várias variáveis têm o mesmo nome](http://msdn.microsoft.com/pt-br/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [PONTA como: modificar propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [PONTA como: Adicionar ou remover referências usando a caixa de diálogo Adicionar referência](http://msdn.microsoft.com/pt-br/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)