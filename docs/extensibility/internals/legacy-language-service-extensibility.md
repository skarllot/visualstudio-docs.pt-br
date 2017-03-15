---
title: "Extensibilidade de serviço de linguagem herdada | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
caps.latest.revision: 42
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
ms.openlocfilehash: 2d5806c6b4133689d6ebb1a4034f4e39d867facd
ms.lasthandoff: 02/22/2017

---
# <a name="legacy-language-service-extensibility"></a>Extensibilidade de serviço de linguagem herdada
Um serviço de linguagem fornece suporte de idioma específico para a edição de código-fonte no IDE.  
  
 Serviços de linguagem herdada são implementados como parte de um VSPackage, mas a maneira mais recente para implementar recursos de serviço de linguagem é usar extensões MEF. Para obter mais informações sobre a nova maneira de implementar um serviço de linguagem, consulte [Editor e extensões do serviço de linguagem](../../extensibility/editor-and-language-service-extensions.md).  
  
 Esta seção aborda a estrutura e a implementação de um serviço de linguagem herdada.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Migrando um serviço de linguagem herdado](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 Explica como atualizar um serviço de linguagem do Visual Studio 2008 para a versão mais recente.  
  
 [Informações gerais de serviço de linguagem herdada](../../extensibility/internals/legacy-language-service-essentials.md)  
 Fornece informações importantes sobre como desenvolver serviços de linguagem para integrar uma linguagem de programação no Visual Studio.  
  
 [Desenvolvendo um serviço de linguagem herdado](../../extensibility/internals/developing-a-legacy-language-service.md)  
 Fornece links para tópicos que podem ajudá-lo a criar um serviço de linguagem.  
  
 [Sintaxe de cores em um serviço de linguagem herdado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Fornece informações sobre o suporte de realce de sintaxe em um serviço de linguagem.  
  
 [Implementando um serviço de linguagem herdado](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Fornece informações sobre como usar a estrutura de pacote gerenciado (MPF) para implementar um serviço de linguagem completa no código gerenciado.  
  
 [Suporte a ferramentas de navegação de símbolo](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Descreve as bibliotecas e ferramentas que permitem que você procure os modos de exibição de árvore de símbolos no IDE.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Editor e extensões do serviço de linguagem](../../extensibility/editor-and-language-service-extensions.md)  
 Fornece uma visão geral dos editores do Visual Studio.  
  
 [Suporte do serviço de linguagem para depuração](../../extensibility/internals/language-service-support-for-debugging.md)  
 Fornece informações e um link para o SDK do Visual Studio de depuração, que contém as informações necessárias para criar e personalizar componentes do depurador usados para depurar programas.
