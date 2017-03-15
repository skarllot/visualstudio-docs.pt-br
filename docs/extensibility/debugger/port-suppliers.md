---
title: Porta fornecedores | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: 15
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
ms.openlocfilehash: bd603588a47f565f7f1d177c0740c3289afc8d7e
ms.lasthandoff: 02/22/2017

---
# <a name="port-suppliers"></a>Fornecedores de porta
Em termos de arquitetura do depurador, uma **supplier porta**:  
  
-   Está contido por um servidor e fornece portas na solicitação ao servidor.  
  
-   Pode adicionar e remover portas do servidor de conteúdo.  
  
-   Pode enumerar todas as portas que ele foi fornecido para o servidor.  
  
-   É representado por um [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interface, que é registrado com o Visual Studio por meio do registro. Essa interface pode ser obtida chamando [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Fornece um fornecedor de porta padrão e uma porta padrão. Se uma porta personalizada precisa ser implementada, um fornecedor de porta personalizada também precisa ser implementada para fornecer essas portas personalizadas.  
  
## <a name="see-also"></a>Consulte também  
 [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Portas](../../extensibility/debugger/ports.md)   
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
