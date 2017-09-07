---
title: "Função SccGetProjPath | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: b45e9a9f33bd5f1b30ee0f300385ef984ce1bc0b
ms.contentlocale: pt-br
ms.lasthandoff: 09/06/2017

---
# <a name="sccgetprojpath-function"></a>Função SccGetProjPath
Essa função solicita ao usuário para um caminho de projeto, que é uma cadeia de caracteres que seja significativa apenas para o plug-in de controle de origem. Ele é chamado quando o usuário é:  
  
-   Criar um novo projeto  
  
-   Adicionar um projeto existente para o controle de versão  
  
-   A tentativa de encontrar um projeto de controle de versão existente  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccGetProjPath (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPSTR  lpProjName,  
   LPSTR  lpLocalPath,  
   LPSTR  lpAuxProjPath,  
   BOOL   bAllowChangePath,  
   LPBOOL pbNew  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pvContext  
 [in] A estrutura de contexto de plug-in de controle de origem.  
  
 hWnd  
 [in] Um identificador para a janela do IDE que o plug-in de controle de origem pode usar como um pai para todas as caixas de diálogo que ele oferece.  
  
 lpUser  
 [out no] O nome de usuário (não deve exceder SCC_USER_SIZE, incluindo o terminador nulo)  
  
 lpProjName  
 [out no] O nome do projeto IDE, espaço de trabalho do projeto ou makefile (não deve exceder SCC_PRJPATH_SIZE, incluindo o terminador nulo).  
  
 lpLocalPath  
 [out no] Caminho de trabalho do projeto. Se `bAllowChangePath` é `TRUE`, o plug-in de controle de origem pode modificar essa cadeia de caracteres (não deve exceder MAX_PATH, incluindo o terminador nulo).  
  
 lpAuxProjPath  
 [out no] Um buffer para o caminho do projeto retornado (não deve exceder SCC_PRJPATH_SIZE, incluindo o terminador nulo).  
  
 bAllowChangePath  
 [in] Se isso for `TRUE`, o plug-in de controle de origem pode solicitar e modificar o `lpLocalPath` cadeia de caracteres.  
  
 pbNew  
 [out no] Valor que indica se para criar um novo projeto. Valor retornado indica o êxito da criação de um projeto:  
  
|entrada|Interpretação|  
|--------------|--------------------|  
|TRUE|O usuário pode criar um novo projeto.|  
|FALSE|O usuário não pode criar um novo projeto.|  
  
|Saída|Interpretação|  
|--------------|--------------------|  
|TRUE|Um novo projeto foi criado.|  
|FALSE|Um projeto existente foi selecionado.|  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|O projeto foi criou ou recuperado com êxito.|  
|SCC_I_OPERATIONCANCELED|A operação foi cancelada.|  
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle de origem, provavelmente devido a problemas de rede ou de contenção.|  
|SCC_E_CONNECTIONFAILURE|Houve um problema ao tentar se conectar ao sistema de controle de origem.|  
|SCC_E_NONSPECIFICERROR|Ocorreu um erro não especificado.|  
  
## <a name="remarks"></a>Comentários  
 O objetivo dessa função é para o IDE adquirir os parâmetros `lpProjName` e `lpAuxProjPath`. Depois que o plug-in de controle de origem solicita ao usuário essas informações, ele passa essas duas cadeias de caracteres para o IDE. O IDE persistir essas cadeias de caracteres em seu arquivo de solução e os passa para o [SccOpenProject](../extensibility/sccopenproject-function.md) sempre que o usuário abrir este projeto. Essas cadeias de caracteres de habilitem o plug-in rastrear as informações associadas a um projeto.  
  
 Quando a função é chamada primeiro, `lpAuxProjPath` é definido como uma cadeia de caracteres vazia. `lProjName`também pode ser vazio, ou pode conter o nome de projeto IDE para que o plug-in de controle de origem pode usar ou ignorar. Quando a função retorna com êxito, o plug-in retorna as duas cadeias de caracteres correspondentes. O IDE não faz nenhuma suposição sobre essas cadeias de caracteres, não usá-los e não permitirá que o usuário para modificá-las. Se o usuário deseja alterar as configurações, o IDE chamará `SccGetProjPath` novamente, passando os mesmos valores ele recebeu a hora anterior. Assim, o plug-in controle total sobre essas duas cadeias de caracteres.  
  
 Para `lpUser`, o IDE pode passar um nome de usuário, ou simplesmente pode transmitir um ponteiro para uma cadeia de caracteres vazia. Se houver um nome de usuário, o plug-in de controle de origem deve usá-lo como padrão. No entanto, se nenhum nome foi aprovado ou se o logon falhou com o nome fornecido, o plug-in deve solicitar ao usuário um logon e passe o nome de volta `lpUser` quando ele recebe um logon válido. Como o plug-in pode alterar essa cadeia de caracteres, o IDE sempre será alocar um buffer de tamanho (`SCC_USER_LEN`+ 1).  
  
> [!NOTE]
>  A primeira ação que executa o IDE pode ser uma chamada para o `SccOpenProject` função ou o `SccGetProjPath` função. Portanto, eles têm um idênticos `lpUser` parâmetro, que permite que o controle de origem plug-in para o logon do usuário a qualquer momento. Mesmo se o retorno da função indica uma falha, o plug-in deve preencher essa cadeia de caracteres com um nome de logon válido.  
  
 `lpLocalPath`é o diretório onde o usuário mantém o projeto. Pode ser uma cadeia de caracteres vazia. Se não houver nenhum diretório atualmente definido (como no caso de um usuário tentar baixar um projeto do sistema de controle de origem) e se `bAllowChangePath` é `TRUE`, o plug-in de controle de origem pode solicitar a entrada do usuário ou use outro método para colocar seu possui a cadeia de caracteres em `lpLocalPath`. Se `bAllowChangePath` é `FALSE`, o plug-in não deve alterar a cadeia de caracteres, porque o usuário já está trabalhando no diretório especificado.  
  
 Se o usuário cria um novo projeto a ser colocado sob controle de origem, o plug-in de controle de origem pode não realmente criá-lo no sistema de controle de origem no momento `SccGetProjPath` é chamado. Em vez disso, ele passa novamente a cadeia de caracteres juntamente com um valor diferente de zero para `pbNew`, indicando que o projeto será criado no sistema de controle de origem.  
  
 Por exemplo, se um usuário a **novo projeto** assistente no Visual Studio adiciona o projeto ao controle de origem, o Visual Studio chama esta função e o plug-in determina se é okey criar um novo projeto no sistema de controle de origem para contém o projeto do Visual Studio. Se o usuário clica em **Cancelar** antes de concluir o assistente, o projeto nunca é criado. Se o usuário clica em **Okey**, o Visual Studio chama `SccOpenProject`, passando `SCC_OPT_CREATEIFNEW`, e o projeto de origem controlada é criado nesse momento.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)
