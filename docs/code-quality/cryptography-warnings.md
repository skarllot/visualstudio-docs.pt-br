---
title: "Avisos de criptografia | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Avisos de criptografia
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Avisos de criptografia oferecem suporte a bibliotecas e aplicativos com o uso correto de criptografia mais seguro. Esses avisos ajudam a evitar falhas de segurança em seu programa. Se você desabilitar um desses avisos, você deve marcar claramente a razão no código e também informar o Diretor de segurança designado para seu projeto de desenvolvimento.  
  
|Regra|Descrição|  
|-----------|---------------|  
|[CA5350: Não Use algoritmos criptográficos fracos](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|Algoritmos de criptografia fraca e funções de hash são usadas atualmente por uma série de motivos, mas eles não devem ser usados para garantir a confidencialidade ou a integridade dos dados que eles protegem. Essa regra dispara quando encontra algoritmos TripleDES, SHA1 ou RIPEMD160 no código.|  
|[CA5351 Não Use algoritmos criptográficos quebrados](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|Divididos criptográfico algoritmos não são considerados seguros e seu uso deve ser altamente desencorajado. Essa regra dispara quando encontra o algoritmo de hash MD5 ou DES ou RC2 algoritmos de criptografia no código.|