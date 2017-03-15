---
title: "Formatação automática em um serviço de linguagem herdado | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
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
ms.openlocfilehash: ad24df06dbff415636e5042f08696cb00a7832d1
ms.lasthandoff: 02/22/2017

---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Formatação em um serviço de linguagem herdado automática
Com a formatação automática, um serviço de linguagem automaticamente insere um trecho de código quando um usuário começa a digitar uma construção de código conhecidas.  
  
## <a name="automatic-formatting-behavior"></a>Comportamento da formatação automática  
 Por exemplo, quando você digitar `if`, o serviço de linguagem insere automaticamente chaves correspondentes, ou se você pressionar a tecla ENTER, o serviço de linguagem força o ponto de inserção na nova linha para o nível de recuo apropriado, dependendo se a linha precedente abre um novo escopo.  
  
 O filtro de comando usado para o resto do serviço de idioma também pode ser usado para formatação automática. Você também pode realçar chaves correspondentes chamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolvendo um serviço de linguagem herdado](../../extensibility/internals/developing-a-legacy-language-service.md)
