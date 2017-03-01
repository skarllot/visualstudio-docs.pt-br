---
title: Criando um controle da fonte de plug-in | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
caps.latest.revision: 18
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
ms.openlocfilehash: 84c6dbdb3e90f8624b9b668ba64142d8db9d947a
ms.lasthandoff: 02/22/2017

---
# <a name="creating-a-source-control-plug-in"></a>Criando um controle da fonte de plug-in
O SDK do Visual Studio fornece recursos que permitem que você adicionar o recurso de controle de origem para o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE). Ele permite usar qualquer DLL de plug-in que esteja em conformidade com a API de plug-in de controle de origem descritos nesta documentação.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Introdução](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)  
 Descreve como instalar um plug-in de controle de origem e realça as versões de API de plug-in de controle do código-fonte disponíveis no momento.  
  
 [Arquitetura](../../extensibility/internals/source-control-plug-in-architecture.md)  
 Usa um diagrama de arquitetura para explicar a integração do plug-in com um controle da fonte de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Guia de teste para Plug-ins de controle de origem](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Fornece orientação sobre como testar a instalação e operação de um plug-in de controle de origem.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Criando um VSPackage de controle de origem](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 Discute como criar um controle de origem VSPackage que não apenas fornece a funcionalidade de controle do código-fonte, mas substitui [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] da interface do usuário do controle de origem.  
  
 [Plug-ins de controle de origem](../../extensibility/source-control-plug-ins.md)  
 Fornece uma lista completa de todos os elementos na API de plug-in de controle de origem.  
  
 [Controle de origem](../../extensibility/internals/source-control.md)  
 Discute as opções para implementar o controle de origem como um recurso integrado de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
