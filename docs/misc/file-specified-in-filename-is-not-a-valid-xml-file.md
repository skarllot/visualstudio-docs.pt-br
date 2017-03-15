---
title: "Arquivo especificado no nome do arquivo n&#227;o &#233; um arquivo XML v&#225;lido | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Arquivo especificado no nome do arquivo n&#227;o &#233; um arquivo XML v&#225;lido
O nome do arquivo que você forneceu não é um arquivo XML válido. Para especificar a estrutura permitida e o conteúdo de um documento XML, você pode usar uma definição de tipo de documento \(DTD\), um esquema de Microsoft XML\-Data Reduced \(XDR\) ou um esquema de linguagem XSD de definição de esquema XML. Esquemas XSD são a melhor maneira de especificar gramáticas XML no [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
> [!NOTE]
>  Em algumas versões anteriores do Visual Studio, o **XML Designer** é o designer para datasets digitados e esquema XML. O **XML Designer** ainda pode ser usado para criar e editar arquivos de esquema XML. No entanto, em [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)], o designer para criar e editar conjuntos de dados tipados é o **Dataset Designer**. Para obter mais informações, consulte [Criando e editando conjuntos de dados tipados](../data-tools/creating-and-editing-typed-datasets.md).  
  
### Para corrigir este erro  
  
-   Verifique se você está fornecendo o nome de arquivo correto.  
  
-   Verifique se o arquivo especificado contém XML válido ao carregar o arquivo XML que você deseja verificar para o **XML Designer**. Do **XML** menu, clique em **Validar XML**. Erros são exibidos no **lista de tarefas**.  
  
-   Se o arquivo XML tem um esquema XML associado, verifique se os elementos aparecem na estrutura definida e que o conteúdo dos elementos individuais em conformidade com os tipos de dados declarados especificados no esquema.  
  
## Consulte também  
 <xref:System.Xml>   
 [Como analisar caminhos de arquivo](../Topic/How%20to:%20Parse%20File%20Paths%20in%20Visual%20Basic.md)