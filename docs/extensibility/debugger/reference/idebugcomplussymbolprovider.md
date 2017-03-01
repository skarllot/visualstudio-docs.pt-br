---
title: IDebugComPlusSymbolProvider | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d2d4549bdff5d666b2b726a5128dc015c2de418e
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
Representa um provedor de símbolo COM+ com métodos que são específicos para o código gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugComPlusSymbolProvider : IDebugSymbolProvider  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Embora não haja nenhuma separação entre as interfaces que são úteis para um avaliador de expressão (EE) e aqueles que devem ser usados por um mecanismo de depuração (DE), os seguintes métodos provavelmente serão relevantes apenas a desenvolvedores DE: AreSymbolsLoaded, GetAddressesInModuleFromPosition, GetEntryPoint, GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFromStream, ReplaceSymbols, UnloadSymbols e UpdateSymbols.  
  
## <a name="methods"></a>Métodos  
 Além dos métodos de [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) interface, essa interface implementa os métodos a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|Determina se os símbolos de depuração são carregados para o módulo especificado considerando o identificador de domínio de aplicativo.|  
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Cria um tipo do tipo primitivo especificado.|  
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|Mapeia uma posição de documento no módulo especificado para uma matriz de endereços de depuração.|  
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Recupera informações sobre a matriz especificada, dada seu endereço de depuração de tipo.|  
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Recupera o nome do assembly dado seu domínio de módulo e o aplicativo.|  
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|Recupera as classes que são implementadas na linguagem de programação específica com o atributo especificado.|  
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|Recupera as classes com o atributo especificado em um determinado módulo.|  
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Recupera o ponto de entrada do aplicativo.|  
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Recupera o endereço em uma função que representa o deslocamento de linha determinada.|  
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Recupera o layout de variáveis locais para um conjunto de métodos.|  
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Retorna o nome associado ao token especificado, dado seu objeto de metadados.|  
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|Recupera os símbolos de depuração com o atributo pai determinado para o módulo especificado.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Recupera o leitor de símbolo a ser usado pelo código não gerenciado.|  
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|Recupera a um tipo de símbolo dado seu endereço de depuração.|  
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|Determina se a função no endereço especificado depuração será excluída.|  
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Determina se a função no endereço especificado debug é considerada obsoleta.|  
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Determina se o código no endereço depurador especificado está oculto.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Carrega os símbolos de depuração especificado na memória.|  
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|O fluxo de dados de símbolos de depuração de cargas.|  
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Substitui os símbolos de depuração atual com aqueles no fluxo de dados especificado.|  
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|Descarrega os símbolos de depuração para o módulo especificado da memória.|  
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Atualiza os símbolos de depuração na memória com aqueles do fluxo de dados especificado.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
