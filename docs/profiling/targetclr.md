---
title: TargetCLR | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
caps.latest.revision: 11
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
ms.openlocfilehash: eb6968192a5c116d4c88347008e398aaea00a062
ms.lasthandoff: 02/22/2017

---
# <a name="targetclr"></a>TargetCLR
A opção **TargetCLR** especifica a versão do CLR (Common Language Runtime) cujo perfil deverá ser criado quando mais de uma versão do CLR for carregada em um aplicativo.  
  
 Por padrão, as Ferramentas de Criação de Perfil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] têm como destino a primeira versão do CLR carregada pelo aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]   
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ClrVersion`  
 O número de versão do CLR. Use o formato de versão **vN.N.NNNNN**.  
  
## <a name="required-options"></a>Opções obrigatórias  
 A opção **TargetCLR** pode ser usada somente com as opções de **Inicialização** ou **Anexar**.  
  
 **Inicialize:** `AppName`  
 Inicia o aplicativo especificado e a criação de perfil.  
  
 **Anexar:** `PID`  
 Começa a criar o perfil do processo especificado.  
  
## <a name="example"></a>Exemplo  
 Nesse exemplo, a opção TargetCLR é usada para garantir que a versão 4.0.11003 do CLR tenha um perfil criado.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```
