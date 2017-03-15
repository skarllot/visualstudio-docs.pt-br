---
title: "Instru&#231;&#245;es passo a passo: configurando e usando um conjunto de regras personalizado | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "análise de código, instruções passo a passo"
  - "conjuntos de regras de análise de código"
ms.assetid: 7fe0a4e3-1ce0-4f38-a87a-7d81238ec7cd
caps.latest.revision: 40
caps.handback.revision: 40
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es passo a passo: configurando e usando um conjunto de regras personalizado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este passo a passo mostra como usar as ferramentas de análise de código que foram configuradas para usar um *conjunto de regras* personalizado em uma biblioteca da classe.  Você pode selecionar uma regra definida que se relaciona ao tipo de projeto que você especificou para sua solução, ou você pode selecionar conjuntos alternativos de regra para atender a uma necessidade específica como o código herdado de exploração de problemas que podem ser corrigidos de uma maneira incondicional.  Em ambos os casos, os conjuntos de regra também podem ser personalizadas para ajustar\-los aos requisitos do seu projeto.  
  
 Neste passo a passo, você pisará com esses processos:  
  
-   Crie uma biblioteca da classe.  
  
-   Selecione o conjunto de regras do código de **Regras Básicas de Diretrizes de Design da Microsoft** .  
  
-   Adicionar seu próprio código para a classe.  
  
-   Executar análise de código.  
  
-   Personalizar o conjunto de regras.  
  
-   Executar análise de código e verificar como o comportamento do conjunto de personalização de regra funciona.  
  
## Pré-requisitos  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] ou [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
## Usando conjuntos de regra com análise de código  
 Primeiro, crie uma biblioteca simples da classe.  
  
#### Crie uma biblioteca de classe  
  
1.  No menu **Arquivo**, clique em **Novo** e em **Projeto**.  
  
2.  Na caixa de diálogo de **Novo Projeto** , em **Tipos de projeto**, clique em **Visual \# C**.  
  
3.  Em **Visual \# C**, **Biblioteca de Classes**selecione.  
  
4.  Na caixa de texto de **Nome** , o tipo RuleSetSample e clique em **OK**.  
  
 Em seguida, você selecionará a regra de **Regras Básicas de Diretrizes de Design da Microsoft** definida e salvá\-la com seu projeto.  
  
#### Selecione um conjunto de regras de análise de código  
  
1.  No menu de **Analisar** , clique **Configurar a análise de código para RuleSetSample**.  
  
     Os parâmetros de configuração para análise do código são exibidos.  
  
2.  Na lista suspensa de **Executar este conjunto de regras** , **Todas as Regras da Microsoft**selecione.  
  
     Para obter mais informações sobre conjuntos de regra disponíveis, consulte [Referência do conjunto de regras da análise de código](../code-quality/code-analysis-rule-set-reference.md).  
  
     No menu arquivo, clique **Salvar itens selecionados** para atualizar o arquivo de projeto com informações sobre a regra definida que você selecionou e as configurações.  
  
    > [!TIP]
    >  Em uma situação do mundo real, uma prática recomendada usar para priorizar os problemas que você deseja destino com a análise do código são começar a regra de **Regras recomendadas mínimo** definida e corrigir problemas desejados, e adicionará incremental mais regras ou define a regra para localizar e corrigir problemas adicionais.  
  
 Em seguida, você adicionará um código para a biblioteca de classes que será usada para demonstrar violações de CA1704 “identificadores deve ser” regra corretamente escrito da análise de código.  Para obter mais informações, consulte [CA1704: os identificadores do recurso devem ter a ortografia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
#### Adicionar seu próprio código  
  
-   No Solution Explorer, abra o arquivo de Class1.cs e substitua o código existente pelo seguinte:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
  
    namespace RuleSetSample  
    {  
        public class Class1  
        {  
            //The variable parameter names "a" and "b" will cause  
            //the warning CA 1704 Microsoft.Naming "Consider   
            //providing a more meaningful name" to fire  
            public int AddIntegers(int a, int b)  
            {  
  
                int sum = a + b;  
  
                return (sum);  
            }  
        }  
    }  
  
    ```  
  
 Agora você pode executar a análise de código no projeto de RuleSetSample e procurar todos os erros e avisos gerados na janela da Lista de erros.  
  
#### Análise de código de execução no projeto de RuleSetSample  
  
1.  No menu de **Analisar** , clique **Executar análise de código em RuleSetSample**.  
  
2.  Na janela da Lista de erros, clique em **Avisos** e clique no cabeçalho da coluna de **Descrição** para classificar alfanumèrica os avisos.  
  
     Em um aplicativo do mundo real, você corrigiria qualquer valor violações de regra que corrige neste momento, ou se desejar desativar ou suprimir uma regra se você determinou que não era corrigir o valor.  Para obter mais informações, consulte [Suprimir avisos usando o atributo SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
3.  Observe os avisos CA1704.  Essas violações nesta regra indica que você deve Considerar “que fornece um nome mais significativo para os parâmetros”. Você pode corrigir o problema em seu código ou você pode desabilitar a regra, conforme explicado no procedimento a seguir.  
  
 Em seguida, você personalizará a regra definida para excluir o aviso CA1704 “, os identificadores devem estar correta.”  
  
#### Personalizar a regra definida para que seu projeto desabilita uma regra específica  
  
1.  No menu de **Analisar** , clique **Configurar a análise de código para RuleSetSample**.  
  
2.  Na lista suspensa de **Executar este conjunto de regras** , verifique se o conjunto de regras de **Todas as Regras da Microsoft** ainda está realçado e clique em **Abrir**.  A página de definição de regra é exibida.  
  
3.  Expanda o nó da categoria de Microsoft.Naming, e selecione o aviso CA1704.  
  
4.  Na coluna de **Ação** , selecione **Nenhum.** Isso impede que CA1704 exibe como um aviso ou um erro na janela da Lista de erros.  
  
     Agora é boas hora fazer experiências com vários botões da barra de ferramentas e opções de filtragem se familiarizar com eles.  Por exemplo, você pode usar a lista suspensa de **Agrupar por** para ajudar a localizar uma regra específica, ou a categoria de regras.  Outro exemplo é que você pode usar o botão de **Regras desabilitadas ocultar** na barra de ferramentas do conjunto de páginas da regra para ocultar ou mostrar todas as regras com a coluna de **Ação** definida como **Nenhum**.  Isso pode ser útil se você quiser examinar as regras que você desativar para verificar se você ainda desejar as ter desabilitadas.  
  
5.  No menu Exibir, clique em Janela de Propriedades.  O tipo **My Custom Rule Set** na caixa nome das propriedades de ferramentas da janela.  Isso altera o nome para exibição da nova regra definida em [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] IDE.  
  
6.  No menu de **Arquivo** , clique **Salvar qualquer Rules.ruleset Microsoft** para salvar o conjunto personalizado da regra.  Navegue para a pasta raiz do projeto.  Na caixa de texto de **o nome do arquivo** , digite MyCustomRuleSet.  O conjunto de regra personalizada pode ser selecionado para uso com seu projeto.  
  
 Com o novo conjunto de regras criado, agora você precisa configurar as configurações de projeto para especificar se deseja usar a nova regra definida com ela.  
  
#### Especifique a nova regra definida para uso com seu projeto  
  
1.  No Solution Explorer, clique com o botão direito do mouse no projeto e selecione **Propriedades**.  
  
2.  Na guia de **Propriedades** , clique **Análise de Código**.  
  
     Na lista suspensa de **Executar este conjunto de regras** , clique **\<Procurar.\>**.  Navegue para a pasta raiz do projeto de código e selecione MyCustomRuleSet.ruleset.  Esta é a nova regra definida que você criou no procedimento anterior.  
  
3.  No menu de **Arquivo** , clique **Salvar** para salvar sua configuração do projeto.  O conjunto de regra personalizada pode ser usado com seu projeto.  
  
 Finalmente, você executará a análise de código que usa novamente o conjunto de regras de MyCustomRuleSet.  Observe que a janela Lista de erros não exibe a violação da regra de desempenho CA1704.  
  
#### Executar análise de código no projeto de RuleSetSample pela segunda vez  
  
1.  No menu de **Analisar** , clique **Executar análise de código em RuleSetSample**.  
  
2.  Na janela da Lista de erros, observe que quando você clica em **Avisos**, você não vir o CA1704 que as violações de aviso para os “identificadores devem ser” regra escrito corretamente.  
  
## Consulte também  
 [Como configurar a análise de código para um projeto de código gerenciado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [Referência do conjunto de regras da análise de código](../code-quality/code-analysis-rule-set-reference.md)