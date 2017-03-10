---
title: "IDiaDataSource::loadDataFromPdb | Microsoft Docs"
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
  - "Método IDiaDataSource::loadDataFromPdb"
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaDataSource::loadDataFromPdb
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Abre e prepara um arquivo de banco de dados \(. PDB\) do programa como uma fonte de dados de depuração.  
  
## Sintaxe  
  
```cpp#  
HRESULT loadDataFromPdb (  
   LPCOLESTR pdbPath  
);  
```  
  
#### Parâmetros  
 pdbPath  
 \[in\] O caminho para o arquivo. PDB.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  A tabela a seguir mostra os valores de retorno possíveis para esse método.  
  
|Valor|Descrição|  
|-----------|---------------|  
|E\_PDB\_NOT\_FOUND|Falha ao abrir o arquivo ou determinado que o arquivo tem um formato inválido.|  
|E\_PDB\_FORMAT|Você tentou acessar um arquivo com um formato obsoleto.|  
|E\_INVALIDARG|Parâmetro inválido.|  
|E\_UNEXPECTED|Fonte de dados já foi preparado.|  
  
## Comentários  
 Esse método carrega os dados de depuração diretamente de um arquivo. PDB.  
  
 Para validar o arquivo. PDB em relação a critérios específicos, use o [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) método.  
  
 Para acessar o processo de carregamento de dados \(por meio de um mecanismo de retorno de chamada\), use o [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método.  
  
 Para carregar um arquivo. PDB diretamente da memória, use o [IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md) método.  
  
## Exemplo  
  
```cpp#  
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );  
if (FAILED(hr))  
{  
    // report error  
}  
```  
  
## Consulte também  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md)