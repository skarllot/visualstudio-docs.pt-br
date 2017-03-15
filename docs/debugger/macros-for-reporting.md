---
title: "Macros para relat&#243;rios | Microsoft Docs"
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
  - "vs.debug.macros"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Macro _RPTFn"
  - "Macro _RPTn"
  - "CRT, macros de relatórios"
  - "depuração [CRT], macros de relatórios"
  - "Macros , macros de relatórios CRT"
  - "Macros , depurando com"
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Macros para relat&#243;rios
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode usar as macros **\_RPTn** e **\_RPTFn** \(definidas em CRTDBG.H\), para substituir o uso de instruções `printf` para depuração.  Essas macros não desaparecem automaticamente na compilação de lançamento quando **\_DEBUG** não estiver definido, de modo que não há necessidade de incluí\-los em **\#ifdef**s.  
  
|Macro|Descrição|  
|-----------|---------------|  
|**\_RPT0**, **\_RPT1**, **\_RPT2**, **\_RPT3**, **\_RPT4**|Gera uma cadeia de caracteres de mensagem e zero a quatro argumentos.  Para \_RPT1 até **\_RPT4**, a cadeia de caracteres de mensagem funciona como uma cadeia de caracteres de formatação de estilo printf para os argumentos.|  
|**\_RPTF0**, **\_RPTF1**, **,\_RPTF2**, **\_RPTF4**|Da mesma forma que **\_RPTn**, mas essas macros também geram a saída do nome do arquivo e o número da linha onde a macro está localizada.|  
  
 Considere o exemplo a seguir:  
  
```  
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 Esse código gera os valores de `someVar` e `otherVar` a **stdout**.  Você pode usar a seguinte chamada para `_RPTF2` para reportar os mesmos valores e, além disso, o nome de arquivo e o número de linha:  
  
```  
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
 Se você achar que um aplicativo específico precisa de um relatório de depuração que as macros fornecidas com a biblioteca em tempo de execução C não fornecem, poderá escrever uma macro criada especificamente para se adaptar a seus próprios requisitos.  Em um dos arquivos de cabeçalho, por exemplo, você pode incluir código como o seguinte para definir uma macro chamada **ALERT\_IF2**:  
  
```  
#ifndef _DEBUG                  /* For RELEASE builds */  
#define  ALERT_IF2(expr, msg, arg1, arg2)  do {} while (0)  
#else                           /* For DEBUG builds   */  
#define  ALERT_IF2(expr, msg, arg1, arg2) \  
    do { \  
        if ((expr) && \  
            (1 == _CrtDbgReport(_CRT_ERROR, \  
                __FILE__, __LINE__, msg, arg1, arg2))) \  
            _CrtDbgBreak( ); \  
    } while (0)  
#endif  
```  
  
 Uma chamada para **ALERT\_IF2** pode executar todas as funções de código **printf** no início deste tópico:  
  
```  
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 Como uma macro personalizada pode ser alterada facilmente para reportar mais ou menos informações para os destinos diferentes \(dependendo do que é mais conveniente\), essa abordagem pode ser útil principalmente à medida que seus requisitos de depuração evoluem.  
  
## Consulte também  
 [Técnicas de depuração CRT](../debugger/crt-debugging-techniques.md)