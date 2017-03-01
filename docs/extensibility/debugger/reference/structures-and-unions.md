---
title: "Estruturas e uniões | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
caps.latest.revision: 11
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
ms.openlocfilehash: 1566dd961a044c3b0d4c563b0fa81584789bd3ad
ms.lasthandoff: 02/22/2017

---
# <a name="structures-and-unions"></a>Estruturas e uniões
A seguir é estruturas e uniões no SDK do Visual Studio de depuração.  
  
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)  
 Especifica a ID do processo, que pode ser uma ID de sistema ou um GUID.  
  
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)  
 Descreve as condições sob as quais um ponto de interrupção será acionado.  
  
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)  
 Descreve a resolução de um ponto de interrupção de erro, inclusive local, o programa e o thread.  
  
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)  
 Especifica o tipo de estrutura usada para descrever o local do ponto de interrupção.  
  
 [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)  
 Define os componentes que descrevem a localização de um ponto de interrupção em um endereço no código.  
  
 [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)  
 Descreve o local de um ponto de interrupção é ligado diretamente ao endereço no programa que está sendo depurado.  
  
 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)  
 Descreve o local de um ponto de interrupção na linha em um arquivo de origem do código.  
  
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)  
 Descreve o local de deslocamento de um ponto de interrupção em uma função no código.  
  
 [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)  
 Usada para definir pontos de interrupção do código com base em uma cadeia de caracteres que o usuário pode inserir a partir do IDE.  
  
 [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)  
 Usada para definir pontos de interrupção de dados se baseiam em uma cadeia de caracteres que o usuário pode inserir a partir do IDE.  
  
 [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)  
 Descreve a resolução de um ponto de interrupção em um local específico.  
  
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)  
 Descreve as condições e contagem no qual um ponto de interrupção será acionado após ter sido passado.  
  
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)  
 Contém as informações necessárias para implementar um ponto de interrupção.  
  
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)  
 Contém as informações necessárias para implementar um ponto de interrupção (mesmo que o [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) estrutura mas inclui informações de GUID, restrição e tracepoint do fornecedor).  
  
 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)  
 Descreve o local de um ponto de interrupção do código.  
  
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)  
 Descreve o resultado de um ponto de interrupção de dados de associação.  
  
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)  
 Descreve as informações de ponto de interrupção associada para um ponto de interrupção de código ou um ponto de interrupção de dados.  
  
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)  
 Especifica a estrutura do local de resolução do ponto de interrupção.  
  
 [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)  
 Descreve uma matriz de cadeias de caracteres.  
  
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)  
 Especifica informações sobre um tipo de campo obtido de metadados.  
  
 [CODE_PATH](../../../extensibility/debugger/reference/code-path.md)  
 Descreve uma chamada para uma função ou método.  
  
 [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md)  
 Descreve o computador no qual o depurador está em execução.  
  
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)  
 Descreve uma lista de GUIDs.  
  
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)  
 Descreve um contexto de memória ou o contexto do código.  
  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)  
 Descreve um endereço em um programa que está sendo depurado.  
  
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)  
 Representa um de vários tipos diferentes de endereços.  
  
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)  
 Identifica um visualizador personalizado ou digite visualizador.  
  
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)  
 Descreve uma propriedade de depuração que por sua vez descreve um objeto de natureza hierárquica com nome, tipo e valor.  
  
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)  
 Descreve uma referência.  
  
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)  
 Descreve a desmontagem para o IDE para exibição.  
  
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)  
 Descreve uma exceção ou erro de tempo de execução gerado pelo programa que está sendo depurado.  
  
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)  
 Descreve uma variável local, parâmetro ou outro campo.  
  
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)  
 Descreve um quadro de pilha.  
  
 [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md)  
 Descreve uma matriz de identificadores exclusivos para os mecanismos de depuração disponíveis.  
  
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)  
 Usado para definir as informações de JustMyCode para um módulo.  
  
 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)  
 Descreve uma determinada máquina.  
  
 [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)  
 Descreve um elemento de matriz em uma matriz.  
  
 [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)  
 Descreve o endereço de um campo de uma classe ou estrutura.  
  
 [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)  
 Descreve o endereço de uma variável local dentro de um escopo (geralmente uma função ou método).  
  
 [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)  
 Descreve o endereço de um método de uma classe.  
  
 [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)  
 Descreve um parâmetro de um método ou função.  
  
 [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)  
 Descreve o valor de retorno de um método ou função.  
  
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)  
 Descreve um tipo de campo obtido de metadados.  
  
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)  
 Descreve um módulo específico (DLL, EXE ou assembly).  
  
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)  
 Descreve informações de status sobre os caminhos de pesquisa do símbolo que tenham sido pesquisados.  
  
 [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)  
 Descreve um endereço nativo.  
  
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)  
 Descreve um tipo de campo obtido um símbolo PDB.  
  
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)  
 Descreve o estado de um ponto de interrupção está pronto para vincular a um local de código.  
  
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)  
 Descreve um processo.  
  
 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)  
 Descreve uma lista de [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objetos que representam nós de programa.  
  
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)  
 Descreve os processos em execução em um computador.  
  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)  
 Descreve o local de linha e coluna no texto especificado.  
  
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)  
 Descreve as propriedades de um thread.  
  
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)  
 Descreve o tipo do campo.  
  
 [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)  
 Descreve um endereço físico.  
  
 [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)  
 Descreve um endereço relativo a um `this` ponteiro (`Me` no Visual Basic).  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h, sh.h ou ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Referência da API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
