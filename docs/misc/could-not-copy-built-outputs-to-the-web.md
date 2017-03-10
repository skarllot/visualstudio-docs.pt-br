---
title: "N&#227;o foi poss&#237;vel copiar sa&#237;das constru&#237;das para a Web | Microsoft Docs"
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
  - "vs.tasklisterror.cantcopyoutputstoweb"
ms.assetid: 59cf714b-cf7d-4df9-81ae-d3254969d5bc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# N&#227;o foi poss&#237;vel copiar sa&#237;das constru&#237;das para a Web
O sistema do projeto não pôde copiar um ou mais arquivos de saída \(por exemplo, a DLL interna, PDB ou assemblies satélite\) para o servidor Web de compilação.  
  
 Esse erro indica que um ou mais arquivos de saída de compilação não foram copiados para o servidor Web.  
  
 Esse erro normalmente ocorre se um arquivo de saída da compilação está bloqueado ou como somente leitura no servidor. Se um arquivo está bloqueado no servidor, isso indicará que o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] em tempo de execução não copiou corretamente os assemblies, satélites ou símbolos de depuração que estão atualmente no servidor.  
  
 Também é possível que o servidor pode estar sem espaço em disco ou se problemas de rede podem estar impedindo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de carregar os arquivos na Web.  
  
### Para corrigir este erro  
  
1.  Verifique se há espaço em disco.  
  
2.  Se um arquivo estiver bloqueado, em seguida, reinicie o servidor Web para liberar [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]do bloqueio de arquivos afetados.  
  
## Consulte também  
 [PDB Files](http://msdn.microsoft.com/pt-br/1761c84e-8c2c-4632-9649-b5f99964ed3f)