---
title: "Função SccGetExtendedCapabilities | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
caps.latest.revision: 16
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
ms.openlocfilehash: c0331979eaae065730dab5d5daf0e226844d5e7a
ms.lasthandoff: 02/22/2017

---
# <a name="sccgetextendedcapabilities-function"></a>Função SccGetExtendedCapabilities
Esta função retorna os recursos adicionais compatíveis com o plug-in de controle de origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccGetExtendedCapabilities(  
   LPVOID pContext,  
   LONG lSccExCaps,  
   LPBOOL pbSupported  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pContext  
 [in] O ponteiro de contexto de plug-in de controle de origem.  
  
 lSccExCaps  
 [in] Um sinalizador que especifica uma funcionalidade estendida para teste (consulte a tabela de código de recurso estendido em [sinalizadores de recurso](../extensibility/capability-flags.md) para os sinalizadores de possíveis).  
  
 pbSupported  
 [out] Retorna diferente de zero (`TRUE`) se houver suporte para o recurso especificado; caso contrário, retorna zero (`FALSE`).  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|A operação de recurso get foi concluída com êxito.|  
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Ocorreu um erro desconhecido ou não especificado.|  
  
## <a name="remarks"></a>Comentários  
 Este método é chamado por demanda. ou seja, quando um recurso precisa ser testado, esse método é chamado para determinar se recursos com suporte. Sinalizador de apenas um por vez é especificado.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [Códigos de erro](../extensibility/error-codes.md)   
 [Sinalizadores de recurso](../extensibility/capability-flags.md)
