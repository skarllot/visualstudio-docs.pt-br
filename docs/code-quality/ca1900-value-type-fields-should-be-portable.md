---
title: "CA1900: os campos de tipo de valor devem ser m&#243;veis | Microsoft Docs"
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
  - "CA1900"
  - "ValueTypeFieldsShouldBePortable"
helpviewer_keywords: 
  - "ValueTypeFieldsShouldBePortable"
  - "CA1900"
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1900: os campos de tipo de valor devem ser m&#243;veis
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ValueTypeFieldsShouldBePortable|  
|CheckId|CA1900|  
|Categoria|Microsoft.Portability|  
|Alteração Significativa|Interromper \- se o campo pode ser considerado fora do assembly.<br /><br /> Sem\-quebras \- se o campo não é visível fora do assembly.|  
  
## Causa  
 Esta regra verifica se as estruturas que são declaradas com layout explícito alinhem corretamente quando marshaling para código não gerenciado em sistemas operacionais de 64 bits.  IA\-64 não permite acessar de memória não alinhados e o processo falhará se essa violação não é fixa.  
  
## Descrição da Regra  
 As estruturas que têm explícito o layout que contém desalihnada causa dos campos falham em sistemas operacionais de 64 bits.  
  
## Como Corrigir Violações  
 Todos os campos que são menores que 8 bytes devem ter os deslocamentos que é um múltiplo de seu tamanho, e os campos que são 8 bytes ou mais devem ter os deslocamentos que é um múltiplo de 8.  Outra solução é usar `LayoutKind.Sequential` em vez de `LayoutKind.Explicit`, se razoável.  
  
## Quando Suprimir Alertas  
 Esse aviso será suprimido apenas se ocorrer um erro.