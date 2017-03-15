---
title: "Como substituir parâmetros em um modelo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- template parameters, substituting
- Visual Studio templates, using parameters
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: 14
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 74a57f5b85e8365bd969056e23c0be42148cd598
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-substitute-parameters-in-a-template"></a>Como substituir parâmetros em um modelo
Você pode substituir parâmetros de modelo, como nomes de classes e namespaces, quando um arquivo baseado em um modelo for criado. Para ver uma lista completa dos parâmetros de modelo, consulte [Parâmetros de Modelo](../ide/template-parameters.md).  
  
## <a name="procedure"></a>Procedimento  
 Você pode substituir parâmetros nos arquivos de um modelo sempre que um projeto baseado nesse modelo for criado. Este procedimento explica como criar um modelo que substitui o nome de um namespace pelo nome do projeto seguro quando um novo projeto for criado com o modelo.  
  
#### <a name="to-use-a-parameter-to-replace-namespace-name-with-the-project-name"></a>Para usar um parâmetro para substituir o nome do namespace pelo nome do projeto  
  
1.  Insira o parâmetro em um ou mais dos arquivos de código no modelo. Por exemplo:  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
    > [!NOTE]
    >  Parâmetros de modelo são escritos no formato $*parâmetro*$.  
  
2.  No arquivo .vstemplate do modelo, localize o elemento `ProjectItem` que inclui esse arquivo.  
  
3.  Defina o atributo `ReplaceParameters` como `true` para o elemento `ProjectItem`. Por exemplo:  
  
    ```  
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)   
 [Parâmetros de modelo](../ide/template-parameters.md)   
 [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Elemento ProjectItem (Modelos de item do Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
