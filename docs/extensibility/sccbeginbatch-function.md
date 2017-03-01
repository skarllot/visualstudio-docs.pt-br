---
title: "Função SccBeginBatch | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
caps.latest.revision: 14
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
ms.openlocfilehash: d7a1306e928cb99a09e7c08136eb239872cb4948
ms.lasthandoff: 02/22/2017

---
# <a name="sccbeginbatch-function"></a>Função SccBeginBatch
Essa função inicia uma sequência de lotes de operações de controle do código-fonte. O [SccEndBatch](../extensibility/sccendbatch-function.md) será chamada para finalizar o lote. Esses lotes não podem ser aninhados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
SCCRTN SccBeginBatch(void);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Nenhum.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Lote de operações começou com êxito.|  
|SCC_E_UNKNOWNERROR|Falha não específica.|  
  
## <a name="remarks"></a>Comentários  
 Lotes de controle do código-fonte são usados para executar as mesmas operações em vários projetos ou vários contextos. Lotes podem ser usados para eliminar as caixas de diálogo do projeto de redundantes a experiência do usuário durante uma operação em lote. O `SccBeginBatch` função e o [SccEndBatch](../extensibility/sccendbatch-function.md) são usados como um par de função para indicar o início e o final de uma operação. Eles não podem ser aninhados. `SccBeginBatch`define um sinalizador que indica que uma operação em lote está em andamento.  
  
 Enquanto uma operação em lote estiver em vigor, o plug-in de controle de origem deve apresentar no máximo uma caixa de diálogo para qualquer pergunta ao usuário e aplicar a resposta da caixa de diálogo em todas as operações subsequentes.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)
