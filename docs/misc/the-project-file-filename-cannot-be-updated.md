---
title: "O arquivo de projeto &#39;&lt;filename&gt;&#39; n&#227;o pode ser atualizado. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.UpgradeErrors"
ms.assetid: ecd1e161-c51c-4aaa-ab80-8fc443bdad81
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# O arquivo de projeto &#39;&lt;filename&gt;&#39; n&#227;o pode ser atualizado.
Você está tentando abrir um projeto criado em uma versão anterior de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  O projeto deve ser atualizado para o formato atual, mas não pode ser atualizado ou porque o arquivo de projeto específico \(.vbproj\) é marcado como somente leitura ou o arquivo está sob o controle de código fonte e atualmente é bloqueado por outro usuário.  
  
### Para corrigir este erro  
  
1.  Em o Arquivo Explorer, localize o arquivo de projeto especificado.  
  
2.  Em o menu de **Arquivo** , escolha **Propriedades**.  
  
3.  Em a caixa de diálogo de **Propriedades** , desmarque o atributo de **Somente leitura** .  
  
 Se o arquivo está sob o controle de código fonte e é bloqueado por outro usuário, espere até o arquivo está disponível e verificar\-l check\-out localmente.  
  
## Consulte também  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/pt-br/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)