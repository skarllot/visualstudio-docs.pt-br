---
title: QUERYCHANGESFUNC | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
caps.latest.revision: 16
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
ms.openlocfilehash: 827a8bef2cf9de538cd0ba1fac5b5c2723723bbe
ms.lasthandoff: 02/22/2017

---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Essa é uma função de retorno de chamada usada pelo [SccQueryChanges](../extensibility/sccquerychanges-function.md) operação para enumerar uma coleção de nomes de arquivo e determinar o status de cada arquivo.  
  
 O `SccQueryChanges` função recebe uma lista de arquivos e um ponteiro para o `QUERYCHANGESFUNC` retorno de chamada. O plug-in de controle de origem enumere a lista e fornece o status (por meio desse retorno de chamada) para cada arquivo na lista.  
  
## <a name="signature"></a>Assinatura  
  
```cpp#  
typedef BOOL (*QUERYCHANGESFUNC)(  
   LPVOID pvCallerData,  
   QUERYCHANGESDATA * pChangesData  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 pvCallerData  
 [in] O `pvCallerData` parâmetro passado pelo chamador (IDE) para [SccQueryChanges](../extensibility/sccquerychanges-function.md). O plug-in de controle de origem não deve fazer nenhuma suposição sobre o conteúdo desse valor.  
  
 pChangesData  
 [in] Ponteiro para uma [QUERYCHANGESDATA estrutura](#LinkQUERYCHANGESDATA) estrutura que descreve as alterações em um arquivo.  
  
## <a name="return-value"></a>Valor de retorno  
 O IDE retorna um código de erro apropriado:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Continue o processamento.|  
|SCC_I_OPERATIONCANCELED|Pare o processamento.|  
|SCC_E_xxx|Qualquer erro de SCC apropriado deve parar o processamento.|  
  
##  <a name="a-namelinkquerychangesdataa-querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a>Estrutura QUERYCHANGESDATA  
 A estrutura passada para cada arquivo é semelhante ao seguinte:  
  
```cpp#  
struct QUERYCHANGESDATA_A  
{  
    DWORD  dwSize;  
    LPCSTR lpFileName;  
    DWORD  dwChangeType;  
    LPCSTR lpLatestName;  
};  
  
typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA;  
  
struct QUERYCHANGESDATA_W  
{  
    DWORD   dwSize;  
    LPCWSTR lpFileName;  
    DWORD   dwChangeType;  
    LPCWSTR lpLatestName;  
};  
```  
  
 dwSize  
 Tamanho desta estrutura (em bytes).  
  
 lpFileName  
 O nome do arquivo original para esse item.  
  
 dwChangeType  
 Código que indica o status do arquivo:  
  
|Código|Descrição|  
|----------|-----------------|  
|`SCC_CHANGE_UNKNOWN`|Não é possível dizer o que foi alterado.|  
|`SCC_CHANGE_UNCHANGED`|Nenhuma alteração de nome para esse arquivo.|  
|`SCC_CHANGE_DIFFERENT`|Arquivo com uma identidade diferente, mas o mesmo nome existe no banco de dados.|  
|`SCC_CHANGE_NONEXISTENT`|Arquivo não existe no banco de dados ou localmente.|  
|`SCC_CHANGE_DATABASE_DELETED`|Arquivo excluído do banco de dados.|  
|`SCC_CHANGE_LOCAL_DELETED`|Arquivos excluídos localmente, mas o arquivo ainda existe no banco de dados. Se isso não puder ser determinado, retorne `SCC_CHANGE_DATABASE_ADDED`.|  
|`SCC_CHANGE_DATABASE_ADDED`|Arquivo adicionado ao banco de dados, mas não existe localmente.|  
|`SCC_CHANGE_LOCAL_ADDED`|Arquivo não existe no banco de dados e um novo arquivo local.|  
|`SCC_CHANGE_RENAMED_TO`|Arquivo renomeado ou movido no banco de dados `lpLatestName`.|  
|`SCC_CHANGE_RENAMED_FROM`|Arquivo renomeado ou movido no banco de dados de `lpLatestName`; se isso é muito caro controlar, retornar um sinalizador diferente, como `SCC_CHANGE_DATABASE_ADDED`.|  
  
 lpLatestName  
 O nome do arquivo atual para este item.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de retorno de chamada implementadas pelo IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)   
 [Códigos de erro](../extensibility/error-codes.md)
