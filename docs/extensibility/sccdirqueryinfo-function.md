---
title: "Função SccDirQueryInfo | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
caps.latest.revision: 14
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
ms.openlocfilehash: 1b83fff70e81739afd021e603687014169da8eeb
ms.lasthandoff: 02/22/2017

---
# <a name="sccdirqueryinfo-function"></a>Função SccDirQueryInfo
Essa função examina uma lista de diretórios totalmente qualificados de seu status atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
SCCRTN SccDirQueryInfo(  
LPVOID  pContext,  
LONG    nDirs,  
LPCSTR* lpDirNames,  
LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pContext  
 [in] A estrutura de contexto de plug-in de controle de origem.  
  
 nDirs  
 [in] O número de diretórios selecionados a serem consultados.  
  
 lpDirNames  
 [in] Uma matriz de caminhos totalmente qualificados dos diretórios a serem consultados.  
  
 lpStatus  
 [no, out] Uma estrutura de matriz para o plug-in para retornar os sinalizadores de status de controle de origem (consulte [código de Status do diretório](../extensibility/directory-status-code-enumerator.md) para obter detalhes).  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|A consulta foi bem-sucedida.|  
|SCC_E_OPNOTSUPPORTED|O sistema de controle de código fonte não oferece suporte a esta operação.|  
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle de origem, provavelmente devido a problemas de rede ou de contenção. Recomenda-se uma nova tentativa.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Falha não específica.|  
  
## <a name="remarks"></a>Comentários  
 A função preenche uma matriz de retorno com uma máscara de bits dos bits do `SCC_DIRSTATUS` família (consulte [código de Status do diretório](../extensibility/directory-status-code-enumerator.md)), uma entrada para cada diretório fornecido. A matriz de status é alocada pelo chamador.  
  
 O IDE usa essa função antes de um diretório é renomeado para verificar se o diretório está sob controle do código-fonte consultando se ele tem um projeto correspondente. Se o diretório não está sob controle de origem, o IDE pode fornecer o aviso apropriado para o usuário.  
  
> [!NOTE]
>  Se um plug-in de controle de origem optar por não implementar um ou mais dos valores de status, o bits não implementados devem ser definidos como zero.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [Código de Status do diretório](../extensibility/directory-status-code-enumerator.md)
