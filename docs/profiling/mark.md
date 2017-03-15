---
title: Marca | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 1f49bf7369f14383c6ca42e515e0c319d587ef9f
ms.lasthandoff: 02/22/2017

---
# <a name="mark"></a>Marca
A opção **Marca** do VSPerfCmd.exe insere as informações especificadas no arquivo de dados de criação de perfil. Marca pode ser listada em um relatório VSPerfReport separado ou na exibição de Relatório de marca da interface do usuário do criador de perfil. **Marca** pode ser usada para especificar os pontos inicial e final em relatórios e exibir filtros.  
  
 A opção **Marca** deve ser a única opção especificada na linha de comando.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
VSPerfCmd.exe /Mark:MarkID,[MarkName]  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `MarkID`  
 Um inteiro definido pelo usuário que está listado como a ID de marca em relatórios e exibições do criador de perfil. `MarkID` não precisa ser exclusivo.  
  
 `MarkName`  
 (Opcional) Uma cadeia de caracteres definida pelo usuário que está listada como o Nome da marca em relatórios e exibições do criador de perfil. Se `MarkName` não for especificado, o campo Nome da marca da listagem de marca estará vazio. Coloque as cadeias de caracteres que contêm espaços ou barras ("/") entre aspas.  
  
## <a name="example"></a>Exemplo  
 Este exemplo insere uma marca com uma ID de 123 e o nome da marca de "TestMark".  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## <a name="see-also"></a>Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de Criação de Perfil](../profiling/command-line-profiling-of-services.md)
