---
title: "Informações gerais de serviço de linguagem herdada | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
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
ms.openlocfilehash: f6f8ba46289e27b2465436a103091983c17de1c0
ms.lasthandoff: 02/22/2017

---
# <a name="legacy-language-service-essentials"></a>Informações gerais de serviço de linguagem herdada
Você deve fornecer um serviço de linguagem para integrar uma linguagem de programação no Visual Studio. Este tópico explica os recursos disponíveis nos serviços de linguagem herdada.  
  
 Serviços de linguagem herdada são implementados como parte de um VSPackage, mas a maneira mais recente para implementar recursos de serviço de linguagem é usar extensões MEF. Para obter mais informações sobre a nova maneira de implementar um serviço de linguagem, consulte [Editor e extensões do serviço de linguagem](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  É recomendável que você comece a usar o novo editor de API assim que possível. Isso irá melhorar o desempenho do seu serviço de linguagem e lhe permitem tirar proveito dos novos recursos do editor.  
  
 Linguagem herdada serviços fornecem os seguintes recursos:  
  
|Recurso|Descrição|  
|-------------|-----------------|  
|Coloração de sintaxe|Faz com que o modo de edição exibir diferentes cores e estilos de fonte para os diferentes elementos de um idioma. Essa diferenciação pode tornar mais fácil de ler e editar arquivos.<br /><br /> Para obter informações gerais, consulte [coloração de sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Para obter informações sobre esse recurso na estrutura de pacote gerenciado (MPF), consulte [coloração de sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|  
|Conclusão da instrução|Conclui uma instrução ou palavra-chave que o usuário começa a digitar. Conclusão de instrução ajuda os usuários a digitar instruções difícil mais facilmente, com menos digitação e menos chances para erro.<br /><br /> Para obter informações gerais, consulte [conclusão de instrução em um serviço de linguagem herdado](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Para obter informações sobre esse recurso no MPF, consulte [preenchimento automático de palavras em um serviço de linguagem herdado](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|  
|Correspondência de chaves|Destaques do par de caracteres como chaves. Quando o usuário digita um caractere de fechamento, como "}", a correspondência de colchetes destaca correspondente abrindo o caractere, como "{". Quando há vários níveis de caracteres de circunscrição, esse recurso ajuda os usuários a confirmar que os caracteres delimitadores estão emparelhados corretamente.<br /><br /> Para obter informações sobre esse recurso no MPF, consulte [correspondência de chaves em um serviço de linguagem herdado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|  
|Dicas de ferramentas de informações de parâmetro|Exibe uma lista de assinaturas possíveis para o método sobrecarregado que o usuário está digitando atualmente.<br /><br /> Para obter informações gerais, consulte [informações de parâmetro em um serviço de linguagem herdado](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Para obter informações sobre esse recurso no MPF, consulte [informações de parâmetro em um serviço de linguagem herdado](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|  
|Marcadores de erro|Exibe um sublinhado vermelho ondulado, também conhecido como um ondulada, sob o texto que está sintaticamente incorreto. Marcadores de erro geralmente são usadas para informar os usuários de palavras-chave incorretas, parênteses não fechadas, caracteres inválidos e erros semelhantes.<br /><br /> As classes MPF, marcadores de erro são manipulados automaticamente no <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A>método de <xref:Microsoft.VisualStudio.Package.AuthoringSink>classe.</xref:Microsoft.VisualStudio.Package.AuthoringSink> </xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A>|  
  
 Muitos desses recursos exigem que o serviço de linguagem para analisar o código-fonte. Você geralmente pode reutilizar a criar tokens e analisar o código para o compilador ou intérprete.  
  
 Os recursos a seguir estão relacionados para oferecer suporte a linguagens de programação, mas não fazem parte dos serviços de idioma:  
  
|Recurso|Descrição|  
|-------------|-----------------|  
|Avaliadores de expressão|Oferece suporte a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador Validando os pontos de interrupção e fornecendo uma lista de expressões a serem exibidos no **Autos** janela de depuração.<br /><br /> Para obter mais informações, consulte [suporte do serviço de linguagem para depuração](../../extensibility/internals/language-service-support-for-debugging.md).|  
|Ferramentas de navegação de símbolo|Oferece suporte a **Pesquisador de objetos**, **exibição de classe**, **Pesquisador de chamadas**, e **localizar resultados de símbolos**.|
