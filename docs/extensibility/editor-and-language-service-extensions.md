---
title: "Editor e linguagem de extensões de serviço | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
caps.latest.revision: 10
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 67d250a2806b367a76fa593026f10d4b671c21b2
ms.lasthandoff: 02/22/2017

---
# <a name="editor-and-language-service-extensions"></a>Editor e extensões do serviço de linguagem
Você pode estender a maioria dos recursos do editor de código do Visual Studio. O editor é baseado no Windows Presentation Foundation (WPF) e é escrito em código gerenciado. Embora esse design difere designs em versões anteriores do Visual Studio, ele fornece a maioria dos mesmos recursos. Para estender o editor, use o Managed Extensibility Framework (MEF).  
  
 O SDK do Visual Studio fornece adaptadores conhecidos como *correções* para oferecer suporte a VSPackages que foram escritos para versões anteriores. No entanto, se você tiver um VSPackage existente, recomendamos que você atualize para a nova tecnologia para obter melhor desempenho e confiabilidade.  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Criando uma extensão com um modelo de Item Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Introdução ao uso de modelos de item Editor.|  
|[Estendendo o Editor e serviços de linguagem](../extensibility/extending-the-editor-and-language-services.md)|Links para documentos que apresentam o design e os recursos do editor do núcleo e mostram como estendê-lo.|  
|[Interfaces herdadas no Editor](../extensibility/legacy-interfaces-in-the-editor.md)|Links para documentos que explicam como acessar o editor de núcleo do código existente.|  
|[Criar Designers e editores personalizados](../extensibility/creating-custom-editors-and-designers.md)|Links para documentos que explicam como criar editores personalizados.|  
|[Extensibilidade de serviço de linguagem herdada](../extensibility/internals/legacy-language-service-extensibility.md)|Links para documentos que descrevem como integrar as linguagens de programação no Visual Studio.|  
|[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Apresenta o Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/Library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Apresenta o Windows Presentation Foundation (WPF).|
