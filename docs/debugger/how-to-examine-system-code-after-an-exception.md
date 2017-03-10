---
title: "Como examinar um c&#243;digo de sistema ap&#243;s uma exce&#231;&#227;o | Microsoft Docs"
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
  - "depuração, exceções"
  - "exceções, depuração"
ms.assetid: a38ad49b-7cf3-483d-91c4-eb3116eba50c
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como examinar um c&#243;digo de sistema ap&#243;s uma exce&#231;&#227;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando uma exceção ocorre, você poderá precisar examinar o código dentro de uma chamada do sistema para determinar a causa da exceção.  O procedimento a seguir explica como fazer isso se você não tiver os símbolos carregados para o código do sistema ou se Just My Code estiver habilitado.  
  
### Para examinar o código do sistema após uma exceção  
  
1.  Na janela **Pilha de Chamadas**, clique com o botão direito e clique em **Mostrar Código Externo**.  
  
     Se Just My Code não estiver habilitado, essa opção não estará disponível no menu de atalho e o código do sistema será mostrado por padrão.  
  
2.  Clique com o botão direito nos quadros de código externos que agora são exibidos na janela **Pilha de Chamadas**.  
  
3.  Aponte para **Carregar Símbolos de** e depois clique em **Servidores de Símbolo Microsoft**.  
  
    1.  Se Just My Code tiver sido habilitado, uma caixa de diálogo será exibida.  Indica que Just My Code agora foi desabilitado.  Isso é necessário para entrar em chamadas do sistema.  
  
    2.  A caixa de diálogo **Baixando símbolos públicos** é exibida.  Ela desaparecerá quando o download for concluído.  
  
4.  Agora você pode examinar o código do sistema na janela **Pilha de Chamadas** e em outras janelas.  Por exemplo, você pode clicar duas vezes em um quadro de pilha de chamadas para exibir o código em uma origem ou janela de **Desmontagem**.  
  
## Consulte também  
 [Gerenciando exceções com o depurador](../debugger/managing-exceptions-with-the-debugger.md)