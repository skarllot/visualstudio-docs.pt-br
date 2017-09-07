---
title: LPTEXTOUTPROC | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 658193f526123d237ef9b90a05861492b9f007c9
ms.contentlocale: pt-br
ms.lasthandoff: 09/06/2017

---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC
Quando o usuário executa uma operação de controle de origem de dentro do ambiente de desenvolvimento integrado (IDE), o plug-in de controle do código-fonte talvez queira transmitir mensagens de erro ou de status relacionadas à operação. O plug-in pode exibir suas próprias caixas de mensagem para essa finalidade. No entanto, para integração perfeita mais, o plug-in pode passar cadeias de caracteres para o IDE, que são exibidos em seu modo nativo de exibir informações de status. O mecanismo para isso é o `LPTEXTOUTPROC` ponteiro de função. O IDE implementa essa função (descrita em mais detalhes abaixo) para exibir o status e erros.  
  
 O IDE passa para o controle de origem plug-in um ponteiro de função para esta função, como o `lpTextOutProc` parâmetro ao chamar o [SccOpenProject](../extensibility/sccopenproject-function.md). Durante uma operação de SCC, por exemplo, no meio de uma chamada para o [SccGet](../extensibility/sccget-function.md) envolvendo muitos arquivos, o plug-in pode chamar o `LPTEXTOUTPROC` função periodicamente passar cadeias de caracteres para exibir. O IDE pode exibir essas cadeias de caracteres em uma barra de status, em uma janela de saída, ou em uma caixa de mensagem separada, conforme apropriado. Opcionalmente, o IDE pode ser capaz de exibir determinadas mensagens com um **Cancelar** botão. Isso permite que o usuário cancelar a operação, e ele permite que o IDE passar essa informação para o plug-in.  
  
## <a name="signature"></a>Assinatura  
 O IDE saída de função tem a seguinte assinatura:  
  
```cpp  
typedef LONG (*LPTEXTOUTPROC) (  
   LPSTR display_string,  
   LONG mesg_type  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 display_string  
 Uma cadeia de caracteres de texto para exibir. Essa cadeia de caracteres não deve terminar com um carro retorno ou uma alimentação de linha.  
  
 mesg_type  
 O tipo de mensagem. A tabela a seguir lista os valores com suporte para esse parâmetro.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|A mensagem será considerada informações, aviso ou erro.|  
|`SCC_MSG_STATUS`|A mensagem mostra o status e pode ser exibida na barra de status.|  
|`SCC_MSG_DOCANCEL`|Enviado com nenhuma cadeia de caracteres de mensagem.|  
|`SCC_MSG_STARTCANCEL`|Começa exibindo um **Cancelar** botão.|  
|`SCC_MSG_STOPCANCEL`|Interrompe a exibição de um **Cancelar** botão.|  
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Solicita o IDE se a operação em segundo plano é cancelada: IDE retorna `SCC_MSG_RTN_CANCEL` se a operação foi cancelada; caso contrário, retornará `SCC_MSG_RTN_OK`. O `display_string` parâmetro será convertido como uma [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) estrutura, que é fornecida pelo plug-in de controle de origem.|  
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Informa o IDE sobre um arquivo antes de serem recuperado do controle de versão. O `display_string` parâmetro será convertido como uma [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) estrutura, que é fornecida pelo plug-in de controle de origem.|  
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Informa o IDE sobre um arquivo depois que ele tiver sido recuperado do controle de versão. O `display_string` parâmetro será convertido como uma [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) estrutura, que é fornecida pelo plug-in de controle de origem.|  
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Informa o IDE do status atual de uma operação em segundo plano. O `display_string` parâmetro será convertido como uma [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) estrutura, que é fornecida pelo plug-in de controle de origem.|  
  
## <a name="return-value"></a>Valor de retorno  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_MSG_RTN_OK|A cadeia de caracteres foi exibida ou a operação foi concluída com êxito.|  
|SCC_MSG_RTN_CANCEL|O usuário deseja cancelar a operação.|  
  
## <a name="example"></a>Exemplo  
 Suponha que o IDE chama o [SccGet](../extensibility/sccget-function.md) com vinte nomes de arquivo. O plug-in de controle de origem deseja evitar Cancelando a operação no meio de obter um arquivo. Depois de obter a cada arquivo, ele chama `lpTextOutProc`, passando as informações de status em cada arquivo e envia um `SCC_MSG_DOCANCEL` mensagem se nenhum status ao relatório. Se a qualquer momento o plug-in recebe um valor de retorno `SCC_MSG_RTN_CANCEL` do IDE, ele cancela a operação imediatamente, para que não há mais arquivos são recuperados.  
  
## <a name="structures"></a>Estruturas  
  
###  <a name="LinkSccMsgDataIsCancelled"></a>SccMsgDataIsCancelled  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
} SccMsgDataIsCancelled;  
```  
  
 Essa estrutura é enviada com o `SCC_MSG_BACKGROUND_IS_CANCELLED` mensagem. Ele é usado para comunicar-se a ID da operação em segundo plano que foi cancelada.  
  
###  <a name="LinkSccMsgDataOnBeforeGetFile"></a>SccMsgDataOnBeforeGetFile  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
} SccMsgDataOnBeforeGetFile;  
```  
  
 Essa estrutura é enviada com o `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` mensagem. Ele é usado para transmitir o nome do arquivo que está prestes a ser recuperado e a ID da operação em segundo plano que está fazendo a recuperação.  
  
###  <a name="LinkSccMsgDataOnAfterGetFile"></a>SccMsgDataOnAfterGetFile  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
   SCCRTN sResult;  
} SccMsgDataOnAfterGetFile;  
```  
  
 Essa estrutura é enviada com o `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` mensagem. Ele é usado para comunicar o resultado de recuperar o arquivo especificado, bem como a ID da operação em segundo plano que fez a recuperar. Consulte os valores de retorno para o [SccGet](../extensibility/sccget-function.md) para o que pode ser fornecido como resultado.  
  
###  <a name="LinkSccMsgDataOnMessage"></a>SccMsgDataOnMessage  
 [C++]  
  
```  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szMessage;  
   BOOL bIsError;  
} SccMsgDataOnMessage;  
```  
  
 Essa estrutura é enviada com o `SCC_MSG_BACKGROUND_ON_MESSAGE` mensagem. Ele é usado para comunicar o status atual de uma operação em segundo plano. O status é expresso como uma cadeia de caracteres a ser exibida pelo IDE, e `bIsError` indica a severidade da mensagem (`TRUE` para uma mensagem de erro; `FALSE` para um aviso ou uma mensagem informativa). A ID da operação em segundo plano enviar o status também é fornecida.  
  
## <a name="code-example"></a>Exemplo de código  
 Aqui está um breve exemplo de chamada `LPTEXTOUTPROC` para enviar o `SCC_MSG_BACKGROUND_ON_MESSAGE` mensagem, mostrando como converter a estrutura para a chamada.  
  
```cpp  
LONG SendStatusMessage(  
    LPTEXTOUTPROC pTextOutProc,  
    DWORD         dwBackgroundID,  
    LPCTSTR       pStatusMsg,  
    BOOL          bIsError)  
{  
    SccMsgDataOnMessage msgData = { 0 };  
    LONG                result  = 0;  
  
    msgData.dwBackgroundOperationID = dwBackgroundID;  
    msgData.szMessage               = pStatusMsg;  
    msgData.bIsError                = bIsError;  
  
    result = pTextOutProc(reinterpret_cast<LPCTSTR>(&msgData), SCC_MSG_BACKGROUND_ON_MESSAGE);  
    return result;  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Funções de retorno de chamada implementadas pelo IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Plug-ins de controle do código-fonte](../extensibility/source-control-plug-ins.md)
