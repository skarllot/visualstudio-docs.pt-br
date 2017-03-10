---
title: "Como sincronizar conjuntos de regras do projeto de c&#243;digo com pol&#237;tica de check-in do projeto da equipe | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.selecttfsruleset"
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como sincronizar conjuntos de regras do projeto de c&#243;digo com pol&#237;tica de check-in do projeto da equipe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você sincroniza as configurações de análise de código para projetos de código da política de check\-in do projeto de equipe especificando uma regra definida que contém pelo menos as regras especificadas na regra definida para a política de check\-in.  A principal do desenvolvedor pode informá\-lo do nome e o local da regra definida para a política de check\-in.  Você pode usar uma das seguintes opções assegurar que a análise de código para o projeto use o conjunto correto de regras:  
  
-   Se a política de check\-in usa um da Microsoft a regra interno define, abre a caixa de diálogo propriedades do projeto de código, exibe a página do código, e seleciona a regra definida na página do código de configurações de projeto de código.  Os conjuntos padrão da regra da Microsoft são instalados automaticamente com o Visual Studio são definidos como somente leitura e não devem ser editados.  Se os conjuntos de regra não são editados, as regras nos conjuntos de política e da regra do local têm garantia de correspondência.  
  
-   Se a política de check\-in usa um conjunto de regra personalizada, executar uma operação get ajustado no arquivo de regra em controle de versão para criar uma cópia local.  Especifique que a localização nas configurações de análise de código para o projeto de código.  As regras têm garantia de correspondência se a regra definida para a política de check\-in é atualizado.  
  
     Se você mapear o local do controle de versão em uma pasta local que está na mesma relação à raiz do projeto de equipe como seu projeto de código, o local da regra é definido usando um caminho relativo.  O caminho relativo garante que a configuração de projeto de código para a análise de código pode ser movida para outros computadores.  
  
-   Personalizar uma cópia da regra definida para a política de check\-in de um projeto de código.  Verifique se o novo conjunto de regras contém todas as regras na política de check\-in e todas as outras regras que você quer incluir.  Você deve garantir que o conjunto de regras inclui todas as regras na regra definida para a política de check\-in.  
  
### Para especificar um conjunto padrão da regra da Microsoft  
  
1.  Em **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto de código, e clique em **Propriedades**.  
  
2.  Clique **Análise de Código**.  
  
3.  Na lista de **Executar este conjunto de regras** , clique no conjunto de regras de política de check\-in.  
  
### Para especificar uma política personalizado de check\-in use o conjunto  
  
1.  Se necessário, executar uma operação get ajustado no arquivo da regra que especifica a política de check\-in.  
  
2.  Em **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto de código, e clique em **Propriedades**.  
  
3.  Clique **Análise de Código**.  
  
4.  Na lista de **Executar este conjunto de regras** , clique **\<Procurar…\>**.  
  
5.  Na caixa de diálogo de **Abrir** , especifique o arquivo ajustado da regra de política de check\-in.  
  
### Para criar uma regra personalizada definida para um código de projeto  
  
1.  Siga um dos procedimentos anteriores neste tópico para selecionar a política de check\-in do projeto da equipe do analysis server na página de código da caixa de diálogo configurações de projeto.  
  
2.  Clique em **Abrir**.  
  
3.  Adicionar ou remover regras usando o editor do conjunto de regra.  
  
     Para obter mais informações, consulte [Criando conjuntos de regras personalizados](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
4.  Salve a regra alterada definida como um arquivo de .ruleset no computador local ou um caminho UNC.  
  
5.  Abrir a caixa de diálogo propriedades do projeto de código, e exibir a página de **Análise de Código** .  
  
6.  Na lista de **Executar este conjunto de regras** , clique **\<Procurar…\>**.  
  
7.  Na caixa de diálogo de **Abrir** , especifique o arquivo ajustado da regra.