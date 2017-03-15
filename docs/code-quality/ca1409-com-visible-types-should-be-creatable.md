---
title: "CA1409: os tipos vis&#237;veis Com devem ser cri&#225;veis | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ComVisibleTypesShouldBeCreatable"
  - "CA1409"
helpviewer_keywords: 
  - "ComVisibleTypesShouldBeCreatable"
  - "CA1409"
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1409: os tipos vis&#237;veis Com devem ser cri&#225;veis
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ComVisibleTypesShouldBeCreatable|  
|CheckId|CA1409|  
|Categoria|Microsoft.Interoperability|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um tipo de referência que é marcado como especificamente visível ao Component Object Model \(COM\) contém um construtor público mas não com parâmetros contém um construtor \(sem parâmetros\) público padrão.  
  
## Descrição da Regra  
 Um tipo sem um construtor público padrão não pode ser criada por clientes COM.  No entanto, o tipo ainda poderá ser acessado pelos clientes COM se outros meios estão disponíveis para criar o tipo e o passar ao cliente \(por exemplo, com o valor de retorno da chamada do método\).  
  
 A regra ignora os tipos derivados de <xref:System.Delegate?displayProperty=fullName>.  
  
 Por padrão, os seguintes são visíveis à: os assemblies, tipos de chaves pública, membros públicos da instância do no utilitário, e todos os membros de tipos de valor públicos.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, adicione um construtor padrão público ou remover <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> do tipo.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso dessa regra se outros modos são fornecidas para criar e passe o objeto ao cliente da.  
  
## Regras Relacionadas  
 [CA1017: marcar assemblies com ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## Consulte também  
 [Qualificando tipos do .NET para interoperação](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)   
 [Interoperação com código não gerenciado](../Topic/Interoperating%20with%20Unmanaged%20Code.md)