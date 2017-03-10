---
title: "Esse erro tamb&#233;m pode ocorrer devido &#224; combina&#231;&#227;o de uma refer&#234;ncia de arquivo para &#39;&lt; arquivo1 &gt;&#39; no projeto &#39;&lt; projectname1 &gt;&#39; com uma refer&#234;ncia de arquivo para &#39;&lt; filename2 &gt;&#39; no projeto &#39;&lt; projectname2 &gt;&#39; &lt; mensagem &gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30970"
  - "vbc30970"
helpviewer_keywords: 
  - "BC30970"
ms.assetid: 81cc4f7b-cc16-46cc-9a49-74980300e158
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Esse erro tamb&#233;m pode ocorrer devido &#224; combina&#231;&#227;o de uma refer&#234;ncia de arquivo para &#39;&lt; arquivo1 &gt;&#39; no projeto &#39;&lt; projectname1 &gt;&#39; com uma refer&#234;ncia de arquivo para &#39;&lt; filename2 &gt;&#39; no projeto &#39;&lt; projectname2 &gt;&#39; &lt; mensagem &gt;
\< Mensagem \> que esse erro também pode ocorrer devido à combinação de uma referência de arquivo para '\< filepathname1 \>' no projeto '\< projectname1 \>' com uma referência de arquivo para '\< filepathname2 \>' no projeto '\< projectname2 \>'.  Se os dois assemblies forem idênticos, tente substituir essas referências para que ambas sejam do mesmo local.  
  
 Código no seu projeto acessa um membro de outro projeto, mas a configuração de sua solução não permite que o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilador resolver a referência.  
  
 Para acessar um tipo definido em outro assembly, o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilador deve ter uma referência a esse assembly. Isso deve ser uma referência única e não ambígua, que não cause referências circulares entre projetos.  
  
 **ID do erro:** BC30970  
  
### Para corrigir este erro  
  
1.  Determine qual projeto produz o melhor conjunto para o seu projeto para fazer referência. Para essa decisão, você pode usar critérios, como a facilidade de acesso a arquivos e a freqüência de atualizações.  
  
2.  Nas propriedades do projeto, adicione uma referência para o arquivo que contém o assembly que define o tipo que você está usando.  
  
## Consulte também  
 [Gerenciando referências em um projeto](../ide/managing-references-in-a-project.md)   
 [NIB: Referenciando Namespaces e componentes](http://msdn.microsoft.com/pt-br/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [NOTINBUILD: Resolvendo uma referência quando várias variáveis têm o mesmo nome](http://msdn.microsoft.com/pt-br/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [PONTA como: Adicionar ou remover referências usando a caixa de diálogo Adicionar referência](http://msdn.microsoft.com/pt-br/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [PONTA como: modificar propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Solucionando Problemas de Referências Quebradas](../ide/troubleshooting-broken-references.md)