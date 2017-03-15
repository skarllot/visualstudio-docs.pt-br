---
title: "Como salvar e abrir arquivos com codificação | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Unicode, bi-directional language support
- files, encoding
- bi-directional language support, encoded files
- file encoding, bi-directional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
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
ms.openlocfilehash: 6b0b95bfd2112383229c6a36ee7b9c6cdab827eb
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-save-and-open-files-with-encoding"></a>Como salvar e abrir arquivos com codificação
É possível salvar arquivos com uma codificação de caracteres específica para dar suporte a idiomas bidirecionais. Também é possível especificar uma codificação ao abrir um arquivo, para que o Visual Studio exiba o arquivo corretamente.  
  
### <a name="to-save-a-file-with-encoding"></a>Para salvar um arquivo com codificação  
  
1.  No menu **Arquivo**, escolha **Salvar Arquivo Como** e clique no botão suspenso ao lado do botão **Salvar**.  
  
     A caixa de diálogo **Opções de Salvamento Avançadas** é exibida.  
  
2.  Em **Codificação**, selecione a codificação a ser usada para o arquivo.  
  
3.  Opcionalmente, em **Terminações de linha**, selecione o formato para caracteres de final de linha.  
  
     Essa opção é útil se você pretende trocar o arquivo com usuários de outro sistema operacional.  
  
     Se deseja trabalhar com um arquivo que você sabe que está codificado de uma maneira específica, é possível informar ao Visual Studio para usar essa codificação ao abrir o arquivo. O método usado dependerá se o arquivo faz parte do projeto.  
  
### <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>Para abrir um arquivo codificado que faz parte de um projeto  
  
1.  Em **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo e escolha **Abrir Com**.  
  
2.  Na caixa de diálogo **Abrir Com**, escolha o editor com o qual o arquivo será aberto.  
  
     Muitos editores do Visual Studio, como o editor de formulários, detectarão a codificação automaticamente e abrirão o arquivo de forma adequada. Se você escolher um editor que permite escolher uma codificação, a caixa de diálogo **Codificação** será exibida.  
  
3.  Na caixa de diálogo **Codificação**, selecione a codificação que o editor deverá usar.  
  
### <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>Para abrir um arquivo codificado que não faz parte de um projeto  
  
1.  No menu **Arquivo**, aponte para **Abrir**, escolha **Arquivo** ou **Arquivo da Web** e, em seguida, selecione o arquivo a ser aberto.  
  
2.  Clique no botão suspenso ao lado do botão **Abrir** e escolha **Abrir Com**.  
  
3.  Siga as Etapas 2 e 3 do procedimento anterior.  
  
## <a name="see-also"></a>Consulte também  
 [Codificação e globalização do Windows Forms](http://msdn.microsoft.com/Library/22e8965d-a712-42b3-8167-3ee346bd70f9)   
 [Globalizando e localizando aplicativos](../ide/globalizing-and-localizing-applications.md)
