---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.ArgumentOutOfRangeException | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
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
  - "Classe ArgumentOutOfRangeException"
ms.assetid: f53c58d9-7c4e-407f-93d3-1e59d90d98f5
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.ArgumentOutOfRangeException
Um <xref:System.ArgumentOutOfRangeException> é lançada quando um método é chamado e pelo menos um dos argumentos passados para o método não é uma referência nula \(`Nothing` no Visual Basic\) e não contém um valor válido.  
  
## Dicas associadas  
 **Verifique se que todos os argumentos para esse método têm valores válidos conforme definido pelo método invocado.**  
 Argumentos que são referências não nulas devem conter valores válidos.  
  
 **Se você estiver trabalhando com uma coleção, certifique\-se de que o índice é menor que o tamanho da coleção.**  
 O índice deve estar dentro do intervalo de tamanho da coleção e não pode exceder o tamanho do intervalo ou ser menor que zero. Para obter mais informações, consulte [Coleções](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md).  
  
 **Ao usar os dois argumentos FindString ou FindStringExact métodos sobrecarregados da classe ComboBox ou ListBox, verifique o parâmetro startIndex**.  
 Essa exceção pode ser disparada se `startIndex` é igual ao valor de índice do último item da lista associada. Para contornar isso, passe 0 como o `startIndex` parâmetro ou use um argumento `FindString` ou `FindStringExact` método. Para obter mais informações, consulte [CComboBox::FindString](../Topic/CComboBox::FindString.md) ou [CListBox::FindString](../Topic/CListBox::FindString.md).  
  
## Consulte também  
 <xref:System.ArgumentOutOfRangeException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)