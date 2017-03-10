---
title: "N&#227;o h&#225; suporte para o evento &#39;Class_Terminate&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42002"
  - "bc42002"
helpviewer_keywords: 
  - "BC42002"
ms.assetid: 11eeac74-666d-4b23-81bc-b1691290ddd0
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o h&#225; suporte para o evento &#39;Class_Terminate&#39;
Não há suporte para o evento 'Class\_Terminate'. Use 'Sub Finalize' para liberar recursos.  
  
 O `Class_Terminate` evento de versões anteriores do Visual Basic é substituído pelos destruidores de classe.  
  
 Por padrão, essa mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC42002  
  
### Para corrigir este erro  
  
-   Declarar uma `Sub` procedimento denominado `Finalize` para encerrar uma classe.`Sub Finalize` é chamado quando o coletor de lixo detecta que não há mais referências ativas à instância.  
  
## Consulte também  
 [Classes for Visual Basic 6.0 Users](http://msdn.microsoft.com/pt-br/d625222c-cd32-4c8d-b25c-ea71729b88b7)   
 [NÃO está em compilação: Usando construtores e destruidores](http://msdn.microsoft.com/pt-br/548eebe1-86c4-4377-b2f5-447cb8be3d90)   
 [NÃO está em compilação: Como: implementar a Dispose Finalize padrão \(Visual Basic\)](http://msdn.microsoft.com/pt-br/adf7a232-4ebb-485d-8626-8d64421eb0c4)