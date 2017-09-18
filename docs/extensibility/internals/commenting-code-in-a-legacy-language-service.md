---
title: "Comentando o código em um serviço de linguagem herdado | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
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
ms.openlocfilehash: 801afcf27049a9b11dfdc322a16e5451b6fb8f7d
ms.lasthandoff: 02/22/2017

---
# <a name="commenting-code-in-a-legacy-language-service"></a>Comentando o código em um serviço de linguagem herdado
Linguagens de programação normalmente fornecem um meio de anotações ou comentários de código. Um comentário é uma seção de texto que fornece informações adicionais sobre o código, mas é ignorada durante a compilação ou interpretação.  
  
 As classes do framework (MPF) pacote gerenciado oferecem suporte para comentário e removendo o texto selecionado.  
  
## <a name="comment-styles"></a>Estilos de comentário  
 Há dois estilos gerais de comentário:  
  
1.  Comentários de linha, onde o comentário esteja em uma única linha.  
  
2.  Comentários do bloco, onde o comentário pode incluir várias linhas.  
  
 Comentários de linha normalmente têm um caractere inicial (ou caracteres), enquanto os comentários do bloco têm caracteres iniciais e finais. Por exemplo, no c#, um comentário de linha começa com / /, e um comentário de bloco começa com / * e termina com \*/.  
  
 Quando o usuário seleciona o comando **comentário seleção** do **editar** -> **avançado** menu, o comando é roteado para o <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A>método de <xref:Microsoft.VisualStudio.Package.Source>classe.</xref:Microsoft.VisualStudio.Package.Source> </xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> Quando o usuário seleciona o comando **seleção remova**, o comando é roteado para o <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A>método.</xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A>  
  
## <a name="supporting-code-comments"></a>Comentários de código de suporte  
 Você pode ter seus comentários de código do idioma serviço suporte por meio do `EnableCommenting` chamado parâmetro de <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>.</xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Isso define a <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A>propriedade de <xref:Microsoft.VisualStudio.Package.LanguagePreferences>classe.</xref:Microsoft.VisualStudio.Package.LanguagePreferences> </xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> Para obter mais informações sobre a configuração de idioma servicce recursos, consulte [registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service1.md)).  
  
 Você também deve substituir o <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>método retorne um <xref:Microsoft.VisualStudio.Package.CommentInfo>estrutura com os caracteres de comentário para seu idioma.</xref:Microsoft.VisualStudio.Package.CommentInfo> </xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> C#-caracteres de comentário de linha de estilo são o padrão.  
  
### <a name="example"></a>Exemplo  
 Aqui está um exemplo de implementação do <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>método.</xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>  
  
```c#  
using Microsoft.VisualStudio.Package;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        public override CommentInfo GetCommentFormat() {  
            CommentInfo info = new CommentInfo();  
            info.LineStart       = "//";  
            info.BlockStart      = "/*";  
            info.BlockEnd        = "*/";  
            info.UseLineComments = true;  
            return info;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Recursos de serviço de linguagem herdada](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service1.md)
