---
title: "NameProfile | Microsoft Docs"
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
  - "NameProfile"
  - "NameProfileA"
ms.assetid: 1bb05441-c4ff-4323-9fef-f3924fba4430
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# NameProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A função de `NameProfile` atribui uma cadeia de caracteres ao processamento ou ao thread especificado.  
  
 O NameProfile API está disponível apenas para analisar a instrumentação.  O NameProfile API não há suporte para analisar de uma amostra de.  
  
## Sintaxe  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI NameProfile(  
                                   LPCTSTR pszName,   
                                   PROFILE_CONTROL_LEVEL Level,  
                                   unsigned int dwId);  
```  
  
#### Parâmetros  
 `pszName`  
  
 O nome do elemento para a criação de perfil.  Um nome é inválido \(resultando no retorno NAME\_ERROR\_INVALID\_NAME de NameProfileA\) se:  
  
-   O ponteiro é transmitido em NameProfileA um valor NULO  
  
-   Os dados de cadeia de caracteres de inicialização de pszName com um número  
  
-   Os dados de cadeia de caracteres de pszName contiver um espaço  
  
-   Os dados de cadeia de caracteres de pszName contêm qualquer um dos seguintes caracteres: ;. \`~\! @\#$%^\*&\= \(\) \[\] {}&#124;\\? \/\<\>  
  
 `Level`  
  
 Indica o perfil no nível a que coleta de dados de desempenho pode ser aplicada.  Os seguintes valores de **PROFILE\_CONTROL\_LEVEL** podem ser usados para indicar um dos três níveis a que a coleta de dados de desempenho pode ser aplicada:  
  
|Enumerador|Descrição|  
|----------------|---------------|  
|PROFILE\_GLOBALLEVEL|A configuração de nível global afeta todos os processos e threads em analisar executado.|  
|PROFILE\_PROCESSLEVEL|Efeito em nível de configuração do processo todos os threads que fazem parte do processo especificado.|  
|PROFILE\_THREADLEVEL|Executável analisar afeta a configuração de nível do thread especificado.|  
  
 `dwId`  
  
 Analisando o identificador do nível.  Use o identificador do processo ou de threads que é gerado pelo sistema.  
  
## Valor de propriedade\/valor de retorno  
 A função indica êxito ou falha usando a enumeração **PROFILE\_COMMAND\_STATUS**.  O valor de retorno pode ser um dos seguintes:  
  
|Enumerador|Descrição|  
|----------------|---------------|  
|NAME\_ERROR\_ID\_NOEXIST|Analisando o elemento especificado não existe.|  
|NAME\_ERROR\_INVALID\_NAME|O nome é inválido.|  
|NAME\_ERROR\_LEVEL\_NOEXIST|O nível de perfil especificado não existe.|  
|NAME\_ERROR\_NO\_SUPPORT|A operação especificada não tem suporte.|  
|NAME\_ERROR\_OUTOFMEMORY|Não havia memória disponível para gravar o evento.|  
|NAME\_ERROR\_REDEFINITION|Um nome tiver sido atribuído no elemento do perfil.  O nome nessa função é ignorado.|  
|NAME\_ERROR\_TEXTTRUNCATED|O texto do nome exceder 32 caracteres que incluem o caractere nulo e foi truncado em virtude disso.|  
|NAME\_OK|O nome foi registrado com êxito.|  
  
## Comentários  
 Apenas um nome pode ser atribuído a cada processo ou thread.  Depois que um elemento analisando for, as chamadas subsequentes a NameProfile para esse elemento serão ignorados.  
  
 Se o mesmo nome é atribuído a threads ou processos diferentes, o relatório incluirá dados de todos os elementos nesse nível com esse nome.  
  
 Se você especificar um processo ou um thread diferente atual, você deve assegurar que foi inicializado e execução iniciada antes da será retornado.  Caso contrário, o método de NameProfile falha.  
  
> [!IMPORTANT]
>  CreateProcess\(\) e as funções de API de CreateThread\(\) podem retornar antes que o thread ou o processo foram inicializados.  
  
## Equivalência do .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## Informações de função  
  
|||  
|-|-|  
|**Cabeçalho**|Include VSPerf.h|  
|**Biblioteca**|Use VSPerf.lib|  
|**Unicode**|Implementado como `NameProfileW` \(Unicode\) e `NameProfileA` \(ANSI\).|  
  
## Exemplo  
 O código a seguir ilustra a chamada da função de NameProfile.  O exemplo assume o uso de macros de cadeias de caracteres Win32 e configurações de compilador ANSI para determinar se o código chama a função habilitada para ANSI.  
  
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
  
## Consulte também  
 [Referência da API do Visual Studio Profiler \(nativo\)](../profiling/visual-studio-profiler-api-reference-native.md)