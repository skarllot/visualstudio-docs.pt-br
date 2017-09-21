---
title: "Função SccGet | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
caps.latest.revision: 14
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
ms.openlocfilehash: 97f79ca001a2e79c6abb8dec0fc738694cb95e7b
ms.lasthandoff: 02/22/2017

---
# <a name="sccget-function"></a>Função SccGet
Esta função recupera uma cópia de um ou mais arquivos para exibição e compilação, mas não para edição. Na maioria dos sistemas, os arquivos são marcados como somente leitura.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
SCCRTN SccGet(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
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
 [in] Número de arquivos especificados na `lpFileNames` matriz.  
  
 lpFileNames  
 [in] Matriz de nomes totalmente qualificados dos arquivos a serem recuperados.  
  
 fOptions  
 [in] Sinalizadores de comando (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 pvOptions  
 [in] Opções de plug-in específico de controle de origem.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Sucesso da operação get.|  
|SCC_E_FILENOTCONTROLLED|O arquivo não está sob controle de origem.|  
|SCC_E_OPNOTSUPPORTED|O sistema de controle de origem não oferece suporte a esta operação.|  
|SCC_E_FILEISCHECKEDOUT|Não é possível obter o arquivo no momento o usuário fez check-out.|  
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle de origem, provavelmente devido a problemas de rede ou de contenção. Recomenda-se uma nova tentativa.|  
|SCC_E_NOSPECIFIEDVERSION|Uma versão inválida ou a data/hora especificado.|  
|SCC_E_NONSPECIFICERROR|Falha não específica; arquivo não foi sincronizado.|  
|SCC_I_OPERATIONCANCELED|Operação cancelada antes da conclusão.|  
|SCC_E_NOTAUTHORIZED|O usuário não está autorizado para executar esta operação.|  
  
## <a name="remarks"></a>Comentários  
 Essa função é chamada com uma contagem e uma matriz de nomes de arquivos a serem recuperados. Se o IDE passar o sinalizador `SCC_GET_ALL`, isso significa que os itens na `lpFileNames` não são arquivos, mas pastas e todos os arquivos sob controle de origem nos diretórios determinados devem ser recuperadas.  
  
 O `SCC_GET_ALL` sinalizador pode ser combinado com o `SCC_GET_RECURSIVE` sinalizador para recuperar todos os arquivos nos diretórios determinados e todos os subdiretórios também.  
  
> [!NOTE]
>  `SCC_GET_RECURSIVE`nunca deve ser passado sem `SCC_GET_ALL`. Além disso, observe que se diretórios C:\A e C:\A\B são ambos passado recursiva obtém, C:\A\B e todas as suas subpastas serão realmente recuperadas duas vezes. É responsabilidade do IDE, e não a fonte de controle do plug-in — para certificar-se de que duplicatas como essa são mantidas fora da matriz.  
  
 Por fim, mesmo que o plug-in de controle de uma origem especificada a `SCC_CAP_GET_NOUI` sinalizador na inicialização, indicando que ele não tem uma interface de usuário para um comando Get, essa função ainda pode ser chamada pelo IDE para recuperar arquivos. O sinalizador significa simplesmente que o IDE não exibirá um item de menu Get e que o plug-in não é esperado para fornecer qualquer interface de usuário.  
  
## <a name="renaming-and-sccget"></a>Renomear e SccGet  
 Situação: um usuário faz check-out de um arquivo, por exemplo, a.txt e modifica a ele. Antes de a.txt pode fazer check-in, um segundo usuário renomeia a.txt para b. txt no banco de dados de controle de origem, o check-out b. txt, faz algumas modificações no arquivo e verifica o arquivo. O primeiro usuário que deseja que as alterações feitas pelo usuário segundo para que o primeiro usuário renomeia sua versão local do arquivo a. txt para b. txt e faz um get no arquivo. No entanto, o cache local que mantém o controle de números de versão ainda considera a primeira versão do a.txt é armazenada localmente e então o controle de origem não pode resolver as diferenças.  
  
 Há duas maneiras de resolver essa situação em que o cache local de versões de controle de origem se torna fora de sincronia com o banco de dados de controle de origem:  
  
1.  Não permite a renomeação de um arquivo de banco de dados de controle de origem que está sendo verificado.  
  
2.  É o equivalente de "excluir antigo" seguido de "Adicionar novo". O seguinte algoritmo é uma forma de fazer isso.  
  
    1.  Chamar o [SccQueryChanges](../extensibility/sccquerychanges-function.md) função para saber mais sobre a renomeação de a.txt para b. txt no banco de dados de controle de origem.  
  
    2.  Renomeie o a.txt local para b. txt.  
  
    3.  Chamar o `SccGet` função a.txt e b. txt.  
  
    4.  Porque a.txt não existe no banco de dados de controle de origem, o cache local de versão é limpos das informações de versão a.txt ausente.  
  
    5.  O arquivo b. txt que está sendo extraído é mesclado com o conteúdo do arquivo local b. txt.  
  
    6.  O arquivo b. txt atualizado agora pode fazer check-in.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [Sinalizadores de bit usados pelos comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)
