---
title: Registrando uma janela de ferramentas | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
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
ms.openlocfilehash: 81edb71b450eeee40eae4e73ba38f5db52d6eaf2
ms.lasthandoff: 02/22/2017

---
# <a name="registering-a-tool-window"></a>Registrando uma janela de ferramentas
Você pode registrar as janelas de ferramenta usando <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>e <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute></xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> </xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>  
  
## <a name="example"></a>Exemplo  
  
```c#  
  
      [ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")] [ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)] [ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]  
[ProvideMenuResource(1000, 1)]  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]  
public class PackageToolWindow : Package  
{  
```  
  
 No código acima, o <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>registra as janelas de ferramenta PersistedWindowPane e DynamicWindowPane com o Visual Studio.</xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> A janela da ferramenta persistente é encaixada e guias com **Solution Explorer**, e a janela dinâmica recebe um inicial posição e tamanho padrão. A janela dinâmica é feita transitória, que indica que ele não será criado na inicialização. Grava um valor de DontForceCreate na chave ToolWindows no registro do sistema. Para obter mais informações, consulte [configuração de exibição da janela de ferramenta](../extensibility/tool-window-display-configuration.md).
