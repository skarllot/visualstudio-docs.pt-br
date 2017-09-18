---
title: "Função SccDiff | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
caps.latest.revision: 16
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
ms.openlocfilehash: ad971e15c36bcd0a404e8383a3e6012686956c21
ms.lasthandoff: 02/22/2017

---
# <a name="sccdiff-function"></a>Função SccDiff
Esta função exibe (ou, opcionalmente, apenas verifica) as diferenças entre o arquivo atual (no disco local) e sua última versão de check-in na fonte de sistema de controle.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
SCCRTN SccDiff(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LPCSTR    lpFileName,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pvContext  
 [in] A estrutura de contexto de plug-in de controle de origem.  
  
 hWnd  
 [in] Um identificador para a janela do IDE que o plug-in de controle de origem pode usar como um pai para as caixas de diálogo que ele fornece.  
  
 lpFileName  
 [in] Nome do arquivo para o qual a diferença é solicitada.  
  
 fOptions  
 [in] Sinalizadores de comando. Consulte comentários para obter detalhes.  
  
 pvOptions  
 [in] Opções de plug-in específico de controle de origem.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|A versão de cópia e o servidor de trabalho são idênticos.|  
|SCC_I_FILESDIFFERS|A cópia de trabalho é diferente da versão sob controle de origem.|  
|SCC_I_RELOADFILE|Um arquivo ou projeto precisa ser recarregado.|  
|SCC_E_FILENOTCONTROLLED|O arquivo não está sob controle de origem.|  
|SCC_E_NOTAUTHORIZED|O usuário não tem permissão para executar esta operação.|  
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle de origem, provavelmente devido a problemas de rede ou de contenção. Recomenda-se uma nova tentativa.|  
|SCC_E_NONSPECIFICERROR|Falha não específica; diferença de arquivo não foi obtida.|  
|SCC_E_FILENOTEXIST|Não foi encontrado no arquivo local.|  
  
## <a name="remarks"></a>Comentários  
 Essa função tem duas finalidades diferentes. Por padrão, ele exibe uma lista de alterações em um arquivo. O plug-in de controle do código-fonte abre sua própria janela, em qualquer formato que escolher, para exibir as diferenças entre o arquivo do usuário no disco e a versão mais recente do arquivo sob controle de origem.  
  
 Como alternativa, o IDE pode simplesmente precisa determinar se um arquivo foi alterado. Por exemplo, o IDE talvez seja necessário determinar se é seguro fazer check-out de um arquivo sem informar o usuário. Nesse caso, o IDE passa o `SCC_DIFF_CONTENTS` sinalizador. O plug-in de controle de origem deve verificar o arquivo no disco, byte por byte, no arquivo de controle do código-fonte e retornar um valor que indica se os dois arquivos são diferentes sem exibir nada para o usuário.  
  
 Como uma otimização de desempenho, o plug-in de controle de origem pode usar uma alternativa baseada em uma soma de verificação ou um carimbo de hora em vez da comparação byte por byte chamado para por `SCC_DIFF_CONTENTS`: esses formulários de comparação são, obviamente, mais rápido, mas menos confiável. Nem todos os sistemas de controle de origem podem oferecer suporte a esses métodos alternativos de comparação, e o plug-in pode ter de fallback para uma comparação de conteúdo. Controle de origem todos os plug-ins deve, no mínimo, oferecer suporte a uma comparação de conteúdo.  
  
> [!NOTE]
>  Os sinalizadores de diferença rápido são mutuamente exclusivos. Ele é válido para não passar nenhum sinalizador, mas não é válido para transmitir simultaneamente mais de um. `SCC_DIFF_QUICK_DIFF`, que é uma máscara que combina todos os sinalizadores, pode ser usado para testar, mas nunca deve ser passada como um parâmetro.  
  
|`fOption`|Significado|  
|---------------|-------------|  
|SCC_DIFF_IGNORECASE|Comparação de maiusculas e minúsculas (pode ser usado para diferença rápida ou visual).|  
|SCC_DIFF_IGNORESPACE|Ignora o espaço em branco (pode ser usado para diferença rápida ou visual).|  
|SCC_DIFF_QD_CONTENTS|Compara silenciosamente o arquivo, byte por byte.|  
|SCC_DIFF_QD_CHECKSUM|Compara silenciosamente o arquivo por meio de uma soma de verificação quando tem suporte. Se não houver suporte reverterá para uma comparação do conteúdo.|  
|SCC_DIFF_QD_TIME|Compara silenciosamente o arquivo por meio de seu carimbo de hora com suporte. Se não houver suporte reverterá para uma comparação do conteúdo.|  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)
