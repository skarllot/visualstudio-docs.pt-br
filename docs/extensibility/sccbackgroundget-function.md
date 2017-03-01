---
title: "Função SccBackgroundGet | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
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
ms.openlocfilehash: 8bc845c2ef3cb4ece3e52dca272fdc75208e8dbd
ms.lasthandoff: 02/22/2017

---
# <a name="sccbackgroundget-function"></a>Função SccBackgroundGet
Esta função recupera do controle de origem cada dos arquivos especificados sem interação do usuário.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccBackgroundGet(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LONG    dwFlags,  
   LONG    dwBackgroundOperationID  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pContext  
 [in] O ponteiro de contexto de plug-in de controle de origem.  
  
 nFiles  
 [in] Número de arquivos especificados na `lpFileNames` matriz.  
  
 lpFileNames  
 [no, out] Matriz de nomes de arquivos a serem recuperados.  
  
> [!NOTE]
>  Os nomes devem ser totalmente qualificado de nomes de arquivo local.  
  
 dwFlags  
 [in] Sinalizadores de comando (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 dwBackgroundOperationID  
 [in] Um valor exclusivo associado a esta operação.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Operação concluída com êxito.|  
|SCC_E_BACKGROUNDGETINPROGRESS|Recuperação de um plano de fundo já está em andamento (o plug-in de controle de origem deve retornar isso apenas se não dá suporte a operações em lotes simultâneos).|  
|SCC_I_OPERATIONCANCELED|A operação foi cancelada antes de serem concluídas.|  
  
## <a name="remarks"></a>Comentários  
 Essa função é sempre chamada em um thread diferente do que carregar o plug-in de controle de origem. Essa função não deve retornar até que seja feita; No entanto, ele pode ser chamado várias vezes com várias listas de arquivos, todos ao mesmo tempo.  
  
 O uso do `dwFlags` argumento é o mesmo que o [SccGet](../extensibility/sccget-function.md).  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGet](../extensibility/sccget-function.md)
