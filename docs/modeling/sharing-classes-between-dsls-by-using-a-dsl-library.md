---
title: Compartilhando Classes entre DSLs usando uma biblioteca de DSL | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 509bd96b-3e66-47f4-8642-771421d0d0d5
caps.latest.revision: 7
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: ed225f315c92cf9276eb97fcb78e1730250ecd4c
ms.lasthandoff: 02/22/2017

---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>Compartilhando classes entre DSLs por meio de uma biblioteca de DSLs
No [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] SDK de modelagem e visualização, você pode criar uma definição de DSL incompleta que você pode importar para outra DSL. Isso permite decompor partes comuns de modelos semelhantes.  
  
## <a name="creating-and-using-dsl-libraries"></a>Criando e usando bibliotecas de DSL  
  
#### <a name="to-create-a-dsl-library"></a>Para criar uma biblioteca de DSL  
  
1.  Criar um novo projeto DSL e escolher o modelo de solução de biblioteca de DSL.  
  
     Um único projeto DSL será criado com um modelo vazio.  
  
2.  Você pode adicionar classes de domínio, relações, formas e assim por diante.  
  
     Os elementos na biblioteca não é necessário que formar uma única árvore de incorporação.  
  
     Para definir uma relação que podem usar importadores, crie duas classes de domínio e criar o relacionamento entre elas.  
  
     É recomendável configurar o **modificador de herança** das classes de domínio para `Abstract`.  
  
3.  Você pode adicionar elementos definidos no Gerenciador de DSL, como construtores de Conexão.  
  
4.  Você pode adicionar as personalizações que requerem código adicional, como restrições de validação.  
  
5.  Clique em **transformar todos os modelos**.  
  
6.  Compile o projeto.  
  
7.  Quando você distribui a DSL para outros usuários, você deve fornecer o conjunto compilado (DLL) e o arquivo `DslDefinition.dsl`. Você pode encontrar o assembly compilado em uma pasta sob`Dsl\bin\*`  
  
#### <a name="to-import-a-dsl-library"></a>Para importar uma biblioteca de DSL  
  
1.  Em outra definição de DSL, em **Gerenciador de DSL**, clique com botão direito a classe raiz do DSL e, em seguida, clique em **adicionar nova importação DslLibrary**.  
  
2.  Na janela Propriedades, defina o **caminho de arquivo** da biblioteca. Você pode usar um caminho absoluto ou relativo.  
  
     A biblioteca importada aparece no Gerenciador de DSL, no modo somente leitura.  
  
3.  Você pode usar as classes importadas como classes base. Criar uma classe de domínio na importação DSL e nas propriedades da janela, defina **classe Base** a uma classe importada.  
  
4.  Clique em transformar todos os modelos.  
  
5.  Adicione uma referência ao assembly (DLL) que foi compilado com o projeto de biblioteca de DSL ao projeto DSL.  
  
6.  Compile a solução.  
  
 Uma biblioteca de DSL podem importar outras bibliotecas. Quando você importa uma biblioteca, suas importações aparecem automaticamente no Gerenciador de DSL.  
  
## <a name="see-also"></a>Consulte também  
 [Como definir uma linguagem específica de domínio](../modeling/how-to-define-a-domain-specific-language.md)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

