---
title: "&#39; &lt; baseinterfacename &gt;. &lt; nome &gt;&#39; de &#39;implementa &lt; derivedinterfacename &gt;&#39; j&#225; foi implementado pela classe base &#39;&lt; baseclassname &gt;&#39;. Reimplementa&#231;&#227;o de &lt; tipo &gt; assumida | Microsoft Docs"
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
  - "bc42014"
  - "vbc42014"
helpviewer_keywords: 
  - "BC42014"
ms.assetid: 95fff622-5d54-4ec8-90f0-477de1d58687
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39; &lt; baseinterfacename &gt;. &lt; nome &gt;&#39; de &#39;implementa &lt; derivedinterfacename &gt;&#39; j&#225; foi implementado pela classe base &#39;&lt; baseclassname &gt;&#39;. Reimplementa&#231;&#227;o de &lt; tipo &gt; assumida
Uma propriedade, procedimento ou evento em uma classe derivada usa um `Implements` cláusula especificando um membro de interface derivada que já é implementado na interface base na classe base.  
  
 O membro sendo implementado é definido pela interface base e herdado pela interface derivada. A classe base diretamente implementa a interface base. A classe derivada implementa a interface derivada e pode facilmente perder o fato de que a classe base já tenha implementado o membro.  
  
 Uma classe derivada pode reimplementar um membro de interface que é implementado pela classe base. Isso não é o mesmo que substituir a implementação da classe base. Para obter mais informações, consulte [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause).  
  
 Por padrão, essa mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC42014  
  
### Para corrigir este erro  
  
-   Se você pretende reimplementar o membro de interface, você não precisa realizar nenhuma ação. Código em sua classe derivada acessa o membro reimplementedo, a menos que você use o [MyBase \- excluir](http://msdn.microsoft.com/pt-br/52491d06-6451-4f6f-9aa6-8fab59bbc2b9) palavra\-chave para acessar a implementação da classe base.  
  
-   Se você não pretende reimplementar o membro de interface, remova o `Implements` cláusula da declaração de propriedade, procedimento ou evento.  
  
## Consulte também  
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)   
 [NÃO está em compilação: Palavra\-chave Implements e a instrução Implements](http://msdn.microsoft.com/pt-br/b96560f7-6413-480f-a1e2-f80253bab5be)