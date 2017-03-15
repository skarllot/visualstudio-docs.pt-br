---
title: "Uso da biblioteca de depura&#231;&#227;o CRT | Microsoft Docs"
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
  - "c.debug.runtime"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Opção de vinculador /DEBUG [C++]"
  - "Função de compilador /LDd [C++]"
  - "Opção de compilador /MDd (C++)"
  - "Opção de compilador /MTd (C++)"
  - "arquivo crtdbg.h"
  - "biblioteca de depuração"
  - "Opção de vinculador DEBUG [C++]"
  - "depuração [CRT], Biblioteca de depuração CRT"
  - "Função de compilador LDd [C++]"
  - "bibliotecas, Biblioteca de depuração CRT"
  - "Opção de compilador MDd [C++]"
  - "Opção de compilador MTd [C++]"
ms.assetid: 464de16b-4215-4787-9bfa-921aaff9d9f4
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Uso da biblioteca de depura&#231;&#227;o CRT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A biblioteca em tempo de execução C fornece amplo suporte à depuração.  Para usar uma das bibliotecas de depuração de CRT, você deve estabelecer um vínculo com [\/DEBUG](/visual-cpp/build/reference/debug-generate-debug-info) e compilar com **\/MDd**, **\/MTd** ou **\/LDd**.  
  
## Comentários  
 As definições e macros principais de depuração de CRT podem ser encontradas no arquivo de cabeçalho CRTDBG.h.  
  
 As funções nas bibliotecas de depuração de CRT são criadas com informações de depuração \([\/Z7, \/Zd, \/Zi, \/ZI \(formato das informações de depuração\)](/visual-cpp/build/reference/z7-zi-zi-debug-information-format)\) e sem otimização.  Algumas funções contêm asserções para verificar os parâmetros passados a elas, e o código\-fonte será fornecido.  Com esse código\-fonte, você pode acessar funções de CRT para confirmar se as funções estão funcionando conforme o esperado e verificar se há parâmetros incorretos ou estados de memória. \(Qualquer tecnologia de CRT é proprietária e não fornece código\-fonte para tratamento de exceções, ponto flutuante e algumas outras rotinas.\)  
  
 Quando você instalar o Visual C\+\+, terá a opção de instalar o código\-fonte da biblioteca em tempo de execução C no disco rígido.  Se você não instalar o código\-fonte, precisará do CD\-ROM para acessar as funções de CRT.  
  
 Para obter mais informações sobre as várias bibliotecas em tempo de execução que você pode usar, consulte [Bibliotecas em tempo de execução C](/visual-cpp/c-runtime-library/crt-library-features).  
  
## Consulte também  
 [Técnicas de depuração CRT](../debugger/crt-debugging-techniques.md)   
 [\/MD, \/MT, \/LD \(usar biblioteca em tempo de execução\)](/visual-cpp/build/reference/md-mt-ld-use-run-time-library)