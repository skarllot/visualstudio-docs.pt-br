---
title: "Função SccDirDiff | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
caps.latest.revision: 15
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
ms.openlocfilehash: 3f39f9aa781751ae3f750aae5dccd694cd6a5d58
ms.lasthandoff: 02/22/2017

---
# <a name="sccdirdiff-function"></a>Função SccDirDiff
Esta função exibe as diferenças entre o diretório local atual no disco do cliente e o projeto sob controle de origem correspondente.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
SCCRTN SccDirDiff(  
   LPVOID    pContext,  
   HWND      hWnd,  
   LPCSTR    lpDirName,  
   LONG      dwFlags,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pContext  
 [in] A estrutura de contexto de plug-in de controle de origem.  
  
 hWnd  
 [in] Um identificador para a janela do IDE que o plug-in de controle de origem pode usar como um pai para as caixas de diálogo que ele fornece.  
  
 lpDirName  
 [in] Caminho totalmente qualificado para o diretório local para o qual mostram uma diferença visual.  
  
 dwFlags  
 [in] Sinalizadores de comando (consulte comentários seção).  
  
 pvOptions  
 [in] Opções de plug-in específico de controle de origem.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|O diretório em disco é o mesmo que o projeto no controle do código fonte.|  
|SCC_I_FILESDIFFER|O diretório no disco é diferente do projeto no controle do código fonte.|  
|SCC_I_RELOADFILE|Um arquivo ou projeto precisa ser recarregado.|  
|SCC_E_FILENOTCONTROLLED|O diretório não está sob controle do código fonte.|  
|SCC_E_NOTAUTHORIZED|O usuário não tem permissão para executar esta operação.|  
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle de origem, provavelmente devido a problemas de rede ou de contenção. Recomenda-se uma nova tentativa.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Falha não específica.|  
|SCC_E_FILENOTEXIST|Não foi possível localizar o diretório local.|  
  
## <a name="remarks"></a>Comentários  
 Essa função é usada para instruir o controle da fonte de plug-in para exibir ao usuário uma lista de alterações para um diretório especificado. O plug-in abre sua própria janela, em um formato de sua escolha, para exibir as diferenças entre o diretório do usuário no disco e o projeto sob controle de versão correspondente.  
  
 Se uma comparação oferece suporte a plug-in de diretórios em todas, deve suportar comparação de diretórios em uma base de nome de arquivo mesmo se não há suporte para as opções "comparação rápida".  
  
|`dwFlags`|Interpretação|  
|---------------|--------------------|  
|SCC_DIFF_IGNORECASE|Comparação de maiusculas e minúsculas (pode ser usado para comparação rápida ou visual).|  
|SCC_DIFF_IGNORESPACE|Ignora o espaço em branco (pode ser usado para comparação rápida ou visual).|  
|SCC_DIFF_QD_CONTENTS|Se houver suporte a plug-in de controle de origem, compara silenciosamente o diretório, byte por byte.|  
|SCC_DIFF_QD_CHECKSUM|Se suportado pelo plug-in, silenciosamente compara o diretório por meio de uma soma de verificação ou, se não houver suporte, volta para SCC_DIFF_QD_CONTENTS.|  
|SCC_DIFF_QD_TIME|Se suportado pelo plug-in, silenciosamente compara o diretório por meio de seu carimbo de hora ou, se não houver suporte, recai em SCC_DIFF_QD_CHECKSUM ou SCC_DIFF_QD_CONTENTS.|  
  
> [!NOTE]
>  Essa função usa os mesmos sinalizadores de comando como o [SccDiff](../extensibility/sccdiff-function.md). No entanto, um plug-in de controle de origem pode optar por não oferece suporte à operação de "comparação rápida" para diretórios.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)
