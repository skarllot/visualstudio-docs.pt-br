---
title: "Saída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
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
ms.openlocfilehash: 47819b963b0e4a3a63649cd27b6b077dc30f6f2b
ms.lasthandoff: 02/22/2017

---
# <a name="output"></a>Saída
A opção **Saída** especifica o nome do arquivo de dados de criação de perfil para a sessão de desempenho. **Saída** deve ser usado com a opção **Iniciar**.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `FileName`  
 O nome do arquivo de dados. Caminhos completos e parciais são aceitos. Se um caminho não for especificado, o arquivo será criado no diretório atual.  
  
## <a name="required-options"></a>Opções obrigatórias  
 A opção **Saída** deve ser usada com a opção **Iniciar**.  
  
 **Iniciar:** `Method`  
 Especifica o nome do arquivo de saída.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o arquivo de dados de criação de perfil é criado no diretório atual.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
```  
  
## <a name="see-also"></a>Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de Criação de Perfil](../profiling/command-line-profiling-of-services.md)
