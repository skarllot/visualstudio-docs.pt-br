---
title: "&lt; tipo &gt; &#39;&lt; methodname &gt;&#39; est&#225; em conflito com outros membros do mesmo nome na hierarquia de heran&#231;a e, portanto deve ser declarado como &#39;Shadows&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42000"
  - "bc42000"
helpviewer_keywords: 
  - "BC42000"
ms.assetid: 3081635f-99a9-4e90-997f-82251144d80f
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt; tipo &gt; &#39;&lt; methodname &gt;&#39; est&#225; em conflito com outros membros do mesmo nome na hierarquia de heran&#231;a e, portanto deve ser declarado como &#39;Shadows&#39;
Uma interface herdando de duas ou mais interfaces define um procedimento com o mesmo nome que um procedimento já definido em mais de uma das interfaces base. O procedimento nesta interface deve sombrear um dos procedimentos interface base.  
  
 Essa mensagem é um aviso.`Shadows` será considerado por padrão. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC42000  
  
### Para corrigir este erro  
  
-   Se você pretende ocultar um dos procedimentos interface base, adicione a `Shadows` palavra\-chave para a nova declaração de procedimento.  
  
-   Se você não pretende ocultar qualquer um dos procedimentos interface base, altere o nome do novo procedimento.  
  
## Consulte também  
 [Sombras](/dotnet/visual-basic/language-reference/modifiers/shadows)   
 [Sombreamento no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/shadowing)