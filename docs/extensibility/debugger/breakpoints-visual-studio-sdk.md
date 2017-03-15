---
title: "Pontos de interrupção (SDK do Visual Studio) | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: fd0eccfa45f20217291b2e00eb175f8eac49d42d
ms.lasthandoff: 02/22/2017

---
# <a name="breakpoints-visual-studio-sdk"></a>Pontos de interrupção (SDK do Visual Studio)
Há três tipos de pontos de interrupção: pendentes associadas e erro.  
  
 **Um ponto de interrupção:**  
  
-   É uma abstração que contém todas as informações necessárias para associar um ponto de interrupção para um ou mais contextos de código em um ou mais programas. Cada vez que um programa que está sendo depurado causa o código para carregar, o mecanismo de depuração verifica todos os pontos de interrupção pendentes para ver se eles podem ser associados.  
  
     Um ponto de interrupção pendente em si nunca associa ao código, mas em vez disso, coleta e deve conter a interrupção acoplada que ele gera.  
  
-   É representado por um [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interface.  
  
 **Um ponto de interrupção associado:**  
  
-   É uma abstração para um ponto de interrupção associada ou associada a um contexto de código única. Cada ponto de interrupção associado é gerado em resposta a um ponto de interrupção pendente. Um ponto de interrupção pendente no entanto, pode gerar mais de um ponto de interrupção associado.  
  
     Quando o código é descarregado, um ponto de interrupção associado pode ser desacoplado e descartado.  
  
-   É representado por um [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) interface.  
  
 **Um ponto de interrupção de erro:**  
  
-   É uma abstração para descrever um erro ao tentar associar um ponto de interrupção pendente para um contexto de código. Um ponto de interrupção de erro descreve um erro no local ou na expressão de ponto de interrupção em si. Para obter mais informações, consulte [pontos de interrupção de associação](../../extensibility/debugger/binding-breakpoints.md).  
  
     O erro de ponto de interrupção pode ser um erro ou um aviso.  
  
-   É representado por um [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) interface.  
  
## <a name="see-also"></a>Consulte também  
 [Programas](../../extensibility/debugger/programs.md)   
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Contexto de código](../../extensibility/debugger/code-context.md)   
 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
