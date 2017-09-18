---
title: IDebugSymbolProvider | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
caps.latest.revision: 14
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
ms.openlocfilehash: bb3f8a9c41e321c8e34e659c3e327b209d515eb8
ms.lasthandoff: 02/22/2017

---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
Essa interface representa um provedor de símbolo que fornece tipos, retorná-las como campos e símbolos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugSymbolProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um provedor de símbolo deve implementar essa interface para fornecer o símbolo e digite as informações para um avaliador de expressão.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Essa interface é obtida por meio do COM `CoCreateInstance` função (por provedores de símbolo não gerenciado) ou carregando apropriado gerenciados assembly de código e instanciar o provedor de símbolo com base nas informações encontradas no assembly. O mecanismo de depuração instancia o provedor de símbolo para trabalhar em conjunto com o avaliador de expressão. Veja o exemplo de uma abordagem para criar uma instância dessa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugSymbolProvider`.  
  
|Método|Descrição|  
|------------|-----------------|  
|`Initialize`|Preterido. Não use.|  
|`Uninitialize`|Preterido. Não use.|  
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Obtém o campo que contém o endereço de depuração.|  
|`GetField`|Preterido. Não use.|  
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|Mapeia uma posição de documento em uma matriz de endereços de depuração.|  
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Mapeia um contexto de documento em uma matriz de endereços de depuração.|  
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Mapeia um endereço de depuração em um contexto de documento.|  
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Obtém o idioma usado para compilar o código no endereço de depuração.|  
|`GetGlobalContainer`|Preterido. Não use.|  
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Obtém o campo que representa um nome de método totalmente qualificado.|  
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Obtém o tipo de campo de classe que representa um nome de classe totalmente qualificado.|  
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Cria um enumerador para namespaces associado ao endereço de depuração.|  
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Mapeia um nome de símbolo em um tipo de símbolo.|  
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Obtém o endereço de depuração que segue um endereço específico de depuração em um método.|  
  
## <a name="remarks"></a>Comentários  
 Essa interface mapeia posições de documento em endereços de depuração e vice-versa.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como criar uma instância do provedor de símbolo, dado seu GUID (um mecanismo de depuração deve saber esse valor).  
  
```cpp#  
// A debug engine uses its own symbol provider and would know the GUID  
// of that provider.  
IDebugSymbolProvider *GetSymbolProvider(GUID *pSymbolProviderGuid)  
{  
    // This is typically defined globally.  For this example, it is  
    // defined here.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
    IDebugSymbolProvider *pProvider = NULL;  
    if (pSymbolProviderGuid != NULL) {  
        CLSID clsidProvider = { 0 };  
        ::GetSPMetric(*pSymbolProviderGuid,  
                      storetypeFile,  
                      metricCLSID,  
                      &clsidProvider,  
                      strRegistrationRoot);  
        if (IsEqualGUID(clsidProvider,GUID_NULL)) {  
            // No file type provider, try metadata provider.  
            ::GetSPMetric(*pSymbolProviderGuid,  
                          ::storetypeMetadata,  
                          metricCLSID,  
                          &clsidProvider,  
                          strRegistrationRoot);  
        }  
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {  
            CComPtr<IDebugSymbolProvider> spSymbolProvider;  
            spSymbolProvider.CoCreateInstance(clsidProvider);  
            if (spSymbolProvider != NULL) {  
                pProvider = spSymbolProvider.Detach();  
            }  
        }  
    }  
    return(pProvider);  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de provedor de símbolo](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
