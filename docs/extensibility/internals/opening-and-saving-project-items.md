---
title: Abrindo e salvando itens de projeto | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
caps.latest.revision: 9
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 38aa636d33b4d7110cfe7bdd9ba097cd1cb49270
ms.lasthandoff: 02/22/2017

---
# <a name="opening-and-saving-project-items"></a>Abrindo e salvando itens de projeto
Quando você adiciona um novo tipo de projeto, você deve gerenciar a abertura e salvar os arquivos de projetos no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE). Os tópicos a seguir abordam as diferentes abordagens para abrir e salvar arquivos.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Exibindo arquivos usando o comando Abrir arquivo](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)  
 Fornece uma explicação passo a passo sobre como o IDE manipula o **abrir arquivo** comando e a função dos projetos na resposta a esse comando.  
  
 [Exibindo arquivos usando o abrir com o comando](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)  
 Fornece uma explicação detalhada, passo a passo sobre como o IDE manipula o **abrir com** comando, solicitando a abertura de um arquivo que tem algumas opções de editores padrão.  
  
 [Como: abrir editores específicos do projeto](../../extensibility/how-to-open-project-specific-editors.md)  
 Fornece instruções passo a passo para especificar que os arquivos de um tipo específico em seu projeto devem ser abertos usando um editor específico do projeto.  
  
 [Como: abrir editores padrão](../../extensibility/how-to-open-standard-editors.md)  
 Fornece instruções passo a passo para especificar como permitir que o IDE abrir um editor padrão para arquivos em seu tipo de projeto.  
  
 [Como: abrir editores para documentos abertos](../../extensibility/how-to-open-editors-for-open-documents.md)  
 Fornece instruções passo a passo para abrir um editor específicas do projeto para um arquivo aberto.  
  
 [Salvar um documento padrão](../../extensibility/internals/saving-a-standard-document.md)  
 Fornece uma explicação detalhada de como o IDE manipula o **salvar**, **Salvar como**, e **Salvar tudo** comandos para um documento aberto em um editor padrão.  
  
 [Salvando um documento personalizado](../../extensibility/internals/saving-a-custom-document.md)  
 Fornece um diagrama e uma explicação detalhada de como o IDE manipula o **salvar**, **Salvar como**, e **Salvar tudo** comandos para documentos abertos em um editor personalizado.  
  
 [Determinando qual Editor abre um arquivo em um projeto](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)  
 Descreve o processo que segue o IDE para selecionar o editor apropriado ou o designer de um arquivo.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Criar Designers e editores personalizados](../../extensibility/creating-custom-editors-and-designers.md)  
 Lista os quatro tipos de editores que o IDE pode hospedar e fornece descrições de cada editor.  
  
 [Tipos de projeto](../../extensibility/internals/project-types.md)  
 Discute como projetos de controle de forma que o código é compilado e criado, como editores são abertos e como os itens de projeto são formatados.
