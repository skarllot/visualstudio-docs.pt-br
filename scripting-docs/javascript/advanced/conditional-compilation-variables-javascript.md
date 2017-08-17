---
title: "Variáveis de compilação condicional (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- conditional compilation, variables
ms.assetid: d6f9827d-c558-412c-8e68-de04c19c3d9d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 900a44dab0ad418cd2899af6423f78016c90fe2b
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="conditional-compilation-variables-javascript"></a>Variáveis de compilação condicional (JavaScript)
As variáveis predefinidas a seguir estão disponíveis para compilação condicional. Se uma variável não for **true**, ela não será definida e não se comportará como `NaN` ao ser acessada.  
  
> [!WARNING]
>  A compilação condicional é compatível com todas as versões do Internet Explorer anteriores ao Internet Explorer 11. A partir do modo Padrões do Internet Explorer 11, e nos aplicativos [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)], a compilação condicional não é mais aceita.  
  
## <a name="variables"></a>Variáveis  
  
|Variável|Descrição|  
|--------------|-----------------|  
|@_win32|True se estiver em execução em um sistema Win32.|  
|@_win16|True se estiver em execução em um sistema Win16.|  
|@_mac|True se estiver em execução em um sistema Apple Macintosh.|  
|@_alpha|True se estiver em execução em um processador DEC Alpha.|  
|@_x86|True se estiver em execução em um processador Intel.|  
|@_mc680x0|True se estiver em execução em um processador Motorola 680x0.|  
|@_PowerPC|True se estiver em execução em um processador Motorola PowerPC.|  
|@_jscript|Sempre true.|  
|@_jscript_build|Contém o número de compilação do mecanismo de script do [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].|  
|@_jscript_version|Contém o número da versão do [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] no formato principal.secundária.|
