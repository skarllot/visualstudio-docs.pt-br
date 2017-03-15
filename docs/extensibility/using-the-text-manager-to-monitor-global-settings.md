---
title: "Usando o Gerenciador de texto para monitorar as configurações globais | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: 14
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
ms.openlocfilehash: 023faf1ec17c1ba6b27f85c5442743ebee3b3992
ms.lasthandoff: 02/22/2017

---
# <a name="using-the-text-manager-to-monitor-global-settings"></a>Usando o Gerenciador de texto para monitorar as configurações globais
Se você implementar um editor de núcleo, você deve monitorar as alterações feitas nas configurações globais, porque essas alterações podem afetar sua instância do editor. Você pode controlar as alterações de ouvir eventos gerados pelo Gerenciador de texto. Por exemplo, quando você especifica uma preferência global para a aparência ou o comportamento de um componente no editor de núcleo, como seu objeto de dados de documento, o Gerenciador de texto armazena essas informações e envia a todos os clientes afetados.  
  
## <a name="text-manager-functions"></a>Funções do Gerenciador de texto  
 O Gerenciador de texto gera eventos de várias configurações, incluindo o seguinte:  
  
-   Se um buffer está sob controle do código fonte  
  
-   Como se registrar para notificações de alteração de arquivo  
  
-   Como manter o controle de quais modos de exibição estão associados a determinadas buffers  
  
-   Preferências de colorização de texto  
  
-   Guia versus preferências de espaço  
  
 Preferências são exclusivas para um determinado idioma não são gerenciadas pelo Gerenciador de texto. Essas configurações devem ser gerenciadas por cada serviço de linguagem.  
  
 Notificação de eventos para o Gerenciador de texto fornecida pelo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> Implementar essa interface no cliente do objeto para manipular eventos gerou o Gerenciador de texto. Registrar esses eventos usando o <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>interface no Gerenciador de texto.</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>  
  
## <a name="see-also"></a>Consulte também  
 [Dentro do Editor de núcleo](../extensibility/inside-the-core-editor.md)   
 [Recursos do Editor](http://msdn.microsoft.com/en-us/bdac940d-1f14-4019-a01f-fd0bb3dc7198)
