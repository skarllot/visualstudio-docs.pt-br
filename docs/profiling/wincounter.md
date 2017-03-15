---
title: WinCounter | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
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
ms.openlocfilehash: 6a2731666f926c7bea01d9fad5cc41a8c5f8787e
ms.lasthandoff: 02/22/2017

---
# <a name="wincounter"></a>WinCounter
A opção **WinCounter** especifica um contador de desempenho do aplicativo ou do Windows para coletar em intervalos definidos durante o perfil de execução. Os contadores de desempenho do aplicativo e do Windows são listados como marcas no arquivo de dados de criação de perfil. Você pode especificar vários contadores de desempenho para coletar em opções separadas.  
  
 Por padrão, os contadores são coletados a cada 500 milissegundos. Use a opção **AutoMark** para especificar um intervalo diferente de coleção.  
  
 Apenas uma opção **AutoMark** é usada. Se várias opções **AutoMark** forem especificadas, a última será usada.  
  
 A opção **WinCounter** só pode ser usada com a opção **Iniciar**.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `Path`  
 O contador de desempenho do Windows no formato de caminho de contador PDH.  
  
## <a name="required-options"></a>Opções obrigatórias  
 A opção **WinCounter** só pode ser usada com a opção **Iniciar**.  
  
 **Iniciar:** `Method`  
 A opção **Iniciar** inicializa o criador de perfil para o método de criação de perfil especificado.  
  
## <a name="exclusive-options"></a>Opções Exclusivas  
 A opção **AutoMark** só pode ser usada com a opção **WinCounter**.  
  
 **AutoMark:** `Milliseconds`  
 Especifica o número de milissegundos entre a coleta de dados do contador de desempenho do Windows.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, dois contadores de desempenho do Windows são especificados para serem coletados em um intervalo de 1000 milissegundos.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000  
```  
  
## <a name="see-also"></a>Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de Criação de Perfil](../profiling/command-line-profiling-of-services.md)
