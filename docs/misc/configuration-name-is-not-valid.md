---
title: "O nome da configura&#231;&#227;o n&#227;o &#233; v&#225;lido. | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_INVALID_CFG_NAME"
  - "vs.message.0x800A00B7"
ms.assetid: aa439582-0863-41d3-825c-7c45b1773cde
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# O nome da configura&#231;&#227;o n&#227;o &#233; v&#225;lido.
Esse erro geralmente ocorre quando o nome digitado para a configuração de compilação inclui caracteres inválidos, como \<\>,, &#124;, e \*.  
  
### Para corrigir este erro  
  
1.  Verifique se o nome da configuração não contêm os seguintes caracteres: \<\>,, \*, &#124;,:, \\, \/, &, %, ",., \#,?, ou um espaço à esquerda ou à direita. Além disso, o nome da configuração não é possível usar nomes reservados do Windows ou do DOS, como "nul", "aux", "con',"com \#","lpt \#"e assim por diante.  
  
2.  Digite o nome novamente.  
  
## Consulte também  
 [Compilando aplicativos no Visual Studio](../ide/compiling-and-building-in-visual-studio.md)