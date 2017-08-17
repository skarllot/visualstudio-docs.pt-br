---
title: VSPerfASPNetCmd | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: f9e9f895-57bb-41e8-8bd1-cdaa738ec220
caps.latest.revision: 6
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
ms.translationtype: HT
ms.sourcegitcommit: 223750aef8d997c6ae017f49ea0a9522bdba72bc
ms.openlocfilehash: ab57983a9dec6ce00e9edef4027b2a23f47d2ae1
ms.contentlocale: pt-br
ms.lasthandoff: 08/10/2017

---
# <a name="vsperfaspnetcmd"></a>VSPerfASPNetCmd
A ferramenta de linha de comando **VSPerfASPNetCmd.exe** permite que você crie o perfil de sites do ASP.Net sem exigir que você defina variáveis de ambiente ou reinicie o computador. Use **VSPerfASPNetCmd.exe** em vez de [VSPerfCmd](../profiling/vsperfcmd.md) quando estiver criando o perfil de sites do ASP.NET e não precisar da funcionalidade adicional fornecida pelo **VSPerfCmd**. Para obter mais informações sobre o **VSPerfASPNetCmd**, consulte [Criação de perfil do site rápida com VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md). **VSPerfASPNetCmd** é a ferramenta de linha de comando de preferência para usar quando estiver usando o criador de perfil autônomo para criar o perfil de sites Web ASP.NET.  
  
## <a name="syntax"></a>Sintaxe  
 **vsperfaspnetcmd** [/*Options*] *Website*  
  
## <a name="options"></a>Opções  
  
|Opção|Descrição|  
|------------|-----------------|  
|**/Sample** ou **/s**|Cria perfil de site usando o método de amostragem. **/Sample** é o método padrão. /Sample não pode ser usado com **/Trace**.|  
|**/Trace** ou **/t**|Cria perfil de site usando o método de instrumentação. /Trace não pode ser usado com **/Sample**.|  
|**/Memory**[**:**`Type`]or   **/m**[**:**{**a**&#124;**l**}]|Cria perfil de alocação de memória e, opcionalmente, cria perfil de tempos de vida do objeto (coleta de lixo). **/Memory** pode ser usado com o método de amostragem ou instrumentação.<br /><br /> *Tipo* pode ser um dos seguintes:<br /><br /> -   **alocação** (ou **a**) coleta apenas dados de alocação de memória.<br />-   **tempo de vida** (ou **l**) coleta dados de alocação de memória e de tempo de vida do objeto.<br /><br /> O `Type` padrão é **alocação**.|  
|**/Tip** ou **/i**|Adiciona informações detalhadas de solicitação ASP.NET e de chamada de ADO.NET para os dados de criação de perfil. **/Tip** pode ser usado com o método de amostragem ou instrumentação e pode ser usado com a opção **/Memory**.|  
|**/Output:** `File` ou   **/o:**`File`|Especifica o nome e o caminho do arquivo de dados de criação de perfil (.vsp).|  
|**/NoWait** ou **/n**|Retorna o prompt de comando imediatamente para que os comandos adicionais possam ser usados na janela do prompt de comando. Você deve digitar **VSPerfASPNETCmd /Shutdown** em uma linha de comando separada para desativar a criação de perfil.|  
|**/PackSymbols**[:{**on**&#124;**off**}ou   **/p**[:{**on**&#124;**off**}|Incorpora símbolos (nomes de parâmetro e função etc.) no arquivo de dados de criação de perfil (.vsp).|  
|**/Shutdown:** `Website`ou **/d:**`Website`|Desativa a criação de perfil. Use como a única opção na linha de comando depois de usar a opção **/NoWait** para iniciar a criação de perfil ou se o criador de perfil encerrar inesperadamente. Especifique a mesma URL que você usou no comando original **VSPerfASPNETCmd**.|  
|`Website`|A URL do site para criação de perfil.|  
  
## <a name="see-also"></a>Consulte também  
 [Criação de perfil de site rápida com VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)   
 [Criando perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)

