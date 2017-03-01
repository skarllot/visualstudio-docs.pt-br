---
title: "Função SccAddFilesFromSCC | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
caps.latest.revision: 17
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
ms.openlocfilehash: 1f3ba293d60c44f91813c587fd0b0c3ac2df9d2d
ms.lasthandoff: 02/22/2017

---
# <a name="sccaddfilesfromscc-function"></a>Função SccAddFilesFromSCC
Essa função adiciona uma lista de arquivos do controle de origem para o projeto aberto no momento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccAddFilesFromSCC(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LPSTR   lpUser,  
   LPSTR   lpAuxProjPath,  
   LONG    cFiles,  
   LPCSTR* lpFilePaths,  
   LPCSTR  lpDestination,  
   LPCSTR  lpComment,  
   LPBOOL  pbResults  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pContext  
 [in] O ponteiro de contexto de plug-in de controle de origem.  
  
 hWnd  
 [in] Um identificador para a janela do IDE que o plug-in de controle de origem pode usar como um pai para as caixas de diálogo que ele fornece.  
  
 lpUser  
 [no, out] O nome de usuário (até SCC_USER_SIZE, incluindo o terminador nulo).  
  
 lpAuxProjPath  
 [no, out] Auxiliar cadeia de caracteres que identifica o projeto (até `SCC_PRJPATH_`tamanho, incluindo o terminador nulo).  
  
 cFiles  
 [in] Número de arquivos fornecido pelo `lpFilePaths`.  
  
 lpFilePaths  
 [no, out] Matriz de nomes de arquivo para adicionar ao projeto atual.  
  
 lpDestination  
 [in] O caminho de destino onde os arquivos devem ser gravados.  
  
 lpComment  
 [in] O comentário a ser aplicado a cada um dos arquivos que está sendo adicionados.  
  
 pbResults  
 [no, out] Matriz de sinalizadores de conjunto para indicar êxito (diferente de zero ou verdadeiro) ou falha (zero ou FALSE) para cada arquivo (tamanho da matriz deve ser pelo menos `cFiles` longo).  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_E_PROJNOTOPEN|Projeto não está aberto.|  
|SCC_E_OPNOTPERFORMED|Conexão não está no mesmo projeto, conforme especificado pelo`lpAuxProjPath.`|  
|SCC_E_NOTAUTHORIZED|Usuário não está autorizado a atualizar o banco de dados.|  
|SCC_E_NONSPECIFICERROR|Erro desconhecido.|  
|SCC_I_RELOADFILE|Um arquivo ou projeto precisa ser recarregado.|  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)
