---
title: Acessando o Visual Studio ou outros Hosts de um modelo de texto | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 5
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
ms.openlocfilehash: 9b4e8c7230391ea460b8a15c548daa3ad6bfec19
ms.lasthandoff: 02/22/2017

---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>Acessando o Visual Studio ou outros hosts a partir de um modelo de texto
Em um modelo de texto, você pode usar métodos e propriedades expostos pelo host que executa o modelo, como [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Isso se aplica a modelos de texto normal, modelos de texto pré-processado não.  
  
## <a name="obtaining-access-to-the-host"></a>Obter acesso ao host  
 Definir `hostspecific="true"` na `template` diretiva. Isso permite que você use `this.Host`, que tem o tipo de <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>.</xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> Esse tipo tem membros que você pode usar, por exemplo, para resolver nomes de arquivo e registro de erros.  
  
### <a name="resolving-file-names"></a>Resolução de nomes de arquivo  
 Para localizar o caminho completo de um arquivo em relação ao modelo de texto, use isso. Host.ResolvePath().  
  
```c#  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ import namespace="System.IO" #>  
<#  
 // Find a path within the same project as the text template:  
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));  
#>  
Content of myFile is:  
<#= myFile #>  
  
```  
  
### <a name="displaying-error-messages"></a>Exibindo mensagens de erro  
 Este exemplo registra mensagens quando você transformar o modelo. Se o host for [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], eles são adicionados à janela de erro.  
  
```c#  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ import namespace="System.CodeDom.Compiler" #>  
<#  
  string message = "test message";  
  this.Host.LogErrors(new CompilerErrorCollection()   
    { new CompilerError(  
       this.Host.TemplateFile, // Identify the source of the error.  
       0, 0, "0",   // Line, column, error ID.  
       message) }); // Message displayed in error window.  
#>  
  
```  
  
## <a name="using-the-visual-studio-api"></a>Usando a API do Visual Studio  
 Se você estiver executando um modelo de texto em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], você pode usar `this.Host` para acessar os serviços fornecidos pelo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e quaisquer pacotes ou as extensões que são carregadas.  
  
 Definir hostspecific = "true" e converter `this.Host` <xref:System.IServiceProvider>.</xref:System.IServiceProvider>  
  
 Este exemplo obtém o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] API, <xref:EnvDTE.DTE>, como um serviço:</xref:EnvDTE.DTE>  
  
```c#  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ assembly name="EnvDTE" #>  
<#@ import namespace="EnvDTE" #>  
<#   
 IServiceProvider serviceProvider = (IServiceProvider)this.Host;  
 DTE dte = serviceProvider.GetService(typeof(DTE)) as DTE;    
#>  
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>  
  
```  
  
## <a name="using-hostspecific-with-template-inheritance"></a>Usando hostSpecific com herança do modelo  
 Especifique `hostspecific="trueFromBase"` se você usar também o `inherits` atributo, e se você herdar de um modelo que especifica `hostspecific="true"`. Isso evita um aviso do compilador para o efeito que a propriedade `Host` tiver sido declarada duas vezes.
