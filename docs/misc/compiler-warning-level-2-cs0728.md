---
title: "Compilador CS0728 de aviso (n&#237;vel 2) | Microsoft Docs"
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
  - "CS0728"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0728"
ms.assetid: ad6d860d-bac4-48f3-9eab-1efd2b6de6c0
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0728 de aviso (n&#237;vel 2)
Atribuição possivelmente incorreta ao local 'variável' que é o argumento para uma instrução using ou lock.  A chamada de Dispose ou desbloqueando será acontecerá no valor original do local.  
  
 Há várias situações em que `using` ou `lock` blocos resultará em uma perda temporária de recursos. Aqui está um exemplo:  
  
 `thisType f = null;`  
  
 `using (f)`  
  
 `{`  
  
 `f = new thisType();`  
  
 `...`  
  
 `}`  
  
 Nesse caso, valor original, como null, da variável `thisType` serão descartados quando o `using` bloco termina a execução, mas o `thisType` objeto criado dentro do bloco não será, embora, eventualmente, obterão coletado como lixo.  
  
 Para resolver esse erro, use o seguinte formato:  
  
 `using (thisType f = new thisType())`  
  
 `{`  
  
 `...`  
  
 `}`  
  
 Nesse caso, o recém\-alocada `thisType` objeto será descartado.  
  
## Exemplo  
 O código a seguir irá gerar um aviso CS0728.  
  
```  
// CS0728.cs using System; public class ValidBase : IDisposable { public void Dispose() {  } } public class Logger { public static void dummy() { ValidBase vb = null; using (vb) { vb = null;  // CS0728 } vb = null; } public static void Main() { } }  
```