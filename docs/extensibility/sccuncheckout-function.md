---
title: "Função SccUncheckout | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
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
ms.openlocfilehash: 36b814be1c5515e1d9929c3a0cdb83631bbf12d7
ms.lasthandoff: 02/22/2017

---
# <a name="sccuncheckout-function"></a>Função SccUncheckout
Essa função desfazer uma operação de check-out anterior, restaurando assim o conteúdo do arquivo selecionado ou arquivos para o estado antes do check-out. Todas as alterações feitas no arquivo desde o check-out serão perdidas.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
SCCRTN SccUncheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pvContext  
 [in] A estrutura de contexto de plug-in de controle de origem.  
  
 hWnd  
 [in] Um identificador para a janela do IDE que o plug-in de controle de origem pode usar como um pai para as caixas de diálogo que ele fornece.  
  
 nFiles  
 [in] Número de arquivos especificados na `lpFileNames` matriz.  
  
 lpFileNames  
 [in] Matriz de nomes de caminho local totalmente qualificado dos arquivos para os quais desfazer um check-out.  
  
 fOptions  
 [in] Sinalizadores de comando (não usados).  
  
 pvOptions  
 [in] Opções de plug-in específico de controle de origem.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Desfazer check-out foi bem-sucedida.|  
|SCC_E_FILENOTCONTROLLED|O arquivo selecionado não está sob controle do código fonte.|  
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle de origem, provavelmente devido a problemas de rede ou de contenção. Recomenda-se uma nova tentativa.|  
|SCC_E_NONSPECIFICERROR|Falha não específica. Desfazer check-out não teve êxito.|  
|SCC_E_NOTCHECKEDOUT|O usuário não tem o arquivo com check-out.|  
|SCC_E_NOTAUTHORIZED|O usuário não tem permissão para executar esta operação.|  
|SCC_E_PROJNOTOPEN|O projeto do controle de origem não foi aberto.|  
|SCC_I_OPERATIONCANCELED|A operação foi cancelada antes da conclusão.|  
  
## <a name="remarks"></a>Comentários  
 Após essa operação, o `SCC_STATUS_CHECKEDOUT` e `SCC_STATUS_MODIFIED` sinalizadores serão ambos ser desmarcados para os arquivos no qual desfazer check-out foi executado.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)
