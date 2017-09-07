---
title: "Função SccCheckin | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
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
ms.openlocfilehash: b082ca831c17dcab3fbc95f8dd547da23a1f8982
ms.contentlocale: pt-br
ms.lasthandoff: 09/06/2017

---
# <a name="scccheckin-function"></a>Função SccCheckin
Essa função verifica no anteriormente arquivos com check-out ao sistema de controle de origem, armazenar as alterações e criar uma nova versão. Esta função é chamada com uma contagem e uma matriz de nomes de arquivos para fazer check-in.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccCheckin (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPSTR*    lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pvContext  
 [in] A estrutura de contexto de plug-in de controle de origem.  
  
 hWnd  
 [in] Um identificador para a janela do IDE que o plug-in do SCC pode usar como um pai para todas as caixas de diálogo que ele oferece.  
  
 nFiles  
 [in] Número de arquivos selecionados para fazer check-in.  
  
 lpFileNames  
 [in] Matriz de nomes de caminho local totalmente qualificado de arquivos para fazer check-in.  
  
 lpComment  
 [in] Comentário a ser aplicado a cada um dos arquivos selecionados em check-in. Isso é `NULL` se o plug-in de controle de origem deve solicitar um comentário.  
  
 fOptions  
 [in] Sinalizadores de comando, 0 ou `SCC_KEEP_CHECKEDOUT`.  
  
 pvOptions  
 [in] Opções de plug-in específico de SCC.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Arquivos foi aprovado com êxito.|  
|SCC_E_FILENOTCONTROLLED|O arquivo selecionado não está sob controle do código fonte.|  
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle de origem, provavelmente devido a problemas de rede ou de contenção. Recomenda-se uma nova tentativa.|  
|SCC_E_NONSPECIFICERROR|Falha não específica. Arquivo não foi aprovado.|  
|SCC_E_NOTCHECKEDOUT|O usuário não tem check-out do arquivo, portanto, não é possível fazer check-in.|  
|SCC_E_CHECKINCONFLICT|Não foi possível executar o check-in porque:<br /><br /> -Outro usuário fez check em frente e `bAutoReconcile` era falso.<br /><br /> -ou-<br /><br /> -A mesclagem automática não pode ser feita (por exemplo, quando os arquivos são binários).|  
|SCC_E_VERIFYMERGE|Arquivo tiver sido mesclados automaticamente, mas não tiver sido incluído com a verificação de usuário pendente.|  
|SCC_E_FIXMERGE|Arquivo tiver sido mesclados automaticamente, mas não tiver sido incluído devido a um conflito de mesclagem deve ser resolvido manualmente.|  
|SCC_E_NOTAUTHORIZED|O usuário não tem permissão para executar esta operação.|  
|SCC_I_OPERATIONCANCELED|Operação foi cancelada antes da conclusão.|  
|SCC_I_RELOADFILE|Um arquivo ou projeto precisa ser recarregado.|  
|SCC_E_FILENOTEXIST|Arquivo local não foi encontrado.|  
  
## <a name="remarks"></a>Comentários  
 O comentário se aplica a todos os arquivos em check-in. O argumento de comentário pode ser um `null` de cadeia de caracteres, caso em que o plug-in de controle de origem pode solicitar ao usuário uma cadeia de caracteres de comentário para cada arquivo.  
  
 O `fOptions` argumento pode ser fornecido um valor de `SCC_KEEP_CHECKEDOUT` sinalizador para indicar a intenção do usuário para o arquivo de check-in e check-out novamente.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API do plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
