---
title: "Aviso: encontrados conflitos entre diferentes vers&#245;es do mesmo assembly dependente | Microsoft Docs"
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
  - "ResolveAssemblyReference.SuggestedRedirects"
ms.assetid: fd14a789-bbdf-46c7-bcd3-9d3165adf96d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Aviso: encontrados conflitos entre diferentes vers&#245;es do mesmo assembly dependente
Esse aviso é exibido se o gráfico de dependência de seu projeto contém referências a versões diferentes do mesmo assembly.  
  
 Se você tiver um arquivo App. config, em seguida, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permite que você adicione um redirecionamento de associação para ele. Um redirecionamento de associação força todas as referências de assembly para redirecionar para a versão mais recente numerada do assembly. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] salva as informações de redirecionamento no App. config. Se você usar um redirecionamento de associação, esse aviso não aparecerá mais.  
  
 Se você decidir não adicionar um redirecionamento de associação, seu projeto continua a fazer referência a mesma versão do assembly como fazia antes. No entanto, esse aviso continuará aparecendo.  
  
### Para corrigir este erro  
  
-   Clique duas vezes no aviso e, em seguida, selecione "Sim" quando você receber o prompt, "Você deseja corrigir esses conflitos adicionando registros de redirecionamento de ligação no arquivo App. config?"