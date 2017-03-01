---
title: "Implementando a coloração de sintaxe | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
caps.latest.revision: 20
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
ms.openlocfilehash: 67535bcc2c907978c24d764c617f8311dc51a444
ms.lasthandoff: 02/22/2017

---
# <a name="implementing-syntax-coloring"></a>Implementando a coloração de sintaxe
Quando o serviço de linguagem fornece coloração de sintaxe, o analisador converte uma linha de texto em uma matriz de itens pode ser coloridos e retorna tipos de token correspondente a esses itens pode ser coloridos. O analisador deve retornar tipos de token que pertencem a uma lista de itens pode ser coloridos. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Exibe cada item pode ser colorido na janela de código de acordo com os atributos atribuídos pelo objeto colorizador para o tipo de token apropriado.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Especifica uma interface de analisador, e a implementação de analisador é completamente até você. No entanto, uma implementação de analisador padrão é fornecida no projeto do pacote de idiomas do Visual Studio. Para código gerenciado, a estrutura de pacote gerenciado (MPF) fornece suporte completo para colorir o texto.  
  
 Serviços de linguagem herdada são implementados como parte de um VSPackage, mas a maneira mais recente para implementar recursos de serviço de linguagem é usar extensões MEF. Para obter mais informações sobre a nova maneira de implementar a coloração de sintaxe, consulte [passo a passo: texto realçando](../../extensibility/walkthrough-highlighting-text.md).  
  
> [!NOTE]
>  É recomendável que você comece a usar o novo editor de API assim que possível. Isso irá melhorar o desempenho do seu serviço de linguagem e lhe permitem tirar proveito dos novos recursos do editor.  
  
## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Etapas seguidas por um Editor para colorir o texto  
  
1.  O editor obtém o colorizador chamando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>objeto.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>  
  
2.  As chamadas do editor de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A>método para determinar se o colorizador precisa o estado de cada linha para ser mantida fora de colorizador.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A>  
  
3.  Se o colorizador requer que o estado seja mantido fora o colorizador, o editor chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A>método para obter o estado da primeira linha.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A>  
  
4.  Para cada linha no buffer, o editor chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>método, que executa as seguintes etapas:</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>  
  
    1.  A linha de texto é passada para um scanner para converter o texto em tokens. Cada token Especifica o texto do token e o tipo de token.  
  
    2.  O tipo de token é convertido em um índice em uma lista de itens pode ser colorido.  
  
    3.  As informações do token são usadas para preencher uma matriz, de modo que cada elemento da matriz corresponde a um caractere na linha. Os valores armazenados na matriz são os índices para a lista de itens pode ser colorido.  
  
    4.  O estado no final da linha é retornado para cada linha.  
  
5.  Se o colorizador requer que o estado seja mantido, o editor armazena em cache o estado para aquela linha.  
  
6.  O editor renderiza a linha de texto usando as informações retornadas de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>método.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Isso exige as seguintes etapas:  
  
    1.  Para cada caractere na linha, obtém o índice do item pode ser colorido.  
  
    2.  Se usar itens padrão pode ser colorido, acesse a lista de itens pode ser colorido do editor.  
  
    3.  Caso contrário, chamar o serviço de linguagem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>método para obter um item pode ser colorido.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>  
  
    4.  Use as informações no item pode ser colorido para processar o texto na exibição.  
  
## <a name="managed-package-framework-colorizer"></a>Colorizador de estrutura de pacote gerenciado  
 A estrutura de pacote gerenciado (MPF) fornece todas as classes que são necessários para implementar um colorizador. Sua classe de serviço de linguagem deve herdar de <xref:Microsoft.VisualStudio.Package.LanguageService>classe e implementar os métodos necessários.</xref:Microsoft.VisualStudio.Package.LanguageService> Você deve fornecer um scanner e parser Implementando o <xref:Microsoft.VisualStudio.Package.IScanner>da interface e retornar uma instância da interface do <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>método (um dos métodos que devem ser implementados na <xref:Microsoft.VisualStudio.Package.LanguageService>classe).</xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> </xref:Microsoft.VisualStudio.Package.IScanner> Para obter mais informações, consulte [coloração de sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como: usar itens pode ser coloridos internos](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Itens pode ser coloridos personalizados](../../extensibility/internals/custom-colorable-items.md)   
 [Desenvolvendo um serviço de linguagem herdado](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Coloração de sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
