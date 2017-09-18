---
title: "Estrutura de tópicos em um serviço de linguagem herdado | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
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
ms.openlocfilehash: 15eb40ed290d1f4389d3c9876c965a7070993cec
ms.lasthandoff: 02/22/2017

---
# <a name="outlining-in-a-legacy-language-service"></a>Estrutura de tópicos em um serviço de linguagem herdado
Estrutura de tópicos torna possível recolher um programa complexo em uma visão geral ou a estrutura de tópicos. Por exemplo, no c# todos os métodos podem ser recolhidos em uma única linha, mostrando apenas a assinatura do método. Além disso, as estruturas e classes podem ser recolhidos para mostrar apenas os nomes de estruturas e classes. Lógica complexa em um único método, pode ser recolhida para mostrar o fluxo geral mostrando somente a primeira linha das instruções como `foreach`, `if`, e `while`.  
  
 Serviços de linguagem herdada são implementados como parte de um VSPackage, mas a maneira mais recente para implementar recursos de serviço de linguagem é usar extensões MEF. Para obter mais informações, consulte [passo a passo: estrutura de tópicos](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  É recomendável que você comece a usar o novo editor de API assim que possível. Isso irá melhorar o desempenho do seu serviço de linguagem e lhe permitem tirar proveito dos novos recursos do editor.  
  
## <a name="enabling-support-for-outlining"></a>Habilitando o suporte para a estrutura de tópicos  
 O `AutoOutlining` entrada do registro é definida como 1 para ativar a estrutura de tópicos automática. Estrutura de tópicos automática configura uma análise da fonte inteira quando um arquivo for carregado ou alterado para identificar regiões ocultas e mostrar os glifos de estrutura de tópicos. Estrutura de tópicos também pode ser controlada manualmente pelo usuário.  
  
 O valor de `AutoOutlining` entrada do registro pode ser obtida por meio da <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A>propriedade de <xref:Microsoft.VisualStudio.Package.LanguagePreferences>classe.</xref:Microsoft.VisualStudio.Package.LanguagePreferences> </xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> O `AutoOutlining` entrada do registro pode ser inicializada com um parâmetro nomeado para o <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>atributo (consulte [registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service1.md) para obter detalhes).</xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>  
  
## <a name="the-hidden-region"></a>A região ocultada  
 Para fornecer a estrutura de tópicos, seu serviço de linguagem deve oferecer suporte a regiões ocultas. Esses são os intervalos de texto que pode ser expandido ou recolhido. Regiões ocultas podem ser delimitados por símbolos de linguagem padrão, como chaves, ou símbolos personalizados. Por exemplo, o c# tem um `#region` / `#endregion` par que delimita uma região oculta.  
  
 Regiões ocultas são gerenciados por um Gerenciador de região oculta, que é exposto como o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>  
  
 Estrutura de tópicos usa regiões ocultas o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion>da interface e contém o período de região oculta, o estado de visibilidade atual e a faixa a ser mostrado quando o período é recolhido.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion>  
  
 O analisador de serviço de linguagem usa o <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A>para adicionar uma nova região oculta com o comportamento padrão para regiões ocultas, enquanto o <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A>método permite que você personalize a aparência e comportamento do contorno.</xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> </xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> Depois de regiões ocultas são fornecidos para a sessão de região oculta, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gerencia as regiões ocultas para o serviço de linguagem.  
  
 Se você precisar determinar quando a sessão de região oculta é destruída, uma região oculta for alterada, ou você precisa certificar-se de que uma determinada região oculta estiver visível; Você deve derivar uma classe a partir de <xref:Microsoft.VisualStudio.Package.Source>classe e substituir os métodos apropriados, <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>, e <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>, respectivamente.</xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A> </xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A> </xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A> </xref:Microsoft.VisualStudio.Package.Source>  
  
### <a name="example"></a>Exemplo  
 Aqui está um exemplo simplificado da criação de regiões ocultas para todos os pares de chaves. Supõe-se que a linguagem fornece correspondência de chaves e as chaves a ser correspondido incluem pelo menos as chaves ({e}). Essa abordagem é apenas para fins ilustrativos. Uma implementação completa teria um tratamento completo de casos no <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>.</xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Este exemplo também mostra como definir o <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A>preferência para `true` temporariamente.</xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> Uma alternativa é especificar o `AutoOutlining` chamado parâmetro no `ProvideLanguageServiceAttribute` atributo em seu pacote de idioma.  
  
 Este exemplo pressupõe c# regras para comentários, cadeias de caracteres e literais.  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
  
    public class MyLanguageService : LanguageService  
    {  
        private LanguagePreferences m_preferences;  
  
        public override LanguagePreferences  GetLanguagePreferences()  
        {  
            if (m_preferences == null)  
            {  
                m_preferences = new LanguagePreferences(this.Site,  
                                                        typeof(MyLanguageService).GUID,  
                                                        Name);  
                m_preferences.Init();  
                // Temporarily enabled auto-outlining  
                m_preferences.AutoOutlining = true;  
            }  
            return m_preferences;  
        }  
  
        public override AuthoringScope  ParseSource(ParseRequest req)  
        {  
            Source source = (Source) this.GetSource(req.FileName);  
            switch (req.Reason)  
            {  
               case ParseReason.HighlightBraces:  
               case ParseReason.MatchBraces:  
               case ParseReason.MemberSelectAndHighlightBraces:  
                  if (source.Braces != null)  
                  {  
                      foreach (TextSpan[] brace in source.Braces)  
                      {  
                         if (brace.Length == 2)  
                         {  
                             if (req.Sink.HiddenRegions == true   
                                   && source.GetText(brace[0]).Equals("{")   
                                   && source.GetText(brace[1]).Equals("}"))  
                             {  
                                //construct a TextSpan of everything between the braces  
                                TextSpan hideSpan = new TextSpan();  
                                hideSpan.iStartIndex = brace[0].iStartIndex;  
                                hideSpan.iStartLine = brace[0].iStartLine;  
                                hideSpan.iEndIndex = brace[1].iEndIndex;  
                                hideSpan.iEndLine = brace[1].iEndLine;  
                                req.Sink.ProcessHiddenRegions = true;  
                                req.Sink.AddHiddenRegion(hideSpan);  
                             }  
                             req.Sink.MatchPair(brace[0], brace[1], 1);  
                         }  
                         else if (brace.Length >= 3)  
                             req.Sink.MatchTriple(brace[0], brace[1], brace[2], 1);  
                  }  
        }  
                   break;  
               default:  
                   break;  
      }  
            // Must always return a valid AuthoringScope object.  
            return new MyAuthoringScope();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Recursos de serviço de linguagem herdada](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service1.md)
