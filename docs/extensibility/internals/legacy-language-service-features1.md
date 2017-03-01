---
title: "Linguagem herdada serviço Features1 | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
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
ms.openlocfilehash: 2cd4b22cc267c29f29f50df095774a9c09ced2c9
ms.lasthandoff: 02/22/2017

---
# <a name="legacy-language-service-features"></a>Recursos de serviço de linguagem herdada
Um serviço de linguagem do framework (MPF) pacote gerenciado pode oferecer suporte a um ou mais [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] recursos como realce de sintaxe, IntelliSense e validação de ponto de interrupção. Cada recurso pode ser implementado independente dos outros, mas exigem um analisador e um scanner, exceto de realce de sintaxe, que requer apenas um scanner.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Chave de correspondência em um serviço de linguagem herdado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 Descreve o que é necessário para suportar o par de idiomas correspondente, também conhecido como correspondência de chaves.  
  
 [Comentando o código em um serviço de linguagem herdado](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 Descreve o que é necessário para suportar os comentários e remover comentários do código selecionado.  
  
 [Propriedades de documento personalizadas em um serviço de linguagem herdado](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 Descreve o que é necessário para dar suporte a propriedades de documento que são inseridas em um arquivo de origem.  
  
 [Estrutura de tópicos em um serviço de linguagem herdado](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 Descreve o que é necessário para dar suporte a estrutura de tópicos por meio da implementação de regiões ocultas.  
  
 [Reformatar o código em um serviço de linguagem herdado](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 Descreve o que é necessário para dar suporte a reformatação de código.  
  
 [Suporte a trechos de código em um serviço de linguagem herdado](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 Descreve o que é necessário para dar suporte a trechos de código, que são segmentos de código que são inseridos e podem ser editados.  
  
 [Informações de parâmetro em um serviço de linguagem herdado](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 Descreve o que é necessário para suportar a operação de informações de parâmetro do IntelliSense para exibir a assinatura de um método como o método é digitado.  
  
 [Informações rápidas em um serviço de linguagem herdado](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 Descreve o que é necessário para suportar a operação de informações rápidas do IntelliSense para exibir informações sobre um identificador.  
  
 [Conclusão de membro em um serviço de linguagem herdado](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 Descreve o que é necessário para suportar a operação de membro do IntelliSense para selecionar um membro de um namespace de uma lista.  
  
 [Preenchimento automático de palavras em um serviço de linguagem herdado](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 Descreve o que é necessário para oferecer suporte a operação IntelliSense Complete Word para completar palavras parcialmente digitadas.  
  
 [Suporte para a janela Autos em um serviço de linguagem herdado](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 Descreve o que um serviço de linguagem pode fazer para oferecer suporte a **Autos** janela enquanto você está depurando.  
  
 [Suporte para a barra de navegação em um serviço de linguagem herdado](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 Descreve como usar o **barra de navegação** na parte superior da exibição de editor para fornecer uma navegação rápida a qualquer tipo ou membro no arquivo mostrado na exibição...  
  
 [Coloração de sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 Descreve o que é necessário para suportar o realce de sintaxe do código-fonte.  
  
 [Validando os pontos de interrupção em um serviço de linguagem herdado](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 Descreve o que um serviço de linguagem pode fazer para oferecer suporte a pontos de interrupção validação fora de um depurador.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Scanner e Parser de serviço de linguagem herdada](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Descreve o analisador e o scanner que são necessários para implementar todos os recursos de um serviço de linguagem que utiliza a estrutura de pacote gerenciado.  
  
 [Implementando um serviço de linguagem herdado](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Descreve o que é necessário para implementar um serviço de linguagem usando MPF.  
  
 [Registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Descreve as etapas necessárias para registrar um serviço de linguagem baseada em MPF com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Usando o IntelliSense](../../ide/using-intellisense.md)  
 Explica como o IntelliSense torna referências da linguagem fácil acesso.  
  
 [Implementando um serviço de linguagem herdado](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Fornece informações sobre como usar a estrutura de pacote gerenciado (MPF) para implementar um serviço de linguagem completa no código gerenciado.
