---
title: "Função SccRunScc | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
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
ms.openlocfilehash: a9db0777ff91bc01688164e5b38c8ede2c005d77
ms.lasthandoff: 02/22/2017

---
# <a name="sccrunscc-function"></a>Função SccRunScc
Essa função chama a ferramenta de administração de controle de origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
SCCRTN SccRunScc(  
   LPVOID  pvContext,  
   HWND    hWnd,  
   LONG    nFiles,  
   LPCSTR* lpFileNames  
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
 [in] Matriz de nomes de arquivo selecionado.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|A ferramenta de administração de controle de origem foi invocada com êxito.|  
|SCC_I_OPERATIONCANCELED|A operação foi cancelada.|  
|SCC_E_INITIALIZEFAILED|Falha ao inicializar o sistema de controle de origem.|  
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle de origem, provavelmente devido a problemas de rede ou de contenção.|  
|SCC_E_CONNECTIONFAILURE|Falha ao conectar ao sistema de controle de origem.|  
|SCC_E_FILENOTCONTROLLED|O arquivo selecionado não está sob controle de origem.|  
|SCC_E_NONSPECIFICERROR|Falha não específica.|  
  
## <a name="remarks"></a>Comentários  
 Essa função permite que o chamador acessar toda a gama de recursos do sistema de controle de origem por meio de uma ferramenta de administração externa. Se o sistema de controle de origem não tem nenhuma interface do usuário, o plug-in de controle de origem pode implementar uma interface para realizar funções administrativas necessárias.  
  
 Essa função é chamada com uma contagem e uma matriz de nomes de arquivo para os arquivos selecionados no momento. Se a ferramenta de administração oferece suporte a ele, a lista de arquivos pode ser usada para pré-selecionar arquivos na interface de administração; Caso contrário, a lista pode ser ignorada.  
  
 Esta função geralmente é chamada quando o usuário seleciona o **iniciar \<servidor de controle de origem >** do **arquivo** -> **controle de origem** menu. Isso **iniciar** opção de menu pode ser sempre desabilitada ou até mesmo ocultada pela configuração de uma entrada de registro. Consulte [como: instalar um plug-in de controle de origem](../extensibility/internals/how-to-install-a-source-control-plug-in.md) para obter detalhes. Essa função é chamada apenas se [SccInitialize](../extensibility/sccinitialize-function.md) retorna o `SCC_CAP_RUNSCC` bit de recurso (consulte [sinalizadores de recurso](../extensibility/capability-flags.md) para obter detalhes sobre esse e outros bits de capacidade).  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [Como: instalar um plug-in de controle de origem](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [Sinalizadores de recurso](../extensibility/capability-flags.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)
