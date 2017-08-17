---
title: "Representações de DateTime e TimeSpan do Windows Runtime | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime dates and times
- TimeSpan [JavaScript]
- DateTime [JavaScript]
ms.assetid: 9743e9ac-9054-463e-8264-427183e4905f
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 3d7c394b57eb0215e3dff857d935b367e602c2b0
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="windows-runtime-datetime-and-timespan-representations"></a>Representações de DateTime e TimeSpan do Windows Runtime
A representação em JavaScript das datas e das horas é diferente da versão do Tempo de Execução do Windows. A estrutura [DateTime](http://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx) do Windows Runtime é representada em JavaScript como um [Date](../javascript/reference/date-object-javascript.md) com um repositório de backup correspondente aos dados `DateTime` (e tem um intervalo e uma precisão diferentes em relação ao JavaScript `Date`). Se você modificar esse objeto `Date` personalizado, ele se tornará um `Date` JavaScript padrão e perderá a precisão. Os valores `Date` JavaScript podem ser passados para um `DateTime` do Tempo de Execução do Windows, o que pode resultar em exceções de marshaling.  
  
 A estrutura [TimeSpan](http://msdn.microsoft.com/en-us/c5defb66-819c-4796-85b5-07ed249a5d86) do Windows Runtime é convertida em milissegundos e retornada como um número JavaScript.  
  
## <a name="see-also"></a>Consulte também  
 [Usar o Windows Runtime em JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)
