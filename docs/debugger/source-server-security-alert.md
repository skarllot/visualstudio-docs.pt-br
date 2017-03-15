---
title: "Alerta de seguran&#231;a do servidor de origem | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.sourceserver.enablewarning"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Alerta de seguran&#231;a do servidor de origem
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ao usar o Servidor de Origem, use somente os arquivos de símbolo que forem de um local conhecido e confiável.  
  
 Este aviso aparece quando você ativa o suporte do servidor de origem.  Os comandos do servidor de origem são inseridos nos arquivos de símbolo de depuração \(arquivos de PDB\).  Verifique se você sabe de onde vêm seus arquivos PDB.  
  
> [!IMPORTANT]
>  As seguintes riscos de segurança devem ser levadas em consideração ao usar o servidor de origem: os comandos arbitrários podem ser inseridos no arquivo de PDB do aplicativo, de forma que você coloque somente aqueles que você deseja executar no arquivo de srcsrv.ini.  Qualquer tentativa de executar um comando que não seja no arquivo srcsvr.ini fará com que uma caixa de diálogo de confirmação apareça.  Para obter mais informações, consulte [Aviso de segurança: o depurador deve executar o comando não confiável](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Nenhuma validação é feita em parâmetros de comando, portanto, tenha cuidado com comandos confiáveis.  Por exemplo, se você confiar no cmd.exe, um usuário mal\-intencionado pode especificar parâmetros que tornariam o comando perigoso.  
  
## Consulte também  
 [Especificar arquivos de símbolo \(.pdb\) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Segurança do depurador](../debugger/debugger-security.md)   
 [servidor de origem](http://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)