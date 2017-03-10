---
title: "CA1726: usar termos preferenciais | Microsoft Docs"
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
  - "UsePreferredTerms"
  - "CA1726"
helpviewer_keywords: 
  - "UsePreferredTerms"
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1726: usar termos preferenciais
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UsePreferredTerms|  
|CheckId|CA1726|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Interromper \- quando é acionado em assemblies<br /><br /> Sem\-quebras \- quando é acionado em parâmetros de tipo|  
  
## Causa  
 O nome de um identificador externamente visível inclui um termo para que uma alternativa, termo preferido existe.  Como alternativa, o nome inclui o sinalizador ou os sinalizadores de termos.  
  
## Descrição da Regra  
 Esta regra analisa um identificador em tokens.  Cada único token e cada combinação de token dupla contíguo são comparados aos termos que são criados na regra e substituído na seção de todos os dicionários personalizados.  A tabela a seguir mostra os termos que são criados na regra e nas alternativas preferidas.  
  
|Termo obsoleto|Termo preferencial|  
|--------------------|------------------------|  
|Arent|Não são|  
|Cancelado|Cancelado|  
|Cant|Não pode|  
|ComPlus|EnterpriseServices|  
|Não pôde|CouldNot|  
|Não fez|Não fez|  
|Não faz|DoesNot|  
|Não faça|DoNot|  
|Sinalizador ou sinalizadores|Não há nenhum termo de substituição.  Não use.|  
|Hadnt|HadNot|  
|Não tem|HasNot|  
|Havent|HaveNot|  
|Índices|Índices|  
|Não é|IsNot|  
|Logon|Logon|  
|Saída|Logoff|  
|Se|ShouldNot|  
|SignOn|SignIn|  
|De término|SignOut|  
|Não era|WasNot|  
|Werent|WereNot|  
|Não|Não|  
|Não|WouldNot|  
|Graváveis|Gravável|  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, substitua o termo com o termo de backup preferencial.  
  
## Quando Suprimir Alertas  
 Suprima um aviso desta regra somente se o nome de identificador é intencional e se relaciona especificamente ao termo original em vez de termos preferencial.  
  
## Regras Relacionadas  
 [Avisos de nomenclatura](../code-quality/naming-warnings.md)