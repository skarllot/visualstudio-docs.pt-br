---
title: "Os sinalizadores de bit usados pelos comandos específicos | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
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
ms.openlocfilehash: 22a781a68e52c6aede33ee5b819e789692128669
ms.lasthandoff: 02/22/2017

---
# <a name="bitflags-used-by-specific-commands"></a>Sinalizadores de bit usados pelos comandos específicos
O comportamento de um número de funções na API de plug-in de controle de origem pode ser modificado, definindo um ou mais bits em um único valor. Esses valores são conhecidos como os sinalizadores de bit. O sinalizadores de bit vários usados pela API de plug-in de controle de origem estão detalhadas aqui, agrupados por função em que os utiliza.  
  
## <a name="checked-out-flag"></a>Check-Out de sinalizador  
 Este sinalizador pode ser definido para qualquer um de [SccAdd](../extensibility/sccadd-function.md) ou [SccCheckin](../extensibility/scccheckin-function.md).  
  
|Sinalizador|Valor|Descrição|  
|----------|-----------|-----------------|  
|`SCC_KEEP_CHECKEDOUT`|0x1000|Manter o arquivo com check-out.|  
  
## <a name="add-flags"></a>Adicionar sinalizadores  
 Esses sinalizadores são usados pelo [SccAdd](../extensibility/sccadd-function.md).  
  
|Sinalizador|Valor|Descrição|  
|----------|-----------|-----------------|  
|`SCC_FILETYPE_AUTO`|0x00|O plug-in de controle de origem é esperado para detectar automaticamente se o arquivo é texto ou binário.|  
|`SCC_FILETYPE_TEXT`|0x01|Tipo de arquivo é texto.|  
|`SCC_FILETYPE_BINARY`|0x04|Tipo de arquivo é binário. **Observação:** `SCC_FILETYPE_TEXT` e `SCC_FILETYPE_BINARY` sinalizadores são mutuamente exclusivos.   Defina exatamente um ou nenhum.|  
|`SCC_ADD_STORELATEST`|0x02|Armazenar a versão mais recente somente (sem deltas).|  
  
## <a name="diff-flags"></a>Sinalizadores de comparação  
 O [SccDiff](../extensibility/sccdiff-function.md) usa esses sinalizadores para definir o escopo de uma operação de comparação. O `SCC_DIFF_QD_xxx` sinalizadores são mutuamente exclusivos. Se qualquer um deles for especificado, nenhum feedback visual é receber. Em um "comparação rápido" (QD), o plug-in não determina como o arquivo é diferente, somente se ele for diferente. Se nenhum desses sinalizadores for especificados, que é feito um "comparação visual"; diferenças de arquivo detalhadas são computadas e exibidas. Se o QD solicitada não é suportada, move o plug-in para o próximo melhor. Por exemplo, se o IDE solicita uma soma de verificação e o plug-in não oferecer suporte a ele, o plug-in não um conteúdo completo Verifique (ainda muito mais rápido do que uma exibição visual).  
  
|Sinalizador|Valor|Descrição|  
|----------|-----------|-----------------|  
|`SCC_DIFF_IGNORECASE`|0x0002|Ignore diferenças de maiusculas.|  
|`SCC_DIFF_IGNORESPACE`|0x0004|Ignore diferenças de espaço em branco. **Observação:** o `SCC_DIFF_IGNORECASE` e `SCC_DIFF_IGNORESPACE` sinalizadores são os sinalizadores de bit opcional.|  
|`SCC_DIFF_QD_CONTENTS`|0x0010|QD, comparando o conteúdo do arquivo inteiro.|  
|`SCC_DIFF_QD_CHECKSUM`|0x0020|QD pela soma de verificação.|  
|`SCC_DIFF_QD_TIME`|0x0040|QD pelo carimbo de data/hora do arquivo.|  
|`SCC_DIFF_QUICK_DIFF`|0x0070|Esta é uma máscara usada para verificar todos os de sinalizadores de QD aos bit. Não devem ser passado para uma função; os QD três os sinalizadores de bit são mutuamente exclusivos. QD sempre não significa que nenhuma exibição da interface do usuário.|  
  
## <a name="populatelist-flag"></a>Sinalizador de PopulateList  
 Este sinalizador é usado pelo [SccPopulateList](../extensibility/sccpopulatelist-function.md) no `fOptions` parâmetro.  
  
|Sinalizador|Valor|Descrição|  
|----------|-----------|-----------------|  
|`SCC_PL_DIR`|0x00000001L|O IDE está passando diretórios, não arquivos.|  
  
## <a name="populatedirlist-flags"></a>Sinalizadores de PopulateDirList  
 Esses sinalizadores são usados pelo [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) no `fOptions` parâmetro.  
  
|Valor de opção|Valor|Descrição|  
|------------------|-----------|-----------------|  
|SCC_PDL_ONELEVEL|0x0000|Examine apenas um nível de diretórios para diretórios (esse é o padrão).|  
|SCC_PDL_RECURSIVE|0x0001|Recursivamente examine todos os diretórios em cada diretório determinado.|  
|SCC_PDL_INCLUDEFILES|0x0002|Inclua nomes de arquivo no processo de análise.|  
  
## <a name="openproject-flags"></a>Sinalizadores de OpenProject  
 Esses sinalizadores são usados pelo [SccOpenProject](../extensibility/sccopenproject-function.md) no `dwFlags` parâmetro.  
  
|Valor de opção|Valor|Descrição|  
|------------------|-----------|-----------------|  
|SCC_OP_CREATEIFNEW|0x00000001L|Se o projeto não existe no controle de origem, crie um. Se este sinalizador não estiver definido, Avisar usuário para o projeto para criar (a menos que `SCC_OP_SILENTOPEN` sinalizador for especificado).|  
|SCC_OP_SILENTOPEN|0x00000002L|Não solicitar ao usuário para criar um projeto; retorne `SCC_E_UNKNOWNPROJECT`.|  
  
## <a name="get-flags"></a>Obtém sinalizadores  
 Esses sinalizadores são usados pelo [SccGet](../extensibility/sccget-function.md) e [SccCheckout](../extensibility/scccheckout-function.md).  
  
|Sinalizador|Valor|Descrição|  
|----------|-----------|-----------------|  
|`SCC_GET_ALL`|0x00000001L|O IDE está passando a diretórios, arquivos não: obter todos os arquivos nesses diretórios.|  
|`SCC_GET_RECURSIVE`|0x00000002L|O IDE está passando diretórios: Obtenha esses diretórios e todos os seus subdiretórios.|  
  
## <a name="noption-values"></a>Valores de nOption  
 Esses sinalizadores são usados pelo [SccSetOption](../extensibility/sccsetoption-function.md) no `nOption` parâmetro.  
  
|Sinalizador|Valor|Descrição|  
|----------|-----------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Definir status da fila de eventos.|  
|`SCC_OPT_USERDATA`|0x00000002L|Especificar dados de usuário para `SCC_OPT_NAMECHANGEPFN`.|  
|`SCC_OPT_HASCANCELMODE`|0x00000003L|O IDE pode manipular Cancelar|  
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Defina um retorno de chamada para alterações de nome.|  
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Desabilitar o controle plug-in da interface do usuário check-out origem e não definir diretório de trabalho.|  
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Adicione do sistema de controle de origem para especificar um diretório de trabalho. Tente compartilhar no projeto associado, se for um descendente direto.|  
  
## <a name="dwval-bitflags"></a>dwVal os sinalizadores de bit  
 Esses sinalizadores são usados pelo [SccSetOption](../extensibility/sccsetoption-function.md) no `dwVal` parâmetro.  
  
|Sinalizador|Valor|Descrição|Usado por `nOption` valor|  
|----------|-----------|-----------------|-----------------------------|  
|`SCC_OPT_EQ_DISABLE`|0x00L|Suspende a atividade de fila de evento.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_EQ_ENABLE`|0x01L|Habilita o log de fila de eventos.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_HCM_NO`|L&0;|(Padrão) Tenha o modo sem cancelar; plug-in deve fornecer se desejado.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_HCM_YES`|L&1;|IDE manipula Cancelar.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_SCO_NO`|L&0;|(Padrão) Okey fazer check-out do plug-in da interface do usuário; definir o diretório de trabalho.|`SCC_OPT_SCCCHECKOUTONLY`|  
|`SCC_OPT_SCO_YES`|L&1;|Nenhum plug-in check-out da interface do usuário, nenhum diretório de trabalho.|`SCC_OPT_SCCCHECKOUTONLY`|  
  
## <a name="see-also"></a>Consulte também  
 [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)
