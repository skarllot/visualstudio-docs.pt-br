---
title: "IDiaSymbol::get_hasSecurityChecks | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Método IDiaSymbol::get_hasSecurityChecks"
ms.assetid: 4bb51f62-8645-41a4-bc44-1451010623fd
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_hasSecurityChecks
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera um sinalizador que especifica se o compiland ou a função foi compilada com verificações de segurança de saturação de buffer \(por exemplo, o [\/GS \(verificação de segurança do buffer\)](/visual-cpp/build/reference/gs-buffer-security-check) opção de compilador\).  
  
## Sintaxe  
  
```cpp#  
HRESULT get_hasSecurityChecks(  
   BOOL *pFlag  
);  
```  
  
#### Parâmetros  
 `pFlag`  
 \[out\] Retorna `TRUE` se a função tiver quaisquer verificações de segurança; Caso contrário, retornará `FALSE`.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retornará `S_FALSE` ou um código de erro.  
  
> [!NOTE]
>  Um valor de retorno de `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## Requisitos  
  
|Requisito|Descrição|  
|---------------|---------------|  
|Cabeçalho:|dia2.h|  
|Versão:|V 8.0 do SDK DIA|  
  
## Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [\/GS \(verificação de segurança do buffer\)](/visual-cpp/build/reference/gs-buffer-security-check)