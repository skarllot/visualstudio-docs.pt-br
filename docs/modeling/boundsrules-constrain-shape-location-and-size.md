---
title: BoundsRules restringem o local de forma e tamanho | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, events
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: 18
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 8a611bd18cb06b712f671d370bfc26d4dc8cf4f3
ms.lasthandoff: 02/22/2017

---
# <a name="boundsrules-constrain-shape-location-and-size"></a>BoundsRules restringem o local e o tamanho de uma forma
A *limites regra* é uma classe que define limites sobre o tamanho e a localização de uma forma. Ele fornece um método é chamado repetidamente enquanto um usuário está arrastando uma forma ou cantos ou lados de uma forma.  
  
 O exemplo a seguir limita uma forma retangular com uma barra de tamanho fixo, horizontal ou vertical. Quando o usuário arrasta o cantos ou lados, a estrutura de tópicos gira entre as duas configurações permitidas de altura e largura.  
  
 A regra de associação é uma classe derivada de <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>.</xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules> Uma instância da regra é criada da forma:  
  
```  
using Microsoft.VisualStudio.Modeling.Diagrams; ...  
public partial class BarShape  
{  
  /// <summary>  
  /// Rule invoked when the user is resizing a shape.  
  /// </summary>  
  public override BoundsRules BoundsRules  
  { get { return new BarBoundsRule(); } }  
}  
/// <summary>  
/// Rule invoked when the user is changing a shape's outline.  
/// Provides real-time mouse rubber-band feedback, so must work fast.  
/// </summary>  
public class BarBoundsRule: BoundsRules  
{   
  public override RectangleD GetCompliantBounds   
     (ShapeElement shape, RectangleD proposedBounds)  
  {  
    double thickness = 0.1;  
    if (proposedBounds.Height > proposedBounds.Width)  
    {  
      // There is a minimum width for a shape; the width  
      // will actually be set to the lesser of   
      // thickness and that minimum.  
      return new RectangleD(proposedBounds.Location,   
            new SizeD(thickness, proposedBounds.Height));  
    }  
    else  
    {  
      // There is a minimum height for a shape; the   
      // height will actually be set to the lesser of   
      // thickness and that minimum.  
      return new RectangleD(proposedBounds.Location,   
         new SizeD(proposedBounds.Width, thickness));  
} } }  
```  
  
 Observe que o local e o tamanho podem ser limitadas se desejar.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules></xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>   
 [Respondendo a alterações e propagando-as](../modeling/responding-to-and-propagating-changes.md)
