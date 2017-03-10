---
title: "&#39;&lt; typename &gt;&#39; tem o mesmo nome que outro tipo exposto em um grupo &#39;My&#39; | Microsoft Docs"
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
  - "vbc36015"
  - "bc36015"
helpviewer_keywords: 
  - "BC36015"
ms.assetid: cd2286da-49be-461f-bec9-58e9c53e250b
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; typename &gt;&#39; tem o mesmo nome que outro tipo exposto em um grupo &#39;My&#39;
'\< typename \>' tem o mesmo nome que outro tipo exposto em um grupo 'My'. Renomeie o formulário ou seu namespace delimitador.  
  
 Uma classe ou estrutura é declarada com o mesmo nome que uma classe ou estrutura em um do `My` objetos.  
  
 Não pode ser evitada uma colisão de nomes entre duas classes que podem ser acessados por meio de um `My` de objeto, como `My.Forms`.  
  
 Se houver uma colisão de nomes possíveis entre classes em um `My` do objeto, o compilador altera o nome da propriedade para o tipo de *ClassName* para *RootNamespace*\_*Namespace*\_*ClassName*. Por exemplo, considere dois formulários denominados `Form1`. Se uma dessas formas está no namespace raiz `WindowsApplication1` e no namespace `Namespace1`, você acessaria o formulário por meio de `My.Forms.WindowsApplication1_Namespace1_Form1`.  
  
 Esse erro pode ocorrer se duas classes têm o mesmo nome e estão em namespaces aninhados com sublinhados em seus nomes. Quando o compilador constrói os novos nomes de propriedade para as classes, ainda há uma colisão de nomes.  
  
 **ID do erro:** BC36015  
  
### Para corrigir este erro  
  
1.  Renomeie o novo formulário.  
  
2.  Renomeie os namespaces.  
  
     Evite qualquer classe ou estrutura de nomenclatura com o mesmo nome que um já existente.  
  
## Consulte também  
 <xref:System.Windows.Forms.Form>   
 <xref:Microsoft.VisualBasic.MyGroupCollectionAttribute>   
 [NOTINBUILD: Resolvendo uma referência quando várias variáveis têm o mesmo nome](http://msdn.microsoft.com/pt-br/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [Objeto My.Forms](/dotnet/visual-basic/language-reference/objects/my-forms-object)