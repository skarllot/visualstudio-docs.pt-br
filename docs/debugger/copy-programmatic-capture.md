---
title: "Copiar (captura program&#225;tica) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Copiar (captura program&#225;tica)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Copia o conteúdo dos gráficos ativas registra o arquivo \(.vsglog\) em um arquivo novo.  
  
## Sintaxe  
  
```cpp  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### Parâmetros  
 `szNewVSGLog`  
 O nome do arquivo do novo arquivo de log dos gráficos.  
  
## Comentários  
 Para copiar informações dos gráficos para um novo arquivo, você já deve ter capturado informações de alguns gráficos; se não, nada acontece.