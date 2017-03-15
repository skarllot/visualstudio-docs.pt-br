---
title: "Função SccGetParentProjectPath | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
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
ms.openlocfilehash: e139cd0a766a757e4ea083976c7456afc56e4683
ms.lasthandoff: 02/22/2017

---
# <a name="sccgetparentprojectpath-function"></a>Função SccGetParentProjectPath
Esta função determina o caminho do projeto pai de um projeto especificado. Essa função é chamada quando o usuário adiciona um projeto do Visual Studio para controle de origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
SCCRTN SccGetParentProjectPath(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpProjPath,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpParentProjPath  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pContext  
 [in] O ponteiro de contexto de plug-in de controle de origem.  
  
 hWnd  
 [in] Um identificador para a janela do IDE que o plug-in de controle de origem pode usar como um pai para as caixas de diálogo que ele fornece.  
  
 lpUser  
 [no, out] O nome de usuário (até SCC_USER_SIZE, incluindo o terminador nulo).  
  
 lpProjPath  
 [in] Cadeia de caracteres identificando o caminho do projeto (até SCC_PRJPATH_SIZE, incluindo o terminador nulo).  
  
 lpAuxProjPath  
 [no, out] Cadeia de caracteres auxiliar que identifica o projeto (até SCC_PRJPATH_SIZE, incluindo o terminador nulo).  
  
 lpParentProjPath  
 [no, out] Cadeia de caracteres de saída identifica o caminho do projeto pai (até SCC_PRJPATH_SIZE, incluindo o terminador nulo).  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Caminho do projeto pai foi obtido com êxito.|  
|SCC_E_INITIALIZEFAILED|Não foi possível inicializar o projeto.|  
|SCC_E_INVALIDUSER|O usuário não pôde fazer logon plug-in de controle de origem.|  
|SCC_E_UNKNOWNPROJECT|Projeto é desconhecido para o plug-in de controle de origem.|  
|SCC_E_INVALIDFILEPATH|Caminho de arquivo inválido ou inutilizável.|  
|SCC_E_NOTAUTHORIZED|O usuário não tem permissão para executar esta operação.|  
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle de origem, provavelmente devido a problemas de rede ou de contenção. Recomenda-se uma nova tentativa.|  
|SCC_E_PROJSYNTAXERR|Sintaxe de projeto inválido.|  
|SCC_E_CONNECTIONFAILURE|Problema de conexão de armazenamento.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Falha não específica.|  
  
## <a name="remarks"></a>Comentários  
 Essa função retorna um código de êxito ou falha e, se for bem-sucedido, preenche a variável `lpParentProjPath` com o caminho completo do projeto para o projeto especificado.  
  
 Essa função retorna o pai de caminho do projeto de um projeto existente. Para o projeto raiz, a função retorna o caminho do projeto que foi passado (ou seja, o mesmo projeto caminho raiz). Observe que um caminho de projeto é uma cadeia de caracteres que é significativa apenas para o plug-in de controle de origem.  
  
 O IDE está preparado para aceitar as alterações para o `lpUser` e `lpAuxProjPath` também os parâmetros. O IDE irá manter essas cadeias de caracteres e passá-los para o [SccOpenProject](../extensibility/sccopenproject-function.md) quando o usuário abrir esse projeto no futuro. Essas cadeias de caracteres, portanto, fornecem uma maneira para o plug-in para acompanhar informações necessárias para associar um projeto de controle de origem.  
  
 Essa função é semelhante do [SccGetProjPath](../extensibility/sccgetprojpath-function.md), exceto que ele não solicita ao usuário selecionar um projeto. Ele também nunca cria um novo projeto mas funciona somente com um projeto existente.  
  
 Quando `SccGetParentProjectPath` é chamado, `lpProjPath` e `lpAuxProjPath` não estará vazio e corresponderá a um projeto válido. Essas cadeias de caracteres geralmente são recebidas pelo IDE a partir de uma chamada anterior a `SccGetProjPath` função.  
  
 O `lpUser` argumento é o nome de usuário. O IDE irá passar o mesmo nome de usuário que anteriormente tinha recebido do `SccGetProjPath` função e o plug-in de controle de origem devem usar o nome como padrão. Se o usuário já tiver uma conexão aberta com o plug-in, em seguida, o plug-in deve tentar eliminar os avisos para certificar-se de que a função funciona silenciosamente. No entanto, se o logon falhar, o plug-in deve solicitar ao usuário para um logon e, quando ele recebe um logon válido, passe o nome de volta no `lpUser`. Como o plug-in pode alterar essa cadeia de caracteres, o IDE sempre será alocar um buffer de tamanho (`SCC_USER_LEN`+&1;). Se a cadeia de caracteres for alterada, a nova cadeia de caracteres deve ser um nome de logon válido (pelo menos como válido como a cadeia de caracteres antiga).  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Observações técnicas para SccCreateSubProject e SccGetParentProjectPath  
 Adicionando soluções e projetos ao controle de origem foi simplificado no Visual Studio para minimizar o número de vezes que um usuário é solicitado a selecionar locais no sistema de controle de origem. Essas alterações são ativadas pelo Visual Studio se um plug-in de controle de origem dá suporte às duas novas funções, o [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) e `SccGetParentProjectPath` função. No entanto, a seguinte entrada do registro pode ser usada para desabilitar essas alterações e reverter para o comportamento anterior do Visual Studio (fonte de controle de plug-in API versão 1.1):  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = DWORD:&00000;001  
  
 Se essa entrada do registro não existe ou está definida como DWORD:&00000;000, Visual Studio tenta usar as novas funções, `SccCreateSubProject`e`SccGetParentProjectPath`.  
  
 Se a entrada do registro é definida como DWORD:&00000;001, Visual Studio tenta usar essas novas funções e as operações de adicionar ao controle de origem funcionam como nas versões anteriores do Visual Studio.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
