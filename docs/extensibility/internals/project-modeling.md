---
title: Modelagem do projeto | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
caps.latest.revision: 9
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
ms.openlocfilehash: d006e44beb55e59fbf0d2c64375fe99144023642
ms.lasthandoff: 02/22/2017

---
# <a name="project-modeling"></a>Projeto de modelagem
A próxima etapa no fornecimento de automação para seu projeto é implementar os objetos de projeto padrão: o <xref:EnvDTE.Projects>e `ProjectItems` coleções; o `Project` e <xref:EnvDTE.ProjectItem>objetos; e os demais objetos exclusivos para sua implementação.</xref:EnvDTE.ProjectItem> </xref:EnvDTE.Projects> Esses objetos padrão são definidos no arquivo Dteinternal.h. Uma implementação dos objetos padrão é fornecida no exemplo BscPrj. Você pode usar essas classes como modelos para criar seus próprios objetos de projeto padrão que suporte lado a lado com objetos de outros tipos de projeto do projeto.  
  
 Presume que um consumidor de automação para poder chamar <xref:EnvDTE.Solution>("`<UniqueProjName>")` e <xref:EnvDTE.ProjectItems>(`n`) onde n é um número de índice para a obtenção de um projeto específico na solução.</xref:EnvDTE.ProjectItems> </xref:EnvDTE.Solution> Fazer esta chamada de automação faz com que o ambiente chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A>na hierarquia de projeto apropriado, passando VSITEMID_ROOT como o parâmetro ItemID e VSHPROPID_ExtObject como parâmetro VSHPROPID.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> `IVsHierarchy::GetProperty`Retorna um `IDispatch` ponteiro para o objeto de automação, fornecendo o núcleo `Project` interface, que você tenha implementado.  
  
 A seguir está a sintaxe de `IVsHierarchy::GetProperty`.  
  
 `HRESULT GetProperty (`  
  
 `VSITEMID` `itemid`,  
  
 `VSHPROPID` `propid`,  
  
 `VARIANT` `*pvar`  
  
 `);`  
  
 Projetos acomodar o aninhamento e usam coleções para criar grupos de itens de projeto. A hierarquia tem esta aparência.  
  
```  
Projects  
  |– Project  
      |– ProjectItems (a collection of ProjectItem)  
          |– ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 Aninhar significa que uma <xref:EnvDTE.ProjectItem>objeto pode ser <xref:EnvDTE.ProjectItems>coleção ao mesmo tempo porque um `ProjectItems` coleção pode conter os objetos aninhados.</xref:EnvDTE.ProjectItems> </xref:EnvDTE.ProjectItem> O exemplo de projeto básico não Demonstre esse aninhamento. Implementando o `Project` do objeto, participar de estrutura de árvore que caracteriza o design do modelo de automação geral.  
  
 A automação de projeto segue o caminho no diagrama a seguir.  
  
 ![Objetos de projeto do Visual Studio](~/docs/extensibility/internals/media/projectobjects.gif "ProjectObjects")  
Automação de projetos  
  
 Se você implementar um `Project` do objeto, o ambiente ainda retornará um genérico `Project` objeto que contém apenas o nome do projeto.  
  
## <a name="see-also"></a>Consulte também  
 <xref:EnvDTE.Projects></xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem></xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems></xref:EnvDTE.ProjectItems>
