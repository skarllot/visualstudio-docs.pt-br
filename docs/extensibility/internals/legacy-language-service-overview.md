---
title: "Visão geral do serviço de linguagem herdada | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
caps.latest.revision: 17
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
ms.openlocfilehash: 85af8b2e4a53c287a01a6e996c12ce1065b61d25
ms.lasthandoff: 02/22/2017

---
# <a name="legacy-language-service-overview"></a>Visão geral do serviço de linguagem herdada
Um serviço de linguagem fornece suporte de editor que permite que você implemente certos [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] recursos. As classes de serviço de linguagem de estrutura de pacote gerenciado (MPF) oferecem suporte completo para recursos usados e suporte parcial para outros recursos.  
  
## <a name="fully-supported-features-in-the-mpf"></a>Recursos com suporte total no MPF  
 As classes de serviço de linguagem MPF suportam os seguintes recursos:  
  
-   Realce de sintaxe  
  
-   Estrutura de tópicos  
  
-   Blocos de código de comentário  
  
-   Correspondência de chaves  
  
-   Trechos de código  
  
-   Propriedades de documento personalizadas  
  
-   Informações de parâmetro do IntelliSense  
  
-   Informações rápidas do IntelliSense  
  
-   Conclusão de membro do IntelliSense  
  
-   Preenchimento automático de palavras do IntelliSense  
  
## <a name="partially-supported-features-in-the-mpf"></a>Recursos parcialmente suportados no MPF  
 MPF fornece suporte parcial somente para os recursos a seguir. Isso significa que você deve implementar os métodos são chamados pelo MPF.  
  
-   Reformatar o código. Forneça o código que implementa a reformatação.  
  
-   Validar os pontos de interrupção, identificando um código válido abrange. Forneça o código que identifica as extensões de código.  
  
-   Suporte o depurador **Autos** janela para exibir variáveis. Forneça o código que determina o que são exibidas na janela.  
  
-   Suporte a **barra de navegação** de navegação rápida entre tipos e membros. Você implementa e retorna uma classe auxiliar que preenche as listas de **barra de navegação** caixas de combinação.  
  
## <a name="implementation"></a>Implementação  
 Você deve concluir várias etapas para implementar o serviço de linguagem e os recursos de serviço de linguagem que você deseja oferecer suporte para o seu idioma. Essas etapas são discutidas nos tópicos a seguir:  
  
-   [Implementando um serviço de linguagem herdado](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
  
-   [Registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service1.md)  
  
-   [Coloração de sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
  
-   [Chave de correspondência em um serviço de linguagem herdado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
  
-   [Estrutura de tópicos em um serviço de linguagem herdado](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
  
-   [Comentando o código em um serviço de linguagem herdado](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
  
-   [Reformatar o código em um serviço de linguagem herdado](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
  
-   [Propriedades de documento personalizadas em um serviço de linguagem herdado](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
  
-   [Suporte a trechos de código em um serviço de linguagem herdado](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
  
-   [Suporte para a barra de navegação em um serviço de linguagem herdado](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
  
-   [Preenchimento automático de palavras em um serviço de linguagem herdado](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
  
-   [Conclusão de membro em um serviço de linguagem herdado](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
  
-   [Informações de parâmetro em um serviço de linguagem herdado](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
  
-   [Informações rápidas em um serviço de linguagem herdado](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
  
-   [Suporte para a janela Autos em um serviço de linguagem herdado](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
  
-   [Validando os pontos de interrupção em um serviço de linguagem herdado](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
  
## <a name="see-also"></a>Consulte também  
 [Implementando um serviço de linguagem herdado](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Extensibilidade de serviço de linguagem herdada](../../extensibility/internals/legacy-language-service-extensibility.md)
