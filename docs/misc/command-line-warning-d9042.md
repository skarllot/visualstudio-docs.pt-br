---
title: "Linha de comando aviso D9042 | Microsoft Docs"
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
  - "D9042"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D9042"
ms.assetid: d710693b-e422-40b2-b2dd-79e1b163b9e6
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Linha de comando aviso D9042
valor inválido 'value' para 'opção'; Supondo que o 'valor'; Avisos da análise de código não estão disponíveis nesta edição do compilador  
  
 Um número de aviso de análise de código foi adicionado para o **\/wd**, **\/we**, **\/wo**, ou **\/wl** opção de linha de comando e o **\/analyze** opção de linha de comando foi especificada em uma plataforma que não oferece suporte a análise de código. Para corrigir esse aviso, alterne para o x86 versão do Visual Studio Team System ou remover o **\/analyze** opção de linha de comando.  
  
## Exemplo  
 O exemplo de linha de comando a seguir gera o aviso D9042 em x64 ou Itanium sistema:  
  
```  
cl /EHsc /LD /wd6001 /analyze filename.cpp  
```  
  
 Para corrigir esse aviso, alterne para o x86 versão do Visual Studio Team System ou remover o **\/analyze** e **\/wd6001** Opções de linha de comando.  
  
## Consulte também  
 [Erros de linha de comando D8000 até D9999](/visual-cpp/error-messages/tool-errors/command-line-errors-d8000-through-d9999)   
 [Opções do compilador](/visual-cpp/build/reference/compiler-options)