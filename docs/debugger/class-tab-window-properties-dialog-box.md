---
title: "Guia Classe, Caixa de di&#225;logo Propriedades da Janela | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "caixa de diálogo Propriedades da Janela, Guia Classe"
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Guia Classe, Caixa de di&#225;logo Propriedades da Janela
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Use o  **classe** guia para mostrar informações sobre a classe da janela selecionada.  Para exibir o  [Caixa de diálogo de propriedades de janela](../debugger/window-properties-dialog-box.md), mover o foco para o  [De exibição do Windows](../debugger/windows-view.md) janela.  Selecione qualquer nó da janela na árvore e escolha  **Propriedades** da  **Exibir** menu.  
  
 As configurações a seguir estão disponíveis na  **classe** guia:  
  
|Entrada|Descrição|  
|-------------|---------------|  
|**Class Name**|O nome \(ou um número ordinal\) dessa classe de janela.|  
|**Estilos de classe**|Uma combinação dos códigos de estilo de classe.|  
|**Bytes de classe**|Dados específicos do aplicativo associados a essa classe de janela.|  
|**Classe Atom**|Átomo para a classe retornado pelo  **RegisterClass** de chamada.|  
|**Identificador de instância**|O identificador de instância do módulo que registrou a classe.  Os identificadores de instância não são exclusivos.|  
|**Bytes de janela**|O número de bytes extras associadas com cada janela dessa classe.  O significado de um desses bytes é determinado pelo aplicativo.  Expanda a caixa de lista para ver os valores de bytes em formato DWORD.|  
|**Janela Proc**|O endereço atual do  **WndProc** a função para o windows dessa classe.  Isso difere do  **Proc da janela** sobre o  **Geral** guia se a janela é uma subclasse.|  
|**Nome do menu**|O nome do menu principal associado ao windows desta classe \("none" se não há nenhum menu\).|  
|**Identificador de ícone**|O identificador para o ícone associado ao windows desta classe \("none" se não houver nenhum ícone\).|  
|**Identificador do cursor**|O identificador do cursor associado ao windows desta classe \("none" se não houver nenhum cursor\).|  
|**Pincel de plano de fundo**|O identificador para o pincel de plano de fundo que está associado com o windows desta classe ou um das cores COLOR\_ \* predefinidas para pintar o plano de fundo da janela \("none" se não houver nenhum pincel\).|