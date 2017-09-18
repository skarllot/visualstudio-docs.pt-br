---
title: IDebugModule3::GetSymbolInfo | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
caps.latest.revision: 17
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
ms.openlocfilehash: af2182c2f4214cfbd405c9275e7095822ef7cc5d
ms.lasthandoff: 02/22/2017

---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
Recupera uma lista de caminhos que são pesquisados para símbolos, bem como os resultados da pesquisa de cada caminho.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetSymbolInfo(  
   SYMBOL_SEARCH_INFO_FIELDS  dwFields,  
   MODULE_SYMBOL_SEARCH_INFO* pInfo  
);  
```  
  
```c#  
int GetSymbolInfo(  
   enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,   
   MODULE_SYMBOL_SEARCH_INFO[]    pinfo  
);  
  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwFields`  
 [in] Uma combinação de sinalizadores do [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) enumeração especificando quais campos de `pInfo` devem ser preenchidos.  
  
 `pInfo`  
 [out] A [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) estrutura cujos membros são a ser preenchido com as informações especificadas. Se esse for um valor nulo, esse método retorna `E_INVALIDARG`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se o método for bem-sucedido, ele retorna `S_OK`; caso contrário, ele retorna um código de erro.  
  
> [!NOTE]
>  Cadeia de caracteres retornada (no `MODULE_SYMBOL_SEARCH_INFO` estrutura) pode estar vazio mesmo se `S_OK` é retornado. Nesse caso, não houve nenhuma informação de pesquisa para retornar.  
  
## <a name="remarks"></a>Comentários  
 Se o `bstrVerboseSearchInfo` campo o `MODULE_SYMBOL_SEARCH_INFO` estrutura não estiver vazia, ele contém uma lista de caminhos pesquisados e os resultados da pesquisa. A lista é formatada com um caminho, seguido por reticências ("..."), seguidas pelo resultado. Se houver mais de um par de resultado de caminho, cada par é separado por um par de "\r\n" (carro-retorno/alimentação de linha). O padrão tem esta aparência:  
  
 \<caminho >... \<resultado > \r\n\<caminho >... \<resultado > \r\n\<caminho >... \<resultado >  
  
 Observe que a última entrada não tem uma sequência \r\n.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, esse método retorna três caminhos com três diferentes resultados. Cada linha é encerrada com um par de carro-retorno/alimentação de linha. O exemplo de saída apenas imprime os resultados da pesquisa como uma única cadeia de caracteres.  
  
> [!NOTE]
>  Um resultado de status é tudo imediatamente após o "…" até o final da linha.  
  
```cpp#  
void ShowSymbolSearchResults(IDebugModule3 *pIDebugModule3)  
{  
    MODULE_SYMBOL_SEARCH_INFO ssi = { 0 };  
    HRESULT hr;  
    hr = pIDebugModule3->GetSymbolInfo(SSIF_VERBOSE_SEARCH_INFO,&ssi);  
    if (SUCCEEDED(hr)) {  
        CComBSTR searchInfo = ssi.bstrVerboseSearchInfo;  
        if (searchInfo.Length() != 0) {  
            std::wcout << (wchar_t *)(BSTR)searchInfo;  
            std::wcout << std::endl;  
        }  
    }  
}  
```  
  
 **c:\symbols\user32.PDB... Arquivo não encontrado.**  
**c:\winnt\symbols\user32.PDB... Versão não corresponde.**  
**\\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.PDB... Símbolos carregados.**   
## <a name="see-also"></a>Consulte também  
 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)   
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)   
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
