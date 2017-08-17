---
title: "Propriedades de erro especial de métodos assíncronos do Windows Runtime | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45155584-06d8-4e7f-93a6-8564a93f643d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 120d8f699c8bedd0fe5762300203c5d5ec18e73e
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="special-error-properties-from-asynchronous-windows-runtime-methods"></a>Propriedades de erro especial de métodos assíncronos do Windows Runtime
Pode ser difícil depurar os métodos assíncronos do Windows Runtime em JavaScript, porque o erro pode ser gerado de algum ponto aprofundado na pilha de chamadas. O objeto JavaScript `Error` tem propriedades adicionais que aparecem somente quando o erro é gerado de um método assíncrono do Windows Runtime quando o aplicativo está sendo executado no modo de depuração.  
  
## <a name="special-error-properties"></a>Propriedades de erro especiais  
 Um objeto de erro que resulta de uma operação assíncrona do Windows Runtime com falha no modo de depuração tem as seguintes propriedades especiais:  
  
-   `asyncOpSource` (Objeto) Obtém informações sobre o local original em que a chamada que produziu um erro foi feita. A propriedade `asyncOpSource.originatingCall` (cadeia de caracteres) exibe o local no código do usuário que originou a operação assíncrona.  
  
-   asyncOpType (cadeia de caracteres) obtém o nome do tipo de operação assíncrona que gerou o erro.  
  
 Para obter mais informações sobre erros com operações assíncronas, consulte:  
  
-   [Como manipular erros com promessas](https://msdn.microsoft.com/en-us/library/windows/apps/hh700337.aspx)  
  
-   [Solução de problemas de erros do Windows Runtime](http://msdn.microsoft.com/en-us/1ef7d7df-82ac-441d-8ad0-54ab1318de64)
