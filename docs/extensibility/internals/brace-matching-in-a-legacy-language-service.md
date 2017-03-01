---
title: "Chave de correspondência em um serviço de linguagem herdado | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
caps.latest.revision: 27
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
ms.openlocfilehash: e9d6dc14abcfbb06271f48df2b764a23e627a663
ms.lasthandoff: 02/22/2017

---
# <a name="brace-matching-in-a-legacy-language-service"></a>Chave de correspondência em um serviço de linguagem herdado
Correspondência de chaves ajuda o desenvolvedor a acompanhar os elementos de linguagem que precisam ocorrer juntos, como parênteses e as chaves. Quando um desenvolvedor digita uma chave de fechamento, a chave de abertura é realçada.  
  
 Você pode combinar duas ou três elementos ocorrência concomitante, chamados de pares e triplos. Triplos são conjuntos de três elementos de ocorrência concomitante. Por exemplo, no c#, o `foreach` um triplo de formulários de instrução: "`foreach()`","`{`", e "`}`". Todos os três elementos são realçados quando a chave de fechamento é digitada.  
  
 Serviços de linguagem herdada são implementados como parte de um VSPackage, mas a maneira mais recente para implementar recursos de serviço de linguagem é usar extensões MEF. Para obter mais informações sobre a nova maneira de implementar a correspondência de chaves, consulte [passo a passo: exibindo chaves correspondentes](../../extensibility/walkthrough-displaying-matching-braces.md).  
  
> [!NOTE]
>  É recomendável que você comece a usar o novo editor de API assim que possível. Isso irá melhorar o desempenho do seu serviço de linguagem e lhe permitem tirar proveito dos novos recursos do editor.  
  
 O <xref:Microsoft.VisualStudio.Package.AuthoringSink>classe oferece suporte a dois pares e triplica com o <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A>e <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A>métodos.</xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> </xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> </xref:Microsoft.VisualStudio.Package.AuthoringSink>  
  
## <a name="implementation"></a>Implementação  
 O serviço de linguagem precisa identificar todos os elementos correspondentes no idioma e, em seguida, localizar todos os pares correspondentes. Isso geralmente é obtido com a implementação de <xref:Microsoft.VisualStudio.Package.IScanner>para detectar um idioma correspondente e, em seguida, usando o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>método para corresponder os elementos.</xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> </xref:Microsoft.VisualStudio.Package.IScanner>  
  
 O <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>método chama o scanner para indexar a linha e retornar o token antes do cursor.</xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> O mecanismo de varredura indica que foi encontrado um par de elemento de linguagem definindo um valor de gatilho de token de <xref:Microsoft.VisualStudio.Package.TokenTriggers>no token atual.</xref:Microsoft.VisualStudio.Package.TokenTriggers> O <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>chamadas de método de <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A>método que por sua vez chama o <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A>método com o valor do motivo de análise de <xref:Microsoft.VisualStudio.Package.ParseReason>para localizar o elemento de linguagem correspondente.</xref:Microsoft.VisualStudio.Package.ParseReason> </xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> </xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> </xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Quando o elemento de linguagem correspondente for encontrado, os dois elementos são realçados.  
  
 Para obter uma descrição completa de como digitar uma chave dispara o realce de chave, consulte a seção "Operação de análise de exemplo" no tópico [analisador de serviço de linguagem herdado e Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
## <a name="enabling-support-for-brace-matching"></a>Habilitando o suporte para correspondência de chaves  
 O <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>atributo pode definir o `MatchBraces`, `MatchBracesAtCaret`, e `ShowMatchingBrace` parâmetros nomeados que defina as propriedades correspondentes da <xref:Microsoft.VisualStudio.Package.LanguagePreferences>classe</xref:Microsoft.VisualStudio.Package.LanguagePreferences> </xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Propriedades de preferência de idioma também podem ser definidas pelo usuário.  
  
|Entrada de registro|Propriedade|Descrição|  
|--------------------|--------------|-----------------|  
|`MatchBraces`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A></xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Habilita a correspondência de chaves|  
|`MatchBracesAtCaret`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A></xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Habilita a correspondência de colchetes como o cursor move.|  
|`ShowMatchingBrace`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A></xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Realça a chave correspondente.|  
  
## <a name="matching-conditional-statements"></a>Correspondência de instruções condicionais  
 Você pode combinar instruções condicionais, como `if`, `else if`, e `else`, ou `#if`, `#elif`, `#else`, `#endif`, da mesma forma como delimitadores correspondentes. Você pode criar uma subclasse de <xref:Microsoft.VisualStudio.Package.AuthoringSink>classe e fornecem um método que pode adicionar texto abrange, bem como delimitadores para a matriz interna de correspondência de elementos.</xref:Microsoft.VisualStudio.Package.AuthoringSink>  
  
## <a name="setting-the-trigger"></a>Definir o gatilho  
 O exemplo a seguir mostra como detectar a correspondência de parênteses, chaves e colchetes e definindo o disparador para ele no scanner. O <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>método o <xref:Microsoft.VisualStudio.Package.Source>classe detecta o disparador e chama o analisador para encontrar o par correspondente (consulte a seção "Localizando a correspondência" neste tópico).</xref:Microsoft.VisualStudio.Package.Source> </xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Este exemplo é apenas para fins ilustrativos. Ele pressupõe que o scanner contém um método `GetNextToken` que identifica e retorna os tokens de uma linha de texto.  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private const string braces = "()[]{}";  
        private Lexer lex;  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false;  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char firstChar = token[0];  
                if (Char.IsPunctuation(firstChar) && token.Length > 0)  
                {  
                    if (braces.IndexOf(firstChar) != -1)  
                    {  
                        tokenInfo.Trigger = TokenTriggers.MatchBraces;  
                    }  
                }  
            }  
            return foundToken;  
        }  
```  
  
## <a name="matching-the-braces"></a>Correspondência de chaves  
 Aqui está um exemplo simplificado para correspondência [], {} elementos de linguagem e () e adicionar seus abrangentes para o <xref:Microsoft.VisualStudio.Package.AuthoringSink>objeto.</xref:Microsoft.VisualStudio.Package.AuthoringSink> Essa abordagem não é uma abordagem recomendada para análise de código fonte. é apenas para fins ilustrativos.  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class Parser  
    {  
         private IList<TextSpan[]> m_braces;  
         public IList<TextSpan[]> Braces  
         {  
             get { return m_braces; }  
         }  
         private void AddMatchingBraces(TextSpan braceSpan1, TextSpan braceSpan2)  
         {  
             if IsMatch(braceSpan1, braceSpan2)  
                 m_braces.Add(new TextSpan[] { braceSpan1, braceSpan2 });  
         }  
  
         private bool IsMatch(TextSpan braceSpan1, TextSpan braceSpan2)  
         {  
             //definition for matching here  
          }  
    }  
  
    public class TestLanguageService : LanguageService  
    {  
         Parser parser = new Parser();  
         Source source = (Source) this.GetSource(req.FileName);  
  
         private AuthoringScope ParseSource(ParseRequest req)  
         {  
             if (req.Sink.BraceMatching)  
             {  
                 if (req.Reason==ParseReason.MatchBraces)  
                 {  
                     foreach (TextSpan[] brace in parser.Braces)  
                     {  
                         req.Sink.MatchPair(brace[0], brace[1], 1);  
                     }  
                 }  
             }  
             return new TestAuthoringScope();  
         }  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Recursos de serviço de linguagem herdada](../../extensibility/internals/legacy-language-service-features1.md)   
 [Scanner e Parser de serviço de linguagem herdada](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
