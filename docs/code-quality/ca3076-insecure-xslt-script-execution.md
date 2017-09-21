---
title: "CA3076: A execu&#231;&#227;o do Script XSLT inseguro | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 53cb7a46-c564-488f-bc51-0e210a7853c9
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA3076: A execu&#231;&#227;o do Script XSLT inseguro
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|NomeDoTipo|InsecureXSLTScriptExecution|  
|CheckId|CA3076|  
|Categoria|Microsoft.Security|  
|Alteração significativa|Não separável|  
  
## Causa  
 Se você executar [transformações de linguagem de folhas de estilo extensível \(XSLT\)](https://support.microsoft.com/en-us/kb/313997) em aplicativos .NET de maneira insegura, o processador pode [resolver referências de URI não confiáveis](http://msdn.microsoft.com/pt-br/ba3e4d4f-1ee7-4226-a51a-78a1f1b5bd8a) que poderia revelar informações confidenciais para invasores, levando a ataques de negação de serviço e sites.  
  
## Descrição da regra  
 [XSLT](http://msdn.microsoft.com/pt-br/6377ce5f-3c45-42a6-b7a9-ec8da588b60c) é um padrão de World Wide Web Consortium \(W3C\) para transformar os dados XML. XSLT é normalmente usado para gravar folhas de estilo para transformar dados XML em outros formatos, como HTML, fixa comprimento texto, texto separado por vírgulas ou outro formato XML. Embora proibidas por padrão, você poderá habilitá\-lo para seu projeto.  
  
 Para garantir que você não estiver expondo uma superfície de ataque, essa regra dispara sempre que o XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> recebe instâncias de combinação inseguro de <xref:System.Xml.Xsl.XsltSettings> e <xref:System.Xml.XmlResolver>, que permite o processamento de um script mal\-intencionado.  
  
## Como corrigir violações  
  
-   Substitua o argumento XsltSettings inseguro XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> ou com uma instância que desabilitou a execução de função e script do documento.  
  
-   Substitua o <xref:System.Xml.XmlResolver> argumento com null ou um <xref:System.Xml.XmlSecureResolver> instância.  
  
## Quando suprimir avisos  
 A menos que você tiver certeza de que a entrada é conhecida por ser de uma fonte confiável, suprime uma regra desse aviso.  
  
## Exemplos de código pseudo  
  
### Violação  
  
```c#  
using System.Xml;  
using System.Xml.Xsl;  
  
namespace TestNamespace   
{   
    class TestClass   
    {  
         void TestMethod()   
        {    
             XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();   
             var settings = XsltSettings.TrustedXslt;   
             var resolver = new XmlUrlResolver();   
             xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn   
        }  
    }   
}   
```  
  
### Solução  
  
```c#  
using System.Xml;   
using System.Xml.Xsl;   
  
namespace TestNamespace   
{   
    class TestClass   
    {   
        void TestMethod()   
        {   
            XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();   
            var settings = XsltSettings.Default;   
            var resolver = new XmlUrlResolver();   
            xslCompiledTransform.Load("testStylesheet", settings, resolver);   
        }   
    }   
}  
```  
  
### Violação  
  
```c#  
using System.Xml;   
using System.Xml.Xsl;   
  
namespace TestNamespace   
{   
    class TestClass   
    {   
        private static void TestMethod(XsltSettings settings)   
        {   
            try   
            {   
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();   
                var resolver = new XmlUrlResolver();   
                xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn   
            }   
            catch { throw; }   
            finally { }   
        }   
    }   
}  
```  
  
### Solução  
  
```c#  
using System.Xml;   
using System.Xml.Xsl;   
  
namespace TestNamespace   
{   
    class TestClass   
    {   
        private static void TestMethod(XsltSettings settings)   
        {   
            try   
            {   
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();   
                settings.EnableDocumentFunction = false;   
                settings.EnableScript = false;   
                var resolver = new XmlUrlResolver();   
                xslCompiledTransform.Load("testStylesheet", settings, resolver);   
            }   
            catch { throw; }   
            finally { }   
        }   
    }   
}  
```