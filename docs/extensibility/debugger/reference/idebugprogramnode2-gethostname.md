---
title: IDebugProgramNode2::GetHostName | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramNode2::GetHostName
helpviewer_keywords:
- IDebugProgramNode2::GetHostName
ms.assetid: 16aad1ff-ad34-4394-a2e4-5621374a7729
caps.latest.revision: 12
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
ms.openlocfilehash: 338f2ca57b88940e5dafb6aa9e3610754b5ca9f0
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprogramnode2gethostname"></a>IDebugProgramNode2::GetHostName
Obtém o nome do processo que hospeda o programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetHostName (   
   GETHOSTNAME_TYPE dwHostNameType,  
   BSTR*            pbstrHostName  
);  
```  
  
```c#  
int GetHostName (   
   enum_GETHOSTNAME_TYPE dwHostNameType,  
   out string            pbstrHostName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwHostNameType`  
 [in] Um valor a partir de [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) enumeração que especifica o tipo de nome a ser retornado.  
  
 `pbstrHostName`  
 [out] Retorna o nome do processo de hospedagem.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como implementar esse método para um simples `CProgram` objeto expõe o [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) interface. Este exemplo ignora o `dwHostNameType` parâmetro e retorna somente o nome do programa como extraído do nome base do caminho do arquivo do módulo.  
  
```cpp#  
HRESULT CProgram::GetHostName(DWORD dwHostNameType, BSTR* pbstrHostName) {    
   // Check for valid argument.    
   if (pbstrHostName)    
   {    
      char szModule[_MAX_PATH];    
  
      // Attempt to assign to szModule the path for the file used  
      // to create the calling process.    
      if (GetModuleFileName(NULL, szModule, sizeof (szModule)))    
      {    
         // If successful then declare several char arrays    
         char  szDrive[_MAX_DRIVE];    
         char  szDir[_MAX_DIR];    
         char  szName[_MAX_FNAME];    
         char  szExt[_MAX_EXT];    
         char  szFilename[_MAX_FNAME + _MAX_EXT];    
         WCHAR wszFilename[_MAX_FNAME + _MAX_EXT];    
  
         // Break the szModule path name into components.    
         _splitpath(szModule, szDrive, szDir, szName, szExt);    
  
         // Copy the base file name szName into szFilename.    
         lstrcpy(szFilename, szName);    
         // Append the field extension szExt into szFilename.    
         lstrcat(szFilename, szExt);    
  
         // Convert the szFilename sequence of multibyte characters    
         // to the wszFilename sequence of wide characters.    
         mbstowcs(wszFilename, szFilename, sizeof (wszFilename) / 2);    
  
         // Assign the wszFilename to the value at *pbstrHostName.    
         *pbstrHostName = SysAllocString(wszFilename);    
  
          return S_OK;    
      }    
   }    
  
    return E_INVALIDARG;    
}    
```  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
