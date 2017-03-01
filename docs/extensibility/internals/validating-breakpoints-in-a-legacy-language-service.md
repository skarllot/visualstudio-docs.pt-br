---
title: "Validando os pontos de interrupção em um serviço de linguagem herdado | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
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
ms.openlocfilehash: 3a8c2df45c0a834430a499cf6a7e7ef2da10bdbf
ms.lasthandoff: 02/22/2017

---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Validando os pontos de interrupção em um serviço de linguagem herdado
Um ponto de interrupção indica que a execução do programa deve parar em um momento específico, enquanto ele está sendo executado em um depurador. Um usuário pode colocar um ponto de interrupção em qualquer linha no arquivo de origem, uma vez que o editor não tem conhecimento do que constitui um local válido para um ponto de interrupção. Quando o depurador é iniciado, todos os pontos de interrupção marcados (chamados de pontos de interrupção pendentes) são vinculados para o local apropriado no programa em execução. Ao mesmo tempo que os pontos de interrupção são validados para garantir que eles marcam os locais de código válido. Por exemplo, um ponto de interrupção em um comentário não é válido, porque não há nenhum código nesse local no código-fonte. O depurador desabilita os pontos de interrupção inválidos.  
  
 Desde que o serviço de linguagem sabe sobre o código-fonte que está sendo exibido, ele pode validar os pontos de interrupção antes que o depurador é iniciado. Você pode substituir o <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>método retorne um intervalo especificando um local válido para um ponto de interrupção.</xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> O local do ponto de interrupção ainda será validado quando o depurador é iniciado, mas o usuário é notificado de pontos de interrupção inválida sem esperar que o depurador carregar.  
  
## <a name="implementing-support-for-validating-breakpoints"></a>Implementando o suporte para validação de pontos de interrupção  
  
-   O <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>método é dada a posição do ponto de interrupção.</xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> Sua implementação deve decidir se ou não o local é válido e indicar isso retornando um intervalo de texto que identifica o código associado à posição de linha no ponto de interrupção.  
  
-   Retornar <xref:Microsoft.VisualStudio.VSConstants.S_OK>se o local é válido, ou <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>se ele não é válido.</xref:Microsoft.VisualStudio.VSConstants.S_FALSE> </xref:Microsoft.VisualStudio.VSConstants.S_OK>  
  
-   Se o ponto de interrupção é válido do trecho de texto será realçado juntamente com o ponto de interrupção.  
  
-   Se o ponto de interrupção for inválido, uma mensagem de erro será exibida na barra de status.  
  
### <a name="example"></a>Exemplo  
 Este exemplo mostra uma implementação de <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>método que chama o analisador para obter o trecho de código (se houver) no local especificado.</xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>  
  
 Este exemplo pressupõe que você tenha adicionado um `GetCodeSpan` método para o <xref:Microsoft.VisualStudio.Package.AuthoringSink>classe valida o trecho de texto e retorna `true` se for um local de ponto de interrupção válido.</xref:Microsoft.VisualStudio.Package.AuthoringSink>  
  
```c#  
using Microsoft VisualStudio;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    class TestLanguageService : LanguageService  
    {  
        public override int ValidateBreakpointLocation(IVsTextBuffer buffer,  
                                                       int line,  
                                                       int col,  
                                                       TextSpan[] pCodeSpan)  
        {  
            int retval = VSConstants.S_FALSE;  
            if (pCodeSpan != null)  
            {  
                // Initialize span to current line by default.  
                pCodeSpan[0].iStartLine = line;  
                pCodeSpan[0].iStartIndex = col;  
                pCodeSpan[0].iEndLine = line;  
                pCodeSpan[0].iEndIndex = col;  
            }  
  
            if (buffer != null)  
            {  
                IVsTextLines textLines = buffer as IVsTextLines;  
                if (textLines != null)  
                {  
                    Source src = this.GetSource(textLines);  
                    if (src != null)  
                    {  
                        TokenInfo tokenInfo = new TokenInfo();  
                        string text = src.GetText();  
                        ParseRequest req = CreateParseRequest(src,  
                                                              line,  
                                                              col,  
                                                              tokenInfo,  
                                                              text,  
                                                              src.GetFilePath(),  
                                                              ParseReason.CodeSpan,  
                                                              null);  
                        req.Scope = this.ParseSource(req);  
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;  
  
                        TextSpan span = new TextSpan();  
                        if (sink.GetCodeSpan(out span))  
                        {  
                            pCodeSpan[0] = span;  
                            retval = VSConstants.S_OK;  
                        }  
                    }  
                }  
            }  
            return retval;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Recursos de serviço de linguagem herdada](../../extensibility/internals/legacy-language-service-features1.md)
