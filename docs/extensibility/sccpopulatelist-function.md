---
title: "Função SccPopulateList | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
caps.latest.revision: 13
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
ms.openlocfilehash: 03c1d1bf84e62646e10c580c46732fb23e9cf5b9
ms.lasthandoff: 02/22/2017

---
# <a name="sccpopulatelist-function"></a>Função SccPopulateList
Essa função atualiza uma lista de arquivos para um comando de controle de origem em particular e fornece o status de controle do código-fonte em todos os arquivos de determinado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
SCCRTN SccPopulateList (  
   LPVOID          pvContext,  
   enum SCCCOMMAND nCommand,  
   LONG            nFiles,  
   LPCSTR*         lpFileNames,  
   POPLISTFUNC     pfnPopulate,  
   LPVOID          pvCallerData,  
   LPLONG          lpStatus,  
   LONG            fOptions  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pvContext  
 [in] A estrutura de contexto de plug-in de controle de origem.  
  
 nCommand  
 [in] O comando de controle de origem que será aplicado a todos os arquivos de `lpFileNames` matriz (consulte [código de comando](../extensibility/command-code-enumerator.md) para obter uma lista de comandos possíveis).  
  
 nFiles  
 [in] Número de arquivos a `lpFileNames` matriz.  
  
 lpFileNames  
 [in] Uma matriz de nomes de arquivo conhecida para o IDE.  
  
 pfnPopulate  
 [in] A função de retorno de chamada IDE para chamar para adicionar e remover arquivos (consulte [POPLISTFUNC](../extensibility/poplistfunc.md) para obter detalhes).  
  
 pvCallerData  
 [in] Inalterado do valor a ser passado para a função de retorno de chamada.  
  
 lpStatus  
 [no, out] Uma matriz para o plug-in para retornar os sinalizadores de status para cada arquivo de controle de origem.  
  
 fOptions  
 [in] Sinalizadores de comando (consulte a seção "PopulateList sinalizador" [os sinalizadores de bit usados pelos comandos específicos](../extensibility/bitflags-used-by-specific-commands.md) para obter detalhes).  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Êxito.|  
|SCC_E_NONSPECIFICERROR|Falha não específica.|  
  
## <a name="remarks"></a>Comentários  
 Essa função examina a lista de arquivos para seu status atual. Ele usa o `pfnPopulate` função de retorno de chamada para notificar o chamador quando um arquivo não corresponde aos critérios para o `nCommand`. Por exemplo, se o comando é `SCC_COMMAND_CHECKIN` e um arquivo na lista não for verificado, o retorno de chamada é usado para informar o chamador. Às vezes, o plug-in de controle de origem pode encontrar outros arquivos que podem ser parte do comando e adicioná-los. Isso permite, por exemplo, um usuário do Visual Basic para check-out de um arquivo. bmp que é usado pelo seu projeto, mas não aparece no arquivo de projeto do Visual Basic. Um usuário escolhe o **obter** comando no IDE. O IDE exibirá uma lista de todos os arquivos que ele considera que o usuário pode obter, mas antes que a lista é exibida, o `SccPopulateList` função é chamada para certificar-se de que a lista a ser exibida é atualizada.  
  
## <a name="example"></a>Exemplo  
 O IDE compila uma lista de arquivos que ele considera que o usuário pode receber. Antes de exibir essa lista, ele chama o `SccPopulateList` function, oferecendo o plug-in de controle de origem a oportunidade de adicionar e excluir arquivos da lista. O plug-in modifica a lista, chamando a função de retorno de chamada fornecido (consulte [POPLISTFUNC](../extensibility/poplistfunc.md) para obter mais detalhes).  
  
 O plug-in continua a chamar o `pfnPopulate` função, que adiciona e exclui arquivos, quando ele for concluído e retorna o `SccPopulateList` função. O IDE pode exibir sua lista. A `lpStatus` matriz representa todos os arquivos na lista original passado pelo IDE. O plug-in, preenche o status de todos esses arquivos Além disso, para fazer com que usa a função de retorno de chamada.  
  
> [!NOTE]
>  Um plug-in de controle de origem sempre tem a opção de simplesmente retornar imediatamente por essa função, deixando a lista como está. Se um plug-in implementa essa função, pode indicar isso definindo a `SCC_CAP_POPULATELIST` sinalizador de bit de recurso na primeira chamada para o [SccInitialize](../extensibility/sccinitialize-function.md). Por padrão, o plug-in deve sempre presumir que todos os itens que estão sendo passados são arquivos. No entanto, se o IDE define o `SCC_PL_DIR` sinalizador no `fOptions` parâmetro, todos os itens que estão sendo passados devem ser considerados diretórios. O plug-in deve adicionar todos os arquivos que pertencem a diretórios. O IDE nunca passará um misto de arquivos e diretórios.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)   
 [Sinalizadores de bit usados pelos comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)   
 [Código de comando](../extensibility/command-code-enumerator.md)
