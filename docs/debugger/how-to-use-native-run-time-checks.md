---
title: "Como usar verifica&#231;&#245;es de tempo de execu&#231;&#227;o nativas | Microsoft Docs"
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
  - "c.runtime.errorchecks"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Opção de compilador /O, Opção /RTC"
  - "Opção de compilador /RTC (C++), Opção de compilador /O"
  - "matrizes [Visual Studio], depuração"
  - "depurador, verificações em tempo de execução nativas"
  - "depurador, erros de tempo de execução"
  - "depurando matrizes"
  - "verificações em tempo de execução nativas"
  - "Opção de compilador O, Opção /RTC"
  - "opção de compilação otimizada"
  - "Opção de compilador  (RTC), Opção de compilador /O"
  - "verificações em tempo de execução"
  - "verificações em tempo de execução, nativa"
  - "erros de tempo de execução, depuração"
  - "erros de tempo de execução, verificações de erros"
  - "runtime_checks (pragma)"
  - "ponteiros de pilha"
  - "ponteiros de pilha, corrompimento"
  - "stack, corrompimento de ponteiro"
  - "variáveis [depurador], capturando dependências em variáveis locais não inicializadas"
  - "variáveis [depurador], perda de dados"
ms.assetid: dc7b2f1e-5ff6-42e0-89b3-dc9dead83ee1
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como usar verifica&#231;&#245;es de tempo de execu&#231;&#227;o nativas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

No Visual C\+\+, você pode usar nativo [runtime\_checks](/visual-cpp/preprocessor/runtime-checks) para capturar erros comuns de tempo de execução, como:  
  
-   Dano do ponteiro de pilha.  
  
-   Excesso de matrizes locais.  
  
-   Corrupção de pilha.  
  
-   Dependências em variáveis locais não inicializadas.  
  
-   Perda de dados em uma atribuição a uma variável mais curta.  
  
 Se você usar **\/RTC** com um otimizado \(**\/O**\) criar um erro de compilação acontece. Se você usar um `runtime_checks` pragma em uma compilação otimizada, o pragma não terá efeito.  
  
 Quando você depurar um programa com verificações de tempo de execução ativadas, a ação padrão é para o programa parar e interromper o depurador quando ocorre um erro de tempo de execução. Você pode alterar esse comportamento padrão para qualquer verificação de tempo de execução. Para obter mais informações, consulte [Gerenciando exceções com o depurador](../debugger/managing-exceptions-with-the-debugger.md).  
  
 Os procedimentos a seguir descrevem como ativar verificações nativas de tempo de execução em uma compilação de depuração e como modificar o comportamento de verificações nativas de tempo de execução.  
  
 Outros tópicos nesta seção fornecem informações sobre:  
  
-   [Personalizar o tempo de execução verifica com a biblioteca de tempo de execução do C](../debugger/native-run-time-checks-customization.md)  
  
-   [Usar o tempo de execução verifica sem a biblioteca de tempo de execução do C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)  
  
### Para ativar verificações nativas de tempo de execução em uma compilação de depuração  
  
-   Use o **\/RTC** opção e vincule com a versão de depuração de uma biblioteca de tempo de execução do C \(\/ MDd, por exemplo\).  
  
### Para modificar o comportamento de verificações nativas de tempo de execução  
  
-   Use o `runtime_checks` pragma.  
  
## Consulte também  
 [Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [runtime\_checks](/visual-cpp/preprocessor/runtime-checks)   
 [Verificação de erros de tempo de execução](/visual-cpp/c-runtime-library/run-time-error-checking)