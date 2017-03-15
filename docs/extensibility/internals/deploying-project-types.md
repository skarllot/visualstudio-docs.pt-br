---
title: "Implantação de tipos de projeto | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: 12
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
ms.openlocfilehash: 79d4bbec7dbd031b318bbb2330f81e2a6d8ced2f
ms.lasthandoff: 02/22/2017

---
# <a name="deploying-project-types"></a>Tipos de projeto de implantação
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]instala um novo agregador de tipo de projeto (ProjectAggregator2.dll) e também um pacote do Windows Installer para redistribuição (ProjectAggregator2.msi). Você deve usar o novo agregador para tipos de projeto de código gerenciado. ProjectAggregator2 funciona limitações de alternativas de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projeto agregador que impedem os tipos de projeto de código gerenciado de funcionar corretamente. As etapas a seguir descrevem como alterar o VSPackage para usar o agregador de novo.  
  
1.  Remova o projeto NativeHierarchyWrapper de sua solução.  
  
2.  Remova qualquer binário NativeHierarchyWrapper da sua instalação.  
  
3.  Adicione ProjectAggregator2.msi à sua instalação.
