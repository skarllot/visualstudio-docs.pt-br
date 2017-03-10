---
title: "Erros e avisos de Editar e Continuar (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.csharp.enc.error_4001"
  - "vs.csharp.enc.error_4034"
  - "vs.csharp.enc.error_4003"
  - "vs.csharp.enc.error_4026"
  - "vs.csharp.enc.error_4032"
  - "vs.csharp.enc.error_4017"
  - "vs.csharp.enc.error_4053"
  - "vs.csharp.enc.error_4024"
  - "vs.csharp.enc.error_4012"
  - "vs.csharp.enc.error_4066"
  - "vs.csharp.enc.error_4020"
  - "vs.csharp.enc.error_4008"
  - "vs.csharp.enc.error_4033"
  - "vs.csharp.enc.error_4014"
  - "vs.csharp.enc.error_4023"
  - "vs.csharp.enc.error_4011"
  - "vs.csharp.enc.error_4006"
  - "vs.csharp.enc.error_4059"
  - "vs.csharp.enc.error_4015"
  - "vs.csharp.enc.error_4018"
  - "vs.csharp.enc.error_4028"
  - "vs.csharp.enc.error_4013"
  - "vs.csharp.enc.error_4009"
  - "vs.csharp.enc.error_4021"
  - "vs.csharp.enc.error_4065"
  - "vs.csharp.enc.error_4029"
  - "vs.csharp.enc.error_4058"
  - "vs.csharp.enc.error_4019"
  - "vs.csharp.enc.error_4007"
  - "vs.csharp.enc.error_4052"
  - "vs.csharp.enc.error_4025"
  - "vs.csharp.enc.error_4055"
  - "vs.csharp.enc.error_4022"
  - "vs.csharp.enc.error_4002"
  - "vs.csharp.enc.error_4016"
  - "vs.csharp.enc.error_4043"
  - "vs.csharp.enc.error_4027"
  - "vs.csharp.enc.error_4054"
  - "vs.csharp.enc.error_4004"
  - "vs.csharp.enc.error_4010"
  - "vs.csharp.enc.error_4030"
  - "vs.csharp.enc.error_4005"
  - "vs.csharp.enc.error_4035"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Editar e continuar [c#], erros e avisos"
  - "erros [c#], depuração"
  - "erros [depurador], editar e continuar"
ms.assetid: c0e12b0a-8009-4a4a-979f-c804a91a5d9b
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "susanno"
manager: "douge"
---
# Erros e avisos de Editar e Continuar (C#)
Você fez uma edição para uma seção de código que não é permitido em Visual c\# editar e continuar.  
  
 [!INCLUDE[csharp_current_short](../misc/includes/csharp_current_short_md.md)] Editar e continuar permite parar a execução do programa no modo de interrupção, fazer alterações ao código em execução e, em seguida, continuar a execução do programa com as alterações recém\-inseridas.  
  
 Edição de código declarativo que afetam a estrutura pública de uma classe é proibidas em geral, e algumas edições que você pode fazer em um método, corpo da propriedade ou declarações privadas dentro de uma classe não são permitidas. Sempre que possível, editar e continuar marca o código que não pode ser editado como cinza claro e exibe uma mensagem de erro.  
  
 Para obter mais informações sobre as edições com suporte em Editar e continuar para [!INCLUDE[csharp_current_short](../misc/includes/csharp_current_short_md.md)], consulte [Alterações de código suportadas \(C\#\)](../debugger/supported-code-changes-csharp.md). Se você precisar de mais informações sobre um erro específico ou um aviso, você pode pesquisar ou postar no MSDN [Fórum do IDE do Visual C\#](http://go.microsoft.com/fwlink/?LinkId=214693).  
  
### Para corrigir este erro  
  
1.  Sobre o **Depurar** menu, escolha **Desfazer** para desfazer a alteração.  
  
     \- ou \-  
  
2.  Parar a sessão de depuração, faça as edições e inicie uma nova sessão de depuração.  
  
## Consulte também  
 [Editar e continuar \(Visual C\#\)](../debugger/edit-and-continue-visual-csharp.md)