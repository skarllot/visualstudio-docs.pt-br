---
title: "Avisos de portabilidade | Microsoft Docs"
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
  - "vs.codeanalysis.PortabilityRules"
helpviewer_keywords: 
  - "avisos de portabilidade"
  - "avisos da análise de código gerenciado, avisos de portabilidade"
  - "avisos de portabilidade"
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Avisos de portabilidade
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Os avisos da portabilidade dão suporte a portabilidade para sistemas operacionais diferentes.  
  
## Nesta seção  
  
|Regra|Descrição|  
|-----------|---------------|  
|[CA1900: os campos de tipo de valor devem ser móveis](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Esta regra verifica se as estruturas que é declarado usando um atributo explícito de layout alinhem corretamente quando marshaling para código não gerenciado em sistemas operacionais de 64 bits.|  
|[CA1901: as declarações de P\/Invoke devem ser portáteis](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Esta regra avalia o tamanho de cada parâmetro e o valor de retorno de um P\/Invoke, e verificar se seu tamanho está correto quando marshaling para código não gerenciado em sistemas operacionais de 32 bits e de 64 bits.|  
|[CA1903: usar apenas a API da estrutura de destino](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Um membro ou um tipo está usando um membro ou um tipo que foram introduzidos em um pacote de serviços que não é incluído com a estrutura de destino do projeto.|