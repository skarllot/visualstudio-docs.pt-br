---
title: "Security Considerations when Working with XML Data | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Security Considerations when Working with XML Data
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tópico aborda problemas de segurança que você precisa saber sobre ao trabalhar com o editor XML ou o depurador XSLT.  
  
## Editor de XML  
 O editor XML é baseado no editor de texto do Visual Studio.  Depende de classes de <xref:System.Xml> e de <xref:System.Xml.Xsl> para manipular muitos dos processos XML.  
  
-   As transformações XSLT são executadas em um domínio de aplicativo.  As transformações XSLT *na área restrita*; isto é, a política de segurança de acesso a código do seu computador é usada para determinar as permissões restritas com base em onde a folha de estilos XSLT é encontrada.  Por exemplo, folhas de estilos de um local da Internet tem as permissões as mais rígidas, enquanto as folhas de estilos copiaram ao seu disco rígido executado com confiança total.  
  
-   A classe de <xref:System.Xml.Xsl.XslCompiledTransform> é usado para compilar XSLT a Microsoft intermediate language para aumentar o desempenho durante a execução.  
  
-   Os esquemas apontando para uma localidade externa no arquivo de catálogo são baixados automaticamente quando o editor XML carrega primeiro.  A classe de <xref:System.Xml.Schema.XmlSchemaSet> é usada para criar esquemas.  O arquivo de catálogo que acompanha o editor XML não possui links para todos os esquemas externos.  O usuário tem que adicionar explicitamente uma referência para o esquema externa antes que o editor XML baixar o arquivo de esquema.  Baixar HTTP pode ser desativado por meio de página de **Diversos opções de ferramentas** para o editor XML.  
  
-   O editor XML usa as classes de <xref:System.Net> para baixar esquemas  
  
## Depurador XSLT  
 O depurador XSLT usa o mecanismo e as classes gerenciadas Visual Studio de depuração de <xref:System.Xml> e do espaço de <xref:System.Xml.Xsl> .  
  
-   O depurador XSLT executa cada transformação XSLT em um domínio de aplicativo na área restrita.  A política de segurança de acesso a código do seu computador é usada para determinar as permissões restritas com base em onde a folha de estilos XSLT é encontrada.  Por exemplo, folhas de estilos de um local da Internet tem as permissões as mais rígidas, enquanto as folhas de estilos copiaram ao seu disco rígido executado com confiança total.  
  
-   A folha de estilos XSLT é compilada usando a classe de <xref:System.Xml.Xsl.XslCompiledTransform> .  
  
-   O avaliador de expressão XSLT é carregado pelo mecanismo gerenciado de depuração.  O mecanismo gerenciado de depuração supõe que qualquer código é executado do computador local do usuário.  Da mesma forma, a classe de <xref:System.Xml.Xsl.XslCompiledTransform> download do arquivo fonte para o computador local do usuário.  A possibilidade que um ataue de elevação de privilégio em execução pode ocorrer é abrandada executando todas as transformações XSLT em um domínio de aplicativo com permissões restritas  
  
## Consulte também  
 [Application Domains](http://msdn.microsoft.com/pt-br/39e57d07-a740-4cd4-ae82-e119ea3856c1)