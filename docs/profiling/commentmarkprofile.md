---
title: "CommentMarkProfile | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CommentMarkProfile"
  - "CommentMarkProfileA"
ms.assetid: 33ccff45-c33a-4672-b41f-5b317b848cd1
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CommentMarkProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A função de `CommentMarkProfile` insere um marcador numérico e uma cadeia de caracteres de texto no arquivo de .vsp.  Para que a marca e o comentário é inserido, a criação do thread que contém a função de `CommentMarkProfile` deverá ser ON.  
  
## Sintaxe  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkProfile(  
                                   long lMarker,   
                                   LPCTSTR szComment);  
```  
  
#### Parâmetros  
 `lMarker`  
  
 Marcador numérico a ser inserido.  O marcador deve ser maior ou igual a 0 \(zero\).  
  
 `szComment`  
  
 Ponteiro para a cadeia de caracteres de texto a ser inserido.  A cadeia de caracteres deve ter menos de 256 caracteres, incluindo o terminador NULO.  
  
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
 Analisando o estado do thread que contém a função do perfil da marca deve estar ON quando as marcas e os comentários inseridos com o VSInstr marcam o comando ou com funções \(CommentMarkAtProfile, CommentMarkProfile, ou MarkProfile\).  
  
 Perfis de marcas são de escopo global.  Por exemplo, um perfil de marca de perfil inserido em uma thread pode ser usado para marcar o início ou o fim de um segmento de dados em qualquer thread do arquivo .vsp.  
  
> [!IMPORTANT]
>  O método de CommentMarkProfile pode ser usado apenas com WQL.  
  
## Equivalência do .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## Informações de função  
  
|||  
|-|-|  
|**Cabeçalho**|Include VSPerf.h|  
|**Biblioteca**|Use VSPerf.lib|  
|**Unicode**|Implementado como `CommentMarkProfileW` \(Unicode\) e `CommentMarkProfileA` \(ANSI\).|  
  
## Exemplo  
 O código a seguir ilustra a chamada da função de CommentMarkProfile.  O exemplo pressupõe que o uso de configurações de macros de cadeia de caracteres do Win32 e do compilador Unicode determinar se o código a seguir chama a chamada da função de [!INCLUDE[vcpransi](../profiling/includes/vcpransi_md.md)] .  
  
```  
void ExerciseCommentMarkProfile()  
{  
    // Declare and initalize variables to pass to   
    // CommentMarkProfile.  The values of these   
    // parameters are assigned based on the needs   
    // of the code; and for the sake of simplicity  
    // in this example, the variables are assigned  
    // arbitrary values.  
    long markId = 01;  
    TCHAR * markText = TEXT("Exercising CommentMarkProfile...");  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare MarkOperationResult Enumerator.    
    // Holds return value from call to CommentMarkProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    markResult = CommentMarkProfile(  
        markId,  
        markText);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("CommentMarkProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## Consulte também  
 [Referência da API do Visual Studio Profiler \(nativo\)](../profiling/visual-studio-profiler-api-reference-native.md)