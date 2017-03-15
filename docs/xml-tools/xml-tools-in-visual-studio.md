---
title: "Ferramentas XML no (Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.xmldesigner"
helpviewer_keywords: 
  - "classes [Visual Studio], XML"
  - "CSS, folhas de estilo para XML"
  - "dados [Visual Studio], XML"
  - "conjuntos de dados [Visual Basic], Esquemas XML"
  - "arquivos de descoberta, XML"
  - "Modelos Corporativos, XML e"
  - "controles de servidor, XML e"
  - "SGML, XML"
  - "folhas de estilos, para XML"
  - "Controles de servidor Web, XML"
  - "Serviços Web"
  - "XML [Visual Studio]"
  - "XML [Visual Studio], Classes do .NET Framework"
  - "XML [Visual Studio], fontes de dados"
  - "XML [Visual Studio], recursos"
  - "XML [Visual Studio], relações SGML a"
  - "esquemas XML"
  - "Classe XMLDataDocument"
  - "esquemas XSD"
  - "XSL"
  - "XSL, folhas de estilos"
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
caps.latest.revision: 21
caps.handback.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Ferramentas XML no (Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*Extensible Markup Language \(XML\)* é uma linguagem de marcação que fornece um formato para a descrição de dados.  Isso facilita declarações mais precisas de conteúdo e mais resultados de pesquisa significativos nas diversas plataformas.  Além disso, o XML permite a separação da apresentação dos dados.  Por exemplo, em HTML, usam\-se marcas para dizer ao navegador para exibir dados como negrito ou itálico; em XML, usam\-se marcas somente para descrever dados, como nome da cidade, temperatura e pressão barométrica.  Em XML, são usadas folhas de estilo como linguagem XSL e CSS \(folhas de estilos em cascata\) para apresentar os dados em um navegador.  O XML separa os dados da apresentação e do processo.  Isso permite exibir e processar os dados como desejar, aplicando diferentes folhas de estilo e aplicações.  
  
 O XML é um subconjunto do SGML que é otimizado para entrega na Web.  Ele é definido pelo World Wide Web Consortium \(W3C\).  Essa padronização garante que dados estruturados serão uniformes e independentes de aplicativos ou fornecedores.  
  
 O XML está no cerne de muitos recursos do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Os tópicos a seguir indicam os nomes de ferramentas e os recursos relacionados ao XML que são oferecidos no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e no [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Para obter mais informações, consulte o [Centro de Desenvolvedores XML](http://go.microsoft.com/fwlink/?LinkID=100176), que fornece a documentação mais recente, as informações técnicas, os downloads, grupos de notícias e outros recursos para desenvolvedores XML.  
  
## Nesta seção  
 [Working with XML Data](../xml-tools/working-with-xml-data.md)  
 Discute a função do XML na maneira que os dados são tratados em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 [Depuração do XSLT](../xml-tools/debugging-xslt.md)  
 Fornece links para tópicos sobre o uso do depurador Visual Studio para depurar o XSLT.  
  
## Referência  
 [Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699)  
 Expõe a árvore de análise do [Editor de XML](http://go.microsoft.com/fwlink/?LinkId=228249) através do [System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250) para qualquer documento XML.  
  
 [Referência a padrões XML](http://msdn.microsoft.com/pt-br/79c78508-c9d0-423a-a00f-672e855de401)  
 Fornece informações sobre as tecnologias XML, incluindo XML, Definição de Tipo de Documento \(DTD\), linguagem XSD do XML e XSLT.  
  
 <xref:System.Xml?displayProperty=fullName>  
 Descreve as classes e outros elementos que compõem o namespace <xref:System.Xml> e fornece links para informações mais detalhadas sobre cada item.  
  
 <xref:System.Xml.Serialization?displayProperty=fullName>  
 Descreve as classes e outros elementos que compõem o namespace <xref:System.Xml.Serialization> e fornece links para informações mais detalhadas sobre cada item.  
  
## Seções relacionadas  
 [XML Document Object Model \(DOM\)](../Topic/XML%20Document%20Object%20Model%20\(DOM\).md)  
 Descreve como o <xref:System.Xml.XmlDocument> e suas classes associadas atendem a conformidade com as especificações de suporte do namespace do Nível 1 e Nível 2 do W3C Document Object Model \(Principal\).  
  
 [Reading XML with the XmlReader](http://msdn.microsoft.com/pt-br/3029834c-a27e-4331-b7aa-711924062182)  
 Descreve como o <xref:System.Xml.XmlReader> fornece acesso somente para leitura, somente para encaminhamento sem armazenamento dos dados XML através de um fluxo XML.  
  
 [Writing XML with the XmlWriter](http://msdn.microsoft.com/pt-br/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86)  
 Descreve como o <xref:System.Xml.XmlWriter> fornece uma maneira de gerar fluxos de XML sem armazenamento em cache, somente para encaminhamento, e auxilia na construção de documentos XML em conformidade com a norma W3C.  
  
 [XSLT Transformations](../Topic/XSLT%20Transformations.md)  
 Descreve como a classe <xref:System.Xml.Xsl.XslCompiledTransform> implementa a recomendação XSLT 1.0.  
  
 [Process XML Data Using the XPath Data Model](../Topic/Process%20XML%20Data%20Using%20the%20XPath%20Data%20Model.md)  
 Descreve como a classe <xref:System.Xml.XPath.XPathNavigator> pode processar os dados XML armazenados em um objeto <xref:System.Xml.XPath.XPathDocument> ou em um <xref:System.Xml.XmlDocument>.  A classe <xref:System.Xml.XPath.XPathNavigator> é baseada no Modelo de Dados XQuery 1.0 e XPath 2.0 ou pode ser usada para navegar e editar dados XML.  
  
 [XML Schema Object Model \(SOM\)](../Topic/XML%20Schema%20Object%20Model%20\(SOM\).md)  
 Descreve as classes usadas para criar e manipular esquemas XML, fornecendo uma classe <xref:System.Xml.Schema.XmlSchema> para carregar e editar um esquema.