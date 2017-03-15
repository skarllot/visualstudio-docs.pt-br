---
title: "IDiaDataSource::loadAndValidateDataFromPdb | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "Método IDiaDataSource::loadAndValidateDataFromPdb"
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaDataSource::loadAndValidateDataFromPdb
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Abre e verifica se o arquivo de banco de dados \(. PDB\) do programa corresponde ao fornecido as informações de assinatura e prepara o arquivo. PDB como uma fonte de dados de depuração.  
  
## Sintaxe  
  
```cpp#  
HRESULT loadAndValidateDataFromPdb (   
   LPCOLESTR pdbPath,  
   GUID*     pcsig70,  
   DWORD     sig,  
   DWORD     age  
);  
```  
  
#### Parâmetros  
 `pdbPath`  
 \[in\] O caminho para o arquivo. PDB.  
  
 `pcsig70`  
 \[in\] A assinatura GUID para ser verificado a assinatura de arquivo. PDB.  Somente. PDB os arquivos na [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] e versões posteriores possuem assinaturas GUID.  
  
 `sig`  
 \[in\] A assinatura de 32 bits para ser verificado a assinatura de arquivo. PDB.  
  
 `age`  
 \[in\] Valor de idade para verificar.  A idade não correspondem necessariamente à qualquer valor de tempo conhecido, ele é usado para determinar se um arquivo. PDB está fora de sincronia com um arquivo. exe correspondente.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  A tabela a seguir mostra os valores de retorno possíveis para esse método.  
  
|Valor|Descrição|  
|-----------|---------------|  
|E\_PDB\_NOT\_FOUND|Falha ao abrir o arquivo ou o arquivo tem um formato inválido.|  
|E\_PDB\_FORMAT|Você tentou acessar um arquivo com um formato obsoleto.|  
|E\_PDB\_INVALID\_SIG|Assinatura não corresponde.|  
|E\_PDB\_INVALID\_AGE|Não é compatível com a idade.|  
|E\_INVALIDARG|Parâmetro inválido.|  
|E\_UNEXPECTED|A fonte de dados já foi preparada.|  
  
## Comentários  
 Um arquivo. PDB contém valores de assinatura e a idade.  Esses valores são replicados no arquivo. exe ou. dll que corresponde ao arquivo. PDB.  Antes de preparar a fonte de dados, esse método verifica a assinatura e a idade do arquivo. PDB nomeado coincidir com os valores fornecidos.  
  
 Para carregar um arquivo. PDB sem validação, use o [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) método.  
  
 Para acessar o processo de carregamento de dados \(por meio de um mecanismo de retorno de chamada\), use o [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método.  
  
 Para carregar um arquivo. PDB diretamente da memória, use o [IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md) método.  
  
## Exemplo  
  
```cpp#  
IDiaDataSource* pSource;  // Previously created data source.  
DEFINE_GUID(expectedGUIDSignature,0x1234,0x5678,0x01,0x02,0x03,0x04,0x05,0x06,0x07,0x08);  
DWORD expectedFileSignature = 0x12345678;  
DWORD expectedAge           = 128;  
  
HRESULT hr;  
hr = pSource->loadAndValidateDataFromPdb( L"yprog.pdb",  
                                          &expectedGUIDSignature,  
                                          expectedFileSignature,  
                                          expectedAge);  
if (FAILED(hr))  
{  
    // Report an error  
}  
  
```  
  
## Consulte também  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md)