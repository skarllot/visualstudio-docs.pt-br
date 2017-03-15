---
title: "Compilador CS1687 de aviso (n&#237;vel 1) | Microsoft Docs"
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
  - "CS1687"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1687"
ms.assetid: f65d184f-fa1d-45d7-be7d-f439f67bace4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS1687 de aviso (n&#237;vel 1)
Arquivo de origem excedeu o limite de 16.707.565 linhas representáveis no PDB, informações de depuração estarão incorretas  
  
 O PDB e depurador tem algumas limitações sobre o tamanho máximo que um arquivo pode ser. Se o arquivo de origem é muito grande, o depurador não se comportará corretamente além desse limite. O usuário deve ou não emitir informações de depuração para esse arquivo, possivelmente usando `#line hidden`, ou eles devem encontrar uma maneira de reduzir o arquivo, possivelmente, dividindo o arquivo em vários arquivos. Ele pode querer usar o `partial` palavra\-chave para dividir uma grande classe.