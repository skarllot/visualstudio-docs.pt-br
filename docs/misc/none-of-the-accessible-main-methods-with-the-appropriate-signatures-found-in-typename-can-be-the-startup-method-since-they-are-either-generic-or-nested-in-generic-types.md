---
title: "Nenhum dos m&#233;todos &#39;Main&#39; acess&#237;veis com as assinaturas apropriadas encontrados em &#39;&lt; typename &gt;&#39; pode ser o m&#233;todo de inicializa&#231;&#227;o porque eles s&#227;o gen&#233;ricos ou aninhados em tipos gen&#233;ricos | Microsoft Docs"
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
  - "vbc30796"
  - "BC30796"
helpviewer_keywords: 
  - "BC30796"
ms.assetid: 606b3629-5a92-4c79-ace2-a530cab8c978
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Nenhum dos m&#233;todos &#39;Main&#39; acess&#237;veis com as assinaturas apropriadas encontrados em &#39;&lt; typename &gt;&#39; pode ser o m&#233;todo de inicializa&#231;&#227;o porque eles s&#227;o gen&#233;ricos ou aninhados em tipos gen&#233;ricos
Uma classe, módulo ou estrutura não tem qualquer `Main` procedimento que qualifica como o procedimento de inicialização do projeto.  
  
 Visual Basic requer que o procedimento de inicialização para um projeto não seja dependente de argumentos de tipo. Portanto, ele deve ser capaz de acessar pelo menos um `Main` procedimento é genérico nem contido em qualquer tipo genérico.  
  
 **ID do erro:** BC30796  
  
### Para corrigir este erro  
  
-   Defina pelo menos um do `Main` procedimentos para que ele não seja genérico e não está contido em um tipo genérico.  
  
     \- ou \-  
  
-   Sobre o **propriedades** para seu projeto, especifique um outro formulário ou módulo para o **formulário de inicialização** ou **objeto de inicialização**.  
  
## Consulte também  
 [PONTA como: modificar propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [NIB: versão do Visual Basic do Hello, World](http://msdn.microsoft.com/pt-br/9d030b60-e148-4366-a462-69532f02294c)