---
title: "IDiaSession | Microsoft Docs"
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
  - "Interface IDiaSession"
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Fornece um contexto de consulta para símbolos de depuração.  
  
## Sintaxe  
  
```  
IDiaSession : IUnknown  
```  
  
## Métodos  
 A tabela a seguir mostra os métodos de `IDiaSession`.  
  
|Método|Descrição|  
|------------|---------------|  
|[IDiaSession::get\_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Recupera o endereço de carregamento para o arquivo executável que corresponde aos símbolos no repositório do símbolo.  Esse é o mesmo valor que foi passado para o método de `put_loadAddress` .|  
|[IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Define o endereço de carregamento para o arquivo executável que corresponde aos símbolos no repositório do símbolo. **Note:**  É importante chamar este método quando você obtém um objeto de `IDiaSession` e antes de iniciar usando o objeto.|  
|[IDiaSession::get\_globalScope](../Topic/IDiaSession::get_globalScope.md)|Recupera uma referência ao escopo global.|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Recupera um enumerador para todas as tabelas contidas no armazenamento de símbolo.|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Recupera um enumerador para todos os símbolos nomeados em locais estáticos.|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Recupera todos os filhos de um identificador pai especificado que corresponde ao nome e o tipo do símbolo.|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|Recupera um tipo especificado do símbolo que contém, ou é o mais próximo da, um endereço especificado.|  
|[IDiaSession::findSymbolByRVA](../Topic/IDiaSession::findSymbolByRVA.md)|Recupera um tipo especificado do símbolo que contém, ou é o mais próximo da, um endereço virtual relativo especificado \(RVA\).|  
|[IDiaSession::findSymbolByVA](../Topic/IDiaSession::findSymbolByVA.md)|Recupera um tipo especificado do símbolo que contém, ou é o mais próximo da, um endereço virtual especificado \(VA\).|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Recupera o símbolo que contém os metadados especificados um.|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|Verifica se dois símbolos são equivalentes.|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Recupera um símbolo por seu identificador exclusivo.|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|Recupera um tipo especificado do símbolo que contém, ou é o mais próximo da, um endereço virtual e um deslocamento relativo especificados.|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|Recupera um tipo especificado do símbolo que contém, ou é o mais próximo da, um endereço virtual e um deslocamento especificado.|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Recupera um arquivo de origem pelo compiland e nome.|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Recupera um arquivo de origem identificador de arquivo de origem.|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Recupera a linha números em um identificador especificado de compiland e de arquivo de origem.|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Recupera linhas em um compiland especificado que contém um endereço especificado.|  
|[IDiaSession::findLinesByRVA](../Topic/IDiaSession::findLinesByRVA.md)|Recupera linhas em um compiland especificado que contém um endereço virtual relativo especificado.|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Localiza a linha informações do número de linhas contidas em um intervalo de endereços especificado.|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Recupera linhas em um compiland especificado pelo arquivo de origem e a linha de comando.|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Recupera uma fonte que é colocada no armazenamento de símbolo por provedores de atributo ou por outros componentes do processo de compilação.|  
|[IDiaSession::getEnumDebugStreams](../Topic/IDiaSession::getEnumDebugStreams.md)|Recupera uma seqüência enumerada de fluxos de dados de depuração.|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Recupera uma enumeração que permite que um cliente executa iterações através dos quadros definidas em um endereço especificado.|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Recupera uma enumeração que permite que um cliente executa iterações através dos quadros definidas em um endereço virtual relativo especificado \(RVA\).|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Recupera uma enumeração que permite que um cliente executa iterações através dos quadros definidas em um endereço virtual especificado \(VA\).|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Recupera uma enumeração que permite que um cliente executa iterações através da linha informações do número das funções que inlined, direta ou indiretamente, pelo símbolo pai especificado.|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Recupera uma enumeração que permite que um cliente executa iterações através da linha informações do número das funções que inlined, direta ou indiretamente, pelo símbolo pai especificado e está contida dentro do intervalo de endereços especificado.|  
|[IDiaSession::findInlineeLinesByRVA](../Topic/IDiaSession::findInlineeLinesByRVA.md)|Recupera uma enumeração que permite que um cliente executa iterações através da linha informações do número das funções que inlined, direta ou indiretamente, pelo símbolo pai especificado e está contida dentro do endereço virtual relativo especificado \(RVA\).|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Recupera uma enumeração que permite que um cliente executa iterações através da linha informações do número das funções que inlined, direta ou indiretamente, pelo símbolo pai especificado e está contida dentro do endereço virtual especificado \(VA\).|  
|[IDiaSession::findInlineeLinesByLinenum](../Topic/IDiaSession::findInlineeLinesByLinenum.md)|Recupera uma enumeração que permite que um cliente executa iterações através da linha informações do número das funções que inlined, direta ou indiretamente, no arquivo de origem e linha número especificado.|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Recupera uma enumeração que permite que um cliente executa iterações através da linha informações do número das funções inlined que correspondem um nome especificado.|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Retorna uma enumeração de símbolos para a variável que o valor especificado de marca corresponde a função pai de stub de aceleração.|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|Um determinado valor correspondente da marca, esse método retorna uma enumeração de símbolos que estão contidos em um pai função especificada de stub de aceleradores em um endereço virtual relativo especificado.|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Retorna uma enumeração de símbolos de quadros internos que correspondem ao nome da função in\-line especificado.|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Retorna uma enumeração de símbolos de quadros internos que correspondem ao local especificado de origem.|  
  
## Comentários  
 É importante chamar o método de [IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) após criar o objeto de `IDiaSession` — e o valor passado ao método de `put_loadAddress` deve ser diferente de zero — para todas as propriedades de \(VA\) do endereço virtual de símbolos para ser acessível.  O endereço de carregamento do que carregou o programa executável que está sendo depurado.  Por exemplo, você pode chamar a função `GetModuleInformation` Win32 para recuperar o endereço de carregamento para o arquivo executável, dado um identificador para o arquivo.  
  
## Exemplo  
 Este exemplo mostra como obter a interface de `IDiaSession` como parte de uma inicialização geral de diâmetro SDK.  
  
```cpp#  
CComPtr<IDiaDataSource> pSource;  
ComPtr<IDiaSession> psession;  
  
void InitializeDIA(const char *szFilename)  
{  
    HRESULT hr = CoCreateInstance( CLSID_DiaSource,  
                                   NULL,  
                                   CLSCTX_INPROC_SERVER,  
                                   __uuidof( IDiaDataSource ),  
                                  (void **) &pSource);  
    if (FAILED(hr))  
    {  
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );  
    }  
    wchar_t wszFilename[ _MAX_PATH ];  
    mbstowcs( wszFilename,  
              szFilename,  
              sizeof( wszFilename )/sizeof( wszFilename[0] ) );  
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )  
    {  
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )  
        {  
            Fatal( "loadDataFromPdb/Exe" );  
        }  
    }  
    if ( FAILED( pSource->openSession( &psession ) ) )  
    {  
        Fatal( "openSession" );  
    }  
}  
```  
  
## Requisitos  
 Cabeçalho: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Consulte também  
 [Interfaces \(SDK de Acesso à Interface de Depuração\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Visão Geral](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [Exe](../../debugger/debug-interface-access/exe.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [Consultando o arquivo .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)