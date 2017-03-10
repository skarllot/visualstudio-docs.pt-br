---
title: "How to: Edit XML Files | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Edit XML Files
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O editor XML é o novo editor para arquivos XML.  Ele pode ser usado em um arquivo XML independente, ou em um arquivo associado a um projeto o Visual Studio.  O Editor de XML está associado às seguintes extensões de arquivo: .config, .dtd, .xml, .xsd, .xdr, .xsl, .xslt e .vssettings.  O Editor de XML também está associado a qualquer outro tipo de arquivo que não tenha nenhum editor específico registrado e que contenha o conteúdo XML ou DTD.  
  
> [!NOTE]
>  Os documentos XHTML são tratados pelo Editor de HTML.  
  
### Para editar um arquivo XML  
  
1.  Clique duas vezes no arquivo que você deseja editar.  
  
### Para adicionar um novo arquivo XML a um projeto  
  
1.  No menu **Projeto**, selecione **Adicionar Novo Item**.  
  
2.  Selecione **Arquivo XML** no painel **Modelos**.  
  
3.  Digite o nome do arquivo no campo **Nome** e pressione **Adicionar**.  
  
     O arquivo XML é adicionado ao projeto e aberto no Editor de XML.  O arquivo contém a declaração XML padrão, `<?xml version="1.0" encoding="utf-8" ?>`.  
  
### Para adicionar um arquivo XML existente a um projeto  
  
1.  No menu **Projeto**, selecione **Adicionar Item Existente**.  
  
     A caixa de diálogo **Adicionar Item Existente** é exibida.  
  
2.  Selecione um arquivo XML e pressione **Adicionar**.  
  
### Para criar um novo arquivo XML ou XSLT  
  
1.  No menu **Arquivo**, selecione **Novo**.  
  
     A caixa de diálogo **Novo Arquivo** aparece.  
  
2.  Selecione **Arquivo XML** para criar um novo arquivo XML; ou selecione **Arquivo XSLT** para criar uma nova folha de estilos XSLT.  
  
3.  Clique em **Abrir**.  
  
### Para criar um projeto para arquivos XML  
  
1.  No menu **Arquivo**, selecione **Novo** e selecione **Projeto**.  
  
     A caixa de diálogo **Novo Projeto** é exibida.  
  
2.  Selecione a linguagem de código de sua escolha, selecione **Projeto Vazio** e clique em **OK**.  
  
3.  Adicionar arquivos XML ao projeto.  
  
     O Editor de XML localiza os esquemas que você adiciona a esse projeto e os usa para validação e IntelliSense em qualquer XML, esquema ou arquivos XSLT que você editar quando o projeto for aberto.  
  
## Consulte também  
 [XML Editor](../xml-tools/xml-editor.md)   
 [XML Document Properties, Properties Window](../xml-tools/xml-document-properties-properties-window.md)   
 [How to: Create an XML Schema from an XML Document](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)