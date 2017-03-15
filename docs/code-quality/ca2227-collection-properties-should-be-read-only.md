---
title: "CA2227: as propriedades de cole&#231;&#227;o devem ser somente leitura | Microsoft Docs"
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
  - "CA2227"
  - "CollectionPropertiesShouldBeReadOnly"
helpviewer_keywords: 
  - "CA2227"
  - "CollectionPropertiesShouldBeReadOnly"
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2227: as propriedades de cole&#231;&#227;o devem ser somente leitura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CollectionPropertiesShouldBeReadOnly|  
|CheckId|CA2227|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Uma propriedade gravável externamente visível é um tipo que implementa <xref:System.Collections.ICollection?displayProperty=fullName>.  Matrizes, os indicadores \(propriedades item com o nome “"\), e os conjuntos de permissões são ignorados pela regra.  
  
## Descrição da Regra  
 Uma propriedade gravável da coleção permite que um usuário substitui a coleção o com uma coleção completamente diferente.  Uma propriedade somente leitura para a coleção de ser substituído mas ainda permite que membros individuais são definidos.  Se a substituição a coleção é uma meta, o padrão preferencial de design é incluir um método para remover todos os elementos da coleção e um método para repopular a coleção.  Consulte os métodos de <xref:System.Collections.ArrayList.Clear%2A> e de <xref:System.Collections.ArrayList.AddRange%2A> da classe de <xref:System.Collections.ArrayList?displayProperty=fullName> para obter um exemplo desse padrão.  
  
 Binários e o serialização XML oferece suporte às propriedades somente leitura que são coleções.  A classe de <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> tem requisitos específicos para os tipos que implementam <xref:System.Collections.ICollection> e <xref:System.Collections.IEnumerable?displayProperty=fullName> para ser serializáveis.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, faça a propriedade somente leitura e, se o design requer a, adicionar métodos para limpar e preencha novamente a coleção.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 O exemplo a seguir mostra um tipo com uma propriedade gravável da coleção e mostra como a coleção pode ser substituída diretamente.  Além disso, o modo preferido de substituir uma propriedade somente leitura da coleção usando `Clear` e métodos de `AddRange` é mostrado.  
  
 [!code-cs[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]  
  
## Regras Relacionadas  
 [CA1819: as propriedades não devem retornar matrizes](../code-quality/ca1819-properties-should-not-return-arrays.md)