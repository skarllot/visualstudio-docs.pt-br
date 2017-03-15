---
title: "Funções de retorno de chamada implementadas pelo IDE | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
caps.latest.revision: 24
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
ms.openlocfilehash: a6a95fb3f03ca8be3ae74fa8458451bcec69f9f2
ms.lasthandoff: 02/22/2017

---
# <a name="callback-functions-implemented-by-the-ide"></a>Funções de retorno de chamada implementadas pelo IDE
Para fazer a integração com o ambiente de desenvolvimento integrado (IDE) como direta possível e para fornecer uma experiência unificada do usuário final, o plug-in de controle de origem pode usar funções de retorno de chamada que são implementadas pelo IDE. O plug-in pode chamar essas funções em momentos apropriados durante uma operação de controle de origem para passar informações para o IDE; o IDE pode exibir essas informações como elementos incorporados em sua interface de usuário. O usuário tem uma experiência menos fragmentada nesse cenário que se o plug-in empregada sua própria interface do usuário.  
  
 O arquivo de cabeçalho necessário é scc.h. O local padrão é \Program Files\VSIP 8.0\EnvSDK\common\inc\\. Ele também está na pasta VSIP que tem o exemplo de plug-in de controle de origem em \Program Files\VSIP 8.0\MSSCCI\\.  
  
## <a name="in-this-section"></a>Nesta seção  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Descreve a função de retorno de chamada que é usada pelo [SccOpenProject](../extensibility/sccopenproject-function.md) para exibir mensagens de controle da fonte de plug-in por meio do IDE.  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 Descreve a função de retorno de chamada que é usada pelo [SccPopulateList](../extensibility/sccpopulatelist-function.md) quando o IDE não tem acesso completo a informações que estão disponíveis somente para o plug-in, como uma lista completa dos arquivos sob controle de versão de controle de origem.  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 Descreve a função de retorno de chamada que é usada pelo [SccQueryChanges](../extensibility/sccquerychanges-function.md) operação.  
  
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)  
 Descreve a função de retorno de chamada que é usada pelo [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) operação.  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 Descreve a função de retorno de chamada definida por uma chamada para o [SccSetOption](../extensibility/sccsetoption-function.md) que permite que o plug-in para se comunicar alterações de nome de volta para o IDE de controle de origem.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 Abre um projeto.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Examina a lista de arquivos para seu status atual. Além disso, usa o `pfnPopulate` função para notificar o chamador quando um arquivo não corresponde aos critérios para o `nCommand`.  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 Examina uma lista de diretórios e arquivos em um projeto ou projetos que estão sob controle de origem. Cada nome de arquivo e diretório encontrado é passado para uma função de retorno de chamada.  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 Examina as alterações de nome que foram feitas em uma lista de arquivos. Cada nome de arquivo é passado para uma função de retorno de chamada junto com seu status de alteração.  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 Define uma ampla variedade de opções. Cada opção começa com `SCC_OPT_xxx` e tem seu próprio conjunto definido de valores.  
  
 [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)  
 Descreve o conteúdo da seção de referência do SDK do plug-in de controle de origem.
