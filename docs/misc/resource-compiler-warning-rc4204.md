---
title: "RC4204 de aviso do compilador de recurso | Microsoft Docs"
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
  - "RC4204"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC4204"
ms.assetid: f9a83b3c-d696-4b38-9576-945d1f6d0063
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# RC4204 de aviso do compilador de recurso
Caracteres ASCII não é equivalente ao código de tecla virtual  
  
 Um literal de cadeia de caracteres foi usado para o código de tecla virtual em um acelerador de tipo VIRTKEY.  
  
 Esse aviso lhe permite continuar, mas lembre\-se de que as teclas de aceleração geradas podem não corresponder a cadeia de caracteres que você indicou. \(VIRTKEYs usar códigos de tecla diferentes de aceleradores de ASCII\).  
  
 Enquanto literais de cadeia de caracteres são sintaticamente válidos, você só pode garantir que você obtenha o Acelerador que desejar usando o **VK\_ \*** `#define` valores no Windows. h.