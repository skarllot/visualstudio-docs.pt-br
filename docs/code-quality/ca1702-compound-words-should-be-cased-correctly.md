---
title: "CA1702: palavras compostas devem ter mai&#250;sculas e min&#250;sculas corretas | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1702"
  - "CompoundWordsShouldBeCasedCorrectly"
helpviewer_keywords: 
  - "CA1702"
  - "CompoundWordsShouldBeCasedCorrectly"
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1702: palavras compostas devem ter mai&#250;sculas e min&#250;sculas corretas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1702|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Alteração \- quando gerado em assemblies<br /><br /> Sem quebra \- quando gerado em parâmetros de tipo.|  
  
## Causa  
 O nome de um identificador contém várias palavras e pelo menos uma das palavras parece ser uma palavra composta que não está capitalizada corretamente.  
  
## Descrição da Regra  
 O nome do identificador é dividido em palavras que são baseadas na capitalização.  Cada combinação contígua de duas palavras é verificada pela biblioteca de correção ortográfico da Microsoft.  Se for reconhecida, o identificador gera uma violação da regra.  Exemplos de palavras compostas que causam uma violação são “CheckSum” e “MultiPart”, que devem ser capitalizadas como “Checksum” e “Multipart”, respectivamente.  Devido ao uso usual anterior, várias exceções estão integradas nesta regra, e várias únicas palavra são marcadas, tais como “Toolbar” e “Filename”, que devem ser capitalizadas como duas palavras distintas \(neste caso, “ToolBar” e “FileName”\).  
  
 Convenções de nomenclatura dão uma aparência comum para bibliotecas que tem como foco o common language runtime.  Isto reduz a curva de aprendizado que é necessária para novas bibliotecas de software, e aumenta confiança dos clientes de que a biblioteca foi desenvolvida por alguém que com experiência programar código gerenciado.  
  
## Como Corrigir Violações  
 Altere o nome de modo que fique capitalizado corretamente.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um alerta desta regra se as duas partes da palavra composta forem reconhecidas pelo dicionário de ortografia e a intenção for usar duas palavras.  
  
## Regras Relacionadas  
 [CA1701: as palavras compostas da cadeia de caracteres do recurso devem ter maiúsculas e minúsculas corretas](../Topic/CA1701:%20Resource%20string%20compound%20words%20should%20be%20cased%20correctly.md)  
  
 [CA1709: os identificadores do recurso devem ter maiúsculas e minúsculas corretas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: os identificadores devem ser diferentes além de maiúsculas de minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## Consulte também  
 [Diretrizes de nomenclatura](../Topic/Naming%20Guidelines.md)   
 [Convenções de maiúsculas e minúsculas](../Topic/Capitalization%20Conventions.md)