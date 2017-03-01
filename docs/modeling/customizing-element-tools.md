---
title: Personalizando o elemento ferramentas | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: 6
author: alancameronwills
ms.author: awills
manager: douge
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
ms.openlocfilehash: 454656fc0f00898578078174f5d9bc6ffa7bae89
ms.lasthandoff: 02/22/2017

---
# <a name="customizing-element-tools"></a>Ferramentas de elemento personalizadas
Em algumas definições de DSL, você pode representar um conceito único como um grupo de elementos. Por exemplo, se você criar um modelo no qual um componente tem um conjunto fixo de portas, você sempre quer que as portas a serem criados no mesmo momento que o componente pai. Portanto, você precisa personalizar a ferramenta de criação de elemento para que ele cria um grupo de elementos em vez de apenas uma. Para fazer isso, você pode personalizar como a ferramenta de criação do elemento é inicializada.  
  
 Você também pode substituir o que acontece quando a ferramenta é arrastada para o diagrama ou um elemento.  
  
## <a name="customizing-the-content-of-an-element-tool"></a>Personalizar o conteúdo de uma ferramenta de elemento  
 Cada ferramenta do elemento armazena uma instância de um <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>(EGP), que contém uma versão serializada de um ou mais elementos de modelo e links.</xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> Por padrão, o EGP de uma ferramenta de elemento contém uma instância da classe que você especificar para a ferramenta. Você pode alterar isso substituindo *YourLanguage*`ToolboxHelper.CreateElementToolPrototype`. Esse método é chamado quando o pacote DSL é carregado.  
  
 Um parâmetro do método é a ID da classe que você especificou na definição de DSL. Quando o método é chamado com a classe que você está interessado, você pode adicionar elementos adicionais para o EGP.  
  
 O EGP deve incluir a incorporação de links de um elemento principal para os elementos da subsidiária. Ele também pode incluir links de referência.  
  
 O exemplo a seguir cria um elemento principal e dois elementos incorporados. A classe principal é chamada Resistor, e ele tem duas relações de incorporação para elementos nomeados Terminal. Propriedades da função incorporação são denominadas Terminal1 e Terminal2, e ambos tenham uma multiplicidade de 1..1.  
  
```  
using Microsoft.VisualStudio.Modeling; ...    
public partial class CircuitDiagramToolboxHelper  
{  
  protected override ElementGroupPrototype    CreateElementToolPrototype(Store store, Guid domainClassId)  
  {  
    // A case for each tool to customize:    
    if (domainClassId == Resistor.DomainClassId)  
    {  
      // Set up the prototype elements and links:  
      Resistor resistor = new Resistor(store);  
      resistor.Terminal1 = new Terminal(store);   
      resistor.Terminal2 = new Terminal(store);  
      resistor.Terminal1.Name = "T1"; // embedding  
      resistor.Terminal2.Name = "T2"; // embedding  
      // We could also set up reference links.  
  
      // Create an element group prototype for the toolbox:  
      ElementGroup egp = new ElementGroup(store.DefaultPartition);  
      egp.AddGraph(resistor, true);  
      // We do not have to explicitly include embedded children.  
      return egp.CreatePrototype();  
    }  
    // Element tools for other classes:  
    else  
      return base.CreateElementToolPrototype(store, domainClassId);  
  }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Personalizando a criação e o movimento de elementos](../modeling/customizing-element-creation-and-movement.md)
