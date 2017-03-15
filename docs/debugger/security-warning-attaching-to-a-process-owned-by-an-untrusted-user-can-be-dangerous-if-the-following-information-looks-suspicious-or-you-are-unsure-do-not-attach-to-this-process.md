---
title: "Aviso de seguran&#231;a: anexar a um processo de propriedade de um usu&#225;rio n&#227;o confi&#225;vel pode ser perigoso. Caso as informa&#231;&#245;es a seguir pare&#231;am suspeitas ou voc&#234; n&#227;o tenha certeza, n&#227;o anexe a esse processo | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.attachsecuritywarning"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Aviso de seguran&#231;a: anexar a um processo de propriedade de um usu&#225;rio n&#227;o confi&#225;vel pode ser perigoso. Caso as informa&#231;&#245;es a seguir pare&#231;am suspeitas ou voc&#234; n&#227;o tenha certeza, n&#227;o anexe a esse processo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Essa caixa de diálogo de aviso é exibida quando você anexa a um processo que contém o código parcialmente confiável ou seja de propriedade de um usuário não confiável imediatamente antes de ocorrer a anexação.  Um processo não confiável que contém o código mal\-intencionado tem o potencial de danificar o computador que faz a depuração.  Se você tiver razão para desconfiar do processo, deverá clicar em **Cancelar** para evitar a depuração.  
  
 Para suprimir esse aviso ao depurar um cenário legítimo, feche o Visual Studio e defina o valor dessa chave de Registro para 1: `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning` e, em seguida, reinicialize o Visual Studio.  Depois de concluir a depurar do cenário, redefina o valor como 0 e reinicie o Visual Studio.  
  
 Os “Usuários confiáveis” incluem você, mais um conjunto de usuários padrão que são definidos normalmente em computadores que têm o .NET Framework instalado, por exemplo, `aspnet`, `localsystem`, `networkservice` e `localservice`.  
  
## Lista UIElement  
 Nome  
 Nome do assembly solicitado para depurar  
  
 User  
 Usuário atual  
  
 Attach  
 Pressione para continuar a depurar anexando  
  
 Não anexar  
 Não anexar ao processo  
  
## Consulte também  
 [Anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Segurança do depurador](../debugger/debugger-security.md)