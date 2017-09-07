---
title: "Usando o modelo de automação | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 82a9c2068bdd3e234bcc53ffa870ca289289d690
ms.contentlocale: pt-br
ms.lasthandoff: 09/06/2017

---
# <a name="using-the-automation-model"></a>Usando o modelo de automação
Depois de conectar seu VSPackage para automação, você pode obter as propriedades e métodos chamando o <xref:EnvDTE.DTEClass.GetObject%2A> método o <xref:EnvDTE._DTE> objeto, passando uma cadeia de caracteres que representa o objeto que você deseja recuperar.  
  
## <a name="obtaining-project-objects"></a>Obtendo objetos do projeto  
 A seguir estão dois exemplos de código que mostram como um consumidor de automação obtém o projeto de objetos de automação. Para obter informações sobre como obter o objeto DTE, consulte [como: obter referências aos objetos DTE2 e DTE](http://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).  
  
```vb  
Sub DoAutomation()  
    Dim MyProjects As Projects  
    MyProjects = DTE.GetObject("AcmeProject")  
End Sub  
```  
  
```cpp  
void DoAutomation(void)  
{  
  CComQIPtr<Projects> pMyPkg; // Use an IDispatch-derived object type.  
    pMyPkg = pDTE->GetObject("AcmeProjects");   
  
   // The '=' performs a Query Interface.  
   // Assumes pDTE is already available as a global.  
   // Use pMyPkg to access your projects object's properties and methods.  
}  
  
```  
  
 Neste ponto, você pode usar os objetos do projeto padrão que fazem parte de um VSPackage específico para mover para baixo o modelo de hierarquia.  
  
 O exemplo de código a seguir mostra como obter um objeto personalizado que é uma propriedade de um tipo de projeto personalizados.:  
  
```vb  
Dim MyPrj As Project  
Dim MyPrjItem As ProjectItem  
Dim objMyObject as MyExtendedObject  
  
MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project  
objMyObject = MyPrj.Object 'You call .Object to get to special Project  
                           'implementation  
objMyObject.MySpecialMethodOrProperty  
```  
  
 O código a seguir lista os nomes de todas as propriedades de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente **geral** opção o **ferramentas** menu:  
  
```vb  
dim objDTE  
dim objEnv  
set objDTE = CreateObject("VisualStudio.DTE")  
set objEnv = objDTE.Properties("Environment", "General")  
for each obj in ObjEnv  
MsgBox obj.Name  
Next  
  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:EnvDTE.DTEClass.GetObject%2A>
