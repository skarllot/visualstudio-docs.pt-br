---
title: Portas | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: 13
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
ms.openlocfilehash: ab9cd15b5f121b45c138e7c5854dbf74cd42156d
ms.lasthandoff: 02/22/2017

---
# <a name="ports"></a>Portas
Em termos de arquitetura do depurador, uma **porta**:  
  
-   Um contêiner para um conjunto de processos em execução em um servidor. Por exemplo, uma porta pode representar uma conexão para um dispositivo baseado em Windows CE por um cabo serial ou para uma máquina não-DCOM em rede. Uma porta especial, chamada de porta local, contém todos os processos em execução na máquina local.  
  
-   Pode identificar-se por nome ou identificador.  
  
-   Pode enumerar todos os processos em execução na porta e iniciar e encerrar esses processos.  
  
-   É representado por um [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interface, que é criada, passando um [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) argumento [adicionar porta](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Fornece uma porta padrão que lida com processos de todos os baseados em Windows, nativos e gerenciados. Uma porta personalizada deve ser implementada para conexões com dispositivos externos que não são baseados em Windows. Para fornecer essas portas personalizadas, um fornecedor de porta personalizada também precisa ser implementado.  
  
## <a name="see-also"></a>Consulte também  
 [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Processos](../../extensibility/debugger/processes.md)   
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [Adicionar porta](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
