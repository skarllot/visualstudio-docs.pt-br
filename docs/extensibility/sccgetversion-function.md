---
title: "Função SccGetVersion | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: 12
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
ms.openlocfilehash: 0fcabba17dbc134d86c286c851054376dcc2cf39
ms.lasthandoff: 02/22/2017

---
# <a name="sccgetversion-function"></a>Função SccGetVersion
Essa função obtém o número de versão da API de plug-in de controle fonte compatíveis com o plug-in de controle de origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
LONG SccGetVersion(void);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Nenhum.  
  
## <a name="return-value"></a>Valor de retorno  
 Um `LONG` tipo de dados que contém o número de versão da API do plug-in de controle de origem com suporte:  
  
|WORD|Descrição|  
|----------|-----------------|  
|HIWORD|Versão principal|  
|LOWORD|Versão secundária|  
  
## <a name="remarks"></a>Comentários  
 Por exemplo, se um plug-in de controle de origem suporta a versão 1.3 da API de plug-in de controle de origem, essa função retornará 0x0103.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)
