---
title: "Renomear n&#243;s de hierarquia de projeto (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Exemplo de HierUtil7 [Visual Studio SDK], renomeando nós do projeto"
  - "nós do projeto, renomeando exemplo HierUtil7"
ms.assetid: cea5968e-e9f8-41a5-b068-622df542247c
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Renomear n&#243;s de hierarquia de projeto (C++)
Você pode renomear um nó de hierarquia de pasta do projeto, usando a estrutura de projeto de HierUtil7 para C\+\+ não gerenciado.  Para obter mais informações, consulte [HierUtil7 Sample](http://msdn.microsoft.com/pt-br/29c15184-a70c-4813-86c2-fb1d47442d11).  
  
## Expandindo o nó da hierarquia  
  
#### Para expandir o nó da hierarquia e renomeie a pasta  
  
1.  Selecione o nó da hierarquia, usando o método a seguir:  
  
    ```  
    IfFailGo(pNode->ExtExpand(EXPF_SelectItem, GUID_MacroExplorer));  
    ```  
  
     `pNode`é o recipiente de hierarquia que corresponde à pasta e `EXPF_SelectItem` é proveniente do <xref:Microsoft.VisualStudio.Shell.Interop.EXPANDFLAGS> enumeração.  O `GUID_MacroExplorer` é uma constante GUID definida em Vsshell.idl e é um exemplo para `rguidPersistenceSlot` na assinatura de função do `ExtExpand`, definido em Hu\_node.h.  
  
    ```  
    HRESULT ExtExpand(EXPANDFLAGS expandflags, REFGUID rguidPersistenceSlot = GUID_SolutionExplorer) const;  
    ```  
  
     Você pode encontrar o arquivo Hu\_node.h na pasta, \< raiz da instalação \> \\Program Files\\VSIP 8.0\\EnvSDK\\common\\hierutil7:  
  
2.  Renomeie a pasta pelo lançamento de usando o comando rename<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.PostExecCommand%2A>  
  
    ```  
    IfFailGo(srpVsUIShell->PostExecCommand(&guidVSStd97, cmdidRename, 0, NULL));  
    ```  
  
     `srpVsUIShell`is a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> pointer: `<IVsUIShell>``srpVsUIShell`.  `guiVSStd97`é um identificador exclusivo do grupo ao qual comando o comando `cmdidRename` pertence, definido em Vsshlids.h.  
  
## Consulte também  
 [Criando tipos de projeto](../extensibility/internals/creating-project-types.md)   
 [Exemplos VSSDK](../misc/vssdk-samples.md)