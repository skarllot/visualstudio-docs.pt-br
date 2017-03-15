---
title: "How to: Execute an XSLT Transformation from the XML Editor | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Execute an XSLT Transformation from the XML Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O editor XML permite que você associe uma folha de estilos XSLT com um documento XML, execute a transformação, e exibe a saída.  A saída resultante de transformação XSLT são exibidas em uma nova janela do documento.  
  
 A propriedade de **Saída** especifica o nome de arquivo para saída.  Se a propriedade de **Saída** está em branco, um nome de arquivo é gerado no diretório temporário.  A extensão de arquivo é baseado no elemento de `xsl:output` na folha de estilos e pode ser .xml, .txt ou .htm.  
  
 Se a propriedade de **Saída** especifica um nome de arquivo com uma extensão de .htm ou de .html, a saída de fonte são visualizadas usando [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Internet Explorer.  Todas as extensões de arquivo restantes é aberto usando o editor padrão escolhido por [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Visual Studio.  Por exemplo, se a extensão de arquivo é .xml, o Visual Studio usa o editor XML.  
  
### Para executar uma transformação XSLT de um documento XML  
  
1.  Abrir um documento XML no editor XML.  
  
2.  Associar uma folha de estilos XSLT com o documento XML.  
  
    -   Adicione uma instrução de processamento de `xml-stylesheet` para o documento XML.  Por exemplo, adicione a seguinte linha `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` ao prólogo do documento.  
  
         \-ou\-  
  
    -   Adicione a folha de estilos XSLT usando a janela de **Propriedades** .  No documento **Janela de propriedades**, clique no botão de **Procurar** para o campo de **Folha de Estilos** , selecione a folha de estilos XSLT, e clique **Abrir**.  
  
3.  Clique no botão de **Mostrar Saída XSL** na barra de ferramentas **Editor de XML** .  
  
    > [!NOTE]
    >  Se não houver nenhuma folha de estilos associada com o documento XML, avisos de uma caixa de diálogo você fornecer a folha de estilos ao uso.  
    >   
    >  A saída resultante de transformação XSLT são exibidas em uma nova janela do documento.  
  
### Para executar uma transformação XSLT de uma folha de estilos XSLT  
  
1.  Abra uma folha de estilos XSLT no editor XML.  
  
2.  Especificar um documento XML no campo de **Entrada** da janela de **Propriedades** do documento.  
  
    > [!NOTE]
    >  O documento XML é o documento de entrada usado para a transformação.  Se um documento não é especificado quando a transformação XSLT é iniciada, a caixa de diálogo aparece **Abrir Arquivo** , e você pode especificar um documento no momento.  
  
3.  Clique no botão de **Mostrar Saída XSLT** na barra de ferramentas **Editor de XML** .  
  
     A saída resultante de transformação XSLT são exibidas em uma nova janela do documento.  
  
### Para fornecer um nome de arquivo diferente de saída  
  
1.  Especifique um nome de arquivo no campo de **Saída** da janela de **Propriedades** do documento.  
  
2.  Clique no botão de **Mostrar Saída XSLT** na barra de ferramentas **Editor de XML** .  
  
     A saída resultante de transformação XSLT são exibidas em uma nova janela de documento e o editor usado na janela de saída depende da extensão de arquivo da propriedade de documento de **Saída** .  
  
## Consulte também  
 [XML Editor](../xml-tools/xml-editor.md)