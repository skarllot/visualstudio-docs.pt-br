---
title: Como escapar caracteres especiais no MSBuild | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
caps.latest.revision: 12
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
ms.sourcegitcommit: 3ba7680d46345f2b49019659c715cfb418933d39
ms.openlocfilehash: 90f2d3d94d7073d0bc694b020496996db31b342a

---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Como escapar caracteres especiais no MSBuild
Determinados caracteres têm significado especial em arquivos de projeto do [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. O ponto e vírgula (;) e o asterisco (*) são exemplos de caracteres. Para obter uma lista completa desses caracteres especiais, consulte [Caracteres especiais do MSBuild](../msbuild/msbuild-special-characters.md).  
  
 Para usar esses caracteres especiais como literais em um arquivo de projeto, eles devem ser especificados usando a sintaxe %*xx*, em que *xx* representa o valor hexadecimal ASCII do caractere.  
  
## <a name="msbuild-special-characters"></a>Caracteres especiais no MSBuild  
 Um exemplo de quando os caracteres especiais são usados é no atributo `Include` de listas de itens. Por exemplo, a lista de itens a seguir declara dois itens: `MyFile.cs` e `MyClass.cs`.  
  
```xml  
<Compile Include="MyFile.cs;MyClass.cs"/>  
```  
  
 Se você quiser declarar um item que contém um ponto e vírgula no nome, você deverá usar a sintaxe %*xx* para escapar o ponto e vírgula e evitar que o [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] declare dois itens separados. Por exemplo, o item a seguir escapa o ponto e vírgula e declara um item denominado `MyFile.cs;MyClass.cs`.  
  
```xml  
<Compile Include="MyFile.cs%3BMyClass.cs"/>  
```  
  
#### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Para usar um caractere especial do MSBuild como um caractere literal  
  
-   Use a notação %*xx* no lugar do caractere especial, em que *xx* representa o valor hexadecimal do caractere ASCII. Por exemplo, para usar um asterisco (*) como um caractere literal, use o valor `%2A`.  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)   
 [Itens do](../msbuild/msbuild.md)
 [MSBuild](../msbuild/msbuild-items.md)


<!--HONumber=Feb17_HO4-->


