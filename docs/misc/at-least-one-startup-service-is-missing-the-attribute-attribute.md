---
title: "Pelo menos um servi&#231;o de inicializa&#231;&#227;o est&#225; com o atributo &#39;atributo&#39; faltando | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.projfile_missing_ss_attrib"
ms.assetid: 987c42dc-4394-4b07-b7fa-a8e7afc6fdfb
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Pelo menos um servi&#231;o de inicializa&#231;&#227;o est&#225; com o atributo &#39;atributo&#39; faltando
Um serviço de inicialização requer o atributo ID, que não foi encontrado um `<Service>` elemento. Por exemplo:  
  
```  
<Service ID="{0000-0000-0000-00000000-000000000000}"/>  
```  
  
 Isso indica que o arquivo de projeto está corrompido.  
  
 Esse erro provavelmente é causado editando manualmente o arquivo de projeto.  
  
 **Para corrigir este erro**  
  
-   Salve o arquivo de projeto.  
  
     A seção com defeito não será gravada e esse erro não ocorrerá na próxima vez que você abrir o projeto.  
  
## Consulte também  
 [NIB: Propriedades de projeto \(Visual Studio\)](http://msdn.microsoft.com/pt-br/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)