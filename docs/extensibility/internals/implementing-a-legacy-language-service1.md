---
title: Implementando um Service1 de idioma herdado | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
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
ms.openlocfilehash: 855f511bec90a9c302433c1489f09b3292b38b40
ms.lasthandoff: 02/22/2017

---
# <a name="implementing-a-legacy-language-service"></a>Implementando um serviço de linguagem herdado
Você pode usar classes do framework de pacote gerenciado (MPF) para implementar um serviço de linguagem herdada que oferece suporte a uma ampla variedade de recursos, como realce de sintaxe, a correspondência de colchetes e do IntelliSense.  
  
 Serviços de linguagem herdada são implementados como parte de um VSPackage, mas a maneira mais recente para implementar recursos de serviço de linguagem é usar extensões MEF. Para obter mais informações sobre a nova maneira de implementar um serviço de linguagem, consulte [Editor e extensões do serviço de linguagem](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  É recomendável que você comece a usar o novo editor de API assim que possível. Isso irá melhorar o desempenho do seu serviço de linguagem e lhe permitem tirar proveito dos novos recursos do editor.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral do serviço de linguagem herdada](../../extensibility/internals/legacy-language-service-overview.md)  
 Uma visão geral dos recursos de serviço de linguagem que têm suporte no MPF.  
  
 [Implementando um serviço de linguagem herdado](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Descreve o que é necessário para implementar um serviço de linguagem usando MPF.  
  
 [Registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Descreve as etapas necessárias para registrar um serviço de linguagem baseada em MPF com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Scanner e Parser de serviço de linguagem herdada](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Descreve os dois analisadores que são necessárias para implementar todos os recursos de um serviço de linguagem usando MPF.  
  
 [Passo a passo: Criando um serviço de linguagem herdado](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)  
 Fornece as etapas básicas necessárias para implementar um serviço de linguagem MPF em um VSPackage.  
  
 [Passo a passo: Obtendo uma lista de trechos de código instalado (implementação herdado)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)  
 Demonstra as técnicas de recuperação de uma lista de trechos de código instalado.  
  
 [Recursos de serviço de linguagem herdada](../../extensibility/internals/legacy-language-service-features1.md)  
 Fornece links para tópicos que detalham o que deve ser feito para implementar todos os recursos de um serviço de linguagem usando MPF.
