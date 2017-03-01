---
title: Arquitetura de tipos de projeto | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
caps.latest.revision: 6
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
ms.openlocfilehash: c9b238f853d7dd3a246f4b3204b15eda34b56885
ms.lasthandoff: 02/22/2017

---
# <a name="project-types-architecture"></a>Arquitetura de tipos de projeto
Esta seção contém informações detalhadas sobre a arquitetura de tipos de projeto no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>Nesta seção  
 [Elementos de um modelo de projeto](../../extensibility/internals/elements-of-a-project-model.md)  
 Lista os serviços que pode consumir um tipo de projeto e as interfaces deve implementar.  
  
 [Componentes principais do projeto modelo](../../extensibility/internals/project-model-core-components.md)  
 Descreve as interfaces de tipos de projeto devem implementar e, opcionalmente, podem ser implementados para fornecer funcionalidade adicional.  
  
 [Quando criar tipos de projeto](../../extensibility/internals/when-to-create-project-types.md)  
 Tipo de ajuda você a decidir quando você deve criar um projeto e quando você pode usar outro [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] recurso de extensibilidade, como editores e VSPackages para atingir o mesmo objetivo.  
  
 [Seleção e hierarquias](../../extensibility/internals/hierarchies-and-selection.md)  
 Descreve como [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usa hierarquias e contexto de seleção para fornecer uma experiência de usuário consistente e simplificada.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Subtipos de projeto](../../extensibility/internals/project-subtypes.md)  
 Explica como os subtipos de projeto permitem que você personalize o comportamento dos sistemas de projeto [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] e [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 [Tipos de projeto](../../extensibility/internals/project-types.md)  
 Fornece uma visão geral de projetos como blocos de construção básicos do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE). São fornecidos links para tópicos adicionais que explicam como projetos de controle de criação e compilação do código.
