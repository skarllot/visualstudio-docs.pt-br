---
title: "CA2105: os campos da matriz n&#227;o devem ser somente leitura | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2105"
  - "ArrayFieldsShouldNotBeReadOnly"
helpviewer_keywords: 
  - "ArrayFieldsShouldNotBeReadOnly"
  - "CA2105"
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2105: os campos da matriz n&#227;o devem ser somente leitura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ArrayFieldsShouldNotBeReadOnly|  
|CheckId|CA2105|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um campo público ou protegido que contém uma matriz é declarado como somente leitura.  
  
## Descrição da Regra  
 Quando você aplica o modificador `readonly` \(`ReadOnly` em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) a um campo que contém uma matriz, o campo não pode ser alterado para se referir a uma matriz diferente.  No entanto, os elementos da matriz que são armazenados em um campo somente leitura podem ser alterados.  O código que toma decisões ou executa operações baseadas em elementos de uma matriz somente leitura que pode ser acessada publicamente pode conter uma vulnerabilidade de segurança explorável.  
  
 Observe que ter um campo público também viola a regra de design [CA1051: não declarar campos de instância visíveis](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).  
  
## Como Corrigir Violações  
 Para corrigir a vulnerabilidade de segurança que é identificada por esta regra, não confie no conteúdo de uma matriz somente leitura que pode ser acessada publicamente.  É altamente recomendável que você use um dos seguintes procedimentos:  
  
-   Substitua a matriz com uma coleção fortemente tipada que não pode ser modificada.  Para obter mais informações, consulte <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.  
  
-   Substitua o campo público com um método que retorna um clone de uma matriz particular.  Porque seu código não confia no clone, não há risco se os elementos forem alterados.  
  
 Se você escolher a segunda abordagem, não substitua o campo com uma propriedade; propriedades que as matrizes de retorno prejudicam o desempenho.  Para obter mais informações, consulte [CA1819: as propriedades não devem retornar matrizes](../code-quality/ca1819-properties-should-not-return-arrays.md).  
  
## Quando Suprimir Alertas  
 A exclusão de um aviso dessa regra é fortemente desencorajada.  Quase não existe cenário onde o conteúdo de um campo somente leitura não é importante.  Se este é o caso com seu cenário, remova o modificador de `readonly` em vez de excluir a mensagem.  
  
## Exemplo  
 Este exemplo demonstra os perigos de violar esta regra.  A primeira parte do exemplo mostra uma biblioteca que tenha um tipo, `MyClassWithReadOnlyArrayField`, que contém dois campos \(`grades` e `privateGrades`\) que não são seguros.  O campo `grades` é público, e portanto vulnerável a qualquer chamador.  O campo `privateGrades` é particular mas ainda é vulnerável aos chamadores porque é retornado pelo método `GetPrivateGrades`.  O campo `securePrivateGrades` é exposto de uma maneira segura pelo método `GetSecurePrivateGrades`.  É declarado particular para seguir boas práticas de design.  A segunda parte mostra código que modifica valores armazenados nos membros de `grades` e de `privateGrades`.  
  
 A biblioteca de classes de exemplo é exibido no exemplo a seguir.  
  
 [!code-cs[FxCop.Security.ArrayFieldsNotReadOnly#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_1.cs)]  
  
## Exemplo  
 O código a seguir usa a biblioteca de classes de exemplo para ilustrar problemas de segurança com matriz de somente leitura.  
  
 [!code-cs[FxCop.Security.TestArrayFieldsRead#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_2.cs)]  
  
 A saída de esse exemplo são:  
  
  **Antes de violação: Classificações: 90, 90, 90 classificações privadas: 90, 90, 90 classificações seguros, 90, 90, 90**  
**Depois de violação: Classificações: 90, 555, 90 classificações privadas: 90, 555, 90 classificações seguros, 90, 90, 90**   
## Consulte também  
 <xref:System.Array?displayProperty=fullName>   
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>