---
title: "Informações de parâmetro um Service2 de idioma herdado | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
caps.latest.revision: 23
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
ms.openlocfilehash: 4ea00c4028ab4c148a421e81b2e7500afe9c40ec
ms.lasthandoff: 02/22/2017

---
# <a name="parameter-info-in-a-legacy-language-service"></a>Informações de parâmetro em um serviço de linguagem herdado
Informações de parâmetro IntelliSense é uma dica de ferramenta que exibe a assinatura de um método quando o usuário digita a lista de parâmetros iniciar caractere (normalmente um parêntese de abertura) para a lista de parâmetros de método. Como cada parâmetro é inserido e o separador de parâmetro (geralmente uma vírgula) for digitado, a dica de ferramenta é atualizada para mostrar o próximo parâmetro em negrito.  
  
 As classes do framework (MPF) pacote gerenciado fornecem suporte para gerenciar a dica de ferramenta de informações do parâmetro. O analisador deve detectar parâmetro Iniciar, parâmetro a seguir, e caracteres de final de parâmetro e ele devem fornecer uma lista de assinaturas de método e seus parâmetros associados.  
  
 Serviços de linguagem herdada são implementados como parte de um VSPackage, mas a maneira mais recente para implementar recursos de serviço de linguagem é usar extensões MEF. Para obter mais informações, consulte [estendendo o Editor e serviços de linguagem](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  É recomendável que você comece a usar o novo editor de API assim que possível. Isso irá melhorar o desempenho do seu serviço de linguagem e lhe permitem tirar proveito dos novos recursos do editor.  
  
## <a name="implementation"></a>Implementação  
 O analisador deve definir o valor de disparador <xref:Microsoft.VisualStudio.Package.TokenTriggers>é definido quando ele encontra um caractere de início de lista de parâmetro (geralmente um parêntese de abertura).</xref:Microsoft.VisualStudio.Package.TokenTriggers> Ele deve ser definido um <xref:Microsoft.VisualStudio.Package.TokenTriggers>disparar quando ele encontra um separador de parâmetro (geralmente uma vírgula).</xref:Microsoft.VisualStudio.Package.TokenTriggers> Isso faz com que uma dica de ferramenta informações de parâmetro seja atualizado e mostrar o próximo parâmetro em negrito. O analisador deve definir o valor de disparador <xref:Microsoft.VisualStudio.Package.TokenTriggers>quando se encontra o caractere de final de lista de parâmetro (geralmente um parêntese de fechamento).</xref:Microsoft.VisualStudio.Package.TokenTriggers>  
  
 O <xref:Microsoft.VisualStudio.Package.TokenTriggers>valor de gatilho inicia uma chamada para o <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A>método, que por sua vez, chama o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>Analisador de método com uma razão de análise de <xref:Microsoft.VisualStudio.Package.ParseReason>.</xref:Microsoft.VisualStudio.Package.ParseReason> </xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> </xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> </xref:Microsoft.VisualStudio.Package.TokenTriggers> Se o analisador determina que o identificador antes de começar a lista de parâmetros de caractere é um nome de método reconhecido, ele retorna uma lista de assinaturas de método em correspondentes a <xref:Microsoft.VisualStudio.Package.AuthoringScope>objeto.</xref:Microsoft.VisualStudio.Package.AuthoringScope> Se forem encontradas quaisquer assinaturas de método, a dica de ferramenta de informações do parâmetro é exibida com a primeira assinatura na lista. Essa dica de ferramenta é atualizada conforme mais a assinatura é digitado. Quando o caractere de final de lista de parâmetro for digitado, a dica de ferramenta de informações do parâmetro é removida do modo de exibição.  
  
> [!NOTE]
>  Para garantir que a dica de ferramenta de informações do parâmetro está formatada corretamente, você deve substituir as propriedades na <xref:Microsoft.VisualStudio.Package.Methods>classe para fornecer os caracteres apropriados.</xref:Microsoft.VisualStudio.Package.Methods> A base <xref:Microsoft.VisualStudio.Package.Methods>classe pressupõe um c#-a assinatura do método estilo.</xref:Microsoft.VisualStudio.Package.Methods> Consulte o <xref:Microsoft.VisualStudio.Package.Methods>classe para obter detalhes sobre como isso pode ser feito.</xref:Microsoft.VisualStudio.Package.Methods>  
  
## <a name="enabling-support-for-the-parameter-info"></a>Habilitando o suporte para obter as informações de parâmetro  
 Para oferecer suporte a dica de ferramenta informações de parâmetro, você deve definir o `ShowCompletion` chamado parâmetro do <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>para `true`.</xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> O serviço de linguagem lê o valor da entrada do registro do <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A>propriedade.</xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A>  
  
 Além disso, o <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A>deve ser definida como `true` para a dica de ferramenta de informações do parâmetro a ser mostrado.</xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A>  
  
### <a name="example"></a>Exemplo  
 Aqui está um exemplo simplificado de detectar os caracteres da lista de parâmetros e definir os gatilhos apropriados. Este exemplo é apenas para fins ilustrativos. Ele pressupõe que o scanner contém um método `GetNextToken` que identifica e retorna os tokens de uma linha de texto. O exemplo de código simplesmente define os disparadores sempre que ele vê o tipo certo de caractere.  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private Lexer lex;  
        private const char parameterListStartChar = '(';  
        private const char parameterListEndChar   = ')';  
        private const char parameterNextChar      = ',';  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char c = token[0];  
                if (Char.IsPunctuation(c))  
                {  
                    tokenInfo.Type = TokenType.Operator;  
                    tokenInfo.Color = TokenColor.Keyword;  
                    tokenInfo.EndIndex = index;  
  
                    if (c == parameterListStartChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterStart;  
                    }  
                    else if (c == parameterListNextChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterNext;  
                    else if (c == parameterListEndChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterEnd;  
                    }  
                }  
            return foundToken;  
        }  
    }  
}  
```  
  
## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Suporte a dica de ferramenta de informações do parâmetro no analisador  
 O <xref:Microsoft.VisualStudio.Package.Source>classe faz algumas suposições sobre o conteúdo de <xref:Microsoft.VisualStudio.Package.AuthoringScope>e <xref:Microsoft.VisualStudio.Package.AuthoringSink>classes quando a dica de ferramenta de informações do parâmetro é exibida e atualizada.</xref:Microsoft.VisualStudio.Package.AuthoringSink> </xref:Microsoft.VisualStudio.Package.AuthoringScope> </xref:Microsoft.VisualStudio.Package.Source>  
  
-   O analisador recebe <xref:Microsoft.VisualStudio.Package.ParseReason>quando o caractere de início de lista de parâmetro for digitado.</xref:Microsoft.VisualStudio.Package.ParseReason>  
  
-   Localização fornecida <xref:Microsoft.VisualStudio.Package.ParseRequest>objeto é imediatamente após a lista de parâmetros iniciar caractere.</xref:Microsoft.VisualStudio.Package.ParseRequest> O analisador deve coletar as assinaturas de todas as declarações de método disponíveis em posição e armazená-los em uma lista na sua versão do <xref:Microsoft.VisualStudio.Package.AuthoringScope>objeto.</xref:Microsoft.VisualStudio.Package.AuthoringScope> Essa lista inclui o nome do método, método tipo (ou no tipo de retorno) e uma lista de possíveis parâmetros. Essa lista é pesquisada posteriormente para a assinatura de método ou assinaturas para exibir a dica de ferramenta de informações do parâmetro.  
  
 O analisador, em seguida, deve analisar a linha especificada pelo <xref:Microsoft.VisualStudio.Package.ParseRequest>objeto para coletar o nome do método que está sendo inserido, bem como a distância ao longo do usuário está na digitação parâmetros.</xref:Microsoft.VisualStudio.Package.ParseRequest> Isso é feito transmitindo o nome do método para o <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A>método no <xref:Microsoft.VisualStudio.Package.AuthoringSink>objeto e, em seguida, chamar o <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>método quando a lista de parâmetros iniciar caractere é analisado, chamar o <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>método quando o parâmetro lista próximo caractere é analisado e, finalmente, chamar o <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>método quando o caractere de final de lista de parâmetro é analisado.</xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> </xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> </xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> </xref:Microsoft.VisualStudio.Package.AuthoringSink> </xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> Os resultados dessas chamadas de método são usados pelo <xref:Microsoft.VisualStudio.Package.Source>classe para atualizar o parâmetro Info tooltip adequadamente.</xref:Microsoft.VisualStudio.Package.Source>  
  
### <a name="example"></a>Exemplo  
 Aqui está uma linha de texto que o usuário pode inserir. Os números abaixo da linha indicam qual etapa é executada pelo analisador nessa posição na linha (supondo que a análise esquerda move para a direita). O pressuposto é que tudo antes da linha já foi analisado para assinaturas de método, incluindo a assinatura do método "testfunc".  
  
```  
testfunc("a string",3);  
     ^^          ^ ^  
     12          3 4  
```  
  
 As etapas que leva o analisador são descritas abaixo:  
  
1.  O analisador chama <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A>com o texto "testfunc".</xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A>  
  
2.  As chamadas de analisador <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>.</xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>  
  
3.  As chamadas de analisador <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>.</xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>  
  
4.  As chamadas de analisador <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>.</xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>
