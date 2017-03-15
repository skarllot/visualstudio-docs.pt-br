---
title: "Conclusão do Word em um serviço de linguagem herdado | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
caps.latest.revision: 15
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
ms.openlocfilehash: 7390b2c0cc8375ec2af586e8e09279c239e21c54
ms.lasthandoff: 02/22/2017

---
# <a name="word-completion-in-a-legacy-language-service"></a>Preenchimento automático de palavras em um serviço de linguagem herdado
Completar palavra preenche os caracteres ausentes em uma palavra digitada parcialmente. Se houver somente uma conclusão possível, a palavra é concluída quando o caractere de conclusão é inserido. Se a palavra parcial corresponde a mais de uma possibilidade, é exibida uma lista de possíveis conclusões. Um caractere de preenchimento pode ser qualquer caractere que não é usado para identificadores.  
  
 Serviços de linguagem herdada são implementados como parte de um VSPackage, mas a maneira mais recente para implementar recursos de serviço de linguagem é usar extensões MEF. Para obter mais informações, consulte [estendendo o Editor e serviços de linguagem](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  É recomendável que você comece a usar o novo editor de API assim que possível. Isso irá melhorar o desempenho do seu serviço de linguagem e lhe permitem tirar proveito dos novos recursos do editor.  
  
## <a name="implementation-steps"></a>Etapas de implementação  
  
1.  Quando o usuário seleciona **Complete Word** do **IntelliSense** menu, o <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>comando é enviado para o serviço de linguagem.</xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>  
  
2.  A <xref:Microsoft.VisualStudio.Package.ViewFilter>classe captura o comando e chama o <xref:Microsoft.VisualStudio.Package.Source.Completion%2A>método com a razão de análise de <xref:Microsoft.VisualStudio.Package.ParseReason>.</xref:Microsoft.VisualStudio.Package.ParseReason> </xref:Microsoft.VisualStudio.Package.Source.Completion%2A> </xref:Microsoft.VisualStudio.Package.ViewFilter>  
  
3.  A <xref:Microsoft.VisualStudio.Package.Source>classe, em seguida, chama o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>método para obter a lista de conclusões possíveis e, em seguida, exibe as palavras em uma lista de dica de ferramenta usando a <xref:Microsoft.VisualStudio.Package.CompletionSet>classe.</xref:Microsoft.VisualStudio.Package.CompletionSet> </xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> </xref:Microsoft.VisualStudio.Package.Source>  
  
     Se houver apenas uma palavra correspondente, a <xref:Microsoft.VisualStudio.Package.Source>classe completa a palavra.</xref:Microsoft.VisualStudio.Package.Source>  
  
 Como alternativa, se o scanner retornará o valor de gatilho <xref:Microsoft.VisualStudio.Package.TokenTriggers>quando o primeiro caractere de um identificador é digitado, a <xref:Microsoft.VisualStudio.Package.Source>classe detecta isso e chama o <xref:Microsoft.VisualStudio.Package.Source.Completion%2A>método com a razão de análise de <xref:Microsoft.VisualStudio.Package.ParseReason>.</xref:Microsoft.VisualStudio.Package.ParseReason> </xref:Microsoft.VisualStudio.Package.Source.Completion%2A> </xref:Microsoft.VisualStudio.Package.Source> </xref:Microsoft.VisualStudio.Package.TokenTriggers> Nesse caso, o analisador deve detectar a presença de um caractere de seleção de membro e fornecer uma lista de membros.  
  
## <a name="enabling-support-for-the-complete-word"></a>Habilitando o suporte para a palavra inteira  
 Para habilitar o suporte para o conjunto de conclusão do word o `CodeSense` chamado parâmetro passado para o <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>associado ao pacote de idioma do atributo de usuário.</xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Isso define a <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A>propriedade de <xref:Microsoft.VisualStudio.Package.LanguagePreferences>classe.</xref:Microsoft.VisualStudio.Package.LanguagePreferences> </xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A>  
  
 O analisador deve retornar uma lista de declarações em resposta ao valor motivo análise <xref:Microsoft.VisualStudio.Package.ParseReason>, para a conclusão do word operar.</xref:Microsoft.VisualStudio.Package.ParseReason>  
  
## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implementando palavra completa no método ParseSource  
 Para a conclusão do word, o <xref:Microsoft.VisualStudio.Package.Source>classe chamadas a <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>método o <xref:Microsoft.VisualStudio.Package.AuthoringScope>classe para obter uma lista de possíveis correspondências.</xref:Microsoft.VisualStudio.Package.AuthoringScope> </xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> </xref:Microsoft.VisualStudio.Package.Source> Você deve implementar a lista em uma classe que deriva de <xref:Microsoft.VisualStudio.Package.Declarations>classe.</xref:Microsoft.VisualStudio.Package.Declarations> Consulte o <xref:Microsoft.VisualStudio.Package.Declarations>classe para obter detalhes sobre os métodos que você deve implementar.</xref:Microsoft.VisualStudio.Package.Declarations>  
  
 Se a lista contiver apenas uma única palavra, em seguida, a <xref:Microsoft.VisualStudio.Package.Source>classe insere automaticamente essa palavra em vez da palavra parcial.</xref:Microsoft.VisualStudio.Package.Source> Se a lista contiver mais de uma palavra, o <xref:Microsoft.VisualStudio.Package.Source>classe apresenta uma lista de dica de ferramenta da qual o usuário pode selecionar a opção apropriada.</xref:Microsoft.VisualStudio.Package.Source>  
  
 Também veja o exemplo de um <xref:Microsoft.VisualStudio.Package.Declarations>na implementação da classe [conclusão de membro em um serviço de linguagem herdado](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).</xref:Microsoft.VisualStudio.Package.Declarations>
