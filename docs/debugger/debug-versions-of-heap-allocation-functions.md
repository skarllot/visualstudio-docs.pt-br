---
title: "Vers&#245;es de depura&#231;&#227;o das fun&#231;&#245;es de aloca&#231;&#227;o da pilha | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.crt"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Macro _CRTDBG_MAP_ALLOC"
  - "Função _malloc_dbg"
  - "depuração [CRT], funções de alocação de heap"
  - "depurando perdas de memória, Funções de biblioteca de depuração CRT"
  - "alocação de heap, depurar"
  - "Função malloc"
  - "perdas de memória, Funções de biblioteca de depuração CRT"
ms.assetid: 91748bdc-f4cd-4d8b-ab98-0493dab7ed0d
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vers&#245;es de depura&#231;&#227;o das fun&#231;&#245;es de aloca&#231;&#227;o da pilha
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A biblioteca em tempo de execução C contém versões especiais de depuração das funções de alocação do heap.  Essas funções têm os mesmos nomes que as versões com o \_dbg anexado a elas.  Este tópico descreve as diferenças entre a versão de lançamento de uma função CRT e a versão de \_dbg, usando `malloc` e `_malloc_dbg` como exemplos.  
  
 Quando [\_DEBUG](/visual-cpp/c-runtime-library/debug) estiver definido, o CRT mapeará todas as chamadas de [malloc](/visual-cpp/c-runtime-library/reference/malloc) para [\_malloc\_dbg](/visual-cpp/c-runtime-library/reference/malloc-dbg).  Consequentemente, você não precisa reescrever seu código usando `_malloc_dbg` em vez de `malloc` para receber os benefícios durante a depuração.  
  
 No entanto, talvez você queira chamar explicitamente `_malloc_dbg`.  Chamar `_malloc_dbg` explicitamente tem alguns benefícios adicionais:  
  
-   Acompanhar alocações de tipo `_CLIENT_BLOCK`.  
  
-   Armazenar o arquivo de origem e o número da linha em que a solicitação de alocação ocorreu.  
  
 Se você não quiser converter suas chamadas de `malloc` para `_malloc_dbg`, poderá obter informações do arquivo de origem definindo [\_CRTDBG\_MAP\_ALLOC](/visual-cpp/c-runtime-library/crtdbg-map-alloc), que faz o pré\-processador mapear diretamente todas as chamadas para `malloc` para `_malloc_dbg` em vez de confiar em um wrapper em torno de `malloc`.  
  
 Para controlar os tipos separados de alocações em blocos do cliente, você deverá chamar `_malloc_dbg` diretamente e definir o parâmetro `blockType` como `_CLIENT_BLOCK`.  
  
 Quando \_DEBUG não estiver definido, as chamadas para `malloc` não serão perturbadas, as chamadas para `_malloc_dbg` serão resolvidas para `malloc`, a definição de [\_CRTDBG\_MAP\_ALLOC](/visual-cpp/c-runtime-library/crtdbg-map-alloc) será ignorada e as informações do arquivo de origem que pertencem à solicitação de alocação não será fornecida.  Como `malloc` não tem um parâmetro de tipo de bloco, as solicitações para tipos de `_CLIENT_BLOCK` são tratadas como alocações padrão.  
  
## Consulte também  
 [Técnicas de depuração CRT](../debugger/crt-debugging-techniques.md)