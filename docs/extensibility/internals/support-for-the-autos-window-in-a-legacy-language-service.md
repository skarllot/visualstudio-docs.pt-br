---
title: "Suporte para a janela Autos em um serviço de linguagem herdado | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
caps.latest.revision: 12
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
ms.openlocfilehash: 88cff53ca5c335fdf60aef85d79e9c6e86f03cfa
ms.lasthandoff: 02/22/2017

---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Suporte para a janela Autos em um serviço de linguagem herdado
O **Autos** janela exibe expressões como variáveis e parâmetros que estão no escopo quando o programa que está sendo depurado está em pausa (seja devido a um ponto de interrupção ou exceção). As expressões podem incluir variáveis, locais ou globais e os parâmetros que foram alterados no escopo local. O **Autos** janela também pode incluir instâncias de uma classe, estrutura ou algum outro tipo. Tudo o que um avaliador de expressão pode avaliar potencialmente pode ser mostrado no **Autos** janela.  
  
 A estrutura de pacote gerenciado (MPF) não oferece suporte direto para o **Autos** janela. No entanto, se você substituir o <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>método, você pode retornar uma lista de expressões para ser apresentado a **Autos** janela.</xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>  
  
## <a name="implementing-support-for-the-autos-window"></a>Implementação de suporte para a janela Autos  
 Você só precisa fazer para oferecer suporte a **Autos** janela é implementar o <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>método de <xref:Microsoft.VisualStudio.Package.LanguageService>classe.</xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> Sua implementação deve decidir, dado um local no arquivo de origem, expressões devem aparecer no **Autos** janela. O método retorna uma lista de cadeias de caracteres na qual cada sequência representa uma única expressão. Um valor de retorno <xref:Microsoft.VisualStudio.VSConstants.S_OK>indica que a lista contém expressões, enquanto <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>indica que não há nenhuma expressão para mostrar.</xref:Microsoft.VisualStudio.VSConstants.S_FALSE> </xref:Microsoft.VisualStudio.VSConstants.S_OK>  
  
 As expressões reais retornadas são os nomes de variáveis ou parâmetros que aparecem nesse local no código. Esses nomes são passados para o avaliador de expressão para obter valores e tipos que são exibidos no **Autos** janela.  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma implementação do <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>método que obtém uma lista de expressões do <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>método usando o motivo de análise <xref:Microsoft.VisualStudio.Package.ParseReason>.</xref:Microsoft.VisualStudio.Package.ParseReason> </xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> Cada uma das expressões é empacotada como um `TestVsEnumBSTR` que implementa o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR>  
  
 Observe que o `GetAutoExpressionsCount` e `GetAutoExpression` são métodos personalizados no `TestAuthoringSink` do objeto e foram adicionados para dar suporte a esse exemplo. Eles representam uma maneira em quais expressões adicionado ao `TestAuthoringSink` objeto pelo analisador (chamando o <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A>método) podem ser acessados fora o analisador.</xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A>  
  
```c#  
using Microsoft.VisualStudio;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override int GetProximityExpressions(IVsTextBuffer buffer,  
                                                    int line,  
                                                    int col,  
                                                    int cLines,  
                                                    out IVsEnumBSTR ppEnum)  
        {  
            int retval = VSConstants.E_NOTIMPL;  
            ppEnum = null;  
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
                                                              ParseReason.Autos,  
                                                              null);  
                        req.Scope = this.ParseSource(req);  
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;  
  
                        retval = VSConstants.S_FALSE;  
                        int spanCount = sink.GetAutoExpressionsCount();  
                        if (spanCount > 0) {  
                            TestVsEnumBSTR bstrList = new TestVsEnumBSTR();  
                            for (int i = 0; i < spanCount; i++)  
                            {  
                                TextSpan span;  
                                sink.GetAutoExpression(i, out span);  
                                string expression = src.GetText(span.iStartLine,  
                                                                span.iStartIndex,  
                                                                span.iEndLine,  
                                                                span.iEndIndex);  
                                bstrList.AddString(expression);  
                            }  
                            ppEnum = bstrList;  
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
