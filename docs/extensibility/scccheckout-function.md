---
title: "Função SccCheckout | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
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
ms.openlocfilehash: 91f9bb8bc5c51f6bee857b19fa3853e168ccf858
ms.lasthandoff: 02/22/2017

---
# <a name="scccheckout-function"></a>Função SccCheckout
Dada uma lista de nomes de arquivo totalmente qualificado, essa função verifica no disco local. O comentário se aplica a todos os arquivos que está sendo feito check-out. O argumento de comentário pode ser um `null` cadeia de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
SCCRTN SccCheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
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
 [in] Número de arquivos selecionados para fazer check-out.  
  
 lpFileNames  
 [in] Matriz de nomes de caminho local totalmente qualificado dos arquivos para fazer check-out.  
  
 lpComment  
 [in] Comentário a ser aplicado a cada um dos arquivos selecionados check-out.  
  
 fOptions  
 [in] Sinalizadores de comando (consulte [os sinalizadores de bit usados pelos comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)).  
  
 pvOptions  
 [in] Opções de plug-in específico de controle de origem.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Check-out foi bem-sucedida.|  
|SCC_E_FILENOTCONTROLLED|O arquivo selecionado não está sob controle do código fonte.|  
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle de origem, provavelmente devido a problemas de rede ou de contenção. Recomenda-se uma nova tentativa.|  
|SCC_E_NOTAUTHORIZED|O usuário não tem permissão para executar esta operação.|  
|SCC_E_NONSPECIFICERROR|Falha não específica. O arquivo não foi extraído.|  
|SCC_E_ALREADYCHECKEDOUT|O usuário já tiver o check-out do arquivo.|  
|SCC_E_FILEISLOCKED|O arquivo está bloqueado, proibindo a criação de novas versões.|  
|SCC_E_FILEOUTEXCLUSIVE|Outro usuário fez um check-out exclusivo nesse arquivo.|  
|SCC_I_OPERATIONCANCELED|A operação foi cancelada antes da conclusão.|  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [Sinalizadores de bit usados pelos comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)
