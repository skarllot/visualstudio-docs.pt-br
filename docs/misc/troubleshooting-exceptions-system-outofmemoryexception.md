---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.OutOfMemoryException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
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
  - "Classe OutOfMemoryException"
ms.assetid: eb16f008-964e-40a1-91f6-6ad25fa82d5a
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.OutOfMemoryException
Um <xref:System.OutOfMemoryException> exceção é lançada quando uma tentativa de alocar memória falha.  
  
## Dicas associadas  
 **Se você estiver criando uma matriz, verifique se que o tamanho está correto.**  
 Para obter mais informações, os usuários do Visual Basic poderão ver [Matrizes](/dotnet/visual-basic/programming-guide/language-features/arrays/index).  
  
 Para obter mais informações, os usuários do c\# poderão ver [Matrizes](/dotnet/csharp/programming-guide/arrays/index).  
  
 **Certifique\-se de que você tenha memória suficiente para fins internos e novos objetos gerenciados.**  
 Se você estiver programando no [!INCLUDE[Compact](../extensibility/includes/compact_md.md)], o common language runtime lança essa exceção quando não há memória suficiente para fins internos ou novos objetos gerenciados. Para evitar a exceção, evite programar métodos grandes que consomem 64 ou mais quilobytes de memória.  
  
## Comentários  
 Uso excessivo de memória gerenciada normalmente é causado por:  
  
-   Ler grandes conjuntos de dados na memória.  
  
-   Criando entradas de cache excessivas.  
  
-   Carregar ou baixar arquivos grandes.  
  
-   Uso excessivo de expressões regulares ou cadeias de caracteres ao analisar arquivos.  
  
-   Estado de exibição excessivo.  
  
-   Muitos dados no estado da sessão ou muitas sessões.  
  
 Essa exceção pode ser lançada com uma mensagem adicional, "não há armazenamento suficiente está disponível para concluir esta operação," ao chamar um método em uma COM tipo de objeto que retorna um definido pelo usuário que contém uma matriz segura \(uma matriz de tamanho não fixo\). Isso ocorre porque o .NET Framework não é possível empacotar uma estrutura de campo com um tipo de matriz segura.  
  
## Consulte também  
 <xref:System.OutOfMemoryException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)