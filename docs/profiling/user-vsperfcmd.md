---
title: "Usuário (VSPerfCmd) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
caps.latest.revision: 7
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
ms.openlocfilehash: c12dad3ef061d579d7d7c4fb3444c23018b041d1
ms.lasthandoff: 02/22/2017

---
# <a name="user-vsperfcmd"></a>Usuário (VSPerfCmd)
A opção **Usuário** especifica o domínio e o nome de usuário da conta que possui o processo com perfil. Esta opção é necessária apenas se o processo estiver sendo executado como um usuário diferente do usuário conectado. O proprietário do processo é listado na coluna Nome de Usuário na guia Processos do Gerenciador de Tarefas do Windows.  
  
 A opção **Usuário** só pode ser especificada em uma linha de comando que também contém a opção **Iniciar**.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `Domain`  
 O nome do domínio do usuário.  
  
 `UserName`  
 O nome do usuário.  
  
## <a name="required-options"></a>Opções obrigatórias  
 A opção **Usuário** só pode ser usada com a opção **Iniciar**.  
  
 **Iniciar:** `Method`  
 Inicializa o criador de perfil para o método de criação de perfil especificado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra o uso da opção **Usuário**.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM  
```  
  
## <a name="see-also"></a>Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de Criação de Perfil](../profiling/command-line-profiling-of-services.md)
