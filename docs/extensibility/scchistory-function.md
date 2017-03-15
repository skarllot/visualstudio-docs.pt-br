---
title: "Função SccHistory | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
caps.latest.revision: 16
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
ms.openlocfilehash: 976c5bca18c4ed5bea54e45b2eef5620dd20f2d2
ms.lasthandoff: 02/22/2017

---
# <a name="scchistory-function"></a>Função SccHistory
Esta função exibe o histórico dos arquivos especificados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
SCCRTN SccHistory(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pvContext`  
 [in] A estrutura de contexto de plug-in de controle de origem.  
  
 `hWnd`  
 [in] Um identificador para a janela do IDE que o plug-in de controle de origem pode usar como um pai para as caixas de diálogo que ele fornece.  
  
 `nFiles`  
 [in] Número de arquivos especificados na `lpFileName` matriz.  
  
 `lpFileName`  
 [in] Matriz de nomes totalmente qualificados dos arquivos.  
  
 `fOptions`  
 [in] Sinalizadores de comando (não usados no momento).  
  
 `pvOptions`  
 [in] Opções de plug-in específico de controle de origem.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Histórico de versão foi obtido com êxito.|  
|SCC_I_RELOADFILE|O sistema de controle de origem modificado, na verdade, o arquivo no disco ao buscar o histórico (por exemplo, obtendo uma versão antiga), para que o IDE deve recarregar o arquivo.|  
|SCC_E_FILENOTCONTROLLED|O arquivo não está sob controle de origem.|  
|SCC_E_OPNOTSUPPORTED|O sistema de controle de origem não oferece suporte a esta operação.|  
|SCC_E_NOTAUTHORIZED|O usuário não tem permissão para executar esta operação.|  
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle de origem, provavelmente devido a problemas de rede ou de contenção. Recomenda-se uma nova tentativa.|  
|SCC_E_PROJNOTOPEN|O projeto não foi aberto.|  
|SCC_E_NONSPECIFICERROR|Falha não específica. Não foi possível obter o histórico de arquivos.|  
  
## <a name="remarks"></a>Comentários  
 O plug-in de controle de origem pode exibir sua própria caixa de diálogo para exibir o histórico de cada arquivo, usando `hWnd` como a janela pai. Como alternativa, o texto opcional de retorno de chamada de saída função fornecido para o [SccOpenProject](../extensibility/sccopenproject-function.md) pode ser usado, se houver suporte.  
  
 Observe que, em determinadas circunstâncias, o arquivo que está sendo examinado pode ser alterados durante a execução desta chamada. Por exemplo, o [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] comando history dá ao usuário a oportunidade de obter uma versão antiga do arquivo. Nesse caso, a fonte de controle plug-in retorna `SCC_I_RELOAD` para avisar o IDE que ele precisa recarregar o arquivo.  
  
> [!NOTE]
>  Se o plug-in de controle de origem não oferece suporte a essa função para uma matriz de arquivos, somente o histórico do arquivo para o primeiro arquivo pode ser exibido.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)
