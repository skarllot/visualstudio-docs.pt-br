---
title: "Função SccOpenProject | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
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
ms.openlocfilehash: ede88d10194016ca07b49a3d81ead64e17c0e859
ms.lasthandoff: 02/22/2017

---
# <a name="sccopenproject-function"></a>Função SccOpenProject
Essa função abre um projeto de controle do código-fonte existente ou cria um novo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
SCCRTN SccOpenProject (  
   LPVOID        pvContext,  
   HWND          hWnd,  
   LPSTR         lpUser,  
   LPCSTR        lpProjName,  
   LPCSTR        lpLocalProjPath,  
   LPSTR         lpAuxProjPath,  
   LPCSTR        lpComment,  
   LPTEXTOUTPROC lpTextOutProc,  
   LONG          dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pvContext  
 [in] A estrutura de contexto de plug-in de controle de origem.  
  
 hWnd  
 [in] Um identificador para a janela do IDE que o plug-in de controle de origem pode usar como um pai para as caixas de diálogo que ele fornece.  
  
 lpUser  
 [no, out] O nome do usuário (não deve exceder SCC_USER_SIZE, incluindo o terminador nulo).  
  
 lpProjName  
 [in] A cadeia de caracteres que identifica o nome do projeto.  
  
 lpLocalProjPath  
 [in] O caminho para a pasta de trabalho para o projeto.  
  
 lpAuxProjPath  
 [no, out] Uma cadeia auxiliar opcional que identifica o projeto (não deve exceder SCC_AUXPATH_SIZE, incluindo o terminador nulo).  
  
 lpComment  
 [in] Comentário para um novo projeto que está sendo criado.  
  
 lpTextOutProc  
 [in] Uma função de retorno de chamada opcional para exibir o texto de saída do plug-in de controle de origem.  
  
 dwFlags  
 [in] Se um novo projeto precisa ser criado se o projeto for desconhecido para a fonte de sinais de controlam plug-in. Valor pode ser uma combinação de `SCC_OP_CREATEIFNEW` e`SCC_OP_SILENTOPEN.`  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Êxito ao abrir o projeto.|  
|SCC_E_INITIALIZEFAILED|Não foi possível inicializar o projeto.|  
|SCC_E_INVALIDUSER|O usuário não pôde fazer logon sistema de controle de origem.|  
|SCC_E_COULDNOTCREATEPROJECT|O projeto não existia antes da chamada;  o `SCC_OPT_CREATEIFNEW` sinalizador foi definido, mas não foi possível criar o projeto.|  
|SCC_E_PROJSYNTAXERR|Sintaxe de projeto inválido.|  
|SCC_E_UNKNOWNPROJECT|O projeto é desconhecido para o plug-in de controle de origem e o `SCC_OPT_CREATEIFNEW` sinalizador não foi configurado.|  
|SCC_E_INVALIDFILEPATH|Caminho de arquivo inválido ou inutilizável.|  
|SCC_E_NOTAUTHORIZED|O usuário não tem permissão para executar esta operação.|  
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle de origem, provavelmente devido a problemas de rede ou de contenção. Recomenda-se uma nova tentativa.|  
|SCC_E_NONSPECFICERROR|Uma falha não específica; o sistema de controle de origem não foi inicializado.|  
  
## <a name="remarks"></a>Comentários  
 O IDE pode passar um nome de usuário (`lpUser`), ou pode simplesmente passar em um ponteiro para uma cadeia de caracteres vazia. Se houver um nome de usuário, o plug-in de controle de origem deve usá-lo como um padrão. No entanto, se nenhum nome foi aprovado ou falha de logon com o nome especificado, o plug-in deve solicitar ao usuário para fazer logon e retornará o nome válido de `lpUser` quando ele recebe um logon válido`.` porque o plug-in pode alterar a cadeia de caracteres de nome de usuário, o IDE sempre será alocar um buffer de tamanho (`SCC_USER_LEN`+&1; ou SCC_USER_SIZE, que inclui espaço para o terminador nulo).  
  
> [!NOTE]
>  A primeira ação que o IDE pode ser necessário para executar pode ser uma chamada para o `SccOpenProject` função ou o [SccGetProjPath](../extensibility/sccgetprojpath-function.md). Por esse motivo, ambos têm um idênticos `lpUser` parâmetro.  
  
 `lpAuxProjPath`e`lpProjName` são lidas do arquivo de solução, ou eles são retornados de uma chamada para o `SccGetProjPath` função. Esses parâmetros contêm as cadeias de caracteres que associa o plug-in de controle de origem com o projeto e são significativos para o plug-in. Se nenhum como cadeias de caracteres são no arquivo de solução e o usuário não tiver sido solicitado ao procurar (que retorna uma cadeia de caracteres por meio de `SccGetProjPath` função), IDE passa cadeias de caracteres vazias para os `lpAuxProjPath` e `lpProjName`e espera que esses valores sejam atualizados pelo plug-in quando essa função retorna.  
  
 `lpTextOutProc`é um ponteiro para uma função de retorno de chamada fornecido pelo IDE para o plug-in para fins de exibição da saída de resultado do comando de controle de origem. Essa função de retorno de chamada é descrita detalhadamente no [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
> [!NOTE]
>  Se o plug-in de controle de origem pretende aproveitar isso, ele deve ter configurado o `SCC_CAP_TEXTOUT` sinalizador no [SccInitialize](../extensibility/sccinitialize-function.md). Se esse sinalizador não foi definida ou se o IDE não oferece suporte a esse recurso, `lpTextOutProc` será `NULL`.  
  
 O `dwFlags` parâmetro controla o resultado que o projeto que está sendo aberto não existe. Ele consiste em dois os sinalizadores de bit, `SCC_OP_CREATEIFNEW` e `SCC_OP_SILENTOPEN`. Se o projeto que está sendo aberto já existir, a função simplesmente abre o projeto e retorna `SCC_OK`. Se o projeto não existe e se o `SCC_OP_CREATEIFNEW` sinalizador estiver no, o plug-in de controle de origem pode criar o projeto no sistema de controle de origem, abri-lo e retornar `SCC_OK`. Se o projeto não existe e se o `SCC_OP_CREATEIFNEW` sinalizador estiver desativado, o plug-in, em seguida, procure o `SCC_OP_SILENTOPEN` sinalizador. Se esse sinalizador é desabilitado, o plug-in poderá solicitar ao usuário um nome de projeto. Se esse sinalizador estiver em, o plug-in deve simplesmente retornar `SCC_E_UNKNOWNPROJECT`.  
  
## <a name="calling-order"></a>Ordem de chamada  
 No curso normal de eventos, o [SccInitialize](../extensibility/sccinitialize-function.md) seria chamado primeiro para abrir uma sessão de controle de origem. Uma sessão pode consistir em uma chamada para `SccOpenProject`, seguido por outras chamadas de função de API de plug-in de controle de origem e será encerrado com uma chamada para o [SccCloseProject](../extensibility/scccloseproject-function.md). Essas sessões podem ser repetidas várias vezes antes do [SccUninitialize](../extensibility/sccuninitialize-function.md) é chamado.  
  
 Se os conjuntos de plug-in de controle de origem a `SCC_CAP_REENTRANT` bit no `SccInitialize`, em seguida, a sequência de sessão acima pode ser repetida várias vezes em paralelo. Diferentes `pvContext` estruturas acompanhar as diferentes sessões, no qual cada `pvContext` está associado um projeto aberto por vez. Com base no`pvContext` parâmetro, o plug-in pode determinar qual o projeto é referenciado em qualquer chamada específica. Se o recurso de bits `SCC_CAP_REENTRANT` não estiver definido, nonreentrant plug-ins de controle de origem são limitadas em sua capacidade de trabalhar com vários projetos.  
  
> [!NOTE]
>  O `SCC_CAP_REENTRANT` bit foi introduzido na versão 1.1 da API de plug-in de controle de origem. Ele não está definido ou é ignorado na versão 1.0, e todos os versão 1.0 fonte plug-ins de controle são considerados nonreentrant.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCloseProject](../extensibility/scccloseproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [Restrições em comprimentos de cadeia de caracteres](../extensibility/restrictions-on-string-lengths.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
