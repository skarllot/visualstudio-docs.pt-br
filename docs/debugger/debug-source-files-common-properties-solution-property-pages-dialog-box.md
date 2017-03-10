---
title: "Caixa de di&#225;logo Depurar Arquivos de Origem, Propriedades Comuns, P&#225;ginas de Propriedade da Solu&#231;&#227;o | Microsoft Docs"
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
  - "vs.debug.options.FindSource"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Página de propriedade Depurar Arquivos de Origem"
  - "depurador, arquivos de origem"
  - "depurando [Visual Studio], especificando arquivos de origem e símbolo"
  - "arquivos de origem, especificando no depurador"
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Caixa de di&#225;logo Depurar Arquivos de Origem, Propriedades Comuns, P&#225;ginas de Propriedade da Solu&#231;&#227;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta página de propriedades especifica onde o depurador procurará arquivos de origem ao depurar a solução.  
  
 Para acessar a página de propriedades **Depurar Arquivos Fonte**, clique com o botão direito do mouse na solução em **Gerenciador de Soluções** e selecione **Propriedades** no menu de atalho.  Expanda a pasta **Propriedades Comuns** e clique na página **Depurar Arquivos Fonte**.  
  
 **Diretórios que contêm o código\-fonte**  
 Contém uma lista de diretórios nos quais o depurador procura arquivos de origem ao depurar a solução.  Os subdiretórios dos diretórios especificados também são pesquisados.  
  
 **Não procurar por estes arquivos de origem**  
 Insira os nomes de todos os arquivos que você não deseja que o depurador leia.  Se o depurador encontrar um desses arquivos em um dos diretórios especificados acima, ele o ignorará.  Se a caixa de diálogo **Localizar Fonte** aparecer durante a depuração e você clicar em **Cancelar**, o arquivo que você procurava será adicionado a essa lista para que o depurador não continue a procurar o arquivo.  
  
## Consulte também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Configurações de depuração e preparação](../debugger/debugger-settings-and-preparation.md)