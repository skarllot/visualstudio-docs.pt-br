---
title: Interfaces herdadas no Editor | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e6f4c118ac9306bc533ba7cf62037a8255e9c42f
ms.lasthandoff: 02/22/2017

---
# <a name="legacy-interfaces-in-the-editor"></a>Interfaces herdadas no Editor
Você pode acessar o editor do Visual Studio das interfaces herdadas. O SDK do Visual Studio inclui adaptadores conhecidos como *correções*, que permitem que essas interfaces interagir com o novo editor. No entanto, recomendamos que você atualize seu código herdado para usar o novo editor de API. Seu código terá melhor desempenho e você pode usar novas tecnologias como Windows Presentation Foundation (WPF) e o Managed Extensibility Framework (MEF).  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Adaptando um código herdado para o Editor](../extensibility/adapting-legacy-code-to-the-editor.md)|Explica como adaptar seu código para o novo editor.|  
|[Comportamento novo ou alterado com adaptadores de Editor](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|Explica como o comportamento dos adaptadores de editor difere das versões anteriores do editor.|  
|[Dentro do Editor de núcleo](../extensibility/inside-the-core-editor.md)|Descreve os diferentes componentes de versões anteriores do editor.|  
|[Criando o Editor principal usando a API herdada](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|Explica como usar a API herdada para instanciar o editor de núcleo.|  
|[Fábricas de editor](../extensibility/editor-factories.md)|Explica como usar as fábricas de editor com a API herdada.|  
|[Como: registrar tipos de arquivo do Editor](../extensibility/how-to-register-editor-file-types.md)|Explica como vincular uma extensão de nome de arquivo para o seu editor.|  
|[Passo a passo: Criar um Editor de núcleo e registrar um tipo de arquivo do Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|Explica como criar um núcleo de editor e vinculá-la a uma extensão de nome de arquivo.|  
|[Como: fornecer contexto para editores](../extensibility/how-to-provide-context-for-editors.md)|Explica como fornecer contexto para o editor.|  
|[Serviços de linguagem e o Editor de núcleo](../extensibility/language-services-and-the-core-editor.md)|Explica as interações entre um serviço de linguagem e um editor.|  
|[Acessando o Buffer de texto usando a API herdada](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|Explica como acessar o buffer de texto usando a API herdada.|  
|[Acessando theText exibição usando a API herdada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|Explica como acessar a exibição de texto usando a API herdada.|  
|[Personalizando o Windows de código usando a API herdada](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|Explica como personalizar o windows de código usando a API herdada.|  
|[Acessando as camadas de texto usando a API herdada](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|Explica como acessar as diferentes camadas de texto usando a API herdada.|  
|[Usar marcadores de texto com a API herdada](../extensibility/using-text-markers-with-the-legacy-api.md)|Explica como adicionar marcadores de texto usando a API herdada.|  
|[Personalizando Menus e controles de Editor usando a API herdada](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|Explica como personalizar controles do editor usando a API herdada.|  
|[Gerenciamento de desfazer e refazer usando a API herdada](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|Explica como gerenciar desfazer e refazer usando a API herdada.|  
|[Como: implementar o localizar e substituir o mecanismo](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|Explica como gerenciar a localizar e substituir, usando a API herdada.|  
|[Como: suprimir notificações de alteração de arquivo](../extensibility/how-to-suppress-file-change-notifications.md)|Explica como suprimir notificações de alteração de arquivo usando a API herdada.|  
|[Criar Designers e editores personalizados](../extensibility/creating-custom-editors-and-designers.md)|Explica como criar designers e editores personalizados.|  
|[Desenvolvendo um serviço de linguagem herdado](../extensibility/internals/developing-a-legacy-language-service.md)|Fornece links para documentos sobre os recursos que fornecem recursos de personalização para o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principal, adicionando suporte para um serviço de linguagem.|  
|[Usando fontes e cores](../extensibility/using-fonts-and-colors.md)|Explica como usar fontes e cores com interfaces herdadas.|
