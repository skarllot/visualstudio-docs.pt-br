---
title: IDebugDocumentContext2::GetLanguageInfo | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDocumentContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugDocumentContext2::GetLanguageInfo
ms.assetid: 6a212ee5-414c-4eb5-ab11-19db1786943d
caps.latest.revision: 10
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
ms.openlocfilehash: 1bb285981011920a5b5c2755bac7e0fdbf8e53d1
ms.lasthandoff: 02/22/2017

---
# <a name="idebugdocumentcontext2getlanguageinfo"></a>IDebugDocumentContext2::GetLanguageInfo
Obtém o idioma associado a esse contexto de documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetLanguageInfo(   
   BSTR* pbstrLanguage,  
   GUID* pguidLanguage  
);  
```  
  
```c#  
int GetLanguageInfo(   
   out string pbstrLanguage,  
   out Guid   pguidLanguage  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbstrLanguage`  
 [out] Retorna o nome do idioma que implementa o código no contexto neste documento.  
  
 `pguidLanguage`  
 [out] Retorna o GUID da linguagem que implementa o código no contexto neste documento. Por exemplo, `guidVBScriptLang` ou `guidCPPLang`. Esse GUID não é limitado às linguagens fornecidas pelo [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como implementar esse método para um simples `CDebugContext` objeto expõe o [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interface.  
  
```cpp#  
HRESULT CDebugContext::GetLanguageInfo(BSTR* pbstrLanguage, GUID* pguidLanguage)    
{    
   HRESULT hr;    
  
   // Check for a valid language argument pointers.    
   if (pbstrLanguage && pguidLanguage)    
   {    
      *pguidLanguage = GUID_NULL;    
      *pbstrLanguage = SysAllocString(L"Batch File");    
      if (*pbstrLanguage)    
      {    
         *pguidLanguage = guidBatLang;    
         hr = S_OK;    
      }    
      else    
      {    
         hr = E_OUTOFMEMORY;    
      }    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
