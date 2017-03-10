---
title: "Guia Geral, Caixa de di&#225;logo Propriedades da Janela | Microsoft Docs"
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
  - "caixa de diálogo Propriedades da Janela, Guia Geral"
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Guia Geral, Caixa de di&#225;logo Propriedades da Janela
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Use o  **Geral** guia para mostrar informações sobre a janela selecionada.  Para exibir o  [Caixa de diálogo de propriedades de janela](../debugger/window-properties-dialog-box.md), mover o foco para o  [De exibição do Windows](../debugger/windows-view.md) janela.  Selecione qualquer nó da janela na árvore e escolha  **Propriedades** da  **Exibir** menu.  
  
 As configurações a seguir estão disponíveis na  **Geral** guia:  
  
|Entrada|Descrição|  
|-------------|---------------|  
|**Legenda da janela**|O texto na legenda da janela, ou o texto contido em uma janela, se for um controle.|  
|**Identificador de janela**|A identificação exclusiva desta janela.  Os números de identificador de janela são reutilizados; Elas identificam uma janela somente para a vida útil do que a janela.|  
|**Janela Proc**|O endereço virtual da função de procedimento de janela para esta janela.  Este campo também indica se essa janela é uma janela de Unicode e seja subclasse.|  
|**Retângulo**|O retângulo delimitador da janela.  O tamanho do retângulo também é exibido.  As unidades são pixels em coordenadas de tela.|  
|**Rect restaurado**|O retângulo delimitador da janela restaurada.  O tamanho do retângulo também é exibido.  Rect restaurado será diferente de retângulo somente quando a janela está maximizada ou minimizada.  As unidades são pixels em coordenadas de tela.|  
|**RET de cliente.**|O retângulo delimitador para a área de cliente da janela.  O tamanho do retângulo também é exibido.  As unidades são pixels relativos à parte superior esquerda da área de cliente da janela.|  
|**Identificador de instância**|O identificador de instância do aplicativo.  Os identificadores de instância não são exclusivos.|  
|**ID de controle ou identificador de Menu**|Se a janela que está sendo exibido é uma janela filho, o rótulo de identificação de controle é exibido.  Identificação do controle é um inteiro que identifica o ID de controle. da janela este filho  Se a janela que está sendo exibido não for uma janela filho, o rótulo de tratar de Menu é exibido.  Identificador de menu é um inteiro que identifica o identificador do menu associado a esta janela.|  
|**Dados do usuário**|Dados específicos do aplicativo que estão anexados a essa estrutura de janela.|  
|**Bytes de janela**|O número de bytes extras associados a esta janela.  O significado de um desses bytes é determinado pelo aplicativo.  Expanda a caixa de lista para ver os valores de bytes em formato DWORD.|