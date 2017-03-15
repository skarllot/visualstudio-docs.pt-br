---
title: SDK do Microsoft Help Viewer | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
caps.latest.revision: 33
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
ms.openlocfilehash: e3a3c9a0dbc5526bb9a6e56c0a0e9d80ccc5e14d
ms.lasthandoff: 02/22/2017

---
# <a name="microsoft-help-viewer-sdk"></a>SDK do Microsoft Help Viewer
Este artigo contém as seguintes tarefas para integradores de Visualizador de Ajuda do Visual Studio:  
  
-   Criar um tópico (F1 suporte)  
  
-   Criando um pacote de conteúdo de identidade visual do Visualizador da Ajuda  
  
-   Implantando um conjunto de artigos  
  
-   Adicionando Ajuda ao shell do Visual Studio (integrado ou isolado)  
  
-   Recursos adicionais  
  
### <a name="creating-a-topic-f1-support"></a>Criar um tópico (F1 suporte)  
 Esta seção fornece uma visão geral dos componentes de um tópico apresentado, requisitos de tópico, uma breve descrição de como criar um tópico (incluindo os requisitos de suporte F1) e, finalmente, um tópico de exemplo com o resultado renderizado.  
  
 **Visão geral de tópico do Visualizador da Ajuda**  
  
 Quando um tópico é chamado para processamento, o Visualizador da Ajuda obtém os elementos de pacote de identidade visual que estão associados com o tópico no momento da última atualização, junto com o tópico XHTML, ou instalar e combina os dois para resultar na exibição de conteúdo apresentada (dados de identidade visual + dados tópico).  O pacote de marcas contém logotipos, suporte para comportamentos de conteúdo e texto de identidade visual (direitos autoral, etc.).  Consulte "Criar pacote de identidade visual" abaixo para obter mais informações sobre os elementos de pacote de identidade visual.  No evento não há nenhum pacote de marcas associada com o tópico, o Visualizador da Ajuda usará o pacote de marcas fallback localizado na raiz do aplicativo Visualizador da Ajuda (Branding_en US.mshc).  
  
 **Requisitos de tópico do Visualizador de ajuda**  
  
 Para ser processado corretamente pelo Visualizador da Ajuda, o conteúdo bruto deve ser W3C básica 1.1 XHTML.  
  
 Um tópico normalmente contém duas seções:  
  
-   Metadados (consulte a referência de metadados de conteúdo): pai dos dados sobre o tópico, por exemplo, a ID exclusiva do tópico, o valor de palavra-chave, o tópico de ID de índice, a ID do nó, etc.  
  
-   Conteúdo do corpo: compatíveis com XHTML do W3C básica 1.1 que inclui suporte para comportamentos de conteúdo (área recolhível, trecho de código, etc. Uma lista completa é mostrada abaixo).  
  
 Pacote de identidade visual do Visual Studio com suporte a controles:  
  
-   Links  
  
-   Trecho de código  
  
-   CollapsibleArea  
  
-   Membro herdado  
  
-   LanguageSpecificText  
  
 Suporte para cadeias de caracteres de idioma (não entre maiusculas e minúsculas):  
  
-   JavaScript  
  
-   CSharp ou c#  
  
-   cplusplus ou visualc + + ou c + +  
  
-   JScript  
  
-   Visual Basic ou vb  
  
-   f # ou fsharp ou fs  
  
-   outros – uma cadeia de caracteres que representa um nome de idioma  
  
 **Criar um tópico do Visualizador da Ajuda**  
  
 Criar um novo documento XHTML chamado ContosoTopic4.htm e incluir a marca de título (abaixo).  
  
```html  
<html>  
<head>  
<title>Contoso Topic 4</title>  
</head>  
  
<body>  
  
</body>  
</html>  
  
```  
  
 Em seguida, adicione dados para definir como o tópico deve ser apresentada (self da marca ou não), como fazer referência a este tópico para F1, onde este tópico existe no Sumário, sua ID (para referência de link por outros tópicos), etc.  Consulte a tabela "Metadados de conteúdo" abaixo para obter uma lista completa de metadados com suporte.  
  
-   Nesse caso, usaremos nosso próprio pacote de identidade visual, uma variante do pacote de identidade visual do Visualizador da Ajuda do Visual Studio.  
  
-   Adicionar o valor e nome de meta F1 (conteúdo de "Microsoft.Help.F1" = "ContosoTopic4") que corresponderá ao valor de F1 fornecido no recipiente de propriedades do IDE.  (Consulte a seção de suporte de F1 para obter mais informações).   Esse é o valor que corresponde ao F1 chamar de dentro do IDE para exibir este tópico quando F1 é escolhido no IDE.  
  
-   Adicionar a ID de tópico. Esta é a cadeia de caracteres que é usada por outros tópicos para vincular a esse tópico.  É a identificação de Visualizador de ajuda para este tópico.  
  
-   Para o Sumário, adicione nó do pai deste tópico para definir em que este nó de Sumário do tópico será exibido.  
  
-   Para o Sumário, adicione a ordem de nó deste tópico. Quando o nó pai tem n número de nós filhos, defina na ordem de nós filho local deste tópico. Por exemplo, este tópico é o número 4 de 4 tópicos filho.)  
  
 Seção de metadados de exemplo:  
  
```html  
<html>  
<head>  
<title>Contoso Topic 4</title>  
  
<meta name="SelfBranded" content="false" />     
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />  
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />  
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />  
    <meta name="Language" content="en-us" />  
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />  
<meta name="Microsoft.Help.TocOrder" content="4" />   
  
</head>  
  
<body>  
  
</body>  
</html>  
  
```  
  
 **O corpo do tópico**  
  
 O corpo (sem incluir o cabeçalho e rodapé) do tópico contém links da página, uma seção de observação, uma área recolhível, um trecho de código e uma seção de texto específica de idioma.  Consulte a seção de identidade visual para obter informações sobre as áreas de tópico apresentada.  
  
1.  Adicione uma marca de título do tópico:`<div class="title">Contoso Topic 4</div>`  
  
2.  Adicione uma seção de Observação:`<div class="alert"> add your table tag and text </div>`  
  
3.  Adicione uma área recolhível:`<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`  
  
4.  Adicione um trecho de código:`<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`  
  
5.  Adicionar texto específico do idioma de código: `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` Observe que devLangnu = permite que você insira outras linguagens. Por exemplo, devLangnu = "Fortran" exibirá Fortran quando o trecho de código DisplayLanguage = Fortran  
  
6.  Adicione links de página:`<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`  
  
> [!NOTE]
>  Observação: para sem suporte novo "idioma de exibição" (exemplo, F #, Cobol, Fortran) colorização de código no trecho de código será monocromático.  
  
 **Tópico Visualizador da Ajuda do exemplo** o código ilustra como definir metadados, um trecho de código, uma área recolhível e texto específico do idioma.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<html>  
<head>  
<title>Contoso Topic 4</title>  
  
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />  
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />  
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />  
    <meta name="Language" content="en-us" />  
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />  
<meta name="Microsoft.Help.TocOrder" content="4" />   
<meta name="SelfBranded" content="false" />     
</head>  
  
<body>  
<div class="title">Contoso Topic 4</div>  
  
  <div id="header">  
<table id="bottomTable" cellpadding="0" cellspacing="0"  width="100%">  
        <tr id="headerTableRow2"><td align="left">  
            <span id="nsrTitle">Contoso Topic 1</span>  
          </td>  
<td align="right">  
</td></tr>  
<tr id="headerTableRow1"><td align="left">  
            <span id="runningHeaderText">Contoso Widgets & Sprockets</span>  
          </td></tr>  
      </table>  
</div>  
  
<h2>Table of Contents</h2>  
  
<ul class="toc">  
<li class="tocline1"><a href="#introduction" target="_self">1.0 Introduction</a></li>  
<li class="tocline1"><a href="#seealso" target="_self">2.1 See Also</a></li>  
</ul>  
  
<div class="topic">  
  
<div id="mainSection">  
<div id="mainBody">  
  
<a name="introduction"></a>  
<h2>1.0 Introduction</h2>  
<p>[This documentation is for sample purposes only.]</p>  
  
<p>Contoso Topic 1 contains examples of:  
<ul>  
<li>Collapsible Area</li>  
<li>Bookmark ("See also")</li>  
<li>Code Snippets from Branding Package</li>  
</ul>  
 </p>  
<div class="alert"><table><tr><th>  
<strong>Note </strong></th></tr>  
<tr><td>  
<p>This is an example of a <span class="label">Note </span>section.    
Call out important items for your reader in this <span class="label">Note </span>box.  
</p></td></tr>  
</table>  
</div>  
</div>  
  
<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading">  
  
            <a id="sectionToggle0"><!----></a>  
  
<div>  
Example of Collapsible Area  
<br/>  
Lorem ipsum dolor sit amet...  
</div>  
</CollapsibleArea>  
  
<div id="snippetGroup" >  
<CodeSnippet EnableCopyCode="true" Language="VisualBasic" ContainsMarkup="false" DisplayLanguage="Visual Basic" >  
Private Sub ToolStripRenderer1_RenderGrip(sender as Object, e as ToolStripGripRenderEventArgs) _ Handles ToolStripRenderer1.RenderGrip  
Dim messageBoxVB as New System.Text.StringBuilder()  
    messageBoxVB.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds)  
    messageBoxVB.AppendLine()  
 ...  
    MessageBox.Show(messageBoxVB.ToString(),"RenderGrip Event")  
End Sub  
</CodeSnippet>  
  
<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" >  
private void ToolStripRenderer1_RenderGrip(Object sender, ToolStripGripRenderEventArgs e)   
{   
System.Text.StringBuilder messageBoxCS = new System.Text.StringBuilder();  
messageBoxCS.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds );  
messageBoxCS.AppendLine();  
...  
MessageBox.Show(messageBoxCS.ToString(), "RenderGrip Event" );  
}  
</CodeSnippet>  
  
<CodeSnippet EnableCopyCode="true" Language="fsharp" ContainsMarkup="false" DisplayLanguage="F#" >  
some F# code  
</CodeSnippet>  
</div>  
  
<h4 class="subHeading">Example of code specific text</h4>Language = <LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />  
  
<a name="seealso"></a>  
<h1 class="heading">See Also</h1>  
  
    <div id="seeAlsoSection" class="section">   
    <div class="seeAlsoStyle">  
        <a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>  
    </div>  
 </div>  
</div>  
</div>  
</body>  
</html>  
  
```  
  
 **Suporte de F1**  
  
 No Visual Studio, selecionar F1 gera valores fornecidos do posicionamento do cursor dentro do IDE e preenche um "recipiente de propriedades" com os valores fornecidos (com base no local do cursor. Quando o cursor está sobre o recurso x, o recurso x está ativo ou em foco e preenche o recipiente de propriedades com valores.  Quando F1 é selecionado o recipiente de propriedades é preenchido e código do Visual Studio F1 verifica se a fonte de ajuda os clientes padrão é local ou online (on-line é o padrão), cria a cadeia de caracteres apropriada com base em usuários definindo (online é o padrão) – execução do shell (consulte o guia do administrador ajuda para exe iniciar parâmetros) com parâmetros para o Visualizador da Ajuda local + palavras-chave do recipiente de propriedades se ajuda local é o padrão , ou a URL do MSDN com a palavra-chave na lista de parâmetros.  
  
 Se três cadeias de caracteres são retornadas para F1, conhecido para como uma cadeia de caracteres de valores múltiplos, levar o primeiro termo, procure ocorrência, e se encontrado, podemos terminar; Caso contrário, mova para a sequência de caracteres.  Ordem é importante. Apresentação de múltiplos valores palavras-chave deve ser a cadeia de caracteres mais longa em cadeia de caracteres mais curta.  Para verificar isso no caso de palavras-chave com vários valores, examine a cadeia de caracteres de URL F1 online, que inclui a palavra-chave escolhida.  
  
 No Visual Studio 2012, intencionalmente fizemos uma divisão mais forte entre online e offline, para que se a configuração do usuário para on-line, em seguida, simplesmente passamos a solicitação F1 diretamente ao nosso serviço consulta online no MSDN, em vez de roteamento por meio do agente de biblioteca de Ajuda que tínhamos no Visual Studio 2010. Em seguida, contamos com um estado de "conteúdo de fornecedor instalado = true" para determinar se deve fazer algo diferente nesse contexto. Se true, em seguida, realizamos essa lógica de roteamento e análise dependendo do que você deseja oferecer suporte para seus clientes. Se false, podemos ir para MSDN. Se a configuração do usuário for Local, basta ir todas as chamadas para o mecanismo de ajuda local.  
  
 F1 diagrama de fluxo:  
  
 ![Fluxo de F1](../../extensibility/internals/media/f1flow.png "F1flow")  
  
 Quando a fonte de conteúdo de Ajuda do Visualizador da Ajuda padrão é definida como on-line (Iniciar no navegador):  
  
-   Recursos do Visual Studio parceiro (VSP) emitir um valor para o recipiente de propriedades F1 (propriedade recipiente prefix.keyword e URL online para o prefixo encontrado no registro): F1 envia uma URL VSP + parâmetros para o navegador.  
  
-   Recursos do Visual Studio (editor de idiomas, itens de menu específicos do Visual Studio, etc.): F1 envia uma URL do Visual Studio para o navegador.  
  
 Quando a fonte de conteúdo de Ajuda do Visualizador da Ajuda padrão é definida como a Ajuda local (lançamento no Visualizador da Ajuda):  
  
-   Recursos VSP onde palavra-chave correspondentes entre o recipiente de propriedades de F1 e índice do repositório local (ou seja, o prefix.keyword de recipiente da propriedade = valor encontrado no índice de repositório local): F1 renderiza o tópico no Visualizador da Ajuda.  
  
-   Recursos do Visual Studio (nenhuma opção para VSP substituir o recipiente de propriedades emitido de recursos do Visual Studio): F1 renderiza um tópico do Visual Studio no Visualizador da Ajuda.  
  
 Defina os seguintes valores de registro para habilitar F1 Fallback para conteúdo de Ajuda do fornecedor. F1 Fallback significa que o Visualizador da Ajuda on-line é definido para procurar conteúdo de ajuda de F1, e o conteúdo do fornecedor é instalado localmente no disco rígido dos usuários. O Visualizador da Ajuda deve examinar a Ajuda local para o conteúdo mesmo que a configuração padrão é para obter ajuda online.  
  
1.  Definir o **VendorContent** valor na chave do registro ajuda 2.1:  
  
    -   Para sistemas operacionais de 32 bits:  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.1\Catalogs\VisualStudio12  
  
         "VendorContent" = DWORD:&00000;001  
  
    -   Para sistemas operacionais de 64 bits:  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12  
  
         "VendorContent" = DWORD:&00000;001  
  
2.  Registre o namespace de parceiro na chave do registro ajuda 2.1:  
  
    -   Para sistemas operacionais de 32 bits:  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.1\Partner*\\<>\>*  
  
         "local"="offline"  
  
    -   Para sistemas operacionais de 64 bits:  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Partner*\\<>\>*  
  
         "local"="offline"  
  
 **Base Namespace nativo de análise**  
  
 Para ativar a análise de base namespace nativo, no registro adicione um novo DWORD pelo nome do: BaseNativeNamespaces e defina seu valor como 1 (sob a chave de catálogo que desejam oferecer suporte).  Por exemplo, se você quiser usar o catálogo do Visual Studio, você pode adicionar a chave para o caminho:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12  
  
 Quando uma palavra-chave F1 no formato de QUE CABEÇALHO/método for encontrado, o caractere '/' será analisado, resultando em construção:  
  
-   CABEÇALHO: será o namespace pode ser usado para registrar no registro  
  
-   MÉTODO: Isso tornará a palavra-chave que é passada.  
  
 Por exemplo, dada uma biblioteca personalizada chamada CustomLibrary e um método chamado MyTestMethod, quando uma solicitação chega de F1 será formatada como `CustomLibrary/MyTestMethod`.  
  
 Um usuário pode registrar CustomLibrary como o namespace sob a seção de parceiros e fornecer qualquer chave local que desejarem, e a palavra-chave passada para a consulta será MyTestMethod.  
  
 **Habilitar ajuda ferramenta no IDE de depuração**  
  
 Adicione a seguinte chave do registro e o valor:  
  
 Tecla de Ajuda do HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\12.0\Dynamic: exibir a saída de depuração no valor de varejo: Sim  
  
 No IDE, sob o item de menu Ajuda, selecione "Debug Help Context"  
  
 **Metadados de conteúdo**  
  
 A tabela a seguir, qualquer cadeia de caracteres que aparece entre colchetes é um espaço reservado que deve ser substituído por um valor reconhecido. Por exemplo, em \<name="Microsoft.Help.Locale meta" conteúdo = "[código de idioma]" / >, "[código de idioma]" deve ser substituído por um valor como "en-us".  
  
|Propriedade (representação em HTML)|Descrição|  
|--------------------------------------|-----------------|  
|\<conteúdo de meta name="Microsoft.Help.Locale" = "[linguagem de código]" / >|Define uma localidade para este tópico. Se essa marca é usada em um tópico, ele deve ser usado apenas uma vez e deve ser inserido acima quaisquer outras marcas do Microsoft Help. Se essa marca não for usada, o texto do corpo do tópico será indexado usando o separador de palavras que está associado com a localidade do produto, se for especificado; Caso contrário, o en-us é usado o separador de palavras. Essa marca está em conformidade com ISOC RFC 4646. Para garantir que o Microsoft Help funciona corretamente, use essa propriedade em vez do atributo de idioma geral.|  
|\<conteúdo de meta name="Microsoft.Help.TopicLocale" = "[linguagem de código]" / >|Define uma localidade para este tópico quando outras localidades também são usadas. Se essa marca é usada em um tópico, ele deve ser usado apenas uma vez. Use essa marca quando o catálogo contém conteúdo em mais de um idioma. Vários tópicos em um catálogo podem ter a mesma ID, mas cada uma deve especificar um TopicLocale exclusivo. O tópico que especifica um TopicLocale que corresponde à localidade do catálogo é o tópico exibido no sumário. No entanto, todas as versões de idioma do tópico são exibidas nos resultados da pesquisa.|  
|\<título > [Title] \< /título >|Especifica o título deste tópico. Essa marca é necessária e deve ser usada apenas uma vez em um tópico. Se o corpo do tópico não contém um título \<div > seção, esse título é exibida no tópico e no índice de conteúdo.|  
|\<nome da meta = "Microsoft.Help.Keywords" conteúdo = "[aKeywordPhrase]" / >|Especifica o texto de um link que é exibido no painel de índice do Visualizador da Ajuda. Quando o link é clicado, o tópico é exibido. Você pode especificar várias palavras-chave de índice para um tópico, ou você pode omitir essa marca se não quiser links deste tópico para que apareça no índice. Palavras-chave "K" de versões anteriores da Ajuda podem ser convertidas para essa propriedade.|  
|\<conteúdo de meta name="Microsoft.Help.Id" = "[TopicID]" / >|Define o identificador para este tópico. Essa marca é necessária e deve ser usada apenas uma vez em um tópico. A ID deve ser exclusiva entre os tópicos no catálogo que tenham a mesma configuração de localidade. Em outro tópico, você pode criar um link para este tópico usando essa ID.|  
|\<meta name="Microsoft.Help.F1" content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/ >|Especifica a palavra-chave F1 para este tópico. Você pode especificar várias palavras-chave F1 para um tópico, ou você pode omitir essa marca se você não quiser que este tópico a ser exibido quando um usuário de aplicativo pressiona F1. Normalmente, apenas uma palavra-chave de F1 é especificada para um tópico. Palavras-chave "F" de versões anteriores da Ajuda podem ser convertidas para essa propriedade.|  
|\<nome da meta = "Description" content = "[Descrição do tópico]" / >|Fornece um breve resumo do conteúdo neste tópico. Se essa marca é usada em um tópico, ele deve ser usado apenas uma vez. Esta propriedade é acessada diretamente pela biblioteca de consulta; ele não é armazenado no arquivo de índice.|  
 conteúdo de meta name="Microsoft.Help.TocParent" = "[parent_Id]" / >|Especifica o tópico pai deste tópico no sumário. Essa marca é necessária e deve ser usada apenas uma vez em um tópico. O valor é o Microsoft.Help.Id do pai. Um tópico pode ter apenas um local na tabela de conteúdo. "-1" é considerado a ID de tópico para a raiz TOC. Em [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)], que a página é a home page do Visualizador da Ajuda. Essa é a razão mesmo que especificamente adicionamos TocParent =-1 para alguns tópicos para garantir que elas aparecem na parte superior nível. A home page do Visualizador da Ajuda é uma página do sistema e portanto não podem ser substituídas. Se um VSP tenta adicionar uma página com uma ID de -1, ele talvez seja adicionado ao conjunto de conteúdo, mas o Visualizador da Ajuda será sempre use a página de sistema – home page Visualizador da Ajuda|  
|\<conteúdo de meta name="Microsoft.Help.TocOrder" = "[inteiro positivo]" / >|Especifica onde este tópico no sumário aparece em relação a seus tópicos de mesmo nível. Essa marca é necessária e deve ser usada apenas uma vez em um tópico. O valor é um inteiro. Um tópico que especifica um número inteiro menor valor aparece acima de um tópico que especifica um número inteiro maior valor.|  
|\<conteúdo de meta name="Microsoft.Help.Product" = "[product code]" / >|Especifica o produto descrita neste tópico. Se essa marca é usada em um tópico, ele deve ser usado apenas uma vez. Essas informações também podem ser fornecidas como um parâmetro que é passado para o indexador de Ajuda.|  
|\<conteúdo de meta name="Microsoft.Help.ProductVersion" = "[version number]" / >|Especifica a versão do produto descrita neste tópico. Se essa marca é usada em um tópico, ele deve ser usado apenas uma vez. Essas informações também podem ser fornecidas como um parâmetro que é passado para o indexador de Ajuda.|  
|\<conteúdo de meta name="Microsoft.Help.Category" = "[string]" / >|Usado por produtos para identificar subseções do conteúdo. Você pode identificar várias subseções para um tópico, ou você pode omitir essa marca se não quiser links para identificar qualquer subseções. Essa marca é usada para armazenar os atributos de TargetOS e TargetFrameworkMoniker quando um tópico é convertido de uma versão anterior da Ajuda. O formato do conteúdo é AttributeName:AttributeValue.|  
|\<conteúdo da meta name="Microsoft.Help.TopicVersion ="[número de versão de tópico]"/ >|Especifica a esta versão do tópico quando existirem várias versões de um catálogo. Como Microsoft.Help.Id não é garantido como sendo exclusivo, essa marca é necessária quando há mais de uma versão de um tópico em um catálogo, por exemplo, quando um catálogo contém um tópico para o .NET Framework 3.5 e um tópico para o .NET Framework 4 e têm o mesmo Microsoft.Help.Id.|  
|\<nome da meta = "SelfBranded" content = "[TRUE ou FALSE]" / >|Especifica se este tópico usa o pacote de marcas de inicialização do Gerenciador de biblioteca da Ajuda ou um pacote de marcas específicas para o tópico. Essa marca deve ser verdadeiro ou falso. Se ele for verdadeiro, o pacote de marcas para o tópico associado substitui o pacote de marcas é definido quando o Gerenciador de biblioteca da Ajuda é iniciado para que o tópico é renderizado como desejado, mesmo se for diferente do processamento de outros tipos de conteúdo. Se for FALSE, do tópico atual é renderizado de acordo com o pacote de marcas é definido quando o Gerenciador de biblioteca da Ajuda é iniciado. Por padrão, o Gerenciador de biblioteca da Ajuda presume automática marcado seja false, a menos que a variável SelfBranded é declarada como TRUE; Portanto, você não precisa declarar \<nome meta = "SelfBranded" content = "FALSE" / >.|  
  
### <a name="creating-a-branding-package"></a>Criando um pacote de marcas  
 A versão do Visual Studio inclui um número de diferentes produtos do Visual Studio, incluindo o isolado e shells integrados para parceiros do Visual Studio.  Cada um desses produtos requer algum grau de conteúdo de ajuda baseados em tópicos marca suporte exclusivo para o produto.  Por exemplo, tópicos do Visual Studio precisam ter uma apresentação de marca consistente, enquanto o SQL Studio, que encapsula o Shell ISO, requer seu próprio exclusivo ajuda conteúdo identidade visual de cada tópico.  Um parceiro de Shell integrado pode ser seus tópicos da Ajuda para estar dentro do conteúdo de Ajuda do produto Visual Studio pai mantendo suas próprias marcas de tópico.  
  
 Pacotes de marcação são instalados com o produto que contém o Visualizador da Ajuda.  Para produtos do Visual Studio:  
  
-   Um pacote de marcas de fallback (Branding_\<localidade > mshc) é instalado na raiz do aplicativo 2.1 do Visualizador de Ajuda (exemplo: C:\Program Files (x86) \Microsoft Help Viewer\v2.1), o pacote de idiomas do Visualizador da Ajuda.  Isso é usado para casos onde o produto marca o pacote não está instalado (nenhum conteúdo foi instalado) ou em que o pacote de marcas instalado está corrompido.  Observe que os elementos do Visual Studio (logotipo e comentários) são ignorados quando o fallback de raiz do aplicativo marca o pacote é usado.  
  
-   Quando o conteúdo do Visual Studio está instalado do serviço do pacote de conteúdo, um pacote de marcas também está instalado (para o primeiro cenário de instalação de conteúdo de tempo).  Se houver uma atualização para o pacote de marcas, a atualização é instalada quando ocorre a próxima atualização de conteúdo ou a ação de instalação do pacote adicional.  
  
 O Visualizador da Ajuda Microsoft oferece suporte a identidade visual de tópicos com base nos metadados do tópico.  
  
-   Em que os metadados de tópico definem self da marca = true, renderizar o tópico como está, não faça nada (até onde a marca).  
  
-   Em que os metadados de tópico definem self da marca = false, usar o pacote de marcas associado com valor de metadados TopicVendor.  
  
-   Conteúdo em que os metadados de tópico definem name="Microsoft.Help.TopicVendor" =\< nome de pacote de identidade visual no fornecedor MSHA >, use o pacote de marcas definido no valor do conteúdo.  
  
-   Observe que, no catálogo do Visual Studio, há um aplicativo de prioridade de pacotes de identidade visual.  Marca primeiro do Visual Studio padrão será aplicada e, se definido nos metadados do tópico e suporte com a marca associada do pacote (conforme definido no msha a instalação), o fornecedor definido identidade visual é aplicado como uma substituição.  
  
 Elementos de identidade visual normalmente se enquadram em três categorias principais:  
  
-   Elementos de cabeçalho (os exemplos incluem link comentários, texto condicional, logotipo)  
  
-   Conteúdo comportamentos (os exemplos incluem elementos de texto do controle expandir/recolher e elementos de trecho de código)  
  
-   Elementos de rodapé (exemplo Copyright)  
  
 Itens considerados como incluem elementos marcados (detalhada nessa especificação):  
  
-   Logotipo do produto/catálogo (exemplo, Visual Studio)  
  
-   Elementos de link e o email de comentários  
  
-   Texto de aviso  
  
-   Texto de direitos autorais  
  
 Os arquivos de suporte do pacote de identidade visual do Visualizador da Ajuda do Visual Studio incluem:  
  
-   Gráficos (logotipos, ícones, etc.)  
  
-   Branding.js – suporte comportamentos de conteúdo de arquivos de script  
  
-   Branding.XML – cadeias de caracteres usado de forma consistente entre o conteúdo do catálogo.  Observação: para elementos de texto de localização do Visual Studio em branding.xml, incluem _locID = "\<valor exclusivo >"  
  
-   Branding.CSS – definições de estilo para consistência de apresentação  
  
-   Printing.CSS – definições de estilo de apresentação impressa consistente  
  
 Conforme observado anteriormente, pacotes de identidade visual são associados ao tópico:  
  
-   Quando SelfBranded = false é definido nos metadados, o tópico herda o catálogo de pacote de identidade Visual  
  
-   Ou quando SelfBranded = false e existe é um pacote de marca exclusivo definido no MSHA e disponível quando o conteúdo está instalado  
  
 Para VSPs Implementando pacotes de identidade visual personalizados (conteúdo VSP, SelfBranded = True), uma maneira para prosseguir é iniciar com o pacote de marcas de fallback (instalado com o Visualizador da Ajuda) e altere o nome do arquivo conforme apropriado.  O Branding_\<localidade > mshc é um arquivo zip com a extensão de arquivo alterado para mshc, simplesmente altere a extensão de mshc para. zip e extraia o conteúdo.  Veja a seguir marca elementos do pacote e modifique conforme apropriado (por exemplo, altere o logotipo para o logotipo VSP e a referência para o logotipo no arquivo Branding.xml, atualizar Branding.xml por especificações VSP, etc.).  
  
 Quando todas as modificações são feitas, crie um arquivo zip que contém os elementos de identidade visual desejados e altere a extensão para mshc.  
  
 Para associar o pacote de marcas personalizado, crie o MSHA que contém a referência ao arquivo de marca mshc juntamente com o conteúdo mshc (que contém os tópicos).  Veja a seguir "MSHA" para saber como criar um MSHA básico.  
  
 O arquivo Branding.xml contém um elemento de lista usado para itens específicos em um tópico de renderização consistente quando o tópico contém \<name="Microsoft.Help.SelfBranded meta" conteúdo = "false" / >.  Lista de elementos no arquivo Branding.xml Visual Studio é listada abaixo.  Observe que essa lista se destina a ser usado como um modelo para usuários de Shell ISO, onde eles modificam esses elementos (por exemplo, logotipo, comentários e direitos autorais) para atender às sua próprias necessidades da marca de produto.  
  
 Observação: variáveis indicadas por "{n}" têm dependências de código – remover ou alterar esses valores causará erros e possivelmente a falha do aplicativo. Identificadores de localização (_locID="codesnippet.n exemplo") são incluídos no pacote do Visual Studio identidade visual.  
  
 **Branding.XML**  
  
|||  
|-|-|  
|Recurso:|**CollapsibleArea**|  
|Uso:|Expandir recolhe o texto de controle de conteúdo|  
|**Elemento**|**Value**|  
|ExpandText|Expandir|  
|CollapseText|Recolher|  
|Recurso:|**Trecho de código**|  
|Uso:|Texto de controle de trecho de código.  Observação: Conteúdo do trecho de código com espaço "Não-separável" será alterado para o espaço.|  
|**Elemento**|**Value**|  
|CopyToClipboard|Copiar para a Área de Transferência|  
|ViewColorizedText|Exibir Colorizado|  
|CombinedVBTabDisplayLanguage|Visual Basic (Exemplo)|  
|VBDeclaration|Declaração|  
|VBUsage|Uso|  
|Recurso:|**Logotipo, rodapé e comentários**|  
|Uso:|Fornece um controle de comentários do cliente fornecer comentários sobre o tópico atual por email.  Texto de direitos autorais para o conteúdo.  Definição de logotipo.|  
|**Elemento**|**Valor (essas cadeias de caracteres podem ser modificadas para atender às necessidade de adoção de conteúdo).**|  
|Direitos autorais|© 2013 Microsoft Corporation. Todos os direitos reservados.|  
|SendFeedback|\<um href = "{0}" {1}>Send comentários\</a > sobre este tópico à Microsoft.|  
|FeedbackLink||  
|LogoTitle|[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]|  
|LogoFileName|vs_logo_bk.gif|  
|LogoFileNameHC|vs_logo_wh.gif|  
|Recurso:|**Isenção de responsabilidade**|  
|Uso:|Um conjunto de casos isenção de responsabilidade específicos para a máquina conteúdo traduzido.|  
|**Elemento**|**Value**|  
|MT_Editable|Este artigo foi traduzido por máquina. Se você tiver uma conexão de Internet, selecione "Exibir este tópico online" para exibir esta página em modo editável com o conteúdo original em inglês ao mesmo tempo.|  
|MT_NonEditable|Este artigo foi traduzido por máquina. Se você tiver uma conexão de Internet, selecione "Exibir este tópico online" para exibir esta página em modo editável com o conteúdo original em inglês ao mesmo tempo.|  
|MT_QualityEditable|Este artigo foi traduzido manualmente. Se você tiver uma conexão de Internet, selecione "Exibir este tópico online" para exibir esta página em modo editável com o conteúdo original em inglês ao mesmo tempo.|  
|MT_QualityNonEditable|Este artigo foi traduzido manualmente. Se você tiver uma conexão de Internet, selecione "Exibir este tópico online" para exibir esta página em modo editável com o conteúdo original em inglês ao mesmo tempo.|  
|MT_BetaContents|Este artigo foi traduzido por máquina para uma versão preliminar. Se você tiver uma conexão de Internet, selecione "Exibir este tópico online" para exibir esta página em modo editável com o conteúdo original em inglês ao mesmo tempo.|  
|MT_BetaRecycledContents|Este artigo foi traduzido manualmente para uma versão preliminar. Se você tiver uma conexão de Internet, selecione "Exibir este tópico online" para exibir esta página em modo editável com o conteúdo original em inglês ao mesmo tempo.|  
|Recurso:|**LinkTable**|  
|Uso:|Suporte para links de tópico online|  
|**Elemento**|**Value**|  
|LinkTableTitle|Vincular Tabela|  
|TopicEnuLinkText|Exibir a versão em inglês\</ a > deste tópico está disponível em seu computador.|  
|TopicOnlineLinkText|Exibir este tópico \<um href = "{0}" {1}>online\</ um >|  
|OnlineText|Online|  
|Recurso:|**Controle de áudio de vídeo**|  
|Uso:|Exibir elementos e o texto do conteúdo de vídeo|  
|**Elemento**|**Value**|  
|MultiMediaNotSupported|O Internet Explorer 9 ou posterior deve estar instalado para oferecer suporte ao conteúdo {0}.|  
|VideoText|exibindo vídeo|  
|AudioText|transmitindo áudio|  
|OnlineVideoLinkText|\<p > para exibir o vídeo associado a este tópico, clique em {0}\<um href = "\ \<" > \ \< aqui\</ a >.\< /p >|  
|OnlineAudioLinkText|\<p > para ouvir o áudio associado a este tópico, clique em {0}\<um href = "\ \<" > \ \< aqui\</ a >.\< /p >|  
|Recurso:|**Controle de conteúdo não instalado**|  
|Uso:|Elementos de texto (cadeias de caracteres) usados para a renderização de contentnotinstalled.htm|  
|**Elemento**|**Value**|  
|ContentNotInstalledTitle|Nenhum conteúdo foi encontrado no seu computador.|  
|ContentNotInstalledDownloadContentText|\<p > para baixar o conteúdo em seu computador, \<um href = "{0}" {1}>click guia gerenciar\</ a >.\< /p >|  
|ContentNotInstalledText|\<p > nenhum conteúdo é instalado em seu computador. Consulte seu administrador para instalação local do conteúdo da Ajuda. \</p>|  
|Recurso:|**Controle de tópico não encontrado**|  
|Uso:|Elementos de texto (cadeias de caracteres) usados para a renderização de topicnotfound.htm|  
|**Elemento**|**Value**|  
|TopicNotFoundTitle|Não é possível localizar o tópico solicitado no seu computador.|  
|TopicNotFoundViewOnlineText|\<p > o tópico solicitado não foi encontrado no seu computador, mas você pode \<um href = "{0}" {1}>view o tópico online\</ a >.\< /p >|  
|TopicNotFoundDownloadContentText|\<p > ver o painel de navegação para obter links para tópicos semelhantes, ou \<um href = "{0}" {1}>click guia gerenciar\</ um > para baixar o conteúdo em seu computador.\< /p >|  
|TopicNotFoundText|\<p > o tópico solicitado não foi encontrado no computador. \</p>|  
|Recurso:|**Tópico corrompido controle**|  
|Uso:|Elementos de texto (cadeias de caracteres) usados para a renderização de topiccorrupted.htm|  
|**Elemento**|**Value**|  
|TopicCorruptedTitle|Não é possível exibir o tópico solicitado.|  
|TopicCorruptedViewOnlineText|\<p > Visualizador da Ajuda é não é possível exibir o tópico solicitado. Pode haver um erro no conteúdo do tópico ou uma dependência do sistema subjacente. \</p>|  
|Recurso:|**Controle de página inicial**|  
|Uso:|Texto de oferecer suporte à exibição do conteúdo do nó de nível superior do Visualizador da Ajuda.|  
|**Elemento**|**Value**|  
|HomePageTitle|Página Inicial do Visualizador da Ajuda|  
|HomePageIntroduction|\<p > bem-vindo ao Visualizador da Ajuda Microsoft, uma fonte essencial de informações para as pessoas que usam ferramentas, produtos, tecnologias e serviços da Microsoft. O Visualizador da Ajuda fornece acesso a instruções e informações de referência, código de exemplo, artigos técnicos e muito mais. Para localizar o conteúdo que necessário, procure o sumário, use a pesquisa de texto completo ou navegue pelo conteúdo usando o índice de palavra-chave. \</p>|  
|HomePageContentInstallText|\<p >\<br / > usar o \<um href = "{0}" {1}>Manage conteúdo\</ um > guia para fazer o seguinte:\<ul >\<li > adicionar conteúdo ao seu computador.\< / li >\<li > verificar atualizações para o conteúdo local.\< / li >\<li > remover o conteúdo de seu computador.\< /li>\</ul>\</p>|  
|HomePageInstalledBooks|Livros Instalados|  
|HomePageNoBooksInstalled|Nenhum conteúdo foi encontrado no seu computador.|  
|HomePageHelpSettings|Configurações de Conteúdo da Ajuda|  
|HomePageHelpSettingsText|\<p > sua configuração atual é ajuda local. O Visualizador da Ajuda exibe o conteúdo que você instalou no seu computador. \<br / > para alterar a fonte de conteúdo da Ajuda, na barra de menus do Visual Studio, escolha \<span style = "{0}" > ajuda a definir preferência ajuda\</span >.\< br />\</p>|  
|Megabytes|MB|  
  
 **branding.js**  
  
 O arquivo branding.js contém JavaScript usado pelos elementos de identidade visual do Visualizador da Ajuda do Visual Studio.  Abaixo está uma lista de elementos de identidade visual e a função JavaScript suporte.  Todas as cadeias de caracteres a ser localizada para esse arquivo são definidas na seção "Cadeias de caracteres localizáveis" na parte superior desse arquivo.  Observe que o arquivo ICL foi criado para loc cadeias de caracteres dentro do arquivo branding.js.  
  
||||  
|-|-|-|  
|**Recurso de identidade Visual**|**Função JavaScript**|**Descrição**|  
|Var...||Definir variáveis|  
|Obter o idioma de código de usuário|setUserPreferenceLang|mapeia um índice # à linguagem de código|  
|Definir e obter valores de cookie|getCookie, setCookie||  
|Membro herdado|changeMembersLabel|Expandir/recolher membro herdado|  
|Quando SelfBranded = False|onLoad|Ler a cadeia de caracteres de consulta para verificar se é uma solicitação de impressão.  Defina todos os codesnippets para se concentrar na guia preferencial do usuário.  Se for uma impressão de solicitação, em seguida, defina isPrinterFriendly como true. Verifique se o modo de alto contraste.|  
|Trecho de código|addSpecificTextLanguageTagSet||  
||getIndexFromDevLang||  
||ChangeTab||  
||setCodesnippetLang||  
||setCurrentLang||  
||CopyToClipboard||  
|CollapsibleArea|addToCollapsibleControlSet|gravar todos os objetos de controle recolhível em lista.|  
||CA_Click|com base no estado da área recolhível, define qual imagem e texto para apresentar|  
|Suporte de contraste do logotipo|isBlackBackground()|Chamado para determinar se o plano de fundo preto.  Preciso apenas quando no modo de alto contraste.|  
||isHighContrast()|usar um intervalo de cor para detectar o modo de alto contraste|  
||onHighContrast(black)|Chamado quando o alto contraste é detectado|  
|Funcionalidade LST|||  
||addToLanSpecTextIdSet(id)||  
||updateLST(currentLang)||  
||getDevLangFromCodeSnippet(lang)||  
|Funcionalidade de multimídia|legenda (começar, final, texto, estilo)||  
||findAllMediaControls(normalizedId)||  
||getActivePlayer(normalizedId)||  
||captionsOnOff(id)||  
||toSeconds(t)||  
||getAllComments(node)||  
||styleRectify (styleName, styleValue)||  
||showCC(id)||  
||SubTitle(ID)||  
  
 **ARQUIVOS HTM**  
  
 O pacote de marcas contém um conjunto de arquivos HTM que suportam cenários de comunicação de informações importantes para usuários de conteúdo de Ajuda, por exemplo uma home page que contém uma seção que descreve quais conjuntos de conteúdo estão instalados e as páginas informando ao usuário quando tópicos não podem ser encontrados no conjunto de locais de tópicos. Observe que esses arquivos HTM podem ser modificados por produto.  Fornecedores de Shell ISO são capazes de usar o pacote de marcas padrão e alterar o comportamento e o conteúdo dessas páginas Suite sua necessidade.  Esses arquivos, consulte seu respectivo pacote de identidade visual para que as marcas de identidade visual para obter o conteúdo correspondente do arquivo branding.xml.  
  
||||  
|-|-|-|  
|**Arquivo**|**Use**|**Fonte de conteúdo exibido**|  
|HomePage|Essa é uma página que exibe conteúdo atualmente instalado e qualquer outra mensagem apropriada para apresentar ao usuário sobre seu conteúdo.  Esse arquivo tem o conteúdo adicional da meta dados atributo "Microsoft.Help.Id" = "-1", que coloca esse conteúdo na parte superior do índice de conteúdo local.||  
||<META_HOME_PAGE_TITLE_ADD></META_HOME_PAGE_TITLE_ADD>|Branding.XML, marca \<HomePageTitle >|  
||<HOME_PAGE_INTRODUCTION_SECTION_ADD></HOME_PAGE_INTRODUCTION_SECTION_ADD>|Branding.XML, marca \<HomePageIntroduction >|  
||<HOME_PAGE_CONTENT_INSTALL_SECTION_ADD></HOME_PAGE_CONTENT_INSTALL_SECTION_ADD>|Branding.XML, marca \<HomePageContentInstallText >|  
||<HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD></HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD>|Título de seção marca Branding.xml\<HomePageInstalledBooks >, os dados gerados de um aplicativo, \<HomePageNoBooksInstalled > quando nenhuma manuais estão instalados.|  
||<HOME_PAGE_SETTINGS_SECTION_ADD></HOME_PAGE_SETTINGS_SECTION_ADD>|Título de seção marca Branding.xml \<HomePageHelpSettings >, seção texto \<HomePageHelpSettingsText >.|  
|topiccorrupted.htm|Quando existe um tópico no conjunto de local, mas por algum motivo não pode ser exibido (conteúdo corrompido).||  
||<META_TOPIC_CORRUPTED_TITLE_ADD></META_TOPIC_CORRUPTED_TITLE_ADD>|Branding.XML, marca \<TopicCorruptedTitle >|  
||<TOPIC_CORRUPTED_SECTION_ADD></TOPIC_CORRUPTED_SECTION_ADD>|Branding.XML, marca \<TopicCorruptedViewOnlineText >|  
|topicnotfound.htm|Quando um tópico não foi encontrado no conteúdo local definido nem disponíveis on-line||  
||<META_TOPIC_NOT_FOUND_TITLE_ADD></META_TOPIC_NOT_FOUND_TITLE_ADD>|Branding.XML, marca \<TopicNotFoundTitle >|  
||<META_TOPIC_NOT_FOUND_ID_ADD></META_TOPIC_NOT_FOUND_ID_ADD>|Branding.XML, marca \<TopicNotFoundViewOnlineText > + \<TopicNotFoundDownloadContentText >|  
||<TOPIC_NOT_FOUND_SECTION_ADD></TOPIC_NOT_FOUND_SECTION_ADD>|Branding.XML, marca \<TopicNotFoundText >|  
|contentnotinstalled.htm|Quando não há nenhum conteúdo local do produto instalado.||  
||<META_CONTENT_NOT_INSTALLED_TITLE_ADD></META_CONTENT_NOT_INSTALLED_TITLE_ADD>|Branding.XML, marca \<ContentNotInstalledTitle >|  
||<META_CONTENT_NOT_INSTALLED_ID_ADD></META_CONTENT_NOT_INSTALLED_ID_ADD>|Branding.XML, marca \<ContentNotInstalledDownloadContentText >|  
||<CONTENT_NOT_INSTALLED_SECTION_ADD></CONTENT_NOT_INSTALLED_SECTION_ADD>|Branding.XML, marca \<ContentNotInstalledText >|  
  
 **Arquivos CSS**  
  
 O pacote Visual Studio ajuda visualizador marca contém dois arquivos css para dar suporte à apresentação conteúda consistente Ajuda do Visual Studio:  
  
-   Branding.css – contém elementos de css para renderizar where SelfBranded = false  
  
-   Printer.css – contém elementos de css para renderizar where SelfBranded = false  
  
 Arquivos de Branding.CSS inclui definições de apresentação de tópico do Visual Studio (limitação é que o branding.css contidas a Branding_\<localidade > mshc do serviço do pacote podem ser alterados).  
  
 **Arquivos gráficos**  
  
 Conteúdo do Visual Studio exibe um logotipo do Visual Studio, bem como outros elementos gráficos.  A lista completa de arquivos gráficos no pacote de identidade visual do Visualizador da Ajuda do Visual Studio é mostrada abaixo.  
  
||||  
|-|-|-|  
|**Arquivo**|**Use**|**Exemplos**|  
|clear.gif|Usado para renderizar área recolhível||  
|footer_slice.gif|Apresentação de rodapé||  
|info_icon.gif|Usado quando exibindo informações|Aviso de isenção de responsabilidade|  
|online_icon.gif|Esse ícone é a ser associado com links on-line||  
|tabLeftBD.gif|Usado para renderizar o contêiner de trecho de código||  
|tabRightBD.gif|Usado para renderizar o contêiner de trecho de código||  
|vs_logo_bk.gif|Usada para referências de logotipo de contraste normal, conforme definido na marca Branding.xml \<LogoFileName >.  Para produtos do Visual Studio, o nome do logotipo é vs_logo_bk.gif.||  
|vs_logo_wh.gif|Usada para referências de logotipo alta normal, conforme definido na marca Branding.xml \<LogoFileNameHC >.  Para produtos do Visual Studio, o nome do logotipo é vs_logo_wh.gif.||  
|ccOff.png|Legenda de gráfico||  
|ccOn.png|Legenda de gráfico||  
|ImageSprite.png|Usado para renderizar área recolhível|Expandir ou recolher o gráfico|  
  
### <a name="deploying-a-set-of-topics"></a>Implantando um conjunto de tópicos  
 Este é um tutorial muito simple e rápido para a criação de uma implantação de conteúdo do Visualizador da Ajuda definida com um arquivo MSHA e o conjunto de arquivos cab ou MSHC que contém os tópicos. O MSHA é um arquivo XML que descreve um conjunto de arquivos cab ou arquivos MSHC. O Visualizador da Ajuda podem ler MSHA para obter uma lista de conteúdo (o. CAB ou. Arquivos MSHC) disponível para instalação local.  
  
 Isso é apenas um livro de instruções que descrevem o esquema XML básico para o MSHA de Visualizador de Ajuda.  Observe que há uma implementação de exemplo abaixo dessa breve visão geral e exemplo HelpContentSetup.  
  
 O nome do MSHA, para fins desta prévia é HelpContentSetup (o nome do arquivo pode ser qualquer coisa, com a extensão. MSHA). HelpContentSetup (exemplo abaixo) deve conter uma lista dos arquivos cab ou MSHCs disponíveis.  Observe que o tipo de arquivo deve ser consistente dentro do MSHA (não oferece suporte a uma combinação de tipos de arquivo MSHA e CAB). Para cada CAB ou MSHC, deve haver um \<div classe = "pacote" >... \</div > (veja exemplo abaixo).  
  
 Observação: no exemplo de implementação a seguir, incluímos o pacote de marcas. Isso é essencial para incluir para obter os elementos necessários de processamento do conteúdo Visual Studio e comportamentos de conteúdo.  
  
 Arquivo HelpContentSetup msha exemplo: (substitua "nome 1 de conjunto de conteúdo" e "conteúdo conjunto nome 2" etc. com seus nomes de arquivo.)  
  
```  
<html>  
<head />  
<body class="vendor-book">  
<div class="details">  
<span class="vendor">Your Company</span>  
<span class="locale">en-us</span>  
<span class="product">Your Company Help Content</span>  
<span class="name">Your Company Help Content</span>  
</div>  
<div class="package-list">  
<div class="package">  
<span class="name">Your_Company _Content_Set_1</span>  
<span class="deployed">True</span>  
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>  
</div>  
<div class="package">  
<span class="name">Your_Company _Content_Set_2</span>  
<span class="deployed">True</span>  
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>  
</div>.  
  
```  
  
1.  Crie uma pasta local, algo como "C:\SampleContent"  
  
2.  Neste exemplo, usaremos arquivos MSHC para conter os tópicos.  Um MSHC é um zip com a extensão de arquivo alterado de. zip para. MSHC.  
  
3.  Criar o abaixo HelpContentSetup como um arquivo de texto (bloco de notas foi usado para criar o arquivo) e salve-o na pasta mencionado acima (consulte a etapa 1).  
  
 Observe que a classe de "Marca" existe e é exclusivo. A marca mshc está incluído nesse livro de instruções para que o conteúdo instalado terão a identidade visual e os comportamentos de conteúdo que estão contidos nos MSHCs terá suporte apropriado elementos contidos no pacote de identidade visual. Sem isso, haverá erros quando o sistema procura por itens de suporte que não fazem parte do copiados (instalado) conteúdo.  
  
 Para obter o pacote de identidade visual do Visual Studio, copie o arquivo de Branding_en US.mshc em C:\Program Files (x86) \Microsoft Help Viewer\v2.1\ para a pasta de trabalho.  
  
```html  
<html>  
<head />  
<body class="vendor-book">  
<div class="details">  
<span class="vendor">Your Company</span>  
<span class="locale">en-us</span>  
<span class="product">Your Company Help Content</span>  
<span class="name">Your Company Help Content</span>  
</div>  
<div class="package-list">  
<div class="package">  
<span class="name">Your_Company _Content_Set_1</span>  
<span class="deployed">True</span>  
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>  
</div>  
<div class="package">  
<span class="name">Your_Company _Content_Set_2</span>  
<span class="deployed">True</span>  
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>  
</div>  
<div class="package">  
<span class="packageType">branding</span>  
<span class="name">Branding_en-US</span>  
<span class="deployed">True</span>  
<a class="current-link" href="Branding_en-US.mshc">Branding_en-US.mshc</a>  
</div>  
</div>  
</body>  
</html>  
  
```  
  
 **Resumo**  
  
 Usar e estender as etapas acima permitirá VSPs implantar seus conjuntos de conteúdo do Visual Studio Help Viewer.  
  
### <a name="adding-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Adicionando Ajuda para o Shell do Visual Studio (integrado e isolado)  
 **Introdução**  
  
 Este passo a passo demonstra como incorporar o conteúdo da Ajuda em um aplicativo de Shell do Visual Studio e, em seguida, implantá-lo.  
  
 **Requisitos**  
  
1.  [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]  
  
2.  [Pacote redistribuível do Shell isolados do Visual Studio 2013](http://www.microsoft.com/visualstudio/11/downloads#vs-shell)  
  
 **Visão Geral**  
  
 O [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell é uma versão do [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] IDE no qual você pode basear um aplicativo. Esses aplicativos contêm o Shell isolado junto com as extensões que você criar. Usar modelos de projeto do Shell isolado, que são incluídos no [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] SDK para criar extensões.  
  
 As etapas básicas para criar um aplicativo baseado no Shell isolado e sua ajuda:  
  
1.  Obter o [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] ISO Shell redistribuível (um download da Microsoft).  
  
2.  No Visual Studio, crie uma extensão de Ajuda que é baseada no Shell isolado, por exemplo, a extensão de Ajuda da Contoso é descrito mais adiante neste passo a passo.  
  
3.  Encapsule a extensão e o Shell de ISO redistribuível para uma implantação MSI (uma configuração de aplicativo). Este passo a passo não inclui uma etapa de configuração.  
  
 Crie um repositório de conteúdo do Visual Studio. Para o cenário de Shell integrado, altere Studio12 Visual para o nome do catálogo de produto da seguinte maneira:  
  
-   Crie a pasta C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12.  
  
-   Crie um arquivo chamado Catalogtype e adicioná-lo à pasta. O arquivo deve conter as seguintes linhas de código:  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?>  
    <catalogType>UserManaged</catalogType>  
    ```  
  
 Defina o repositório de conteúdo no registro. Para o Shell integrado, altere VisualStudio12 para o nome do catálogo de produto:  
  
-   HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12  
  
     Chave: Valor de cadeia de caracteres LocationPath: C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12\  
  
-   HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12\en-US  
  
     Chave: Valor de cadeia de caracteres Nome_do_catálogo: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] documentação  
  
 **Criar o projeto**  
  
 Para criar uma extensão de Shell isolado:  
  
1.  No Visual Studio, em **arquivo**, escolha **novo projeto**, em **Other Project Types** escolha **extensibilidade**e, em seguida, escolha **Visual Studio Shell isolado**. Nomeie o projeto `ContosoHelpShell`) para criar um projeto de extensibilidade com base no modelo de Shell isolado do Visual Studio.  
  
2.  No Solution Explorer, no projeto ContosoHelpShellUI, na pasta arquivos de recurso, abra ApplicationCommands.vsct. Verifique se que essa linha é comentada (procure por "No_Help"):`<!-- <define name=“No_HelpMenuCommands”/> -->`  
  
3.  Escolha a tecla F5 para compilar e executar **depurar**. Na instância experimental do IDE do Shell isolado, escolha o **ajuda** menu. Verifique se o **exibir ajuda**, **adicionar e remover conteúdo da Ajuda**, e **Definir preferência ajuda** comandos são exibidos.  
  
4.  No Solution Explorer, no projeto ContosHelpShell, na pasta de personalização do Shell, abra ContosoHelpShell.pkgdef. Para definir o catálogo de Ajuda da Contoso, adicione as seguintes linhas:  
  
    ```  
     [$RootKey$\Help]  
    "Product"="Contoso"  
    "Catalog"="Contoso"  
    “Version"="100"  
    "BrandingPackage"="ContosoBrandingPackage.mshc"  
    ```  
  
5.  No Solution Explorer, no projeto ContosHelpShell, na pasta de personalização do Shell, abra ContosoHelpShell.Application.pkgdef. Para ativar a Ajuda F1, adicione as seguintes linhas:  
  
    ```  
    // F1 Help Provider  
  
    [$RootKey$\HelpProviders\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]  
    "Name"="13407"  
    "Package"="{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}"  
    @="Help3 Provider"  
    [$RootKey$\HelpProviders]  
    @="{C99BDC23-FF29-46bf-9658-ADD634CCAED8}"  
    [$RootKey$\Services\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]  
    "Name"="Help3 Provider"  
    @="{4A791146-19E4-11D3-B86B-00C04F79F802}"  
    ```  
  
6.  No Solution Explorer, no menu de contexto da solução ContosoHelpShell, escolha o **propriedades** item de menu. Em **propriedades de configuração**, selecione **do Configuration Manager**. No **configuração** coluna, altere todos os valores "Debug" para "Versão".  
  
7.  Compile a solução. Isso cria um conjunto de arquivos em uma pasta de versão, que será usada na próxima seção.  
  
 Para testar isso como se implantado:  
  
1.  No computador, você está implantando Contoso para instalar baixado ISO Shell (acima).  
  
2.  Crie uma pasta na \\\Program Files (x86)\\e nomeie-o `Contoso`.  
  
3.  Copie o conteúdo da pasta da versão ContosoHelpShell para \\pasta de \Contoso\ do \Program Files (x86).  
  
4.  Inicie o Editor do registro, escolhendo **executar** no **iniciar** menu e inserindo `Regedit`. No editor do registro, escolha **arquivo**e então **importação**. Navegue até a pasta do projeto ContosoHelpShell. Na pasta ContosoHelpShell sub, escolha ContosoHelpShell.reg.  
  
5.  Crie um repositório de conteúdo:  
  
     Para o Shell do ISO - criar um repositório de conteúdo de Contoso C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12  
  
     Para [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Integrated Shell, crie a pasta C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12  
  
6.  Criar Catalogtype e adicione o repositório de conteúdo (etapa anterior) que contém:  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?>  
    <catalogType>UserManaged</catalogType>  
    ```  
  
7.  Adicione as seguintes chaves do registro:  
  
     HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12Key: Valor de cadeia de caracteres LocationPath:  
  
     Para o Shell do ISO:  
  
     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio12  
  
     [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]Shell integrado:  
  
     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio12en-US  
  
     Chave: Valor de cadeia de caracteres Nome_do_catálogo: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] documentação. Para o Shell do ISO, esse é o nome do catálogo.  
  
8.  Copie seu conteúdo (cabs ou MSHC e MSHA) para uma pasta local.  
  
9. Exemplo a linha de comando do Shell integrado para testes de armazenamento de conteúdo. Para o Shell do ISO, altere os valores de catálogo e launchingApp conforme apropriado para coincidir com o produto.  
  
     Método de /helpQuery /catalogname. VisualStudio12 "C:\Program (x86) arquivos \Microsoft Help Viewer\v2.1\HlpViewer.exe" = "página < / id = ContosoTopic0" /launchingApp Microsoft VisualStudio,&12;.0  
  
10. Inicie o aplicativo Contoso (da raiz do aplicativo Contoso). No Shell de ISO, escolha o **ajuda** item de menu e altere o **Definir preferência ajuda** para **usar a Ajuda Local**.  
  
11. Dentro do shell, escolha o **ajuda** item de menu, em seguida, **exibir ajuda**. Deve iniciar o Visualizador da Ajuda local. Escolha o **gerenciar conteúdo** guia. Em **origem de instalação**, escolha o **disco** botão de opção. Escolha o **... ** botão e navegue até a pasta local que contém conteúdo Contoso (copiado para a pasta local na etapa anterior). Escolha o HelpContentSetup. A Contoso deve mostrar agora como um livro em seleções de livro. Escolha **adicionar**e, em seguida, escolha o **atualização** botão (canto inferior direito).  
  
12. Dentro da Contoso IDE, escolha a tecla F1 para testar a funcionalidade de F1.  
  
### <a name="additional-resources"></a>Recursos adicionais  
 Para a API de tempo de execução, consulte [API de Ajuda do Windows](http://msdn.microsoft.com/library/windows/desktop/hh447318\(v=vs.85\).aspx).  
  
 Para obter informações adicionais sobre como usar a API de Ajuda, consulte [exemplos de código do Visualizador de ajuda](http://visualstudiogallery.msdn.microsoft.com/f08f296f-7076-4aec-8da3-8f0fbe04461e)  
  
 Para fornecer comentários sobre esses componentes, use [Microsoft Connect](http://connect.microsoft.com/).  
  
 Envie sugestões de recursos para [Microsoft User Voice](http://visualstudio.uservoice.com/forums/121579-visual-studio)  
  
 Para obter ajuda adicional, tente o [fóruns do sistema de Ajuda e documentação do desenvolvedor MSDN](http://social.msdn.microsoft.com/Forums/devdocs/threads)  
  
 Atualizações em Dividir o problema, consulte o [Leiame do Visualizador de ajuda](http://go.microsoft.com/fwlink/?LinkID=231397&clcid=0x409)  
  
 Para contatar a equipe PM do Visualizador de ajuda diretamente, envie um email parahlpfdbk@microsoft.com
