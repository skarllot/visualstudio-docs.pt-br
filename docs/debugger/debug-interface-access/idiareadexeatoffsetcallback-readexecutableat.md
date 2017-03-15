---
title: "IDiaReadExeAtOffsetCallback::ReadExecutableAt | Microsoft Docs"
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
  - "C++"
helpviewer_keywords: 
  - "Método IDiaReadExeAtOffsetCallback::ReadExecutableAt"
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaReadExeAtOffsetCallback::ReadExecutableAt
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lê o número especificado de bytes começando no deslocamento especificado a partir de um arquivo executável.  
  
## Sintaxe  
  
```cpp#  
HRESULT ReadExecutableAt (   
   DWORDLONG fileOffset,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### Parâmetros  
 fileOffset  
 \[in\] O deslocamento no arquivo executável para iniciar a leitura.  
  
 cbData diferente  
 \[in\] Número de bytes a serem lidos.  
  
 pcbData  
 \[out\] Retorna o número de bytes lidos.  
  
 Data\]  
 \[in, out\] Uma matriz que é preenchida com bytes lidos do arquivo.  
  
## Comentários  
 Este método é chamado pelo código de suporte do DIA para carregar os bytes de dados de um executável usando um deslocamento de arquivo absoluto.  Este método é chamado para oferecer suporte a [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método.  
  
## Consulte também  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)