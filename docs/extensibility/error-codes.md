---
title: "Códigos de erro | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
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
ms.openlocfilehash: d230ba4fa5e9eed40bb6920e77127ae6f97fe150
ms.lasthandoff: 02/22/2017

---
# <a name="error-codes"></a>Códigos de erro
Quando uma função da API de plug-in de controle de origem retorna um erro, ele deve ser um dos seguintes códigos de erro. Todos os erros são negativos, avisos ou códigos de erro informativas são positivos, e o sucesso é 0.  
  
|Código do erro|Valor|Descrição|  
|----------------|-----------|-----------------|  
|`SCC_I_SHARESUBPROJOK`|7|Plug-in permite adicionar arquivos de controle de origem em duas etapas. Para obter mais informações, consulte [SccSetOption](../extensibility/sccsetoption-function.md).|  
|`SCC_I_FILEDIFFERS`|6|O arquivo local é diferente do arquivo do banco de dados de controle de origem (por exemplo, [SccDiff](../extensibility/sccdiff-function.md) pode retornar esse valor).|  
|`SCC_I_RELOADFILE`|5|Arquivo local foi alterado durante a operação de controle de origem. o IDE deve recarregar o arquivo se possível.|  
|`SCC_I_FILENOTAFFECTED`|4|O arquivo não é afetado.|  
|`SCC_I_PROJECTCREATED`|3|O projeto foi criado durante a operação de controle de origem (por exemplo, durante uma chamada para [SccOpenProject](../extensibility/sccopenproject-function.md) quando `SCC_OP_CREATEIFNEW` sinalizador for especificado).|  
|`SCC_I_OPERATIONCANCELED`|2|Operação cancelada.|  
|`SCC_I_ADV_SUPPORT`|1|Oferece suporte a plug-in opções avançadas para o comando especificado. Para obter mais informações, consulte [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md).|  
|`SCC_OK`|0|Êxito.|  
|`SCC_E_INITIALIZEFAILED`|-1|Erro: Falha na inicialização.|  
|`SCC_E_UNKNOWNPROJECT`|-2|Erro: o projeto é desconhecido.|  
|`SCC_E_COULDNOTCREATEPROJECT`|-3|Erro: não foi possível criar o projeto.|  
|`SCC_E_NOTCHECKEDOUT`|-4|Erro: o arquivo não foi extraído.|  
|`SCC_E_ALREADYCHECKEDOUT`|-5|Erro: o arquivo já fez check-out.|  
|`SCC_E_FILEISLOCKED`|-6|Erro: o arquivo está bloqueado.|  
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Erro: o arquivo é check-out exclusivo.|  
|`SCC_E_ACCESSFAILURE`|-8|Houve um problema ao acessar o sistema de controle de origem, provavelmente devido a problemas de rede ou de contenção. Recomenda-se uma nova tentativa.|  
|`SCC_E_CHECKINCONFLICT`|-9|Erro: Houve um conflito durante o check in.|  
|`SCC_E_FILEALREADYEXISTS`|-10|Erro: o arquivo já existe.|  
|`SCC_E_FILENOTCONTROLLED`|-11|Erro: o arquivo não está sob controle de origem.|  
|`SCC_E_FILEISCHECKEDOUT`|-12|Erro: o arquivo foi extraído.|  
|`SCC_E_NOSPECIFIEDVERSION`|-13|Erro: não há nenhuma versão especificada.|  
|`SCC_E_OPNOTSUPPORTED`|-14|Erro: não há suporte para a operação.|  
|`SCC_E_NONSPECIFICERROR`|-15|Erro não específico.|  
|`SCC_E_OPNOTPERFORMED`|-16|Erro, a operação não foi executado.|  
|`SCC_E_TYPENOTSUPPORTED`|-17|Erro: o tipo de arquivo, por exemplo, binário, não é suportado pelo sistema de controle de código fonte.|  
|`SCC_E_VERIFYMERGE`|-18|Arquivo foi mesclada automaticamente, mas não foi verificado porque ele é a verificação de usuário pendente.|  
|`SCC_E_FIXMERGE`|-19|Arquivo foi mesclada automaticamente, mas não tiver sido incluído devido a um conflito de mesclagem deve ser resolvido manualmente.|  
|`SCC_E_SHELLFAILURE`|-20|Erro devido a uma falha de shell.|  
|`SCC_E_INVALIDUSER`|-21|Erro: o usuário é inválido.|  
|`SCC_E_PROJECTALREADYOPEN`|-22|Erro: o projeto já está aberto.|  
|`SCC_E_PROJSYNTAXERR`|-23|Erro de sintaxe do projeto.|  
|`SCC_E_INVALIDFILEPATH`|-24|Erro: o caminho do arquivo é inválido.|  
|`SCC_E_PROJNOTOPEN`|-25|Erro: o projeto não está aberto.|  
|`SCC_E_NOTAUTHORIZED`|-26|Erro: o usuário não está autorizado para executar esta operação.|  
|`SCC_E_FILESYNTAXERR`|-27|Erro de sintaxe do arquivo.|  
|`SCC_E_FILENOTEXIST`|-28|Erro, o arquivo local não existe.|  
|`SCC_E_CONNECTIONFAILURE`|-29|Erro: Ocorreu uma falha de conexão.|  
|`SCC_E_UNKNOWNERROR`|-30|Erro desconhecido.|  
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|Operação de obtenção de plano de fundo está em andamento.|  
  
## <a name="macros-provided-for-quick-checking"></a>Macros fornecidas para a verificação rápida  
  
```cpp#  
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)  
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)  
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)  
```  
  
## <a name="remarks"></a>Comentários  
 Todas as funções de API de plug-in de controle do código-fonte (exceto o [SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md), e [SccDiff](../extensibility/sccdiff-function.md)) devem ter sucesso quando os arquivos locais são passados como argumentos não existe na pasta de trabalho. Por exemplo, o IDE pode emitir uma chamada para o [SccCheckout](../extensibility/scccheckout-function.md) ou [SccUncheckout](../extensibility/sccuncheckout-function.md) em um arquivo que não existe na pasta de trabalho, mas existe no sistema de controle de origem. Essa chamada deve ser bem-sucedida. Apenas quando não há nenhum arquivo na pasta de trabalho ou no sistema de controle de origem é a função espera falhe.  
  
 Determinadas funções, como `SccAdd` e `SccCheckin`, especificamente deve retornar `SCC_E_FILENOTEXIST` quando o arquivo na pasta de trabalho não existe. Outras funções devem ter êxito quando o arquivo de trabalho não existir, se as funções operam em um nome de arquivo válido no sistema de controle de origem.  
  
 O plug-in de controle de origem não deve fazer nenhuma suposição sobre privilégios em um arquivo na pasta de trabalho, mesmo se o plug-in tive marcado o arquivo somente leitura durante uma operação. Um arquivo na pasta de trabalho pode ser movido, excluído e alterado fora de controle do plug-in.  
  
## <a name="see-also"></a>Consulte também  
 [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)
