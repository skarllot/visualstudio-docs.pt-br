---
title: NameProfile | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- NameProfile
- NameProfileA
ms.assetid: 1bb05441-c4ff-4323-9fef-f3924fba4430
caps.latest.revision: 16
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
ms.openlocfilehash: 65681e7d5628c934a87eacb1239733e99f877094
ms.lasthandoff: 02/22/2017

---
# <a name="nameprofile"></a>NameProfile
A função `NameProfile` atribui uma cadeia de caracteres ao thread ou processo especificado.  
  
 A API NameProfile está disponível somente para a criação de perfil de instrumentação. Não há suporte para a API NameProfile para criação de perfil de amostragem.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI NameProfile(  
                                   LPCTSTR pszName,   
                                   PROFILE_CONTROL_LEVEL Level,  
                                   unsigned int dwId);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszName`  
  
 O nome do elemento de criação de perfil. Um nome é inválido (resultando em NameProfileA retorna NAME_ERROR_INVALID_NAME) se:  
  
-   O ponteiro transmitido para NameProfileA é um valor NULL  
  
-   Os dados de cadeia de caracteres de pszName começam com um número  
  
-   Os dados de cadeia de caracteres de pszName contêm um espaço  
  
-   Os dados de cadeia de caracteres de pszName contêm todos os seguintes caracteres: ,;.`~!@#$%^&*()=[]{}&#124;\\?/<>  
  
 `Level`  
  
 Indica o nível de perfil de desempenho que pode ser aplicado a coleta de dados. Os seguintes valores de **PROFILE_CONTROL_LEVEL** podem ser usados para indicar um dos três níveis aos quais a coleta de dados de desempenho pode ser aplicada:  
  
|Enumerador|Descrição|  
|----------------|-----------------|  
|PROFILE_GLOBALLEVEL|A configuração de nível global afeta todos os processos e threads na execução da criação de perfil.|  
|PROFILE_PROCESSLEVEL|A configuração de nível de processo afeta todos os threads que fazem parte do processo especificado.|  
|PROFILE_THREADLEVEL|A configuração do nível de criação de perfil do thread afeta o thread especificado.|  
  
 `dwId`  
  
 Identificador de nível de criação de perfil. Use o identificador de processo ou thread que é gerado pelo sistema.  
  
## <a name="property-valuereturn-value"></a>Valor de propriedade/Valor de retorno  
 A função indica êxito ou falha usando a enumeração de **PROFILE_COMMAND_STATUS**. O valor retornado pode ser um dos seguintes:  
  
|Enumerador|Descrição|  
|----------------|-----------------|  
|NAME_ERROR_ID_NOEXIST|O elemento de criação de perfil especificado não existe.|  
|NAME_ERROR_INVALID_NAME|O nome é inválido.|  
|NAME_ERROR_LEVEL_NOEXIST|O nível de perfil especificado não existe.|  
|NAME_ERROR_NO_SUPPORT|Não há suporte para a operação especificada.|  
|NAME_ERROR_OUTOFMEMORY|Não havia memória disponível para registrar o evento.|  
|NAME_ERROR_REDEFINITION|Um nome já foi atribuído ao elemento do perfil. O nome nessa função será ignorada.|  
|NAME_ERROR_TEXTTRUNCATED|O texto de nome excedeu 32 caracteres, incluindo o caractere nulo e, portanto, foi truncado.|  
|NAME_OK|O nome foi registrado com êxito.|  
  
## <a name="remarks"></a>Comentários  
 Apenas um nome pode ser atribuído a cada processo ou thread. Depois que um elemento de criação de perfil é nomeado, as chamadas subsequentes para NameProfile para esse elemento são ignoradas.  
  
 Se o mesmo nome é fornecido a diferentes processos ou threads, o relatório incluirá dados de todos os elementos nesse nível com esse nome.  
  
 Se você especificar um processo ou thread que não seja o atual, você deve se certificar de que ele foi inicializado e começou a ser executado antes de você nomeá-lo. Caso contrário, o método NameProfile falhará.  
  
> [!IMPORTANT]
>  As funções de API CreateProcess() e CreateThread() podem retornar antes de o thread ou processo ser inicializado.  
  
## <a name="net-framework-equivalent"></a>Equivalente ao .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Informações de Função  
  
|||  
|-|-|  
|**Cabeçalho**|Incluir VSPerf.h|  
|**Biblioteca**|Usar VSPerf.lib|  
|**Unicode**|Implementado como `NameProfileW` (Unicode) e `NameProfileA` (ANSI).|  
  
## <a name="example"></a>Exemplo  
 O código a seguir ilustra a chamada da função NameProfile. O exemplo pressupõe o uso de macros de cadeia de caracteres do Win32 e as configurações de compilador para ANSI para determinar se o código chama a função habilitada por ANSI.  
  
```  
void ExerciseNameProfile()  
{  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Create and initialize variables to pass to   
    // ExerciseNameProfile.  The value of this   
    // parameter is based on the needs of the code;  
    // and for the sake of simplicity in this example,   
    // the variable is assigned an arbitrary value.  
    TCHAR * profileName = TEXT("ExerciseNameProfile");  
  
    // Declare enumeration to hold result of call to   
    // ExerciseNameProfle.  
    PROFILE_COMMAND_STATUS nameResult;  
  
    nameResult =  NameProfile(  
        profileName,  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("NameProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, nameResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência da API do criador de perfil do Visual Studio (nativo)](../profiling/visual-studio-profiler-api-reference-native.md)
