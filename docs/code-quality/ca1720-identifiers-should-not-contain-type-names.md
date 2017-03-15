---
title: "CA1720: os identificadores n&#227;o devem conter nomes de tipo | Microsoft Docs"
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
  - "CA1720"
  - "IdentifiersShouldNotContainTypeNames"
helpviewer_keywords: 
  - "IdentifiersShouldNotContainTypeNames"
  - "CA1720"
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1720: os identificadores n&#227;o devem conter nomes de tipo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotContainTypeNames|  
|CheckId|CA1720|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Quebra|  
  
## Causa  
 O nome de um parâmetro em um membro externamente visível contém um nome de tipo de dados.  
  
 \- ou \-  
  
 O nome de um membro externamente visível contém um nome específico do idioma do tipo de dados.  
  
## Descrição da Regra  
 Os nomes dos parâmetros e dos membros são usados para comunicar melhor seu significado do que para descrever seu tipo, que deve ser fornecido por ferramentas de desenvolvimento.  Para nomes de membros, se um nome de tipo de dados deve ser usado, use um nome independente em vez de um específico do idioma.  Por exemplo, em vez do nome do tipo int “” C\#, use o nome independente do tipo de dados, Int32.  
  
 Cada token discreto em nome do parâmetro ou do membro é verificado nos seguintes nomes específicos de idioma do tipo de dados, em um modo sem diferenciação de maiúsculas e minúsculas:  
  
-   Bool  
  
-   WChar  
  
-   Int8  
  
-   UInt8  
  
-   Short  
  
-   UShort  
  
-   Int  
  
-   UInt  
  
-   Integer  
  
-   UInteger  
  
-   Long  
  
-   ULong  
  
-   Não assinados  
  
-   Assinado  
  
-   Float  
  
-   Float32  
  
-   Float64  
  
 Além disso, os nomes de parâmetro também são verificados em relação aos seguintes nomes de independentes de tipo de dados, em um modo sem diferenciação de maiúsculas e minúsculas:  
  
-   Object  
  
-   Obj  
  
-   Booleano  
  
-   Char  
  
-   Cadeia de caracteres  
  
-   SByte  
  
-   Byte  
  
-   UByte  
  
-   Int16  
  
-   UInt16  
  
-   Int32  
  
-   UInt32  
  
-   Int64  
  
-   UInt64  
  
-   IntPtr  
  
-   Ptr  
  
-   Ponteiro  
  
-   UInptr  
  
-   UPtr  
  
-   UPointer  
  
-   Single  
  
-   Double  
  
-   Decimal  
  
-   Guid  
  
## Como Corrigir Violações  
 **Se acionado em um parâmetro:**  
  
 Substitua o identificador do tipo de dados em nome do parâmetro com o como um termo que melhor descreve o significado ou uma condição mais genérico, como “value”.  
  
 **Se acionado em relação a um membro:**  
  
 Substitua o identificador específico do idioma do tipo de dados em nome do membro com um termo que melhor descreve o significado, um equivalente independente, ou uma condição mais genérico, como “value”.  
  
## Quando Suprimir Alertas  
 Uso ocasional de nomes de tipo base do parâmetro e o membro pode ser apropriado.  No entanto, para desenvolvimento, nenhum cenário conhecido ocorre quando você precisar eliminar um aviso desta regra.  Para as bibliotecas que têm enviado anterior, talvez seja necessário suprimir um aviso desta regra.  
  
## Regras Relacionadas  
 [CA1709: os identificadores do recurso devem ter maiúsculas e minúsculas corretas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: os identificadores devem ser diferentes além de maiúsculas de minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707: os identificadores não devem conter sublinhados](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)  
  
 [CA1719: os nomes de parâmetro não devem corresponder aos nomes de membro](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)