---
title: "Função SccGetEvents | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
caps.latest.revision: 13
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 5a715cfbf7e0944d76c92b992c53088428cfd1b9
ms.lasthandoff: 02/22/2017

---
# <a name="sccgetevents-function"></a>Função SccGetEvents
Esta função recupera um evento de status em fila.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
SCCRTN SccGetEvents (  
   LPVOID pvContext,  
   LPSTR  lpFileName,  
   LPLONG lpStatus,  
   LPLONG pnEventsRemaining  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pvContext  
 [in] A estrutura de contexto de plug-in de controle de origem.  
  
 lpFileName  
 [no, out] Buffer onde o plug-in de controle de origem coloca o nome de arquivo retornado (até caracteres MAX_PATH).  
  
 lpStatus  
 [no, out] Retorna o código de status (consulte [código de Status do arquivo](../extensibility/file-status-code-enumerator.md) para os valores possíveis).  
  
 pnEventsRemaining  
 [no, out] Retorna o número de entradas de permanecer na fila após esta chamada. Se esse número for grande, o chamador poderá optar por chamar o [SccQueryInfo](../extensibility/sccqueryinfo-function.md) para obter as informações de uma vez.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Obter eventos com êxito.|  
|SCC_E_OPNOTSUPPORTED|Não há suporte para essa função.|  
|SCC_E_NONSPECIFICERROR|Falha não específica.|  
  
## <a name="remarks"></a>Comentários  
 Essa função é chamada durante o processamento ocioso para ver se houve quaisquer atualizações de status para arquivos sob controle de origem. O plug-in de controle de origem mantém o status de todos os arquivos que ele sabe sobre e sempre que uma alteração de status é observada pelo plug-in, o status e o arquivo associado são armazenadas em uma fila. Quando `SccGetEvents` é chamado, a parte superior elemento da fila é recuperado e retornado. Essa função é restrito para retornar somente informações armazenadas em cache anteriormente e deve ter um retorno muito rápido (ou seja, sem leitura do disco ou pedindo o sistema de controle do código-fonte status); Caso contrário, o desempenho do IDE pode começar a ser degradada.  
  
 Se não houver nenhuma atualização de status de relatório, o plug-in de controle de origem armazena uma cadeia de caracteres vazia no buffer apontado por `lpFileName`. Caso contrário, o plug-in armazena o nome de caminho completo do arquivo para o qual as informações de status foi alterado e retorna o código de status apropriado (um dos valores detalhados em [código de Status do arquivo](../extensibility/file-status-code-enumerator.md)).  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [Código de Status do arquivo](../extensibility/file-status-code-enumerator.md)
