---
title: "IDiaDataSource::loadDataForExe | Microsoft Docs"
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
  - "Método IDiaDataSource::loadDataForExe"
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaDataSource::loadDataForExe
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Abre e prepara os dados de depuração associados ao arquivo.exe\/.dll.  
  
## Sintaxe  
  
```cpp#  
HRESULT loadDataForExe (  
   LPCOLESTR executable,  
   LPCOLESTR searchPath,  
   IUnknown* pCallback  
);  
```  
  
#### Parâmetros  
 executável  
 \[in\] Caminho para o arquivo. exe ou. dll.  
  
 searchPath  
 \[in\] Caminho alternativo para procurar dados de depuração.  
  
 pCallback  
 \[in\] Um `IUnknown` interface para um objeto que oferece suporte a uma interface de retorno de chamada de depuração, como o [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md), [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md), o [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md), e\/ou o [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) interfaces.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  A tabela a seguir mostra alguns dos possíveis códigos de erro para este método.  
  
|Valor|Descrição|  
|-----------|---------------|  
|E\_PDB\_NOT\_FOUND|Falha ao abrir o arquivo ou o arquivo tem um formato inválido.|  
|E\_PDB\_FORMAT|Você tentou acessar um arquivo com um formato obsoleto.|  
|E\_PDB\_INVALID\_SIG|Assinatura não corresponde.|  
|E\_PDB\_INVALID\_AGE|Não é compatível com a idade.|  
|E\_INVALIDARG|Parâmetro inválido.|  
|E\_UNEXPECTED|Fonte de dados já foi preparado.|  
  
## Comentários  
 O cabeçalho de depuração do arquivo.exe\/.dll nomeia o local dos dados associados de depuração.  
  
 Este método lê o cabeçalho de debug e, em seguida, procura e prepara os dados de depuração.  O progresso da pesquisa pode, opcionalmente, relatado e controlado por meio de retornos de chamada.  Por exemplo, o [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) é chamado quando o `IDiaDataSource::loadDataForExe` método localiza e processa um diretório de depuração.  
  
 O [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) e [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) interfaces permite que o aplicativo cliente fornecer métodos alternativos para leitura de dados do arquivo executável quando o arquivo não pode ser acessado diretamente por meio de e\/S de arquivo padrão.  
  
 Para carregar um arquivo. PDB sem validação, use o [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) método.  
  
 Para validar o arquivo. PDB em relação a critérios específicos, use o [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) método.  
  
 Para carregar um arquivo. PDB diretamente da memória, use o [IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md) método.  
  
## Exemplo  
  
```cpp#  
class MyCallBack: public IDiaLoadCallback  
{  
...  
};  
MyCallBack callback;  
...  
HRESULT hr = pSource->loadDataForExe( L"myprog.exe", L".\debug", (IUnknown*)&callback);  
if (FAILED(hr))  
{  
    // Report error  
}  
```  
  
## Consulte também  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md)