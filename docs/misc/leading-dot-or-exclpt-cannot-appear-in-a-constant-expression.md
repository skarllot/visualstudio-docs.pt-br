---
title: "&#192; esquerda &#39;. &#39;ou&#39;!&#39; n&#227;o pode aparecer em uma express&#227;o constante | Microsoft Docs"
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
  - "vbc30995"
  - "bc30995"
helpviewer_keywords: 
  - "BC30995"
ms.assetid: eed62684-66db-4fdb-9da7-f1407a55b172
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#192; esquerda &#39;. &#39;ou&#39;!&#39; n&#227;o pode aparecer em uma express&#227;o constante
Acesso de membro \(.\) e acesso de membro de dicionário \(\!\) requerem uma expressão especificando o elemento que contém o membro na maioria das vezes, incluindo expressões constantes. A declaração a seguir não é válida.  
  
```  
' Not valid. Const c As String = .name  
```  
  
 **ID do erro:** BC30995  
  
### Para corrigir este erro  
  
-   Especifique a instância que contém o membro que você deseja acessar.  
  
## Consulte também  
 [Inicializadores de objeto: tipos nomeados e anônimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Como: declarar uma instância de um tipo anônimo \(Visual Basic\)](http://msdn.microsoft.com/pt-br/119f616c-9bcd-4731-ac00-4285be5959f7)   
 [Instrução Const](/dotnet/visual-basic/language-reference/statements/const-statement)