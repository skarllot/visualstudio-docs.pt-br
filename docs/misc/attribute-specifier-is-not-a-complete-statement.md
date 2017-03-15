---
title: "Especificador de atributo n&#227;o &#233; uma declara&#231;&#227;o completa | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32035"
  - "bc32035"
helpviewer_keywords: 
  - "BC32035"
ms.assetid: a0ddd673-4170-4bea-9c22-777d7bf21dfd
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Especificador de atributo n&#227;o &#233; uma declara&#231;&#227;o completa
Especificador de atributo não é uma instrução completa. Use uma continuação de linha para aplicar o atributo à instrução a seguir.  
  
 Um bloco de atributo aparece sozinho em uma linha de código\-fonte. Atributos devem ser aplicados no início de uma instrução de declaração, e eles devem ser parte dessa instrução.  
  
 **ID do erro:** BC32035  
  
### Para corrigir este erro  
  
-   Se a instrução de declaração estiver na linha a seguir, adicione um espaço e um sublinhado \(`_`\) após o bloco de atributo para combinar as linhas de código\-fonte.  
  
-   Se nenhuma instrução de declaração estiver associada com o bloco de atributo, forneça uma ou remova o bloco de atributo.  
  
-   Se o atributo for aplicar ao assembly inteiro ou para o módulo do assembly atual, o bloco de atributo permanecerá em uma linha de código\-fonte separado. Preceda o nome do atributo dentro dos colchetes angulares \(`< >`\) com `Assembly:` ou `Module:` e não adicione um espaço ou sublinhado após o bloco de atributo. Além disso, certifique\-se de que este bloco de atributo esteja no início do seu arquivo de origem.  
  
## Consulte também  
 [NÃO está em compilação: Aplicação de atributos](http://msdn.microsoft.com/pt-br/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Como quebrar e combinar instruções no código](../Topic/How%20to:%20Break%20and%20Combine%20Statements%20in%20Code%20\(Visual%20Basic\).md)