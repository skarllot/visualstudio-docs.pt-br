---
title: "CA2204: os literais do recurso devem ter a ortografia correta | Microsoft Docs"
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
  - "Literals should be spelled correctly"
  - "CA2204"
  - "LiteralsShouldBeSpelledCorrectly"
helpviewer_keywords: 
  - "CA2204"
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2204: os literais do recurso devem ter a ortografia correta
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|LiteralsShouldBeSpelledCorrectly|  
|CheckId|CA2204|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 Um método envia uma cadeia de caracteres literal que será usado em um parâmetro ou a propriedade que requer uma cadeia de caracteres localizada e a cadeia de caracteres literal contém uma ou mais palavras que não são reconhecidos pela biblioteca de SPELLING CHECKER da Microsoft.  
  
## Descrição da Regra  
 Esta regra verifica uma cadeia de caracteres literal que será passada como um valor em um parâmetro ou a uma propriedade quando um ou mais dos casos a seguir for verdadeiro:  
  
-   O atributo de <xref:System.ComponentModel.LocalizableAttribute> de parâmetro ou da propriedade for definido para retificar.  
  
-   O nome do parâmetro ou da propriedade contém o texto”, “a “, mensagem” ou “legenda”.  
  
-   O nome do parâmetro de cadeia de caracteres que é passado para um método de Console.Write ou de Console.WriteLine é “valor” ou “formato”.  
  
 Esta regra analisa a cadeia de caracteres literal em palavras, em palavras compostas de geração de tokens, e em verificações a ortografia de cada palavra\/token.  Para obter informações sobre o algoritmo de análise, consulte [CA1704: os identificadores do recurso devem ter a ortografia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
 Por padrão, a versão em inglês \(en\) de SPELLING CHECKER é usada.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, corrigir a ortografia de palavras ou adicionar a palavra a um dicionário personalizado.  Para obter informações sobre como usar dicionários personalizados, consulte [Como personalizar o dicionário de análise do código](../Topic/How%20to:%20Customize%20the%20Code%20Analysis%20Dictionary.md).  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  As palavras estar escrito corretamente reduzir a curva de aprendizagem necessária para novas bibliotecas de software.  
  
## Regras Relacionadas  
 [CA1704: os identificadores do recurso devem ter a ortografia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA1703: as cadeias de caracteres do recurso devem ter a ortografia correta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)