---
title: Controlando cor, estilo de linha e outras propriedades de forma | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c06d0066-24aa-4c65-b91c-c2089b81ec8d
caps.latest.revision: 2
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
ms.openlocfilehash: 7071fcbff2e3f787ccb42a2b1987e628faaa7a9c
ms.lasthandoff: 02/22/2017

---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Controlando cor, estilo de linha e outras propriedades de formas
Algumas propriedades de forma, como cor pode ser 'exposta' – ou seja, vinculado a uma propriedade de domínio da forma. Outros têm seja controlado diretamente.  
  
## <a name="exposing-a-property"></a>Expor uma propriedade  
 Algumas propriedades da forma como cor podem ser vinculadas ao valor de uma propriedade de domínio.  
  
 Na definição de DSL, selecione uma forma, conector ou classe de diagrama. No menu de contexto, escolha **adicionar exposto**e, em seguida, escolha a propriedade que você deseja, como cor de preenchimento.  
  
 A forma agora tem uma propriedade de domínio que podem ser definidas no código do programa ou como um usuário.  
  
## <a name="dynamically-updating-an-exposed-property"></a>Atualizando dinamicamente uma propriedade exposta  
 Normalmente você deseja fazer a propriedade exposta dependente de outra propriedade. Por exemplo, convém uma forma fique vermelho sempre que uma propriedade de domínio específico é menor que zero. Para fazer essa dependência, crie uma [regra](../modeling/rules-propagate-changes-within-the-model.md). Por exemplo:  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
namespace ExampleNamespace  
{  
 // Attribute associates the rule with class:  
 [RuleOn(typeof(CarShape), FireTime = TimeToFire.TopLevelCommit)]  
 // The rule is a class derived from one of the abstract rules:  
 class CarShapeAddRule : AddRule  
 {  
 // Override the abstract method:  
 public override void ElementAdded(ElementAddedEventArgs e)  
 {  
 base.ElementAdded(e);  
 CarShape shape = e.ModelElement as CarShape;  
 Store store = shape.Store;  
 // Ignore this call if we're currently loading a model:  
 if (store.TransactionManager.CurrentTransaction.IsSerializing)   
  return;  
 Car car = shape.ModelElement as Car;  
 // Code here propagates change as required - for example:  
 shape.FillColor = car.Somebool ? System.Drawing.Color.Red : System.Drawing.Color.Green;   
 }  
}  
 // The rule must be registered:  
 public partial class ExampleDomainModel  
 {  
 protected override Type[] GetCustomDomainModelTypes()  
 {  
  List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
  types.Add(typeof(CarShapeAddRule));  
  // If you add more rules, list them here.   
  return types.ToArray();  
 }  
 }  
}  
```
