---
title: "CA2207: inicializar campos est&#225;ticos de tipo de valor embutido | Microsoft Docs"
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
  - "InitializeValueTypeStaticFieldsInline"
  - "CA2207"
helpviewer_keywords: 
  - "CA2207"
  - "InitializeValueTypeStaticFieldsInline"
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2207: inicializar campos est&#225;ticos de tipo de valor embutido
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InitializeValueTypeStaticFieldsInline|  
|CheckId|CA2207|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 Um tipo de valor declara um construtor estático explícito.  
  
## Descrição da Regra  
 Quando um tipo de valor é declarado, sofrerá uma inicialização padrão em que todos os campos de tipo de valor são definidos como zero e todos os campos de referência\- tipo são definidos a `null` \(`Nothing` no Visual Basic\).  Um construtor estático explícito é garantido apenas para executar antes que um construtor da instância do ou membro de tipo estático de ser chamado.  Em virtude disso, se o tipo for criado sem chamar um construtor da instância do, o construtor estática não é garantido para executar.  
  
 Se todos os dados estáticos forem embutidos inicializado e nenhum construtor estático explícito é declarado, os compiladores C\# e Visual Basic adicionam o sinalizador de `beforefieldinit` à definição de classe de MSIL.  Os compiladores também adicionam um construtor estático particular que contém o código de inicialização estático.  Este construtor estático privado é garantido para executar antes que todos os campos estáticos do tipo são acessadas.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra inicializar todos os dados estáticos quando é declarada e remover o construtor estático.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Regras Relacionadas  
 [CA1810: inicializar campos estáticos de tipo de referência embutido](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)