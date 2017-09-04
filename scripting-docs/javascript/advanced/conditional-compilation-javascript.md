---
title: "Compilação condicional (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ConditionalComp_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- conditional compilation, overview
- conditional compilation
ms.assetid: a843de4e-3aae-43cd-ad64-477dd00814a2
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 6d6a5987b21afcab8c62a609dfba33f963d544de
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="conditional-compilation-javascript"></a>Compilação condicional (JavaScript)
A compilação condicional permite o uso de novos recursos da linguagem [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] sem sacrificar a compatibilidade com versões anteriores que não oferecem suporte a esses recursos.  
  
> [!WARNING]
>  A compilação condicional é compatível com todas as versões do Internet Explorer anteriores ao Internet Explorer 11. A partir do modo Padrões do Internet Explorer 11, e nos aplicativos [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)], a compilação condicional não é mais aceita.  
  
## <a name="statements"></a>Instruções  
 A compilação condicional é ativada com o uso da instrução `@cc_on` ou de uma instrução `@if` ou `@set`. Alguns usos típicos da compilação condicional incluem o uso de novos recursos em [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], inserção de suporte para depuração em um script e rastreamento da execução de códigos.  
  
 Sempre insira o código de compilação condicional em comentários para que hosts (como o Netscape Navigator) que não oferecem suporte à compilação condicional possam ignorá-la. Vejamos um exemplo.  
  
```JavaScript  
/*@cc_on @*/  
/*@if (@_jscript_version >= 4)  
    alert("JavaScript version 4 or better");  
    @else @*/  
    alert("Conditional compilation not supported by this scripting engine.");  
/*@end @*/  
```  
  
 Este exemplo usa delimitadores de comentário especiais que são usados somente quando a compilação condicional é ativada pela instrução `@cc_on`. Os mecanismos de script que não dão suporte à compilação condicional enxergam apenas a mensagem informando que não há suporte à compilação condicional.
