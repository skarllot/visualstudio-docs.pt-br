---
title: IDebugDocumentPositionOffset2::GetRange | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
caps.latest.revision: 6
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
ms.openlocfilehash: d14c212a3cb4499996ba6cf4d73d0b2fca73f7bc
ms.lasthandoff: 02/22/2017

---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
Recupera o intervalo para a posição atual do documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetRange(  
   DWORD* pdwBegOffset,  
   DWORD* pdwEndOffset  
);  
```  
  
```c#  
public int GetRange(  
   ref uint pdwBegOffset,  
   ref uint pdwEndOffset  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdwBegOffset`  
 [no, out] Deslocamento da posição inicial do intervalo. Defina este parâmetro como um valor nulo se essas informações não são necessárias.  
  
 `pdwEndOffset`  
 [no, out] Deslocamento para a posição final do intervalo. Defina este parâmetro como um valor nulo se essas informações não são necessárias.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O intervalo especificado em uma posição de documento para um ponto de interrupção de local é usado pelo mecanismo de depuração (DE) para procurar uma instrução que realmente contribui com código em frente. Por exemplo, considere o seguinte código:  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 Linha 5 não contribui nenhum código para o programa que está sendo depurado. Se desejar que o depurador que define o ponto de interrupção na linha 5 DE para procurar uma determinada quantidade para a primeira linha que contribui com o código, o depurador deve especificar um intervalo que inclui linhas adicionais candidato onde um ponto de interrupção pode ser colocado corretamente. O DE seria Pesquisar para frente por essas linhas até que ela encontrou uma linha que pode aceitar um ponto de interrupção.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
