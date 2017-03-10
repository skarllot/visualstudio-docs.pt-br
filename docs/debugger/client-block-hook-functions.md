---
title: "Fun&#231;&#245;es de gancho do bloco de clientes | Microsoft Docs"
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
  - "vs.debug.hooks"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Função _CrtSetDumpClient"
  - "blocos de cliente, funções de gancho"
  - "blocos de cliente, validando e relatando dados"
  - "depurando [C++], funções de gancho"
  - "ganchos, bloco de cliente"
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Fun&#231;&#245;es de gancho do bloco de clientes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se você quiser validar ou reportar o conteúdo dos dados armazenados em blocos `_CLIENT_BLOCK`, poderá escrever uma função especificamente para essa finalidade.  A função que você escreve deverá ter um protótipo semelhante ao seguinte, conforme definido em CRTDBG.H:  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 Em outras palavras, sua função de gancho deve aceitar um ponteiro **void** para o início do bloco de alocação, junto com um valor do tipo **size\_t** que indica o tamanho da alocação, e retornar `void`.  Além disso, o conteúdo depende de você.  
  
 Quando você tiver instalado a função de gancho usando [\_CrtSetDumpClient](/visual-cpp/c-runtime-library/reference/crtsetdumpclient), ela será chamada sempre que um bloco `_CLIENT_BLOCK` for despejado.  Você pode usar [\_CrtReportBlockType](/visual-cpp/c-runtime-library/reference/crtreportblocktype) para obter informações sobre o tipo ou subtipo de blocos despejados.  
  
 O ponteiro para sua função que você passa para `_CrtSetDumpClient` é do tipo **\_CRT\_DUMP\_CLIENT**, conforme definido em CRTDBG.H:  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## Consulte também  
 [Gravação da função de gancho de depuração](../debugger/debug-hook-function-writing.md)   
 [crt\_dbg2 Sample](http://msdn.microsoft.com/pt-br/21e1346a-6a17-4f57-b275-c76813089167)   
 [\_CrtReportBlockType](/visual-cpp/c-runtime-library/reference/crtreportblocktype)