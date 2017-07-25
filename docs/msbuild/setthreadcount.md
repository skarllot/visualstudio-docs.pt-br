---
title: SetThreadCount | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SetThreadCount
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SetThreadCount
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
caps.latest.revision: 4
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 11a9cee75f912c5fb31cf4a031644abe9c63d744
ms.openlocfilehash: d46fea0afc0d6d47a431954dc80a0b58611de0f3
ms.contentlocale: pt-br
ms.lasthandoff: 06/03/2017

---
# <a name="setthreadcount"></a>SetThreadCount
Define a contagem de thread global e atribui valores para o thread atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT WINAPI SetThreadCount(int threadCount);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 [in] `threadCount`  
 O número máximo de threads.  
  
## <a name="return-value"></a>Valor de retorno  
 Um **HRESULT** com o conjunto de bit **SUCCEEDED** se a contagem de thread foi atualizada.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** FileTracker.h
