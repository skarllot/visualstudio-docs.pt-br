---
title: "Aviso de seguran&#231;a: o depurador deve executar o comando n&#227;o confi&#225;vel | Microsoft Docs"
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
  - "vs.debug.sourceserver.securityalert"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Aviso de seguran&#231;a: o depurador deve executar o comando n&#227;o confi&#225;vel
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta caixa de diálogo de aviso aparece quando você estiver usando o servidor de origem.  Indica que o comando que o depurador precisa executar para obter o código\-fonte não está na lista de comandos confiáveis para o servidor de origem contido no arquivo srcsvr.ini.  Se esse for um comando válido, você poderá adicioná\-lo ao arquivo srcsvr.ini.  Caso contrário, você não deverá executá\-lo.  Para obter mais informações, consulte [Especificar arquivos de símbolo \(.pdb\) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## Texto da mensagem  
 O depurador deve executar o seguinte comando não confiável para obter o código fonte do servidor de origem.  
  
 Se o arquivo de símbolo de depuração \(\*.pdb\) não for de uma origem conhecida e confiável, a execução deste comando pode ser inválida ou perigosa.  
  
 Você deseja executar este comando?  
  
## Lista UIElement  
 Caixa de Texto  
 Comando do arquivo de .pdb a ser executado.  
  
 Executar  
 Permita a execução do comando.  
  
 Não execute  
 Interromper a execução de comando e fazer download do arquivo do servidor de origem.  
  
## Consulte também  
 [Especificar arquivos de símbolo \(.pdb\) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Segurança do depurador](../debugger/debugger-security.md)   
 [servidor de origem](http://msdn.microsoft.com/library/windows/desktop/ms680641\(v=vs.85\).aspx)