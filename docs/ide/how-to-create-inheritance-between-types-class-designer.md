---
title: "Como criar herança entre tipos (Designer de Classe) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
caps.latest.revision: 30
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: bd4969c26d1cc0043945189bd4da3acbf5792107
ms.contentlocale: pt-br
ms.lasthandoff: 05/13/2017

---
# Como criar herança entre tipos (Designer de Classe)
<a id="how-to-create-inheritance-between-types-class-designer" class="xliff"></a>
Para criar uma relação de herança entre dois tipos em um diagrama de classes usando o Designer de Classe, conecte o tipo de base ao seu tipo ou tipos derivados. Você pode ter uma relação de herança entre duas classes, entre uma classe e uma interface ou entre duas interfaces.  
  
### Para criar uma herança entre tipos
<a id="to-create-an-inheritance-between-types" class="xliff"></a>  
  
1.  No seu projeto localizado no Gerenciador de Soluções, abra um arquivo de diagrama de classes (.cd).  
  
     Se você não possuir um diagrama de classes, crie um. Consulte [Como adicionar diagramas de classe a projetos (Designer de Classe)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).  
  
2.  Na **Caixa de Ferramentas**, no **Designer de Classe**, clique em **Herança**.  
  
3.  No diagrama de classes, desenhe uma linha de herança entre os tipos que você deseja, começando de:  
  
    -   Uma classe derivada para uma classe base  
  
    -   Uma classe de implementação para uma interface implementada  
  
    -   Uma interface em extensão para uma interface estendida  
  
4.  Se desejar, quando você tiver um tipo derivado de um tipo genérico, clique na linha de herança. Na janela **Propriedades**, defina a propriedade **Argumentos de Tipo** para corresponder ao tipo que você deseja para o tipo genérico.  
  
    > [!NOTE]
    >  Se uma classe abstrata pai contiver pelo menos um membro abstrato, todos os membros abstratos serão implementados como classes de herança não abstratas.  
    >   
    >  Embora você possa visualizar os tipos genéricos existentes, não é possível criar novos tipos genéricos. Você também não pode alterar os parâmetros de tipos genéricos existentes.  
  
## Consulte também
<a id="see-also" class="xliff"></a>  
 [Herança](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)   
 [Noções básicas sobre herança](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Como exibir herança entre tipos (Designer de Classe)](../ide/how-to-view-inheritance-between-types-class-designer.md)   
 [Classes do Visual C++ no Designer de Classe](../ide/visual-cpp-classes-in-class-designer.md)
