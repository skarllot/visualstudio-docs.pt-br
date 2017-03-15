---
title: "Caixa de diálogo Configurações Internacionais, Ambiente, Opções | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Environment.InternationalSettings
- VS.ToolsOptionsPages.Environment.International_Settings
- VS.Environment.International Settings
- VS.ToolsOptionsPag.Environment.International_Settings
helpviewer_keywords:
- International Settings dialog box
- languages, environment settings
- Options dialog box, international settings
- languages, specifying default
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
caps.latest.revision: 14
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 275a397a2c14611108602ca27cb2bd66c0532b78
ms.lasthandoff: 02/22/2017

---
# <a name="international-settings-environment-options-dialog-box"></a>Caixa de diálogo Configurações Internacionais, Ambiente, Opções
A página Configurações Internacionais permite alterar o idioma padrão quando você tem mais de uma versão de idioma do IDE (ambiente de desenvolvimento integrado) instalada em seu computador. Você pode acessar essa caixa de diálogo selecionando **Opções** no menu **Ferramentas** e, em seguida, escolhendo **Configurações Internacionais** na pasta **Ambiente**. Se essa página não aparecer na lista, selecione **Mostrar todas as configurações** na caixa de diálogo **Opções**.  
  
> [!NOTE]
>  As opções disponíveis nas caixas de diálogo e os nomes os locais dos comandos de menu que você vê podem diferir do que é descrito na Ajuda, dependendo de suas configurações ativas ou da edição. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 **Linguagem**  
 Lista os idiomas disponíveis para as versões de idioma do produto instalado. Essa opção ficará não disponível a menos que você tenha mais de uma versão de idioma instalada no computador. Se vários idiomas de produtos ou uma instalação de idioma misto dos produtos compartilhar o ambiente, a seleção de idioma será alterada para **Usar o idioma do Microsoft Windows**.  
  
> [!CAUTION]
>  Em um sistema com vários idiomas instalados, as ferramentas de build do Visual C++ (cl.exe, link.exe, nmake.exe, bscmake.exe e arquivos relacionados) não são afetadas por essa configuração. Essas ferramentas usam a versão do último idioma instalado, e as ferramentas do idioma instalado anteriormente são substituídas porque as ferramentas de build do Visual C++ não usam o modelo DLL satélite.  
  
## <a name="see-also"></a>Consulte também  
 [Instalando várias versões de idioma do Visual Studio](../Topic/Installing%20Multiple%20Language%20Versions%20of%20Visual%20Studio.md)   
 [Caixa de diálogo Opções do Ambiente](../../ide/reference/environment-options-dialog-box.md)
