---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.InvalidCastException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Classe InvalidCastException"
ms.assetid: a855dfe1-5c06-45a6-9c2f-c9e799ccf8f0
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.InvalidCastException
Um <xref:System.InvalidCastException> exceção é lançada quando ocorre uma falha durante uma conversão de referência explícita. Conversões de referência são conversões de tipo de uma referência para outro. Embora elas possam alterar o tipo de referência, eles nunca altere o tipo ou valor de destino da conversão. Objetos de conversão de um tipo para outro é uma causa frequente dessa exceção.  
  
## Dicas associadas  
 **Verifique os tipos de origem em relação aos tipos de destino para certificar\-se de que a conversão é válida.**  
 Para obter informações sobre conversões com suporte pelo sistema, consulte <xref:System.Convert>.  
  
## Comentários  
 Para uma conversão de referência explícita seja bem\-sucedida, o valor de origem deve ser Null \(`Nothing` no Visual Basic\), ou o tipo de objeto referenciado pelo argumento de origem deve ser conversível para o tipo de destino por uma conversão implícita de referência.  
  
 Quando um aplicativo Visual Basic 6.0 com uma chamada para um evento personalizado em um controle de usuário é atualizado para uma versão mais recente do Visual Basic e executada, essa exceção pode ocorrer com as informações adicionais, "conversão especificada não é válido." Para resolver esse erro, localize a seguinte linha de código em `Form1`:  
  
 `Call UserControl11_MyCustomEvent(UserControl11, New UserControl1.MyCustomEventEventArgs(5))`  
  
 E substitua por:  
  
 `Call UserControl11_MyCustomEvent(UserControl11(0), New UserControl1.MyCustomEventEventArgs(5))`  
  
## Consulte também  
 <xref:System.InvalidCastException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Como converter um objeto em outro tipo no Visual Basic](../Topic/How%20to:%20Convert%20an%20Object%20to%20Another%20Type%20in%20Visual%20Basic.md)   
 [Converting Strings to .NET Framework Data Types](../Topic/Converting%20Strings%20to%20.NET%20Framework%20Data%20Types.md)   
 [Como implementar conversões definidas pelo usuário entre structs](../Topic/How%20to:%20Implement%20User-Defined%20Conversions%20Between%20Structs%20\(C%23%20Programming%20Guide\).md)