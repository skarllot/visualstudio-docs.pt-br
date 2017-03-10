---
title: "A vers&#227;o personalizada do &#39;. ExtensionAttribute&#39; encontrada pelo compilador n&#227;o &#233; v&#225;lida | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36558"
  - "bc36558"
helpviewer_keywords: 
  - "BC36558"
ms.assetid: f47d310a-95fd-4340-bda2-21262c217dbb
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A vers&#227;o personalizada do &#39;. ExtensionAttribute&#39; encontrada pelo compilador n&#227;o &#233; v&#225;lida
A versão personalizada do '. ExtensionAttribute' encontrada pelo compilador não é válida. Seus sinalizadores de uso do atributo devem ser definidos para permitir assemblies, classes e métodos.  
  
 A versão personalizada do <xref:System.Runtime.CompilerServices.ExtensionAttribute?displayProperty=fullName> que o compilador encontrado não define seu atributo sinalizadores de uso para habilitar o aplicativo do atributo para classes, métodos e assemblies. É necessário o aplicativo pelo menos esses três elementos de programa.  
  
 **ID do erro:** BC36558  
  
### Para corrigir este erro  
  
-   Altere a definição de atributo para habilitar o atributo a ser aplicado pelo menos a assemblies, métodos e classes, conforme mostrado nos exemplos a seguir.  
  
-   Use <xref:System.Runtime.CompilerServices.ExtensionAttribute?displayProperty=fullName> em vez da versão personalizadas.  
  
## Exemplo  
 O exemplo a seguir usa o `AttributeUsage` atributo para especificar quais elementos do programa a nova versão do `ExtensionAttribute` pode aplicar a. O exemplo especifica três membros do `AttributeTargets` enumeração: `Assembly`, `Class`, e `Method`. A omissão de qualquer um desses elementos fará com que esse erro.  
  
```  
Namespace System.Runtime.CompilerServices <AttributeUsage(AttributeTargets.Assembly Or _ AttributeTargets.Class Or AttributeTargets.Method)> Class ExtensionAttribute Inherits System.Attribute ' Definitions of methods, fields, and properties. End Class End Namespace  
```  
  
 Como alternativa, você pode permitir que `ExtensionAttribute` para aplicar a todos os elementos de programa usando o `All` membro do `AttributeTargets`.  
  
```  
<AttributeUsage(AttributeTargets.All)>  
```  
  
 Excluindo o `AttributeUsage` linha, conforme mostrado no código a seguir produz o mesmo resultado.  
  
```  
Namespace System.Runtime.CompilerServices Class ExtensionAttribute Inherits System.Attribute ' Definitions of methods, fields, and properties. End Class End Namespace  
```  
  
## Consulte também  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>   
 [NÃO está em compilação: Visão geral de atributos no Visual Basic](http://msdn.microsoft.com/pt-br/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [NÃO está em compilação: Atributos personalizados no Visual Basic](http://msdn.microsoft.com/pt-br/d72d8a5c-8f64-4614-b15b-cad66845d047)   
 [Métodos de extensão](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [NÃO está em compilação: Como: definir seus próprios atributos](http://msdn.microsoft.com/pt-br/039609c4-ec43-4f44-945f-aa3b5b535c6a)   
 [Escrevendo atributos personalizados](../Topic/Writing%20Custom%20Attributes.md)