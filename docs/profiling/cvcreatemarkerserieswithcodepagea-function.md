---
title: "Função CvCreateMarkerSeriesWithCodePageA | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cvmakers/CvCreateMarkerSeriesWithCodePageA
helpviewer_keywords:
- CvCreateMarkerSeriesWithCodePageA method
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 4a08c25082a2d555882a3c13bf149f8bac27d228

---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>Função CvCreateMarkerSeriesWithCodePageA
Cria a série de marcador para determinado provedor e uma página de código especificada. Essa função pode ser usada para especificar a página de código explicitamente para o texto gravado por funções ANSI da API do marcador. Configurar a página de código pode ser útil caso o rastreamento seja capturado e então analisado em diferentes computadores com diferentes localidades/idiomas. Por padrão, a página de código retornada pela função GetACP() é usada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CvCreateMarkerSeriesWithCodePageA(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ LPCSTR pSeriesName,  
   _In_ UINT nTextCodePage,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pProvider`  
 Objeto de provedor inicializado anteriormente por CvInitProvider. Não pode ser NULL.  
  
 `pSeriesName`  
 Nome da série de marcador. Não pode ser NULL, mas uma cadeia de caracteres vazia é permitida.  
  
 `nTextCodePage`  
 Página de código válida.  
  
 `ppMarkerSeries`  
 Endereço de uma variável de saída que armazenará o contexto de série de marcador. Não pode ser NULL.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK quando a série de marcador é criada com êxito ou código de erro no caso de erros. Use as macros SUCCEEDED/FAILED para verificar a condição de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** cvmarkers.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência de biblioteca C++](../profiling/cpp-library-reference.md)


<!--HONumber=Feb17_HO4-->


