---
title: "&lt; tipo &gt; &#39;&lt; typename &gt;&#39; sombreia um m&#233;todo substitu&#237;vel na classe base | Microsoft Docs"
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
  - "vbc40005"
  - "bc40005"
helpviewer_keywords: 
  - "BC40005"
ms.assetid: 1dadda7f-1d26-4ae8-a668-9f69d55ceb50
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt; tipo &gt; &#39;&lt; typename &gt;&#39; sombreia um m&#233;todo substitu&#237;vel na classe base
\< tipo \> '\< typename \>' sombreia um método substituível na classe base. Se você quiser substituir o método base, esse método deve ser declarado 'Overrides'.  
  
 Um elemento de programação é declarado com o mesmo nome que um procedimento ou propriedade substituível definido na classe base. Nessa situação, o elemento nessa classe deve sombrear o elemento da classe base.  
  
 Por padrão, essa mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC40005  
  
### Para corrigir este erro  
  
-   Se você pretende substituir o procedimento base, adicione a `Overrides` palavra\-chave para a declaração.  
  
-   Se você pretende sombrear o procedimento base, adicione a `Shadows` palavra\-chave para a declaração.  
  
-   Se você não pretende nem substituir nem sombrear, altere o nome do elemento que está sendo declarado.  
  
## Consulte também  
 [NÃO está em compilação: Substituindo métodos e propriedades](http://msdn.microsoft.com/pt-br/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Sombreamento no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/shadowing)   
 [Substituições](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [Sombras](/dotnet/visual-basic/language-reference/modifiers/shadows)