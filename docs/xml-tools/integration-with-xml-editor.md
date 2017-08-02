---
title: "Integration with XML Editor | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
caps.latest.revision: 3
caps.handback.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Integration with XML Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O designer de esquema XML está integrado com o editor XML.  Se você alterar um arquivo XSD no editor XML, a alteração será refletida em [XML Schema Explorer](../xml-tools/xml-schema-explorer.md).  Se você tiver [O modo de gráfico](../xml-tools/graph-view.md) ou [O modo do modelo de conteúdo](../xml-tools/content-model-view.md) aberto, a alteração será refletida também lá.  Você pode navegar entre o designer de esquema XML e o editor XML das seguintes maneiras:  
  
-   No editor XML, clique com o botão direito do mouse em um nó e selecione **Apresentação em XML Schema Explorer**.  
  
-   No modo de gráfico e o XML Schema Explorer, clique duas vezes em um nó, ou clique com o botão direito do mouse em um nó e selecione **Exibir Código**.  No modo do modelo de conteúdo, clique com o botão direito do mouse em um nó e selecione **Exibir Código**.  
  
 A captura de tela a seguir mostra um esquema XML aberto em XML Schema Explorer.  XML Schema Explorer exibe o esquema definido em um modo de exibição de árvore.  O editor XML exibe a exibição do texto do nó que está atualmente ativa em XML Schema Explorer.  
  
 ![XSDDesignerWithXMLEditor](~/xml-tools/media/xsddesignerwithxmleditor.gif "XSDDesignerWithXMLEditor")  
  
 Às vezes é útil consulte o código no editor XML e no designer gráfico lado a lado.  Para exibir ao mesmo tempo ambos os arquivos, clique com o botão direito do mouse em qualquer lugar no editor XML e selecione **Exibir Designer**.  No menu do Visual Studio Windows, **Novo grupo \(horizontal ou vertical\) da guia**.  
  
 ![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif "XSDDesignerWithXMLEditorAndCMV")  
  
## Consulte também  
 [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)