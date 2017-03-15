---
title: "Falha no cancelamento de registro de interoperabilidade COM | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannot_unregister_com2"
ms.assetid: 1172b560-c4b0-4aff-9f74-cf9b29ff76d9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Falha no cancelamento de registro de interoperabilidade COM
Ocorreu um problema ao tentar cancelar o registro de uma cópia antiga do assembly.  
  
 Se o **Register for COM Interop** estiver definida, o sistema do projeto tentará primeiro cancelar o registro de uma cópia antiga do objeto COM antes de registrar a cópia que acabou de criar. Isso é feito para manter o registro atual.  
  
 Consulte o **criar** página de propriedades na pasta propriedades de configuração para acessar o **Register for COM Interop** propriedade.  
  
 Algumas razões possíveis de falha incluem:  
  
-   Incapacidade de cancelar o registro da biblioteca de tipos anteriores para o assembly. Isso pode ser um problema de permissões no registro.  
  
-   Incapacidade de cancelar o registro do assembly antigo. Isso pode ser um problema de permissões no registro.  
  
 Se o processo de cancelamento do registro falhar, um vazamento da GUID para objetos CoCreatable pode ocorrer, bem como para qualquer biblioteca de tipos GUIDs. No entanto, o processo geral de compilação ainda será bem\-sucedida.  
  
## Consulte também  
 [Interoperabilidade COM em aplicativos .NET Framework](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications)