---
title: Comandos e Menus que usam Assemblies de interoperabilidade | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
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
ms.openlocfilehash: c0d2cf9218743ec21121d849482e5a3086b36ab2
ms.lasthandoff: 02/22/2017

---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Comandos e Menus que usam Assemblies de interoperabilidade
Um VSPackage que implementa os comandos de menu e barra de ferramentas usando assemblies de interoperabilidade deve:  
  
-   Informar o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE) sobre os comandos que ele oferece suporte e se elas estão habilitadas.  
  
-   Aderir às regras (contrato) de manipulação de comandos.  
  
-   Implementar manipulação de comando explicitamente, usando o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>  
  
 O seguinte descreve como realizar essas tarefas.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Determinar o Status de comando usando Assemblies de interoperabilidade](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 Descreve como um VSPackage notifica o IDE sobre quais comandos dá suporte e se elas estão habilitadas.  
  
 [Comando contratos em Assemblies de interoperabilidade](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Fornece uma definição de contrato comando básico usado por todos os VSPackages implementando comandos usando assemblies de interoperabilidade  
  
 [Implementação](../../extensibility/internals/command-implementation.md)  
 Fornece uma visão geral de como um VSPackage implementa um comando.  
  
 [Registrando manipuladores de comandos do Assembly de interoperabilidade](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 Descreve as entradas do registro necessárias para notificar o IDE um VSPackage fornece um manipulador de comandos.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Disponibilidade](../../extensibility/internals/command-availability.md)  
 Descreve os critérios que serão usados pelo IDE para determinar quais comandos VSPackage estão disponíveis e qual objeto lida com eles.  
  
 [Como os VSPackages adicionar elementos de Interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Fornece detalhes sobre como criar uma interface do usuário que usa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] suporte de comando.  
  
 [Roteamento de comando em VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)  
 Visão geral do processo usado para relacionar um objeto com a solicitação de comando correto.
