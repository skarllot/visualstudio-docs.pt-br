---
title: "Função SccGetUserOption | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
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
ms.openlocfilehash: cbc06f25a57ee3b7ebab6f697cebc21f702d3bc8
ms.lasthandoff: 02/22/2017

---
# <a name="sccgetuseroption-function"></a>Função SccGetUserOption
Esta função recupera uma variedade de opções específicas do usuário.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccGetUserOption(  
   LPVOID pContext,  
   LONG nOption,  
   LPLONG lpVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pContext  
 [in] O ponteiro de contexto de plug-in de controle de origem.  
  
 nOption  
 [in] Opção de recuperação (consulte comentários para obter possíveis opções).  
  
 lpVal  
 [out] Valor associado com a opção.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Opção foi recuperada com êxito.|  
|SCC_E_OPNOTSUPPORTED|Não há suporte para a opção.|  
|SCC_E_NONSPECIFICERROR|Ocorreu um erro não especificado.|  
  
## <a name="remarks"></a>Comentários  
 As opções a seguir são suportadas por este comando:  
  
|Opção de usuário|Descrição|  
|-----------------|-----------------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Determina se o usuário deseja fazer check-out da versão local dos arquivos. `lpVal`recebe `SCC_USEROPT_COLV_YES` (o usuário deseja fazer check-out de arquivos locais) ou `SCC_USEROPT_COLV_NO`.|  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [Códigos de erro](../extensibility/error-codes.md)
