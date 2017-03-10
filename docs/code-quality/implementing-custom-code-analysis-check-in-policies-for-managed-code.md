---
title: "Implementando pol&#237;ticas de check-in de an&#225;lise do c&#243;digo personalizadas para c&#243;digo gerenciado | Microsoft Docs"
ms.custom: ""
ms.date: "12/12/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.code.analysis.selecttfsrulesets"
  - "vs.code.analysis.browsefortfsruleset"
  - "vs.code.analysis.policyeditor"
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Implementando pol&#237;ticas de check-in de an&#225;lise do c&#243;digo personalizadas para c&#243;digo gerenciado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Uma política de check\-in do código especifica um conjunto de regras que os membros de um projeto de equipe deve estar em execução no código\-fonte antes que tenha sido feito check\-in no controle de versão.  A Microsoft fornece um conjunto de *conjuntos de regra* padrão que agrupam regras de análise de código em áreas funcionais.  *Os conjuntos personalizadas da regra de política de check\-in* especificam um conjunto de regras de análise de código específicas a um projeto de equipe.  Um conjunto de regras é armazenado em um arquivo de .ruleset.  
  
 As políticas de check\-in são definidas no nível de projeto de equipe e especificadas pelo local de um arquivo de .ruleset na árvore do controle de versão.  Não há nenhuma limitação no local do controle de versão do conjunto de regra personalizada da política de equipe.  
  
 A análise de código é configurada para os projetos individuais de código na janela de propriedades para cada projeto.  Uma regra personalizada definida para um projeto de código é especificado pela o local físico do arquivo de .ruleset no computador local.  Quando um arquivo de .ruleset é especificado que está localizado na mesma unidade que o projeto de código, o Visual Studio usa um caminho relativo ao arquivo na configuração do projeto.  
  
 Uma prática sugerido para criar um conjunto de regra personalizada de projeto de equipe é armazenar o arquivo de política .ruleset de check\-in em uma pasta especial que não é uma parte de nenhum projeto de código.  Se você armazenar o arquivo em uma pasta dedicada, você pode aplicar as permissões que restringem os quais pode editar o arquivo da regra e, você pode mover facilmente a estrutura de diretórios que contém o projeto para outro computador ou diretório.  
  
## Criando o conjunto personalizado da regra do check\-in do projeto de equipe  
 Para criar uma regra personalizada definida para um projeto de equipe, primeiro você cria uma pasta especial para a regra de política de check\-in definida em **Gerenciador do Controle do Código\-Fonte**.  No momento da criação do arquivo do conjunto de regra e adiciona o arquivo ao controle de versão.  Finalmente, você especifica a regra definida como a política de check\-in do código para o projeto de equipe.  
  
> [!NOTE]
>  Para criar uma pasta em um projeto de equipe, você primeiro deve mapear a raiz do projeto de equipe em um local no computador local.  Para obter mais informações, consulte [Criar e trabalhar com espaços de trabalho](http://msdn.microsoft.com/pt-br/db4d5692-179a-44fe-ad31-0c1c900c9cb2).  
  
#### Para criar a pasta de controle de versão da política de check\-in use o conjunto  
  
1.  Em [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], expanda o nó do projeto de equipe, e clique em **Controle do Código\-Fonte**.  
  
2.  No painel de **Pastas** , clique com o botão direito do mouse no projeto de equipe e clique em **Nova Pasta**.  
  
3.  No painel de controle do código\-fonte principal, clique com o botão direito do mouse em **Nova Pasta**, clique **Renomear**, e digite um nome para a pasta de conjunto da regra.  
  
#### Para criar o conjunto de regras de política de check\-in  
  
1.  No menu **Arquivo**, aponte para **Novo**, e em seguida, clique em **Arquivo**.  
  
2.  Na lista de **Categorias** , clique **Geral**.  
  
3.  Na lista de **Modelos** , clique duas vezes em **Conjunto de Regras da Análise de Código**.  
  
4.  Especificar as regras a serem incluídas no conjunto de regras, e salve o arquivo ajustado de regra à pasta de conjunto da regra que você criou.  
  
     Para obter mais informações, consulte [Criando conjuntos de regras personalizados](../code-quality/creating-custom-code-analysis-rule-sets.md)  
  
#### Para adicionar o arquivo do conjunto de regras ao controle de versão  
  
1.  Em **Gerenciador do Controle do Código\-Fonte**, clique com o botão direito do mouse na nova pasta, e clique em **Adicionar Itens à Pasta**.  
  
     Para obter mais informações, consulte [Usar controle de versão](../Topic/Use%20version%20control.md).  
  
2.  Clique no arquivo do conjunto de regras que você criou, e clique em **Concluir**.  
  
     O arquivo é adicionado ao controle do código\-fonte e fazer check\-out para você.  
  
3.  Na janela detalhes de **Gerenciador do Controle do Código\-Fonte** , clique com o botão direito do mouse no nome de arquivo e clique em **Fazer Check\-in de Alterações Pendentes**.  
  
4.  Na caixa de diálogo de **Fazer Check\-in** , você tem a opção de adicionar um comentário e clique em **Fazer Check\-in**.  
  
    > [!NOTE]
    >  Se você já tiver configurado uma política de check\-in de análise de código para seu projeto de equipe e você selecionou **Impõe o check\-in para conter somente os arquivos que fazem parte da solução atual**, você irá um aviso de falha da política.  Na caixa de diálogo da falha da política, selecione **Substituir falha da política e continuar o check\-in**.  Adicionar um comentário necessário, e clique em **OK**.  
  
#### Para especificar o arquivo ajustado da regra como a política de check\-in  
  
1.  No menu de **Equipe** , aponte para **Configurações de Projeto de Equipe**, e clique em **Controle do Código\-Fonte**.  
  
2.  Clique **Política de Check\-in**, e clique em **Adicionar**.  
  
3.  Na lista de **Política de Check\-in** , clique duas vezes em **Análise de Código**, e verifique se a caixa de seleção de **Impor Análise de Código para Código Gerenciado** está selecionada.  
  
4.  Na lista de **Executar este conjunto de regras** , clique **\<Selecionar Conjunto de Regras do Controle do Código\-Fonte\>**.  
  
5.  Digite o caminho do arquivo do conjunto de regra de política de check\-in no controle de versão.  
  
     O caminho deve estar de acordo com a seguinte sintaxe:  
  
     **$\/** `TeamProjectName` **\/** `VersionControlPath`  
  
    > [!NOTE]
    >  Você pode copiar o caminho usando um dos seguintes procedimentos em **Gerenciador do Controle do Código\-Fonte**:  
  
    -   No painel de **Pastas** , clique na pasta que contém o arquivo ajustado da regra.  Copie o caminho do controle de versão da pasta que aparece na caixa de **Origem** , e digite o nome do arquivo do conjunto de regra manualmente.  
  
    -   Na janela de detalhes, clique com o botão direito do mouse no arquivo do conjunto de regra, e clique em **Propriedades**.  Na guia de **Geral** , copie o valor em **Nome do servidor**.  
  
## Sincronizando projetos de código ao conjunto de regras de política de check\-in  
 Você especifica uma regra de política do check\-in do projeto da equipe definida como a regra de análise de código definida de uma configuração de projeto de código na caixa de diálogo propriedades do projeto de código.  Se o conjunto de regras está localizado na mesma unidade que o projeto de código, um caminho relativo será usado especificar a regra definida quando o caminho é selecionado da caixa de diálogo do arquivo.  O caminho relativo habilita as configurações das propriedades de projeto para ser portátil para outros computadores que usam estruturas semelhantes locais de controle de versão.  
  
#### Para especificar uma regra de projeto de equipe definida como a regra definida de um código de projeto  
  
1.  Se necessário, recuperar a pasta e o arquivo de conjunto da regra de política de check\-in de controle de versão.  
  
     Você pode executar esta etapa em **Gerenciador do Controle do Código\-Fonte** clique com o botão direito do mouse na pasta do conjunto de regra e clicando em **Obter Última Versão**.  
  
2.  Em **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto de código, e clique em **Propriedades**.  
  
3.  **Análise de código em**.  
  
4.  Se necessário, selecione as opções apropriadas em listas de **Configuração** e de **Plataforma** .  
  
5.  Para executar todas as vezes na análise de código que o projeto de código é construído usando a configuração especificada, marque a caixa de seleção de **Habilitar a análise de código na construção \(define a constante de CODE\_ANALYSIS\)** .  
  
6.  Para ignorar o código em componentes de outras empresas, marque a caixa de seleção de **Suprimir resultados do código gerado** .  
  
7.  Na lista de **Executar este conjunto de regras** , clique **\<Procurar…\>**.  
  
8.  Especificar a versão local do arquivo do conjunto de regra de política de check\-in.