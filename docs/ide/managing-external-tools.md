---
title: Gerenciar ferramentas externas | Microsoft Docs
ms.custom: 
ms.date: 01/23/2017
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
translationtype: Human Translation
ms.sourcegitcommit: 66e09a22bcedb37f82eb9517a8f9d4affbe3a374
ms.openlocfilehash: ad9461bb29dba3e8e2ffe242c1f709587729ce22
ms.lasthandoff: 02/22/2017

---
# <a name="manage-external-tools"></a>Gerenciar ferramentas externas
É possível chamar ferramentas externas no Visual Studio. Algumas ferramentas padrão estão disponíveis no menu **Ferramentas**, mas é possível adicionar outros executáveis de sua preferência.  
  
## <a name="tools-available-on-the-visual-studio-tools-menu"></a>Ferramentas disponíveis no menu das Ferramentas do Visual Studio
 É possível chamar as ferramentas a seguir no menu **Ferramentas** em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Você também pode chamá-las pelo nome na janela **Início Rápido**. Por exemplo, para chamar GuidGen.exe, digite **Criar GUID**.  
  
1.  Criar GUID: gera um GUID.  
  
2.  Pesquisa de Erro: obtém uma mensagem de erro do valor inserido. Para obter mais informações, consulte [Referência de ERRLOOK](/visual-cpp/build/reference/errlook-reference).  
  
3.  Ferramenta de Rastreamento da ATL/MFC: mostra mensagens de rastreamento de depuração nas fontes ATL e MFC.  
  
4.  PreEmptive Dotfuscator e Análise: protege os programas .NET contra a engenharia reversa.  
  
5.  SPY++: exibe processos, threads, janelas e mensagens de janela graficamente.  
  
6.  Editor de Configuração do serviço WCF: permite criar e modificar definições de configuração para os serviços WCF.  
  
> [!WARNING]
>  Você poderá ver uma lista diferente de ferramentas externas, dependendo de qual edição do Visual Studio está instalada e o perfil de configurações aplicado. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="add-new-tools-to-the-tools-menu"></a>Adicionar novas ferramentas ao menu Ferramentas 
 É possível adicionar uma ferramenta externa ao menu **Ferramentas**. Abra a caixa de diálogo **Ferramentas Externas**, clique em **Adicionar** e, em seguida, preencha as informações. Por exemplo, a seguinte entrada faz com que o Windows Explorer abra o diretório do arquivo atualmente aberto no Visual Studio:  
  
1.  Título: Abrir local do arquivo  
  
2.  Comando: explorer.exe  
  
3.  Argumentos: /root, "$(ItemDir)"  
  
## <a name="arguments-for-external-tools"></a>Argumentos para ferramentas externas  
 Os argumentos a seguir são variáveis do Visual Studio atribuídas ao iniciar uma ferramenta externa. Links para ferramentas externas, como Bloco de notas ou Spy++, podem estar listados no menu **Ferramentas** com a caixa de diálogo Ferramentas Externas.  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Ferramentas de build do C/C++](/visual-cpp/build/reference/c-cpp-build-tools)

