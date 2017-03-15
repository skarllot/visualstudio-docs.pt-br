---
title: "O assembly &#39;&lt; filepath1 &gt;&#39; referencia o assembly &#39;&lt; assemblyidentity &gt;&#39;, que &#233; amb&#237;guo entre &#39;&lt; filepath2 &gt;&#39; (referenciado pelo projeto &#39;&lt; projectname1 &gt;&#39;) e &#39;&lt; filepath3 &gt;&#39; (referenciado pelo projeto &#39;&lt; projectname2 &gt;&#39;) | Microsoft Docs"
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
  - "bc42204"
  - "vbc42204"
helpviewer_keywords: 
  - "BC42204"
ms.assetid: b0c3d2b6-2776-4981-b79e-2e36f03d4123
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O assembly &#39;&lt; filepath1 &gt;&#39; referencia o assembly &#39;&lt; assemblyidentity &gt;&#39;, que &#233; amb&#237;guo entre &#39;&lt; filepath2 &gt;&#39; (referenciado pelo projeto &#39;&lt; projectname1 &gt;&#39;) e &#39;&lt; filepath3 &gt;&#39; (referenciado pelo projeto &#39;&lt; projectname2 &gt;&#39;)
O assembly '\< filepath1 \>' referencia o assembly '\< assemblyidentity \>', que é ambíguo entre '\< filepath2 \>' \(referenciado pelo projeto '\< projectname1 \>'\) e '\< filepath3 \>' \(referenciado pelo projeto '\< projectname2 \>'\). '\< filepath2 \>' será usado. Se os dois assemblies forem idênticos, altere as referências para o mesmo local.  
  
 Um assembly acessa um tipo em outro assembly que têm mais de uma referência de arquivo.  
  
 O compilador não pode garantir que os arquivos em diferentes locais mantém a mesma versão do mesmo assembly. Portanto, as referências de arquivo são ambíguas, e o compilador deve selecionar um.  
  
 O *identidade do assembly* inclui nome, versão, chave pública, se houver e cultura do assembly. Essa informação identifica unicamente o assembly.  
  
 Por padrão, essa mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC42204  
  
### Para corrigir este erro  
  
1.  Determine qual arquivo representa a melhor opção para o assembly. Você pode usar critérios, como a versão mais recente, a acessibilidade do arquivo e a probabilidade de que está sendo atualizado quando apropriado.  
  
2.  Altere todas as referências de arquivo a esse assembly para usarem o caminho do arquivo idêntico ao seu arquivo escolhido.  
  
## Consulte também  
 [NÃO na compilação: Assemblies](http://msdn.microsoft.com/pt-br/6c5c7b30-fa78-4f40-b908-120d0743b0e6)   
 [Assemblies no Common Language Runtime](../Topic/Assemblies%20in%20the%20Common%20Language%20Runtime.md)   
 [Benefícios dos assemblies](../Topic/Assembly%20Benefits.md)   
 [Gerenciando referências em um projeto](../ide/managing-references-in-a-project.md)   
 [PONTA: Referências](http://msdn.microsoft.com/pt-br/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [PONTA como: Adicionar ou remover referências usando a caixa de diálogo Adicionar referência](http://msdn.microsoft.com/pt-br/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)