---
title: "StartProfile | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "StartProfile"
ms.assetid: 1761311d-c9d5-48f5-b1f8-b3605829940a
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# StartProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A função de `StartProfile` define ao contrário de 1 \(ativado\) para o nível de perfil especificado.  
  
## Sintaxe  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI StartProfile(  
                        PROFILE_CONTROL_LEVEL Level,   
                        unsigned int dwId);  
```  
  
#### Parâmetros  
 `Level`  
  
 Indica o perfil no nível a que coleta de dados de desempenho pode ser aplicada.  Os seguintes enumeradores de **PROFILE\_CONTROL\_LEVEL** podem ser usados para indicar um dos três níveis a que a coleta de dados de desempenho pode ser aplicada:  
  
|Enumerador|Descrição|  
|----------------|---------------|  
|PROFILE\_GLOBALLEVEL|A configuração de nível global afeta todos os processos e threads em analisar executado.|  
|PROFILE\_PROCESSLEVEL|A configuração de nível de processo afeta todos os threads que fazem parte do processo especificado.|  
|PROFILE\_THREADLEVEL|Executável analisar afeta a configuração de nível do thread especificado.|  
  
 `dwId`  
  
 O identificador do processo ou de thread gerado pelo sistema.  
  
## Valor de propriedade\/valor de retorno  
 A função indica êxito ou falha usando a enumeração **PROFILE\_COMMAND\_STATUS**.  O valor de retorno pode ser um dos seguintes:  
  
|Enumerador|Descrição|  
|----------------|---------------|  
|PROFILE\_ERROR\_ID\_NOEXIST|A ID de perfil do elemento não existe.|  
|PROFILE\_ERROR\_LEVEL\_NOEXIST|Analisando o nível especificado não existe.|  
|PROFILE\_ERROR\_MODE\_NEVER|A criação de perfis estava definida como NUNCA quando a função foi chamada.|  
|PROFILE\_ERROR\_NOT\_YET\_IMPLEMENTED|A chamada de função, analisando do nível, ou uma combinação de chamada e de nível não for implementada.|  
|PROFILE\_OK|A chamada obteve êxito.|  
  
## Comentários  
 StartProfile e StopProfile controlam o estado de Iniciar\/parar para o nível analisando.  O valor padrão de Iniciar\/parar é 1.  O valor inicial pode ser alterado no Registro.  Cada chamada para conjuntos de StartProfile Iniciar\/parar a 1; cada chamada para StopProfile defina\-o como 0.  
  
 Quando o Iniciar\/parar é maior que 0, o estado de Iniciar\/parar para o nível é ON.  Quando for menor ou igual a 0, o estado de Iniciar\/parar é.  
  
 Quando o estado de Iniciar\/parar e o estado de suspensão\/resumo são ambas ON, o estado de perfil para o nível é ON.  Para que um thread ser analisada, o GAC, o processo, e os estados de nível de thread para o thread devem estar ON.  
  
## Equivalência do .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## Informações de função  
 Cabeçalho: Declarado em VSPerf.h  
  
 Biblioteca de importação: VSPerf.lib  
  
## Exemplo  
 O exemplo a seguir ilustra a chamada da função de StartProfile.  
  
```  
void ExerciseStartProfile()  
{  
    // StartProfile and StopProfile control the  
    // Start/Stop state for the profiling level.   
    // The default initial value of Start/Stop is 1.   
    // The initial value can be changed in the registry.   
    // Each call to StartProfile sets Start/Stop to 1;   
    // each call to StopProfile sets it to 0.   
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold return value of   
    // the call to StartProfile.  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = StartProfile(  
        PROFILE_THREADLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("StartProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## Consulte também  
 [Referência da API do Visual Studio Profiler \(nativo\)](../profiling/visual-studio-profiler-api-reference-native.md)