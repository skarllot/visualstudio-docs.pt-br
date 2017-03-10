---
title: "N&#227;o foi poss&#237;vel copiar o assembly &#39;assembly&#39; de v&#225;rios arquivos para o diret&#243;rio &#39;diret&#243;rio&#39;. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannotcopyscatterassembly"
ms.assetid: 939519c7-741d-4e05-8b63-71e39fb426ad
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# N&#227;o foi poss&#237;vel copiar o assembly &#39;assembly&#39; de v&#225;rios arquivos para o diret&#243;rio &#39;diret&#243;rio&#39;. &lt;reason&gt;
Assemblies multi\-arquivos são copiados para um subdiretório do diretório do projeto do qual serão executados.  Por exemplo, se o caminho de saída é c:\\project1\\bin e existe um assembly \(cujo `CopyLocal` propriedade é `true`\) denominado Test contendo arquivos dll e b. dll, você terá a seguinte estrutura de arquivo após a conclusão da cópia:  
  
```  
c:\project1\bin\Test  
   c:\project1\bin\Test\Test.dll   (main assembly)  
   c:\project1\bin\Test\a.dll       (file a.dll)  
   c:\project1\bin\Test\b.dll       (file b.dll)  
```  
  
 Esse erro seria exibido pelo sistema do projeto se o c:\\project1\\bin\\Test de diretório não pôde ser criado no disco.  
  
 Este erro indica que estão fora do espaço em disco ou está atingindo o limite MAX\_PATH comprimentos caminho.  
  
 **Para corrigir este erro**  
  
-   Verifique se há espaço em disco.  
  
-   Mova o projeto para uma pasta cujo tamanho de caminho é que menor que o comprimento do caminho da pasta do projeto está atualmente.  
  
-   Altere o diretório de saída para uma pasta com um comprimento de caminho absoluto menor \(aplicável cliente somente para projetos\).  
  
## Consulte também  
 [Solucionando Problemas de Referências Quebradas](../ide/troubleshooting-broken-references.md)   
 [Como adicionar ou remover referências usando a caixa de diálogo Adicionar Referência](http://msdn.microsoft.com/pt-br/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/pt-br/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)