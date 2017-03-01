---
title: Enumeradores | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
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
ms.openlocfilehash: fafb08116f06f3b0b21f69ddf4088bc2ab8d47fc
ms.lasthandoff: 02/22/2017

---
# <a name="enumerators"></a>Enumeradores
Esta seção lista os tipos de dados de enumerador na API de plug-in controle de origem que o plug-in de controle de origem deve saber sobre.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Código de comando](../extensibility/command-code-enumerator.md)  
 Enumera as opções para o [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) e [SccPopulateList](../extensibility/sccpopulatelist-function.md) funções.  
  
 [Mensagem](../extensibility/message-enumerator.md)  
 Enumera os sinalizadores usados para o retorno de chamada de impressão, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
 [Código de Status do arquivo](../extensibility/file-status-code-enumerator.md)  
 Contém valores constantes nomeadas que especificam o estado de um arquivo sob controle de origem.  
  
 [Código de Status do diretório](../extensibility/directory-status-code-enumerator.md)  
 Contém valores constantes nomeadas que especificam o estado de uma pasta sob controle de origem.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Criando um controle da fonte de plug-in](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Define o SDK de plug-in de controle de origem e descreve os recursos incluídos.  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 Solicita ao usuário as opções avançadas para o comando especificado.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Examina a lista de arquivos para seu status atual. Além disso, usa o `pfnPopulate` função para notificar o chamador quando um arquivo não corresponde aos critérios para o `nCommand`.  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Descreve a função de retorno de chamada que é usada pelo [SccOpenProject](../extensibility/sccopenproject-function.md) para exibir mensagens de controle da fonte de plug-in por meio do IDE.  
  
 [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)  
 Fornece uma lista completa de todos os elementos na API de plug-in de controle de origem.
