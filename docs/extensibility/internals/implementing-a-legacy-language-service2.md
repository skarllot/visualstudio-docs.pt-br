---
title: Implementando um Service2 de idioma herdado | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
caps.latest.revision: 26
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
ms.openlocfilehash: 40df713356e33feecd9caf0372d569f88a40af6a
ms.lasthandoff: 02/22/2017

---
# <a name="implementing-a-legacy-language-service"></a>Implementando um serviço de linguagem herdado
Para implementar um serviço de idioma usando a estrutura de pacote gerenciado (MPF), você deve derivar uma classe a partir de <xref:Microsoft.VisualStudio.Package.LanguageService>classe e implementar as propriedades e métodos abstratos seguintes:</xref:Microsoft.VisualStudio.Package.LanguageService>  
  
-   O <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>método</xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>  
  
-   O <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>método</xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>  
  
-   O <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>método</xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>  
  
-   A <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>propriedade</xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>  
  
 Consulte as seções apropriadas abaixo para obter detalhes sobre como implementar esses métodos e propriedades.  
  
 Para oferecer suporte a recursos adicionais, o serviço de linguagem talvez precise derivar uma classe de uma das classes de serviço de linguagem MPF; Por exemplo, para oferecer suporte a comandos de menu adicionais, você deve derivar uma classe a partir de <xref:Microsoft.VisualStudio.Package.ViewFilter>classe e substituir vários os métodos de manipulação de comandos (consulte <xref:Microsoft.VisualStudio.Package.ViewFilter>para obter detalhes).</xref:Microsoft.VisualStudio.Package.ViewFilter> </xref:Microsoft.VisualStudio.Package.ViewFilter> A <xref:Microsoft.VisualStudio.Package.LanguageService>classe fornece vários métodos que são chamados para criar novas instâncias de várias classes e substituir o método apropriado de criação para fornecer uma instância de sua classe.</xref:Microsoft.VisualStudio.Package.LanguageService> Por exemplo, você precisa substituir o <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>método na <xref:Microsoft.VisualStudio.Package.LanguageService>classe para retornar uma instância de sua própria <xref:Microsoft.VisualStudio.Package.ViewFilter>classe.</xref:Microsoft.VisualStudio.Package.ViewFilter> </xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> Consulte a seção "Criando Classes personalizadas" para obter mais detalhes.  
  
 O serviço de linguagem também pode fornecer seus próprios ícones, que são usados em vários locais. Por exemplo, quando uma lista de conclusão do IntelliSense é exibida, cada item na lista pode ter um ícone associado a ele, marcando o item como um método de classe, namespace, propriedade, ou o que for necessário para seu idioma. Esses ícones são usados em todas as listas do IntelliSense, o **barra de navegação**e no **Error List** janela tarefas. Consulte a seção "Imagens do serviço de linguagem" abaixo para obter detalhes.  
  
## <a name="getlanguagepreferences-method"></a>Método GetLanguagePreferences  
 O <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>método sempre retorna a mesma instância de uma <xref:Microsoft.VisualStudio.Package.LanguagePreferences>classe.</xref:Microsoft.VisualStudio.Package.LanguagePreferences> </xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> Você pode usar a base de <xref:Microsoft.VisualStudio.Package.LanguagePreferences>classe se você não precisar de qualquer preferências adicionais para seu serviço de linguagem.</xref:Microsoft.VisualStudio.Package.LanguagePreferences> As classes de serviço de linguagem MPF pressupõem a presença de pelo menos a base <xref:Microsoft.VisualStudio.Package.LanguagePreferences>classe.</xref:Microsoft.VisualStudio.Package.LanguagePreferences>  
  
### <a name="example"></a>Exemplo  
 Este exemplo mostra uma implementação típica do <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>método.</xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> Este exemplo usa a <xref:Microsoft.VisualStudio.Package.LanguagePreferences>classe</xref:Microsoft.VisualStudio.Package.LanguagePreferences> de base  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private LanguagePreferences m_preferences;  
  
        public override LanguagePreferences GetLanguagePreferences()  
        {  
            if (m_preferences == null)  
            {  
                m_preferences = new LanguagePreferences(this.Site,  
                                                        typeof(TestLanguageService).GUID,  
                                                        this.Name );  
                m_preferences.Init();  
            }  
            return m_preferences;  
        }  
    }  
}  
```  
  
## <a name="getscanner-method"></a>Método GetScanner  
 Esse método retorna uma instância de um <xref:Microsoft.VisualStudio.Package.IScanner>objeto que implementa um analisador orientado por linhas ou scanner usado para a obtenção de tokens e seus tipos e disparadores.</xref:Microsoft.VisualStudio.Package.IScanner> Este scanner é usado na <xref:Microsoft.VisualStudio.Package.Colorizer>classe para colorir, embora o scanner também pode ser usado para obter tipos de tokens e gatilhos, como um prelúdio para uma operação de análise mais complexa.</xref:Microsoft.VisualStudio.Package.Colorizer> Você deve fornecer a classe que implementa o <xref:Microsoft.VisualStudio.Package.IScanner>interface e você deve implementar todos os métodos de <xref:Microsoft.VisualStudio.Package.IScanner>interface.</xref:Microsoft.VisualStudio.Package.IScanner> </xref:Microsoft.VisualStudio.Package.IScanner>  
  
### <a name="example"></a>Exemplo  
 Este exemplo mostra uma implementação típica do <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>método.</xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> O `TestScanner` classe implementa o <xref:Microsoft.VisualStudio.Package.IScanner>interface (não mostrado).</xref:Microsoft.VisualStudio.Package.IScanner>  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private TestScanner m_scanner;  
  
        public override IScanner GetScanner(IVsTextLines buffer)  
        {  
            if (m_scanner == null)  
            {  
                m_scanner = new TestScanner(buffer);  
            }  
            return m_scanner;  
        }  
    }  
}  
    internal class TestScanner : IScanner  
    {  
        private IVsTextBuffer m_buffer;  
        string m_source;  
  
        public TestScanner(IVsTextBuffer buffer)  
        {  
            m_buffer = buffer;  
        }  
  
        bool IScanner.ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo, ref int state)  
        {  
            tokenInfo.Type = TokenType.Unknown;  
            tokenInfo.Color = TokenColor.Text;  
            return true;  
        }  
  
        void IScanner.SetSource(string source, int offset)  
        {  
            m_source = source.Substring(offset);  
        }  
    }  
  
```  
  
## <a name="parsesource-method"></a>Método ParseSource  
 Analisa o arquivo de origem com base em uma série de motivos diferentes. Esse método recebe um <xref:Microsoft.VisualStudio.Package.ParseRequest>objeto que descreve o que é esperado de uma determinada operação de análise.</xref:Microsoft.VisualStudio.Package.ParseRequest> O <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>método invoca um analisador mais complexo que determina a funcionalidade de token e escopo.</xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> O <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>método é usado no suporte para operações do IntelliSense, bem como a correspondência de colchetes.</xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Mesmo se você não dão suporte a essas operações avançadas, você ainda deverá retornar válido <xref:Microsoft.VisualStudio.Package.AuthoringScope>objeto e que precisa criar uma classe que implementa o <xref:Microsoft.VisualStudio.Package.AuthoringScope>da interface e implementar todos os métodos nessa interface.</xref:Microsoft.VisualStudio.Package.AuthoringScope> </xref:Microsoft.VisualStudio.Package.AuthoringScope> Você pode retornar valores nulos de todos os métodos, mas o <xref:Microsoft.VisualStudio.Package.AuthoringScope>objeto propriamente dito não deve ser um valor nulo.</xref:Microsoft.VisualStudio.Package.AuthoringScope>  
  
### <a name="example"></a>Exemplo  
 Este exemplo mostra uma implementação mínima do <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>método e o <xref:Microsoft.VisualStudio.Package.AuthoringScope>classe, suficiente para permitir que o serviço de linguagem ser compilado e funcionar sem suporte, na verdade, qualquer um dos recursos mais avançados.</xref:Microsoft.VisualStudio.Package.AuthoringScope> </xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override AuthoringScope ParseSource(ParseRequest req)  
        {  
            return new TestAuthoringScope();  
        }  
    }  
  
    internal class TestAuthoringScope : AuthoringScope  
    {  
        public override string GetDataTipText(int line, int col, out TextSpan span)  
        {  
            span = new TextSpan();  
            return null;  
        }  
  
        public override Declarations GetDeclarations(IVsTextView view,  
                                                     int line,  
                                                     int col,  
                                                     TokenInfo info,  
                                                     ParseReason reason)  
        {  
            return null;  
        }  
  
        public override string Goto(VSConstants.VSStd97CmdID cmd, IVsTextView textView, int line, int col, out TextSpan span)  
        {  
            span = new TextSpan();  
            return null;  
        }  
  
        public override Methods GetMethods(int line, int col, string name)  
        {  
            return null;  
        }  
}  
```  
  
## <a name="name-property"></a>Propriedade Name  
 Essa propriedade retorna o nome do serviço de idioma. Isso deve ser o mesmo nome fornecido quando o serviço de linguagem foi registrado. Esse nome é usado em vários lugares, é o mais proeminente de <xref:Microsoft.VisualStudio.Package.LanguagePreferences>classe onde o nome é usado para acessar o registro.</xref:Microsoft.VisualStudio.Package.LanguagePreferences> O nome retornado por essa propriedade não deve ser localizado como ele é usado no registro para a entrada do registro e nomes de chave.  
  
### <a name="example"></a>Exemplo  
 Este exemplo mostra uma possível implementação de <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>propriedade.</xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> Observe que o nome aqui é embutido em código: o nome real deve ser obtido de um arquivo de recurso para que possa ser usado no registro de um serviço de linguagem (consulte [registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service1.md)).  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override string Name  
        {  
            get { return "Test Language"; }  
        }  
    }  
}  
```  
  
## <a name="instantiating-custom-classes"></a>Criando Classes personalizadas  
 Os seguintes métodos nas classes especificados podem ser substituídos para fornecer instâncias de suas próprias versões de cada classe.  
  
### <a name="in-the-languageservice-class"></a>Na classe LanguageService  
  
|Método|Classe retornados|Descrição|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A></xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager></xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Para oferecer suporte a adições personalizadas para a exibição de texto.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A></xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties></xref:Microsoft.VisualStudio.Package.DocumentProperties>|Para oferecer suporte a propriedades de documento personalizadas.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A></xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars></xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Para oferecer suporte a **barra de navegação**.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A></xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction></xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Para oferecer suporte a funções em modelos de trecho de código.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A></xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider></xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Para oferecer suporte a trechos de código (esse método normalmente não é substituído).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A></xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest></xref:Microsoft.VisualStudio.Package.ParseRequest>|Para oferecer suporte a personalização do <xref:Microsoft.VisualStudio.Package.ParseRequest>estrutura (esse método normalmente não é substituído).</xref:Microsoft.VisualStudio.Package.ParseRequest>|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A></xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source></xref:Microsoft.VisualStudio.Package.Source>|Para oferecer suporte a formatação código-fonte, especificando os caracteres de comentário e personalização de assinaturas de método.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A></xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter></xref:Microsoft.VisualStudio.Package.ViewFilter>|Para oferecer suporte a comandos de menu adicionais.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A></xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer></xref:Microsoft.VisualStudio.Package.Colorizer>|Para oferecer suporte a realce de sintaxe (esse método normalmente não é substituído).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A></xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences></xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Para dar suporte ao acesso às preferências de idioma. Esse método deve ser implementado, mas pode retornar uma instância da classe base.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A></xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner></xref:Microsoft.VisualStudio.Package.IScanner>|Para fornecer um analisador usado para identificar os tipos de tokens em uma linha. Este método deve ser implementado e <xref:Microsoft.VisualStudio.Package.IScanner>deve ser derivado de.</xref:Microsoft.VisualStudio.Package.IScanner>|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A></xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope></xref:Microsoft.VisualStudio.Package.AuthoringScope>|Para fornecer um analisador usado para identificar a funcionalidade e escopo em todo um arquivo de origem inteiro. Esse método deve ser implementado e deve retornar uma instância de sua versão da <xref:Microsoft.VisualStudio.Package.AuthoringScope>classe.</xref:Microsoft.VisualStudio.Package.AuthoringScope> Se tudo o que você deseja oferecer suporte é realce de sintaxe (que exige o <xref:Microsoft.VisualStudio.Package.IScanner>Analisador retornado do <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>método), pode fazer nada nesse método diferente de retorno de uma versão do <xref:Microsoft.VisualStudio.Package.AuthoringScope>classe cujos todos os métodos retornam valores nulos.</xref:Microsoft.VisualStudio.Package.AuthoringScope> </xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> </xref:Microsoft.VisualStudio.Package.IScanner>|  
  
### <a name="in-the-source-class"></a>Na classe de origem  
  
|Método|Classe retornados|Descrição|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A></xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet></xref:Microsoft.VisualStudio.Package.CompletionSet>|Para personalizar a exibição de listas de conclusão do IntelliSense (esse método normalmente não é substituído).|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A></xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask></xref:Microsoft.VisualStudio.Package.DocumentTask>|Para oferecer suporte a marcadores na lista de tarefas da lista de erros; Especificamente, suporte para recursos além de abrir o arquivo e saltar para a linha que causou o erro.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A></xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData></xref:Microsoft.VisualStudio.Package.MethodData>|Para personalizar a exibição de dicas de ferramenta do IntelliSense parâmetro Info.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A></xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo></xref:Microsoft.VisualStudio.Package.CommentInfo>|Para dar suporte a comentando o código.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A></xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink></xref:Microsoft.VisualStudio.Package.AuthoringSink>|Para coletar informações durante a operação de análise.|  
  
### <a name="in-the-authoringscope-class"></a>Na classe AuthoringScope  
  
|Método|Classe retornados|Descrição|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A></xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations></xref:Microsoft.VisualStudio.Package.Declarations>|Fornece uma lista de declarações como membros ou tipos. Esse método deve ser implementado, mas pode retornar um valor nulo. Se esse método retorna um objeto válido, o objeto deve ser uma instância de sua versão da <xref:Microsoft.VisualStudio.Package.Declarations>classe.</xref:Microsoft.VisualStudio.Package.Declarations>|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A></xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods></xref:Microsoft.VisualStudio.Package.Methods>|Fornece uma lista de assinaturas de método para um determinado contexto. Esse método deve ser implementado, mas pode retornar um valor nulo. Se esse método retorna um objeto válido, o objeto deve ser uma instância de sua versão da <xref:Microsoft.VisualStudio.Package.Methods>classe.</xref:Microsoft.VisualStudio.Package.Methods>|  
  
## <a name="language-service-images"></a>Imagens de serviço de linguagem  
 Para fornecer uma lista de ícones a serem usados em todo o serviço de linguagem, substituir o <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A>método o <xref:Microsoft.VisualStudio.Package.LanguageService>da classe e retornar um <xref:System.Windows.Forms.ImageList>que contém os ícones.</xref:System.Windows.Forms.ImageList> </xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> A base <xref:Microsoft.VisualStudio.Package.LanguageService>classe carrega um conjunto padrão de ícones.</xref:Microsoft.VisualStudio.Package.LanguageService> Desde que você especifique o índice de imagem exata nesses lugares que precisam de ícones, como organizar sua própria lista de imagens é integralmente com você.  
  
### <a name="images-used-in-intellisense-completion-lists"></a>Imagens usadas em listas de conclusão do IntelliSense  
 Para listas de conclusão do IntelliSense, o índice de imagem é especificado para cada item a <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A>método o <xref:Microsoft.VisualStudio.Package.Declarations>classe, que você deve substituir se quiser fornecer um índice de imagem.</xref:Microsoft.VisualStudio.Package.Declarations> </xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> O valor retornado do <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A>método é um índice na lista de imagens fornecida para o <xref:Microsoft.VisualStudio.Package.CompletionSet>construtor da classe e é a mesma lista de imagem retornado do <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A>método no <xref:Microsoft.VisualStudio.Package.LanguageService>classe (você pode alterar a lista imagem a ser usado para o <xref:Microsoft.VisualStudio.Package.CompletionSet>se você substituir o <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>método na <xref:Microsoft.VisualStudio.Package.Source>classe para fornecer uma lista de imagens diferentes).</xref:Microsoft.VisualStudio.Package.Source> </xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> </xref:Microsoft.VisualStudio.Package.CompletionSet> </xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> </xref:Microsoft.VisualStudio.Package.CompletionSet> </xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A>  
  
### <a name="images-used-in-the-navigation-bar"></a>Imagens usadas na barra de navegação  
 O **barra de navegação** exibe listas de tipos e membros e é usado para navegação rápida pode mostrar ícones. Esses ícones são obtidos a partir de <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A>método no <xref:Microsoft.VisualStudio.Package.LanguageService>classe e não pode ser substituída especificamente para o **barra de navegação**.</xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> Os índices usados para cada item nas caixas de combinação são especificados quando as listas que representa as caixas de combinação são preenchidas o <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>método o <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>classe (consulte [suporte para a barra de navegação em um serviço de linguagem herdado](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)).</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Esses índices de imagem são obtidos de alguma forma do analisador, normalmente por meio de sua versão da <xref:Microsoft.VisualStudio.Package.Declarations>classe.</xref:Microsoft.VisualStudio.Package.Declarations> Como os índices são obtidos é integralmente com você.  
  
### <a name="images-used-in-the-error-list-task-window"></a>Imagens usadas na janela de tarefas da lista de erros  
 Sempre que o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>Analisador de método (consulte [analisador de serviço de linguagem herdado e Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)) encontra um erro e passa esse erro para o <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A>método na <xref:Microsoft.VisualStudio.Package.AuthoringSink>classe, o erro é relatado no **lista de erros** janela tarefas.</xref:Microsoft.VisualStudio.Package.AuthoringSink> </xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Um ícone pode ser associado a cada item que aparece na janela de tarefas e esse ícone proveniente da mesma lista de imagem retornada do <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A>método de <xref:Microsoft.VisualStudio.Package.LanguageService>classe.</xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> O comportamento padrão das classes MPF é não mostrar uma imagem com a mensagem de erro. No entanto, você pode substituir esse comportamento derivando uma classe a partir de <xref:Microsoft.VisualStudio.Package.Source>classe e substituindo o <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>método.</xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> </xref:Microsoft.VisualStudio.Package.Source> Nesse método, você cria um novo <xref:Microsoft.VisualStudio.Package.DocumentTask>objeto.</xref:Microsoft.VisualStudio.Package.DocumentTask> Antes de retornar esse objeto, você pode usar o <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A>propriedade o <xref:Microsoft.VisualStudio.Package.DocumentTask>objeto para definir o índice de imagem.</xref:Microsoft.VisualStudio.Package.DocumentTask> </xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> Isso seria algo como o exemplo a seguir. Observe que `TestIconImageIndex` é uma enumeração que lista todos os ícones e é específico para este exemplo. Você pode ter uma maneira diferente de identificação de ícones no seu serviço de linguagem.  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.Shell;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    class TestSource : Source  
    {  
        public override DocumentTask CreateErrorTaskItem(  
            TextSpan          span,  
            string            filename,  
            string            message,  
            TastPriority      priority,  
            TaskCategory      category,  
            MARKERTYPE        markerType,  
            TaskErrorCategory errorCategory)  
        {  
            DocumentTask taskItem = base.CreateErrorTaskItem(  
                                           span,  
                                           filename,  
                                           message,  
                                           priority,  
                                           category,  
                                           markerType,  
                                           errorCategory);  
            if (errorCategory == TaskErrorCategory.Error)  
            {  
                taskItem.ImageIndex = TestIconImageIndex.Error;  
            }  
            return taskItem;  
        }  
    }  
}  
```  
  
## <a name="the-default-image-list-for-a-language-service"></a>A lista de imagem padrão para um serviço de linguagem  
 A lista de imagem padrão fornecida com as classes de serviço de linguagem MPF base contém um número de ícones associados os elementos de linguagem mais comuns. A maior parte desses ícones são organizadas em conjuntos de seis variações, correspondentes aos conceitos de acesso do público, interno, amigo, protegido, particular e atalho. Por exemplo, você pode ter diferentes ícones para um método dependendo se é pública, protegida ou privada.  
  
 A enumeração a seguir especifica nomes típicos para cada conjunto de ícones e especifica o índice associado. Por exemplo, com base na enumeração, você pode especificar o índice de imagem para um método protegido como `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`. Você pode alterar os nomes desta enumeração conforme desejado.  
  
```c#  
public enum IconImageIndex  
        {  
            // access types  
            AccessPublic = 0,  
            AccessInternal = 1,  
            AccessFriend = 2,  
            AccessProtected = 3,  
            AccessPrivate = 4,  
            AccessShortcut = 5,  
  
            Base = 6,  
            // Each of the following icon type has 6 versions,  
            //corresponding to the access types  
            Class = Base + 0,  
            Constant = Base + 1,  
            Delegate = Base + 2,  
            Enumeration = Base + 3,  
            EnumMember = Base + 4,  
            Event = Base + 5,  
            Exception = Base + 6,  
            Field = Base + 7,  
            Interface = Base + 8,  
            Macro = Base + 9,  
            Map = Base + 10,  
            MapItem = Base + 11,  
            Method = Base + 12,  
            OverloadedMethod = Base + 13,  
            Module = Base + 14,  
            Namespace = Base + 15,  
            Operator = Base + 16,  
            Property = Base + 17,  
            Struct = Base + 18,  
            Template = Base + 19,  
            Typedef = Base + 20,  
            Type = Base + 21,  
            Union = Base + 22,  
            Variable = Base + 23,  
            ValueType = Base + 24,  
            Intrinsic = Base + 25,  
            JavaMethod = Base + 26,  
            JavaField = Base + 27,  
            JavaClass = Base + 28,  
            JavaNamespace = Base + 29,  
            JavaInterface = Base + 30,  
            // Miscellaneous icons with one icon for each type.  
            Error = 187,  
            GreyedClass = 188,  
            GreyedPrivateMethod = 189,  
            GreyedProtectedMethod = 190,  
            GreyedPublicMethod = 191,  
            BrowseResourceFile = 192,  
            Reference = 193,  
            Library = 194,  
            VBProject = 195,  
            VBWebProject = 196,  
            CSProject = 197,  
            CSWebProject = 198,  
            VB6Project = 199,  
            CPlusProject = 200,  
            Form = 201,  
            OpenFolder = 202,  
            ClosedFolder = 203,  
            Arrow = 204,  
            CSClass = 205,  
            Snippet = 206,  
            Keyword = 207,  
            Info = 208,  
            CallBrowserCall = 209,  
            CallBrowserCallRecursive = 210,  
            XMLEditor = 211,  
            VJProject = 212,  
            VJClass = 213,  
            ForwardedType = 214,  
            CallsTo = 215,  
            CallsFrom = 216,  
            Warning = 217,  
        }  
```  
  
## <a name="see-also"></a>Consulte também  
 [Implementando um serviço de linguagem herdado](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Visão geral do serviço de linguagem herdada](../../extensibility/internals/legacy-language-service-overview.md)   
 [Registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Scanner e Parser de serviço de linguagem herdada](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
