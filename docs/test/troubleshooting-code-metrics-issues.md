---
title: "Solucionando problemas de m&#233;tricas do c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 4
caps.handback.revision: 4
author: "erickson-doug"
ms.author: "douge"
manager: "douge"
---
# Solucionando problemas de m&#233;tricas do c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode encontrar qualquer um dos seguintes problemas quando a coleta a métrica de código:  
  
-   [Alterações em cálculos da complexidade do código do Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)  
  
##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a> Alterações em cálculos da complexidade do código do Visual Studio 2010  
 Para a mesma função, a métrica da complexidade do código calculado em [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] pode ser diferente da métrica calculado por versões anteriores de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] para as seguintes situações:  
  
-   A função contém um ou mais blocos de try\/catch.  Em versões anteriores de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], os blocos de try\/catch não foram incluídos no cálculo.  Em [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)], a complexidade de cada bloco de captura é adicionada à complexidade da função.  
  
-   A função contém uma instrução switch \(selecionar casos em VB\).  As diferenças do compilador entre [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] e versões anteriores podem gerar o código diferente de MSIL para algumas instruções de alternância que contêm queda\- por meio dos casos.  
  
## Consulte também  
 [Medindo complexidade e facilidade de manutenção do código gerenciado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)