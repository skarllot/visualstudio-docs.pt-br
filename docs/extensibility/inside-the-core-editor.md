---
title: "Dentro do Editor de núcleo | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: 21
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
ms.openlocfilehash: 9a3a6d39539c6abfc7e5ccb28d39f7eff23eb862
ms.lasthandoff: 02/22/2017

---
# <a name="inside-the-core-editor"></a>Dentro do Editor de núcleo
O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] principal editor é um conjunto de vários componentes que permitem que você modifique e consultar informações textuais. Se você tiver personalizado o editor principal usando a API herdada, você pode continuar a usar essas personalizações, que serão roteadas através de adaptadores do editor. No entanto, ele é recomendável que você adapte suas personalizações para o novo editor de API.  
  
 As seguintes áreas são alguns aspectos importantes do editor principal:  
  
-   Buffer de texto  
  
-   Exibição de texto  
  
-   Janela de código  
  
-   Marcadores de texto  
  
-   Gerenciador de texto  
  
-   Integração com serviços de linguagem  
  
## <a name="in-this-section"></a>Nesta seção  
 [Criando o Editor principal usando a API herdada](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Fornece instruções passo a passo sobre como usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>para criar uma instância do núcleo do editor.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>  
  
 [Acessando o Buffer de texto usando a API herdada](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 Discute a função do buffer de texto no editor de núcleo, explica os sistemas associados que são usados para acessar o buffer e fornece uma lista das interfaces implementadas pelo objeto de buffer de texto, <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.</xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>  
  
 [Eventos de Buffer de texto na API herdada](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Fornece uma lista das interfaces que são usadas para notificação de eventos de buffer de texto.  
  
 [Como: registrar eventos de Buffer de texto com a API herdada](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 Descreve como eventos de buffer de texto de aviso.  
  
 [Usando o Gerenciador de texto para monitorar as configurações globais](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Aborda como receber notificação de eventos do Gerenciador de texto e como o Gerenciador de texto é usado para compartilhar informações de preferências globais com os componentes principais do editor.  
  
 [Acessando theText exibição usando a API herdada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 Descreve a função do modo de exibição de texto no editor de núcleo e lista as interfaces implementadas pelo <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>objeto.</xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>  
  
 [Personalizando o Windows de código usando a API herdada](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Fornece informações sobre como uma janela de código é usada para incluir o modo de exibição de texto, discute como o Gerenciador de janelas de código é usado para fornecer decorações à janela de código e fornece notificação de novas visualizações.  
  
 [Alterando as configurações de exibição usando a API herdada](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Fornece instruções passo a passo sobre como forçar configurações de exibição e como remover configurações forçadas.  
  
 [Serviços de linguagem e o Editor de núcleo](../extensibility/language-services-and-the-core-editor.md)  
 Descreve a instanciação de um serviço de linguagem para decorações de código do controle.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Passo a passo: Criar um Editor de núcleo e registrar um tipo de arquivo do Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Fornece instruções passo a passo sobre como iniciar o editor de núcleo do código gerenciado.  
  
 [Barra de menu suspenso](../extensibility/drop-down-bar.md)  
 Discute como a barra suspensa é usada na janela de código e descreve as interfaces que são usadas quando você implementa uma barra de menu suspenso.  
  
 [Usar marcadores de texto com a API herdada](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Explica o conceito de marcadores de texto e como eles são usados no editor de núcleo e lista as interfaces que são usadas para acessar e gerenciar marcadores de texto.  
  
 [Como: adicionar marcadores de texto padrão](../extensibility/how-to-add-standard-text-markers.md)  
 Fornece instruções passo a passo sobre como criar um marcador de texto e como adicionar um comando personalizado a um menu de atalho.  
  
 [Como: criar marcadores de texto personalizado](../extensibility/how-to-create-custom-text-markers.md)  
 Fornece instruções passo a passo sobre como criar um marcador de texto personalizado e como fornecer o tipo de marcador, como um serviço.
