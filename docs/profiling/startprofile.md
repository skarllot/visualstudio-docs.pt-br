---
title: StartProfile | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- StartProfile
ms.assetid: 1761311d-c9d5-48f5-b1f8-b3605829940a
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 0f3fb0cc83befd44c3d154873dfba9d4c9b8766f
ms.lasthandoff: 02/22/2017

---
# <a name="startprofile"></a>StartProfile
A função `StartProfile` define o contador como 1 (on) para o nível de criação de perfil especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI StartProfile(  
                        PROFILE_CONTROL_LEVEL Level,   
                        unsigned int dwId);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `Level`  
  
 Indica o nível de perfil de desempenho que pode ser aplicado a coleta de dados. Os enumeradores seguintes **PROFILE_CONTROL_LEVEL** podem ser usados para indicar um dos três níveis de desempenho aos quais a coleta de dados pode ser aplicada:  
  
|Enumerador|Descrição|  
|----------------|-----------------|  
|PROFILE_GLOBALLEVEL|A configuração de nível global afeta todos os processos e threads na execução da criação de perfil.|  
|PROFILE_PROCESSLEVEL|Configuração de nível de processo afeta todos os threads que fazem parte do processo especificado.|  
|PROFILE_THREADLEVEL|A configuração do nível de criação de perfil do thread afeta o thread especificado.|  
  
 `dwId`  
  
 O identificador de processo ou thread gerado pelo sistema.  
  
## <a name="property-valuereturn-value"></a>Valor de propriedade/Valor de retorno  
 A função indica êxito ou falha usando a enumeração de **PROFILE_COMMAND_STATUS**. O valor retornado pode ser um dos seguintes:  
  
|Enumerador|Descrição|  
|----------------|-----------------|  
|PROFILE_ERROR_ID_NOEXIST|A ID de elemento de criação de perfil não existe.|  
|PROFILE_ERROR_LEVEL_NOEXIST|O nível de criação de perfil especificado não existe.|  
|PROFILE_ERROR_MODE_NEVER|O modo de criação de perfil foi definido para NUNCA quando a função foi chamada.|  
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|A chamada de função de criação de perfil, o nível de criação de perfil ou combinação de chamada e nível ainda não foi implementada.|  
|PROFILE_OK|A chamada foi bem-sucedida.|  
  
## <a name="remarks"></a>Comentários  
 StartProfile e StopProfile controlam o estado de início/parada para o nível de criação de perfil. O valor padrão de Iniciar/parar é 1. O valor inicial pode ser alterado no Registro. Cada chamada para StartProfile define Iniciar/Parar como 1; cada chamada para StopProfile define como 0.  
  
 Quando a Iniciar/Parar é maior que 0, o estado de Iniciar/Parar para o nível está como ON. Quando for menor ou igual a 0, o estado de Iniciar/Parar é OFF.  
  
 Quando o estado de Iniciar/Parar e o estado de Suspender/Retomar estiverem em ON, o estado de criação de perfil para o nível será ON. Para um thread ser perfilado, os estados de nível global, processo e thread para o thread devem estar em ON.  
  
## <a name="net-framework-equivalent"></a>Equivalente ao .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Informações de Função  
 Cabeçalho: declarado em VSPerf.h  
  
 Biblioteca de importação: VSPerf.lib  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra a chamada da função StartProfile.  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Referência da API do criador de perfil do Visual Studio (nativo)](../profiling/visual-studio-profiler-api-reference-native.md)
