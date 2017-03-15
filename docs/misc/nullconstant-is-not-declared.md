---
title: "&#39;&lt; nullconstant &gt;&#39; n&#227;o est&#225; declarado. | Microsoft Docs"
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
  - "bc30822"
  - "vbc30822"
helpviewer_keywords: 
  - "BC30822"
ms.assetid: dda0e2c1-46a3-4cc4-b36c-0858a5259bac
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; nullconstant &gt;&#39; n&#227;o est&#225; declarado.
'\< nullconstant \>' não está declarado. Não há suporte para a constante NULL; Use DBNull.  
  
 Uma instrução usa o `Null` palavra\-chave, que não é mais suportado no Visual Basic.  
  
 **ID do erro:** BC30822  
  
### Para corrigir este erro  
  
1.  Use <xref:System.DBNull> em vez de `Null`. O exemplo a seguir demonstra isso.  
  
    ```  
    Sub TestDBNull() Dim t As DataTable ' Assume the DataGrid is bound to a DataTable. t = CType(DataGrid1.DataSource, DataTable) Dim r As DataRow r = t.Rows(datagrid1.CurrentCell.RowNumber) r.BeginEdit r(1) = System.DBNull.Value ' Assign DBNull to the record. r.EndEdit r.AcceptChanges If r.IsNull(1) Then MsgBox("") End If End Sub  
    ```  
  
2.  Use o [nada](/dotnet/visual-basic/language-reference/nothing) palavra\-chave para atribuições e comparações quando você usa variáveis de objeto. O exemplo a seguir demonstra isso.  
  
    ```  
    Sub TestNothing() Dim cls As Object ' cls is Nothing if it has not been assigned using the New keyword. If (cls Is Nothing) Then MsgBox("cls is Nothing") End If cls = Nothing ' Assign Nothing to the class variable cls. End Sub  
    ```  
  
## Consulte também  
 <xref:System.DBNull>   
 [nada](/dotnet/visual-basic/language-reference/nothing)   
 [Programming Element Support Changes Summary](http://msdn.microsoft.com/pt-br/0483590a-6309-449c-a2fa-effa26a03b95)