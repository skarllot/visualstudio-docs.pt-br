---
title: "CommentMarkAtProfile | Microsoft Docs"
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
  - "CommentMarkAtProfile"
  - "CommentMarkAtProfileA"
ms.assetid: 04294ca3-bf9c-4c76-86f1-898c2140de27
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CommentMarkAtProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O método `CommentMarkAtProfile` adiciona um carimbo de data\/hora, uma marca numérica, e um comentário em forma de cadeia de caracteres ao arquivo .vsp.  O valor do carimbo de data\/hora pode ser usado para sincronizar eventos externos.  Para que a marca e o comentário sejam inseridos, a criação de perfis para o segmento que contém a função CommentMarkAtProfile deve estar ATIVADA.  
  
## Sintaxe  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkAtProfile (  
                                   __int64 dnTimestamp,  
                                   long lMarker,  
                                   LPCTSTR szComment);  
```  
  
#### Parâmetros  
 `dnTimestamp`  
  
 Um inteiro de 64 bits que representa um valor de carimbo de data\/hora.  
  
 `lMarker`  
  
 O marcador numérico a inserir.  O marcador deve ser maior ou igual a 0 \(zero\).  
  
 `szComment`  
  
 Um ponteiro para a cadeia de caracteres a inserir.  A cadeia de caracteres deve ter menos de 256 caracteres, incluindo o terminador NULO.  
  
## Valor de propriedade\/valor de retorno  
 A função indica êxito ou falha usando a enumeração **PROFILE\_COMMAND\_STATUS**.  O valor de retorno pode ser um dos seguintes:  
  
|Enumerador|Descrição|  
|----------------|---------------|  
|MARK\_ERROR\_MARKER\_RESERVED|O parâmetro é menor ou igual a 0.  Estes valores são reservados.  A marca e o comentário não são gravados.|  
|MARK\_ERROR\_MODE\_NEVER|A criação de perfis estava definida como NUNCA quando a função foi chamada.  A marca e o comentário não são gravados.|  
|MARK\_ERROR\_MODE\_OFF|A criação de perfis estava definida como DESATIVADA quando a função foi chamada.  A marca e o comentário não são gravados.|  
|MARK\_ERROR\_NO\_SUPPORT|Não há suporte para marcas neste contexto.  A marca e o comentário não são gravados.|  
|MARK\_ERROR\_OUTOFMEMORY|Não havia memória disponível para gravar o evento.  A marca e o comentário não são gravados.|  
|MARK\_TEXTTOOLONG|A cadeia de caracteres excede o máximo de 256 caracteres.  A cadeia de caracteres de comentário é truncada e a marca e o comentário são gravados.|  
|MARK\_OK|MARK\_OK é retornado para indicar sucesso.|  
  
## Comentários  
 A criação de perfil para a thread que contém a função de perfil de marca deve estar ativada para marcas e comentários inseridos com o comando Marca ou funções da API \(CommentMarkAtProfile, CommentMarkProfile, ou MarkProfile\).  Perfis de marcas são de escopo global.  Por exemplo, um perfil de marca de perfil inserido em uma thread pode ser usado para marcar o início ou o fim de um segmento de dados em qualquer thread do arquivo .vsp.  
  
> [!IMPORTANT]
>  Métodos CommentMarkAtProfile devem ser usados somente com instrumentação.  
  
## Equivalência do .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## Informações de função  
  
|||  
|-|-|  
|**Cabeçalho**|Include VSPerf.h|  
|**Biblioteca**|Use VSPerf.lib|  
|**Unicode**|Implementado como CommentMarkAtProfileW \(Unicode\) e CommentMarkAtProfileA \(ANSI\).|  
  
## Exemplo  
 O código a seguir ilustra o uso da chamada genérica de função CommentMarkAtProfile.  O exemplo assume o uso de macros de cadeias de caracteres Win32 e configurações de compilador ANSI para determinar se o código chama a função habilitada para ANSI.  
  
```  
void ExerciseCommentMarkAtProfile(void)  
{  
    // Declare and initalize variables to pass to   
    // CommentMarkAtProfile.  The values of these   
    // parameters are assigned based on the needs   
    // of the code; and for the sake of simplicity  
    // in this example, the variables are assigned  
    // arbitrary values.  
    int64 timeStamp = 0x1111;  
    long markId = 01;  
    TCHAR * markText = TEXT("Exercising CommentMarkAtProfile...");  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare MarkOperationResult Enumerator.    
    // Holds return value from call to CommentMarkAtProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    markResult = CommentMarkAtProfile(  
        timeStamp,  
        markId,  
        markText);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("CommentMarkAtProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
    pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## Consulte também  
 [Referência da API do Visual Studio Profiler \(nativo\)](../profiling/visual-studio-profiler-api-reference-native.md)