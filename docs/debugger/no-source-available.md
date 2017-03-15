---
title: "Nenhuma origem dispon&#237;vel | Microsoft Docs"
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
  - "vs.debug.nosource"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Caixa de diálogo Não Há Nenhum Código-Fonte Disponível para o Local Atual"
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Nenhuma origem dispon&#237;vel
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O projeto não contém código\-fonte para o código que você está tentando exibir.  A causa comum é clicar duas vezes em um módulo que não tem o código\-fonte na **Janela de Pilha de Chamadas** ou **Janela de Threads**.  Você pode continuar a depuração, mas não pode usar a janela de origem para definir pontos de interrupção e executar outras ações nesse local.  Se você precisar definir um ponto de interrupção, use a **Janela de Desmontagem**.  
  
 Nas Páginas de Propriedades de Solução, você pode alterar os diretórios em que o depurador procura arquivos de origens e informa o depurador para ignorar os arquivos de origem selecionados.  Consulte [Caixa de diálogo Depurar Arquivos de Origem, Propriedades Comuns, Páginas de Propriedade da Solução](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).  
  
 **Navegar para localizar o código\-fonte**  
 Clique neste link para abrir uma caixa de diálogo onde você pode procurar para localizar o código\-fonte.  
  
 **Mostrar Desmontagem**  
 Inicia a **Janela de Desmontagem**.  
  
 **Sempre mostrar desmontagem para arquivos de origem ausentes**  
 Selecione esta opção para exibir **Janela de Desmontagem** automaticamente quando nenhuma origem estiver disponível.  Essa configuração também pode ser alterada na caixa de diálogo **Opções**, categoria **Depuração**, página **Geral**, marcando ou desmarcando **Mostrar desmontagem se a fonte não estiver disponível**.  
  
## Consulte também  
 [Caixa de diálogo Depurar Arquivos de Origem, Propriedades Comuns, Páginas de Propriedade da Solução](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [Especificar arquivos de símbolo \(.pdb\) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll \(Extensão de Depuração SOS\)](../Topic/SOS.dll%20\(SOS%20Debugging%20Extension\).md)