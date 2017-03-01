---
title: "Desenvolvendo um serviço de linguagem herdado | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords:
- language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
caps.latest.revision: 28
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
ms.openlocfilehash: c33de03bc9df2e5b30e707115ac4947908141d90
ms.lasthandoff: 02/22/2017

---
# <a name="developing-a-legacy-language-service"></a>Desenvolvendo um serviço de linguagem herdado
Esta seção vincula para tópicos que ajudam você criar um serviço de linguagem herdada.  
  
 Serviços de linguagem herdada são implementados como parte de um VSPackage, mas a maneira mais recente para implementar recursos de serviço de linguagem é usar extensões MEF. Para obter mais informações sobre a nova maneira de implementar um serviço de linguagem, consulte [Editor e extensões do serviço de linguagem](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  É recomendável que você comece a usar o novo editor de API assim que possível. Isso irá melhorar o desempenho do seu serviço de linguagem e lhe permitem tirar proveito dos novos recursos do editor.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Modelo de um serviço de linguagem herdado](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 Fornece um modelo de um serviço de linguagem mínima para o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] editor básicos. Você pode usar esse modelo como um guia para criar seu próprio serviço de linguagem.  
  
 [Interfaces de serviço de linguagem herdada](../../extensibility/internals/legacy-language-service-interfaces.md)  
 Discute os objetos necessários para implementar um serviço de linguagem e fornece uma lista de objetos adicionais que você pode usar para fornecer o realce de sintaxe, dados de método e outros recursos.  
  
 [Interceptação de comandos de serviço de linguagem herdado](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 Descreve como inserir um filtro de comando em seu serviço de linguagem para comandos de interceptação que trataria a exibição de texto.  
  
 [Registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 Fornece informações sobre como registrar seu serviço de linguagem usando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Suporte do serviço de linguagem para depuração](../../extensibility/internals/language-service-support-for-debugging.md)  
 Descreve como um serviço de linguagem pode fornecer recursos para dar suporte a um depurador.  
  
 [Lista de verificação: Criar um serviço de linguagem herdado](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 Fornece instruções passo a passo para criar e integrar um serviço de linguagem para o editor de núcleo.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Sintaxe de cores em um serviço de linguagem herdado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Discute como implementar o realce de sintaxe em seu serviço de linguagem.  
  
 [Conclusão de instrução em um serviço de linguagem herdado](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 Discute a conclusão da instrução, o processo pelo qual um serviço de linguagem ajuda os usuários a concluir um elemento que eles começaram a digitação ou a palavra-chave language.  
  
 [Informações de parâmetro em um serviço de linguagem herdado](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 Descreve como fornecer dicas de método para funções sobrecarregadas e métodos.  
  
 [Como: fornecer suporte a texto oculto em um serviço de linguagem herdado](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 Explique a finalidade de uma região de texto oculto e fornece instruções sobre como implementar uma região de texto oculto.  
  
 [Como: fornecer suporte expandido de estrutura de tópicos em um serviço de linguagem herdado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 Explica as duas opções que estendem o suporte de estrutura de tópicos para a sua linguagem, além de oferecer suporte a *recolher para definições de* comando.
