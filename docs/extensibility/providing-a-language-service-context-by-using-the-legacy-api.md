---
title: "Fornecer um contexto de serviço de idioma usando a API herdada | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
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
ms.openlocfilehash: 10221f77e65acfb91c625c2f711b5804b64f827e
ms.lasthandoff: 02/22/2017

---
# <a name="providing-a-language-service-context-by-using-the-legacy-api"></a>Fornecer um contexto de serviço de idioma usando a API herdada
Há duas opções para um serviço de linguagem fornecer o contexto de usuário usando o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor básicos: fornecer contexto do marcador de texto, ou fornecer todo o contexto de usuário. As diferenças entre cada um deles são descritas aqui.  
  
 Para obter mais informações sobre o fornecimento de contexto para um serviço de linguagem que está conectado ao seu próprio editor, consulte [como: fornecer contexto para os editores](../extensibility/how-to-provide-context-for-editors.md).  
  
## <a name="provide-text-marker-context-to-the-editor"></a>Fornecer o contexto de marcador de texto no Editor  
 Para fornecer contexto para erros de compilador indicados por marcadores de texto no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] principal editor, implemente o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> Nesse cenário, o serviço de linguagem fornece contexto somente quando o cursor está sobre um marcador de texto. Isso permite que o editor fornecer a palavra-chave na posição do cursor para a **ajuda dinâmica** janela sem atributos.  
  
## <a name="provide-all-user-context-to-the-editor"></a>Fornecer todo o contexto de usuário para o Editor  
 Se você estiver criando um serviço de linguagem e estiver usando o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] principal editor, em seguida, você pode implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>interface para fornecer contexto para o serviço de linguagem.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>  
  
 Para a implementação de `IVsLanguageContextProvider`, um recipiente de contexto (coleção) é anexado ao editor, que é responsável por atualizar o recipiente de contexto. Quando o **ajuda dinâmica** janela chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A>interface deste recipiente de contexto no tempo ocioso, o recipiente de contexto consultará o editor para uma atualização.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> O editor notifica o serviço de linguagem que deve atualizar o editor e passa um ponteiro para o recipiente de contexto. Isso é feito chamando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A>método do editor para o serviço de linguagem.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A> Usando o ponteiro para o recipiente de contexto, o serviço de linguagem pode agora adicionar e remover palavras-chave e atributos. Para obter mais informações, consulte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>  
  
 Há duas maneiras de implementar `IVsLanguageContextProvider`:  
  
-   Forneça uma palavra-chave para o recipiente de contexto  
  
     Quando o editor é chamado para atualizar o recipiente de contexto, passe a palavras-chave e atributos e, em seguida, retornar `S_OK`. Esse valor de retorno instrui o editor para manter seu contexto de palavra-chave e atributo em vez de fornecer a palavra-chave na posição do cursor para o recipiente de contexto.  
  
-   Obter a palavra-chave de palavra-chave na posição do cursor  
  
     Quando o editor é chamado para atualizar o recipiente de contexto, passe os atributos apropriados e, em seguida, retornar `E_FAIL`. Esse valor de retorno instrui o editor para manter seus atributos no recipiente de contexto, mas atualizar o recipiente de contexto com a palavra-chave na posição do cursor.  
  
 O diagrama a seguir demonstra como o contexto é fornecido para um serviço de linguagem que implementa `IVsLanguageContextProvider`.  
  
 ![Gráfico de LangServiceImplementation2](~/extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
Contexto de um serviço de linguagem  
  
 Como você pode ver no diagrama, o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor de texto principal tem um recipiente de contexto anexado a ele. Esse recipiente de contexto aponta para três recipientes subcontexto separado: serviço de linguagem, o editor de padrão e o marcador de texto. Os recipientes language service e texto marcador subcontexto contêm atributos e palavras-chave para o serviço de linguagem se o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>interface é implementada, marcadores de texto e se o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>interface é implementada.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> Se você não implementar qualquer uma dessas interfaces, o editor fornece contexto para a palavra-chave na posição do cursor no recipiente de contexto do editor de padrão.  
  
## <a name="context-guidelines-for-editors-and-designers"></a>Diretrizes de contexto para editores e Designers  
 Designers e editores devem fornecer uma palavra-chave geral do editor ou a janela do designer. Isso é feito para que exiba um tópico de ajuda genérico, mas apropriado, para o designer ou editor quando o usuário pressiona F1. Um editor deve, além disso, forneça a palavra-chave atual na posição do cursor ou fornecer um termo-chave com base na seleção atual. Isso é feito para garantir que um tópico da Ajuda para o texto ou elemento de interface do usuário apontado ou selecionado exibe quando o usuário pressiona F1. Um designer fornece contexto para um item selecionado em um designer, como um botão em um formulário. Editores e designers também devem se conectar a um serviço de linguagem conforme descrito em [herdado Language Service Essentials](../extensibility/internals/legacy-language-service-essentials.md).
