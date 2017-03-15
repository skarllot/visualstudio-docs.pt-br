---
title: "Função CvReleaseProvider | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 501fbce45fb071d5f023bfd22078069c383b87d1

---
# <a name="cvreleaseprovider-function"></a>Função CvReleaseProvider
Libera o provedor de marcador. A liberação do provedor de marcador não afetará a série de marcador criada anteriormente desse provedor. A série de marcador deve ser liberada separadamente pela chamada CvReleaseMarkerSeries. A falha ao liberar o provedor causa uma perda de memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CvReleaseProvider(  
   _In_ PCV_PROVIDER pProvider  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pProvider`  
 Contexto de provedor. Não pode ser NULL.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK quando o provedor é liberado com êxito ou código de erro no caso de erros. Use as macros SUCCEEDED/FAILED para verificar a condição de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** cvmarkers.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência de biblioteca C++](../profiling/cpp-library-reference.md)


<!--HONumber=Feb17_HO4-->


