---
title: Gerenciamento de desfazer e refazer usando a API herdada | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 14
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
ms.openlocfilehash: 1fc18f17cc8a3e68fca9cdd6d740ab1506acd3ae
ms.lasthandoff: 02/22/2017

---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>Gerenciamento de desfazer e refazer usando a API herdada
Editores devem oferecer suporte a operações de desfazer que permitem aos usuários reverter as alterações recentes ao modificar o código. A maioria dos editores implementados em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] podem ter suporte à função desfazer automaticamente fornecida pelo ambiente de desenvolvimento integrado (IDE).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como: implementar o gerenciamento de desfazer](../extensibility/how-to-implement-undo-management.md)  
 Fornece capacidade de desfazer para editores único ou vários modos de exibição.  
  
 [Como: limpar a pilha de desfazer](../extensibility/how-to-clear-the-undo-stack.md)  
 Descreve como limpar uma pilha de desfazer.  
  
 [Como: usar o gerenciamento de desfazer vinculado](../extensibility/how-to-use-linked-undo-management.md)  
 Incorpora o gerenciamento de desfazer vinculado em seu editor.  
  
## <a name="reference"></a>Referência  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager></xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Fornece gerenciamento de desfazer para um editor que oferece suporte a vários modos de exibição.  
  
## <a name="related-sections"></a>Seções relacionadas
