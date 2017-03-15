---
title: "&#39;Microsoft.VisualBasic.ComClassAttribute&#39; est&#225; especificado para classe &#39;&lt; classname &gt;&#39;, mas ele tem n&#227;o membros p&#250;blicos que podem ser expostos ao COM; Portanto, nenhuma interfaces COM s&#227;o geradas | Microsoft Docs"
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
  - "bc40011"
  - "vbc40011"
helpviewer_keywords: 
  - "BC40011"
ms.assetid: 39aed273-bf27-4667-8116-022c4dd8f3c5
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Microsoft.VisualBasic.ComClassAttribute&#39; est&#225; especificado para classe &#39;&lt; classname &gt;&#39;, mas ele tem n&#227;o membros p&#250;blicos que podem ser expostos ao COM; Portanto, nenhuma interfaces COM s&#227;o geradas
Uma classe usando um `COMClassAttribute` Bloco de atributo não define nenhum `Public` Propriedades ou métodos. Se uma classe deve ser exposta como um objeto COM, suas propriedades e métodos devem ser declarados com `Public` acesso.  
  
 A mensagem é um aviso por padrão. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC40011  
  
### Para corrigir este erro  
  
-   Adicionar o `Public` palavra\-chave para uma ou mais propriedades ou métodos na classe, ou remover o `COMClassAttribute` Bloco de atributo.  
  
## Consulte também  
 [NÃO está em compilação: Atributos usados no Visual Basic](http://msdn.microsoft.com/pt-br/22231318-8a40-49af-9245-e0aab723563b)   
 [NÃO está em compilação: Aplicação de atributos](http://msdn.microsoft.com/pt-br/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Público](/dotnet/visual-basic/language-reference/modifiers/public)   
 [Classe ComClassAttribute](http://msdn.microsoft.com/pt-br/5c2f0835-9210-47dc-bc59-5c1769953574)