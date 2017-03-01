---
title: "Novidades na origem controle plug-in API versão 1.3 | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
caps.latest.revision: 13
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
ms.openlocfilehash: ad92bf2d4c3e0d757e0669964465ab3888d8b1ed
ms.lasthandoff: 02/22/2017

---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Novidades na origem controle plug-in API versão 1.3
A API de plug-in de controle de origem versão 1.3 apresenta as seguintes novas funções para fornecer um controle mais avançado.  
  
## <a name="changes"></a>Alterações  
 As funções a seguir são novas para a API de plug-in de controle de origem versão 1.3:  
  
|Função|Visão Geral|  
|--------------|--------------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Permite que os bits de funcionalidade adicional a ser relatado|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Permite o exame dos arquivos que têm versões mais recentes do banco de controle versão que no disco local|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Permite o exame do estado das alterações de nome (renomeações, adições e exclusões) para os arquivos especificados|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Permite o exame dos diretórios e arquivos do banco de dados de controle de versão|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Adiciona uma lista especificada de arquivos do banco de dados de controle de versão para o projeto atual|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Executa um silenciosa "Get" dos arquivos especificados (sem interface do usuário é mostrada)|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Permite o acesso a opções específicas do usuário|  
  
## <a name="see-also"></a>Consulte também  
 [Introdução](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [Novidades na origem controle plug-in API versão 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
