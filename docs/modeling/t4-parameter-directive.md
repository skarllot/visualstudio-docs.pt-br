---
title: "T4 Diretiva de parâmetro | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d590387-1d9d-40a5-a72c-65fae7a8bdf3
caps.latest.revision: 3
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
ms.openlocfilehash: cbffe1545d9cfd9abd62eb357e4236e853c67249
ms.lasthandoff: 02/22/2017

---
# <a name="t4-parameter-directive"></a>Diretiva de parâmetro T4
Em um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modelo de texto, o `parameter` diretiva declara propriedades em seu código de modelo que são inicializadas de valores passados do contexto externo. Você pode definir esses valores se você escrever código que chama a transformação de texto.  
  
## <a name="using-the-parameter-directive"></a>Usando a diretiva de parâmetro  
  
```  
<#@ parameter type="Full.TypeName" name="ParameterName" #>  
```  
  
 A `parameter` diretiva declara propriedades em seu código de modelo que são inicializadas de valores passados do contexto externo. Você pode definir esses valores se você escrever código que chama a transformação de texto. Os valores podem ser passados no `Session` dicionário, ou em <xref:System.Runtime.Remoting.Messaging.CallContext>.</xref:System.Runtime.Remoting.Messaging.CallContext>  
  
 Você pode declarar parâmetros de qualquer tipo remoto. Ou seja, o tipo deve ser declarado com <xref:System.SerializableAttribute>, ou ele deve derivar de <xref:System.MarshalByRefObject>.</xref:System.MarshalByRefObject> </xref:System.SerializableAttribute> Isso permite que os valores de parâmetro a ser passado para o AppDomain em que o modelo é processado.  
  
 Por exemplo, você poderia escrever um modelo de texto com o seguinte conteúdo:  
  
```  
<#@ template language="C#" #>  
  
<#@ parameter type="System.Int32" name="TimesToRepeat" #>  
  
<# for (int i = 0; i < TimesToRepeat; i++) { #>  
Line <#= i #>  
<# } #>  
  
```  
  
## <a name="passing-parameter-values-to-a-template"></a>Passando valores de parâmetro para um modelo  
 Se você estiver escrevendo um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensão como um comando de menu ou um manipulador de eventos, você pode processar um modelo usando o serviço de modelagem de texto:  
  
```c#  
// Get a service provider – how you do this depends on the context:  
IServiceProvider serviceProvider = dte; // or dslDiagram.Store, for example   
// Get the text template service:  
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;  
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;  
// Create a Session in which to pass parameters:  
host.Session = host.CreateSession();  
// Add parameter values to the Session:  
session["TimesToRepeat"] = 5;  
// Process a text template:  
string result = t4.ProcessTemplate("MyTemplateFile.t4",  
  System.IO.File.ReadAllText("MyTemplateFile.t4"));  
  
```  
  
## <a name="passing-values-in-the-call-context"></a>Passando valores no contexto de chamada  
 Você também pode passar valores como dados lógicos no <xref:System.Runtime.Remoting.Messaging.CallContext>.</xref:System.Runtime.Remoting.Messaging.CallContext>  
  
 O exemplo a seguir passa valores usando os dois métodos:  
  
```c#  
ITextTemplating t4 = this.Store.GetService(typeof(STextTemplating)) as ITextTemplating;  
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;  
host.Session = host.CreateSession();  
// Pass a value in Session:  
host.Session["p1"] = 32;  
// Pass another value in CallContext:  
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("p2", "test");  
  
// Process a small template inline:  
string result = t4.ProcessTemplate("",   
   "<#@parameter type=\"System.Int32\" name=\"p1\"#>"  
 + "<#@parameter type=\"System.String\" name=\"p2\"#>"  
 + "Test <#=p1#> <#=p2#>");  
  
// Result value is:  
//     Test 32 test  
  
```  
  
## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>Passar valores para um modelo de texto de tempo de execução (pré-processado)  
 Não é geralmente necessário usar o `<#@parameter#>` diretiva com modelos de texto de tempo de execução (pré-processado). Em vez disso, você pode definir um construtor adicional ou uma propriedade configurável para o código gerado, por meio do qual você pode passar valores de parâmetro. Para obter mais informações, consulte [geração de texto de tempo de execução com modelos de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 No entanto, se você quiser usar `<#@parameter>` em um modelo de tempo de execução, você pode passar valores a ele usando o dicionário de sessão. Por exemplo, suponha que você criou o arquivo como um modelo pré-processado chamado `PreTextTemplate1`. Você pode chamar o modelo em seu programa usando o código a seguir.  
  
```c#  
PreTextTemplate1 t = new PreTextTemplate1();  
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();  
t.Session["TimesToRepeat"] = 5;  
// Add other parameter values to t.Session here.  
t.Initialize(); // Must call this to transfer values.  
string resultText = t.TransformText();  
  
```  
  
## <a name="obtaining-arguments-from-texttemplateexe"></a>Obtendo argumentos de TextTemplate.exe  
  
> [!IMPORTANT]
>  O `parameter` diretiva não recuperar os valores definidos na `–a` parâmetro o `TextTransform.exe` utilitário. Para obter esses valores, defina `hostSpecific="true"` no `template` diretiva e usar `this.Host.ResolveParameterValue("","","argName")`.
