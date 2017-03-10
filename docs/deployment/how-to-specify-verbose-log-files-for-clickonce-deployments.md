---
title: "Como especificar arquivos de log detalhados para implanta&#231;&#245;es do ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "implantação ClickOnce, log"
  - "logs, implantação ClickOnce"
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como especificar arquivos de log detalhados para implanta&#231;&#245;es do ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]mantém os arquivos de log de atividade em todas as implantações.  Esses logs documentam detalhes pertencentes à instalação, inicializando, atualização e desinstalação de um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação.  Para aumentar o detalhe que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] gravações para esses arquivos de log, use o Editor do registro \(**regedit.exe**\) para especificar o nível de verbosidade.  
  
> [!CAUTION]
>  Se você usar o Editor do Registro incorretamente, você pode causar problemas sérios que podem exigir a reinstalação do sistema operacional.  Use o Editor do Registro e assuma os riscos.  
  
 O procedimento a seguir descreve como especificar o nível de verbosidade de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] arquivos de log para o usuário atual.  Para reduzir o nível de verbosidade, remova esse valor do registro.  
  
### Para especificar os arquivos de log detalhado  
  
1.  Abra **Regedit.exe**.  
  
2.  Navegue até o nó  `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Se necessário, crie um novo valor de seqüência de caracteres denominado  `LogVerbosityLevel`.  
  
4.  Definir o  `LogVerbosityLevel` valor para  `1`.  
  
## Consulte também  
 [Solução de problemas de implantações do ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)