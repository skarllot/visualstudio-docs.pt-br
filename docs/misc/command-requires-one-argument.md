---
title: "O comando requer um argumento. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_INCORRECTPARAMCOUNT1"
  - "vs.message.0x800A00C3"
ms.assetid: b4d98e6d-6970-42fb-b1de-43f2e952fb9d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# O comando requer um argumento.
Esse erro geralmente ocorre quando não há informações suficientes para o comando foi inseridas ou porque foi usada uma combinação incorreta de argumentos.  
  
 Por exemplo, se `alias` `/delete sample1 sample2` foi inserido para o `alias` de comando, esse erro será exibido como alias `/delete` só pode ter um nome de alias, não dois.  Nomes de alias não contêm espaços, portanto, a **Localizar\/comando** caixa e **comando** janela interpretar `sample1 sample2` como dois nomes de alias diferente.  
  
### Para corrigir este erro  
  
1.  Verifique a documentação para obter a sintaxe correta para o comando e tente novamente.  
  
## Consulte também  
 [Comandos do Visual Studio](../ide/reference/visual-studio-commands.md)