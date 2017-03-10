---
title: "Como escrever uma fun&#231;&#227;o de relat&#243;rios de erro de tempo de execu&#231;&#227;o | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
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
  - "função de relatórios"
  - "erros de tempo de execução, funções de relatórios"
ms.assetid: 989bf312-5038-44f3-805f-39a34d18760e
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como escrever uma fun&#231;&#227;o de relat&#243;rios de erro de tempo de execu&#231;&#227;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Uma função personalizada de relatório para erros em tempo de execução deve ter a mesma declaração que `_CrtDbgReportW`.  Deve retornar um valor de 1 para o depurador.  
  
 O exemplo a seguir mostra como definir uma função personalizada de relatório.  
  
## Exemplo  
  
```  
#include <stdio.h>  
int errorhandler = 0;  
void configureMyErrorFunc(int i)  
{  
    errorhandler = i;  
}  
  
int MyErrorFunc(int errorType, const wchar_t *filename,  
                int linenumber, const wchar_t *moduleName,  
                const wchar_t *format, ...)  
{  
    switch (errorhandler)  
    {  
    case 0:  
    case 1:  
        wprintf(L"Error type %d at %s line %d in %s",  
                errorType, filename, linenumber, moduleName);  
        break;  
    case 2:  
    case 3:  
        fprintf(stderr, "Error type");  
        break;  
    }  
  
    return 1;  
}  
```  
  
## Exemplo  
 O exemplo a seguir mostra uma função personalizada de relatório mais complexa.  Neste exemplo, a instrução switch trata vários tipos de erro, conforme definido pelo parâmetro `reportType` de `_CrtDbgReportW`.  Como você está substituindo `_CrtDbgReportW`, não poderá usar `_CrtSetReportMode`.  A função deve tratar a saída.  O primeiro argumento variável nessa função usa um número de erro em tempo de execução.  Para obter mais informações, consulte [\_RTC\_SetErrorType](/visual-cpp/c-runtime-library/reference/rtc-seterrortype).  
  
```  
#include <windows.h>  
#include <stdarg.h>  
#include <rtcapi.h>  
#include <malloc.h>  
#pragma runtime_checks("", off)  
int Catch_RTC_Failure(int errType, const wchar_t *file, int line,   
                   const wchar_t *module, const wchar_t *format, ...)  
{  
    // Prevent re-entrance.  
    static long running = 0;  
    while (InterlockedExchange(&running, 1))  
        Sleep(0);  
    // Now, disable all RTC failures.  
    int numErrors = _RTC_NumErrors();  
    int *errors=(int*)_alloca(numErrors);  
    for (int i = 0; i < numErrors; i++)  
        errors[i] = _RTC_SetErrorType((_RTC_ErrorNumber)i, _RTC_ERRTYPE_IGNORE);  
  
   // First, get the rtc error number from the var-arg list.  
    va_list vl;  
    va_start(vl, format);  
    _RTC_ErrorNumber rtc_errnum = va_arg(vl, _RTC_ErrorNumber);  
    va_end(vl);  
  
    wchar_t buf[512];  
    const char *err = _RTC_GetErrDesc(rtc_errnum);  
    swprintf_s(buf, 512, L"%S\nLine #%d\nFile:%s\nModule:%s",  
        err,  
        line,  
        file ? file : L"Unknown",  
        module ? module : L"Unknown");  
    int res = (MessageBox(NULL, buf, L"RTC Failed...", MB_YESNO) == IDYES) ? 1 : 0;  
    // Now, restore the RTC errortypes.  
    for(int i = 0; i < numErrors; i++)  
        _RTC_SetErrorType((_RTC_ErrorNumber)i, errors[i]);  
    running = 0;  
    return res;  
}  
#pragma runtime_checks("", restore)  
```  
  
## Exemplo  
 Use `_RTC_SetErrorFuncW` para instalar a função personalizada em vez de `_CrtDbgReportW`.  Para obter mais informações, consulte [\_RTC\_SetErrorFuncW](/visual-cpp/c-runtime-library/reference/rtc-seterrorfuncw).  O valor de retorno de `_RTC_SetErrorFuncW` é a função de relatório anterior, que você pode salvar e restaurar se necessário.  
  
```  
#include <rtcapi.h>  
int main()  
{  
    _RTC_error_fnW oldfunction, newfunc;  
    oldfunction = _RTC_SetErrorFuncW(&MyErrorFunc);  
    // Run some code.  
    newfunc = _RTC_SetErrorFuncW(oldfunction);  
    // newfunc == &MyErrorFunc;  
    // Run some more code.  
}  
```  
  
## Consulte também  
 [Personalização das verificações de tempo de execução nativas](../debugger/native-run-time-checks-customization.md)