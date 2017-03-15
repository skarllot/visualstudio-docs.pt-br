---
title: "Métodos de utilitário de modelo de texto | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, utility methods
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: 50
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.ht:
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
ms.openlocfilehash: fcce7e9447cab1f7e570a3af5113ff5c5c80bc1f
ms.lasthandoff: 02/22/2017

---
# <a name="text-template-utility-methods"></a>Métodos de utilitário do modelo de texto
Há vários métodos que estão sempre disponíveis para você quando você escrever código em um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modelo de texto. Esses métodos são definidos no <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.</xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>  
  
> [!TIP]
>  Você também pode usar outros métodos e os serviços fornecidos pelo ambiente de host em um modelo de texto (não pré-processado) regular. Por exemplo, você pode resolver caminhos de arquivo, registro de erros e obter serviços fornecidos por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e qualquer carregados pacotes.  Para obter mais informações, consulte [acessando o Visual Studio a partir de um modelo de texto](http://msdn.microsoft.com/en-us/0556f20c-fef4-41a9-9597-53afab4ab9e4).  
  
## <a name="write-methods"></a>Escrever métodos  
 Você pode usar o `Write()` e `WriteLine()` métodos para acrescentar o texto dentro de um bloco de código padrão, em vez de usar um bloco de código da expressão. Os blocos de código de dois seguintes são funcionalmente equivalentes.  
  
##### <a name="code-block-with-an-expression-block"></a>Bloco de código com um bloco de expressão  
  
```  
<#  
int i = 10;  
while (i-- > 0)  
    { #>  
        <#= i #>  
    <# }  
#>  
```  
  
##### <a name="code-block-using-writeline"></a>Bloco de código usando WriteLine()  
  
```  
<#   
    int i = 10;  
    while (i-- > 0)  
    {   
        WriteLine((i.ToString()));  
    }  
#>  
```  
  
 Talvez seja útil usar um desses métodos de utilitário em vez de um bloco de expressão dentro de um bloco de código longo com estruturas de controle aninhadas.  
  
 O `Write()` e `WriteLine()` métodos têm duas sobrecargas, uma que usa um parâmetro único de cadeia de caracteres e outro que usa uma cadeia de caracteres de formato composto e uma matriz de objetos a serem incluídas na cadeia de caracteres (como o `Console.WriteLine()` método). Os seguintes dois usos de `WriteLine()` são funcionalmente equivalentes:  
  
```  
<#  
    string msg = "Say: {0}, {1}, {2}";  
    string s1 = "hello";  
    string s2 = "goodbye";  
    string s3 = "farewell";  
  
    WriteLine(msg, s1, s2, s3);  
    WriteLine("Say: hello, goodbye, farewell");  
#>   
```  
  
## <a name="indentation-methods"></a>Métodos de recuo  
 Você pode usar métodos de recuo para formatar a saída do seu modelo de texto. O <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>classe tem um `CurrentIndent` propriedade string que mostra o recuo atual no modelo de texto e um `indentLengths` campo que é uma lista dos recuos que foram adicionados.</xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> Você pode adicionar um recuo com o `PushIndent()` método e subtrair um recuo com o `PopIndent()` método. Se você quiser remover todos os recuos, use o `ClearIndent()` método. O bloco de código a seguir mostra o uso desses métodos:  
  
```  
<#  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
    ClearIndent();  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
#>  
```  
  
 Este bloco de código produz a seguinte saída:  
  
```  
Hello  
        Hello  
                Hello  
Hello  
        Hello  
```  
  
## <a name="error-and-warning-methods"></a>Métodos de aviso e erro  
 Você pode usar métodos de utilitário de erro e aviso para adicionar mensagens para o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lista de erros. Por exemplo, o código a seguir adicionará uma mensagem de erro para a lista de erros.  
  
```  
<#  
  try  
  {  
    string str = null;  
    Write(str.Length.ToString());  
  }  
  catch (Exception e)  
  {  
    Error(e.Message);  
  }  
#>    
```  
  
## <a name="access-to-host-and-service-provider"></a>Acesso ao Host e o provedor de serviços  
 A propriedade `this.Host` pode fornecer acesso a propriedades expostas pelo host que está executando o modelo. Usar `this.Host`, você deve definir `hostspecific` atributo a `<@template#>` diretiva:  
  
 `<#@template ... hostspecific="true" #>`  
  
 O tipo de `this.Host` depende do tipo de host no qual o modelo está em execução. Em um modelo que está sendo executado no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], você pode converter `this.Host` para `IServiceProvider` para obter acesso a serviços como o IDE. Por exemplo:  
  
```  
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
```  
  
## <a name="using-a-different-set-of-utility-methods"></a>Usando um conjunto diferente de métodos de utilitário  
 Como parte do processo de geração de texto, o arquivo de modelo é transformado em uma classe, denominada `GeneratedTextTransformation`e herda de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.</xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> Se você quiser usar um outro conjunto de métodos em vez disso, você pode escrever sua própria classe e especificá-la na diretiva do modelo. Sua classe deve herdar de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.</xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>  
  
```  
<#@ template inherits="MyUtilityClass" #>  
```  
  
 Use o `assembly` diretiva para fazer referência ao assembly onde a classe compilada pode ser encontrada.
