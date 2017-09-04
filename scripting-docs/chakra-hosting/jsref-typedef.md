---
title: Typedef JsRef | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6aafc39f-6b9c-457f-8bf0-48831bffe9b8
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: d9d4c478a45f53e83dfa59fdde21cfa4c988c92e
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsref-typedef"></a>Typedef JsRef
Uma referência a um objeto possuído pelo coletor de lixo Chakra.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef void *JsRef;  
```  
  
## <a name="remarks"></a>Comentários  
 Um tempo de execução do Chakra rastreará automaticamente referências JsRef enquanto estiverem ativas armazenadas em variáveis locais ou em parâmetros (ou seja, na pilha). Armazenar uma JsRef em outro lugar além da pilha exige chamar JsAddRef e JsRelease para gerenciar a vida útil do objeto, caso contrário, o coletor de lixo poderá liberar o objeto enquanto ele ainda estiver em uso.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
