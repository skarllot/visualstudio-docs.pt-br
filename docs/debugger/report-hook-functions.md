---
title: "Fun&#231;&#245;es de gancho do relat&#243;rio | Microsoft Docs"
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
  - "Função _CrtDbgReport"
  - "Função _CrtSetReportHook"
  - "depurador, funções de gancho de relatório"
  - "depurando [C++], funções de gancho"
  - "ganchos, relatório"
  - "alocação de memória, heap de depuração"
  - "funções de gancho de relatório"
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Fun&#231;&#245;es de gancho do relat&#243;rio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Uma função de gancho de relatório, instalada usando [\_CrtSetReportHook](/visual-cpp/c-runtime-library/reference/crtsetreporthook), é chamada sempre que [\_CrtDbgReport](/visual-cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) gera um relatório de depuração.  Você pode usá\-la, entre outras coisas, para filtrar relatórios com foco em tipos de alocações específicos.  Uma função de gancho de relatório deve ter um protótipo como o seguinte:  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 O ponteiro que você passa para **\_CrtSetReportHook** é do tipo **\_CRT\_REPORT\_HOOK**, conforme definido em CRTDBG.H:  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Quando a biblioteca em tempo de execução chama sua função de gancho, o argumento *de nRptType* contém a categoria do relatório \(**\_CRT\_WARN**, **\_CRT\_ERROR** ou **\_CRT\_ASSERT**\), *szMsg* contém um ponteiro para uma cadeia de caracteres de mensagem de relatório completamente montada e *retVal* especifica se `_CrtDbgReport` deve continuar a execução normal depois de gerar o relatório ou iniciar o depurador. \(Um valor de *retVal* igual a zero continua a execução, um valor igual a 1 inicia o depurador\).  
  
 Se o gancho tratar completamente a mensagem em questão, de modo que nenhum relatório adicional seja necessário, ele retornará **TRUE**.  Caso ele retorne **FALSE**, `_CrtDbgReport` relatará a mensagem normalmente.  
  
## Consulte também  
 [Gravação da função de gancho de depuração](../debugger/debug-hook-function-writing.md)   
 [crt\_dbg2 Sample](http://msdn.microsoft.com/pt-br/21e1346a-6a17-4f57-b275-c76813089167)