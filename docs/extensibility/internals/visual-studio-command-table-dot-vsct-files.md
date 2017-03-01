---
title: Tabela de comando do Visual Studio (. Arquivos VSCT) | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ce98f8730dcb5465fff2278b9f24d494676390bd
ms.lasthandoff: 02/22/2017

---
# <a name="visual-studio-command-table-vsct-files"></a>Tabela de comando do Visual Studio (. Arquivos de VSCT)
Um arquivo de configuração da tabela de comando é um arquivo de texto que descreve o conjunto de comandos que contém um VSPackage. O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comando compilador de tabela (VSCT) compila a configuração baseada em XML (arquivos. VSCT) nos arquivos de saída (.cto) de tabela do comando binário. Os arquivos resultantes .cto são iguais às que são criadas usando o compilador de tabela (CTC) do comando para compilar os arquivos de configuração .ctc. No entanto, arquivos. VSCT baseado em XML tem algumas vantagens, como um editor de XML e XML IntelliSense.  
  
 Para saber mais sobre a sintaxe e semântica de arquivos. VSCT, consulte [criar tabela de comando XML (. Arquivos de VSCT)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## <a name="in-this-section"></a>Nesta seção  
 [Criar tabela de comando XML (. Arquivos de VSCT)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 Descreve como criar arquivos. VSCT.  
  
 [Como: criar um. Arquivo VSCT](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 Compara os métodos para criar um arquivo. VSCT. Descreve o processo de criação manual de um novo arquivo. VSCT.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Referência de esquema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)  
 Fornece detalhes sobre cada seção do arquivo de configuração do comando tabela XML.  
  
 [Configuração da tabela de comando (. Arquivos CTC)](http://msdn.microsoft.com/en-us/3413dda1-f372-4669-bcf0-c64d3463842c)  
 Apresenta uma visão geral do formato de arquivo .ctc preterido.  
  
 [Como os VSPackages adicionar elementos de Interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Descreve a especificação de formato de tabela do comando.  
  
 [Recursos em VSPackages](../../extensibility/internals/resources-in-vspackages.md)  
 Descreve como usar os recursos gerenciados e não gerenciados em VSPackages gerenciados.  
  
 [Barras de ferramentas, Menus e comandos](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Explica como criar uma interface do usuário que inclui menus, barras de ferramentas e caixas de combinação de comando.
