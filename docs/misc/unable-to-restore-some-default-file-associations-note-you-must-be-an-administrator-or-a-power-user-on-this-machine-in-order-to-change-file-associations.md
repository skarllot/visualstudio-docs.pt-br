---
title: "N&#227;o &#233; poss&#237;vel restaurar algumas associa&#231;&#245;es de arquivo padr&#227;o. Observa&#231;&#227;o: voc&#234; deve ser um administrador ou usu&#225;rio avan&#231;ado neste computador para alterar associa&#231;&#245;es de arquivo. | Microsoft Docs"
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
  - "VS.Message.0x00006A85"
  - "VS_E_RESTOREFILEASSOCS"
ms.assetid: 449c5608-83e3-4ddd-91f1-1061916995b3
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# N&#227;o &#233; poss&#237;vel restaurar algumas associa&#231;&#245;es de arquivo padr&#227;o. Observa&#231;&#227;o: voc&#234; deve ser um administrador ou usu&#225;rio avan&#231;ado neste computador para alterar associa&#231;&#245;es de arquivo.
Esse erro ocorre quando o \/AssociateFiles de opção de linha de comando devenv é usado, mas os direitos de usuário atuais não permitem o acesso à seção HKEY\_CLASSES\_ROOT do registro. Quando você executar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] em [!INCLUDE[wiprlhext](../misc/includes/wiprlhext_md.md)], você deve executar devenv como um administrador para usar a opção \/AssociateFiles \(devenv.exe\).  
  
### Para corrigir este erro  
  
-   Alterar credenciais administrativas e tente novamente.  
  
## Consulte também  
 [User Rights and Visual Studio](http://msdn.microsoft.com/pt-br/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Opções de linha de comando do desenvolvedor](../ide/reference/devenv-command-line-switches.md)