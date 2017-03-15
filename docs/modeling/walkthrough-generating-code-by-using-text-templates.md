---
title: "Passo a passo: Gerenciando código usando modelos de texto | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- walkthroughs [text templates], generating application code
- walkthroughs [text templates]
ms.assetid: 24602ade-baca-425e-a6ce-be09a2c7f7e1
caps.latest.revision: 11
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ce77bdffa69b646867246d1070d62f8722f44cdb
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-generating-code-by-using-text-templates"></a>Instruções passo a passo: gerenciando código usando modelos de texto
Geração de código permite produzir código do programa que tem rigidez de tipos e ainda pode ser facilmente alterado quando altera o modelo de origem. Compare isso com a técnica alternativa de escrever um programa completamente genérico que aceita um arquivo de configuração, que é mais flexível, mas resulta no código que não é tão fácil de ler e alterar, nem tem tal bom desempenho. Este passo a passo demonstra esse benefício.  
  
## <a name="typed-code-for-reading-xml"></a>Código digitado para a leitura de XML  
 O namespace System. XML fornece ferramentas abrangentes para carregar um documento XML e navegando-lo livremente na memória. Infelizmente, todos os nós têm o mesmo tipo, XmlNode. Portanto, é muito fácil cometer erros de programação como esperando o tipo errado de nó filho ou atributos errados.  
  
 Neste projeto de exemplo, um modelo lê um arquivo XML de exemplo e gera classes que correspondem a cada tipo de nó. No código escrito manualmente, você pode usar essas classes para navegar o arquivo XML. Você também pode executar seu aplicativo em todos os arquivos que usam os mesmos tipos de nó. A finalidade do arquivo XML de exemplo é fornecer exemplos de todos os tipos de nó que você deseja que seu aplicativo para lidar com.  
  
> [!NOTE]
>  O aplicativo [xsd.exe](http://go.microsoft.com/fwlink/?LinkId=178765), que está incluído no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], pode gerar classes com rigidez de tipos de arquivos XML. O modelo mostrado aqui é fornecido como um exemplo.  
  
 Aqui está o arquivo de exemplo:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<catalog>  
  <artist id ="Mike%20Nash" name="Mike Nash Quartet">  
    <song id ="MikeNashJazzBeforeTeatime">Jazz Before Teatime</song>  
    <song id ="MikeNashJazzAfterBreakfast">Jazz After Breakfast</song>  
  </artist>  
  <artist id ="Euan%20Garden" name="Euan Garden">  
    <song id ="GardenScottishCountry">Scottish Country Garden</song>  
  </artist>  
</catalog>  
```  
  
 No projeto que constrói este passo a passo, você pode escrever código como o seguinte e IntelliSense lhe com os nomes de atributo e filho corretos ao digitar:  
  
```  
Catalog catalog = new Catalog(xmlDocument);  
foreach (Artist artist in catalog.Artist)  
{  
  Console.WriteLine(artist.name);  
  foreach (Song song in artist.Song)  
  {  
    Console.WriteLine("   " + song.Text);  
  }  
}  
```  
  
 Compare isso com o código sem tipo que você pode escrever sem o modelo:  
  
```  
XmlNode catalog = xmlDocument.SelectSingleNode("catalog");  
foreach (XmlNode artist in catalog.SelectNodes("artist"))  
{  
    Console.WriteLine(artist.Attributes["name"].Value);  
    foreach (XmlNode song in artist.SelectNodes("song"))  
    {  
         Console.WriteLine("   " + song.InnerText);  
     }  
}  
```  
  
 Na versão com rigidez de tipos, uma alteração no esquema XML resultará em alterações para as classes. O compilador irá realçar as partes do código do aplicativo que deve ser alterado. Na versão não tipada que usa código XML genérico, não há nenhum tal suporte.  
  
 Neste projeto, um único arquivo de modelo é usado para gerar as classes que possibilitam a versão digitada.  
  
## <a name="setting-up-the-project"></a>Configurar o projeto  
  
### <a name="create-or-open-a-c-project"></a>Crie ou abra um projeto c#  
 Você pode aplicar essa técnica para qualquer projeto de código. Este passo a passo usa um projeto c#, e para fins de teste, usamos um aplicativo de console.  
  
##### <a name="to-create-the-project"></a>Para criar o projeto  
  
1.  Sobre o **arquivo** menu clique **novo** e, em seguida, clique em **projeto**.  
  
2.  Clique o **Visual C#** nó e, em seguida, no **modelos** painel, clique em **aplicativo de Console.**  
  
### <a name="add-a-prototype-xml-file-to-the-project"></a>Adicionar um arquivo XML de protótipo para o projeto  
 A finalidade desse arquivo é fornecer exemplos dos tipos de nó XML que você deseja que o aplicativo seja capaz de ler. Pode ser um arquivo que será usado para testar seu aplicativo. O modelo produzirá uma classe c# para cada tipo de nó nesse arquivo.  
  
 O arquivo deve ser parte do projeto para que o modelo possa lê-lo, mas ele não será criado para o aplicativo compilado.  
  
##### <a name="to-add-an-xml-file"></a>Para adicionar um arquivo XML  
  
1.  Em **Solution Explorer**, com o botão direito no projeto, clique em **adicionar** e, em seguida, clique em **Novo Item**.  
  
2.  No **Adicionar Novo Item** caixa de diálogo, selecione **arquivo XML** do **modelos** painel.  
  
3.  Adicione o conteúdo de exemplo para o arquivo.  
  
4.  Para este passo a passo, nomeie o arquivo `exampleXml.xml`. Defina o conteúdo do arquivo a ser o XML mostrado na seção anterior.  
  
 ..  
  
### <a name="add-a-test-code-file"></a>Adicionar um arquivo de código de teste  
 Adicionar um arquivo c# ao seu projeto e gravar em uma amostra do código que você deseja ser capaz de gravar. Por exemplo:  
  
```  
using System;  
namespace MyProject  
{  
  class CodeGeneratorTest  
  {  
    public void TestMethod()  
    {  
      Catalog catalog = new Catalog(@"..\..\exampleXml.xml");  
      foreach (Artist artist in catalog.Artist)  
      {  
        Console.WriteLine(artist.name);  
        foreach (Song song in artist.Song)  
        {  
          Console.WriteLine("   " + song.Text);  
} } } } }  
```  
  
 Nesse estágio, esse código não compilar. Enquanto você escreve o modelo, você irá gerar classes que permitem que ele seja bem-sucedida.  
  
 Um teste mais abrangente pode verificar a saída dessa função de teste em relação ao conteúdo conhecido do arquivo XML de exemplo. Mas neste passo a passo, ficará satisfeitos quando compila o método de teste.  
  
### <a name="add-a-text-template-file"></a>Adicione um arquivo de modelo de texto  
 Adicione um arquivo de modelo de texto e definir a extensão de saída para ". cs".  
  
##### <a name="to-add-a-text-template-file-to-your-project"></a>Para adicionar um arquivo de modelo de texto ao seu projeto  
  
1.  Em **Solution Explorer**, com o botão direito no projeto, clique em **adicionar**e, em seguida, clique em **Novo Item**.  
  
2.  No **Adicionar Novo Item** caixa de diálogo, selecione **modelo de texto** do **modelos** painel.  
  
    > [!NOTE]
    >  Certifique-se de que você adicione um modelo de texto e não um pré-processados modelo de texto.  
  
3.  No arquivo, na diretiva do modelo, altere o `hostspecific` atributo `true`.  
  
     Essa alteração permitirá que o código do modelo acessar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] serviços.  
  
4.  Na diretiva de saída, altere o atributo de extensão para ". cs", para que o modelo gera um arquivo c#. Em um projeto do Visual Basic, você deve alterá-lo para "vb".  
  
5.  Salve o arquivo. Nesse estágio, o arquivo de modelo de texto deve conter estas linhas:  
  
    ```  
    <#@ template debug="false" hostspecific="true" language="C#" #>  
    <#@ output extension=".cs" #>  
    ```  
  
 .  
  
 Observe que um arquivo. cs é exibido no Gerenciador de soluções como uma subsidiária do arquivo de modelo. Você pode vê-lo clicando em [+] ao lado do nome do arquivo de modelo. Este arquivo é gerado do arquivo de modelo sempre que salvar ou move o foco para fora o arquivo de modelo. O arquivo gerado será compilado como parte do seu projeto.  
  
 Para conveniência ao desenvolver o arquivo de modelo, organize as janelas do arquivo de modelo e o arquivo gerado para que você pode vê-los ao lado do outro. Isso permite ver imediatamente a saída do seu modelo. Você também observará que, quando o modelo gera código c# inválido, erros serão exibidos na janela de mensagem de erro.  
  
 Qualquer edição que executar diretamente no arquivo gerado serão perdidas sempre que você salvar o arquivo de modelo. Você deve, portanto, evite editar o arquivo gerado ou editá-lo somente para testes curtos. Às vezes é útil tentar um fragmento de código no arquivo gerado, onde o IntelliSense está em operação, de curto e, em seguida, copie-o para o arquivo de modelo.  
  
## <a name="developing-the-text-template"></a>Desenvolvendo o modelo de texto  
 Após o melhor conselho no desenvolvimento ágil, desenvolveremos o modelo no passo a passo, limpar alguns dos erros em cada incremento, até que o código de teste compila e executa corretamente.  
  
### <a name="prototype-the-code-to-be-generated"></a>O código a ser gerado de protótipo  
 O código de teste requer uma classe para cada nó no arquivo. Portanto, alguns dos erros de compilação desaparecerá se você acrescentar essas linhas para o modelo e, em seguida, salvá-lo:  
  
```  
class Catalog {}   
class Artist {}  
class Song {}  
```  
  
 Isso ajuda você a ver o que é necessário, mas as declarações devem ser geradas a partir de tipos de nós no arquivo XML de exemplo. Exclua essas linhas experimentais do modelo.  
  
### <a name="generate-application-code-from-the-model-xml-file"></a>Gerar código de aplicativo a partir do arquivo XML de modelo  
 Para ler o arquivo XML e gerar declarações de classe, substitua o modelo de conteúdo com o código de modelo a seguir:  
  
```  
<#@ template debug="false" hostspecific="true" language="C#" #>  
<#@ output extension=".cs" #>  
<#@ assembly name="System.Xml"#>  
<#@ import namespace="System.Xml" #>  
<#  
 XmlDocument doc = new XmlDocument();  
 // Replace this file path with yours:  
 doc.Load(@"C:\MySolution\MyProject\exampleXml.xml");  
 foreach (XmlNode node in doc.SelectNodes("//*"))  
 {  
#>  
  public partial class <#= node.Name #> {}  
<#  
 }  
#>  
```  
  
 Substitua o caminho do arquivo com o caminho correto para o seu projeto.  
  
 Observe os delimitadores de bloco de código `<#...#>`. Esses delimitadores colchete um fragmento do código do programa que gera o texto. Os delimitadores de bloco da expressão `<#=...#>` uma expressão pode ser avaliada como uma cadeia de caracteres de colchetes.  
  
 Quando você estiver escrevendo um modelo que gera o código-fonte do seu aplicativo, você está lidando com dois textos de outro programa. O programa dentro de delimitadores de bloco de código é executado sempre que você salva o modelo ou move o foco para outra janela. O texto aparece fora os delimitadores, que é gerada, é copiado para o arquivo gerado e se torna parte do código do aplicativo.  
  
 A `<#@assembly#>` diretiva se comporta como uma referência, disponibilizando o assembly para o código de modelo. A lista de assemblies visto pelo modelo é separada da lista de referências do projeto de aplicativo.  
  
 O `<#@import#>` diretiva age como um `using` instrução, permitindo que você use os nomes curtos de classes do namespace importado.  
  
 Infelizmente, embora esse modelo gera código, ele produz uma declaração de classe para cada nó no arquivo XML de exemplo, para que se houver várias instâncias do `<song>` nó várias declarações da música classe serão exibidos.  
  
### <a name="read-the-model-file-then-generate-the-code"></a>Ler o arquivo de modelo, em seguida, gerar o código  
 Muitos modelos de texto seguem um padrão no qual a primeira parte do modelo lê o arquivo de origem e a segunda parte gera o modelo. Precisamos ler todo o arquivo de exemplo para resumir os tipos de nós que ele contém e gerar as declarações de classe. Outro `<#@import#>` é necessária para que podemos usar`Dictionary<>:`  
  
```  
<#@ template debug="false" hostspecific="true" language="C#" #>  
<#@ output extension=".cs" #>  
<#@ assembly name="System.Xml"#>  
<#@ import namespace="System.Xml" #>  
<#@ import namespace="System.Collections.Generic" #>  
<#  
 // Read the model file  
 XmlDocument doc = new XmlDocument();  
 doc.Load(@"C:\MySolution\MyProject\exampleXml.xml");  
 Dictionary <string, string> nodeTypes =   
        new Dictionary<string, string>();  
 foreach (XmlNode node in doc.SelectNodes("//*"))  
 {  
   nodeTypes[node.Name] = "";  
 }  
 // Generate the code  
 foreach (string nodeName in nodeTypes.Keys)  
 {  
#>  
  public partial class <#= nodeName #> {}  
<#  
 }  
#>  
```  
  
### <a name="add-an-auxiliary-method"></a>Adicionar um método auxiliar  
 Um bloco de controle de recurso de classe é um bloco no qual você pode definir métodos auxiliares. O bloco é delimitado por `<#+...#>` e ele deve aparecer como o último bloco no arquivo.  
  
 Se você preferir nomes de classe para começar com uma letra maiuscula, você pode substituir a última parte do modelo com o código de modelo a seguir:  
  
```  
// Generate the code  
 foreach (string nodeName in nodeTypes.Keys)  
 {  
#>  
  public partial class <#= UpperInitial(nodeName) #> {}  
<#  
 }  
#>  
<#+  
 private string UpperInitial(string name)  
 { return name[0].ToString().ToUpperInvariant() + name.Substring(1); }  
#>  
```  
  
 Nesse estágio, o arquivo. cs gerado contém as seguintes declarações:  
  
```  
public partial class Catalog {}  
public partial class Artist {}  
public partial class Song {}  
```  
  
 Para obter mais detalhes, como propriedades de texto interno, atributos e nós filho podem ser adicionados usando a mesma abordagem.  
  
### <a name="accessing-the-visual-studio-api"></a>Acessando a API do Visual Studio  
 Definindo o `hostspecific` atributo o `<#@template#>` diretiva permite que o modelo obter acesso ao [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] API. O modelo pode usar isso para obter o local dos arquivos de projeto, para evitar o uso de um caminho de arquivo absoluto no código do modelo.  
  
```  
<#@ template debug="false" hostspecific="true" language="C#" #>  
...  
<#@ assembly name="EnvDTE" #>  
...  
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
// Open the prototype document.  
XmlDocument doc = new XmlDocument();  
doc.Load(System.IO.Path.Combine(dte.ActiveDocument.Path, "exampleXml.xml"));  
```  
  
## <a name="completing-the-text-template"></a>Concluindo o modelo de texto  
 O conteúdo de modelo a seguir gera código que permite que o código de teste compilar e executar.  
  
```  
<#@ template debug="false" hostspecific="true" language="C#" #>  
<#@ output extension=".cs" #>  
<#@ assembly name="System.Xml" #>  
<#@ assembly name="EnvDTE" #>  
<#@ import namespace="System.Xml" #>  
<#@ import namespace="System.Collections.Generic" #>  
using System;using System.Collections.Generic;using System.Linq;using System.Xml;namespace MyProject{  
<#  
 // Map node name --> child name --> child node type  
 Dictionary<string, Dictionary<string, XmlNodeType>> nodeTypes = new Dictionary<string, Dictionary<string, XmlNodeType>>();  
  
 // The Visual Studio host, to get the local file path.  
 EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
 // Open the prototype document.  
 XmlDocument doc = new XmlDocument();  
 doc.Load(System.IO.Path.Combine(dte.ActiveDocument.Path, "exampleXml.xml"));  
 // Inspect all the nodes in the document.  
 // The example might contain many nodes of the same type,   
 // so make a dictionary of node types and their children.  
 foreach (XmlNode node in doc.SelectNodes("//*"))  
 {  
   Dictionary<string, XmlNodeType> subs = null;  
   if (!nodeTypes.TryGetValue(node.Name, out subs))  
   {  
     subs = new Dictionary<string, XmlNodeType>();  
     nodeTypes.Add(node.Name, subs);  
   }  
   foreach (XmlNode child in node.ChildNodes)  
   {  
     subs[child.Name] = child.NodeType;  
   }   
   foreach (XmlNode child in node.Attributes)  
   {  
     subs[child.Name] = child.NodeType;  
   }  
 }  
 // Generate a class for each node type.  
 foreach (string className in nodeTypes.Keys)  
 {  
    // Capitalize the first character of the name.  
#>  
    partial class <#= UpperInitial(className) #>  
    {      private XmlNode thisNode;      public <#= UpperInitial(className) #>(XmlNode node)       { thisNode = node; }  
  
<#  
    // Generate a property for each child.  
    foreach (string childName in nodeTypes[className].Keys)  
    {  
      // Allow for different types of child.  
      switch (nodeTypes[className][childName])  
      {  
         // Child nodes:  
         case XmlNodeType.Element:  
#>  
      public IEnumerable<<#=UpperInitial(childName)#>><#=UpperInitial(childName) #>      {         get         {            foreach (XmlNode node in                thisNode.SelectNodes("<#=childName#>"))              yield return new <#=UpperInitial(childName)#>(node);       } }  
<#  
         break;  
         // Child attributes:  
         case XmlNodeType.Attribute:  
#>  
      public string <#=childName #>      { get { return thisNode.Attributes["<#=childName#>"].Value; } }  
<#  
         break;  
         // Plain text:  
         case XmlNodeType.Text:  
#>  
      public string Text  { get { return thisNode.InnerText; } }  
<#  
         break;  
       } // switch  
     } // foreach class child  
  // End of the generated class:  
#>  
   }   
<#  
 } // foreach class  
  
   // Add a constructor for the root class   
   // that accepts an XML filename.  
   string rootClassName = doc.SelectSingleNode("*").Name;  
#>  
   partial class <#= UpperInitial(rootClassName) #>   {      public <#= UpperInitial(rootClassName) #>(string fileName){        XmlDocument doc = new XmlDocument();        doc.Load(fileName);        thisNode = doc.SelectSingleNode("<#=rootClassName#>");}   }}  
<#+  
   private string UpperInitial(string name)  
   {  
      return name[0].ToString().ToUpperInvariant() + name.Substring(1);  
   }  
#>  
```  
  
### <a name="running-the-test-program"></a>Executando o programa de teste  
 O principal do aplicativo de console, as linhas a seguir executará o método de teste. Pressione F5 para executar o programa no modo de depuração:  
  
```  
using System;  
namespace MyProject  
{ class Program  
  { static void Main(string[] args)  
    { new CodeGeneratorTest().TestMethod();  
      // Allow user to see the output:  
      Console.ReadLine();  
} } }  
```  
  
### <a name="writing-and-updating-the-application"></a>Gravando e atualizando o aplicativo  
 O aplicativo agora pode ser escrito em estilo fortemente tipados, usando as classes geradas em vez de usar o código XML genérico.  
  
 Quando altera o esquema XML, novas classes facilmente podem ser gerados. O compilador informará o desenvolvedor onde o código do aplicativo deve ser atualizado.  
  
 Para regenerar as classes, quando o arquivo XML de exemplo é alterado, clique em **transformar todos os modelos** na barra de ferramentas Solution Explorer.  
  
## <a name="conclusion"></a>Conclusão  
 Este passo a passo demonstra várias técnicas e benefícios de geração de código:  
  
-   *Geração de código* é a criação de parte do código-fonte do seu aplicativo de um *modelo*. O modelo contém informações em um formato adequado para o domínio de aplicativo e pode ser alterados durante a vida útil do aplicativo.  
  
-   Tipagem forte é uma vantagem de geração de código. Enquanto o modelo representa informações em um formato mais adequado para o usuário, o código gerado permite que outras partes do aplicativo para lidar com as informações usando um conjunto de tipos.  
  
-   IntelliSense e o compilador ajudam a criar código que cumpre o esquema do modelo, ao escrever novo código e quando o esquema é atualizado.  
  
-   A adição de um arquivo de modelo descomplicadas único para um projeto pode fornecer esses benefícios.  
  
-   Um modelo de texto pode ser desenvolvido e testado rapidamente e de forma incremental.  
  
 Neste passo a passo, o código do programa, na verdade, é gerado de uma instância do modelo, um exemplo representativo dos arquivos XML que processará o aplicativo. Uma abordagem mais formal, o esquema XML seria a entrada para o modelo, na forma de um arquivo. xsd ou uma definição de linguagem específica do domínio. Essa abordagem tornaria mais fácil para o modelo determinar características como a multiplicidade de uma relação.  
  
## <a name="troubleshooting-the-text-template"></a>O modelo de texto de solução de problemas  
 Caso você tenha visto erros de compilação ou transformação de modelo no **Error List**, ou se o arquivo de saída não foi corretamente gerado, você pode solucionar o modelo de texto com as técnicas descritas em [gerando arquivos com o utilitário TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).  
  
## <a name="see-also"></a>Consulte também  
 [Geração de código de tempo de design usando modelos de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)   
 [Gravando um modelo de texto T4](../modeling/writing-a-t4-text-template.md)
