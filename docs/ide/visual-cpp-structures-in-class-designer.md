---
title: Estruturas do Visual C++ no Designer de Classe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 11
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
ms.openlocfilehash: a71ab225aa28e75c4e996bb1cda3d165b9fd91d9
ms.lasthandoff: 02/22/2017

---
# <a name="visual-c-structures-in-class-designer"></a>Estruturas do Visual C++ no Designer de Classe
O Designer de Classe dá suporte a estruturas C++ declaradas com a palavra-chave `struct`. Veja um exemplo a seguir:  
  
```  
struct MyStructure  
{  
   char a;  
   int i;  
   long j;  
};  
```  
  
 Para obter mais informações sobre o uso do tipo `struct`, consulte [struct](/visual-cpp/cpp/struct-cpp).  
  
 Uma forma de estrutura C++ em um diagrama de classe parece uma forma de classe e funciona como uma, exceto que o rótulo lê **Struct** e tem cantos quadrados em vez de arredondados.  
  
|Elemento de código|Modo de exibição do Designer de Classe|  
|------------------|-------------------------|  
|`struct StructureName {};`|**StructureName**<br /><br /> Estrutura|  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com código do Visual C++ (Designer de Classe)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [Classes e structs](/visual-cpp/cpp/classes-and-structs-cpp)   
 [struct](/visual-cpp/cpp/struct-cpp)
