---
title: "CA3077: Processamento inseguro no projeto de API, o documento XML e o leitor de texto XML | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA3077: Processamento inseguro no projeto de API, o documento XML e o leitor de texto XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|NomeDoTipo|InsecureDTDProcessingInAPIDesign|  
|CheckId|CA3077|  
|Categoria|Microsoft.Security|  
|Alteração significativa|Não separável|  
  
## Causa  
 Quando criar uma API derivados do XMLDocument e XMLTextReader, tenha cuidado com a <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>.  Usando inseguro DTDProcessing instâncias quando referenciando Resolvendo fontes de entidade externa ou definindo valores inseguros no XML pode levar a divulgação de informações.  
  
## Descrição da regra  
 A [definição de tipo de documento \(DTD\)](https://msdn.microsoft.com/en-us/library/aa468547.aspx) é uma das duas maneiras de um analisador XML pode determinar a validade de um documento, conforme definido pelo  [World Wide Web Consortium \(W3C\) Extensible Markup Language \(XML\) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/). Esta regra procura propriedades e instâncias onde os dados não confiáveis é aceito para alertar os desenvolvedores sobre potencial [Divulgação de informações](../Topic/Information%20Disclosure.md) ameaças, que podem levar a [dos \(negação de serviço\)](../Topic/Denial%20of%20Service.md) ataques. Essa regra dispara quando:  
  
-   <xref:System.Xml.XmlDocument> ou <xref:System.Xml.XmlTextReader> classes usam valores de resolvedor padrão para processamento de DTD.  
  
-   Nenhum construtor é definido para o XmlDocument ou XmlTextReader classes derivadas ou nenhum valor seguro é usado para <xref:System.Xml.XmlResolver>.  
  
## Como corrigir violações  
  
-   Capturar e processar todas as exceções de XmlTextReader corretamente para evitar a divulgação de informações de caminho.  
  
-   Use <xref:System.Xml.XmlSecureResolver>em vez de XmlResolver para restringir os recursos que o XmlTextReader pode acessar.  
  
## Quando suprimir avisos  
 A menos que você tiver certeza de que a entrada é conhecida por ser de uma fonte confiável, suprime uma regra desse aviso.  
  
## Exemplos de código pseudo  
  
### Violação  
  
```c#  
using System;   
using System.Xml;   
  
namespace TestNamespace   
{   
    class TestClass : XmlDocument    
    {   
        public TestClass () {} // warn   
    }   
  
    class TestClass2 : XmlTextReader    
    {       
        public TestClass2() // warn   
        {   
        }   
    }   
}  
```  
  
### Solução  
  
```c#  
using System;   
using System.Xml;   
  
namespace TestNamespace   
{   
    class TestClass : XmlDocument    
    {   
        public TestClass ()    
        {   
            XmlResolver = null;   
        }   
    }   
  
    class TestClass2 : XmlTextReader    
    {       
        public TestClass2()    
        {   
               XmlResolver = null;   
        }   
    }   
}  
```