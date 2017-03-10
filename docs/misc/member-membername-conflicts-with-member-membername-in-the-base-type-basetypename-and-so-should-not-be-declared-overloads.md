---
title: "Membro &#39;&lt; nome do membro &gt;&#39; est&#225; em conflito com o membro &#39;&lt; nome do membro &gt;&#39; no tipo base &#39;&lt; NomeDoTipoBase &gt;&#39; e, portanto n&#227;o deve ser declarado &#39;Overloads&#39; | Microsoft Docs"
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
  - "bc40021"
  - "vbc40021"
helpviewer_keywords: 
  - "BC40021"
ms.assetid: 2ec72726-ab0e-4545-9c1e-2409eb54482e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Membro &#39;&lt; nome do membro &gt;&#39; est&#225; em conflito com o membro &#39;&lt; nome do membro &gt;&#39; no tipo base &#39;&lt; NomeDoTipoBase &gt;&#39; e, portanto n&#227;o deve ser declarado &#39;Overloads&#39;
Uma propriedade ou um procedimento usa o [Sobrecargas](/dotnet/visual-basic/language-reference/modifiers/overloads) palavra\-chave para declarar novamente uma propriedade existente ou um procedimento com o mesmo nome, mas a propriedade existente ou o procedimento está na classe base.  
  
 Sobrecarga é usado para definir várias versões de uma propriedade ou procedimento todas na mesma classe. Você não pode definir uma versão adicional de um membro da classe base, a menos que o membro da classe base já especifique [Sobrecargas](/dotnet/visual-basic/language-reference/modifiers/overloads).  
  
 Por padrão, essa mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC40021  
  
### Para corrigir este erro  
  
-   Se você pretende definir uma versão adicional do membro da classe base e tem acesso ao código\-fonte da classe base, adicione a [Sobrecargas](/dotnet/visual-basic/language-reference/modifiers/overloads) palavra\-chave para a definição da classe base.  
  
-   Se você não tiver acesso ao código\-fonte da classe base, você não pode sobrecarregar o membro em uma classe derivada. Remover o `Overloads` palavra\-chave.  
  
-   Se você deseja substituir o membro da classe base em vez de definir uma versão adicional dele, use o [Substituições](/dotnet/visual-basic/language-reference/modifiers/overrides) palavra\-chave em vez de `Overloads`.  
  
-   Se você desejar ocultar o membro da classe base com um novo membro na classe derivada, use o [Sombras](/dotnet/visual-basic/language-reference/modifiers/shadows) palavra\-chave em vez de `Overloads`.  
  
## Consulte também  
 [Sobrecarga de procedimento](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Noções básicas de herança](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)