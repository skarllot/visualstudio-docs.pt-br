---
title: "&#39;&lt; procedure1 &gt;&#39; e &#39;&lt; procedure2 &gt;&#39; n&#227;o pode sobrecarregar porque diferem somente pelos par&#226;metros declarados &#39;ByRef&#39; ou &#39;ByVal&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42003"
  - "bc42003"
helpviewer_keywords: 
  - "BC42003"
ms.assetid: f058f1e0-64d2-4497-85fc-a58e16b0d805
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; procedure1 &gt;&#39; e &#39;&lt; procedure2 &gt;&#39; n&#227;o pode sobrecarregar porque diferem somente pelos par&#226;metros declarados &#39;ByRef&#39; ou &#39;ByVal&#39;
'\< procedure1 \>' e '\< procedure2 \>' não pode sobrecarregar porque diferem somente pelos parâmetros declarados ByRef nem ByVal. Sombras assumidas.  
  
 Duas declarações de procedimento especificam o mesmo nome e a lista de argumentos, e a única diferença está na especificação de `ByRef` ou `ByVal` para um ou mais dos argumentos. Versões sobrecarregadas de um procedimento devem ser diferentes entre si no número, ordem ou tipos de dados dos argumentos.  
  
 Essa mensagem é um aviso.`Shadows` será considerado por padrão. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC42003  
  
### Para corrigir este erro  
  
-   Se você pretende criar um conjunto de versões sobrecarregadas de um procedimento, verifique o número, ordem ou tipos de dados dos argumentos diferentes em cada versão. Além disso, adicione o `Overloads` palavra\-chave para cada declaração.  
  
-   Se você não pretende sobrecarregar um procedimento, altere o nome do procedimento em uma das declarações.  
  
## Consulte também  
 [Sobrecarga de procedimento](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)