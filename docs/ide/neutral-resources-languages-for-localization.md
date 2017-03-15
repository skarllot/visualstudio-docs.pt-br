---
title: "Idiomas de recursos neutros para localização | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- localization [Visual Studio], resources
- NeutralResourcesLanguageAttribute class
- globalization [Visual Studio], resources
- resources [Visual Studio], fallback system
- culture, locating resources
- neutral resources
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
caps.latest.revision: 8
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
ms.openlocfilehash: 3000cf25ec1f070171185511a571abaaaecd5fac
ms.lasthandoff: 02/22/2017

---
# <a name="neutral-resources-languages-for-localization"></a>Idiomas de recursos naturais para localização
A classe <xref:System.Resources.NeutralResourcesLanguageAttribute> especifica a cultura dos recursos incluídos no assembly principal. Esse atributo é usado como um aperfeiçoamento de desempenho, de modo que o objeto <xref:System.Resources.ResourceManager> não pesquise por recursos incluídos no assembly principal.  
  
 O código a seguir mostra como definir o idioma de recursos neutros. O código pode ser colocado em um script de build ou no arquivo AssemblyInfo.vb ou AssemblyInfo.cs.  
  
```vb#  
' Set neutral resources language for assembly.  
<Assembly: NeutralResourcesLanguageAttribute("en")>  
  
```  
  
```c#  
// Set neutral resources language for assembly.  
[assembly: NeutralResourcesLanguageAttribute("en")]  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Resources.ResourceManager>   
 [Introdução a aplicativos internacionais com base no .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Organização hierárquica de recursos para localização](../ide/hierarchical-organization-of-resources-for-localization.md)   
 [Localizando aplicativos](../ide/localizing-applications.md)   
 [Globalizando e localizando aplicativos](../ide/globalizing-and-localizing-applications.md)
