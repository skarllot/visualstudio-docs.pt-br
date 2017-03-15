---
title: SuspendProfile | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SuspendProfile
ms.assetid: 7c8de6e6-bb88-4353-92c3-ce7290310d61
caps.latest.revision: 8
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
ms.openlocfilehash: e89083cb093daf0d2e6254894da4c6ad67969532
ms.lasthandoff: 02/22/2017

---
# <a name="suspendprofile"></a>SuspendProfile
O método `SuspendProfile` incrementa o contador de Suspender/Retomar do nível de criação de perfil especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI SuspendProfile(  
                       PROFILE_CONTROL_LEVEL Level,   
                       unsigned int dwId);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `Level`  
  
 Indica o nível de perfil de desempenho que pode ser aplicado a coleta de dados. Os enumeradores seguintes **PROFILE_CONTROL_LEVEL** podem ser usados para indicar um dos três níveis de desempenho aos quais a coleta de dados pode ser aplicada:  
  
|Enumerador|Descrição|  
|----------------|-----------------|  
|PROFILE_GLOBALLEVEL|A configuração de nível global afeta todos os processos e threads na execução da criação de perfil.|  
|PROFILE_PROCESSLEVEL|A configuração de nível de processo afeta todos os threads que fazem parte do processo especificado.|  
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
 O valor inicial do contador Suspender/Retomar é 0. Cada chamada para SuspendProfile adiciona 1 à contagem de Suspender/Retomar; cada chamada para ResumeProfile subtrai 1.  
  
 Quando a contagem de suspender/retomar for maior que 0, o estado de Suspensão/retomar para o nível é OFF. Quando a contagem for menor ou igual a 0, o estado de Suspensão/retomar é ON.  
  
 Quando o estado de Iniciar/Parar e o estado de Suspender/Retomar estiverem em ON, o estado de criação de perfil para o nível será ON. Para um thread ter seu perfil criado, os estados de nível global, processo e de thread para o thread devem estar em ON.  
  
## <a name="net-framework-equivalent"></a>Equivalente ao .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Informações de Função  
 Cabeçalho: declarado em VSPerf.h  
  
 Biblioteca de importação: VSPerf.lib  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o método SuspendProfile. Esse exemplo supõe que uma chamada anterior para StartProfile foi feita para o processo ou thread identificado por [PROFILE_CURRENTID](../profiling/profile-currentid.md).  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Referência da API do criador de perfil do Visual Studio (nativo)](../profiling/visual-studio-profiler-api-reference-native.md)
