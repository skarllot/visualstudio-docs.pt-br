---
title: "Função SccEndBatch | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
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
ms.openlocfilehash: 62b5ca139d52854ae42622f7443145046e82bc6f
ms.lasthandoff: 02/22/2017

---
# <a name="sccendbatch-function"></a>Função SccEndBatch
Essa função conclui um lote de operações de controle do código-fonte. Esses lotes não podem ser aninhados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
SCCRTN SccEndBatch(void);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Nenhum.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Lote de operações concluídas com êxito.|  
|SCC_E_UNKNOWNERROR|Falha não específica.|  
  
## <a name="remarks"></a>Comentários  
 Lotes de controle do código-fonte são usados para executar as mesmas operações de controle de origem em vários projetos ou vários contextos. Lotes podem ser usados para eliminar as caixas de diálogo redundantes a experiência do usuário durante uma operação em lote. O [SccBeginBatch](../extensibility/sccbeginbatch-function.md) e `SccEndBatch` função são usados como um par para indicar o início e o final de uma operação. Eles não podem ser aninhados.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
