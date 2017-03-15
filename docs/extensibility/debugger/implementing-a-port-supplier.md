---
title: Implementando um fornecedor de porta | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: 11
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
ms.openlocfilehash: 1796ac44f798028ffd37047cef1c09bb191d574d
ms.lasthandoff: 02/22/2017

---
# <a name="implementing-a-port-supplier"></a>Implementando um fornecedor de porta
Um fornecedor de porta fornece portas de solicitação para o Gerenciador de sessão de depuração (SDM). Um fornecedor de porta deve ser implementado durante a depuração de uma máquina não-DCOM ou quando um novo dispositivo precisa de suporte. Por exemplo, para fornecer a depuração para um telefone celular, você pode implementar um fornecedor de porta que fornece portas que conectar-se para o telefone celular (talvez por meio de Infravermelho ou uma conexão de célula) e enumera os processos e programas em execução no telefone.  
  
 Para depuração de programas em computadores baseados no Windows (incluindo a depuração remota), o Visual Studio fornece fornecedores de porta para nativo e processos de Common Language Runtime (CLR), portanto, não há necessidade de implementar seu próprio fornecedor de porta nesses casos.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Implementando e registrando um fornecedor de porta](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 Discute como o SDM interage com o fornecedor de porta e as portas.  
  
 [Interfaces de fornecedor porta necessária](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Documenta as interfaces que devem ser implementadas para obter um fornecedor de porta.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)  
 Descreve os principais conceitos de arquiteturas de depuração.  
  
## <a name="see-also"></a>Consulte também  
 [Extensibilidade do depurador do Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
