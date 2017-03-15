---
title: "Função SccGetProjPath | Documentos do Microsoft"
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 551fe26fe20da62d6892a8c7e807cf6c22600fc8
ms.lasthandoff: 02/22/2017

---
# <a name="sccgetprojpath-function"></a>Função SccGetProjPath
Essa função solicita ao usuário um caminho de projeto, que é uma cadeia de caracteres que é significativa apenas para o plug-in de controle de origem. Ele é chamado quando o usuário é:  
  
-   Criar um novo projeto  
  
-   Adicionar um projeto existente para controle de versão  
  
-   A tentativa de encontrar um projeto de controle de versão existente  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
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
 [in] Um identificador para a janela do IDE que o plug-in de controle de origem pode usar como um pai para as caixas de diálogo que ele fornece.  
  
 lpUser  
 [no, out] O nome de usuário (não deve exceder SCC_USER_SIZE, incluindo o terminador nulo)  
  
 lpProjName  
 [no, out] O nome do projeto IDE, espaço de trabalho do projeto ou makefile (não deve exceder SCC_PRJPATH_SIZE, incluindo o terminador nulo).  
  
 lpLocalPath  
 [no, out] Caminho de trabalho do projeto. Se `bAllowChangePath` é `TRUE`, o plug-in de controle de origem pode modificar essa cadeia de caracteres (não deve exceder MAX_PATH, incluindo o terminador nulo).  
  
 lpAuxProjPath  
 [no, out] Um buffer para o caminho retornado do projeto (não deve exceder SCC_PRJPATH_SIZE, incluindo o terminador nulo).  
  
 bAllowChangePath  
 [in] Se isso for `TRUE`, o plug-in de controle de origem pode solicitar e modificar o `lpLocalPath` cadeia de caracteres.  
  
 pbNew  
 [no, out] Valor que indica se para criar um novo projeto. Valor retornado indica o êxito da criação de um projeto:  
  
|Entrada|Interpretação|  
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
|SCC_OK|O projeto foi criado com êxito ou recuperado.|  
|SCC_I_OPERATIONCANCELED|A operação foi cancelada.|  
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle de origem, provavelmente devido a problemas de rede ou de contenção.|  
|SCC_E_CONNECTIONFAILURE|Houve um problema ao tentar se conectar ao sistema de controle de origem.|  
|SCC_E_NONSPECIFICERROR|Ocorreu um erro não especificado.|  
  
## <a name="remarks"></a>Comentários  
 O objetivo dessa função é o IDE adquirir os parâmetros `lpProjName` e `lpAuxProjPath`. Depois que o plug-in de controle de origem solicita ao usuário essas informações, ele passa essas duas cadeias de caracteres para o IDE. O IDE persistir essas cadeias de caracteres em seu arquivo de solução e os passa para o [SccOpenProject](../extensibility/sccopenproject-function.md) sempre que o usuário abre este projeto. Essas cadeias de caracteres habilitem o plug-in acompanhar informações associadas a um projeto.  
  
 Quando a função é chamada pela primeira vez, `lpAuxProjPath` é definido como uma cadeia de caracteres vazia. `lProjName`também pode ser vazio, ou pode conter o nome do projeto IDE que o plug-in de controle de origem pode usar ou ignorar. Quando a função retorna com êxito, o plug-in retorna as duas cadeias de caracteres correspondentes. O IDE não faz nenhuma suposição sobre essas cadeias de caracteres, não irá usá-los e não permitirá que o usuário para modificá-las. Se o usuário deseja alterar as configurações, o IDE irá chamar `SccGetProjPath` novamente, passando os mesmos valores ele recebeu a hora anterior. Assim, o plug-in controle total sobre essas duas cadeias de caracteres.  
  
 Para `lpUser`, o IDE pode passar um nome de usuário ou pode simplesmente passar em um ponteiro para uma cadeia de caracteres vazia. Se houver um nome de usuário, o plug-in de controle de origem deve usá-lo como um padrão. No entanto, se nenhum nome foi aprovado ou falha de logon com o nome especificado, o plug-in deve solicitar ao usuário um logon e passar o nome de volta `lpUser` quando ele recebe um logon válido. Como o plug-in pode alterar essa cadeia de caracteres, o IDE sempre será alocar um buffer de tamanho (`SCC_USER_LEN`+&1;).  
  
> [!NOTE]
>  A primeira ação que executa o IDE pode ser uma chamada para o `SccOpenProject` função ou o `SccGetProjPath` função. Portanto, ambos têm um idênticos `lpUser` parâmetro, que permite que o controle de origem plug-in para conectar o usuário a qualquer momento. Mesmo que o retorno da função indica uma falha, o plug-in deve preencher essa cadeia de caracteres com um nome de logon válido.  
  
 `lpLocalPath`é o diretório onde o usuário mantém o projeto. Pode ser uma cadeia de caracteres vazia. Se não houver nenhum diretório definido atualmente (como no caso de um usuário tentar baixar um projeto do sistema de controle de origem) e se `bAllowChangePath` é `TRUE`, o plug-in de controle de origem pode solicitar entrada do usuário ou usar algum outro método para inserir sua própria cadeia de caracteres em `lpLocalPath`. Se `bAllowChangePath` é `FALSE`, o plug-in não deve alterar a cadeia de caracteres, porque o usuário já estiver trabalhando no diretório especificado.  
  
 Se o usuário cria um novo projeto a ser colocado sob controle de origem, o plug-in de controle de origem pode não realmente criá-lo no sistema de controle de origem no momento `SccGetProjPath` é chamado. Em vez disso, ele passa de volta a cadeia de caracteres juntamente com um valor diferente de zero para `pbNew`, indicando que o projeto será criado no sistema de controle de origem.  
  
 Por exemplo, se um usuário no **novo projeto** assistente no Visual Studio adiciona seu projeto ao controle de origem, o Visual Studio chama essa função e o plug-in determina se é okey criar um novo projeto no sistema de controle de origem para conter o projeto do Visual Studio. Se o usuário clicar **Cancelar** antes de concluir o assistente, o projeto nunca é criado. Se o usuário clicar **Okey**, o Visual Studio chama `SccOpenProject`, passando `SCC_OPT_CREATEIFNEW`, e o projeto de origem controlada é criado nesse momento.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)
