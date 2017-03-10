---
title: "Hierarquias de classe base virtuais | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "classes [C++], as classes base virtuais"
  - "hierarquias de classes, classes base virtuais"
  - "classes derivadas, considerações de hierarquia de classe"
  - "funções virtuais, em hierarquias de classe base virtual"
  - "classes base virtuais"
  - "classes base virtuais, hierarquias"
  - "hierarquias de classe base virtual"
ms.assetid: d24fda17-f829-48d6-84ec-8100f26bc5cf
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Hierarquias de classe base virtuais
Algumas hierarquias de classe são amplas mas têm muitas coisas em comum. O código comum é implementado na classe base, enquanto o código específico está em classes derivadas.  
  
 É importante para as classes base estabelecer um protocolo por meio do qual as classes derivadas podem acessar a funcionalidade máxima. Esses protocolos são implementados normalmente usando funções virtuais. Às vezes, a classe base fornece uma implementação padrão para essas funções. Em uma hierarquia de classe, como o `Document` hierarquia na Figura exemplo de gráfico acíclico direcionado \(consulte [herança única](/visual-cpp/cpp/single-inheritance)\), duas funções úteis são `Identify` e `WhereIs`.  
  
 Quando chamado, o `Identify` função retorna uma identificação correta, apropriada para o tipo de documento: para um `Book`, uma chamada de função como `doc->Identify()` deve retornar o número ISBN; no entanto, para um `HelpFile`, um produto nome e número de revisão são provavelmente mais apropriados. Da mesma forma, `WhereIs` deve retornar uma linha e uma prateleira para um `Book`, mas para um `HelpFile` deve retornar um local de disco — talvez um diretório e nome de arquivo.  
  
 É importante que todas as implementações da `Identify` e `WhereIs` funções retornam o mesmo tipo de informação. Nesse caso, uma cadeia de caracteres é apropriada.  
  
 Essas funções são implementadas como funções virtuais e, em seguida, invocado usando um ponteiro para uma classe base. A associação ao código real ocorre em tempo de execução, selecionando o correto `Identify` ou `WhereIs` função.  
  
## Consulte também  
 [Visão geral de classes derivadas](../misc/overview-of-derived-classes.md)