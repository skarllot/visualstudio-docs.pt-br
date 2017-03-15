---
title: Implementando e registrando um fornecedor de porta | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: 17
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
ms.openlocfilehash: 229269f50cfc861312b036841107386ba23917b6
ms.lasthandoff: 02/22/2017

---
# <a name="implementing-and-registering-a-port-supplier"></a>Implementando e registrando um fornecedor de porta
A função de um fornecedor de porta é controlar e fornecer portas, que por sua vez, gerenciar processos. No momento em que uma porta precisa ser criado, o fornecedor de porta é instanciado usando CoCreate com o GUID do fornecedor de porta (o Gerenciador de sessão de depuração [SDM] usará o fornecedor de porta o usuário selecionado ou o fornecedor de porta especificado pelo sistema de projeto). O SDM chamará [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) para ver se todas as portas podem ser adicionadas. Se uma porta pode ser adicionada, uma nova porta é solicitada chamando [adicionar porta](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) e passando-o um [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) que descreve a porta. `AddPort`Retorna uma nova porta representada por uma [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interface.  
  
## <a name="discussion"></a>Discussão  
 Uma porta é criada por um fornecedor de porta, que é associado a um servidor de máquina ou de depuração. Um servidor pode enumerar seus fornecedores de porta por meio de[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) método e um fornecedor de porta podem enumerar suas portas por meio de [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) método.  
  
 O registro COM típico, além de um fornecedor de porta deve se registrar com o Visual Studio colocando sua CLSID e nome em locais específicos do registro. Uma função auxiliar de depuração SDK chamado `SetMetric` manipula essa tarefa: ele é chamado uma vez para cada item a ser registrado, assim:  
  
```cpp#  
SetMetric(metrictypePortSupplier,  
          <GUID of your port supplier>,  
          metricCLSID,  
          <CLSID of your port supplier>,  
          false,  
          NULL)  
SetMetric(metrictypePortSupplier,  
          <GUID of your port supplier>,  
          metricName,  
          <name of your port supplier>,  
          false,  
          NULL);  
```  
  
 Um fornecedor de porta cancela o registro em si chamando `RemoveMetric` (outra função de auxiliar de depuração SDK) uma vez para cada item que foi registrado, assim:  
  
```cpp#  
RemoveMetric(metrictypePortSupplier,  
             <GUID of your port supplier>,  
             metricCLSID,  
             NULL);  
RemoveMetric(metrictypePortSupplier,  
             <GUID of your port supplier>,  
             metricName,  
             NULL);  
```  
  
> [!NOTE]
>  O [SDK auxiliares para depuração](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` e `RemoveMetric` são funções estáticas definidas no dbgmetric.h e compilado em ad2de.lib. O `metrictypePortSupplier`, `metricCLSID`, e `metricName` auxiliares também são definidos no dbgmetric.h.  
  
 Um fornecedor de porta pode fornecer seu nome e GUID por meio dos métodos [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) e [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), respectivamente.  
  
## <a name="see-also"></a>Consulte também  
 [Implementando um fornecedor de porta](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Auxiliares do SDK para depuração](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Fornecedores de porta](../../extensibility/debugger/port-suppliers.md)
