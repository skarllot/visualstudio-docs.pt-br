---
title: "&#39;ParamArray&#39; n&#227;o pode ser aplicado ao primeiro par&#226;metro de um m&#233;todo de extens&#227;o | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36554"
  - "bc36554"
helpviewer_keywords: 
  - "BC36554"
ms.assetid: 0778a854-246f-4c2b-943d-ea8883b3aa6f
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ParamArray&#39; n&#227;o pode ser aplicado ao primeiro par&#226;metro de um m&#233;todo de extens&#227;o
'ParamArray' não pode ser aplicado ao primeiro parâmetro de um método de extensão. O primeiro parâmetro especifica que tipo para estender.  
  
 O primeiro parâmetro de um método de extensão especifica o tipo de dados que o método estende. Portanto, o primeiro parâmetro é obrigatório e não pode ser opcional. Como uma matriz de parâmetros é automaticamente opcional, não é válido como o primeiro argumento de um método de extensão.  
  
> [!NOTE]
>  Quando o método for executado, a instância do tipo de dados estendidos que chama o método torna\-se o argumento para o primeiro parâmetro do método. Por exemplo, a instância `greeting` em `greeting.Print()` é o argumento para o primeiro parâmetro, `str`, no método de extensão `Public Sub Print (ByVal str As String)`.  
  
 **ID do erro:** BC36554  
  
### Para corrigir este erro  
  
-   Se a matriz de parâmetros não especificar o tipo de dados que você deseja estender, adicione um novo primeiro parâmetro que especifica este tipo.  
  
    ```  
    <Extension()> Public Sub AddTo(ByRef str As String, ByVal ParamArray addOns() As String) ' Concatenate the strings in addOns to str. End Sub  
    ```  
  
-   Se a matriz de parâmetros especificar o tipo de dados que você deseja estender, considere alterá\-la para uma matriz regular, que requer um argumento, em vez de uma matriz de parâmetros. Matrizes regulares podem ser estendidas.  
  
    ```  
    <Extension()> Public Function Sum(ByVal ints() As Integer) As Integer Dim total As Integer = 0 For Each i As Integer In ints total = total + i Next i Return total End Function  
    ```  
  
## Consulte também  
 [Métodos de extensão](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Matrizes de parâmetros](/dotnet/visual-basic/programming-guide/language-features/procedures/parameter-arrays)   
 [Parâmetros opcionais](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)