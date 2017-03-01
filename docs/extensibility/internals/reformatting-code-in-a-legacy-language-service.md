---
title: "Reformatar o código em um serviço de linguagem herdado | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
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
ms.sourcegitcommit: 08d537f003279283509913d5f3d6aaa1bb1c4600
ms.openlocfilehash: d78fb976b3500a657d080634c6a041c218c3f1a1
ms.lasthandoff: 02/22/2017

---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Reformatar o código em um serviço de linguagem herdado

Em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] código-fonte pode ser reformatado Normalizando o uso de recuos e espaço em branco. Isso pode incluir inserir ou remover espaços ou tabulações no início de cada linha, adicionando novas linhas entre as linhas ou substituindo espaços por guias com espaços ou tabulações.  
  
>**Observação:** inserindo ou excluindo os caracteres pode afetar marcadores, como pontos de interrupção e indicadores mas adicionando ou removendo espaços ou tabulações não afeta marcadores.  
  
Os usuários podem iniciar uma operação de reformatação selecionando **seleção de formato** ou **documento** do **avançado** menu o **editar** menu. Uma operação de reformatação também pode ser acionada quando um determinado caractere ou um trecho de código é inserido. Por exemplo, quando você digita uma chave de fechamento em c#, tudo entre a correspondente chave de abertura e o colchete de fechamento é recuado automaticamente para o nível adequado.
  
Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] envia o **seleção de formato** ou **documento** comando para o serviço de linguagem, a <xref:Microsoft.VisualStudio.Package.ViewFilter>classe chama o <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>método de <xref:Microsoft.VisualStudio.Package.Source>classe.</xref:Microsoft.VisualStudio.Package.Source> </xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> </xref:Microsoft.VisualStudio.Package.ViewFilter> Para oferecer suporte a formatação que você deve substituir o <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>método e forneça sua própria formatação de código.</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>  
  
## <a name="enabling-support-for-reformatting"></a>Habilitando o suporte para reformatação  

Para oferecer suporte a formatação, o `EnableFormatSelection` parâmetro o <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>deve ser definido como `true` quando você registra o VSPackage.</xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Isso define o <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A>propriedade `true`.</xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> O <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A>método retorna o valor dessa propriedade.</xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> Se ele retornar true, a <xref:Microsoft.VisualStudio.Package.ViewFilter>classe chama <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>.</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> </xref:Microsoft.VisualStudio.Package.ViewFilter>  
  
## <a name="implementing-reformatting"></a>Implementando a reformatação

Para implementar a reformatação, você deve derivar uma classe a partir de <xref:Microsoft.VisualStudio.Package.Source>classe e substituir o <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>método.</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> </xref:Microsoft.VisualStudio.Package.Source> O <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>objeto descreve o intervalo para o formato e o <xref:Microsoft.VisualStudio.Package.EditArray>objeto contém as edições feitas a span.</xref:Microsoft.VisualStudio.Package.EditArray> </xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> Observe que esse período pode ser o documento inteiro. No entanto, como há provavelmente várias alterações feitas para o período, todas as alterações devem ser reversíveis em uma única ação. Para fazer isso, envolver todas as alterações em uma <xref:Microsoft.VisualStudio.Package.CompoundAction>objeto (consulte a seção "Usando a classe CompoundAction" neste tópico).</xref:Microsoft.VisualStudio.Package.CompoundAction>

### <a name="example"></a>Exemplo  

O exemplo a seguir garante que haja um único espaço após cada vírgula na seleção, a menos que a vírgula é seguida por uma tabulação ou no final da linha. Espaços à direita depois da última vírgula em uma linha são excluídos. Consulte a seção "Usando a classe CompoundAction" deste tópico para ver como esse método é chamado a partir de <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>método.</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>  

```csharp 
using Microsoft.VisualStudio.Package;  
using Microsoft VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        private void DoFormatting(EditArray mgr, TextSpan span)  
        {  
            // Make sure there is one space after every comma unless followed  
            // by a tab or comma is at end of line.  
            IVsTextLines pBuffer = GetTextLines();  
            if (pBuffer != null)  
            {  
                int    startIndex = span.iStartIndex;  
                int    endIndex   = 0;  
                string line       = "";  
                // Loop over all lines in span  
                for (int i = span.iStartLine; i <= span.iEndLine; i++)  
                {  
                    if (i < span.iEndLine)  
                    {  
                        pBuffer.GetLengthOfLine(i, out endIndex);  
                    }  
                    else  
                    {  
                        endIndex = span.iEndIndex;  
                    }  
                    pBuffer.GetLineText(i, startIndex, i, endIndex, out line);  
  
                    if (line.Length > 0)  
                    {  
                        int index = 0;  
                        // Loop over all commas in line  
                        while ((index = line.IndexOf(',', index)) != -1)  
                        {  
                            int spaceIndex = index + 1;  
                            // Determine how many spaces after comma  
                            while (spaceIndex < line.Length && line[spaceIndex] == ' ')  
                            {  
                                ++spaceIndex;  
                            }  
  
                            int      spaceCount      = spaceIndex - (index + 1);  
                            string   replacementText = " ";  
                            bool     fDoEdit         = true;  
                            TextSpan editTextSpan    = new TextSpan();  
  
                            editTextSpan.iStartLine  = i;  
                            editTextSpan.iEndLine    = i;  
                            editTextSpan.iStartIndex = index + 1;  
  
                            if (spaceIndex == line.Length)  
                            {  
                                if (spaceCount > 0)  
                                {  
                                    // Delete spaces after a comma at end of line  
                                    editTextSpan.iEndIndex = spaceIndex;  
                                    replacementText = "";  
                                }  
                                else  
                                {  
                                    // Otherwise, do not add spaces if comma is  
                                    // at end of line.  
                                    fDoEdit = false;  
                                }  
                            }  
                            else if (spaceCount == 0)  
                            {  
                                if (spaceIndex < line.Length && line[spaceIndex] == '\t')  
                                {  
                                    // Do not insert space if a tab follows  
                                    // a comma.  
                                    fDoEdit = false;  
                                }  
                                else  
                                {  
                                    // No space after comma so add a space.  
                                    editTextSpan.iEndIndex = index + 1;  
                                }  
                            }  
                            else if (spaceCount > 1)  
                            {  
                                // More than one space after comma, replace  
                                // with a single space.  
                                editTextSpan.iEndIndex = spaceIndex;  
                            }  
                            else  
                            {  
                                // Single space after a comma and not at end  
                                // of the line, leave it alone.  
                                fDoEdit = false;  
                            }  
                            if (fDoEdit)  
                            {  
                                // Add edit operation  
                                mgr.Add(new EditSpan(editTextSpan, replacementText));  
                            }  
                            index = spaceIndex;  
                        }  
                    }  
                    startIndex = 0; // All subsequent lines start at 0  
                }  
                // Apply all edits  
                mgr.ApplyEdits();  
            }  
        }  
    }  
}  
```  
  
## <a name="using-the-compoundaction-class"></a>Usando a classe CompoundAction  
 
Todos os a reformatação feita em uma seção de código deve ser reversível em uma única ação. Isso pode ser feito usando uma <xref:Microsoft.VisualStudio.Package.CompoundAction>classe.</xref:Microsoft.VisualStudio.Package.CompoundAction> Essa classe encapsula um conjunto de operações de edição no buffer de texto em uma operação única edição.  
  
### <a name="example"></a>Exemplo

Aqui está um exemplo de como usar a <xref:Microsoft.VisualStudio.Package.CompoundAction>classe.</xref:Microsoft.VisualStudio.Package.CompoundAction> Consulte o exemplo na seção "Implementando suporte para formatação" neste tópico para obter um exemplo de `DoFormatting` método.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        public override void ReformatSpan(EditArray mgr, TextSpan span)  
        {  
            string description = "Reformat code";  
            CompoundAction ca = new CompoundAction(this, description);  
            using (ca)  
            {  
                ca.FlushEditActions();      // Flush any pending edits  
                DoFormatting(mgr, span);    // Format the span  
            }  
        }  
    }  
}  
```  

## <a name="see-also"></a>Consulte também

[Recursos de serviço de linguagem herdada](legacy-language-service-features1.md)
