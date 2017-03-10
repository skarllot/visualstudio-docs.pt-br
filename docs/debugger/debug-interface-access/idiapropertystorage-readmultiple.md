---
title: "IDiaPropertyStorage::ReadMultiple | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadMultiple"
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::ReadMultiple
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Leituras especificado propriedades do conjunto atual de propriedade.  
  
## Sintaxe  
  
```cpp#  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### Parâmetros  
 `cpspec`  
 \[in\] Contagem de propriedades especificadas na `rgpspec` array.  Se for zero, o método retorna sem propriedades mas retornar `S_OK` como um código de sucesso.  
  
 `rgpspec`  
 \[in\] Uma matriz de propriedades a serem lidos.  Propriedades podem ser especificadas por uma identificação de propriedade ou por um nome de seqüência de caracteres opcional.  Não é necessário especificar as propriedades em uma ordem específica na matriz.  A matriz pode conter propriedades duplicadas, resultando em valores de propriedade duplicada no retorno nas propriedades simples.  Propriedades simples não devem retornar em uma tentativa para abri\-los pela segunda vez o acesso negado.  A matriz pode conter uma mistura de identificações de propriedade e seqüência de caracteres.  Essa matriz deve ter pelo menos `cpspec` número de valores de propriedade.  
  
 `rgvar`  
 \[in, out\] Uma matriz de `PROPVARIANT` estruturas \(no namespace Microsoft.VisualStudio.OLE.Interop\) para ser preenchido com valores para cada propriedade.  A matriz deve ser pelo menos `cpspec` elementos de tamanho.  O chamador não precisa inicializar os valores na matriz.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`.  Retorna `S_FALSE` se um ou mais das propriedades não foi encontrado.  Caso contrário, retorna um código de erro.  
  
## Comentários  
 Se uma propriedade não foi encontrada, a entrada correspondente na `rgvar` matriz contém um `VARIANT` com o tipo de `VT_EMPTY`.  
  
## Consulte também  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)