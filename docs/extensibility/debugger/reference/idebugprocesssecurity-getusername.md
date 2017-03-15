---
title: IDebugProcessSecurity::GetUserName | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 4
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
ms.openlocfilehash: 7d28882bb12a5429bc12f8eb6f3fa6d0c53a0eb0
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Obtém o nome de usuário do fornecedor de porta.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetUserName(  
    BSTR *pbstrUserName  
);  
```  
  
```c#  
int GetUserName (  
    string pbstrUserName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbstrUserName`  
 [out] Uma cadeia de caracteres que contém o nome de usuário.  
  
## <a name="return-value"></a>Valor de retorno  
 Se o método for bem-sucedido, ele retornará `S_OK`. Caso contrário, ele retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 `GetUserName`Retorna o nome de usuário que é exibido no **nome de usuário** coluna o **anexar ao processo** caixa de diálogo. Para exibir o **anexar ao processo** caixa de diálogo, clique em **anexar ao processo** no **ferramentas** menu o [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE).  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
