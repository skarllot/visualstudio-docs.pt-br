---
title: "Remoção de informações de controle de origem do. PROJ e. Arquivos sln | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
caps.latest.revision: 14
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
ms.openlocfilehash: 10678a677a1fb7da24c049a3657435230ed96a5f
ms.lasthandoff: 02/22/2017

---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Remoção de informações de controle de origem do. PROJ e. Arquivos sln
Na versão 1.2 da API de plug-in controle de origem SCC informações são armazenadas em um MSSCCPRJ. Arquivos SCC. A vantagem do MSSCCPRJ. Arquivos SCC é que as informações de SCC é fonte não - controlada, como nos arquivos. proj e. sln.  
  
## <a name="version-12-changes"></a>Alterações de versão 1.2  
 Em origem plug-ins de controle que usam a API de plug-in de controle de origem versão 1.1, informações sobre o controle de origem são armazenadas no projeto (. proj) e arquivos de solução (. sln). O local do banco de dados das informações de controle de origem for especificado, o AuxPath e o local específico no banco de dados é especificado por NomeDoProjeto. Esse comportamento pode causar problemas após a ramificação, bifurcação ou operações de cópia porque o NomeDoProjeto normalmente seriam inválido após qualquer uma dessas operações.  
  
 Na API de plug-in de controle de origem versão 1.1, o IDE usada ~ arquivos SAK para detectar se um plug-in oferece suporte a MSSCCPRJ. Método SCC de armazenar informações de controle de origem. A API de plug-in de controle de origem versão 1.2 fornece um novo recurso para detectar o suporte para MSSCCPRJ. Arquivos SCC sem usar um ~ arquivo SAK. Para obter mais informações, consulte [eliminação de ~ SAK arquivos](../../extensibility/internals/elimination-of-tilde-sak-files.md).  
  
## <a name="see-also"></a>Consulte também  
 [Novidades na origem controle plug-in API versão 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
