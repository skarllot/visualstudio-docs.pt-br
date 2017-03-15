---
title: "Solução de problemas de métricas de código | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 4
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
ms.openlocfilehash: 26dc2869ceb16e2c16a74ee52249777394fb666a
ms.lasthandoff: 02/22/2017

---
# <a name="troubleshooting-code-metrics-issues"></a>Solucionando problemas de métricas do código
Você pode encontrar alguns dos problemas a seguir ao coletar as métricas de código:  
  
-   [Alterações nos cálculos de complexidade de código do Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)  
  
##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a>Alterações nos cálculos de complexidade de código do Visual Studio 2010  
 Para a mesma função, a métrica de complexidade do código calculada em [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] pode ser diferente da métrica calculada por versões anteriores do [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] nas seguintes situações:  
  
-   A função contém um ou mais blocos catch. Nas versões anteriores do [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], os blocos catch não foram incluídos no cálculo. Em [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)], a complexidade de cada bloco catch é adicionada à complexidade da função.  
  
-   A função contém uma instrução de opção (selecione o caso em VB). Diferenças de compilador entre [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] e versões anteriores podem gerar códigos MSIL diferentes para algumas instruções de opção que contêm casos com falhas.  
  
## <a name="see-also"></a>Consulte também  
 [Medindo complexidade e facilidade de manutenção do código gerenciado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
