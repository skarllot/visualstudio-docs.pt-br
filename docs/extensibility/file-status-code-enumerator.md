---
title: "Enumerador de código de Status do arquivo | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
caps.latest.revision: 15
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
ms.openlocfilehash: 8ae9e713ee612c470116f47b6d27c5a58612ddc2
ms.lasthandoff: 02/22/2017

---
# <a name="file-status-code-enumerator"></a>Enumerador de código de Status do arquivo
O `SccStatus` enumerador contém valores constantes nomeadas que especificam o estado de um arquivo no sistema de controle de origem. Essa enumeração é usada pelo [SccQueryInfo](../extensibility/sccqueryinfo-function.md) e `POPLISTFUNC` função de retorno de chamada (consulte [POPLISTFUNC](../extensibility/poplistfunc.md) para obter detalhes).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
enum SccStatus {  
   SCC_STATUS_INVALID          = -1L,  
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,  
   SCC_STATUS_CONTROLLED       = 0x0001L,  
   SCC_STATUS_CHECKEDOUT       = 0x0002L,  
   SCC_STATUS_OUTOTHER         = 0x0004L,  
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,  
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,  
   SCC_STATUS_OUTOFDATE        = 0x0020L,  
   SCC_STATUS_DELETED          = 0x0040L,  
   SCC_STATUS_LOCKED           = 0x0080L,  
   SCC_STATUS_MERGED           = 0x0100L,  
   SCC_STATUS_SHARED           = 0x0200L,  
   SCC_STATUS_PINNED           = 0x0400L,  
   SCC_STATUS_MODIFIED         = 0x0800L,  
   SCC_STATUS_OUTBYUSER        = 0x1000L  
   SCC_STATUS_NOMERGE          = 0x2000L  
   SCC_STATUS_RESERVED_1       = 0x4000L  
   SCC_STATUS_RESERVED_2       = 0x8000L  
};  
```  
  
## <a name="members"></a>Membros  
 SCC_STATUS_INVALID  
 Não foi possível obter o status; Não confie nele.  
  
 SCC_STATUS_NOTCONTROLLED  
 O arquivo não está no controle do código-fonte.  
  
 SCC_STATUS_CONTROLLED  
 Arquivo está sob controle de origem.  
  
 SCC_STATUS_CHECKEDOUT  
 Check-out pelo usuário atual no disco local.  
  
 SCC_STATUS_OUTOTHER  
 Arquivo de check-out por outro usuário.  
  
 SCC_STATUS_OUTEXCLUSIVE  
 Arquivo é check-out exclusivo.  
  
 SCC_STATUS_OUTMULTIPLE  
 Arquivo de check-out por mais de um usuário.  
  
 SCC_STATUS_OUTOFDATE  
 O arquivo não é o mais recente.  
  
 SCC_STATUS_DELETED  
 Arquivo foi excluído do projeto.  
  
 SCC_STATUS_LOCKED  
 Arquivo está bloqueado; Não há versões mais permitidos.  
  
 SCC_STATUS_MERGED  
 Arquivo foi mesclado, mas ainda não fixo/verificado.  
  
 SCC_STATUS_SHARED  
 Arquivo é compartilhado entre projetos.  
  
 SCC_STATUS_PINNED  
 Arquivo compartilhado para uma versão explícita.  
  
 SCC_STATUS_MODIFIED  
 Arquivo foi modificado/dividida/violadas.  
  
 SCC_STATUS_OUTBYUSER  
 Arquivo de check-out pelo usuário atual.  
  
 SCC_STATUS_NOMERGE  
 Arquivo nunca pode ser mesclado com e não precisa ser salvo antes de um GET.  
  
 SCC_STATUS_RESERVED_1  
 Reservado para uso interno.  
  
 SCC_STATUS_RESERVED_2  
 Reservado para uso interno.  
  
## <a name="see-also"></a>Consulte também  
 [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)
