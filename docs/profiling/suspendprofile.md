---
title: "SuspendProfile | Microsoft Docs"
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
  - "SuspendProfile"
ms.assetid: 7c8de6e6-bb88-4353-92c3-ce7290310d61
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# SuspendProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O método de `SuspendProfile` incrementa a suspensão\/resumo de contador para o nível de perfil especificado.  
  
## Sintaxe  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI SuspendProfile(  
                       PROFILE_CONTROL_LEVEL Level,   
                       unsigned int dwId);  
```  
  
#### Parâmetros  
 `Level`  
  
 Indica o perfil no nível a que coleta de dados de desempenho pode ser aplicada.  Os seguintes enumeradores de **PROFILE\_CONTROL\_LEVEL** podem ser usados para indicar um dos três níveis a que a coleta de dados de desempenho pode ser aplicada:  
  
|Enumerador|Descrição|  
|----------------|---------------|  
|PROFILE\_GLOBALLEVEL|A configuração de nível global afeta todos os processos e threads em analisar executado.|  
|PROFILE\_PROCESSLEVEL|Efeito em nível de configuração do processo todos os threads que fazem parte do processo especificado.|  
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
 O valor inicial do contador de suspensão\/resumo é 0.  Cada chamada para SuspendProfile adiciona 1 à contagem de suspensão\/resumo; cada chamada para ResumeProfile subtrai 1.  
  
 Quando a contagem de suspensão\/resumo é maior que 0, o estado de suspensão\/resumo do nível é.  Quando a contagem é menor ou igual a 0, o estado de suspensão\/resumo é ON.  
  
 Quando o estado de Iniciar\/parar e o estado de suspensão\/resumo são ambas ON, o estado de perfil para o nível é ON.  Para que um thread ser analisada, o GAC, o processo, e os estados de nível de thread para o thread devem estar ON.  
  
## Equivalência do .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## Informações de função  
 Cabeçalho: Declarado em VSPerf.h  
  
 Biblioteca de importação: VSPerf.lib  
  
## Exemplo  
 O exemplo a seguir ilustra o método de SuspendProfile.  Este exemplo assume que uma chamada anterior a StartProfile esteve feito para o processo ou o thread identificado por [PROFILE\_CURRENTID](../profiling/profile-currentid.md).  
  
```  
void ExerciseSuspendProfile()  
{  
    // The initial value of the Suspend/Resume counter is 0.  
    // Each call to SuspendProfile adds 1 to the  
    // Suspend/Resume count; each call  
    // to ResumeProfile subtracts 1.  
  
    // Variables used to print output  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold result of call  
    // to SuspendProfile  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = SuspendProfile(  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("SuspendProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## Consulte também  
 [Referência da API do Visual Studio Profiler \(nativo\)](../profiling/visual-studio-profiler-api-reference-native.md)