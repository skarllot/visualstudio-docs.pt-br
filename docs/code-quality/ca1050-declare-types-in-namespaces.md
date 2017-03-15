---
title: "CA1050: declarar tipos em namespaces | Microsoft Docs"
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
  - "CA1050"
  - "DeclareTypesInNamespaces"
helpviewer_keywords: 
  - "CA1050"
  - "DeclareTypesInNamespaces"
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1050: declarar tipos em namespaces
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DeclareTypesInNamespaces|  
|CheckId|CA1050|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um tipo público ou protegido é definido fora do escopo de um namespace nomeado.  
  
## Descrição da Regra  
 Tipos são declarados em namespaces para evitar conflitos de nome, e são uma maneira de organizar tipos relacionados em uma hierarquia de objetos.  Tipos fora de qualquer namespace nomeado estão em um namespace global que não pode ser referenciado no código.  
  
## Como Corrigir Violações  
 Para corrigir uma violação de esta regra, coloque o tipo em um namespace.  
  
## Quando Suprimir Alertas  
 Embora você nunca precise obrigatoriamente suprimir um alerta desta regra, é seguro fazer isso quando o assembly nunca será usado junto com outros assemblies.  
  
## Exemplo  
 O exemplo a seguir mostra uma biblioteca que contém um tipo declarado incorretamente fora de um namespace, e um tipo que com o mesmo nome declarado em um namespace.  
  
 [!code-cs[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]  
  
## Exemplo  
 O aplicativo a seguir usa a biblioteca que foi definida anteriormente.  Observe que o tipo que é declarado fora de um namespace é criado quando o nome `Test` não é qualificado por um namespace.  Observe também que para acessar `Test` em `Goodspace`, o nome do namespace é necessário.  
  
 [!CODE [FxCop.Design.TestTypesLive#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive#1)]