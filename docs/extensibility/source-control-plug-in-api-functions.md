---
title: "Funções de API de plug-in de controle de origem | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
caps.latest.revision: 19
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
ms.openlocfilehash: 1becbc53e64e04dc40cb45fe92fad67201897ebd
ms.lasthandoff: 02/22/2017

---
# <a name="source-control-plug-in-api-functions"></a>Funções de API de plug-in de controle de origem
A API de plug-in de controle de origem fornece as seguintes funções, que devem ser implementadas pelo plug-in de acordo com essa API de controle de origem. As assinaturas de cada função e a semântica associados com os sinalizadores de bit e outros parâmetros são descritos em detalhes nesta referência.  
  
## <a name="initialization-and-housekeeping-functions"></a>Inicialização e funções de manutenção  
  
|Função|Descrição|  
|--------------|-----------------|  
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Fecha um projeto.|  
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Solicita ao usuário as opções avançadas para o comando especificado.|  
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Retorna a versão do controle da fonte de plug-in.|  
|[SccInitialize](../extensibility/sccinitialize-function.md)|Inicializa o plug-in de controle de origem. Ele é chamado uma vez para cada instância do plug-in.|  
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Abre um projeto.|  
|[SccSetOption](../extensibility/sccsetoption-function.md)|Uma função genérica usada para definir uma ampla variedade de opções. Cada opção começa com `SCC_OPT_xxx` e tem seu próprio conjunto definido de valores.|  
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Chamado uma vez quando um plug-in de controle de origem precisa ser desconectado.|  
  
## <a name="core-source-control-functions"></a>Principais funções de controle de origem  
  
|Função|Descrição|  
|--------------|-----------------|  
|[SccAdd](../extensibility/sccadd-function.md)|Adiciona uma matriz dos arquivos especificados pelos nomes de caminho totalmente qualificado para o sistema de controle de origem.|  
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Permite que o usuário navegue para os arquivos que já estão no sistema de controle de origem e, em seguida, fazer parte desses arquivos do projeto atual.|  
|[SccCheckin](../extensibility/scccheckin-function.md)|Verifica em uma matriz de arquivos.|  
|[SccCheckout](../extensibility/scccheckout-function.md)|Check-out de uma matriz de arquivos.|  
|[SccDiff](../extensibility/sccdiff-function.md)|Mostra as diferenças entre o arquivo do usuário especificado por um nome de caminho totalmente qualificado e a versão no controle de origem.|  
|[SccGet](../extensibility/sccget-function.md)|Recupera uma cópia somente leitura de um conjunto de arquivos.|  
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Verifica o status de arquivos que o chamador solicitou sobre (via `SccQueryInfo`).|  
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Faz com que o plug-in para avisar o usuário para um caminho de projeto que seja significativo para o plug-in de controle de origem.|  
|[SccHistory](../extensibility/scchistory-function.md)|Mostra o histórico de uma matriz de nomes de arquivo local totalmente qualificado.|  
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Examina a lista de arquivos para seu status atual. Além disso, usa o `pfnPopulate` função para notificar o chamador quando um arquivo não corresponde aos critérios para o `nCommand`.|  
|[SccProperties](../extensibility/sccproperties-function.md)|Mostra as propriedades de um arquivo totalmente qualificado.|  
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Examina uma lista de arquivos totalmente qualificados de seu status atual.|  
|[SccRemove](../extensibility/sccremove-function.md)|Remove a matriz de arquivos completos do sistema de controle de origem.|  
|[SccRename](../extensibility/sccrename-function.md)|Renomeia o arquivo fornecido para um novo nome no sistema de controle de origem.|  
|[SccRunScc](../extensibility/sccrunscc-function.md)|Acessa a gama completa de recursos do sistema de controle de origem.|  
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Desfaz um check-out de um conjunto de arquivos.|  
  
## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Funções que oferecem suporte a recursos adicionais (versão 1.2 da API de plug-in de controle de origem)  
 Esse grupo de funções define os recursos adicionais incluídos na versão 1.2 da API de plug-in de controle de origem. Eles fornecem acesso a recursos de controle do código-fonte e recursos mais avançados.  
  
|Função|Descrição|  
|--------------|-----------------|  
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Inicia uma operação em lote.|  
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Cria um subprojeto com o nome especificado em um projeto existente do pai.|  
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Mostra as diferenças entre o diretório do usuário especificado por um nome de caminho totalmente qualificado e o local de banco de dados de controle de origem.|  
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Examina uma lista de diretórios totalmente qualificados de seu status atual.|  
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Termina uma operação em lote.|  
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Retorna pai caminho do projeto específico (o projeto deve existir).|  
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Verifica se são permitidos vários check-outs em um arquivo.|  
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Verifica se o plug-in criará MSSCCPRJ. Arquivos SCC.|  
  
## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Funções que oferecem suporte a recursos avançados (versão 1.3 da API de plug-in de controle de origem)  
 Esse grupo de funções define a funcionalidade adicional incluída na versão 1.3 da API de plug-in de controle de origem. Eles fornecem acesso a recursos de controle do código-fonte e recursos mais avançados.  
  
|Função|Descrição|  
|--------------|-----------------|  
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Adiciona uma lista de arquivos do controle de origem no projeto atual.|  
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Recupera uma lista de arquivos do controle de origem sem interface do usuário.|  
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Recupera uma lista de arquivos no controle de origem que são diferentes dos arquivos locais.|  
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Recupera os sinalizadores que especificam recursos estendidos compatíveis com o plug-in de controle de origem.|  
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Recupera as opções específicas do usuário.|  
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Examina uma lista de diretórios e arquivos em um projeto ou projetos que estão sob controle de origem. Cada nome de arquivo e diretório encontrado é passado para uma função de retorno de chamada.|  
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Examina as alterações de nome a uma lista de arquivos. Cada nome de arquivo é passado para uma função de retorno de chamada com seu status de alteração.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: scc.h  
  
 (Fornecida no SDK do ambiente comum inclui a pasta, por padrão *[unidade]*\Program Files\VSIP 8.0\EnvSDK\common\inc; também é fornecido na pasta VSIP com o exemplo MSSCCI, *[unidade]*\Program Files\VSIP 8.0\MSSCCI).  
  
## <a name="see-also"></a>Consulte também  
 [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)   
 [Criando um controle da fonte de plug-in](../extensibility/internals/creating-a-source-control-plug-in.md)
