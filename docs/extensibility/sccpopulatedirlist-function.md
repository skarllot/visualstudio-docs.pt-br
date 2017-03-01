---
title: "Função SccPopulateDirList | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
caps.latest.revision: 11
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
ms.openlocfilehash: 1f4a2668a5e4c67f048ae17b1bbc683509aeabae
ms.lasthandoff: 02/22/2017

---
# <a name="sccpopulatedirlist-function"></a>Função SccPopulateDirList
Esta função determina quais diretórios e (opcionalmente) arquivos são armazenados no controle de origem, dada uma lista de diretórios para examinar.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccPopulateDirList(  
   LPVOID        pContext,  
   LONG          nDirs,  
   LPCSTR*       lpDirPaths,  
   POPDIRLISTFUNCpfnPopulate,  
   LPVOID        pvCallerData,  
   LONG          fOptions  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pContext  
 [in] O ponteiro de contexto de plug-in de controle de origem.  
  
 nDirs  
 [in] Número de caminhos de diretório no `lpDirPaths` matriz.  
  
 lpDirPaths  
 [in] Matriz de caminhos de diretório para examinar.  
  
 pfnPopulate  
 [in] Função de retorno de chamada para chamar para cada caminho de diretório e (opcionalmente) o nome de arquivo no `lpDirPaths` (consulte [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) para obter detalhes).  
  
 pvCallerData  
 [in] Inalterado do valor a ser passado para a função de retorno de chamada.  
  
 fOptions  
 [in] Uma combinação de valores que controlam como os diretórios são processados (consulte a seção "Sinalizadores PopulateDirList" [os sinalizadores de bit usados pelos comandos específicos](../extensibility/bitflags-used-by-specific-commands.md) para os valores possíveis).  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|A operação foi concluída com êxito.|  
|SCC_E_UNKNOWNERROR|Ocorreu um erro.|  
  
## <a name="remarks"></a>Comentários  
 Somente os diretórios e (opcionalmente nomes de arquivos que realmente estão no repositório de controle de origem) são passados para a função de retorno de chamada.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [Sinalizadores de bit usados pelos comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [Códigos de erro](../extensibility/error-codes.md)
