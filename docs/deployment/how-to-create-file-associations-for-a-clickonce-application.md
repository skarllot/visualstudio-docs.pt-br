---
title: "Como criar associa&#231;&#245;es de arquivo para um aplicativo ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "implantação ClickOnce, associações de arquivos"
  - "associações de arquivos, Aplicativos ClickOnce"
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como criar associa&#231;&#245;es de arquivo para um aplicativo ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]aplicativos podem ser associados um ou mais extensões de nome de arquivo, para que o aplicativo será iniciado automaticamente quando o usuário abre um arquivo desses tipos.  A adição de suporte de extensão de nome de arquivo para um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo é simples.  
  
### Criar associações de arquivo para um aplicativo de ClickOnce  
  
1.  Criar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo normalmente, ou usar as existentes [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.  
  
2.  Abra o manifesto do aplicativo com um editor de texto ou XML, como o bloco de notas.  
  
3.  Encontrar o `assembly` elemento.  Para obter mais informações, consulte [Manifesto de aplicativo ClickOnce](../deployment/clickonce-application-manifest.md).  
  
4.  Como um filho do `assembly` elemento, adicione um `fileAssociation` elemento.  O `fileAssociation` elemento possui quatro atributos:  
  
    -   `extension`: A extensão de nome de arquivo que você deseja associar com o aplicativo.  
  
    -   `description`: Uma descrição do tipo de arquivo, que aparecerá no shell do Windows.  
  
    -   `progid`: Uma seqüência de caracteres que identifica o tipo de arquivo, para marcá\-lo no registro.  
  
    -   `defaultIcon`: Um ícone a ser usado para esse tipo de arquivo.  O ícone deve ser adicionado como um recurso de arquivo no manifesto do aplicativo.  Para obter mais informações, consulte [Como incluir um arquivo de dados em um aplicativo ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Para obter um exemplo de `file` e `fileAssociation` elementos, consulte [Elemento \<fileAssociation\>](../deployment/fileassociation-element-clickonce-application.md).  
  
5.  Se você deseja associar mais de um tipo de arquivo com o aplicativo, adicionar adicional `fileAssociation` elementos.  Observe que o `progid` atributo deve ser diferente para cada um.  
  
6.  Quando tiver concluído com o manifesto de aplicativo, assinar novamente o manifesto.  Você pode fazer isso partir da linha de comando usando o Mage.  
  
     `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
     Para mais informações, consulte: [Mage.exe \(Ferramenta de Geração e Edição de Manifesto\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md).  
  
## Consulte também  
 [Elemento \<fileAssociation\>](../deployment/fileassociation-element-clickonce-application.md)   
 [Manifesto de aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Mage.exe \(Ferramenta de Geração e Edição de Manifesto\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)