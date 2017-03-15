---
title: "Página Opções, Propriedades do Nó de Fontes e Cores | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tools Options settings, Fonts and Colors node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
caps.latest.revision: 8
author: kempb
ms.author: kempb
manager: ghogen
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
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: b54f38aa51904ca502ab7298359fdc7124a807a9
ms.lasthandoff: 02/22/2017

---
# <a name="options-page-fonts-and-colors-node-properties"></a>Página de Opções, Fontes e Cores, Propriedades de Nó
Este documento descreve as propriedades de fonte e de cor de uma janela de ferramentas registrada para ser exibida em **Fontes e Cores** na categoria **Ambiente** da caixa de diálogo **Opções**. Isso dá suporte à natureza dinâmica de grupos de itens de coloração, que poderão ser alterados se os VSPackages forem instalados ou desinstalados.  
  
 A seção a seguir mostra um exemplo de um tipo de janela registrada e as propriedades disponíveis para cada janela.  
  
## <a name="text-editor-or-printer-or-dialogs-and-tool-windows"></a>Editor de Texto, impressora ou caixas de diálogo e janelas de ferramentas  
 `DTE.Properties("FontsAndColors", "TextEditor")`  
  
 -ou-  
  
 `DTE.Properties("FontsAndColors", "Printer")`  
  
 -ou-  
  
 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`  
  
|Nome do item de propriedade|Valor|Descrição|  
|------------------------|-----------|-----------------|  
|FontFamily|Get/Set (Cadeia de Caracteres)|O nome da fonte a ser usado, como “Courier New”.|  
|FontCharacterSet|Get/Set (<xref:EnvDTE.vsFontCharSet>)|Um valor <xref:EnvDTE.vsFontCharSet>, que especifica o tipo de conjunto de caracteres a ser usado, como hebraico ou russo.|  
|FontSize|Get/Set (Curto)|O tamanho da fonte a ser usado, em pontos. Por exemplo, 10 ou 12.|  
  
## <a name="see-also"></a>Consulte também  
 [Controlando configurações de opções](http://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)   
 [Determinando os nomes de itens de propriedades em páginas de opções](http://msdn.microsoft.com/Library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)   
 [Página Opções, Propriedades do Nó de Ambiente](../../ide/reference/options-page-environment-node-properties.md)   
 [Página de Opções, Propriedades do Nó de Editor de Texto](../../ide/reference/options-page-text-editor-node-properties.md)
