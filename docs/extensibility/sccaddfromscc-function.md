---
title: "Função SccAddFromScc | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
caps.latest.revision: 17
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
ms.openlocfilehash: 8f79d7d590e55f7ecce6672a9273ba32f7c546ab
ms.lasthandoff: 02/22/2017

---
# <a name="sccaddfromscc-function"></a>Função SccAddFromScc
Essa função permite que o usuário navegue para os arquivos que já estão no sistema de controle de origem e depois fazer parte desses arquivos do projeto atual. Por exemplo, essa função pode obter um arquivo de cabeçalho comum no projeto atual sem copiar o arquivo. Matriz de retorno de arquivos, `lplpFileNames`, contém a lista de arquivos que o usuário deseja adicionar ao projeto do IDE.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
SCCRTN SccAddFromScc (  
   LPVOID   pvContext,  
   HWND     hWnd,  
   LPLONG   lpnFiles,  
   LPCSTR** lplpFileNames  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pvContext  
 [in] A estrutura de contexto de plug-in de controle de origem.  
  
 hWnd  
 [in] Um identificador para a janela do IDE que o plug-in de controle de origem pode usar como um pai para as caixas de diálogo que ele fornece.  
  
 lpnFiles  
 [no, out] Um buffer para o número de arquivos que estão sendo adicionados no. (Isso é `NULL` se a memória apontada pelo `lplpFileNames` será liberada. Consulte os comentários para obter detalhes).  
  
 lplpFileNames  
 [no, out] Uma matriz de ponteiros para todos os nomes de arquivo sem caminhos de diretório. Essa matriz é alocada e liberada por meio do plug-in de controle de origem. Se `lpnFiles` = 1 e `lplpFileNames` não é `NULL`, o nome da matriz apontada por `lplpFileNames` contém a pasta de destino.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Os arquivos foram localizados e adicionados ao projeto com êxito.|  
|SCC_I_OPERATIONCANCELED|A operação foi cancelada com nenhum efeito.|  
|SCC_I_RELOADFILE|Um arquivo ou projeto precisa ser recarregado.|  
  
## <a name="remarks"></a>Comentários  
 O IDE chama essa função. Se o plug-in de controle de origem oferece suporte à especificação de uma pasta de destino, o IDE passa `lpnFiles` = 1 e passa o nome da pasta local em `lplpFileNames`.  
  
 Quando a chamada para o `SccAddFromScc` função retorna, o plug-in atribuiu valores para `lpnFiles` e `lplpFileNames`, alocação de memória para a matriz de nome de arquivo conforme necessário (Observe que essa alocação substitui o ponteiro em `lplpFileNames`). O plug-in de controle de origem é responsável pela colocação de todos os arquivos no diretório do usuário ou na pasta designação especificado. O IDE adiciona os arquivos para o projeto do IDE.  
  
 Por fim, o IDE chama essa função uma segunda vez, passando `NULL` para `lpnFiles`. Isso é interpretado como um sinal especial pelo controle da fonte de plug-in para liberar a memória alocada para a matriz de nome de arquivo em`lplpFileNames``.`  
  
 `lplpFileNames`é um `char ***` ponteiro. O plug-in de controle de origem coloca um ponteiro para uma matriz de ponteiros para os nomes de arquivo, passando a lista, portanto, o modo padrão para essa API.  
  
> [!NOTE]
>  As versões iniciais da API VSSCI não forneceu uma maneira de indicar o projeto de destino para os arquivos adicionados. Para acomodar isso, a semântica do `lplpFIleNames` parâmetro foram aprimoradas para torná-lo um parâmetro de entrada/saída, em vez de um parâmetro de saída. Se apenas um único arquivo for especificado, ou seja, o valor apontado por `lpnFiles` = 1, então o primeiro elemento da `lplpFileNames` contém a pasta de destino. Para usar esse novos semântica, o IDE chama o `SccSetOption` funcionar com o `nOption`parâmetro definido como `SCC_OPT_SHARESUBPROJ`. Se um plug-in de controle de origem não oferece suporte a semântica, ele retornará `SCC_E_OPTNOTSUPPORTED`. Fazer assim desabilita o uso do **adicionar do controle de origem** recurso. Se um oferece suporte a plug-in a **adicionar do controle de origem** recurso (`SCC_CAP_ADDFROMSCC`), ele deve oferecer suporte a nova semântica e retornar `SCC_I_SHARESUBPROJOK`.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)
