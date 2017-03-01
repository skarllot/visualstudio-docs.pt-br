---
title: "Introdução ao Plug-ins de controle de origem | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
caps.latest.revision: 21
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
ms.openlocfilehash: 2365c3618af3396718b7f36b88719f8176abda38
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-source-control-plug-ins"></a>Introdução ao Plug-ins de controle de origem
Para criar um controle da fonte de plug-in, você deve criar uma DLL que implementa as funções definidas na API de plug-in de controle de origem, e, em seguida, para registrar a DLL com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para torná-lo disponível para uso no controle de versão do código fonte.  
  
 Três versões da API de plug-in controle de origem (versões 1.1, 1.2 e 1.3) estão disponíveis para plug-ins de controle de origem. A API de plug-in de controle de origem documentadas aqui é versão 1.3. Ele foi projetado para ser totalmente compatível com plug-ins de controle de origem com suporte a versões 1.1 e 1.2. O [o que há de novo na fonte de controle de plug-in API versão 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) seção detalha os novos recursos de suporte na versão mais recente do que a API de plug-in de controle de origem.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como: instalar um plug-in de controle de origem](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 Descreve como criar as entradas do registro que são necessárias para conectar uma DLL de controle de origem.  
  
 [Novidades na origem controle plug-in API versão 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 Fornece uma visão geral das alterações que foram feitas para a API de plug-in de controle de origem na versão 1.3.  
  
 [Novidades na origem controle plug-in API versão 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 Fornece uma visão geral das alterações que foram feitas para a API de plug-in de controle de origem na versão 1.2.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Plug-ins de controle de origem](../../extensibility/source-control-plug-ins.md)  
 Fornece uma lista completa de todos os elementos na API de plug-in de controle de origem.  
  
 [Criando um controle da fonte de plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Define o SDK de plug-in de controle de origem e descreve os recursos incluídos.
