---
title: "Solução de problemas de análise de código | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: 5
author: erickson-doug
ms.author: douge
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: abd929692d247b4dab8a178f111362437e74ba3c
ms.lasthandoff: 02/22/2017

---
# <a name="troubleshooting-code-analysis-issues"></a>Solucionando problemas de análise do código
Este tópico contém informações de solução de problemas para os seguintes problemas de análise de código do Visual Studio.  
  
-   [Alterações em uma Regra do Visual Studio 2010 Não Afetarão as Versões Anteriores do Visual Studio](#ChildRuleSetChangesInPreviousVersions)  
  
##  <a name="ChildRuleSetChangesInPreviousVersions"></a> Alterações em uma Regra do Visual Studio 2010 Não Afetarão as Versões Anteriores do Visual Studio  
 Ao criar um conjunto de regras no [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] que contém um conjunto de regras filho, uma alteração no conjunto de regras filho pode não ser aplicada em execuções de análise de código em computadores que usam uma versão anterior do Visual Studio. Para resolver esse problema, é necessário forçar uma reescrita de conjunto de regras pai, que é o conjunto de regras que contém o conjunto de regras filho.  
  
1.  Abra o conjunto de regras pai no [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].  
  
2.  Faça uma alteração, como adicionar ou remover uma regra e salve o conjunto de regras.  
  
3.  Abra o conjunto de regras, reverta a alteração e, em seguida, salve o conjunto de regras novamente.  
  
## <a name="see-also"></a>Consulte também  
 [Analisando a Qualidade do Aplicativo](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [Analisando a Qualidade do Código Gerenciado](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Usando conjuntos de regras para agrupar regras de análise de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
