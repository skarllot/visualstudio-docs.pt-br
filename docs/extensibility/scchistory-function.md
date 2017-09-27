---
title: "Função SccHistory | Microsoft Docs"
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 0efb8505fa59957f8178214d64c7ac0d979a3359
ms.contentlocale: pt-br
ms.lasthandoff: 09/26/2017

---
# <a name="scchistory-function"></a>Função SccHistory
Esta função exibe o histórico de arquivos especificados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
 [in] Um identificador para a janela do IDE que o plug-in de controle de origem pode usar como um pai para todas as caixas de diálogo que ele oferece.  
  
 `nFiles`  
 [in] Número de arquivos especificados na `lpFileName` matriz.  
  
 `lpFileName`  
 [in] Matriz de nomes totalmente qualificados de arquivos.  
  
 `fOptions`  
 [in] Sinalizadores de comando (não usados no momento).  
  
 `pvOptions`  
 [in] Opções de plug-in específico de controle de origem.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Histórico de versão foi obtido com êxito.|  
|SCC_I_RELOADFILE|O sistema de controle de origem modificado, na verdade, o arquivo em disco ao buscar o histórico (por exemplo, fazendo com que uma versão antiga dele), portanto o IDE deve recarregar o arquivo.|  
|SCC_E_FILENOTCONTROLLED|O arquivo não está sob controle de origem.|  
|SCC_E_OPNOTSUPPORTED|O sistema de controle de origem não oferece suporte a esta operação.|  
|SCC_E_NOTAUTHORIZED|O usuário não tem permissão para executar esta operação.|  
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle de origem, provavelmente devido a problemas de rede ou de contenção. Recomenda-se uma nova tentativa.|  
|SCC_E_PROJNOTOPEN|O projeto não foi aberto.|  
|SCC_E_NONSPECIFICERROR|Falha não específica. Não foi possível obter o histórico de arquivos.|  
  
## <a name="remarks"></a>Comentários  
 O plug-in de controle de origem pode exibir sua própria caixa de diálogo para exibir o histórico de cada arquivo, usando `hWnd` como a janela pai. Como alternativa, o texto opcional saída de retorno de chamada de função fornecido para o [SccOpenProject](../extensibility/sccopenproject-function.md) pode ser usado, se houver suporte.  
  
 Observe que, em determinadas circunstâncias, o arquivo que está sendo examinado pode ser alterados durante a execução desta chamada. Por exemplo, o [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] comando Histórico dá ao usuário a oportunidade de obter uma versão antiga do arquivo. Nesse caso, a fonte de controlar o plug-in retorna `SCC_I_RELOAD` para avisar o IDE que precisa recarregar o arquivo.  
  
> [!NOTE]
>  Se o plug-in de controle de origem não dá suporte a essa função para uma matriz de arquivos, somente o histórico de arquivos para o primeiro arquivo pode ser exibido.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)
