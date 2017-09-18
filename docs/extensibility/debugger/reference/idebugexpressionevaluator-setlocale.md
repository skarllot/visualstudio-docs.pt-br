---
title: IDebugExpressionEvaluator::SetLocale | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugExpressionEvaluator::SetLocale
helpviewer_keywords:
- IDebugExpressionEvaluator::SetLocale method
ms.assetid: d3d2027d-74e2-4ae6-bcc7-59d12f873b7c
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
ms.openlocfilehash: e3b0d4b160aa3d0608a16b0969c65763fae7eeb1
ms.lasthandoff: 02/22/2017

---
# <a name="idebugexpressionevaluatorsetlocale"></a>IDebugExpressionEvaluator::SetLocale
Esse método define o idioma usado para criar resultados de impressão.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT SetLocale(   
   WORD wLangID  
);  
```  
  
```c#  
int SetLocale(  
   ushort wLangID  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `wLangID`  
 [in] O identificador de idioma.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método pode ser chamado várias vezes enquanto o avaliador de expressão (EE) é carregado para que o EE deve ser capaz de alternar idiomas dinamicamente. O EE usa essa localidade para retornar mensagens de erro e cadeias de caracteres no idioma apropriado.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
