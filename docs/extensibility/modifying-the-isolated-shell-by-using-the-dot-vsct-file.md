---
title: Modificando o Shell isolado usando o. Arquivo VSCT | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: 8
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
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: a20b546c6e8d6d70a17d3d0bae575a5b2898d781
ms.lasthandoff: 02/22/2017

---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>Modificando o Shell isolado usando o. Arquivo VSCT
O projeto de interface do usuário para um projeto do Visual Studio shell isolado contém um arquivo. VSCT que permite que você especifique quais grupos de aplicativos e comandos individuais estão disponíveis no aplicativo. A seguir está um trecho de um arquivo. VSCT sem modificações.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 Por padrão, a maioria dos comandos e grupos de comando são incluídos. Para excluir um comando ou um grupo de comandos, simplesmente remova esse comando ou grupo.  
  
 Por exemplo, para remover o próximo painel e os comandos anteriores do painel, remova o `No_PaneNextPaneCommand` e `No_PanePrevPaneCommand` entradas:  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 Para mais obter exemplo essas personalizações, consulte [passo a passo: Criando um aplicativo de Shell isolado básico](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="referenced-files"></a>Arquivos referenciados  
 O arquivo. VSCT de padrão para um aplicativo referencia os arquivos a seguir. Esses arquivos estão localizados no subdiretório \VisualStudioIntegration\Common\Inc\ do diretório de instalação do SDK do Visual Studio.  
  
|Arquivo|Descrição|  
|----------|-----------------|  
|wbids.h|Identidades de interface do usuário para o pacote da Web procurar.|  
|AppIDCmdUsed.vsct|Tabela de comando para os principais elementos de IU do Visual Studio.|  
|EmulatorCmdUsed.vsct|Tabela de comando de editores Emacs e Brief elementos de interface do usuário de emulação do editor.|  
|Vsdebugguids.h|Define os GUIDs dos comandos, página de opções e outros recursos do depurador do Visual Studio.|  
|VsDbgCmdUsed.vsct|Tabela de comando do depurador.|  
  
 O arquivo AppIDCmdUsed.vsct inclui elementos de IU do Visual Studio com base nos símbolos definidos no arquivo VSCT do aplicativo.  
  
 Para obter mais informações, consulte [criar tabela de comando XML (. Arquivos VSCT)](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md) e [referência de esquema XML VSCT](../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="see-also"></a>Consulte também  
 [Visual Studio isolada Shell](../extensibility/visual-studio-isolated-shell.md)
