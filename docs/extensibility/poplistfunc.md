---
title: POPLISTFUNC | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
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
ms.openlocfilehash: 96a4f3dd006d271ede80cd3a7b0132f3abeb9d24
ms.lasthandoff: 02/22/2017

---
# <a name="poplistfunc"></a>POPLISTFUNC
Esse retorno de chamada é fornecido para o [SccPopulateList](../extensibility/sccpopulatelist-function.md) pelo IDE e é usado pelo plug-in de controle de origem para atualizar uma lista de arquivos ou pastas (também é fornecido para o `SccPopulateList` função).  
  
 Quando um usuário escolhe o **obter** comando no IDE, o IDE exibirá uma caixa de listagem de todos os arquivos que o usuário pode receber. Infelizmente, o IDE não sabe a lista exata de todos os arquivos que o usuário pode obter; somente o plug-in tem essa lista. Se outros usuários adicionar arquivos ao projeto de controle do código fonte, esses arquivos devem aparecer na lista, mas o IDE não sabe sobre eles. O IDE compila uma lista dos arquivos que ele achar que o usuário pode receber. Antes de exibir essa lista para o usuário, ele chama o [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` dando o plug-in de controle de origem a oportunidade de adicionar e excluir arquivos da lista.  
  
## <a name="signature"></a>Assinatura  
 O plug-in de controle de origem modifica a lista, chamando uma função IDE implementado com o seguinte protótipo:  
  
```cpp#  
typedef BOOL (*POPLISTFUNC) (  
   LPVOID pvCallerData,  
   BOOL fAddRemove,  
   LONG nStatus,  
   LPSTR lpFileName  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 pvCallerData  
 O `pvCallerData` parâmetro passado pelo chamador (IDE) para o [SccPopulateList](../extensibility/sccpopulatelist-function.md). O plug-in de controle de origem deve pressupor que nada sobre o conteúdo desse parâmetro.  
  
 fAddRemove  
 Se `TRUE`, `lpFileName` é um arquivo que deve ser adicionado à lista de arquivos. Se `FALSE`, `lpFileName` é um arquivo que deve ser excluído da lista de arquivos.  
  
 nStatus  
 Status de `lpFileName` (uma combinação da `SCC_STATUS` bits; consulte [código de Status do arquivo](../extensibility/file-status-code-enumerator.md) para obter detalhes).  
  
 lpFileName  
 Caminho completo do diretório do nome do arquivo para adicionar ou excluir da lista.  
  
## <a name="return-value"></a>Valor de retorno  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`TRUE`|O plug-in poderá chamar essa função.|  
|`FALSE`|Houve um problema no lado do IDE (como uma saída de situação de memória). O plug-in deve interromper a operação.|  
  
## <a name="remarks"></a>Comentários  
 Para cada arquivo que deseja que o plug-in de controle do código-fonte para adicionar ou excluir da lista de arquivos, ele chama essa função, passando o `lpFileName`. O `fAddRemove` sinalizador indica um novo arquivo para adicionar à lista ou um arquivo antigo a ser excluído. O `nStatus` parâmetro fornece o status do arquivo. Quando o plug-in de SCC concluiu a adição e exclusão de arquivos, ele retorna do [SccPopulateList](../extensibility/sccpopulatelist-function.md) chamar.  
  
> [!NOTE]
>  O `SCC_CAP_POPULATELIST` bit de recurso é necessária para o Visual Studio.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de retorno de chamada implementadas pelo IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [Código de Status do arquivo](../extensibility/file-status-code-enumerator.md)
