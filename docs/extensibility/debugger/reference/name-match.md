---
title: NAME_MATCH | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- NAME_MATCH
helpviewer_keywords:
- NAME_MATCH enumeration
ms.assetid: 3842c417-a3c9-4259-a05f-52b64b829ef6
caps.latest.revision: 8
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
ms.openlocfilehash: cae44c561a72a94680f6a456cb9faa58ab914437
ms.lasthandoff: 02/22/2017

---
# <a name="namematch"></a>NAME_MATCH
Seleciona a opção caso para correspondência de nomes.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
typedef enum {   
   nmNone            = 0,  
   nmCaseSensitive   = 1,  
   nmCaseInsensitive = 2  
} NAME_MATCH;  
```  
  
```c#  
public enum NameMatchOptions {   
   nmNone            = 0,  
   nmCaseSensitive   = 1,  
   nmCaseInsensitive = 2  
}  
```  
  
## <a name="members"></a>Membros  
 nmNone  
 Nenhuma opção é especificada.  
  
 nmCaseSensitive  
 Indica que os nomes a serem correspondidos diferenciam maiusculas de minúsculas.  
  
 nmCaseInsensitive  
 Indica que os nomes a serem correspondidos não diferenciam maiusculas de minúsculas.  
  
## <a name="remarks"></a>Comentários  
 Passada como um argumento para os métodos a seguir:  
  
-   [GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)  
  
-   [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)  
  
-   [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)  
  
-   [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)   
 [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)   
 [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)   
 [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)
