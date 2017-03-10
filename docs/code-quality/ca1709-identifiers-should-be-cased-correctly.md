---
title: "CA1709: os identificadores do recurso devem ter mai&#250;sculas e min&#250;sculas corretas | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IdentifiersShouldBeCasedCorrectly"
  - "CA1709"
helpviewer_keywords: 
  - "CA1709"
  - "IdentifiersShouldBeCasedCorrectly"
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
caps.latest.revision: 29
caps.handback.revision: 29
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1709: os identificadores do recurso devem ter mai&#250;sculas e min&#250;sculas corretas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldBeCasedCorrectly|  
|CheckId|CA1709|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Interrompendo \- se for gerado em assemblies, nos namespaces, tipos, membros e parâmetros.<br /><br /> Sem\-quebras \- quando é acionado em parâmetros de tipo genéricas.|  
  
## Causa  
 O nome de um identificador não é encaixotado corretamente.  
  
 \- ou \-  
  
 O nome de um identificador contiver um acrônimo de duas letras e a segunda letra é minúsculos.  
  
 \- ou \-  
  
 O nome de um identificador contiver um acrônimo de três ou mais letras maiúsculas.  
  
## Descrição da Regra  
 Convenções de nomenclatura dão uma aparência comum para bibliotecas que tem como foco o common language runtime.  Isto reduz a curva de aprendizado que é necessária para novas bibliotecas de software, e aumenta confiança dos clientes de que a biblioteca foi desenvolvida por alguém que com experiência programar código gerenciado.  
  
 Por convenção, caixas de camelo o uso de nomes de parâmetros; o namespace, digite e, os nomes de membro usam o uso de maiúsculas e minúsculas de Pascal.  Em um nome camelo\- encaixotado, a primeira letra minúscula é, e a primeira letra de todas as palavras restantes no nome está em maiúsculas.  Exemplos de nomes camelo\- boxed são “packetSniffer”, “ioFile”, e “fatalErrorCode”.  Em um nome Pascal\- encaixotado, a primeira letra maiúscula é, e a primeira letra de todas as palavras restantes no nome está em maiúsculas.  Exemplos de nomes Pascal\- boxed são “PacketSniffer”, “IOFile”, e “FatalErrorCode”.  
  
 Essa regra se divide o nome na palavra com base em minúsculas e verifica todas as palavras de duas letras em uma lista de palavras de duas letras comuns, como “em” ou “my”.  Se não for encontrada uma correspondência, as palavras são consideradas um acrônimo.  Além disso, esta regra assumir\-las encontrou um acrônimo quando o nome contiver quatro letras maiúsculas em uma linha ou três letras maiúsculas em uma linha no final do nome.  
  
 Por convenção, os acrônimos de duas letras usam letras maiúsculas, e acrônimos de três ou mais caracteres use as caixas de Pascal.  Os exemplos a seguir usam essa convenção de nomenclatura: “DB”, “CR”, “Cpa”, e “Ecma”.  Os exemplos violam a convenção: “Io”, “XML”, e “DoD”, e para nomes de nonparameter, “XP” e “completo”.  
  
 O “ID” especial é encaixotado para causar uma violação desta regra. A “ID” não é um acrônimo mas é uma abreviação para “ID”.  
  
## Como Corrigir Violações  
 Altere o nome de modo que fique capitalizado corretamente.  
  
## Quando Suprimir Alertas  
 É seguro suprimir esse aviso se você tem suas próprias convenções de nomenclatura, ou se o identificador representa um nome apropriado, por exemplo, o nome de uma empresa ou tecnologia.  
  
 Você também pode adicionar termos, abreviações, e os acrônimos específicos que a um dicionário personalizado do código.  Os termos especificados no dicionário personalizado não causará violações desta regra.  Para obter mais informações, consulte [Como personalizar o dicionário de análise do código](../Topic/How%20to:%20Customize%20the%20Code%20Analysis%20Dictionary.md)  
  
## Regras Relacionadas  
 [CA1708: os identificadores devem ser diferentes além de maiúsculas de minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)