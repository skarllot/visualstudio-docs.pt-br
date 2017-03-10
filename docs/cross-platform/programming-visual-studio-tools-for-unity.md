---
title: "Programando o Visual Studio Tools for Unity | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "tgt-pltfrm-cross-plat"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5758cb0-e73b-45f5-8cae-c0eb40491026
caps.latest.revision: 3
caps.handback.revision: 3
ms.author: "crdun"
manager: "crdun"
---
# Programando o Visual Studio Tools for Unity
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nesta seção, você encontrará exemplos de uso do Visual Studio Tools para a API do Unity.  
  
## Exemplos  
 Aqui estão alguns exemplos que mostram como você pode usar o Visual Studio Tools para APIs do Unity.  
  
### Personalizar os arquivos de projeto criados por VSTU  
 Visual Studio Tools para o Unity fornece um retorno de chamada de estilo do Unity durante a geração do arquivo de projeto.  Para saber como você pode modificar o arquivo de projeto sempre que ele for gerado novamente, consulte [Exemplo: geração de arquivo de projeto](../cross-platform/customize-project-files-created-by-vstu.md).  
  
### Compartilhar o retorno de chamada de log do Unity com VSTU  
 O Visual Studio Tools para o Unity registra um retorno de chamada de log com o Unity para poder transmitir seu console para o Visual Studio.  Se o scripts de editor também registram um retorno de chamada de log com o Unity, o retorno de chamada VSTU pode interferir com ele.  Para saber como você pode compartilhar o retorno de chamada de log do Unity com VSTU, consulte [Exemplo: retorno de chamada de log](../cross-platform/share-the-unity-log-callback-with-vstu.md).