---
title: "Extensão do Editor e do idioma serviços | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: 22
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 4d04f4588b1005e9b5ccb42c6042d01aacb45710
ms.lasthandoff: 02/22/2017

---
# <a name="extending-the-editor-and-language-services"></a>Estendendo o Editor e serviços de linguagem
Você pode adicionar recursos de serviço de linguagem (como IntelliSense) para o seu próprio editor e estender a maioria dos recursos do editor de código do Visual Studio.  Para obter uma lista completa de como você pode estender, consulte [serviço de linguagem e pontos de extensão de Editor](../extensibility/language-service-and-editor-extension-points.md).  
  
 Você pode estender a maioria dos recursos do editor usando o Managed Extensibility Framework (MEF). Por exemplo, se o recurso de editor que você deseja estender coloração de sintaxe, você pode escrever um MEF *parte do componente* que define as classificações que você deseja cores diferentes e como eles devem ser tratados. O editor também oferece suporte a várias extensões do mesmo recurso.  
  
 A camada de apresentação do editor é com base em Windows Presentation Framework (WPF). WPF fornece uma biblioteca de elementos gráficos para formatação de texto flexível e também fornece visualizações, como gráficos e animações.  
  
 O SDK do Visual Studio fornece adaptadores conhecidos como *correções* para oferecer suporte a VSPackages que foram escritos para versões anteriores. No entanto, se você tiver um VSPackage existente, recomendamos que você atualize para a nova tecnologia para obter melhor desempenho e confiabilidade.  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Introdução ao serviço de linguagem e as extensões do Editor](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Explica como criar uma extensão para o editor.|  
|[Dentro do Editor](../extensibility/inside-the-editor.md)|Descreve a estrutura geral do editor e lista alguns dos seus recursos.|  
|[Managed Extensibility Framework no Editor](../extensibility/managed-extensibility-framework-in-the-editor.md)|Explica como usar o Managed Extensibility Framework (MEF) com o editor.|  
|[Serviço de linguagem e pontos de extensão de Editor](../extensibility/language-service-and-editor-extension-points.md)|Lista os pontos de extensão do editor. Pontos de extensão representam os recursos do editor que podem ser estendidos.|  
|[Passo a passo: Criando um adorno de exibição, comandos e configurações (guias de coluna)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Apresenta e explica criando um adorno de modo que desenha linhas de gudie de coluna para ajudar a manter o código para uma determinada largura de exibição.  Também mostra lendo e gravando configurações, bem como declarar e implementação de comandos que você pode chamar na janela de comando.|  
|[Editor de importações](../extensibility/editor-imports.md)|Lista os serviços que pode importar uma extensão.|  
|[Adaptando um código herdado para o Editor](../extensibility/adapting-legacy-code-to-the-editor.md)|Explica diferentes maneiras de adaptar o código herdado (pré-Visual Studio 2010) para estender o editor.|  
|[Migrando um serviço de linguagem herdado](../extensibility/internals/migrating-a-legacy-language-service.md)|Explica como migrar um serviço de linguagem VSPackage com base.|  
|[Passo a passo: Vinculação de um tipo de conteúdo para uma extensão de nome de arquivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Mostra como vincular um tipo de conteúdo a uma extensão de nome de arquivo.|  
|[Passo a passo: Criando um glifo de margem](../extensibility/walkthrough-creating-a-margin-glyph.md)|Mostra como adicionar um ícone para uma margem.|  
|[Passo a passo: Realçando texto](../extensibility/walkthrough-highlighting-text.md)|Mostra como usar *marcas* para realçar o texto.|  
|[Instruções passo a passo: estrutura de tópicos](../extensibility/walkthrough-outlining.md)|Mostra como adicionar a estrutura de tópicos para tipos específicos de chaves.|  
|[Passo a passo: Exibindo chaves correspondentes](../extensibility/walkthrough-displaying-matching-braces.md)|Mostra como realce de chaves correspondentes.|  
|[Passo a passo: Exibindo Informaçãorápida dicas de ferramenta](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Mostra como exibir pop-ups Informaçãorápida que descrevem os elementos de código, como propriedades, métodos e eventos.|  
|[Passo a passo: Exibindo a Ajuda de assinatura](../extensibility/walkthrough-displaying-signature-help.md)|Mostra como exibir pop-ups que fornecem informações sobre o número e tipos de parâmetros em uma assinatura.|  
|[Walkthrough: Displaying Statement Completion (Passo a passo: exibindo o preenchimento de declaração)](../extensibility/walkthrough-displaying-statement-completion.md)|Mostra como implementar a conclusão de instrução.|  
|[Passo a passo: Implementando trechos de código](../extensibility/walkthrough-implementing-code-snippets.md)|Mostra como implementar a expansão de trecho de código.|  
|[Passo a passo: Exibindo sugestões de lâmpada](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Mostra como exibir as lâmpadas para sugestões de código.|  
|[Passo a passo: Usando um comando de Shell com uma extensão de Editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Mostra como associar um comando de menu em um VSPackage com um componente MEF.|  
|[Passo a passo: Usando uma tecla de atalho com uma extensão de Editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Mostra como associar um atalho de menu em um VSPackage com um componente MEF.|  
|[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Fornece informações sobre o Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/Library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Fornece informações sobre o Windows Presentation Foundation (WPF).|  
  
## <a name="reference"></a>Referência  
 O editor do Visual Studio inclui os seguintes namespaces.  
  
 <xref:Microsoft.VisualStudio.Language.Intellisense></xref:Microsoft.VisualStudio.Language.Intellisense>  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification></xref:Microsoft.VisualStudio.Language.StandardClassification>  
  
 <xref:Microsoft.VisualStudio.Editor></xref:Microsoft.VisualStudio.Editor>  
  
 <xref:Microsoft.VisualStudio.Text></xref:Microsoft.VisualStudio.Text>  
  
 <xref:Microsoft.VisualStudio.Text.Adornments></xref:Microsoft.VisualStudio.Text.Adornments>  
  
 <xref:Microsoft.VisualStudio.Text.Classification></xref:Microsoft.VisualStudio.Text.Classification>  
  
 <xref:Microsoft.VisualStudio.Text.Differencing></xref:Microsoft.VisualStudio.Text.Differencing>  
  
 <xref:Microsoft.VisualStudio.Text.Document></xref:Microsoft.VisualStudio.Text.Document>  
  
 <xref:Microsoft.VisualStudio.Text.Editor></xref:Microsoft.VisualStudio.Text.Editor>  
  
 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods></xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>  
  
 <xref:Microsoft.VisualStudio.Text.Formatting></xref:Microsoft.VisualStudio.Text.Formatting>  
  
 <xref:Microsoft.VisualStudio.Text.IncrementalSearch></xref:Microsoft.VisualStudio.Text.IncrementalSearch>  
  
 <xref:Microsoft.VisualStudio.Text.Operations></xref:Microsoft.VisualStudio.Text.Operations>  
  
 <xref:Microsoft.VisualStudio.Text.Outlining></xref:Microsoft.VisualStudio.Text.Outlining>  
  
 <xref:Microsoft.VisualStudio.Text.Projection></xref:Microsoft.VisualStudio.Text.Projection>  
  
 <xref:Microsoft.VisualStudio.Text.Tagging></xref:Microsoft.VisualStudio.Text.Tagging>  
  
 <xref:Microsoft.VisualStudio.Utilities></xref:Microsoft.VisualStudio.Utilities>
