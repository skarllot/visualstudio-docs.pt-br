---
title: "Função SccRename | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
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
ms.openlocfilehash: c896688743e6ff41fcc2fd5e11197ab36c45719e
ms.lasthandoff: 02/22/2017

---
# <a name="sccrename-function"></a>Função SccRename
Essa função renomeia um arquivo no sistema de controle de origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
SCCRTN SccRename(  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName,  
   LPCSTR lpNewName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pvContext  
 [in] A estrutura de contexto de plug-in de controle de origem.  
  
 hWnd  
 [in] Um identificador para a janela do IDE que o plug-in de controle de origem pode usar como um pai para as caixas de diálogo que ele fornece.  
  
 lpFileName  
 [in] O nome de arquivo totalmente qualificado do arquivo que está sendo renomeado.  
  
 lpNewName  
 [in] O novo nome totalmente qualificado. Se o caminho do diretório é diferente, o arquivo foi movido de um subdiretório para outro.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|A operação de renomeação foi concluída com êxito.|  
|SCC_E_PROJNOTOPEN|O projeto não está aberto no controle de origem.|  
|SCC_E_FILENOTCONTROLLED|O arquivo não está sob controle de origem.|  
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle de origem, provavelmente devido a problemas de rede ou de contenção.|  
|SCC_E_NOTAUTHORIZED|O usuário não está autorizado para concluir esta operação.|  
|SCC_E_COULDNOTCREATEPROJECT|O projeto não pôde ser criado como parte do processo de renomeação.|  
|SCC_E_OPNOTPERFORMED|A operação não foi executada.|  
|SCC_E_NONSPECIFICERROR|Ocorreu um erro geral ou não especificado.|  
  
## <a name="remarks"></a>Comentários  
 Essa função pode ser usada para renomear um arquivo ou movê-lo de um local para outro no sistema de controle de origem. O plug-in de controle de origem não deve tentar acessar o arquivo no disco. É responsabilidade do IDE para renomear o arquivo local.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)
