---
title: Gerenciar ferramentas externas | Microsoft Docs
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- Create GUID tool
- RC (Resource Compiler)
- ReBase tool
- Windows NT Message Compiler
- Windows NT C++ Symbol Undecorator
- tstcon32.exe
- Type Library Generator
- Windows NT Image Binder
- tools [Visual Studio], external
- RowsetViewer tool
- utilities, external tools
- Local Test Manager
- OLE DB Rowset Viewer
- Midlc (IDL Compiler)
- ATL Trace Tool
- Odbcte32w.exe
- IDL Compiler
- HCW (Help Workshop)
- Message Compiler [Visual Studio]
- UUID Generator
- MIDL, external tools
- ErrLook tool
- MAKEHM tool
- Error lookup tool
- OLEVIEW (Object Viewer)
- Uuidgen.exe
- WebDbg tool
- OLE/COM Object Viewer
- LTM (Local Test Manager)
- ATLTraceTool.exe
- Bind tool
- Vsvars32.bat
- external tools [Visual Studio]
- ODBC Test
- Windows NT Image Rebaser
- undname.exe
- Vcspawn.exe
- ActiveX Control Test Container
- mc (Message Compiler)
- GUIDGEN tool
- Odbcte32.exe
- DisableMsg tool
- MkTypLib tool
- Help Workshop
- Resource Compiler
ms.assetid: f382fd40-a98f-4934-8c9a-5aeae881acde
caps.latest.revision: 38
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 1d273749cc41eb975dc9f93329edf9a57aaae09a
ms.contentlocale: pt-br
ms.lasthandoff: 05/24/2017

---
# Gerenciar ferramentas externas
<a id="manage-external-tools" class="xliff"></a>
Você pode chamar ferramentas externas de dentro do Visual Studio usando o menu **Ferramentas**. Algumas ferramentas padrão estão disponíveis no menu **Ferramentas**, mas é possível adicionar outros executáveis de sua preferência.  

## Ferramentas disponíveis no menu das Ferramentas do Visual Studio
<a id="tools-available-on-the-visual-studio-tools-menu" class="xliff"></a>
 O menu **Ferramentas** contém vários comandos internos, como:

*  **Extensões e Atualizações** para [gerenciamento de Extensões do Visual Studio](finding-and-using-visual-studio-extensions.md)
*  **Gerenciador de Trechos de Código...** para [organizar Trechos de Código](code-snippets.md#code-snippet-manager)
*  **Proteção Preemptiva - Dotfuscator** para iniciar o [Dotfuscator Community Edition (CE)](dotfuscator/index.md) se ele estiver [instalado](dotfuscator/install.md)
*  **Personalizar...** para [personalizar menus e barras de ferramentas](how-to-customize-menus-and-toolbars-in-visual-studio.md)
*  **Opções...** para [configurar uma variedade de opções diferentes para o IDE do Visual Studio e outras ferramentas](reference/options-dialog-box-visual-studio.md)

## Adicionar novas ferramentas ao menu Ferramentas
<a id="add-new-tools-to-the-tools-menu" class="xliff"></a> 
 É possível adicionar uma ferramenta externa ao menu **Ferramentas**. Abra a caixa de diálogo **Ferramentas Externas...**, clique em **Adicionar** e, em seguida, preencha as informações. Por exemplo, a seguinte entrada faz com que o Windows Explorer abra o diretório do arquivo atualmente aberto no Visual Studio:  
  
1.  Título: *Abrir local do arquivo*
  
2.  Comando: `explorer.exe`  
  
3.  Argumentos: `/root, "$(ItemDir)"`  
  
 Esta é uma lista completa de argumentos que podem ser usados ao definir uma ferramenta externa.
  
> [!NOTE]
>  A barra de status do IDE exibe as variáveis Linha atual e Coluna atual para indicar a localização do ponto de inserção no Editor de Código ativo. A variável Texto atual retorna o texto ou o código selecionado nesse local.  
  
|Nome|Argumento|Descrição|  
|----------|--------------|-----------------|  
|Caminho do item|$(ItemPath)|O nome de arquivo completo do arquivo atual (unidade + caminho + nome de arquivo).|  
|Diretório do item|$(ItemDir)|O diretório do arquivo atual (unidade + caminho).|  
|Nome de Arquivo do Item|$(ItemFilename)|O nome de arquivo do arquivo atual (nome de arquivo).|  
|Extensão de item|$(ItemExt)|A extensão de nome de arquivo do arquivo atual.|  
|Linha atual|$(CurLine)|A posição da linha atual do cursor na janela de código.|  
|Coluna atual|$(CurCol)|A posição da coluna atual do cursor na janela de código.|  
|Texto atual|$(CurText)|O texto selecionado.|  
|Caminho de destino|$(TargetPath)|O nome de arquivo completo do item a ser criado (unidade + caminho + nome de arquivo).|  
|Diretório de Destino|$(TargetDir)|O diretório do item a ser criado.|  
|Nome de Destino|$(TargetName)|O nome de arquivo do item a ser criado.|  
|Extensão de Destino|$(TargetExt)|A extensão de nome de arquivo do item a ser criada.|  
|Diretório binário|$(BinDir)|O local final do binário que está sendo criado (definido como unidade + caminho). Por exemplo: **\\...\My Documents\Visual Studio \<Versão>\\<ProjectName\>\bin\debug**|  
|Diretório do Projeto|$(ProjDir)|O diretório do projeto atual (unidade + caminho).|  
|Nome do arquivo de projeto|$(ProjFileName)|O nome de arquivo do projeto atual (unidade + caminho + nome de arquivo).|  
|Diretório da solução|$(SolutionDir)|O diretório da solução atual (unidade + caminho).|  
|Nome de arquivo da solução|$(SolutionFileName)|O nome de arquivo da solução atual (unidade + caminho + nome de arquivo).|  

## Consulte também
<a id="see-also" class="xliff"></a>  
 [Ferramentas de build do C/C++](/cpp/build/reference/c-cpp-build-tools)

