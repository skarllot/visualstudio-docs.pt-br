---
title: "Depurando um controle ActiveX com liga&#231;&#227;o de dados | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Controles ActiveX, depuração"
  - "controles [Visual Studio], ActiveX"
  - "controles associados a dados, ActiveX"
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depurando um controle ActiveX com liga&#231;&#227;o de dados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se você estiver desenvolvendo um controle ActiveX que será associado a um controle da fonte de dados, poderá criar seu próprio aplicativo de contêiner e usar esse contêiner para depurar o controle ActiveX.  
  
 Por exemplo, você pode criar um aplicativo MFC baseado em diálogo e colocar o controle associado a dados e um controle da fonte de dados na caixa de diálogo.  Você pode usar esse aplicativo MFC para teste de tempo de execução e como o executável do contêiner para depurar seu controle ActiveX associado a dados.  
  
## Usando o contêiner de teste  
 Se você quiser um contêiner que possa modificar facilmente para dar suporte a várias interfaces no controle ou no contêiner, use o contêiner de teste ActiveX como o executável para a sessão de depuração.  No contêiner de teste ActiveX, clique em **Opções** no menu **Contêiner** para habilitar várias interfaces.  Para obter mais informações, consulte [Testando propriedades e eventos com contêiner de teste](/visual-cpp/mfc/testing-properties-and-events-with-test-container).  
  
 Se você precisar entrar no código do contêiner enquanto está depurando, use a versão de depuração do contêiner ou use a versão de depuração do contêiner de teste ActiveX.  Para obter mais informações, consulte [TSTCON Sample: ActiveX Control Test Container](http://msdn.microsoft.com/pt-br/72fa40ef-27d3-400c-813f-10b03236e600).  
  
## Consulte também  
 [Depuração de COM e ActiveX](../debugger/com-and-activex-debugging.md)   
 [Controles ActiveX](/visual-cpp/mfc/activex-controls)