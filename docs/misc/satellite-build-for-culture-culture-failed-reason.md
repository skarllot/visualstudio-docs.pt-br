---
title: "Falha na compila&#231;&#227;o sat&#233;lite para a cultura &#39;cultura&#39;. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.satellite_build_failed"
ms.assetid: c97c589f-cf4d-4f6b-941a-7526a1091fce
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Falha na compila&#231;&#227;o sat&#233;lite para a cultura &#39;cultura&#39;. &lt;reason&gt;
Não foi possível criar um assembly satélite para uma determinada cultura.  Esse erro fará com que o processo de compilação falhe.  
  
 Este erro pode ocorrer por dois motivos:  
  
1.  ALINK.EXE não está instalado no sistema.  
  
2.  ALINK.EXE falha mas não retornou nenhuma informação de erro estendido.  
  
 **Para corrigir este erro**  
  
-   Reinstale o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou apenas o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
-   Quando \<reason\> é informada como "O vinculador de assembly não pôde ser iniciado.  O arquivo existe,"Esvaziar a pasta Temp gerados os arquivos \(por exemplo, C:\\Documents and Settings \\ \<user\> \\Local Settings\\Temp\).  
  
## Consulte também  
 [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)